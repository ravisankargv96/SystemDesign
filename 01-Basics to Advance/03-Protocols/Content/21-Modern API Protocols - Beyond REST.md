Hello and welcome to this session on modern API protocols.

Protocols beyond Rest.

While Rest has been dominant API standard for many years.

Newer approaches like gRPC, GraphQL addresses some of its limitations.

In this lecture, we will explore why we need alternatives to Rest, how gRPC and GraphQL works, their

key advantages, and when to use each one.

So let's dive in.

So why do we need more than rest?

Well, rest has been the standard for building APIs for years, but it comes with certain limitations

that can impact performance and flexibility in modern applications.

One major issue is over fetching.

And under fetching the data, the client often receives either too much of unnecessary data or too little

data, which is not enough for them, and thus requiring extra requests to be sent to the server.

For example, fetching user details might return an entire profile of the user when you only need a

name and email.

Second challenge is higher latency.

Rest APIs often require multiple round trips to fetch related data.

If a client needs a user's detail along with their recent transactions, it may have to make multiple

requests, which will increase the response time for the client.

Third, rest is also not optimized for real time communications.

It relies on polling, where clients repeatedly send requests to check for updates, which is inefficient

and consumes extra resources.

To address these limitations, modern solutions like gRPC and GraphQL have emerged.

gRPC improves performance and efficiency, especially in microservices, while GraphQL provide flexible

data fetching, allowing clients to request exactly what they need.

So now that we understand the limitations of Rest, let's introduce two modern alternatives gRPC and

GraphQL.

Let's start with gRPC.

gRPC is a high performance API framework that uses Protocol Buffers.

In short, Protobufs instead of JSON, making it faster and more efficient.

It is optimized for microservices and it supports the real time streaming over HTTP two, which makes

it ideal for low latency, high performance in our applications.

On the other hand, GraphQL GraphQL is a query language that gives clients precise control over the

data they are fetching.

Instead of receiving a fixed response in Rest, Clients can request only the fields they need, which

reduces overfitting and improve the performance for front end applications.

In simple terms, if you need speed, efficiency and microservices communication, gRPC is a great fit.

But if you want flexibility and optimized data fetching, GraphQL is the way to go.

Now let's dive a little deeper into gRPC.

So we looked at gRPC is designed for high performance communication especially in microservices architecture.

But what makes it so efficient.

First it is built on HTTP two which brings several key advantages.

It allows multiplex requests, meaning multiple requests and responses can happen simultaneously over

a single connection.

Unlike Rest, which is over HTTP one where request open a new connection or weights in sequence.

Another advantage of HTTP two is compression, which reduces the payload size, leading to faster and

more efficient data transfer compared to the JSON based APIs.

One of the most powerful features of gRPC is full duplex streaming, where both clients and servers

can send and receive data continuously in real time.

It is a major improvement over Rest, which follows a strict request response protocol.

Lastly, gRPC uses Protocol Buffers Protobufs instead of JSON for serialization.

Protobuf messages are much smaller and faster and more efficient, which makes gRPC significantly faster

than traditional Rest APIs.

So now that we understand the details how gRPC works, let's discuss when to use it and its ideal use

cases.

First, microservices architecture benefit greatly from gRPC because it enables fast, efficient communication

between services.

Since microservices often exchange large amounts of data across multiple instances, gRPC has low latency

and efficient serialization makes it a perfect fit there.

Another key use case is real time streaming.

With gRPC full duplex bidirectional communication, both the client and server can send and receive

data continuously, which makes it ideal for video streaming, real time analytics, and financial trading

platforms.

gRPC is also widely used in IoT and low bandwidth applications, since it uses protocol buffers instead

of JSON.

It significantly reduces payload size, making communication faster and more efficient even in the constrained

environments.

Lastly, gRPC is a great choice for multi-language ecosystems.

It supports auto generated client and server code for languages like go, Java, Python, and many more,

allowing seamless communication across different tech stacks.

While gRPC is powerful, it may not always be the best choice, especially for public facing APIs where

Rest or GraphQL might be more suitable.

It is usually a best fit for communication within your services.

If you have a microservices architecture, it is better to use gRPC.

It is recommended to use gRPC for communication between these services.

Now let's look a little bit about GraphQL.

So unlike Rest, which typically has multiple endpoints for different resources, GraphQL operates with

a single endpoint where clients can specify exactly what data they need, and this will eliminate the

issue of overfitting and underfitting seen in the rest API.

So at the core of GraphQL is the GraphQL schema, which defines the type of data available and how they

relate to each other.

This schema acts as the contract between client and server, ensuring that the requested data is structured

and validated.

Then clients send queries to GraphQL server.

Asking for specific fields and instead of returning a fixed response, the GraphQL server dynamically

resolves each field and assembles the response based on clients request.

This means that client controls the response shape and thus reducing the unnecessary data transfer.

Now that we understand how GraphQL works, let's explore where it truly shines.

So the first use case is about front end applications.

Front end applications get optimized in the GraphQL usage.

Clients can request exactly what they need.

Avoiding unnecessary data transfer.

This is especially beneficial for modern UI frameworks where different components may need different

sets of data.

Next, reducing API request is another key benefit in Rest.

Fetching related data often requires multiple API calls, but with GraphQL, a single query can request

data from multiple related entities and thus reducing network overhead and ultimately improving the

performance for mobile and web applications.

GraphQL is highly useful in slow or unstable network conditions.

Since client receive only the data they require, payloads are much smaller, leading to faster responses

and a smoother user experience.

Lastly, GraphQL simplifies aggregating data from multiple services.

If your application pulls data from multiple databases or APIs, GraphQL can unify these sources and

provide a single structured response to the client, making it much easier to work with the distributed

systems.

So we looked at the basics of gRPC and GraphQL.

And on this slide we have a few important interview questions related to gRPC and GraphQL.

Whatever we have covered so far will help you answer these effectively.

But there is a PDF attached with this lecture in case you want more details for reference.

Now let's wrap up with some key takeaways of this lecture.

First, gRPC is ideal when you need high performance, low latency communication, especially for microservices

and real time streaming.

It uses binary serialization and HTTP two supports makes it incredibly fast and efficient.

On the other hand, GraphQL is perfect for front end driven APIs where clients need flexible data fetching.

It eliminates over fetching and under fetching, making it a great choice for mobile applications,

dashboards, and applications that are pulling data from multiple sources.

Ultimately, there is no one size fits all solution when it comes to what to use.

The choice between gRPC, GraphQL, and Rest depends on your system requirements, whether it is prioritizing

speed, flexibility, simplicity, or compatibility.

That will dictate the choice of using the standard that you want to use.

In system design, interviews is not just about knowing these protocols.

It's also about justifying your choice based on trade offs.

So be ready to explain why you would choose one over the other.

So that concludes this lecture on gRPC and GraphQL.

Up next we will summarize everything that we have learned in this section of protocols and see how they

apply in the real world scenario.

So I will see you in the next one.

