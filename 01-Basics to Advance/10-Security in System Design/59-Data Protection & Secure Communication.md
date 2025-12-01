Hello and welcome to this lecture on data protection and secure communication.

Well, in today's digital world, where data is constantly being transmitted, stored and accessed across

distributed systems, ensuring its security and integrity is more critical than ever.

So this lecture will dive into the core principles and practices that are behind securing data at rest

and in transit using encryption, hashing, TLS, SSL, and more.

We will also look at how secure communications work under the hood, what makes public key infrastructure

so powerful, and how APIs stay protected from malicious access.

So whether you are designing cloud systems, microservices, or just prepping for the high level interview,

understanding these concepts are non-negotiable.

So let's get started.

So let's start with the why part of it.

Why is data protection such a big deal?

First, the threat landscape is growing rapidly, from high profile data breaches to man in the middle

attack and accidental data leaks.

Sensitive data is constantly at risk.

A single weak point in your system can expose everything from personal information to financial records.

Then there are regulatory requirements frameworks like GDPR, HIPAA and other legally mandate how data

should be handled, stored and protected.

Non-compliance can mean massive fines and legal consequences.

But beyond just threats and laws, there is this element of user trust.

Also, if users don't believe that their data is safe, they won't use your platform.

Data protection is essential to building reliable, secure systems that users and businesses can trust.

So whether you are an engineer, architect or a product owner, this isn't just a back end concern,

it's the core part of modern system design.

Now let's talk about encryption, one of the most fundamental techniques in data security.

Well, at its core, encryption is the process of converting readable data or plain text data into unreadable

format, which is often called a cipher text.

How is it done?

It is done using a secret, which is also known as key.

The idea is simple even if someone intercepts the data, they can't make sense of it without the key.

Later, the ciphertext can be decrypted back into plain text, but only with the correct key.

So the overall flow looks like this.

You have a plain text.

You have a key.

You encrypt this plain text using a key, and the plain text becomes a cipher text.

This is encryption.

On the other side of the coin, you have the cipher text and you have the key.

You decrypt the cipher text using the key, and you get your plain text back so you can read it.

This is the decryption part of the story.

So whether it's your message files or password encryption ensures that only the right people can access

the data even if it is exposed to the outside world.

Now, when we talk about encryption and system design, it is important to look at where the data is

being protected.

And that brings us to the two key concepts encryption at rest and encryption in transit.

So what is encryption at rest?

Encryption at rest protects the data that is stored somewhere, whether it is on a physical disk, inside

a database, or backed up in a cloud.

Common techniques here are full disk encryption, where the entire storage drive is encrypted.

Database level encryption, which secures the sensitive fields like password and personal data in the

database.

You will see this used in cloud storage, user uploaded files, and even system logs that contain confidential

information.

On the other hand, encryption in transit protects the data that is traveling over the network.

Like when a user sends a login request or an API fetches data from the service, the data is in transit.

So this is where protocols like TLS, SSL come in picture.

So we use Https for all the data that is in transit and thereby securing communication channels from

eavesdropping and man in the middle attacks.

Encryption of data in transit is non-negotiable for everything that involves APIs, user sessions,

or external integration.

So together, these two things encryption at rest and encryption at transit are the foundation of end

to end data protection, covering both storage and communication channels.

Now let's break down the two main types of encryption.

Symmetric and asymmetric symmetric encryption using a single secret key for both encrypt and decrypt

data.

So remember we talked about key for encryption.

And key is required for decryption.

So if you are using the same key for encrypting your data and you are using the same key for decrypting

the data, it is called symmetric encryption.

It is very fast and efficient, which makes it ideal for encrypting large volumes of data files, backups,

or database fields.

But there is a challenge.

Both the sender and receiver of the data need to have the same key.

And that means that you need a secure way to share the key.

That is where asymmetric encryption comes in.

Picture.

Asymmetric encryption uses a pair of keys, a public key to encrypt the data, and a private key to

decrypt the data.

This allows secure communications without ever sharing a secret key.

In the open, which makes it perfect for things like secure key exchange, digital signatures, and

identity verification.

In practice, systems often combine both approaches.

For example, during a TLS handshake, asymmetric encryption is used to securely exchange a symmetric

key, and then that symmetric key is used for rest of the session because symmetric key is comparatively

faster.

So in short, symmetric encryption is fast and both sender and receiver has same key.

Asymmetric is much more secure because there are two keys, but it is comparatively slower.

And to get the best of both worlds, use them together.

Use asymmetric key to transfer the key for symmetric algorithm and then use symmetric then points onwards.

Now let's look at the TLS SSL and how they power the secure communication on the web.

First thing first Https is just HTTP over TLS.

There is nothing special about it.

It is the secure version of HTTP and it ensures three critical things.

Remember CIA confidentiality that data is encrypted and hidden from eavesdropper.

Integrity data cannot be tampered with in transit.

Authenticity.

You are talking to the real server and not an imposter.

This all happens thanks to the TLS handshake, which kicks off every secure connection during the handshake.

What happens is that the client and server first exchange a cryptographic key using asymmetric encryption.

Then they negotiate which cipher suite they will use.

They establish a shared symmetric key for the fast, secure communication.

And once the handshake is complete, data flow securely over the Https.

And that is what protects everything from login forms and banking sessions to API calls.

