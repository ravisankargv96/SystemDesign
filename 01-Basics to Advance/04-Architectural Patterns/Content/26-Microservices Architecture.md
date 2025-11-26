Hello and welcome to the next lecture of our course on microservices architecture.

In this lecture we will explore how modern applications are designed using microservices, how they

differ from monolithic systems, and why leading tech companies like Netflix, Uber and Amazon have

adopted to this approach.

By the end of this lecture, you will understand the key components of microservices, how services

communicate the common challenges of microservices, and deployment strategies to build scalable and

resilient systems.

So let's start with the basics.

What is microservices architecture?

Microservices architecture is a software design pattern that structures an application as a collection

of small independent services, each handling a specific business function.

Unlike monolithic application where all components are tightly integrated, Microservices are loosely

coupled, meaning each service operates independently and communicate via APIs.

The key characteristics of microservices are.

First, they are independently deployable.

Each service can be deployed, updated and maintained without affecting any other service.

Second, they are loosely coupled and modular.

Services interact with each other through a well-defined API, but by themselves they remain self-contained.

Third is scalability.

You can scale individual services based on demand and failure in any one of the service.

Don't bring down the whole system.

This approach enables organizations to build applications that are more resilient, scalable, and maintainable,

making microservices a preferred choice for modern software development.

Now, one of the key challenges in microservices architecture is deciding how to break down an application

into several individual services.

So how do we identify microservices?

So the first principle is business capabilities.

Each microservice should align with a specific business function like payment order or user.

This ensures clear ownership and logical separation.

Next, we follow a single responsibility principle.

A microservice should do one thing well.

If the service handles multiple unrelated concerns, it may need further decomposition.

Then there is this critical rule of data ownership.

Each microservice should manage its own database.

Shared databases create dependencies and reduce the benefits of independent deployments.

And finally, microservices should be independently deployable, meaning updates to one service should

not require redeploying the entire application, which includes other services.

Now, how do we structure our microservices correctly?

First thing that we do is we use domain driven design to break the system into logical domains.

This helps us in grouping services based on business needs.

Second, we ensure that microservices communicate through a well-defined API, whether via Rest, API,

gRPC or event driven messaging.

Next, we must choose the right granularity to large and we end up with a monolith again, too small

and we will increase the complexity with excessive service interactions.

So we need to size our microservice with very careful thought.

Lastly, implementing observability in microservices is essential.

Logging, monitoring and tracing help in tracking interactions between services and identifying the

issues early.

By following these principles, we can design a scalable and maintainable microservices architecture.

Now, in microservices architecture, services need to communicate with each other to exchange data

and process requests.

The two main communication models are synchronous and asynchronous.

So first let's go through synchronous communication.

In synchronous communication services, wait for a response before proceeding.

And there are two common methods for synchronous communication.

The first is Rest APIs.

Rest is most commonly used approach as it follows HTTP standards and is easy to implement, however,

since it relies on text based communication, either JSON or XML.

It can introduce higher latency.

So what is the alternative?

The alternative is gRPC.

gRPC, on the other hand, is a high performance communication protocol that uses a binary format called

Protocol Buffers.

It is much more efficient than Rest and is ideal for microservices, which require low latency and high

throughput.

Then there is this second way of communication that is called asynchronous communication.

So in many cases, microservices do not need to wait for the immediate response.

This is where asynchronous communication comes in.

Using event driven messaging.

Event driven architecture relies on message brokers like Kafka or RabbitMQ.

These systems enable microservices to publish and subscribe to events, reducing dependencies between

services and improving scalability.

Liability.

For example, when a user places an order in an e-commerce system, the order service can publish an

event like order created.

The other services, like payment service and inventory service can react to this event without any

direct dependencies.

So choosing the right communication strategy will depend on your use case.

Rest and gRPC meaning synchronous communication is great when services need immediate responses.

On the contrary, event driven asynchronous communication is ideal when services need loose coupling

and scalability.

By leveraging the right mix of synchronous and asynchronous communication, we can build a very highly

efficient and scalable microservices system.

Now, it's not always positive about microservices.

While microservices brings Bring scalability, flexibility and independent deployment.

They also introduce several challenges that the teams need to address.

The first challenge is data consistency.

Unlike monolithic applications where a single database ensures strong consistency, microservices often

use distributed databases.

This leads to the concept of eventual consistency, where changes take time to propagate across services.

For example, in an e-commerce system, if an order service updates an order status, it may take a

