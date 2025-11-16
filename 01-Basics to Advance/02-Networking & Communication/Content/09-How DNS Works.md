Hello everyone, and welcome back to this next lecture in the series of Mastering System Design.

In this lecture we will see how DNS works.

Today we will dive into the fascinating world of domain name systems.

One of the fundamental building blocks of the internet is Domain Name Systems.

We will explore how domain names get translated into IP addresses, how caching improves performance,

and why DNS plays a crucial role in large scale systems.

By the end of this session, you will not only understand the DNS resolution process, but also gain

insights into the optimization and security considerations.

It's an essential topic for both system design and technical interviews.

So let's get started.

Before we dive into the technical details, let's start with a simple question what is DNS or domain

Name System?

DNS is often called as the phone book of internet.

Just like we store phone numbers under contact names in our phones, DNS help us access websites using

human readable domain names instead of complicated IP addresses.

For example, when you type google.com in your browser, your computer doesn't actually understand google.com.

What it does is it needs an IP address, something like 142.

241.

9078 to locate the Google server, DNS is the one that makes the translation actually happen behind

the scenes.

So why is DNS important first?

Imagine without DNS, we'll have to memorize long string of IP addresses for every website.

Imagine remembering different IP addresses for all these websites that we are accessing on a daily basis.

That will be a nightmare for us.

Second, DNS actually helps to scale the internet efficiently.

Also, the internet consists of billions of devices.

The DNS ensures that they can communicate smoothly by organizing domain names into structured distributed

systems.

In short, DNS is the foundation that keeps the internet user friendly and scalable.

So in the next section, we will explore how exactly this process works.

Now, before we get into the details of how exactly the DNS resolution process works, first try to

understand what all different types of DNS servers are there.

See, if you look at it, we when we talk about DNS, there has to be some servers that is actually

keeping track of these mappings that okay, this name google.com has to resolve to this IP address.

This name Amazon.com has to resort to this IP address.

So essentially we have DNS servers, but there are multiple types of servers.

So let's first try to understand what all types of servers are there.

So the first type of server is called root name server.

These are the top level servers that handle queries for all domain extensions like.com, dot org, dot

net, etc. they don't store the actual domain records, but it direct all the requests to appropriate

second level, which are called TLD name servers.

So if a request for.com comes, it knows to which TLD server to go.

If a request for.org comes, it knows to which TLD name server to go.

If a request for something like dot n comes, it knows to which TLD servers to go.

Then the second level is the TLD name servers.

This is a set of servers where whenever the request reaches the TLD server, it redirects the query

to an authoritative name server.

So the TLD server keep tracks of.

So let's say we have a TLD server for.com.

Search query for google.com reaches this.

Then TLD name servers.

Responsibility is to figure out which actual server has this mapping of google.com to the IP address,

which is the third level called authoritative name servers.

Authoritative name servers are the actual servers that store the DNS records like a records CNAME record

MX record, where they have the mapping for what domain and IP addresses there.

Once a request reaches the authoritative server, it returns the correct IP address to the user.

And then there are final level of servers which are called recursive resolvers.

Recursive resolvers actually handle the DNS queries on behalf of the user, so typically ISP set up

a recursive resolvers at their end, and predominantly their responsibility is to forward the request

to the authoritative name server and also to cache the domain names for whatever requests have been

resolved already, which will provide a little bit of efficiency.

So whenever the user makes a request, we will first check with the recursive resolver server whether

it is there or not.

If not, then we will go to the top and figure out from where this domain name can be resolved, and

then the actual IP address will be returned to the user.

We look at the complete process in detail in a couple of slides.

Now before looking at the complete process, also understand the DNS caching and how it can help in

performance optimization.

So imagine if every time you wanted to call a friend, you had to pick up their number from the directory.

That would be very slow and inefficient.

Instead, if you just save their number in your phone, you just have to dial that contact's information.

DNS caching somehow works in the same way.

So why is caching important first to understand that.

So first thing is that it actually reduces the latency.

Instead of performing the full DNS lookup every time, the cache records allow the devices to resolve

domain names almost instantly.

And second, it also reduces the load on the DNS servers.

Fewer queries means less traffic to the DNS servers, which will improve the overall performance of

the internet.

Now where all this caching can happen.

So DNS caching happens at multiple levels first.

Once you make the request, the request goes all the way to the domain server and it gets resolved and

you open that site in your browser.

So the browser also caches the DNS records.

So the next time you make a request for the same domain, it will look at the browser cache and cache

it there.

Operating system is also caching DNS records.

So there is one more level of caching.

And then finally there are these recursive resolvers cache servers that we talked about.

The ISPs have the DNS resolver caches.

It keeps all the resolved domains in its cache, and it serves all the next requests for all those domains

from that cache.

Only one important thing that we need to understand when we are talking about DNS caching is TTL, which

is called time to live.

It is the expiration timer for the cache record, So every DNS record has a TTL value which determines

how long the cache is valid before it expires.

A short TTL ensures that all the cache records have up to date IP addresses for every domain.

On the contrary, a long one will actually reduces the queries to the DNS server, making it much more

optimal.

But any update in the domain to IP will be delayed.

So in summary, DNS caching significantly improves performance and efficiency.

However, managing time to live values is the key to balancing speed and accuracy.

There has to be some balance between the performance and the accuracy of your records.

Now let's move on to understand the actual domain name resolution process.

Let's say you type google.com in your browser and hit enter.

What happens next?

First, your browser checks its own cache.

