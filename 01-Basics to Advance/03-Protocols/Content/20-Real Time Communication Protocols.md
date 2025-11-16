Hello and welcome to this lecture on real time communication protocols.

A very essential topic in system design.

In modern applications, delivering instant updates to users is critical.

Whether it's a live chat application, stock price tracker or real time notification system, the right

communication protocol can make all the difference here.

In this lecture, we will explore the major approaches to real time communication.

We will look at WebSockets and long polling.

We will dive into how they work, their advantages, when to use each one, and some real world examples

where they are applied.

By the end of this lecture, you will have a solid understanding of these protocols and be able to choose

the right one when designing scalable and efficient systems.

So let's get started.

So first let's try to understand What is real time communication?

In today's world, users expect instant updates, whether it's receiving a chat message, tracking a

stock price, or playing an online game.

This is where real time communication comes in.

So what is real time communication?

Real time communication refers to the continuous exchange of data with minimal latency.

So unlike traditional systems where updates happen only when a user's manually requests them, real

time systems push updates automatically and instantly.

Think about your WhatsApp when you send a message.

It appears instantly for the receiver or stock market app, where prices get updated in real time.

So why is real time communication important?

Imagine this WhatsApp chat application where you had to refresh the page to see any new messages.

That would be frustrating, right?

So real time communication is critical for providing a smooth user experience in applications like instant

messaging, live stock market updates, multiplayer gaming, live sports, and score streaming.

Without real time communication, these experiences would feel slow, outdated, and unresponsive.

So why cannot traditional HTTP solve this problem?

Well, there is a problem with the traditional HTTP.

The traditional web follows a request response model where the client requests the data and the server

responds.

While this works well for static content, it has the major limitation for real time application.

What are the limitations?

First is high latency.

The client has to wait for the updates.

Second, inefficiency the server only responds when asked, causing unnecessary delays for the client.

And then we have some scalability issues there.

Also how we can use HTTP to continuously poll for updates.

But it will not be a scalable solution.

It will increase the server load over the time.

So to solve these issues, various techniques have been developed to improve real time communications.

So there are multiple ways to achieve real time updates, and each of it has its trade offs.

Some of the key approaches are.

First is polling.

The client will repeatedly ask for the server for updates at fixed intervals.

Second is WebSockets.

WebSockets is a persistent connection.

A full duplex connection allow instant two way communication between client and servers.

Then we have server side events.

It's a unidirectional stream where the server pushes updates to the client.

Unlike HTTP.

And then we have long polling.

It's a variation of polling Pooling where the server holds the request rather than responding to every

request, the server will hold the request open until there is new data available.

Each of these techniques has its advantages and is suited for different use cases.

In this lecture, we will explore WebSockets and long polling in depth to understand how they enable

efficient real time communications.

So what are WebSockets?

In modern applications?

Real time data exchange is crucial, and one of the most efficient ways of achieving it is through WebSockets.

WebSockets provide a persistent full duplex connection between the client and server over a TCP connection,

and thus enabling real time bidirectional communication.

Unlike traditional HTTP, where a client requests data and waits for the response, WebSocket allows

continuous communication without needing to establish a new connection for every message.

So the first point is that the connection will be persistent.

The connection stays open once it is established.

Second, it is full duplex.

Both the client and server can send and receive message at any time.

And third, it is actually efficient.

It eliminates the overhead of repeating HTTP requests.

Think of it like a direct phone call.

Rather rather than sending the separate letters back and forth.

Once connected, both sides can talk freely until one decides to hang up.

So how WebSockets work?

Well, the websockets actually have a step by step process how they communicate.

So first step is client request to use the WebSocket.

So initially the communication starts with the regular HTTP request, but the client includes a special

upgrade header requesting to switch to a WebSocket.

This tells the server I like to upgrade our communication to a WebSocket connection.

Then in second step, server accepts this request and keeps the connection open.

But the server has to support the WebSocket.

So if the server supports WebSockets, it responds to A101 return code and switching the protocol to

WebSockets.

At this point the connection is established and it will remain open until either the client or the server

decides to close it.

Then in step three, the data is exchanged in real time using the frames.

So once the connection gets open, messages can be sent in either direction at any time.

Unlike traditional HTTP, where each request requires a new connection, and then in step four, when

the communication is no longer needed, either the client or the server can close the connection using

a special WebSocket close frame.

So, to summarize, WebSockets offer a powerful way to enable real time communications by maintaining

a persistent bidirectional connection.

They are widely used in applications like chat systems, live notifications, stock market updates,

and gaming.

So now that we understand how WebSockets work, let's talk about why they are so powerful and where

they are commonly used.

So advantages of WebSockets.

The first one we have already discussed.

Persistent connection.

Unlike traditional HTTP request, WebSockets maintain a single open connection, eliminating the need

to repeatedly establish new connections.

This significantly reduces the latency and make the interactions feel much more instant.

Second, it reduces the overhead compared to HTTP polling.

With polling, the client must constantly send requests even if there is no new data.

WebSockets eliminate this unnecessary traffic and thus reducing the bandwidth usage and server load.

It is very efficient for real time applications.

Since WebSockets enable bidirectional event driven communication, they are perfect for applications

