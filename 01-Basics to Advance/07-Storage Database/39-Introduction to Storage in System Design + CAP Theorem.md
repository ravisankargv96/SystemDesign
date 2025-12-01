And welcome to section seven of this course on Mastering System Design.

This section is all about databases and storage.

In this section, we are diving deep into how systems store, retrieve, and manage data.

One of the most critical aspects of any large scale architecture.

So here is what we will be covering in this section.

We will start with the big picture why storage matters and how it fits into the overall system architecture.

Then we will compare the relational database and various NoSQL models like key value, document, column

and graph.

Then we go deep into advanced database topic.

We will explore sharding, replication cap theorem and polyglot persistence.

These are the strategies used to scale database effectively.

Then we will learn how systems use services like Amazon S3 to handle large scale unstructured data.

Then we will go under the hood of how data is stored in the traditional and distributed file systems.

Then we will look at some of the big data fundamentals.

We will touch on how large scale data is processed and stored.

Introducing data lakes batch versus stream processing.

Then we will tie everything together with practical guidance on how to evaluate and choose the right

storage option for different use cases.

So let's get started with the first lecture on Introduction to Storage in System Design.

We are kicking things off with this foundational lecture because we want to cover the basics first and

then go into details.

So we all know storage is at the heart of almost every system, whether it's a messaging app, a banking

platform, or a content delivery network.

The way we store, retrieve, and manage data has a huge impact on system performance, reliability

and scalability.

In this lecture, we will explore the different types of storage.

We will dive into the structured versus unstructured data.

We will discuss the core storage properties like durability, consistency, etc..

And we will see how these decisions shape real world system design.

By the end of this lecture, you will have a strong understanding of why storage isn't just about saving

data, it is about architecting for scale, fault tolerance, and architecting for future.

So let's start with a very simple truth.

Every system generates and consume data, whether it's a user input logs, media file, or analytics.

But it's not enough to generate data.

We need a way to store it reliably, retrieve it efficiently, and manage it at scale.

That's where storage becomes foundational to system design.

Persistent storage is what powers features like user profiles, save preferences, watch history, shopping

carts, and even things like recommendations or analytics dashboard.

And it's not just about storing data.

Your choice of storage system directly impacts system performance, reliability, and cost.

For example, slow storage can bottleneck your response time, and unreliable storage can result in

data loss or downtime.

That's why thinking about storage early in the design process is very critical.

It should not be an afterthought, but it should be done early.

When we are building scalable and fault tolerant systems.

So to design effective storage solutions, it's important to understand the nature of the data we are

working with.

And that starts with the distinction between structured and unstructured data.

Structured data is highly organized and stored in a well-defined format.

Typically rows and columns.

Think of a SQL database table where fields like user ID, email, createdat, etc. exist.

The schema is predefined, which makes structured data easy to query using languages like SQL.

Unstructured data, on the other hand, doesn't follow a rigid schema.

It's flexible in format and often comes as images, videos, PDFs, log files, or social media posts.

You can't just run a simple SQL to get the data.

Instead, the data is stored in object stores or blob storage and analyzed differently.

Both types are common in modern systems.

For example, an e-commerce app might store user information as structured data and product images or

reviews as unstructured data.

Understanding this distinction help us choose the right storage technology and design for performance,

scalability and retrieval efficiency.

So now that we understand the type of data, let's explore the different categories of storage available

in system design.

Each one is optimized for a different use case.

First we have database storage.

This is your traditional SQL or NoSQL database used to store structured or semi-structured data.

SQL databases like PostgreSQL are great for strong consistency and complex queries, while NoSQL options

like MongoDB or Cassandra offer flexibility and horizontal scalability.

Next is object storage like Amazon S3 or Google Cloud Storage.

This is ideal for unstructured data such as images, videos, logs, or backup.

It is built for durability and scalability, and objects are accessed via APIs.

