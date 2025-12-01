Hello and welcome to this lecture on messaging and queues for decoupling.

In this lecture, we will explore how asynchronous messaging helps build scalable and resilient systems.

We will look at when to use queues, compare brokers like RabbitMQ and Kafka, and understand the key

delivery guarantee methods like at least once or exactly once.

We will also see some real world examples like order processing and rate limiting.

And we will learn how decoupling boosts system performance and flexibility.

So let's get started.

So when building large scale systems, asynchronous messaging can be a game changer.

So how.

First it helps us in achieving loose coupling.

Producers just send messages without needing to know who will consume them.

This also boosts performance since producers can move on immediately without waiting for a response.

Think of a service.

Wants to send a message to another service.

Rather than making this call synchronously, it can just send a message and move on irrespective of

how much time the receiver will take to process that message.

That is the first advantage.

Also, we gain scalability.

Consumers can scale up or down independently based on the workloads.

So all the consumers, if there are a lot of messages coming for some given functionality, then we

can scale and add more nodes to the consumers.

So the consumers can scale independently.

Plus the queues bring resilience through message durability.

If, for example, a consumer fails, messages are not lost.

The messages are there in the queue.

Next time when the consumer comes back again, they will receive the message and they can process it

again.

And finally, we get Flexibility.

We can plug in new consumers anytime without modifying the producers, because there is no dependency

between producers and consumers.

So it is a very clean and modular way to design the system.

So let's break down the core building blocks of messaging system.

So first we have the message itself.

Message is what it is just a piece of data.

It is often JSON or binary sent from one service to another.

So some message that we want to send from one service to another.

The service that sends the message is called the producer, while the one that receives and process

is called the consumer.

So now we have three players.

Producers are producing the messages.

Consumers want to consume these messages how this message will now reach to the consumer.

So in between we have a broker.

Broker is the heart of the system, like rabbit, MQ or Kafka are very popular nowadays.

So what happens is that the broker temporarily stores messages and ensures that they are delivered correctly.

Within broker, messages can be organized into queues or topics which are like logical channels.

So you can have multiple logical channels and the producers can send messages to a specific channel

or topic.

And consumers can say, I want to actually consume the messages from this particular topic only.

So we have logical channels for messages called topics.

Then finally there is this acknowledgment, which is a signal from consumer that says I got the message

and processed it successfully.

This is not the same implementation in all the other message queues nowadays, but from a conceptual

perspective, acknowledge helps the broker decide whether to remove the message or retry it.

So this acknowledgement will be sent from consumers to message queues.

Now let's walk through a real world example of decoupled architecture using asynchronous messaging.

So the flow starts with catalog microservice.

Catalog microservice receives an update price command through its web API.

And it's a synchronous call from the user that wants to update the price of the product.

Now the service processes the request by updating its local database with the new price.

After successfully updating the local database, the catalog service publishes the price updated event

to the event bus.

As you can see here, this is where the decoupling begins.

The event bus acts as a message queue.

It's a pub sub system, Subsystem.

So allow we have some subscribers to this also.

So what this does is that it allows other microservices to react independently to this event.

For example, you can see here the basket microservice listens to this event and update any basket items

that has the old price.

This ensures consistency in user's cart.

Other microservices can also subscribe to the same event.

Other services like billing analytics.

They can also subscribe to the same event and trigger whatever logic they need to trigger.

Now notice very carefully services are not directly calling each other.

There is no direct coupling between the catalog service, the basket service, and whatever other services

we want to add.

No tight coupling.

So if one of the service is temporarily down, the message can still be delivered later.

This boost fault tolerance, scalability, and system responsiveness.

Then at the bottom you see that there is an event bus.

Actually could be implemented by other tools also.

So we are saying event bus here.

But we can use tools like RabbitMQ, Azure Service Bus or any other broker.

So this shows a decoupled architecture.

Briefly this pattern is the heart of event driven architecture enabling systems to scale and evolve

independently.

Now when should we use message queues?

When does it make sense to use the message queues?

Well, first we should understand that queues are great when we are dealing with bursty workloads.

If your system sometimes gets a sudden spike in requests like flash sales or traffic spikes, a queue

can help smooth these peaks by buffering all this load.

Also, these kind of systems shine when you need a decoupled service.

For example, if a front end app triggers multiple back end tasks, a queue allows each service to process

these tasks independently and at its own pace.

Also, this architecture is ideal for background jobs like sending emails, generating reports, processing

exports, all the things that don't need to block the user and can run asynchronously.

Queues are useful for rate limited or expensive operations.

So instead of hitting an external API too often, or running resource heavy computation right away,

you offload them to a queue.

So what happens is that the queue will modulate the speed of these operations based on whatever rate

it is allowed to do.

And finally, queues help absorb traffic spikes and avoid overloading the downstream Stream systems

by acting as a buffer.