that require instant updates without delays.

Some of the use cases like we have already discussed, are live chat applications like WhatsApp, slack,

discord.

Stock market price updates like Nasdaq provides it, multiplayer online games like Fortnite, Call of

Duty uses IT, and collaborative tools like Google Docs and Google Slides where we can work on a single

document together.

So to summarize, WebSockets provide a low latency, high efficiency solution for real time communication.

Whether it's a chat application, stock price update application, gaming application, WebSockets ensure

that the data flows instantly and efficiently.

Now let's briefly talk about long polling.

Long polling is a technique that allows us to achieve real time communication, even when WebSockets

are not available.

Long polling is a technique where the client sends an HTTP request to the server, but instead of server

responding immediately, the server will hold the request open until the new data is available.

So what it does is it simulates real time updates using HTTP only, and it is much more efficient than

regular polling because in regular polling the constant request will be sent to the server, whereas

in this the single request will be held by the server.

This is very useful when WebSockets are not supported or not needed.

Now how long polling is different from regular polling?

Let's try to understand it a little bit in depth.

In regular polling, the client keeps sending requests at fixed intervals whether or not new data is

available.

This wastes resources and creates unnecessary server load.

With long polling, the client sends a request, but the server waits until there is a new data available

before responding.

This reduces unnecessary requests and provides faster updates whenever there is any change on the server

side.

So how long polling works?

There are again a few steps in this.

First, the client makes an HTTP request to the server asking for new data.

Second, instead of responding immediately, the server will keep the request open until new data is

available.

Then once the server has the new data, it will send the response to the client.

Finally, the client will get the response and it will immediately send another request to wait for

the next update.

It will close the first one and it will send the another one.

This cycle will repeat keeping the data fresh while reducing unnecessary traffic.

So to summarize, long polling provides a more efficient way to achieve real time updates over HTTP.

Not as good as WebSockets, but still better than traditional HTTP.

It's not as fast as WebSockets, but it is useful in environments where WebSockets aren't supported

or even simpler solution is needed.

So when to use WebSockets and when to use long polling.

The first question is WebSockets.

So if.

High frequency See bidirectional data exchange is needed if our application requires continuous instant

communication between clients and server, WebSockets are the best choice.

This is especially true when both the parties need to send messages at any time, whenever low latency

is critical.

In use cases like real time chat, stock trading, multiplayer gaming where every millisecond counts,

WebSockets provide a persistent low latency connection, ensuring data is transmitted without delays.

Then, when to use long polling.

The first scenario could be very simple.

If WebSockets are not supported or if they are an overkill, then we switch to long polling.

Long polling provides a very good alternative to WebSockets and using standard HTTP protocols.

Second scenario could be when periodic updates are sufficient if our updates do not need to be sent

every second, but still need to appear quickly.

Long polling works well.

It allows the server to push updates when they are available, rather than client constantly checking

for it.

So if we talk about some of the real world examples, slack uses WebSockets.

Twitter uses long polling.

Stock exchange application uses WebSockets, but IoT devices actually use long polling.

Choosing the right approach depends on your use case.

WebSockets are ideal for instant high frequency communication, while long polling works well for periodic

updates when WebSockets are not an option.

So now that we have covered the key concepts of real time communication protocols, let's go over some

common interview questions related to this topic.

Understanding these questions is crucial because system design interviews often test not just your theoretical

knowledge, but also your ability to apply concepts in real world scenarios.

These questions will test your grasp of architectural trade offs, scalability, and efficiency, which

are all essential for designing high performance distributed systems.

So all the questions that you see on my screen, you should be able to answer them using the concepts

we have covered so far to help you prepare.

We have also attached a reference PDF with detailed answers to these questions.

Feel free to review it if you need a refresher.

Now, before we conclude this lecture, let's try to quickly summarize what we have learned and how

we can apply it.

So there are a few key takeaways of this lecture.

First, WebSockets are persistent full duplex connection.

They provide a continuous bidirectional connection between client and server.

They are ideal for low latency, high frequency updates, making them perfect for chat applications,

gaming application and stock price updates.

Long polling, on the other hand, allows clients to receive updates without repeatedly polling the

server.

It works well in scenarios when WebSockets are not available or when real time communication is needed,

but at a lower frequency, not continuous interaction is required.

A lower frequency interaction could work.

It will be used in systems like notification system and social media updates.

We have to choose the WebSocket versus long polling based on our latency, needs and infrastructure.

If our system demands real time, high speed data exchange, WebSockets are the way to go.

If we are working on a Rest based API or have a infrastructure constant where less frequent updates

can be used, long polling is a better option and effective alternative understanding.

Real time communication is crucial in system design.

Whether you are building a chat application, a stock trading platform or an IoT system, choosing the

right approach WebSockets versus long polling will ensure your application delivers data efficiently

and effectively.

So what's next for us?

In the next lecture, we will dive into more advanced API communication methods, exploring technologies

that are beyond rest and connected sockets.

We'll try to look at gRPC, which is which is a high performance binary based protocol for microservices.

And we will also look at GraphQL, which is a flexible query language for APIs, allowing clients to

request exactly what they need.

So that is all for today's lecture.

Thanks for joining in and I will see you in the next one.