If you recently visited Google, your browser may already have the IP address stored, so it can skip

the lookup and load the page instantly.

If your browser cache doesn't have it, maybe the operating system caches there.

So the computer also keeps a local cache of DNS records, which reduces the need for external lookups.

Now let's say the OS also doesn't have it.

Then a query is sent to the local DNS resolver, usually provided by your internet service providers.

This is the first step in reaching out to the broader DNS network, which is outside of your home network.

If the local DNS resolver doesn't have the required domain cache, it reaches out to the root DNS servers.

These are the backbone of the DNS system, redirecting the request to appropriate top level domain servers.

The top level domain name servers like.com, dot org or dot net responds with the details of the authoritative

DNS server, which has the actual record the actual domain to IP mapping.

Then the authoritative DNS server is hit.

It will find what IP is to be sent back for that requested DNS.

It contains the actual IP address for the google.com, so it returns it to the resolver.

Then the local DNS resolver caches it at their ISPs and and send it back to your OS and your browser,

and your OS and browser will cache it, and your browser will then connect to that IP and the website

will load.

All this happens in milliseconds, and thanks to DNS caching, the next time we are visiting, this

process will be even faster.

So that's the complete process of domain name resolution.

Now let's try to understand the importance of DNS in large scale systems.

In small scale applications, DNS simply resolves domain names to IP addresses, but in large scale

system, DNS plays a much bigger role in ensuring reliability, performance, and security for global

applications like Google, Amazon, Netflix.

Downtime is not an option, so DNS based load balancing is the first benefit that we can get.

Instead of pointing all the traffic to a single server, DNS can actually distribute requests across

multiple servers worldwide, preventing the overloading of any single server and ensuring smooth performance.

Second is anycast DNS instead of a single DNS server responding to queries, multiple geographically

distributed servers can handle the DNS resolution request.

This ensures that the users get a response from the nearest server, which will be the fastest server

for them, and it will reduce the latency.

The second important thing about DNS in large scale systems is about DNS failover strategies.

So there are actually two types of DNS servers two categories of DNS servers, let's say primary and

secondary DNS servers.

If the primary DNS server fails, requests are automatically routed to the backup, which will ensure

the continuity of your domain name resolution.

Functionality.

There are health checks and Failovers configured there, so some DNS providers monitor their server

health and automatically redirect traffic to the healthy servers if the primary is not healthy.

If it goes down, it will actually send it to the secondary server automatically.

Then comes content delivery networks.

So DNS helps content delivery networks or CDNs to optimize their performance.

When you visit a website using a CDN, the DNS will redirect you to the nearest server instead of a

central one, for example.

If a user in India accesses a website hosted in New York, a CDN can serve the content from a local

data center in Mumbai, which will reduce the latency and improving load time.

How it happens.

So let's say my CDN is called w ww dot example.com.

So when my domain name resolution happens, the DNS will make sure to resolve it to the nearest server

to load my content nearest in terms of geographically.

And that's how the overall performance is improved.

One thing we need to understand is about the DNS security risks.

DNS is also a target for cyber attacks, so DNS poisoning and cache poisoning attackers.

There is a possibility for attackers to inject fake DNS records directly to the malicious sites.

So instead of the actual IP address, they can actually replace it with a malicious sites IP address.

And the moment you type the domain, they can take you to the malicious website.

DDoS attack on DNS servers are very common.

Attackers flood DNS servers with requests, making websites unreachable.

So if you type a domain name and DNS server is under DDoS attack and you are not able to resolve the

IP address of that particular website, you will never be able to reach that website.

So there are some secure DNS protocols like DNS sec, which will help us verify the authenticity and

prevent the tampering of DNS records.

But the important thing is that we have to consider the DNS security risks whenever we are designing

large scale systems.

In summary, DNS is more than just a lookup service.

It's a key player in performance, scalability, and security.

Now, here are a few interview questions that can come up during an interview related to DNS.

Whatever we have discussed so far, I think you should be able to answer these questions.

Test your understanding of both fundamental concepts and practical application of DNS in the real world

systems.

We won't go through the answers now, but don't worry, I have prepared a PDF with detailed answers

which you can refer to later.

Make sure you go through it and practice these concepts as they are very common in in the in the interviews,

and they often come up in a most of the system design interviews.

So before we wrap up this lecture, let's quickly review the key takeaways from this session.

The first takeaway is that DNS is critical for internet functionality.

It acts as the phonebook of the internet, translating human readable domain names into IP addresses,

enabling seamless connectivity to websites.

Second, DNS caching improves efficiency and reduces latency by storing DNS responses at multiple levels

and caching them.

Browser OS and recursive resolving servers DNS caching speeds up website access and reduces unnecessary

queries to the actual domain servers.

DNS load balancing and failover are essential for large scale system.

That's the next takeover.

Techniques like anycast, DNS, primary and secondary DNS servers and CDNs help ensure high availability

and optimized performance.

Next, the important thing to consider is that security threats exist, but the best practices help

mitigate them.

Attackers like DNS poisoning and DDoS attacks very much, and they can disrupt all the services.

But using protocols like DNS, SEC, secure configurations and monitoring DNS servers help protect DNS

infrastructure.

In short, understanding DNS is crucial for the system design, performance optimization, and security.

The more you know about how it works, the better you will be at designing reliable and scalable systems.

Next lecture, we will dive into another fundamental concept the client server model, which is the

backbone of the modern computing from websites to cloud computing.

So in the next one we will explore how clients and servers communicate to power the internet.

So I will see you in the next one.