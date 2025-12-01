Hello everyone, and welcome to section ten of this course on Mastering System Design.

In this section we are going to talk about security in system design.

We are going to explore the most critical yet often overlooked pillars of system architecture.

And that is security.

So let's dive in.

So here is what we will cover in this section on security.

First we will start with Introduction to security in System design.

We will begin with the fundamentals what security means and distributed systems.

The CIA triad threat models and attack vectors.

Then we will look at authentication and authorization.

We will discuss how to verify users and control access using techniques like OAuth, JWT and role based

access control.

Then we will dive into data protection and secure communication.

We will learn how to protect data both at rest and in transit, including encryption, TLS and certificate

management.

Then we will look at network and infrastructure security.

We will look at securing your infrastructure with firewalls, VPCs, zero trust models and DDoS mitigation.

Then we will summarize and see how all these things fit together with best practices, common pitfalls,

and how to apply what we have learned in this section in the final lecture.

So let's get started with the first lecture of this section.

And this section is all about Introduction to Security in System Design.

In this lecture we will lay the groundwork for thinking about security from a system design perspective.

So let's get started.

So let's start with simple but crucial question.

Why does security matter in system design.

Well, security is often treated as a non-functional requirement, meaning it doesn't directly affect

what your system does, but it deeply impacts how reliably and safely your system does it.

So at its core, security builds user trust.

If users don't feel safe sharing data with your platform, they will simply not use it.

It also ensures that data protection, both from external threats and accidental leaks, and it plays

a huge role in maintaining system reliability.

Because the system under attack is a system that can't perform well.

We have all seen high profile real world examples of security breaches like the Equifax breach, Facebook

data structure, exposure, and many, many more where the lack of security design led to massive financial

and reputational damage.

So the bottom line is security is not optional.

It's a core pillar of modern system architecture.

Now, in a distributed system, security becomes more complex and more critical.

Why?

Well, unlike monolithic systems, distributed architectures have more components, more nodes, more

entry points.

As a result, more potential vulnerabilities.

So what exactly does security mean in the context of distributed systems?

Well, it means thinking holistically about few things.

What are those things?

First, protecting your data in transit and at rest using encryption technologies.

Second, implementing robust authentication and authorization to ensure only the right users and services

can access the right resource, then we should be exposing secure APIs and endpoints with rate limiting,

validation and protection from common exploits and finally securing the node themselves through firewalls,

network segmentation and monitoring.

To guard against both internal and external threats.

In short, security in distributed system means defense in depth, securing every layer from the request

all the way to the infrastructure.

Now let's break down this, uh, CIA triad.

I mean, people call it CIA triad, which is the core framework for thinking about security in system

design.

So what does the CIA stand for first?

See, for confidentiality, this is all about preventing unauthorized access to sensitive data.

It ensures that only authorized users and services can view or modify specific information.

Encryption, both at rest and in transit plays a very key role here.

Second, I is for integrity.

This ensures that data cannot be tampered or altered by unauthorized users.

Techniques like hashing and digital signatures help ensure data stays intact and unmodified, even in

transit.

Lastly, a for availability.

This means ensuring that your system and data are always available and accessible to users when they

need it.

This requires robust infrastructure redundancy.

Failover mechanism and DDoS protection are essential to maintain availability of a system.

Together, these 3CIA these three principles forms the backbone of any secure system.

Security isn't just about stopping attackers.

It's also about ensuring data is accurate, protected and accessible at all the time.

Now, when we want to design secure systems, we need to understand who our adversaries are.

And that's where something called threat model is going to help us.

What is a threat model?

Threat modeling is a process of identifying potential attackers, understanding their motivations,

and analyzing how they might try to exploit your system.

So when we are performing threat model, consider the following things.

First, we need to think that we need to consider attack surface.

What are the exposed parts of your system that attacker can target?

These could be APIs, user interfaces, or network access points.

Second thing is entry points.

Where can attacker gain access?

These might be vulnerabilities in your system.

Third party integration or even some errors in the user facing APIs or UI.

Then we need to consider assets to protect what assets to protect?

What data or resource needs to be protected the most.

This might include user data, financial transactions, or intellectual property that your application

might have.

One very powerful tool for threat modeling is trade Model, which categorizes threats into six main

types.

So Stride is an acronym.

So let's go through each letter one by one.

