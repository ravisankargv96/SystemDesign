Hello and welcome to this lecture on understanding Database Models SQL versus NoSQL.

So we know databases are at the heart of nearly every system we design, from storing user accounts

and product catalogs to managing massive analytics pipeline.

In this lecture, we will break down the two major paradigms of data storage relational and non-relational.

Or some call it SQL versus NoSQL.

We will try to understand how, when and why to choose one over the other.

We will also touch on the concepts like acid and base properties, introduce NoSQL subtypes like document

stores and key value databases, and revisit the Cap theorem from a database perspective.

By the end of this lecture, you will be equipped to make smarter choices by selecting databases in

real world system design scenarios.

So let's get started.

So what is a database?

So let's start with very basic a database is simply a structured way to store, retrieve, and manage

data.

It allows us to persist data over time, even after a system shutdown or restarts.

More than just storage.

A good database provides tools for efficient querying so we can find exactly what we need, whether

that's a user profile, product listing, or a transaction record.

Databases are core to backend systems.

Whether you are building a simple to do list app or a large scale e-commerce platform.

Some form of database is always needed.

So in short, if your system handles data and most of them do, it needs a database.

So now let's look at relational database.

The traditional and still very widely used type of database systems.

So examples of relational databases are MySQL, PostgreSQL, Oracle SQL server.

And these all are SQL based databases, meaning they use Structured Query Language to read and write

the data in relational database.

Data is organized in tables with rows and columns, pretty much like a spreadsheet that we have.

What sets them apart is their strict schema.

Before inserting any data, you need to define exactly what fields each row must contain and what data

types are allowed.

This structure brings benefits like data integrity, relationship between tables, and powerful querying

capacity.

Using joins, filters, and aggregations.

So what are the core building blocks of a relational database?

The concept that makes them very reliable and powerful is first schemas.

A relational database is schema based, meaning the structure is predefined.

You must define tables, their columns, their data times upfront.

This ensures consistency in how data is stored and accessed.

Next joins.

One of the strengths of relational databases is the ability to combine data from multiple tables using

joins.

For example, joining a user table with an order table can get you all the orders placed by the users.

And finally, the asset properties, which guarantees safe and reliable transactions.

We have looked at the asset properties in the previous lecture also, but let's do a quick recap.

Asset stands for first atomicity, meaning all the steps in a transaction succeed or none do.

Like transferring money between accounts.

C is for consistency.

It ensures that the database never enters an invalid state.

All rules and constraints are enforced.

Isolation transactions don't interfere with each other even when they are running concurrently.

And then we have durability.

Once a transaction is committed, the change will persist even after the power loss or system crash

happens.

These properties are key to maintaining the trust in systems, and systems become more accurate and

consistent.

We can use such databases in areas that require strong consistency like finance, healthcare, and inventory

management.

But okay.

Relational databases are powerful, but they are not always the right tool for every use case.

So let's look at where they fall short first.

Rapidly changing or schemaless data in systems where structure of the data changes, often like adding

new fields dynamically, relational databases can become rigid and a little hard to maintain.

Second, scaling horizontally is not possible.

Traditional SQL databases are not designed for easy horizontal scaling.

Scaling out across multiple nodes requires complex sharding or replication strategies, and consistency

becomes a little harder to manage in relational databases.

Third, nested or flexible data formats are not supported.

If you need to store deeply nested or variable data like JSON blobs, arrays, or documents, relational

tables can feel unnatural and become a little clunky also.

This is where NoSQL databases start to shine because they offer more flexibility, scalability, and

performance for certain types of workloads.

So let's now explore NoSQL.

It's a broad category of databases designed for flexibility, scalability, and high performance.

Unlike relational databases.

NoSQL systems are often schemaless or allow a dynamic schema, meaning you can store data without defining

a rigid structure upfront.

This makes them great for handling evolving or unstructured data.

There are several types of NoSQL databases, and each one is optimized for a different use case.

So first is document database like MongoDB, which stores data as flexible JSON like documents.

It is perfect for nested and varied data.

Then we have key value stores like Reddis or DynamoDB.

They offer lightning fast reads and writes, mapping unique keys to values, so they are ideal for caching

system session data and simple lookup data.

Then we have columnar databases like Cassandra or HBase.

They store data in columns instead of rows, optimized for analytics and high write workloads.

Then we have graph databases which are tailored for relationships.

Great for social networks, recommendation engines and fraud detection.

But when it comes to NoSQL, NoSQL isn't one size fits all.

It's a toolbox of models designed to handle the need that relational databases usually struggle with.

So now let's take a closer look at the four main types of NoSQL databases.

And remember, each one is tailored for specific data needs and patterns.

So let's start with document database.

So document databases store JSON like documents.

These documents can have nested fields arrays and varying structure.

These kind of databases are perfect for use cases like user profiles, content management, or anywhere

you need to store rich and flexible objects.

Then we have key value databases like Reddis or DynamoDB.

These are ultra simple databases.

Think of them as a giant hash map.

You store and retrieve values using a unique key.

These are great for caching, system session storage, or any scenario that requires high performance

and low latency.

Then we have columnar databases.

Cassandra or HBase.

