Hello and welcome to this lecture on event driven Architecture.

In today's lecture, we will explore how event driven systems enable asynchronous and decoupled communication

in modern architectures.

We'll cover key components like pub, sub model and event streaming.

We will look at the major components such as event producers, brokers and consumers.

And we will try to see how the event driven architecture is helpful in modern architecture.

By the end of this lecture, you will understand how event driven architecture improves scalability,

fault tolerance and flexibility in large scale distributed systems.

So let's get started.

Let's start with the basics.

What is event driven architecture?

Event driven architecture is a system design approach where different components communicate through

events, instead of making direct calls to each other.

This allows system to be more flexible and scalable.

So what are the key characteristics that defined event driven systems?

First, they rely on asynchronous processing.

Unlike traditional request response models where service waits for a response, event driven architecture

allows services to continue working while events are processed in the background.

Second, they promote loose coupling.

Since components communicate through events rather than direct connections, they can evolve independently

without breaking the system.

And third, they enhance scalability and flexibility.

Since event driven systems don't have tight dependencies, they can handle spikes in traffic much more

efficiently.

So why should we use event driven architecture?

First, it improves system responsiveness by enabling real time event processing, making it ideal for

applications like financial transactions, notifications, and monitoring systems.

Second, it also supports complex workflows where multiple services need to react to a change, such

as order processing system, uh, Internet of Things, data handling, or supply chain management.

In summary, event driven architecture is a powerful approach that allows systems to be more dynamic,

resilient, and scalable.

So before we dive deeper into event driven architecture, let's first understand the difference between

synchronous and asynchronous communication.

So what is synchronous communication?

In a synchronous system, a request is sent and the sender waits for a response before proceeding.

This means the process is blocking.

Nothing else can happen until a response is received.

This approach creates a tight coupling between components, as one service depends on another to function

properly.

A common example of synchronous communication is a traditional HTTP call.

When a client sends a request to a server, it waits for a response before moving forward.

While this model is simple and easy to understand, it can lead to bottlenecks, especially when multiple

services rely on each other.

So what is the answer?

Asynchronous communication.

So in contrast, asynchronous communication operates on a non-blocking model.

A service can send an event and continue processing other tasks without waiting for an immediate response.

This enables loose coupling, meaning components are independent and evolve separately, making the

system much more flexible and scalable.

Examples of asynchronous communications are message queues and event brokers like Kafka and RabbitMQ.

These systems allow different components to react to events whenever they are ready.

So in summary, synchronous systems are direct and simple, but they can become bottlenecks.

Whereas asynchronous systems promote scalability and resilience by decoupling components.

This is why event driven architecture is so powerful.

Now let's dive into two fundamental event driven messaging patterns publish, subscribe and event streaming.

So let's start with publish.

Subscribe.

In a publish subscribe model, events are broadcasted to multiple subscribers.

The publisher doesn't need to know who the subscribers are.

It simply sends an event and any interested subscriber will receive it.

Each subscriber gets the events once, meaning the message is not stored for later retrieval.

In real world example of publisher subscriber like in a notification system, when a user posts an update,

multiple followers get notified instantly.

Nowadays, technologies like RabbitMQ and AWS Simple Notification Service actually implements this model.

The second model is event streaming.

Unlike pub Sub, event streaming is designed for long term event retention.

Events are stored in an ordered fashion, allowing consumer to process them at different times.

This means consumers don't have to be online.

When an event is published, they can receive the past events from the log and process them at their

own pace.

A common use case for event streaming is processing real time analytics, such as tracking a website

visits over time.

We have popular technologies for event streaming like Apache Kafka and AWS Kinesis.

So to summarize, Pub Sub is great for real time notifications, while event streaming is better suited

for scenarios where event history and ordered processing matter.

Choosing the right approach depend on your use case of the application.

So now that we understand the basics of event driven architecture, let's break down its key components

and how they work together.

So the first key component is event producers.

Event producers are generating the events.

Event producers are the starting point of an event driven system.

These are the components that generate events based on system activities.

Producers can be anything from user actions like clicking a button, microservices, updating a database,

or IoT devices sending sensor data.

For example, in an e-commerce system, when the user places an order, an order placed event is generated

by the order service.

Then the second component are event brokers.

