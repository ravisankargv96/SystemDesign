Hello everyone, and welcome to this lecture on database performance Optimization technique.

In this lecture, we will be diving into various strategies and best practices for optimizing database

performance.

As you know, database at the core of most modern system and ensuring they perform efficiently is key

to building scalable and reliable applications.

By the end of this lecture, you will have a solid understanding of how to optimize your database for

performance in real world applications.

So let's get started.

Let's begin with a recap of replication that we have already seen.

So what is replication?

Replication refers to the process of copying and maintaining database objects in multiple places.

This is done to ensure data availability and reliability across different systems.

Why to replicate?

Well, there are several key reasons why replication is essential.

First is high availability.

It ensures that data remains available even in case of system failures.

If one database goes down, another can take over.

Second is load balancing.

Replication allows us to distribute read traffic across multiple servers, which helps to reduce the

load on any single server.

Then we have disaster recovery with multiple copies of data in different locations.

Replication ensures that system can recover quickly in case of disaster.

Then what are different types of replication?

Well, there is master slave replication.

In this setup there is one primary database the master, and multiple read only replicas.

The slave all writes happen to the master and reads are distributed among the slaves.

Then we have master.

Master replication.

Here, multiple databases act as primary sources capable of handling both reads and writes.

This setup is used for redundancy and fault tolerance, allowing both write and read operations to be

handled by multiple nodes.

Replication is critical for maintaining both performance and reliability in large scale systems, especially

when high availability and load balancing are very important.

Now let's talk about sharding and partitioning techniques.

We have looked at them in the database section, but we are going to recap it quickly because they are

also important for performance in database when it comes to scale.

So what is sharding?

Sharding is the process of splitting a large dataset into smaller, more manageable pieces known as

shards.

The goal of sharding is to distribute data across multiple servers to achieve better performance and

scalability.

Instead of putting all the data in a single server, we break it up to spread the load.

For example, imagine we have a global user base.

We could split user data across multiple shards based on geographical region, one shard for us, another

for Europe, and so on.

This helps us ensure that our database remains responsive even when the number of users grows exponentially.

Then we have partitioning.

This is similar to sharding, but typically done within a single database.

Partitioning involves dividing data within a single database into separate tables or partitions.

Think of it as organizing data into different drawers, where each drawer hold a portion of the complete

data set.

So there are two common types of partitioning.

One is range partitioning.

This involves splitting data by ranges of values.

For example, you could partition data by date where each partition holds data for a specific time period.

Then second is hash partitioning.

Here, data is split based on a hash function applied to a key.

For instance, if partition user data by user id, we can hash the ID and store it in a specific partition.

This ensures that the data is evenly distributed across partitions.

Both sharding and partitioning are designed to optimize scalability and performance by breaking down

large datasets.

Sharding is done across multiple servers, while partitioning is typically done within a single server

or database.

Each method has its benefits depending on your architecture and workload needs.

We should try to choose which one is better for us.

Now let's quickly revisit cap theorem with a focus on performance.

So what is the Cap theorem?

The Cap theorem outlines the three key properties of distributed systems.

Consistency.

This means that every node in the system sees the same data at the same time.

So if one node is updated, all the other nodes must reflect the change instantly.

Then we have availability.

Every request to the system must receive a response even if some nodes are down.

The system is designed to be always available.

Then we have partition tolerance.

This ensures that system can continue to operate even in the case of network failures or partition between

nodes are not able to communicate to each other.

The system can handle communication breakdowns between different parts of the system gracefully.

Now, what Cap theorem says is that you can have any two of them and not the three of them.

So in case of distributed system, since partition tolerance is required, we could either have availability

and partition tolerance or consistency and partition tolerance.

So we could have either AP systems or CP systems.

Now from a performance perspective, when we talk about performance in distributed system, there is

often a trade off.

In a real world application, especially as systems are scaling, you will need to decide whether to

compromise on consistency or availability to decide what performance level you want.

For example, in a highly distributed system, you may decide that it is okay if not every node is perfectly

consistent as long as the system remains available and tolerant to partitions.

This approach tends to prioritize availability and partition tolerance over consistency to ensure that

the system performs well under a heavy load or network failures.

So there could be other side of the spectrum also that you want strong consistency along with partition

tolerance, like in banking applications where it is okay to be not available, but it is not okay to

have the inconsistent data going to the user.

In summary, the Cap theorem helps you understand the trade offs that we need to make when building

highly distributed systems for better performance at scale.

Many systems choose to optimize for availability and partition tolerance rather than consistency, but

choose consistency when you cannot afford to have wrong data.

Going back to the users.

Now let's dive into indexes.

What are its types and use cases?

What are indexes?

Well, an index is essentially a data structure designed to improve the performance of queries.

It works by allowing the database to find data more efficiently without having to scan every single

record.

Think of it as like the index at the back of the book, helping you quickly locate specific information

rather than flipping through all the pages.

Then there are different types of indexes, like B-tree indexes, hash indexes.

So what are these B-tree indexes?

Store the indexes in form of a B-tree.

