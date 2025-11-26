Hello everyone, and welcome to this lecture on multi-tier Architecture, a fundamental architectural

pattern that is used in modern software design.

In this lecture, we will explore how multi-tier architecture works, its key components, and why it

is widely used in scalable and secure applications.

We'll break down the difference between two tier, three tier and N-tier architecture.

We will examine their impact on performance and scalability, and look at real world examples like web

applications and enterprise systems.

By the end of this lecture, you will have a solid understanding of Multitier architecture and how to

apply it in system design.

So let's get started.

So let's start with the basics.

What is Multitier architecture?

Multitier architecture is a software design pattern that structures an application into multiple layers,

where each layer has a specific role instead of a monolithic system where everything is tightly coupled.

Multi-layer design separates the concerns into independent layers.

This separation improves scalability, maintainability and security, making it a popular choice for

modern applications.

There are a few key points to remember when it comes to Multitier architecture.

First, it organizes applications into independent layers, so changes in one layer don't affect the

other layers.

Second, it separates concerns the UI, the business logic.

The data storage layers are handled separately.

Improving the code organization and reusability.

Then it enhances performance and security by allowing load balancing, caching, and secure database

access.

Finally, it is widely used in web applications, enterprise systems, and cloud architectures, where

scalability and Reliability are crucial.

So let's dive into the two tier architecture to start with.

In a two tier architecture we have two layers the client layer and the database layer.

The client layer typically represents the user interface or the application logic where the user interacts

with the system.

The database layer is where the application stores and retrieves data from, usually through a SQL database

or any NoSQL database setup.

We have the data layer.

So in this setup, the client communicates directly with the database without any intermediate business

logic layer.

So client layer is where the user interface and application logic will reside.

Example could be a desktop application where the user will input the data and interact with the application,

and the database layer will be the layer that will manage the data storage and retrieval in a two tier

application.

Data flows directly between client and the database, with no intermediate layers in between.

We have talked about it already.

So what are the pros of this architecture?

First is it is very simple to implement since there are only two layers.

It's easy to set up and understand.

Second, it is very fast for small scale applications.

It is ideal for applications that do not require much scalability.

But there are some cons also.

The biggest con is the poor scalability.

As the number of users grow, performance can degrade because there is no intermediary to handle business

logic or distribute the load.

Second is there is a security risk.

Direct database access means that there are potential vulnerabilities, as there is no business logic

layer to filter out or secure the data.

The use case for such an architecture could be a desktop application that directly queries a SQL database

that resides on the same machine.

This is okay because scalability is not a primary concern here.

So while simple and effective for small scale systems, two tier architecture is often unsuitable for

larger, more complex applications.

Let's now move on to three tier architecture, which introduces an important middle layer a business

logic layer.

In a three tier architecture, we have three layers the front end which will have the UI, the business

logic layer and the database layer.

This setup adds a separation of concern between the user interface, the application logic and the data.

So how it works.

First we have the front end layer.

The user interface interacts with the business logic layer through an API.

So the front end will talk to the business logic layer.

What happens in the business logic layer?

This layer processes business rules, application logic and requests from the UI.

It communicates with the database to fetch, update and delete the data.

Then we have the database layer.

The database stores and manages the application data.

It only communicates with the business logic layer and not the UI layer directly.

So typically what happens is that we have a presentation layer which has the responsibility of all the

UI related thing, business logic layer, where all my business and application logic will be there.

Data access layer which will have all the data access related code and the data separately stored in

the database.

So unlike the two tier architecture where the clients communicates directly with the database, the

three tier architecture uses a middle layer to handle the logic and secure database interactions.

So what are the pros of this?

First is improve the scalability and security by separating the business logic layer.

We can independently scale each layer and enforce stricter security policies between the UI and the

database.

Then we have better separation of concern.

Each layer handles a specific responsibility, making the system easier to manage and evolve over time.

And then finally, it is easier to maintain changes in one layer do not affect other layers, making

the system easier to maintain and extend.

So what are the cons of this?

Well, there is slightly higher latency because we have extra layer, and adding an extra layer of processing

introduces some latency as requests.

Now go through the business logic layer before reaching to the database.

However, this is typically offset by the benefits of scalability and security.

So what are the examples?

Traditional web applications are classic examples of three tier architectures where it can have a front

end like React or Angular application communicate with the back end API, which could be a business

logic layer which will talk to the data access layer, process the request and interact with the database

to retrieve and store the data.

Three tier architecture is highly suitable for applications that need better scalability, security

and separation of concerns.

It provides a solid foundation for modern web applications.

Now let's explore the entire architecture, which extends the concept of three tier by adding more specialized

layers to handle more complex systems.

So what is N-tier architecture?

N-tier architecture?

We go beyond the basic three layers by introducing additional specialized layers such as caching, API

gateway, microservices and more.

These extra layers help handle the complexity of modern high traffic applications.

Why should we use N-tier architecture?

Well, N-tier architecture handles high traffic and complex business logic applications much better.