These databases organize data by columns instead of rows.

This makes them ideal for large scale analytical queries like processing logs, time series data, or

running aggregation on billions of records.

And then we have graph databases such as Neo4j's.

These databases specialize in modeling complex relationships.

They use nodes and edges to represent entities and their connections.

Ideal for social graphs, recommendation engines, and fraud detection.

So anywhere where the relationships are as important as the data itself, you use graph databases.

So the key takeaway is to choose the NoSQL model that matches your access pattern and data shape.

Don't just stick to one and keep using it for everything, because one size doesn't fit all when it

comes to NoSQL.

NoSQL databases often relax.

The traditional consistency guarantees in favor of availability and scalability.

So we talked about acid properties in case of relational databases.

But in case of NoSQL, HBase properties comes in which is an alternative to Acid properties of relational

databases.

So let's break down what HBase stands for.

So b a is basically available.

The system in NoSQL is designed to always return a response.

Even during failures of partition the response might be a little stale or incomplete.

But you won't get a system error.

Then S stands for soft state.

The state of the system may change even without new input because of eventual synchronization between

distributed nodes.

This means different replicas might temporarily show different values, but they will have the data

eventually without any user action.

The missing data.

Which brings to E!

Eventually consistent.

All updates will propagate through the system.

Over time.

The data will become consistent eventually, though not necessarily right away.

So why is this important?

Well, based systems trade strong consistency for availability and partition tolerance, which is often

more suitable for web scale applications where uptime is more critical than immediate accuracy.

So let's revisit the cap theorem once again.

We know it's the foundational concept in distributed systems, and it has a direct impact on how SQL

and NoSQL databases are designed.

So let's take a reminder.

Consistency in Caps stands for every read receives the most recent writes.

We don't get stale data availability.

Every request receives a response without guarantee of this being latest.

We will respond, but the data could be stale.

Partition tolerance the system continues to function despite network failure between nodes.

So the theorem states that the presence of a network partitioning a distributed system must choose to

become either consistency or availability, but it cannot choose both.

So where do our database models, relational and NoSQL fall on this spectrum?

SQL databases, especially in distributed settings, tend to favor consistency and partition tolerance.

They prioritize data accuracy.

Even if that means that temporarily unavailable be during a partition failure.

Whereas NoSQL databases often lean toward availability, so they prioritize availability and partition

tolerance so they will be always online, even if it means seeing stale data.

But eventually consistent data will be available.

This works well with the base model that we have just discussed in the last slide.

So relational databases have consistency and partition tolerance.

CP and NoSQL databases have availability and partition tolerance which is AP.

This trade off is crucial in system design and its wide different use cases demand different storage

strategies.

Now when to use what?

The natural question that we are now asking ourself is that if we have a problem?

Should we use SQL or should we use NoSQL?

So let's start with the SQL.

Relational databases will shine when you need complex queries and joins across multiple tables.

Second, strong consistency is non-negotiable, like banking applications or inventory systems.

Third, your data is structured and follow a known schema like customer records, transactions, orders.

So banking systems, ERP platforms, CRM tools, and inventory management can use SQL databases or relational

databases.

On the other hand, we should use NoSQL when our system needs to scale horizontally to scale large traffic

or data volume.

Second, we are dealing with flexible, evolving or nested data structures such as user profiles, product

metadata, or logs.

Where the data structure is not fixed, it will keep on evolving or the data is nested within each other.

Third, we require low latency access or high throughput rates, such as in caching layers or real time

analytics.

So most of the IoT platforms, recommendation engines, social media feeds and logging systems use NoSQL

databases.

So, but what happens in reality is that many modern architectures use a polyglot persistence approach,

which means they combine both SQL and NoSQL based on specific needs in different parts of the system.

So some parts of the system will keep using the relational database, and some parts of the system keep

using the NoSQL database.

And there could also be a possibility that they are using different types of NoSQL databases for different

parts of the system based on need.

This is known as polyglot persistence, and modern applications do use polyglot persistence approach

a lot.

So now we have some of the key interview questions visible on the screen.

These questions test your understanding of relational versus non-relational databases, how they behave

under different conditions, and when to use each model.

So if you have followed along with this lecture, you should be able to answer each of these confidently,

either in interviews or while making an actual architectural decision.

Also, a PDF with detailed answers is attached for your revision and practice.

Okay, so before we wrap up, let's try to look at the summary and key takeaways of this lecture.

First, both SQL and NoSQL databases are critical tools in a system designer's toolbox.

Each has unique strengths and is best suited for different kinds of workloads and data structures.

When deciding which to use, consider your need for strong consistency.

the complexity of queries and whether your data is structured or not.

If you need horizontal scalability, can you work with the eventual consistency?

How flexible your data structure and schema should be.

These are the factors that will define what to choose.

Also, remember you do not have to choose just one.

Most real world systems today use a polyglot persistence strategy, combining both SQL and NoSQL databases

depending on the use case of the application.

So this concludes our lecture on relational versus non-relational databases.

What's next?

We will build on this foundation by diving into more advanced database topics like sharding, replication

and polyglot persistence, which are keys for building scalable and resilient systems at scale.

So I will see you in the next one.
