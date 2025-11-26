Hello and welcome back to this lecture on load balancing.

In today's lecture, we will explore why load balancing is essential in system architecture.

The different types of load balancers and the various strategies used to distribute traffic effectively.

Load balancing plays a critical role in ensuring high availability, scalability, and reliability in

modern applications.

By the end of this lecture, you will have a clear understanding of how load balancers work and how

to choose the right approach for your system.

So let's dive in.

So in modern systems, handling traffic efficiently is crucial to ensuring smooth user experiences.

This is where load balancing comes in picture.

Let's go through the key reasons why load balancing is essential.

First is high availability.

A load balancer ensures that our system stays up and running even when the traffic spikes.

If one server goes down, the traffic is automatically redirected to the healthy servers, which will

minimize the downtime for the application.

Next is traffic distribution.

Instead of overwhelming a single server, a load balancer spreads out the requests evenly across multiple

servers.

This ensures no one machine bears too much load.

Third, prevents overload.

Without load balancing, a sudden surge in traffic could crash a server, leading to service disruptions.

Load balancers help prevent this by distributing the workload intelligently.

Then comes improved performance by sending requests to the least busy server or fastest responding server,

a load balancer can reduce the overall latency and ensure users get a faster response time.

Then it handles failures Gracefully.

If a server crashes or become unresponsive, the load balancer detects it and it reroutes the request

to other healthy servers, ensuring the container service to the end user.

Then it supports scalability as traffic to our web server grows as traffic to our website grows.

We can add more servers and the load balancer will automatically distribute requests among them, allowing

our systems to scale efficiently.

To put all this in perspective, consider a high traffic e-commerce website like Amazon.

During a sale event without load balancing, a sudden influx of users could overwhelm a single server,

causing slow performance or even downtime in some cases.

But with a load balancer in place, incoming requests are intelligently distributed across multiple

servers, and it ensures a smooth shopping experience for all the customers.

This is why load balancing is a fundamental component of modern system design.

Next, let's explore the different type of load balancers and how they function.

So now that we understand why load balancing is essential, let's dive into the different types of load

balancers.

Load balancers can be categorized based on two key aspects.

First, the network layer that they operate on, and second is based on their deployment model.

So let's look at the first one where the categorization is based on the network layer that they have.

So the load balancer can be categorized based on the OSI layer of networking on which they operate.

There are two main types of load balancers layer seven load balancers and layer four load balancers.

Layer four load balancers work on the transport layer.

Layer four load balancers operate at transport layer, meaning they make the routing decision based

on the network level data such as IP addresses and the TCP or UDP ports.

They do not inspect the actual content of the request because they cannot.

The actual content is only visible at level seven.

Only the metadata surrounding it is visible to the layer four load balancer.

Because of this, layer four load balancers are extremely fast and efficient, and it makes them the

ideal choice in scenarios where speed and performance are the highest priority.

AWS Network Load Balancer and HAProxy operate in the layer four mode.

The second one is layer seven Load Balancers.

They operate on the application layer, the layer seven load balancers.

Inspect the actual request contents also.

This allows them to make intelligent routing decisions based on factors such as what are, what HTTP

headers are present, what cookies are there, what query strings are there, what is the request path,

and even the user's location?

For example, an e-commerce site could use a layer seven load balancer to redirect traffic for product

pages to one set of servers, while sending checkouts requests to a different set of servers which are

optimized for transactions.

This flexibility makes layer seven load balancers powerful, but it also means that they require more

processing power compared to layer four load balancers.

Some examples of this are AWS Application Load Balancers and nginx.

So that was the categorization based on the layer on which the load balancers operate.

The second Categorization is based on the deployment model.

Apart from the network layer, load balancer are also classified based on how they are deployed.

So there are three main categories for this hardware software and cloud based load balancers.

So what are hardware based load balancers?

Hardware load balancers.

Load.

They are physical devices specifically built for high performance load balancing.

