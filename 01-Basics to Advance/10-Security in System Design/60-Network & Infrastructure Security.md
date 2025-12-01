Hello and welcome to today's lecture on network and infrastructure security.

In this lecture, we will be covering key security principles and practices to safeguard the critical

component of your system architecture.

By the end of this lecture, you will have a solid understanding of how to design and implement security

measures for your network and infrastructure to ensure robust protection in your systems.

Just a disclaimer.

Network and infrastructure security is a vast topic, so we will not be covering everything in detail,

but rather we will be looking at everything that is required briefly so that you will have an idea on

what all to actually keep in mind when you are doing the actual system design.

So let's get started.

So network security is critical in today's landscape due to various external factors and internal threats.

So let's start with understanding why network security actually matters.

So first is because of the external threats.

What kind of external threats?

Well, DDoS attacks could be there that could overwhelm the service and cause downtime.

Intrusion attempts could be there where hackers breach the network to steal data or disrupt your operation.

There could be IP spoofing where attackers fake IP addresses to bypass security measures.

So all these are the examples of external risk.

Other than that, internal risks are also there.

And internal risks are also as dangerous as the external ones.

Internal risks like misconfigurations on your firewalls, like you keep some ports open accidentally,

that could be a problem.

Then there could be this thing called lateral movement, where attackers move within the network after

breaching one area of your network, and this lateral movement can actually lead to larger compromises.

Since the rise of cloud native technologies has expanded the attack surface nowadays.

They introduced new security challenges that require securing not just the perimeter, but also the

internal systems and data flows.

So network security is the key to reliability and user trust.

A secure network maintains operations and build confidence, ensuring that your users are feeling safe.

So keep in mind network security is all about protecting your infrastructure, ensuring your business

continuity, and earning user trust.

So let's start with two essential components of network security firewalls and reverse proxies.

So what are firewalls?

Firewalls control and filter incoming and outgoing traffic based on IPS ports and protocols.

So network based firewalls protect entire network at the entry point.

Then host based firewall secure individual devices or servers.

And then we have cloud based firewalls that are tailored for cloud environment and scale to protect

cloud resources.

Why is firewall important?

Firewall will ensure that only legitimate traffic reaches internal system and blocking all the malicious

access.

So firewalls are very, very important.

Then we have something called reverse proxy.

So a reverse proxy is something that sits between user and the back end servers.

And it is primarily responsible for routing traffic through itself instead of allowing direct access

to the server resources.

So what it does is it masks the back end identities and thus adding a security layer by hiding servers

from the internet.

So servers are actually not visible directly on the internet, but the servers are sitting behind a

reverse proxy.

How does this help?

Well, it mitigates DDoS attacks.

It can distribute traffic.

It can often offer load balancing, SSL termination, and functionalities like caching.

So there are some reverse proxies like nginx that can be used very easily.

So to summarize, firewalls filter traffic at the perimeter while reverse proxies route traffic securely

and enhance their back end protection.

Now there are few techniques for protecting your API.

So let's cover three key techniques for protecting API's and back end systems.

Let's start with rate limiting.

What is rate limiting?

Rate limiting actually controls how many requests a user or an IP address can make within a given time.

For example, 100 requests per minute is allowed.

It prevents DDoS attacks, brute force attempts, and misuse by bots or clients by limiting excessive

traffic to your servers.

Then there is this notion of throttling.

Throttling slows down request processing under high load, allowing the system to handle traffic without

crashing.

So unlike rate limiting, it reduces the speed rather than the volume of request, so that we can ensure

the continued operation even when there are traffic spikes.

Then we have IP filtering.

IP filtering allows or blocks.

List of control access based on IP addresses, meaning it will keep a whitelist of IPS or blacklist

of IPS and only whitelisted IPS will be allowed.

It will allow only permitted trusted IPS while blocking the malicious IPS.

So all these techniques rate limiting, throttling and IP filtering help to protect your APIs from abuse.

It can handle traffic spikes, and it can maintain system performance and security.

Now let's explore network segmentation and isolation.

A key practice for enhancing security.

So what is network segmentation?

Well, network segmentation splits your network into zones or subnets to control flow and reduce lateral

movement in case of a breach.

So what it means is that multiple parts of your system will be in isolated networks, so that if one

part of the system gets compromised, the little movement to another part of the system is not possible.

How can we do that?

So there are many ways.

So first is that we can set up DMZ, DMZ or demilitarized zones for our public facing services like

web servers and all.

Then we can actually establish a private internal network for business applications and critical systems.

Then we can have a separate database zone to isolate our sensitive databases.

So by creating these zones you limit lateral movement.

If one part is compromised the attacker cannot easily access the entire infrastructure.

So there are multiple tools that we can use to implement the network segmentations.