So without TLS it is just plain HTTP, which means no encryption and no protection.

So Https is required.

So just to summarize HTTP secure is called Https.

And all this happens using TLS.

Both the parties client and server first exchange the key with each other.

And they use asymmetric encryption to encrypt the key itself.

And the key that they are sharing is the key for the symmetric encryption, which will be used for the

data transfer in the further request and responses.

Now let's talk about how we protect passwords and why we don't just store them directly, even in encrypted

form.

Well, what we do is that we use a technique called hashing, which is one way transformation.

It takes input data like a password, and run it through a hashing algorithm to produce a fixed length

string.

The key point hashing is not reversible.

You cannot take the hash and get the original password back.

That is why it is ideal for securely storing the password.

Remember, hashing is not same as encryption from encryption.

If you have the ciphertext and key, you can get back the original plaintext.

But from hash hash you will never be able to get your password back.

But there is a catch.

Sometimes the basic hashing is not enough.

Why?

If two users have same password, then their hashes would also be the same.

Then attackers can use this.

Precomputed tables are also called the rainbow tables to guess the passwords based on common hash values.

So how can we solve this?

Well, that's where salting comes in.

A salt is a random string added to the password before hashing.

It ensures that even if two users use the same password, their final hash output will be completely

different.

How?

Well, they will provide the password.

We will add a random string at the end of the password, which will be known as salt.

And then we generate the hash and we store that hash.

This makes it much harder for the attacks to reverse engineer or mass guess the passwords, because

they will have no way of knowing that the password plus salt is same for two users.

And in modern systems, we often use dedicated algorithms like Bcrypt or Argon2, which are designed

specifically for password hashing.

and they have the support for built in salt also.

Now let's dive into something that powers secure communication and internet at scale.

Public key infrastructure or in short, PCA.

PCA is the system that manages digital certificates and public private key pairs, ensuring trust between

users, browsers and servers.

Three players user, browser and server.

So here is how it works.

Every secure website uses a digital certificate which contains its public key and identity information.

But how do we know that this certificate and the server can be trusted?

That's where certificate authority, or CA comes in.

CAS are trusted organizations that issue and sign digital certificates after verifying the identity

of the requester.

So when your browser sees a certificate, it checks.

Was it issued by a trusted CA?

Yes.

Then it checks.

Is the certificate still valid?

Yes.

And then it checks.

Does the digital signature match?

Yes.

Now, these certificates form a chain of trust from the website certificate up to the intermediate certificate.

And finally to the root certificate trusted by your system or browser.

So this public key infrastructure ensures that whatever key you are using for the asymmetric encryption

during TLS handshake is actually being issued by a trusted authority.

By using the proper certificate authorities.

Also, these pkis enables digital signatures where someone can sign data using their private key, and

anyone with the public key can verify it wasn't tampered or not.

So in short, PCA is what makes things like Https secure.

Email software updates.

All of these things trustworthy and verifiable on the internet.

Now let's talk about securing something at the heart of modern systems.

Our APIs.

APIs are often the front door to our systems, data and functionality, so they need to be treated as

high value assets.

So first and foremost, always use Https for all API traffic.

This ensures that encryption in transit and it protects against the eavesdropping or man in the middle

attack.

Plain HTTP is never never, never acceptable in production environments.

Next, always use authentication and authorization.

Most APIs today use tokens such as JWT tokens or OAuth tokens to validate user's identity and permission.

These tokens should be securely signed and verified on every request.

Beyond the basic things, consider additional layers of defense in your APIs like rate limiting.

Why?

To prevent abuse and denial of service attacks.

IP whitelisting to restrict services to known and trusted clients only.

Then there is something called as manual TLS also.

This is for highly sensitive internal APIs where both client and server verify each other's identity

using certificates.

So if you use all these techniques together to create a defense in depth strategy, making your APIs

resilient not just to casual misuse, but to targeted attacks as well.

So in short, APIs are powerful, but with great power comes the need for great security control.

So be aware of that.

Now let's look at a few important interview questions related to this topic.

So these questions are not just for theory.

They often show up in the system design interviews also.

Well, the good news is you should be able to answer all of them using whatever we have covered in this

lecture so far.

Also, I have included a PDF with detailed answers in the resources section of this lecture.

Now let's bring it all together and look at the key takeaways and best practices from this lecture.

First, make sure your encrypting data in both places at rest in transit.

What is at rest?

Data stored in databases.

Disk and backup.

What is data in transit?

Data that is moving across the network via Https.

Second, for handling passwords, don't rely on encryption.

Use hashing with a unique salt per user.

This makes it much harder for the attackers to crack passwords, even if they get access to your database.

Third, lean on proven infrastructure for secure communication.

Always use TLS and Https for every API and web service.

Also, trust in the public key infrastructure and digital certificates for verifying identity and encrypting

traffic.

And finally harden your API.

That means enforce authentication using tokens.

Protect against abuse with the use of rate limiting, IP filtering, and use things like manual TLS.

Following all these practices doesn't just prevent breaches, it also helps build trust with the users

staying compliant with regulations and keeps your system resilient.

So that brings an end to this lecture.

What is next?

Next lecture we will zoom out and look at the broader landscape of network and infrastructure security,

where we will try to explore firewalls, VPCs, VPNs, and how to secure your cloud environments end

to end.

So I will see you in the next one.
