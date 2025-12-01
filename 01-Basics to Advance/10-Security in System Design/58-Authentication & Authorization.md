Hello everyone, and welcome to this lecture on authentication and Authorization.

In this lecture, we will dive into two of the most fundamental building blocks of secure system design.

Whether you are designing internal enterprise application or global scale consumer platforms.

Understanding how systems verify identity and control access is absolutely critical.

So let's get started.

So let's start with the definition.

So these two terms are often confused but fundamentally different authentication and authorization.

So let's look at each of them one by one.

Authentication.

Authentication is about verifying who the user is.

It answers the question are you really who you claim to be?

Think about login password biometrics or multifactor authentication.

On the other hand, authorization comes after authentication, it determines what the authenticated

user is allowed to do, like accessing an admin dashboard, downloading a file, or modifying a resource

whether you are allowed to do all these functionalities or not.

So a simple way to remember is authentication is about identity, who you are and authorization is about

permission.

What you can do.

And you need both to design a secure and well controlled system.

Now let's look at some of the most widely used authentication methods in modern software.

So first we have basic authentication the simplest form where the username and password are sent with

each request.

It is very easy to implement but insecure without Https and it is not ideal for production use.

Then we have OAuth, a very powerful protocol for delegated access.

What it means is that it allows third party apps to access user data without exposing credentials.

For example, when you login to a service using your Google or Facebook account, your Google and Facebook

accounts take care of verifying your identity.

That third party app will never get to know what is your username and password that is OAuth in action.

So there is something called as OpenID connect.

Also, what is OpenID connect?

OpenID connect is something that is built on top of OAuth.

So we have OpenID connect where we are adding an identity layer on top of OAuth two.

So this is often used in single sign on where a user can authenticate once and access multiple services.

Then we have JWT, JSON web tokens.

So these are compact stateless tokens which are used widely in modern APIs.

A server generates a signed Sign token.

After the login and the client includes it in the header for each request, there is no need to maintain

server side session state explicitly.

So to summarize, basic authentication is where we are sending username and password with each request.

It should be done over https.

OAuth two and OpenID is using third party identity providers like Google and Facebook, so that the

actual application need not know about your username and credentials.

And these third party providers, like Google and Facebook will provide the authentication on your behalf.

And then third is JSON web tokens, where the token contains information about your state and credentials.

Each of these methods have trade offs around complexity, security, and usability.

You should choose the right one depending on what our application needs are.

Now, since session based and token based authentication are the two most popular approaches.

We are going to compare these two.

So let's start with the session based authentication.

In session based authentication the server keeps track of the user session.

So after login a session ID is stored on the server.

And what we do is that we will send that session ID back to the client.

The client will keep it in form of a cookie.

And there will be some memory space on the server which will keep the user's session information there.

Now whenever a client is making a request, it will send that session ID back to the server.

The server will look up that session to verify whether the user is authenticated or not.

So what are the pros of this approach?

Well, first it is very easy to implement and it works very well with the traditional monolithic web

applications.

But there is a problem in distributed systems.

Session data must be shared across Server.

Because if you have a server infrastructure which is scaled out, that means that you have multiple

servers handling the load.

Now we know that the session information was stored on the server memory, but now you have multiple

servers, so you never know which server has the session stored and you never know.

Next request will go to which server.

So it adds an extra layer of complexity and it can affect the scalability of your system.

There are ways to circumvent it by moving the session memory out and keeping it in a centralized cache

like Reddis, but that's the complexity part.

It does add some complexity in terms of scalability.

Compare this with token based authentication like in JWT.

This is completely stateless.

After login, the server returns a signed token that the client will have to include in every request

onwards.

The server does not need to store any session data, all the information that is required to identify

the user is in the token on every request.

The server will just verify the token, extract the information and use it for performing the operation.

What are the pros of this approach?

This approach scales easily across multiple services, especially in case of microservices, where we

have decoupled authentication from the backend services, where each service is actually not authenticating

again and again, but the authentication is separate from all the microservices.

What are the cons of this?

Well, you need to actually be very careful in token handling the token securely, because if the token

is leaked then you have a problem.