Event brokers are responsible for transmitting and storing Touring events.

Event brokers act as intermediaries between the event producers and consumers.

They ensure events are reliably transmitted and in some cases stored for later consumption.

They help in decoupling components, making the system more scalable and fault tolerant.

Common event brokers include Apache Kafka, RabbitMQ and AWS EventBridge.

Now what could be an example?

One example could be in a real time analytics system.

Kafka can store a stream of events for multiple sources and distribute them to multiple consumers.

And then the next key component is event consumers.

These are the components that are reacting to events.

Event consumers are the components that listen for events and take actions based on them.

Consumers can be anything from a database updater, a notification service, or a fraud detection system.

An example could be that in a ride sharing app, when a user requests a ride, a consumer service matches

the user with the nearby driver, and then the last key component is event storage.

It's not visible in the diagram, but it is also one of the key component, and its responsibility is

persisting events for replay.

So it's not present in all the systems.

But in many cases we don't just want to process the events in real time, but we also need to store

them for historical analysis, debugging or replaying in case of failures.

So in these cases, in these components, log based storage allows events to be replayed and reprocessed,

which is especially useful in systems like financial transactions or audit logs.

Examples like Kafka and AWS Kinesis are very helpful in event storage.

Together, these four components form the backbone of an event driven system, enabling scalability,

resilience, and loosely coupled architecture.

So event driven architecture brings a lot of benefits, but it also comes with its own set of challenges.

So let's discuss some of the key ones and how to handle them effectively.

So the first challenge is about eventual consistency.

So unlike traditional request response systems where updates happen synchronously, event driven systems

rely on eventual consistency.

This means that different parts of the system may not immediately reflect the latest state, leading

to temporary inconsistencies, but the data will get synced to all the services eventually, and it

will show the correct picture eventually.

For example, in an e-commerce system, after an order is placed, the inventory might take a few seconds

to update.

We use techniques like distributed transactions, idempotent processing and compensating actions to

manage all this.

Then the second is ordering guarantees.

Ensuring that events are processed in sequence is important.

So typically what happens in a distributed system is that maintaining the correct order of events can

be very challenging, especially when multiple consumers process events concurrently.

For example, if a payment process event arrives before an order placed event, the system may behave

incorrectly.

So there could be solutions, and these solutions include partitioning the events by keys like user

IDs or order IDs, or giving them sequence numbers, or implementing functionalities like event deduplication.

But ordering of events is a challenge in case of event driven architecture.

Next challenge is fault tolerance.

How to handle failures gracefully.

Failures can happen at any stage event producers, brokers or consumers anything can fail.

A resilient system should handle failures without losing events.

For instance, if an email notification service goes down, event shouldn't be lost.

They should be retried at a later stage.

So there is something called dead letter queues, something called exponential backoff and retries an

event reprocessing mechanisms which will help us in ensuring reliability.

Then the challenge that all the developers faced is is debugging complexity.

Since events move asynchronously across multiple services, debugging issues become harder than in traditional

synchronous architecture.

For example, if a customer support team needs to investigate a failed transaction, Tracking the exact

event flow can be very difficult.

Distributed tracing tools like Opentelemetry and all can be used to get some help here.

So what we have understood while these challenges exist with event driven architecture, careful architectural

decisions and the right tooling can make event driven systems highly reliable, scalable and efficient,

even though it comes with some set of challenges.

Now, to build a robust and reliable event driven system, it's important to follow best practices.

Let's go over some of the key recommendations to avoid some common pitfalls.

So the first best practice is that use idempotent event processing to avoid duplicates.

So what happens is events may be delivered multiple times due to retries or network failures.

And without proper handling this can actually lead to duplicate processing.

For example, if a payment process event is received twice, we don't want to charge the customer twice.

To prevent this event, consumers should be idempotent, meaning they should be able to process the

same event multiple times without any unintended side effects.

Second is we should always implement dead letter queues.

So what happens is not all events will be processed successfully on the first attempt.

So if a consumer continuously fails to process a message, it shouldn't get stuck in an infinite retry

loop.

For example, if an email notification service keeps failing due to an invalid email address, we need

a way to capture this and investigate this failure.

So how to solve this?

Dead letter queues.

Dead letter queues provide a separate storage mechanism for failed messages, allowing engineers to