These are most commonly used indexes.

They are great for exact match queries like where ID equals to five.

And they are also great for range queries like where ID is greater than zero that we are passing.

B-tree allows the database to quickly navigate between range of data, making them efficient for many

different types of queries.

Then we have hash indexes.

They are used primarily for equality comparisons, like where name equals to Rahul.

Hash indexes are very fast for looking up exact values, but they don't support range queries.

They are best used when you know that you will be performing exact matches in queries.

Then we have full text indexes.

These are used to optimize queries on large textual data, such as searching for a word within a paragraph.

For example, if you are building a search engine on an application with extensive textual data, full

text indexes can make those searches significantly faster.

Then we have bitmap indexes.

These are useful when you have low cardinality columns columns with the small number of distinct values.

For example, a column that represents gender or status.

So these columns would benefit from the bitmap index because it's quick and space efficient for columns

with only a few distinct values.

So when should we use indexes?

First is when we have read of heavy operations.

If your system performs many read queries using index can dramatically speed up query performance,

reducing the time it takes to fetch the data.

Then in write heavy systems, we have to be very cautious because if we are using indexes in systems

where you are performing a lot of inserts and updates, then we have some performance issues.

So while indexes improve read performance, they come at a cost on time of write performance.

Each time data is written to the database, the indexes needs to be updated as well, which can slow

down the entire operation.

So in summary, indexes are a powerful tool to improve query performance, but you need to consider

your system's workload, read heavy systems or write heavy systems.

What kind of system do you have?

Read heavy systems will benefit most from indexes, while write heavy systems require careful management

of how and where indexes are applied.

Now let's talk about normalization and denormalization.

The two crucial concepts in database design.

So what is normalization.

The main goal of normalization is to reduce data redundancy by organizing data into separate tables.

You break down large, complex tables into smaller related ones to eliminate repeated data.

What are the benefits of normalization?

It helps minimize storage cost and eliminate anomalies like update, insert, or delete anomalies.

It ensures that data integrity and consistency remains across the system.

However, normalization can lead to complex joins when retrieving the data, which can result in slower

read performances because the database has to combine data from multiple tables.

This is the drawback of normalization.

Denormalization, on the other hand, involves introducing redundancy back into the database.

The goal is to reduce the number of joins required by storing related data in a single table.

So what are the benefits of Denormalization?

Well, Denormalization can improve read performance, especially in reporting systems when we are dealing

with read heavy workloads.

Because the data is already pre-joined, it makes it faster to retrieve.

But there are some drawbacks to it.

The drawback is that it leads to increased storage requirements and potential data anomalies.

Since the data is repeated, updates, inserts, or deletes can become more complicated and error prone

because we have to update multiple tables, especially the Denormalized tables.

So when to use normalization and when to use denormalization.

Normalization is ideal for transactional systems where data consistency and integrity are the primary

focus.

Think of systems where you frequently insert, update, or delete records like e-commerce platforms

or banking applications.

Denormalization is better for reporting systems or read heavy workloads, where performance and fast

query response times are priority.

Denormalization work well in a system that need to perform lot of Select queries, such as data warehousing

or business intelligence systems.

So to summarize, whether to normalize or denormalize depend on your system's use case normalization

helps with data consistency, while Denormalization improves read performance at the cost of increased

storage and potential data anomalies.

Now let's discuss an additional technique for performance in.

When it comes to databases called connection pooling, it's an important technique for managing database

connections efficiently.

So what is connection pooling?

Connection pooling is a technique used to manage database connections by reusing established connections

instead of constantly creating new ones.

It's very similar to thread pool.

Essentially, a connection pool is a set of pre-established database connections that are kept open

and available for use.

Why to use it?

Well, the main advantage of connection pooling is that it reduces the overhead of frequently creating

and closing the database connections.

Opening a new connection to the database can be a time consuming operation, and with a large number

of requests, this can add significant delays.

With connection pooling.

You can avoid this overhead by reusing connections that are already open.

It allows for efficient handling of a large number of concurrent connections, making it ideal for systems

that need to scale and handle many simultaneous database requests, such as web applications or microservices.

So, in short, connection pooling improves both performance and scalability by reducing the time spent

in establishing new connections and enabling the systems to efficiently manage multiple simultaneous

database connections.

Then we have one more technique for performance called query optimization, and it's all about improving

the performance of our SQL queries.

So query optimization is the process of improving the performance of SQL queries, especially when working

with large data sets.

The goal is to reduce query execution time and make your database interactions as efficient as possible.

So what are the techniques of query optimization, we have looked at the use of indexes, which is one

of the most effective ways to optimize queries.

Indexes speed up search operations by allowing the database to quickly locate the data without scanning

every row.

Then we have this notion of avoiding n plus one queries.

The n plus one query problem occurs when your application makes one query to get a list of results,

and then for each result, it makes additional query.

This leads to many unnecessary database heads.

To avoid this, use joins or batching of queries to fetch all the necessary data in fewer calls.

Then there is this technique of using proper joins.

Well, we know that joins are essential for combining data from multiple tables.