So we have to prevent theft, manage expiry and avoid leaking sensitive data in our token very cautiously.

So choosing between them.

Between session based authentication or token based authentication depends on your application architecture.

For modern APIs and distributed systems, token based authentication is often a better choice.

Now we have access control model.

So so far we have been talking about the authentication.

But now once the user is authenticated, the next step is deciding what they are allowed to do in our

system, meaning the authorization part.

That's where the access control model comes in.

So first we have Rbac role based access control.

In this model the permissions are tied to role of the user.

User can have roles like admin editor, viewer and these roles determine what the user can access.

It is a simple and scalable approach, especially for the teams where we have clear role definitions,

especially for the users where we can assign roles very clearly, but it lacks the flexibility when

more granular control is needed.

So what to do if more granular control is needed?

Well, we have attribute based access control.

This model uses users attributes like department project clearance level to decide what level of access

this user can have.

So it is more fine grained and powered for complex organizations.

And compared to Rbac it has more granular control.

It provides more granular control, but it adds extra layer of complexities.

The policies that we put in to look at the attributes and define what the user can perform, they can

become harder to manage.

So what next?

We have something called as DAC.

Discretionary access control where the owner of the resource decide who can access it.

This is commonly seen in file system where users can grant or revoke permissions.

Then we have Mac mandatory Access control.

Here, access decisions are enforced by a central authority based on strict security policies.

This is very common in military or government systems where data classification is very crucial.

Each model has its own use case, and in practice system often combine multiple approaches for having

layered security.

But from the end user application perspective, or if you are working with a microservices architecture,

most probably you will be working with role based access control or attribute based access control.

Now let's talk about improving the user experience through single sign on and identity federation.

What are these three things?

Well single sign on allows the user to log in once and gain access to multiple applications or systems

without needing to re-enter credentials for each one.

This means fewer passwords to remember, less friction, and a very smooth user journey, especially

in case of enterprise environment or SaaS platforms where you have multiple services available to you

and each service wants you to log in well.

So single sign on is going to help you in a way where you log into only one service, and each time

you are going to the other service, it will actually take your account information from the previous

one and seamlessly let you access the second service also.

Then what is Identity Federation?

Identity Federation takes this concept of single sign on a step further.

What it does is that it allows authentication across different organizations or domains by trusting

external identity providers like Google, Facebook or Microsoft.

We talked about it briefly when we talked about OAuth two and OpenID.

So instead of maintaining your own user store, your system can trust these providers to authenticate

users securely.

So Identity Federation is using an external identity provider.

Typically it works using OAuth two an OpenID.

How does this help?

This helps to reduce the amount of, uh, user IDs and passwords that the user need to create for each

and every website.

The account creation friction is not there, because user does not have to create, account and account

for every separate website.

So offloading the authentication responsibility to a trusted identity provider is the key here.

So in short, single sign on improves usability within a system and identity federation.

Extend that trust across systems, making both essential tools in modern authentication design, Single

Sign on and identity federation.

Now here are some common interview questions based on the concept we have just covered.

These questions are important because they will not only test your understanding of core security principles,

but also your ability to apply them in the real world system.

You should be able to answer these questions based on whatever we have covered so far, but I have also

attached the answers PDF along with this lecture.

Just in case you want to refer, you can actually use that PDF.

Now let's quickly look at the summary and key takeaways of today's lecture.

First we discussed the key distinction between authentication and authorization.

Authentication is about verifying who the user is while authorization is about defining what the user

is allowed to do.

Then we looked at some common authentication methods, from simple basic auth to more secure and scalable

approaches like Oauth2, OpenID, and JWT tokens.

We also explored access control models, including role based access controls, attribute based policies,

and DSC and MSC and how to use them depending on the level of control and flexibility that we need.

Then we covered Single Sign On and Identity Federation, two key mechanisms that simplify authentication

across multiple systems and improve user experience.

So the bottom line is security starts with identity, but it does not stop there.

So let's move forward.

Building on top of the foundation that we have learned in the first two lectures, from our next lecture,

we will dive deep into data protection and secure communication.

In this lecture, we will talk about how to keep data safe, both in transit and in rest.

So I will see you in the next one.
