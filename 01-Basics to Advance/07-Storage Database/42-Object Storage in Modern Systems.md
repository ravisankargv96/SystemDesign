Hello and welcome to lecture four of this series, Object Storage in Modern Systems.

Today we will be diving into a really important and increasingly popular topic in the modern system

architecture.

And that is object storage.

So if you have ever uploaded a file to a cloud, watch the video on demand or stored backup in the cloud.

Chances are you have already interacted with object storage in some way.

In this lecture, we will break down what object storage is, how it works, and how it's different

from other storage types like file and block storage, and why it has become the go to solution for

handling unstructured data at scale.

We'll also look at popular platforms like Amazon S3, Google Cloud Storage, and Azure Blob Storage.

We will discuss some common use cases of these object storage like media storage, backup, and data

lakes.

So let's get started.

So let's start with the basics.

What exactly is object storage?

Well, object storage is a type of storage architecture that manages data as objects rather than files

in a hierarchy or blocks.

It's a fundamental shift in how we store and access data, especially when dealing with massive amounts

of unstructured data like images, videos, documents, and backups.

Each object in this system has three key parts.

First, the actual data, which could be anything.

It could be a photo, a PDF, or a video file.

Then second, we have the unique identifier or the key that allows you to retrieve this object easily.

And third, and most importantly, metadata, which can store custom attributes about this object like

content type, timestamp, user defined tags, or even access control policies.

So unlike traditional file or block storage, object storage is designed to be highly scalable and distributed.

It doesn't care about the folders or volumes.

Everything is stored in a flat namespace, which makes it easier to scale across servers, regions,

and even continents.

This architecture is what makes services like Amazon S3 so powerful.

You can store billions of objects, access them via simple HTTP APIs, and still maintain durability,

availability, and performance.

So now that we understand what object storage is, let's break down some of the key concepts that make

it work.

First is the object itself.

An object is the fundamental unit of storage in this model.

It is a self-contained package that includes the data itself.

A unique identifier and the associated metadata are also associated with this object.

Think of it like a zip file.

It has everything bundled inside object, the identifier, and the associated metadata.

Next we have the bucket.

Bucket is a logical container used to organize objects, sort of like folders in file storage, but

without hierarchical complexity.

Each bucket can hold millions or even billions of objects.

In services like Amazon S3 or Google Cloud Storage, every object you store must live inside a bucket.

And then we have the metadata.

This is what really sets object storage apart.

Metadata is flexible and powerful.

It can include system design attributes like content type, last modified time size, but also custom

tags that we can define.

For example, we could tag an object with the user who has uploaded it, the project it belongs to,

or whether it's a public or private objects.

Together, these concepts allow object storage to be scalable, searchable, and smart, which makes

it ideal for modern data heavy applications.

Now, object storage has become a core part of the modern infrastructure, and several major platforms

lead the way in offering scalable, reliable object storage services.

So first is Amazon S3.

The industry gold standard of object storage is Amazon S3.

It's been around since 2006 and offer a rich ecosystem, seamless integration with AWS services, and

it is very durable.

Next, we have Google Cloud Storage, or GCS.

It offers a clean, simplified set of storage tiers and is especially friendly for machine learning

workloads.

Then we have Azure Blob Storage, which fits perfectly into the Microsoft ecosystem.

It's ideal if your applications are built with dotnet Azure Functions or Microsoft SQL server plus,

it offers flexible storage tiers and lifecycle management.

Finally, for hybrid or on prem environments, there are great open source alternatives available also.

These provide cloud native object storage so that you can run your own data center, giving you the

flexibility of S3 style APIs without locking on to a cloud provider.

So each of these platforms are very powerful.

The choice on choosing which one will depend on your tech stack, scale, and deployment needs.

Now let's look at some of the real world use cases where object storage really shines.

First is media storage, whether it's a high resolution image video, or a design file.

Object storage is perfect for handling unstructured, large binary files.

Its scalability and cost effectiveness makes it ideal for platforms like YouTube, image galleries or

product asset management systems.

Second backup and archive because object storage is durable and cheap at scale.

It's widely used for storing long term backups.

System snapshot compliance data, especially in cold or infrequent access tiers.