These are used in large enterprises or data centers that require dedicated solutions for handling millions

and millions of requests per second.

Hardware load balancers often comes with built in features like SSL termination, DDoS protection,

and advanced traffic management.

Some of the famous hardware load balancers are F5 network Big-ip Load Balancers and Citrix Netscaler.

Then the other side is software load balancers.

This software.

Load balancers are the applications that run on general purpose servers.

They provide flexibility and cost effectiveness because no dedicated hardware is required.

They can be deployed on any virtual machine, container or even on premises infrastructure.

The popular open source software load balancers include nginx, HAProxy and envoy's.

These are widely used in modern architecture, including the Kubernetes based microservices environments.

And then finally cloud based load balancers.

With the rise of cloud computing, many organizations now use cloud based load balancers.

These are managed services provided by our cloud vendors that automatically distribute traffic across

virtual machines, containers, or even multiple geographical regions.

Cloud based load balancers eliminate the need for manual infrastructure management and that provide

scalability, security, and global traffic distribution out of the box.

Some examples are AWS Elastic Load balancers, Google Cloud Load balancers, Azure load balancers.

So in summary, the load balancer classification can be based on their network layer.

Layer four for the fast transport level distribution and layer seven for the content aware intelligent

routing.

Additionally, they can be deployed as hardware application for enterprise needs, software application

for flexible deployment or as cloud based solution for seamless scaling.

Choosing the right type of load balancers depend on the use case, what performance requirements are

there and what infrastructure requirements are there.

Now that we know the different types of load balancers, let's try to explore the different load balancing

strategies and how they help distribute traffic efficiently.

Load balancing strategies can be broadly classified into two categories static load balancing and dynamic

load balancing.

The choice of strategy depends on the system architecture, the traffic patterns, and the server capabilities,

but we need to understand both these types in detail.

So the first one is static load balancing.

Static load balancing strategies distribute traffic based on predefined rules without considering the

real time server conditions.

These strategies work very well in environment where the server capacities are similar and the workloads

are predictable.

Remember, that's the keyword where the workloads are predictable.

So the first technique is round robin.

It is one of the simplest load balancing techniques.

Round robin sends requests sequentially to each server in a circular order.

Once the server receives the request, the process starts over from the first server again.

For example, if there are three servers, the first request goes to server one.

The When the second request goes to server two, the third request goes to server three and then this

cycle repeats on continuously.

This ensures an even distribution of traffic, but it does not consider the server load or the response

time that each server is providing.

So there is another static load balancing technique which is called least connection.

This strategy directs how new requests to the server with the fewest active connections, meaning the

server with the fewest active connection right now will receive the next request.

This is especially useful for applications where request processing times are very significantly different

from each other.

They are not standard, they vary very significantly.

For example, in a database system, some queries might take longer time, some might take less time.

Least connection ensures that a heavily loaded server doesn't receive more requests until it is clearing

the existing ones that it has.

Then another static load balancing technique is IP hashing.

In IP hashing.

A client's IP address determines which server handles the request.

A hash function maps each IP address to a specific server, ensuring that requests from the same clients

are consistently routed to the same backend server.

This is useful in scenarios where we require session persistence, such as when a user is logging in

into a system or a website, and it needs to stay connected to the same server for the duration of the

session.

Many load balancers also coined the term as session, affinity, or sticky session for this kind of

technique, where they want each user session to go to the same server for that particular session.

Now, the static strategies are simple and effective in certain scenarios, but they may not be very

optimal for the systems with fluctuating workloads.

That's where dynamic load balancing comes in.

Unlike static strategies, dynamic load balancing takes real time server performance into account when

distributing traffic.

These strategies continuously monitor server conditions to optimize request routing.

So the first one is least response time.

This method direct request to the server with the lowest response time, ensuring that the users get

the fastest possible responses.

It is particularly useful for the application where speed is very critical, such as financial trading

platforms or live streaming video services.

Then we have adaptive load balancing.

