Hello and welcome to this lecture on advanced Database Topics.

The topics that we are going to discuss in this lecture are critical areas which are in system design

interviews and real world architecture.

In this session, we are going beyond Crud operations and diving into how large scale systems manage

growth, performance and resilience.

We will explore powerful concepts like scaling for databases, sharding, replication, and polyglot

persistence.

These concepts are foundational for building high availability, globally distributed and scalable system,

and they come up very often in technical discussions also, especially when designing real world architecture.

So let's get started.

So let's start with discussion on scaling strategies, especially for databases.

We are comparing two fundamental scaling strategies vertical scaling and horizontal scaling and how

they relate to SQL versus NoSQL SQL databases.

So let's start with vertical scaling or scale up.

This is the approach traditionally used with SQL databases like MySQL, PostgreSQL, Oracle and SQL

server.

It means increasing the capacity of a single machine.

Adding more CPU, Ram, SSD to handle more load.

It's a simpler architecture to manage and you get strong consistency thanks to acid properties.

However, the downside is that it is limited by hardware.

You can only scale up so much before hitting a wall.

Also, cost increases non-linearly and the systems become a single point of failure.

But what about horizontal scaling or scaling out?

Well, this is the domain of NoSQL databases like MongoDB, Cassandra, and DynamoDB.

Instead of making one machine more powerful, you add more machines to the cluster to handle load and

data distribution.

It's far more elastic and better suited to modern high traffic applications.

It can scale globally, handle big data, and offer better fault tolerance by design.

But it comes with complexity.

Distributed systems are harder to manage, and they often trade off strong consistency for eventual

consistency.

To stay available and scalable.

So in short, SQL systems favor simplicity and consistency, while NoSQL systems shine when scaling

is your top priority.

Your architecture choice here directly influence how your system behaves under real world traffic and

data growth.

So now let's talk about replication, one of the core strategies used in distributed database systems.

At the basic level, replication means copying data from one database node to another.

This can be across the same data center or spread geographically around the world.

So why is replication important?

Well, it provides some critical benefits.

First, it adds fault tolerance.

If one node goes down, others can take over.

Second, it helps improving read performances, especially in high traffic systems.

We can allow reads to be distributed across multiple replicas, which will improve the performance.

And third, it improves data availability, ensuring that users can access data even during failures

or spikes in demand.

But like everything in distributed systems, replication involves tradeoffs, especially when viewed

through the lens of Cap theorem.

Most real world replication strategies favor availability and partition tolerance, but that often means

that we sacrifice strong consistency.

For example, replicas may lag behind the primary node, leading to eventual consistency.

So while replication improves scales and resilience, we have to design carefully depending on what's

more critical for our use case strong consistency or always on availability.

So now let's dive into one of the most common replication models.

It is called leader follower replication, also known as primary replica or master slave replication.

So here is how it works.

All write operations go to a central node called the leader.

The follower nodes receive replicated data from the leader and are typically used to handle read operations

only.

This model helps offload read traffic from the main database, making it easier to scale read heavy

applications.

But there is a key consistency consideration to keep in mind, especially around asynchronous replication,

if the replication from leader to followers is asynchronous.

There can be a lag between when the right is committed to the leader and when it appears to the follower.

This means a read from follower may return stale data depending on the replication delay.

That's where tradeoffs between consistency and availability become more important.

Leader follower replication is widely used in production systems because it offers a solid balance between

performance and fault tolerance, but it needs thoughtful handling of read consistency.

Now there is this another strategy called read replicas, a specialized form of replication often used

in large scale systems.

The main use case of read replicas is to scale read heavy workloads.

When you have millions of read requests per second, like a content heavy app, news feed or product

catalog, read replicas help to distribute that load and reduce latency.

Now how are read replicas differ from full blown leader follower replication?

We looked at leader follower and we are talking about read replicas, but there has to be some difference,

right?

Read replicas are not involved in write operations.

All right.

Still go to the primary node.

Their purpose is purely for load balancing and read traffic.

In many architecture, you can add or remove read replicas dynamically to adjust your traffic spikes.

This approach improves read scalability without introducing the complexity of full replication topologies.

However, like before, there can still be replication lag.

So if your application needs to have up to the second accuracy, you need to plan accordingly.

Read replicas are a key tool in modern systems, especially when you want to scale without compromising

performance or overloading your primary databases.

Now let's move into the world of sharding, one of the most important techniques for scaling database

horizontally.

At its core, sharding means splitting your data across multiple databases or database nodes, which

we call shards.

Each shard contain a subset of the whole data, and collectively they represent the full data set.

So why do we need sharding?

Well, as our system grows, a single database node starts to hit limits both in terms of storage capacity

and performance.

Reads and writes starts to slow down.

Disk usage grows and the system becomes harder to scale vertically.

Sharding solves this by distributing the load.

So instead of having one massive machine to do all the work, you spread it across many smaller ones.

This allows systems to handle massive data sets and millions of users efficiently, especially in write

heavy environments.

There are mainly two types of sharding.