Next data lakes services like Amazon S3 are commonly used to build massive repositories of raw data

and multiple sources.

This means that this has to support big data analytics, AI training and reporting.

And that is where if we store all this data in object storage, it will be very useful.

Another use case is static website hosting.

Amazon S3, for instance, can host static HTML, CSS and JS files with custom domains.

Now this is very useful for landing pages or front end apps without needing a web server.

We can directly store these things as object storages.

And nowadays IoT and ML data pipelines are also using object storage.

Think of object storage as the sink for streaming sensor data or model training data set.

It scales to handle high throughput ingestion and integrates smoothly with downstream processing tools.

So whenever you are dealing with large volumes of unstructured data or you need reliable, scalable

storage, object storage is likely the fit for you.

Now that we have seen what object storage is and where it is used, let's talk about some important

trade offs and considerations when we are working with object storage.

Let's talk about both from the perspective of performance and cost.

So let's start with performance consideration.

So first is latency.

Object storage is not as fast as block or file storage, especially for small frequent reads and writes.

It is optimized more for throughput than for ultra low latency.

But on the flip side, it handles massive parallel access very well, which makes it great for workloads

like analytics or streaming large data sets.

So for small files, it is not an optimal choice.

But for large files and large data sets it is actually a very good choice.

Another thing to keep in mind is about consistency.

For platforms like Amazon S3, you might encounter eventual consistency in certain operations, meaning

changes might not be instantly visible.

And then there is a thing about access patterns.

So object storage is best for write once and read many scenarios.

If you have something that needs frequent updating or appending, object storage might not be an ideal

choice.

Now what about cost?

Let's talk about cost consideration.

So from a pricing point of view, Object storage can be very affordable, but if we are using it smartly.

Platforms like S3 offer storage as standard.

Backups.

Archive.

So we need to pick up the tier that best suits the use case to make it cost effective.

So we are charged not just for the amount of storage that we are using, but also for the API requests

like port or get that we make to the object stored in the object storage.

So it is also very crucial to monitor our access patterns.

So to optimize cost there are some best practices.

So first is always use lifecycle rules to automatically archive or delete stale data.

So this will help to control the cost and still stay organized.

Also we should regularly monitor the usage metrics and adjust our storage classes accordingly.

Sometimes a storage that started as frequently accessed may not be accessed anymore, or not accessed

as frequently.

So it is a potential candidate to move to the archive tier.

So in short, object storage is powerful.

But like any cloud service, the devil is in the details when it comes to performance and cost management.

Now let's look at some of the interview questions for object storage.

These questions are important because they test both your conceptual clarity and your ability to apply

these concepts in the real world architecture scenarios.

We have already covered everything you need to answer this, from the basics to object storage, metadata,

performance, cost, and security considerations.

But I have also attached a detailed PDF in the resources section for you, which includes the answer

and sample explanations.

So if you want, you can refer them to.

Now let's try to quickly wrap up this lecture with key takeaways that we have learned in this lecture.

So first we started with the object storage.

Object storage is scalable.

It is a distributed solution designed for handling unstructured data, especially things like images,

videos, logs and backups.

Instead of working with files or blocks, it treats data itself as self-contained object.

Each of its unique identifier and metadata stored with the object inside a bucket.

So what we have is object, its ID, and its metadata stored inside the bucket.

Then we talked about popular platforms like Amazon S3, Google Cloud Storage, and Azure Blob Storage.

Then we also talked about the on prem alternatives that we can use as options whenever we want to run

the object storage on our on prem environment.

Then we briefly looked at some of the real world use cases from media storage, backups, data lakes,

and static website hosting.

All things object storage is specifically good at.

So what is the key takeaway of this?

Well, choosing the right storage tier based on how frequently your data is accessed is crucial for

both performance and cost optimization.

Second, use object storage when you need to scale massively, store large or unstructured data, or

support.

Write once, read many access patterns.

And finally, keep in mind that metadata and lifecycle management are your best friends when organizing

and optimizing your object storage.

So this brings us to the end of this lecture on object storage.

What's next?

Up next we'll look at the file system and distributed storage, where we explore how traditional and

modern distributed file systems work and how they differ from the object storage.

So I will see you in the next one.