So spoofing.

Spoofing is impersonating legitimate users or services then.

Tampering.

Tampering is altering data or code in unauthorized ways.

Then repudiation, which is denying an action or event that happened in the system.

Then we have information disclosure exposing sensitive data to unauthorized users.

Then we have denial of service.

Disrupting access to the system or making it unavailable is denial of service.

Then E for elevation of privilege.

This is gaining unauthorized access to higher level resource or functionality.

So we looked at threat modeling.

And one of the tools to perform threat modeling is stride model.

By understanding these threats and systematically evaluating how they apply to your system, you can

design with these risks in mind and build stronger defenses for your system.

Now let's explore how attackers typically gain access to the system.

So these are known as attack vectors.

What are these attack vectors.

So the first one is insecure APIs.

APIs are often the first point of attack if not properly secured.

Attacker can exploit them through injection attacks, lack of rate limiting or even exposed sensitive

data.

Securing API with proper authentication authorization input validation is very critical.

Second is misconfigured server.

Many, many breaches occur due to servers that are improperly configured, leaving sensitive information

exposed.

This could involve default credentials and patch software.

Unsecured cloud configuration.

So we should be doing regular audits and configuration management practices to reduce this risk.

Then we have poor Authentication, weak or missing authentication mechanism.

Open the door for attackers in secure password storage, lack of multi-factor authentication or weak

session management.

All these things can lead to unauthorized access.

So what to do?

Well, implementing strong authentication and token based systems like OAuth or JWT can greatly improve

the security of our system.

Then there is one more.

Open ports or services?

Unnecessary services on open ports can be a vulnerability on your servers.

These open ports could be exploited for remote code execution or unauthorized access.

Use firewalls, network segmentation, and close all these unused ports so that you can significantly

reduce these risk on your infrastructure.

So by identifying and securing these common attack vectors.

You strengthen your defenses and make it much harder for attackers to infiltrate your system.

Now this is a very loaded slide, but these are some of the most common attacks that can compromise

your system security.

And understanding these will help you design with defense in mind.

So let's go through each one of them one by one.

Let's start with DDoS which is distributed denial of service a DDoS attack.

What it does is it floods your system with massive amounts of traffic to overwhelm and disrupt your

service.

What is its primary target?

The primary target is availability because if your system is busy, your availability will take a hit.

How can we mitigate it?

Well, rate limiting is one option that can be used to mitigate this problem.

There is also failover strategies.

So what could happen is that if one part of your system is getting overloaded, you can actually failover

to another part of system, or you can load distribute to another part of the system.

That can give us some amount of availability for other users.

Then we have this, uh, attack called man in the middle.

In a man in the middle attack, the attacker intercepts communication between two parties, often to

steal sensitive data or alter the message.

This impacts confidentiality and integrity.

How can we protect it?

Well, use Https with TLS encryption for secure communication.

Or you can do certificate pinning.

It will ensure that you are communicating with trusted servers.

There is also this possibility that VPNs can also encrypt communication over untrusted networks.

So we can do that also.

Then we have this attack called injection attack or SQL injection attack.

To be precise, injection attack occurs when attackers send malicious inputs that get executed by the

system, allowing them to perform unintended operations like altering or stealing data.

This affects data integrity and confidentiality.

There are few mitigation strategies here.

We can do input validations to ensure that only safe data is processed.

We can always use parameterized queries to prevent malicious SQL code execution, and we can use web

application firewalls that can detect and block malicious input.

Then we have spoofing attacks.

Spoofing involves an attacker Impersonating another user or system, such as IP spoofing, email spoofing,

or DNS spoofing.

These attacks aim to bypass authentication or redirect traffic.

So how can we defend against spoofing?

Well, first is we can use multi-factor authentication to ensure that attackers cannot simply rely on

stolen credentials.

Then we can also use token based authentication to verify systems.

Well, IP whitelisting is also one way to allow trusted sources to access sensitive information.

So these are four very common attacks that can happen on your system.

Understanding these common attack types and their mitigation strategies is essential for designing secure

systems that can stand up to malicious actions.

Now security must be integrated throughout the entire software development life cycle, not just something

that you do at the end of your software development life cycle.

This approach is often called shift left, meaning we prioritize security early in the process instead

of treating it as an afterthought.

So let's try to break down security in each phase of SDLC.