It is very similar to the first point that we talked about.

So overall, if you want to make your system more resilient, decoupled and scalable, message queues

are a solid choice.

Now let's quickly compare two popular message brokers RabbitMQ and Kafka.

We will only have a 30,000ft overview.

We will not go into detail.

So RabbitMQ is a traditional message broker based on Amqp protocol.

It uses a push model where messages are delivered to consumers immediately.

It is very reliable.

IT support retries.

There are acknowledgments and it is very great for task queues, notifications and background jobs.

But once consumed by the consumer, messages are gone.

Kafka, on the other hand, is a distributed event streaming platform.

It uses a pull model, so consumers decide when to read.

So it stores messages in a log, and it also supports the replay.

So you can also replay the logs.

And consumers will decide when to pull these messages from this log and process them.

So this actually makes it perfect for things like event sourcing, analytics and stream processing.

Also, Kafka is highly scalable and it retains messages even after they are consumed.

So in short, use RabbitMQ when you want flexible routing and task queues, use Kafka when you need

durability, replays and high throughput.

So when dealing with messaging systems, delivery guarantees are crucial for designing reliable applications.

So what are some of the most used delivery guarantee models.

So first we have at least once.

This is the default in many systems.

Messages are retried until acknowledged.

It is a reliable model where the consumer will get the message at least once.

But it can cause duplicates.

So if the consumers don't send acknowledgement, the broker will send it again.

So there is a chance that the consumer will get it multiple times.

So it is a good idea for consumers to make the operation idempotent, meaning they handle the repeated

messages safely without any damage.

Then we have at most one strategy.

So the message is sent only once and no retries are attempted.

So it is fast, but risky because no one is waiting for the acknowledgement.

You might lose messages if something falls midway, and consumer did not get the message or was not

able to process the message.

Then we have exactly one.

This is the holy grail of the models.

It ensures that the message is processed once and only once, with no duplicates and no loss.

But it is very hard to implement and very resource intensive.

Kafka supports it, but only under very specific conditions.

So choosing the right guarantee depends on your system's tolerance for duplicates and losses.

This is how the critical operations on the consumer end will dictate which model to be used.

So some real world example of message queues.

The classic one is order processing, where you decouple the front end from back end services like inventory,

payment and shipping.

Then they are also great for logging and monitoring.

Pushing logs to centralized system for real time analytics is something where we can use cues.

Rate limiting can also be useful.

So cues help you in managing spikes by pacing the flow of the request, rather than overwhelming the

request by sending all the requests to the server.

It do some rate limiting at the queue level.

Then for notifications like emails, SMS that can be queued and sent asynchronously.

ETL pipelines.

I mean, especially with Kafka, queues actually enable a powerful real time data transformation and

streaming.

So these are some of the use cases that shows how queues and decoupled architecture enhance performance,

scalability and resilience across systems.

Now let's talk about some of the best practices when it comes to using message queues.

So when designing with message queues, we should always try to consider some of the best practices.

So first always make consumers idempotent since messages might be retried, processing them multiple

times should not cause any unintended effect.

That should be the very first thing.

Second, use dead letter queues to catch messages that will repeatedly.

This help you isolate and inspect the problematic payload.

Third, monitor queue length and processing time to detect bottlenecks early.

A growing queue can indicate troubles in downstream services, and you might need to scale up your downstream

services to process faster.

Then always handle retries and failures gracefully with exponential backoff or circuit breakers.

This will help you in avoiding the cascaded issues so your queue will not end up growing very huge.

Then choose the delivery guarantee wisely at least once is common, but sometimes you will need exactly

once or at most once also.

So look at your application requirements and depending on the business needs, choose the delivery guarantee.

And lastly don't forget security.

Use proper authentication and authorization and encryption to protect sensitive data moving through

your queues.

Now you can see some of the interview questions on the screen that can test your understanding of messaging

and queues.

Mastering these concepts and being able to articulate them clearly can set you apart in system design

interviews, especially for backend and distributed system roles.

So whatever we have covered so far, you should be able to answer these questions.

If not, I have also attached a PDF with the answers that you can refer.

Now let's quickly wrap up.

We have seen how asynchronous messaging is a powerful tool for building scalable and decoupled systems.

It helps systems stay responsive, even under load.

Then use cues when you don't need an immediate response, for example.

Background jobs are processing spikes in traffic.

Then RabbitMQ is something that works very well for traditional use cases like task distribution or

notification.

While Kafka shines in event streaming and real time analytics at scale.

Choosing the right delivery guarantee.

Whether it is at least once, exactly once or at most once depends on your system's tolerance for duplicates

and losses, and that will be defined by your business needs.

This concludes our lecture on message queues and decoupled architecture.

What's next?

Next we will explore concurrency and parallelism.

We will dive deeper into how we can make our services process things faster and more efficiently.

So I will see you in the next one.