Adaptive load balancing continuously analyzes the real time data such as CPU usage, memory utilization,

and server health to make intelligent routing decisions.

For instance, if one of the server is experiencing high CPU usage, the load balancer will dynamically

shift traffic to healthier servers, preventing the overload of the already overloaded server and thus

improving the overall performance.

Then the next one is weighted load balancing.

In the weighted load balancing, different servers are assigned weights based on their capacity.

For example, a powerful server with high processing power may receive twice as many requests as the

less capable server.

This approach is useful when infrastructure consists of heterogeneous machines with varying performance

level with different system specifications.

Some of them are very powerful, some of them are not that powerful.

So all these dynamic load balancing strategies, ensure better resource utilization and system reliability

by adapting to the traffic conditions in real time.

However, they require more monitoring and processing overheads compared to the static load balancing

methods.

So to summarize, static load balancing methods like round robin, lease connection and IP hashing uses

predefined rules, making them simple but not adaptive.

On the other hand, dynamic strategies like risk response time, adaptive load balancing, and weighted

load balancing provides much smarter traffic distribution decisions based on the server health and performance.

Choosing the right load balancing strategy depends on what your system needs are.

If all servers have equal capacity, round robin may work well, but in systems with fluctuating workloads,

dynamic strategies like adaptive load balancing are much more effective now that we know different load

balancing strategies.

Let's look at some real world scenarios and how load balancers operate in action.

So imagine we have a web application that serves thousands or even millions of users daily.

This applications run on multiple back end servers to handle this load efficiently.

However, without a load balancer, users request with either overload a single server or require them

to manually select a server, which isn't very practical.

That's where load balancer comes in when the user sends a request, whether it's off loading a web page

or making a payment or submitting a form, the load balancer acts as an intermediate tree instead of

requests going to a single server.

The load balancer distributes them across multiple servers based on the chosen strategy.

For example, if we use round robin strategy, the first request is sent to server one, the next server

two, and then so on.

If we use the least connection strategy, then the server with the fewest active connections will get

the request, ensuring the efficient resource utilization.

Now what happens if one of the backend server crashes?

Let's say this server crashes.

The load balancer continuously monitors the server health.

It detects the failures and reroutes the traffic to the remaining healthy servers.

This ensures that the user experience no downtime, and we will keep maintaining our high availability

and reliability of the application.

The real world example of this could be a high traffic e-commerce platform like Amazon.

During peak shopping hours, millions of users are browsing and placing orders simultaneously.

The load balancer ensures that requests are efficiently distributed across multiple servers, preventing

slow response times and system crashes.

So this demonstrates how load balancing is crucial for ensuring system reliability, scalability, and

seamless user experience.

Now that we have seen the basics of load balancer, the next big question is how do you choose the right

one for your system?

The choice of a load balancer depends on multiple factors, including your network layer.

It operates on scalability requirements, security considerations, and the specific use case of the

application.

So the first decision that we have to think about is whether we want to use a layer four or layer seven

load balancer.

We use a layer four load balancer when we want fast and efficient traffic distribution purely based

on network level data like IP addresses and ports, it is ideal for handling TCP and UDP traffic where

the content inspection is not required.

On the contrary, we use a layer seven load balancer when we need more intelligent traffic routing decisions

based on either HTTP headers, cookies, request paths, or query strings.

This is useful in API gateways, microservices, or anything that is content aware that requires a content

aware traffic distribution.

The second thing that we need to think about is the scalability needs.

As our application grows, handling the increasing traffic becomes a challenge.

So choosing the right load balancer depends on the expected workload also.

So for small to medium scale applications, software based load balancers like nginx or HAProxy could

be a very cost effective solution.

But for high traffic applications, cloud based load balancers like AWS, ELB or Google Cloud Load Balancers,

they will automatically scale based on demand.

For enterprise level workloads, hardware level load balancers are much better suited as they provide

lower latency and they are ideal for mission critical applications.

