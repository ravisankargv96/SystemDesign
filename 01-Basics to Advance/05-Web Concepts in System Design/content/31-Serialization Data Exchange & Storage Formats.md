Hello and welcome to this lecture on serialization.

The data exchange and storage formats serialization plays a very crucial role in system design, enabling

efficient data exchange between systems, storage and databases, and optimize performance in APIs.

Whether you are designing web applications, distributed systems, or working with large scale data,

understanding serialization is key to building scalable and high performance architecture.

In this lecture, we will break down what serialization is, why it matters, and explore different

serialization formats like JSON, XML, Protocol Buffers and much more.

We'll also discuss their tradeoffs, performance impact, and best practices for using serialization

effectively in real world applications.

So let's get started.

So first let's try to understand why serialization matter.

Well, in modern applications, exchanging and storing structured data efficiently is a fundamental

requirement.

Whether it's a web API, sending a response, or it's a database storing user data, or a caching system

which is optimizing the retrieval speeds of the application.

In all these scenarios, serialization plays a very critical role.

So serialization is the process of converting complex objects into a format that can be easily transferred

or stored without serialization.

Data exchange between different systems and programming languages would be slow and inefficient, and

sometimes even impossible.

So from RESTful APIs using JSON to high performance systems, leveraging protocol buffers and big data

pipelines storing Avro files, serialization is everywhere in system design.

Understanding serialization allows us to build scalable, efficient and high performance applications.

So we have already talked about what serialization.

Let's look at the definition of serialization.

So serialization is the process of converting objects into a format that can be easily transmitted or

stored.

Whether it's sending data over a network, saving it in a database, or caching it for quick retrieval,

serialization makes structured data portable and reusable.

On the other hand, deserialization is the reverse process, taking serialized data and converting it

back into an object that an application can use.

So this process is essential in distributed systems because in distributed systems, data need to be

exchanged between different services, applications, or even programming languages.

In some cases, without serialization and deserialization systems wouldn't be able to communicate efficiently,

leading to performance bottlenecks and compatibility issues.

So serialization format actually plays a very big role.

And let's look at some of this serialization formats.

So serialization formats determine how the data is structured, stored and transmitted between systems.

Each format has its own trade off in terms of readability, efficiency, and compatibility.

Let's explore some of the most commonly used serialization formats and their characteristics.

So the first is JSON format.

JSON or JavaScript Object Notation is one of the most widely used serialization formats.

It is human readable, lightweight, and easy to parse in almost every modern programming language.

JSON allows follow a simple key value structure, making it ideal for web APIs and front end applications.

However, because it is text based, it tends to be larger in size compared to binary formats, which

could lead to higher bandwidth usage when it is being transmitted.

The second format is XML.

XML or Extensible Markup Language is another widely used format, especially in older enterprise systems

and configuration files.

So unlike JSON, XML is tag based, allowing for complex hierarchical structures.

However, its verbosity increases the size of XML even more than the JSON file, making them less efficient

for data transmissions.

But despite this, XML is still used in certain industries, such as banking and enterprise applications,

where strict schema validation and metadata are needed.

Because XML can provide this.

And then we have this third format called protocol Buffers or protobuf.

Proto buffers or protobuf, is a binary serialized format developed by Google.

It is designed for high performance, making it much faster and more efficient than text based formats

like JSON and XML.

So unlike JSON and XML, protobuf requires a predefined schema which helps in reducing the data size

and improving the parsing speed.

This makes it an ideal choice for performance critical applications such as gRPC based APIs and microservices

communication.

So because protobuf is a binary format, it is not human readable, but it significantly reduces bandwidth

and processing time, making it a preferred choice for real time applications where bandwidth should

be used in a limited way and we want faster response time.

So how would you decide to decide?

We need to keep few important things regarding these three formats in mind.

First, JSON is simple, human readable, and widely used in web APIs, but it is text based and larger

in size.

XML allows complex hierarchical structure, but it is verbose and less efficient for data transmission.

Even less than JSON, protobuf is compact, efficient, and optimized for performance, but it requires