Then there is file storage, which provides a hierarchical file system like NFS or SMB.

It is commonly used in legacy systems or environments that need shared access to file over the network.

And then finally we have block storage.

And these block storages provide low latency, high performance access to raw storage blocks.

It is perfect for databases or virtual machines that need direct disk access and fast IO.

So choosing the right storage category depends on the data type, access pattern, performance needs,

and scale of our application.

So when choosing or designing a storage system, we need to understand the core properties that define

its behavior, especially in distributed environments.

So what are these core properties?

The first is durability.

This means that once data is written, it will persist even in the face of power loss, crashes, or

hardware failures.

A durable system ensures that your data won't just disappear.

Second is availability.

Availability refers to the system's ability to serve data when it is requested, even during partial

outages or node failures.

High availability is critical for systems that can't afford downtime, like payment platforms or messaging

apps.

Then comes consistency.

Consistency ensures that every read reflects the most recent write.

In simpler terms, once you update something, say user profile or any amount in your account table,

anyone fetching that data sees the latest version.

And then finally, and optionally, we also should talk about atomicity, which is especially relevant

in transactional systems.

It means operations are either all or nothing.

Either everything succeeds or nothing succeeds.

This is vital when you are updating multiple records and system need to stay in a valid state even after

the update.

So these properties durability, availability, consistency and atomicity forms the foundation of evaluation

when it comes to finding trade offs and selecting the right storage mechanism for our application.

So in the real world, storage design is all about trade offs because unfortunately there is no silver

bullet that gives you everything.

So you often have to balance three key factors scalability, reliability, and performance.

Scalability means that the system can handle increased load, more data, more user, more requests

without breaking down.

It is essential for growing systems.

Reliability is all about ensuring that the system continues to function even when parts of it fails.

It could be done either through replication, failover mechanism, and strong data guarantees.

Performance refers to the fast system access how fast system can read and write data, which directly

impacts user experience and back end responsiveness.

But there is a challenge.

Optimizing for one of these usually comes at the expense of the other.

A super performance system might not scale well.

A highly reliable system might involve latency due to replication overheads.

So what to do?

Well, every architectural decision comes down to what your system needs most and where you are willing

to compromise.

So this is where system designers add real value by making smart, context driven trade offs that align

with business goals and technical realities.

Now, one of the most important concept in distributed systems is the Cap theorem, and it directly

impacts how we design and choose our storage system.

So Cap stands for consistency, availability and partition tolerance.

This theorem states that in any distributed system, you can only fully guarantee two out of three at

any given point of time.

So let's try to break it down.

Consistency means every read returns the most recent write.

No stale data is coming back.

Then availability means every request gets a response, even if it's not most up to date.

And then finally, the most confusing one partition tolerance means that the system continues to operate

even if there is a network failure Layer or some nodes can't communicate.

What it means is if your database is partitioned and it exists at multiple nodes, your system should

still be operational if some of the nodes are not available.

It could be due to network failure or the nodes failure itself.

That is called partition tolerance.

Now what is the catch?

According to Cap theorem, you can't have all three at once.

In the presence of a network partition, which is almost inevitable in the large scale systems.

So you are forced to choose between consistency and availability.

So different systems make different trade offs.

Some prioritize consistency and partition tolerance.

Others choose availability and partition tolerance.

And the systems that offer consistency and availability but does not tolerate partition are very rare,

but are not really distributed.

Understanding this Cap theorem help us make smart architectural choices based on the system's tolerance

for stale data downtime and failures.

So now that we have seen what a Cap theorem is, let's look at how different systems make tradeoffs

between consistency availability and partition tolerance.

So first we have CP systems which guarantee consistency and partition tolerance.

These systems prioritize data correctness over availability.

During a network partition, the system may reject requests to avoid serving stale or incorrect data.

A great example of this is HBase, which is a distributed, strongly consistent store.