inspect and manually handle them at a later point in time.

Then we should always try to choose the right event broker based on our system requirements.

We have seen that different event brokers serve different purpose.

Choosing the right one depends on factors like message durability, ordering guarantees, and scalability.

For example, Kafka is great for high throughput event streaming, but RabbitMQ is better suited for

traditional message queuing.

And if we look at AWS EventBridge, it is very useful for cloud native event routing.

So selecting the right event broker ensures the system remains efficient and meets performance expectations.

Then one more best practice is that we should try to ensure event versioning to handle schema changes.

So what happens is that over time, event structures will evolve.

Adding or removing fields in events can break the existing consumers if they are not handled correctly.

For instance, if a user created event initially contains name and email, but later adds phone number,

also, the older consumers might fail to process it to handle this.

We use event versioning strategies such as adding new fields instead of modifying existing ones, or

using schema registries like Apache.

Avro is one example.

So by following these best practices, we can build scalable, fault tolerant and maintainable event

driven architecture that supports our evolving business needs.

So what are the use cases of event driven architecture?

Event driven architecture is widely used across industries to enable real time, scalable and flexible

systems.

So let's try to explore some common use cases.

First is logging and auditing.

Keeping a record of systems activities crucial for debugging, compliance and security.

For example, every time a user updates their profile, an event can be logged in an audit trail.

This helps organizations track changes and detect anomalies.

Event driven logging ensures that every action is captured without slowing down the main application.

Then second use case is about real time notifications.

All our chat applications stock price update applications use this.

So there are many modern applications that require instant updates to keep the users informed.

Same example in a chat application.

When a user sends a message, an event is triggered notifying the recipient in real time.

Then we have this use case of microservices.

Decoupling microservices should be independently scalable and fault tolerant.

We know that.

So one of the biggest advantage of event driven architecture is that it enables loosely coupled microservices.

For example, in an e-commerce system, the order service, payment service and an inventory service

don't need to communicate directly.

Instead, an order placed event can be triggered and payment processing will happen once this event

is received by the payment service.

This approach ensures flexibility and resilience and decoupled microservices.

Then we have this use case of IoT system.

So we all know that IoT devices generate massive amounts of real time data that needs to be processed

efficiently.

So if your smart home system is generating a lot of events and it wants to trigger actions like turning

the air condition on or off, what we can do is that we can use event brokers like Kafka to handle this

high frequency data efficiently.

And then this is actually a practical use case of e-commerce, where if the e-commerce site is well

designed, what it does is it follows a sequence of events to ensure smooth order fulfillment.

For example, when a customer places an order, an order placed event is generated.

It triggers payment processing, which then triggers inventory updates, which then triggers shipping

notification.

All this happens asynchronously using events.

This asynchronous event flow ensures scalability and prevents bottlenecks in high traffic systems.

So these are some typical use cases that we have seen here to highlight the power of event driven architecture.

Event driven architecture is very helpful in building responsive, scalable and resilient systems across

various domains.

So now there are some of the important interview questions listed on the screens.

These questions Help assess whether you can think practically about designing scalable and maintainable

event driven systems.

Make sure to practice these and relate them to real world examples to make your answers stand out in

interviews.

I have also attached a PDF in the resources section with detailed answers to these questions.

Make sure to go through it for a deeper understanding.

Now let's quickly wrap up and look at the key takeaways of this lecture.

First thing we discussed about is event driven architecture enables scalable and decoupled system.

We saw how event driven architecture allows systems to process events asynchronously, enabling better

scalability, flexibility and responsiveness by decoupling services.

We reduce dependencies, making the system much more resilient and adaptable to change.

Then we looked at two models pub sub model and event streaming model.

Pub sub is great when multiple consumers need to receive the same event.

While event streaming ensures ordered processing and replayability of events over time.

Then we looked at some of the challenges that exist in event driven architecture.

We highlighted some of the key challenges like eventual consistency, event ordering, and fault tolerance.

We looked at the techniques like idempotent processing, dead letter queues, and schema versioning

that can help in overcoming these issues.

So what is next for us in the next session?

We have looked at some of the architectural patterns in this section.

So in the next lecture we will try to summarize what all we have seen.

We will see how all these pattern fit into the system design landscape and when to use each one of them.

So I will see you in the next one.