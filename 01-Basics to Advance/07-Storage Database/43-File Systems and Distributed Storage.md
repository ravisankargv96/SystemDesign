Hello and welcome to this lecture on file systems and distributed storage.

In this lecture, we are shifting our focus from object storage to the underlying file system that powers

many of the world's most critical applications.

From traditional file servers to big data analytics platforms, all use file systems underneath.

We will explore how file systems work at a basic level, then dive into distributed file systems.

The building block of modern scalable storage used in data processing, machine learning, and cloud

infrastructure.

By the end of this lecture, you will not only understand how distributed file system like HDFS work,

but how they can store data across multiple machines.

You should be able to evaluate their strengths, trade offs and ideal use cases.

So let's get started.

So let's begin with the basics.

What is a file system?

A file system is the foundation layer that defines how data is stored, organized and accessed in a

storage medium like a hard drive SSD or removable disk.

It doesn't just store your files, it also manages metadata such as file name, timestamp sizes, and

access permissions.

It keeps track of directory structure.

It handles read write operations and enforces permissions and access control.

Some of the common file systems are ext4, which is widely used in Linux, NTFS, which is for windows,

and ZFS, which is designed for high performance environments.

Understanding file systems is crucial because they impact performance, reliability, and compatibility,

especially when choosing infrastructure for modern applications.

So now that we understand what file system is, let's look at some of the key characteristics of traditional

file systems.

Traditional file systems like ext4 or NTFS.

They use a hierarchical structure meaning data is stored in Folders and subfolders, much like how you

arrange files on your personal computer.

They are generally designed for a single node system, meaning the entire storage and file management

happens on one machine.

This makes them ill suited for large scale distributed application where we have multiple nodes in play.

Another key limitation here is scalability.

Traditional file systems don't easily scale across multiple servers or data centers.

Once you outgrow the storage or performance limits of a single machine, you hit a ceiling.

These file systems are only ideal for personal devices, small scale servers, or workloads that don't

require massive storage, distribution, or parallel access.

But in modern systems, especially in data heavy applications, we need more scalable and fault tolerant

options.

That's where distributed file systems come in.

So what is distributed file systems?

Distributed file systems.

Often abbreviated as DFS, is in simple terms, it's a file system that allows you to store and access

files across multiple nodes or machines.

Instead of relying on just one, from the user perspective, it appears as a single unified file system.

But behind the scenes, data is spread across multiple servers.

One of the biggest advantage of DFS is that it ensures redundancy and fault tolerance.

If one node fails, the system can still retrieve your data from replicas that are on other nodes.

This makes it extremely reliable.

Another key benefit is scalability.

As your storage needs to grow, you can simply add more nodes to the system without restructuring everything.

A great example of DFS is HDFS, which is Hadoop Distributed File System.

It is widely used in big data analytics frameworks like Hadoop and Spark DFS is also used in enterprise

file storage, scientific computing, media content delivery, and backup systems all scenarios where

large scale, reliable storage is crucial.

So in a world that is generating more data than ever now, DFS is a very powerful tool for architecting

and managing storage at scale.

So now let's break down how a distributed file system is actually structured and how it ensures how

data is both available and safe, even in the face of failure.

So at the heart of most DFS implementations, for example DFS, we have two core components the name

node and the data node.

The name node acts like the brain of the system.

It manages all the metadata like file names, directory structure, access permissions, and most importantly,

which block of file are stored on which data node.

Then you have the data node, which is the like workhorse.

They actually store the data blocks.

When a file is uploaded, it's split into the fixed blocks.

It could be of any size 128 MB, let's say for instance, and distributed across different different

data nodes.

Now here's where replication comes in.

To make the system fault tolerant, each block is replicated across multiple nodes.

So if one node goes down, the system can still fetch the block from another node.

This is key to ensure availability.

The number of copies stored is defined by something called as the replication factor.

For example, HDFS.

The default replication factor is three, meaning each block is stored on three different machines.

We also have block size and stripping concept.

Um, so block size determines how big chunk of the file is on each node, and stripping helps in distributing

parts of files across nodes for parallel access and faster throughput.

This entire architecture allows DFS to scale, stay reliable, and serve high volumes of workload efficiently.

So when we are working with massive data sets, think of petabytes or more amount of data.

We need a system that can grow with your needs and recover when things go wrong.

So this is where distributed file system truly shines.

So first let's talk about scalability.

DFS platforms are built to scale horizontally, which means you can simply add more machines or nodes

to the system and increase the storage capacity and throughput.

There is no need to upgrade a single giant server like in case of traditional file systems.

You just plug in more nodes and the system adapts.

Then there is automatic Rebalancing.

As the new nodes are added, the old ones go offline.

The DFS can automatically rebalance data across the cluster to ensure that storage is efficiently distributed

and performance remains consistent.

So even if your nodes are getting overloaded, if you add more nodes to this cluster, the automatic

rebalancing will happen and even the data on the old nodes will be distributed to the new nodes and

the performance will improve.

Then we have fault tolerance.

These systems are designed to handle failures gracefully.

So if a node fails in large scale system, let's say it is bound to happen.

So if a node fails, the DFS automatically shifts responsibility to healthier nodes using replication

and metadata from the name node.

This means that no manual intervention is needed for uh in case of fault.

The system keeps running and serving data even without the user noticing the problem.

And finally, DFS can support high throughput workloads like parallel reads and writes across distributed

nodes.

This is especially important in analytics, machine learning, or backup systems, where performance

at scale really matters.

So in short, DFS gives you both the elasticity to grow and the resilience to stay online, no matter

how large or demanding your workload becomes.

So let's go over some of the potential interview questions.

You can see them on the screen.

These are not just theoretical questions.

Understanding these will help you explain the core system design decisions in interviews, especially

when you are asked about storage in large scale or analytics heavy systems.

You should be able to answer all these questions based on whatever we have covered so far.

But I have also attached a PDF with details Answer so you can actually refer them.

Now let's quickly wrap up this lecture and look at the key takeaways from this lecture.

So what did we see in this lecture.

First we looked at file systems are foundational.

They define how data is structured, stored and accessed on disk.

Whether you are on a personal device or you are managing an enterprise infrastructure.

Understanding file system is crucial.

But when we move to large scale environments, especially when data is distributed across multiple machines,

traditional file system falls short.

That's where distributed file system comes in.

They offer horizontal scalability, fault tolerance, and high throughput access, making them ideal

for modern analytics platforms and big data processing.

Of course, like everything else in system design, there are trade offs to consider trade offs for

performance, complexity, operational overhead and how much fault tolerance your system really needs.

Choosing the right file system or DFS depends on your workload.

Are you working with high frequency data access patterns?

Do you need to tolerate node failures?

How important is latency versus durability?

All these factors will determine whether you should be using DFS or not.

Ultimately, DFS is a critical piece of storage puzzle, especially in systems that handle large volumes

of data across distributed environments.

So this concludes this lecture on file systems and distributed file systems.

What is next?

Next we will dive even deeper into the workloads of big data architecture.

So we will look at a 30,000 foot overview of big data fundamentals and big data data processing to understand

how DFS actually powers the world of Big data.

So I will see you in the next one.