And how will these segments communicate.

Well we use firewalls to control traffic between these separate network zones.

We will divide these networks into subnets for granular control.

And then we use firewall rules to make the communication between these separate zones possible.

Now in cloud environments segmentation is just as critical because um we in cloud what happens is we

create virtual private clouds to create isolated networks.

We set up security groups, which acts as firewalls for individual instances.

So this is something that is very cloud specific.

So still we are doing the same thing.

We are creating separate zones, but we are using VPCs and security groups to actually isolate the network

for different parts of our system.

Also there is something called as network access control list NaCl.

This controls traffic at the subnet level.

So if you even want to control the traffic at the subnet level, you can use Nacls to do that.

So in short, network segmentation and isolation are essential for minimizing risks and improving security

because by doing this we are prohibiting the lateral movement of a compromise even if one part of the

system is compromised.

Now there is this zero trust security model which is nowadays gaining significant adoption.

So what is this zero trust security model?

Well, the core principle of zero trust is never trust.

Always verify.

That's it.

No device, no user, no request is automatically trusted, even if it is within your network.

So how it works?

Let's see how it works.

So every request must be authenticated and authorized regardless of its origin, which contrasts with

the traditional perimeter security model that trust users once they are inside the network.

Now in this model, we will never trust.

We will always authenticate and authorize every request.

Now, in case of microservices.

Microservices also implement zero trust by mutual TLS authentication, so every service need to authenticate

other service using TLS, so there will always be secure communication between your microservices.

Then we implement strict access control.

Users and devices are granted the least privilege so that they can only access the data and resources

they need, nothing else.

This is called the principle of least privilege.

Then we do continuous verification even within the internal network.

Every request is authenticated and verified, ensuring that the access to all the resources is secure.

That is what we call continuous verification.

So where does zero trust apply?

I think zero trust applies everywhere.

Zero trust applies to both on premises infrastructure, cloud infrastructure and any other place ensuring

security across all layers and communication channels.

So in summary, zero trust minimizes the risk of unauthorized access, data breach, and lateral movement

within your network by constantly verifying and enforcing strict access controls.

Now how to secure our cloud environments.

Securing cloud environments is also crucial as nowadays organizations are increasingly moving toward

the cloud infrastructure.

So at the heart of cloud security is this shared responsibility model.

What is that?

Well, the cloud service provider secures the cloud infrastructure.

What is that hardware network and data center.

The cloud service provider will secure that part, but the customer is responsible for securing their

data, application and user access for everything they are hosting on the cloud platform.

So that is the shared responsibility model.

There are some key aspects of this cloud based security.

One is that every cloud environment provide identity and access management called IAM.

We should use IAM to control user identities, roles and permissions.

As simple as that, so that we can enforce least privilege access and multifactor authentication for

giving access to any of the resource to any of the user.

So use IAM for ensuring the least privilege access and configure multifactor authentication even within

that, so that you get complete security.

Second, encryption always encrypt.

Encryption is very essential for protecting sensitive data in the cloud.

Encrypt everything in storage.

Encrypt everything that is at rest.

Encrypt everything that is in transit.

Even the logs should be encrypted.

Then third thing is audit logging.

Audit logging means you keep a log of every operation that is being performed in your cloud infrastructure.

So it will help you detect security incidents and meeting the compliance requirements.

So we should be continuously assessing our cloud configurations against security best practices.

So there is something called cloud security posture management tools.

They are very helpful in continuously assessing the configurations that we have in our cloud against

the security best practices.

They are very useful in identifying misconfiguration and vulnerabilities before they can be exploited.

So in summary securing cloud environments requires managing shared responsibilities.

Vendors will control the security of hardware and infrastructure.

You will control the security of everything that you are hosting there and the networks that you are

configuring there.

We need to ensure proper identity access management.

We need to have encryption in place.

We need to put audit logging in place.

And we should continuously be using Cspm tools to ensure that we are monitoring all our configuration.

All this help us to protect the infrastructure, data and applications that we are hosting in our cloud

and thus minimizing the risks and keeping our cloud resources secure.

Now there is this world of serverless and containerized workloads still in the cloud.

So how are we going to secure them?

Well, let's look at a few key aspects of securing serverless and containerized workloads.

Well, we talked about IAM roles.

So for serverless use IAM roles you assign unique minimal permissions to each function with the least

privilege principle.

Least privilege principle is one of the most important principle.

So every instance should have least principals using the IAM roles.

Also set the proper timeouts and execution limits to prevent resource exhaustion.

Then always try to use API gateways.

API gateways will help you to secure API access with authentication, authorization, rate limiting,

and IP filtering everything.

So if you follow these few things like IAM roles, timeouts, API gateways, serverless instances,

and services will be secured.