If a node can't confirm a write across replicas, HBase simply won't serve any of that data, even if

it means temporarily being unavailable for the user.

So CP systems are ideal for financial services, banking and systems where data integrity is non-negotiable.

Then we have AP systems, which guarantees availability and partition tolerance.

These systems will always try to stay online and serve requests, even if that means that returning

stale or eventually consistent data is acceptable.

DynamoDB is a great example here.

It embraces eventual consistency to keep system responsive and highly available.

AP systems work well for use cases like social media feeds, product catalogs, or media delivery,

where it is okay to sacrifice strict consistency to keep things running smoothly.

And finally, we have CA systems, which guarantees consistency and availability, but only if there

is no partition on network.

So in a distributed system that is not possible.

So this trade off is rarely practical in real world environments.

If you have a distributed system, however, in a non-distributed system like a standalone PostgreSQL

database, which has only single node running standalone on a system, we can achieve CCA because this

system is consistent and available as long as there are no failures in the underlying infrastructure.

That is why CCA systems are sometimes called the unicorns of Cap, because they are very beautiful in

theory.

But it is not impossible.

I mean, not possible to achieve in real world.

The key takeaway here is understanding where your system sits on the Cap theorem help you design for

the right trade off, depending on whether data correctness is important.

Uptime is important or fault tolerance is important for your application.

Now let's look at some of the real world use cases that ties everything together, also showing how

different types of storages are applied based on kind of data and system needs.

So first, e-commerce platforms, these often deal with both structured and unstructured data.

The product catalog with prices inventory SKUs typically uses a relational database or a structured

NoSQL storage.

But all those product images and videos, those are best handled through object storage like Amazon

S3 or Azure Blob Storage.

Next, we have streaming services Netflix, Spotify, the actual media files, movies, songs, thumbnails.

They are huge files and unstructured data.

So these are stored in the object storage for durability and efficient delivery.

While user preferences, watch history and playback settings are often stored in NoSQL database for

fast reads and flexible schema.

Then there are log aggregation systems used in observability and monitoring.

So these generate massive, massive amounts of semi-structured or unstructured data.

Most of the time.

So this data might go into a time series database like influx or column store like Clickhouse for fast

analytics.

Or it might be dumped into object storage also for cost effective archiving and batch processing later.

So you can see storage isn't one size fits all.

And that's what I wanted to communicate from this slide.

Each use case demands the right combination of storage model to balance performance, scalability,

and cost.

So before we wrap up this lecture, let's take a moment to reinforce what we have learned with a set

of interview questions.

So take a moment to read through them and try to understand what each question is trying to ask.

These questions are very important in real world interviews and in actual system architecture when you

are working on it, you are expected to make informed storage choices, and these questions will help

you by understanding durability, availability, consistency, and when to use what type of storage.

Whatever we have covered so far in this lecture, you should be able to answer them confidently, but

I have also attached a PDF with details.

Answer.

Feel free to use it as reference.

Now, before we conclude, let's look at the summary and key takeaways of today's lecture.

First and foremost, storage is foundational in every system.

Whether you are building a tiny app or a global platform, how you store and retrieve data will directly

impact your system's performance, scalability, and reliability.

Understanding your data is step one.

It is structured like user profiles and transactions or if it is unstructured images, videos, and

logs.

This Distinction influences the type of storage we should use.

Then we explored several storage types from database object files block storage, each with unique trade

offs in durability, availability, consistency, and scalability.

One of the key takeaways is that there is no universal best choice.

Real world systems often use a combination of storage types to meet diverse needs.

For example, a system might use a SQL database for transaction object storage for media, and NoSQL

for fast lookups.

That is entirely possible.

So we have to make a decision based on our system requirements and needs.

That is the key takeaway for this lecture.

So what's next?

In the next lecture, we will go deeper into database models and explore the big debate SQL versus NoSQL

which to use when and how to design for your system needs.

So I will see you in the next one.