In case our application experiences unpredictable spikes in traffic, using a cloud based load balancer

will also ensure the seamless scaling without manual intervention.

Because cloud based load balancers come with auto scaling options.

The third thing that we need to consider is about security, SSL termination, and DDoS protection is

something that every system designer should be aware of.

Encryption and decryption of HTTP traffic requires significant processing power, and many load balancers

actually come with this capability.

So if you choose a load balancer that provides this capability of SSL termination, offloading this

process from the backend server will actually improve the performance of your overall application by

a lot.

DDoS protection is also important.

Cloud based and enterprise grade load balancers come with built in DDoS mitigation feature.

They detect and filter out malicious traffic before it even reaches the backend servers.

So if your application handles very sensitive data like you have a banking application, healthcare

application, and you need strong encryption and DDoS protection, then you should keep these things

in mind before choosing the right load balancer.

That the load balancer provides the capability of SSL termination and DDoS protection.

Then I have listed some of the use cases and for which use case which load balancer is ideal.

Choosing the right load balancer for your system is crucial.

The right load balancer, like we have already seen, depends on several factors.

Choose a layer for for speed and efficiency.

Layer seven for Intelligent Routing.

Match the load balancer to your expected traffic volumes to ensure scalability.

Consider security features like SSL termination, DDoS protection and select the right type based on

your system architecture.

Software load balancer provide much more flexibility.

Cloud based provide much more scalability and hardware based for the enterprise grade performance.

Next let's look at some of the interview questions.

Now we have covered the fundamental concepts of load balancing from why it is needed to different types,

strategies and real world use cases.

With this knowledge, you should be well prepared to tackle system design interviews on this topic.

Remember, load balancing is a core component of scalable system architecture, making it a very frequently

discussed topic in system design interviews.

Interviewers often test your understanding of load balancing strategies, failure handling, and real

world implementations.

So the questions that you are looking on my screen, these questions test both theoretical knowledge

and practical decision making in designing scalable systems.

Since whatever we have covered so far all the fundamental concepts, I think you should be able to answer

most of these questions very confidently.

Additionally, there is a PDF attached in the resources section with detailed explanation and reference

material to help you prepare further.

So, with the solid grasp on the load balancing, now let's try to look at the key takeaways from today's

lecture.

First, load balancing enhances scalability, reliability, and performance.

Added course load balancing ensures that no single server is overwhelmed, allowing system to handle

high traffic efficiently.

By distributing requests across multiple servers.

It improves performance, prevent bottlenecks, and ensure high availability.

Second, we understood different types of load balancers do exist based on layers and the deployment

models we discussed.

Layer four.

Layer seven load balancers.

Layer four works at the transport layer and distribute traffic based on the network level data.

Layer seven operates at the application layer and can make intelligent routing decisions based on HTTP

headers, URL's, query strings, and cookies.

We have also looked at different deployment model, hardware based, software based and cloud based

load balancer.

Each serve different scalability and requirement need.

Then we looked at how to choose the right strategy.

Choosing the right strategy depends on the traffic patterns and the system requirements.

There is no one size fits all approach when it comes to load balancing.

Some strategies like round robin are simple, but they may not work well in all the scenarios.

Others, like lease connection or adaptive load balancing, take real time server health into account.

Choosing the right strategy depends on your system architecture, expected traffic load and whatever

performance requirements are there from the application.

Then we looked at how load balancing is essential for highly available and resilient systems.

High availability is a crucial goal for any system, and load balancers play a key role in achieving

it.

The prevent Downtime handles server failures very gracefully and enables smooth scaling as demand grows.

Without proper load balancing, even the most well designed applications can suffer from slowdowns or

crashes under heavy load.

So next, we will explore auto scaling how system scale automatically based on demand.

In cloud environments, we'll cover strategies horizontal versus vertical and best practices for building

resilient and cost efficient systems in cloud, from managed services to monitoring.

This is where scalability meets real world cloud architecture, so I will see you in the next one.