moment for the inventory service to reflect the change.

Event driven messaging can help in handling these delays.

Then second is distributed tracing.

Since microservices interact over a network, tracking a single request across multiple services is

challenging.

Debugging issues like failures, delays, and incorrect responses required distributed tracing.

Then we have network overheads.

Microservices rely heavily on API calls for communication, introducing network latency.

More services mean more inter service calls, which can be slow and bring down performance.

Optimizations like using gRPC, binary format caching and aggregating requests can help in reducing

these overheads.

And then there is this security concern.

In a microservices environment, every service needs proper authentication, authorization and data

protection.

Unlike monolithic applications where security is centralized, microservices must implement security

at multiple levels.

Secure service to service communication is very much essential.

Addressing all these challenges requires the right design patterns, tools, and best practices.

Ensuring that microservices remain scalable, secure, and reliable.

But we need to acknowledge the fact that implementing microservices architecture brings additional level

of complexity, and we need to be ready to handle this complexity in our application.

Now, scaling is one of the biggest advantages of microservices.

Unlike monolithic applications, where scaling requires increasing resources for a single application,

microservices allow us to scale individual components independently.

Now let's look at some of the key strategies.

First is horizontal scaling.

Instead of making a single server more powerful, which was called the vertical scaling, we add multiple

instances of a microservice and distribute traffic among them.

This ensures high availability and load balancing.

For example, if the order service in an e-commerce system is under heavy load, we can deploy additional

instances of the order service to handle more requests.

Then we have auto scaling.

Manually adding or removing instances is insufficient.

So we use auto scaling solutions from the cloud vendors or like Kubernetes horizontal pods.

And they will help us in automatically scaling the service whenever there is high load on that service.

These tools automatically scale these services up or down based on CPU, memory and request load.

Then there is this technique of sharding and database scaling.

As traffic increases, database performance can become a bottleneck.

One solution is sharding, where we split the database into smaller partitions based on a unique key.

Another approach is read replicas, where we have multiple database copies to handle read heavy traffic

efficiently.

So by using a combination of horizontal scaling, auto scaling, and database optimization, we can

ensure that microservices handle increasing loads efficiently without downtime.

We will go deep into all these topics in upcoming lectures.

So if this slide looks a little overwhelming, don't be afraid of it.

We will go in deep in all these topics in the upcoming lectures.

Now let's look at some of the real world, most successful companies example that have adopted microservices

to scale and improve their performance.

Netflix actually relies heavily on microservices to handle video streaming, personalization, and recommendation.

They have decoupled each function into separate services, and they can scale different components independently

and ensure smooth experience for millions and millions of users on the same lines.

Uber also uses microservices to scale ride matching payment and navigation independently.

Also, Amazon has a microservices based architecture where each function, such as search payment recommendation,

runs in its own service.

This modularity ensures that Amazon can handle massive traffic and make real time changes without downtimes.

So these companies are great examples of microservices enable scalability, flexibility, and resilience,

making them able to meet the need of millions of customers every day.

Now that we have covered the basics of microservices architecture, let's go over some key interview

questions you might encounter when discussing this topic in a System Design interview.

These questions test your understanding of how to design, implement, and scale Microservices.

Effectively, they are crucial because microservices have become the standard for building modern,

scalable applications.

You should be able to answer these questions based on what we have discussed in this lecture.

Understanding these concepts will not only help you on interviews, but also when working on the real

world projects.

Also, a detailed PDF with the answers is attached to this lecture so you can review and practice these

questions later.

Now before we end this, let's just recap.

Microservices offer tremendous advantages in terms of scalability, fault tolerance, and faster development

by decoupling applications into smaller, independently deployable services.

However, implementing microservices require key components like API gateway, service discovery and

load balancing to manage inter service communication and high availability.

So whatever additional complexities microservices are bringing, we need to take care of those complexities

also.

But like any architecture, microservices comes with own set of challenges also.

We talked about the complexity challenges we discussed, like managing data consistency, handling distributed

tracing, debugging, and dealing with the complexity of deployment and orchestration.

So we need to be aware of all these complexities that comes with microservices architecture.

Then we looked at some real world examples like Netflix, Uber and Amazon, how they have successfully

leveraged microservices to scale their operations and serve millions of customers globally.

In the next lecture, we will dive into event driven architecture, a powerful mechanism for creating

scalable and decoupled systems, particularly for handling asynchronous communications.

So I will see you in the next one.