What about Containerized workload.

Well, to keep your containerized workload secure, the first thing is that doing regular image scanning

regularly scan your container images for vulnerabilities.

There are many tools available to do scanning, like clear, so you can use them.

Then there is runtime hardening.

You limit the container privileges, use Non-root users and secure file systems.

This in theory is very similar to the principle of least privilege.

Non-root users should be used and containers should have minimal privileges.

This will ensure that containers only have the minimum resources they need to reduce the attack surface.

So since they have the minimum resource access, the attack surface will be very minimal and even if

something gets compromised, the lateral movement will not be very easy.

So in both serverless and container environments, the goal is to minimize risk by controlling access,

monitoring the vulnerabilities, and applying the security hardening measures continuously.

It's an ongoing practice.

It's not a one time thing.

You have to keep doing it day by day.

Now let's discuss very briefly about security in microservices.

In microservices, it's all about service to service authentication.

So first thing is we should be using tokens for secure authentication between services.

It could be JWT tokens or TLS tokens.

JWT will allow services to verify each other's identity, while the TLS ensures that both parties authenticate

each other using certificates.

This is the first thing that we should be doing.

Second is we should be using API gateway always.

The API gateway should be configured to handle key security functions like validation, authentication,

read limiting like validation.

What will it do?

It will ensure that only valid requests reach the microservices.

Authentication will verify the JWT tokens.

Rate limiting will protect against the abuse by limiting the number of requests per user or per IP whatever

model we are configuring it to.

Then finally, using something like a service mesh, service mesh provides a fine grained control over

service to service communication.

What it does is that it enables TLS encryption and implement security policies like authentication,

access control, and traffic monitoring.

So if you want, you can use service mesh also for additional security for your service to service communication.

In short, when we have microservices architecture, it is crucial to secure inter service communication.

So always validate your API traffic.

Always manage policies effectively using tools like API gateways and service meshes.

Now let's look at some of the common security vulnerabilities based on OWASp top ten.

We will not go into much detail, but I highly recommend going through OWASp top ten in detail, because

this is the holy grail of understanding the common vulnerabilities and how to mitigate them.

So let's briefly look at some of them.

First is injection, where attackers exploit vulnerabilities in the input fields in our application

to run the malicious code.

Then there is something called as broken authentication.

Weak authentication mechanism will allow attackers to impersonate any other user.

Then sensitive data exposure.

Well, failing to encrypt sensitive data will leave it vulnerable to leaks.

Then security misconfiguration, poor configuration or default values left like that can expose systems

to attacks.

Cross-site scripting malicious scripts are injected into web pages and thus compromising the user's

data.

Then we have CSRF cross-site request forgery, where an attacker tricks a user into making unwanted

requests to some other site rather than the original site.

Then we have Ssrf also, which is server side request forgery.

In this, somebody is trying to exploit a server side functionality to make unauthorized requests on

behalf of the attacker.

That is also possible.

So all these vulnerabilities are highly relevant in both web application and in microservices architecture.

The key is awareness and that is why I am putting this slide here.

Identify these risks early and implement mitigation strategies like input validation, encryption and

strong authentication to protect your system.

But again highly recommended to go through OWASp top ten and how to protect against these common vulnerabilities.

Please go through it once.

Now we have some interview questions visible on the screen.

These are the kind of questions you might get in the system design or infrastructure security interview.

They test your practical understanding and how you think about security in depth.

Everything that we have covered so far, you should be able to answer these questions.

Also, a reference answer PDF is attached in the resource section of this lecture.

Now before we conclude, let's look at the summary best practices and key takeaways of this lecture.

First, use firewalls and segment your network to protect different zones of your system infrastructure.

This will help to minimize the lateral movement within your infrastructure.

Second, always apply a rate limiting IP filtering and try to use reverse proxy to prevent abuse of

your infrastructure and ensure that traffic is properly routed.

Then embrace zero trust model by verifying every request, whether it is internal or external, and

encrypt everything.

Data at rest.

Data in transit.

Also secure your APIs.

Secure your services.

Secure your containers.

Secure your serverless functions by implementing strong authentication, encryption, and proper access

control.

Then one recommendation is stay alert to the OWASp top ten vulnerabilities and continually monitor your

system for vulnerabilities.

And by following these best practices, you will significantly improve the security of your system.

That brings us to the end of this lecture on network and infrastructure security.

This was a 30,000 foot overview of this topic because this topic is very deep and vast, but I want

to keep all these things on top of your mind so that you are aware about all these things.

And whenever you have to implement something related to security, you know what all you have to go

deep in.

So that brings into this lecture what is next?

Next we will try to summarize this section.

See how all these things come together.

And look at the recap of how to design secure distributed systems.

So I will see you in the next one.