schema definitions and it is not human readable.

So how would you choose?

Choosing the right serialization format depends on the use case for web APIs.

JSON is the default choice for legacy enterprise applications.

XML may be used, but we can use JSON also.

And for high performance applications, protobuf offers significant advantages if we can use gRPC for

communication between services.

Now there are some trade offs majorly readability, efficiency versus compatibility, related trade

offs and every serialization format come with trade off.

And choosing the right one depends on the use case.

So let's try to break it down a little bit.

So let's start with readability.

JSON and XML are human readable, making them easy to debug and work with.

However, they're text based.

Nature makes them less efficient in terms of size and speed.

Second is efficiency.

Binary format protobuf is compact and faster to serialize and deserialize, but they are not human friendly

because they are not readable, so they are actually high performant, but they are not human friendly.

And then finally, the compatibility XML supports strong schema validation, Making it reliable for

structured data over time.

JSON has limited schema enforcement, while protobuf provides versioning support, but it requires predefined

schemas.

So ultimately the choice depends on whether we prioritize human readability, performance, or long

term data compatibility.

So serialization plays a crucial role in real world applications, especially in APIs, caching and

data storage.

Let's look at where different serialization formats are used.

We've already talked about it briefly, but let's look at it once more in APIs.

JSON is the default format for Rest APIs because of its simplicity and wide adoption.

On the other hand, gRPC APIs use protobuf to improve efficiency and reduce bandwidth.

XML.

Though less common, it's still used in legacy soap based web services.

And when it comes to caching and data storage, serialization help in optimizing the performance.

So in-memory databases like Redis and Memcached, or serialized data or protobuf data for fast access.

Either they store JSON or in protobuf format.

NoSQL databases like MongoDB uses Bson, which is binary encoded JSON format to improve storage efficiency.

So rather than using protobuf, they use Bson, which is still JSON, but binary encoded protobuf is

often used to store and process large data sets efficiently while allowing schema evolution, because

we can version these schemas.

So understanding serialization in action, whatever we have seen so far help us in designing better

APIs, optimize storage, and improve system performance.

So talking about performance, the choice of serialization formats directly impacts system performance,

affecting bandwidth, CPU usage, and memory efficiency.

All three.

How so?

JSON and XML, being text based, create larger payloads which increase bandwidth usage and slow down

parsing.

This can be a bottleneck for high performance systems.

On the other hand, protobuf is a binary format which generates much smaller payload and is a significantly

faster to parse.

However, they require predefined schemas, adding complexity to development.

So from a performance perspective, choosing the right serialization format depends on balancing the

ease of use with performance needs.

For web APIs, JSON is usually sufficient, while high performance applications benefit from protobuf

s efficiency.

So now let's take a moment to go through some important interview questions.

Serialization is fundamental in system design, affecting APIs, data storage, and performance.

Interviewers often test your understanding of different serialization formats, their tradeoffs, and

their impact on scalability and efficiency.

So throughout this lecture, we have discussed serialization formats like JSON, XML, protobuf and

along with their use cases and trade offs.

With this knowledge, you should be able to confidently explain how serialization impacts system performance

and why choosing the right format matters.

But for your reference, I have also included a PDF with detailed answers to these questions.

So review that PDF to reinforce your understanding and be well prepared for system design interviews.

Now let's summarize and look at the key takeaways of this lecture.

First, serialization is a fundamental concept that enables efficient data exchange and storage across

systems.

Choosing the right format can impact performance, readability, and compatibility.

Second, JSON remains the go to format for APIs due to its simplicity and widespread adoption.

Protobuf offers high efficiency and compact data representation, making it ideal for high performance

applications that are able to use gRPC.

Serialization choices actually affect bandwidth, processing speed, and storage efficiency.

So well informed decision can optimize your system performance and scalability.

That brings us to the end of this lecture on serialization and deserialization.

What is next for us?

Next we will dive into Cors Cross-origin request sharing and web security related things.

It's an essential topic for securing web application and handling Cross-origin requests.

So I will see you in the next one.