Horizontal sharding, which is the most common type of sharding is means splitting rows across different

shards.

For example, users with IDs, let's say 1 to 1000 go to shard A, then users with ID 1000, 1 to 2000

can go shard B, and so on.

It is ideal when the data set gets too large to fit on one single node.

Then we have vertical sharding.

What vertical sharding does is that it splits the data by feature or function.

For instance, user profile data might live on one shard and billing or analytics data can be on another

shard.

This is useful when different parts of your application have very different load characteristics.

Both are valid approaches and often used together in mature systems.

But while sharding gives you scalability, it also brings complexity in terms of data placement, query

routing, and consistency.

So now that we understand what sharding is, let's explore some of the most commonly used sharding techniques

and the trade offs that comes with each one of them.

So first is range based sharding.

This is a simple strategy where we split the data by value ranges.

For example, that we have seen users with ID 1 to 1000 go to a shard 1001 to 2000 go to shard B, and

so on.

It is easy to implement and intuitive, but it can lead to hotspots, meaning some shards get overloaded

while others remain underutilized, especially if the IDs are sequential or access patterns are skewed.

Then we have hash based sharding.

So instead of assigning data based on ranges, we use a hash function on a key like user ID to decide

which shard it goes to.

This help to distribute data evenly across all shards, reducing the risk of hotspots.

But there is a downside it becomes much harder to perform range queries because now the related data

may be scattered across multiple shards.

And I think when we are talking about hash based sharding, it is also important to talk about consistent

hashing.

So what happens in traditional hash based sharding is that you add or remove a node, the hash function

output changes, and then you have to remap almost all your keys, which is very inefficient.

So if let's say you remove a node or add a node in your cluster, the hashes will be calculated again

and the data will move from one node to another.

Because now the hash function is giving a different value.

To solve this, we use consistent hashing instead of rehashing everything.

Consistent hashing ensures that only a small subset of keys needs to move when the node is added or

removed.

This enables better elasticity and make sure your sharding strategy is much more resilient to scaling

and failures.

Consistent hashing is a key technique used in large scale distributed systems.

Finally, we have geo based sharding.

This strategy assigns data to shards based on geographical regions.

For example, users in Europe go to one shard, Asia to another, and so on.

This improves latency and compliance in geo distributed applications like content delivery or social

media, where proximity matters.

So we have seen each strategy has its strength, and often real world systems combine multiple strategies

for optimal performance and flexibility.

Stability.

The key is choosing based on your data access pattern, scalability needs, and fault tolerance goals.

Now let's talk about a modern design principle that is becoming increasingly common in large scale systems,

and that is called polyglot persistence.

So what is it?

Polyglot persistence means using different types of databases for different parts of your system or

application.

Instead of forcing one database to do everything.

You pick the right tool for each job.

But why do we do this?

Because no single database is perfect at everything.

You need to store and query complex relationships.

Then use a relational database.

You need a full text search.

Use Elasticsearch.

You need to scale writes or store flexible data structure.

Use a document store like MongoDB or a key value store like DynamoDB.

So the key benefit of this approach is performance optimization.

Each database is tuned for a specific purpose.

So your queries are faster.

Your storage is leaner and your architecture is much more scalable.

This also allows you to decouple services, letting each service choose its own ideal storage layer.

So in short, polyglot persistence is using the right database for the right job.

And it's the hallmark of robust production grade system design.

You will see this pattern used in companies like Netflix, Uber, and Amazon, where microservices,

architecture and diverse workload make it the only scalable choice for persistence.

Now we have few interview questions listed on the screen.

These questions are frequently asked in system design interviews to evaluate your understanding of data

scaling, distributed consistency, and modern database architecture choices.

If you have followed along with the lecture, you should now be able to answer each of them confidently

and to make your preparation easier.

I have also attached a PDF with detailed answers to these questions, so use it as a study resource

for the interviews.

Now, before we conclude, let's wrap up everything that we have covered in this lecture on advanced

database topics.

First we looked at the database scaling strategies, how vertical scaling works well for traditional

SQL systems, how horizontal scaling provides NoSQL systems with modern distributed databases.

We then explored replication, including key strategies like leader, follower, and read replicas,

and how it helps to improve the fault tolerance and read performance.

Then we moved into sharding.

Understanding how breaking your data into logical shards helps with scale and performance.

We also discussed various sharding strategies range based, hash based, geo based, and we talked about

how consistent hashing helps system stay elastic and fault tolerance.

Finally, we covered polyglot persistence, the idea that using different types of databases for different

needs leads to a better performance, flexibility, and maintainability in large scale systems.

These concepts are critical not just in production architecture, but also in system design interviews.

In interviews we are demonstrating this kind of knowledge shows how you can design scalable and resilient

systems.

So this concludes this lecture on advanced database topics.

What's next?

In the next lecture we will shift gears from databases to object storage.

How it works, where it fits into the modern architecture, and why it's essential for handling large

scale unstructured data like media file logs and backups using object storage.

So I will see you in the next one.