The additional layers allow the system to distribute loads efficiently and process complex business

logic in a scalable way.

For example, caching layer can reduce database load and microservices can isolate functionality to

keep things manageable.

Second, independent scaling of services is also beneficial.

Each layer can be scaled independently to meet specific needs.

For instance, the caching layer can be scaled separately from the business logic layer, allowing you

to allocate resources based on demand.

This makes the system more flexible and efficient in handling varied workload.

What could be the example of this?

Well, microservices based applications is one of the best example.

Microservices often use N-tier architecture, where each microservice is a separate tier on the layer

in architecture, allowing each service to scale and evolve independently.

For example, one tier may handle user authentication, another may handle payment processing and another

inventory management.

So it is a perfect use case for using N-tier architecture.

Also, if you are developing large scale enterprise software like e-commerce platforms, banking systems,

CRM tools, they can also use N-tier to scale and handle the traffic with specialized layers for things

like security, caching, monitoring and analytics.

So in short, n tier architecture is ideal for systems that require high scalability, fault tolerance,

and the ability to manage complex business logic.

It's widely used in enterprise applications and large scale services like social media platforms, e-commerce

sites, and cloud native applications.

So now that we have looked at two tier, three tier and N tier architecture, let's try to explore how

the number of tiers in the architecture impacts system performance and scalability.

So as we introduce more layers and more complexity into the system, each layer adds a certain processing

overhead, which can affect performance and scalability if we are not managing it carefully.

So first we have to consider the latency related things.

One key factor is when we are adding more tiers.

Then latency will increase.

Every additional layer introduces more communication between different components, which can lead to

higher latency in data processing.

That means that the request must pass through multiple points, which will introduce delays.

So the more layers you have, the higher the latency.

Unless those layers are properly optimized.

So what are the solutions for optimizing it?

One solution is caching.

Caching is the way to optimize latency and improve performance.

For instance, frequently accessed data can be stored in a cache so that it doesn't have to be received

from the database every time.

This can significantly reduce latency and improve response times.

Another very good solution that we need to keep in mind is about the scaling strategies.

We can scale our application to actually make it perform better in an n-tier architecture.

So there are two types of scaling.

First is vertical scaling and second is horizontal scaling.

Vertical scaling involves adding more resources like CPU, Ram, or storage to a single server.

While this can help handle increased load for a while, it has limits.

Eventually, a single machine will reach its capacity.

However, for applications that don't require massive scale, vertical scaling can be a simple solution

to improve the performance.

Then we have horizontal scaling.

Horizontal scaling is more powerful for handling high traffic.

It involves adding more servers to distribute the load and improve the fault tolerance.

As the demand grows, you can simply add more machines, allowing the system to handle large traffic

volumes.

This is especially useful for cloud based systems that can scale on demand.

So to summarize, the more tiers you introduce in your system, in an n tier architecture, the greater

the importance of optimizing the latency and scalability.

Using techniques like caching and load balancing, combined with vertical and horizontal scaling, can

help you build a system that handles high traffic efficiently and provides low latency responses to

the end user.

Now, on the screen, you can see a list of important interview questions related to Multitier architecture.

These questions are commonly asked in system design interviews because multitier architecture is a fundamental

concept in designing scalable and maintainable applications.

So if you understand these questions, you will be able to explain the architectural choices clearly.

You will be able to discuss trade offs between different tiered architectures, and you should be able

to apply the best practices.

When designing the real world systems.

You should be able to answer these questions based on whatever we have covered in this lecture so far,

like differences between two tier and three tier architecture, how tiering affects performance, scalability

and security consideration.

But to help you further, I have attached a PDF with detailed answers to these questions.

Make sure to go through them and test your understanding.

Now, before we wrap up, let's look at the key takeaways of this particular lecture.

First, multi-tier architecture for better scalability and maintainability.

Multi-Tier architecture is all about separating concerns and organizing your system into independent

layers.

This structure improves scalability, maintainability, and security, making it easier to manage and

scale as your system grows.

Then we looked at two tier architecture.

Two tier architecture is simple to implement and works well for small scale applications, but it's

limited in terms of scalability and security.

It is suitable for small, less complex systems, but becomes a bottleneck as our system grows.

Then we looked at three tier architecture.

The three tier architecture is the standard for most of the modern web applications.

It separates the UI business logic data access layer, allowing for better scalability, security and

easier maintenance.

It's the go to choice for most web applications today.

Then we looked at n tier architecture for large scale cloud native systems for large scale applications,

especially those are cloud native and built with microservices, N-tier is the preferred approach.

It introduces specialized layer such as caching, API gateway and microservices layer to handle high

traffic and complex business logic.

This makes it ideal for enterprise applications and high traffic services.

So now that we have covered all about Multitier architecture, what's next?

Our next topic will be Microservices architecture.

We will dive deeper into microservices architecture, which is building on the principle of multi tiered

design, but focuses on breaking down the application into smaller independent services, microservices,

often even more scalability and flexibility.

So I will see you in the next one.