But complex joins, especially with many, many tables can slow down your queries.

So minimize the use of complex joins whenever possible and ensure that your joins are efficient.

Also, always ensure that your tables are indexed on the columns that are being joined.

So by applying these techniques, you will ensure that your queries run more efficiently, especially

in production systems with large data set and heavy traffic.

Efficient queries improve not only the performance, but also the scalability and responsiveness of

your application.

Then we have this notion of materialized views, a very powerful technique for improving query performance,

especially in reporting systems.

So what is a materialized view?

A materialized view is essentially a pre-computed query result that is stored as a table.

Unlike a regular view which is computed on demand.

A materialized view stores the result of a query, allowing you to quickly retrieve pre-aggregated or

pre-computed data.

So what are the benefits?

Well, first it speeds up the query performance.

Since the results are pre-computed and stored, querying a materialized view is much faster than recalculating

the results from scratch each time.

This is particularly helpful for complex aggregations or joins.

Then it avoids the real time computation, so it eliminates the need for real time computations.

Reducing the load on the database and improving the performance for read heavy operations.

So in what scenarios we should be using materialized view.

So what are the use cases for using materialized views?

First is data aggregation for systems that need to aggregate or summarize data frequently, like uh,

finding out sales figures or calculating averages.

Materialized views can hold these results pre-computed?

Computed.

You don't need to compute them each time you query the data.

Then, in reporting system, materialized views are perfect for reporting systems where fast data retrieval

is crucial.

If you are generating reports from a large amount of data, you can pre-compute these reports into materialized

views and refresh them periodically.

So when to use materialized views.

If you want to summarize, materialized views are ideal when you have data that doesn't change often,

but it requires frequent querying, especially for aggregation.

They are perfect for scenarios like reporting, dashboards and data warehousing where you need fast

access to summarized or pre-computed data.

Then let's talk about two more things paging and batching.

Well, what is batching?

Batching involves sending multiple operations in a single request or transaction to reduce the overhead

of processing each operation individually.

So instead of inserting or updating records one by one, you bundle them into a batch and process them

in one go.

What could be the use case for batching?

A common use case for batching is bulk insert or updates in databases.

When you need to insert a large number of records or update multiple rows, batching allows you to handle

it in one request and thus significantly reducing the network and database overhead.

Then second thing is pagination.

What is pagination?

Pagination is the technique of breaking large sets of data into smaller, more manageable chunks for

efficient retrieval.

Instead of querying an entire data set at once, you retrieve a subset of data in pages.

So why is this important?

Well, it prevents the overload on the system.

So pagination prevents large queries from overwhelming the database and causing timeouts or memory issues.

It ensures that you are only fetching a subset of data at any given point of time.

It also improves the UI responsiveness for user interfaces.

Pagination is very crucial for ensuring that system remains responsive by fetching smaller chunks of

data incrementally.

The UI doesn't freeze or slow down and thus providing a smooth user experience.

So when to use pagination.

When we are querying large data sets, especially when displaying lists or tables of data in the UI

such as product catalogs or search results, we should use pagination for APIs that actually need to

handle large amounts of data.

Pagination ensures that data is served incrementally without putting undue strain on the system.

So to summarize, batching is ideal for bulk operations such as inserts or updates, and it reduces

the overhead and improves the overall performance.

Pagination is critical for efficiently handling large data sets by breaking them down into smaller chunks,

and thus preventing slow queries and improving the overall UI responsiveness.

By using batching and pagination, we can ensure that our system remains scalable, responsive, and

efficient even when dealing with massive amounts of data.

Now, there are some key interview questions visible on your screen, and these interview questions

cover most of the topics that are relevant for database performance optimization.

So far, whatever we have seen in this lecture, you should be able to answer these questions.

Additionally, I have provided a reference PDF with detailed answers to all these questions which you

can use for review or as a study guide.

Now let's quickly recap and look at the key takeaways from this lecture.

Well, we started by looking at the recap of replication and sharding.

Replication and sharding are both essential for scaling databases across multiple servers.

Replication helps ensure high availability and load balancing, while sharding distributes data across

multiple servers to improve performance and scalability.

Then we looked at Cap theorem.

The Cap theorem reminds us of the tradeoffs between consistency, availability, and partition tolerance

in distributed systems.

Understanding these tradeoffs help you make informed decisions on how to design systems that balance

performance and reliability.

Then we looked at indexes and how indexes are key to improving query performance, but they should be

used wisely because over indexing can slow down the write operations, so it is crucial to manage them

properly based on your system need.

Then we looked at normalization and denormalization.

Normalization is great for transactional systems, and Denormalization is great for reporting systems

or read heavy workloads.

Then we looked at few other techniques techniques like connection pooling, query optimization, materialized

views, batching, and pagination that are all important for improving the efficiency of database operations.

All these techniques help you reduce the overhead and ensure your database handles high traffic smoothly.

So what's next?

In the next section, we will try to summarize whatever we looked in this section of performance, and

we will see how all these things tie together to make a performance system work nicely.

So I will see you in the next one.