What exactly you can do in each phase of your software development life cycle?

Let's start with requirements.

During the requirement phase, start with threat modeling.

This is where you identify potential threats, vulnerabilities, and risks to your system before even

the development begins.

Understanding these risks help in making informed design decisions.

Then, in design phase, you will focus on secure architecture.

You want to build systems that are resilient to attacks, Tags employing principles like least privileges,

defense in depth, and segregation of duties.

Then during development, secure coding practices are crucial during development cycle.

This involves writing code that avoids vulnerabilities like SQL injection, cross site scripting, buffer

overflows.

Also, make sure that code reviews static code analysis tools and developer training.

All these things are actually looking for security related vulnerabilities in code two.

Then in testing, it's time to test your security tool.

Use techniques like fuzzing, where you input random or unexpected data to find vulnerabilities, do

penetration testing, do dynamic analysis, and do other kind of testing all this to uncover any weaknesses

in the system, then deployment.

When we are deploying, secret management becomes very essential.

This involves securing credentials, API keys, and sensitive configurations.

Use tools like keywords, secret managers, or environment variables.

Ensure that secrets are safely stored and are not exposed in your code base.

Then maintenance.

So even after deployment, security does not stop.

Patch management is key to keeping your system secure over time.

Regularly apply security patches and updates to address newly discovered vulnerabilities and threats

on your servers.

So by embedding security into every phase of SDLC, you make your system more resilient to threats and

ensure that security is not an afterthought, but a continuous priority throughout the life cycle of

software development.

Now, to build truly secure systems, there are several best practices that should be consistently followed

throughout the development and deployment process.

So let's go through them briefly first.

Adopt security by design.

We just talked about it.

This means incorporating security into your system architecture from the very beginning rather than

adding it later.

Security should be an integral part of every decision, whether you are choosing a technology or whether

you are defining workflows.

Second, use encryption to protect your data.

Transport Layer Security, or TLS, is essential for securing data in transit, while encryption at

rest ensures that your data that is stored is also safe.

So even if an attacker gains access to the storage system or to the data which is in transit, it is

always safe.

We need to always ensure sensitive information is encrypted during transfer and while stored.

Then harden your infrastructure by implementing security measures like firewalls and virtual private

clouds.

These act as barrier to unauthorized access and help you isolate your critical systems from the outside

world.

Security groups and proper network segmentation are key to minimizing your attack surfaces.

Then about user inputs.

Validate all user inputs.

Sanitize all user inputs.

Never trust user inputs.

That is the key input validation ensures that any data coming into your system is safe, and sanitizing

output prevents malicious data from escaping into the responses that could lead to attacks like cross-site

site scripting or injection, and then finally monitor and log all the activities of your system.

Real time monitoring allows you to detect suspicious activity early, while comprehensive logging provides

valuable forensic evidence if a breach occurs.

Make sure logs are stored securely and are accessible for analysis whenever they are needed.

These are some of the best practices, and by adopting these best practices, you can significantly

improve the security posture of your system and protect it against a wide range of potential threats.

Now, here are a few commonly asked interview questions focused on system security.

These questions are important because they test your ability to think about security from an architectural

standpoint, not just at the code level, but across the entire system's life cycle.

So whatever we have covered so far, you should be able to answer these questions.

Also, I have attached the PDF with the answers along with this lecture, so you can refer it if you

want.

Now, before wrapping up, let's look at the summary and key takeaways of this lecture.

We started with looking at security and how security is an ongoing process, not a one time task.

It requires continuous vigilance and updates as threats are evolving over time.

Then we looked at CIA triad, CIA confidentiality, integrity, and availability.

These are the foundational practices of securing your system.

Then we looked at how identifying and addressing threat vectors can help us know your attacker.

It can help you to identify what can exploit your system and take proactive steps to defend against

them.

Finally, build secure systems from the ground up.

Security must be integrated at every step of the development lifecycle, starting from design and continue

through maintenance.

We should keep these principles in mind as we continue our journey in system design.

Because securing our systems is not just a checkbox, but it is an integral part of building reliable,

trustworthy, and good architectural software.

That's it for this introductory lecture on security and system design.

What's next?

In the next lecture, we will dive into authentication and authorization.

Two critical pillars of system security.

These concepts are essential for ensuring that only the right users can access your system and data.

So I will see you in the next one.
