Welcome back everyone.

Today we are going to explore a fundamental concept that powers modern computing the client server model.

Whether you are browsing the web, using an app, or streaming a video, you are interacting with this

model every day.

Understanding how client and servers communicate is crucial for designing scalable and efficient systems.

In this model, usually we have a client such as your laptop, phone, or even a smart device like a

refrigerator.

It sends a request to the server which processes the request and sends back the response.

This interaction happens millions of times per second across the internet.

This enables everything from simple web pages to complex cloud based applications.

In this lecture, we will break down the communication process, explore how the request response cycle

work, and discuss real world applications of client server model.

By the end, you will have a clear understanding of how this architecture plays a vital role in system

design.

Now that we have an overview, let's dive deeper and define the client server model.

This is one of the most fundamental architectures in computing, and it serves as the backbone of modern

applications.

It doesn't matter whether the applications are web based, mobile based, or these are cloud services.

If you look at the first point, the client server model is a computing framework where clients request

services and servers provide them.

The client initiates communication while the server processes the request and responds accordingly.

This separation of concerns allows for efficient resource management and scalability in our modern computing

environments.

Next, why is this model so important?

First, it allows for efficient resource management, meaning computational power storage and processing

are distributed optimally at the server level.

Instead of each device.

Handling.

Complex processing tasks are delegated to powerful servers.

And second, it enables seamless communication across various applications.

Whether you are accessing a website, you are sending an email, or you are interacting with an API,

the functionality that you will get will be same.

To understand better, let's look at some real world examples.

Imagine you are browsing a website.

Your web server acts as the client.

It sends a request to the web server and the server hosts that site.

The server processes this request, retrieves the web page, and sends it back to the browser for display.

Another example we can think about is email communication.

When you send an email from your phone or from your computer Your email application functions as the

client.

It communicates with the email server to send, store and retrieve messages.

This client server interaction ensures smooth and reliable email exchange across different devices and

networks.

As you can see, this model is everywhere from websites to cloud computing to gaming to IoT devices.

It is very crucial to understand this.

And now that we understand what it really is and why it is important, let's move on to how the client

server communication actually works.

So let's break down this model into three main components.

The first is client, the second is server and the third is the network.

These elements work together to enable seamless communication in almost every digital service that we

are using today.

So the first thing is the Client.

This is the user facing application that initiates the request.

The client would be a web browser loading a web page or a mobile application, or an API consumer.

It wants to interact with the back end system.

Clients are designed to request information, process the response that it is getting from the server,

and display the results to the user.

The second component is the server.

Servers are responsible for processing requests and returning the responses.

Depending on the application, a server could be a web server that delivers web pages, a database server

that retrieves and store the information, or a mail server that manages the email communication between

senders and receivers.

Essentially, the server does the heavy lifting of all the functionality, ensuring that the clients

receive the correct data efficiently.

And the third and the final section is network the invisible bridge connecting clients and servers are

networks.

Networks can take many forms, including the internet, which powers the global communication across

the world.

Local area networks, which are used inside homes and businesses connected through either wire or Wi-Fi

connections.

And even 5G networks, which enables high speed mobile data communication across mobile devices.

Without a network, clients and servers would not be able to communicate at all.

In summary, the client sends request, the server processes them and responds to those requests, and

the network facilitates the connection between them.

These three components forms the foundation of client server model, ensuring smooth and scalable interaction

in our modern applications.

Now that we understand the key components, let's explore how they actually Communicate with each other.

So how clients and servers communicate at a high level, the client server communications follow a simple

five step process.

The client sends a request.

This could be an HTTP request for a web page, or a SQL query to a database, or an API call from a

mobile app.

Then this request is transmitted over the network.

It travels through the internet, a local area network, or any other communication channel that lies

between a client and a server.

The server receives and processes the request, and this could also involve retrieving data from databases,

performing computations, calculations, and then finally generating a response.

Once the response is ready at the server, the server sends back the response.

The response could be a web page, a JSON document, or raw database result.

Also, the response comes back to the client.

The client receives and processes the the response.

It can then present the data.

The response that it has received to the user.

If it's a web page it will display the web page.

If it is dot data, it will update the UI based on the data that is received.

But not all client server communications follow the same pattern.

So if we talk about the types of communication in client server model, there are mainly two types of

communication in the client server applications.

The first type is the request response model.

This is the most common.

And the client sends a request and waits for the response before proceeding to do anything else.

The main examples are the HTTP request in web applications, and the rest API calls that we make in

microservices.

This model is actually ideal for transactional interactions, where each request is independent of one

another.

The second type is persistent connections.

Unlike the request response model, persistent connection keep the client and server continuously connected

for real time communication.

The examples include WebSockets, which enable live chat applications like WhatsApp FTP sessions which

enable file transfer across servers.

All this happens because in this model, we maintain an open connection for continuous or large transfers

of data over the network.

So whether it's a simple request response, interaction or a continuous real time connection, client

server communication forms the backbone of modern application.

Now let's take a deeper dive into one of the most common examples the HTTP request response cycle.

The HTTP request response cycle.

This process happens every time you visit a web page, and if you understand it, it is very crucial

for designing the large scale systems.

So how does it happen?

It all starts when the browser requests a web page.

Let's say you type example.com in your browser address bar and hit enter.

But before the browser can reach the website, we first need to know where this website is located.

That's where DNS comes in picture.

So your browser first needs to find the IP address of example.com.

The DNS resolution will kick in the domain name server.

Translation happens at multiple levels.

If the IP is cached for this domain, it is retrieved from the cache.

If not, it will go to the domain name server and get the IP.

Once the browser has the correct IP address, it sends an HTTP get request to the web server.

This request is asking the server to provide the actual content of this web page.

Now everything will happen on the server side.

The client side part is done.

The web server receives the request and it will process it.

If the page contains dynamic data, the server might need to query a database to fetch the data.

It might need to do some computations and calculations on top of that data.

But when all the necessary information is gathered, the server will create a response.

The server will then send back the HTTP response.

This response includes the status code like 200.

If the response is successful, or an error like 404 if the page that user is requesting is not found,

and it sends back the actual content of the web page, which could be HTML, CSS, JavaScript, or even

raw JSON if it's an API response.

Finally, the browser receives the response and processes it.

It renders the HTML, loads the styles and javascripts, and display the fully formed web page on the

screen.

This entire request response cycle happens just in milliseconds, and it enables the smooth web experience

that we are so reliant on nowadays.

Now that we understand how the HTTP communication works, let's try to explore a different communication

model which is synchronous and asynchronous communication model.

So far we have discussed how clients and servers communicate, but not all interactions happen in the

same way.

Some applications require immediate response, while others need to handle multiple tasks simultaneously,

and they might respond after some time.

Which brings us to the key difference between synchronous and asynchronous communication.

So what is a synchronous communication?

In this model, the client waits for a response before continuing.

So it's a blocking call.

The client makes a request and it waits for the response from the server before doing anything else.

It follows a strict request response pattern, meaning nothing else can happen until the server replies.

A common example of this is submitting a form on a website.

You fill out your details and you click submit.

Then you wait for the confirmation message before doing anything else.

This is a typical working in the Rest APIs and traditional web applications, where each request must

be fully processed before moving to the next one.

But is that always ideal?

Especially in case of real time applications like WhatsApp, chat and all?

I don't think so.

That's where asynchronous communication comes in.

With asynchronous communication, the client does not wait for a response.

Instead, it can continue other tasks while the server processes the request in the background.

Once the response is ready, the server will notify the client and then the client can get the response

from the server.

Same example.

We talked about real time chat applications like WhatsApp.

When you send a message in a chat application, the app doesn't freeze while waiting for a reply.

Instead, it keeps running and when the recipient responds, the new message appears instantly.

This is powered by technologies like WebSocket, which enables continuous two way communication and

which allows all the web pages to also fetch the data without reloading.

So two ways of communication synchronous communication and asynchronous communication.

If you have to summarize, synchronous communication is lacking, like making a phone call.

You speak, wait for the response, and then continue.

Asynchronous communication, on the other hand, is like sending a text message.

You send it and continue doing other things until you get a reply from the other side.

That's the crux of synchronous and asynchronous communication.

Now that we understand the synchronous and asynchronous communication, let's also explore another important

concept which is stateful versus stateless servers.

So to understand the client server interactions in more detail, there is another key distinction to

understand.

And that is stateless versus stateful servers.

This difference determines how a server handles user interactions over time, and it also significantly

impacts performance, scalability and user experience.

And that is why this is very important in terms of system design.

So let's look at the stateless server.

These servers do not retain any memory of past interactions.

So if me as a user making a server multiple server calls, the stateless server will not retain any

memory of the past interaction.

Every request is treated as independent, meaning the servant does not store any session details of

previous request.

Each request must contain all the necessary information for the server to process it.

A very common example of this is rest API.

When you make a request to rest API, the server processes it and responds back, but it doesn't remember

any previous interaction.

Another example is basic HTTP web servers where you don't have to login.

Each request for a web page is handled separately without maintaining any user session data.

Stateless servers are ideal for Scalability because they can handle a large number of independent requests

efficiently.

They also enable better caching, as the responses don't have to rely on the stored session data.

Additionally, they work very well with load balancer, where load balancer can distribute incoming

requests across multiple servers, and it will ultimately improve the performance because none of the

servers actually stores any of the user data.

However, many, many applications want to retain the user context, so that's where the stateful server

comes in.

Unlike stateless server, stateful server maintains session information across multiple requests.

This means the server remembers previous interactions and keep track of the user's state throughout

their session.

Example.

Some common example of stateful systems include WebSockets multiplayer online games where the server

tracks player position as the game is progressing.

Banking application where the user has to login and the server has to maintain a session for processing

the secure transactions.

The main benefit of stateful server is personalization.

They enable seamless user specific experiences by remembering session details.

This is essential for real time applications like chat applications, gaming applications, banking

applications, or any application where maintaining the user's state and session is very critical.

So to summarize, stateless servers are great for scalability and efficiency.

They make them ideal choice for web APIs and distributed systems.

Stateful servers, on the other hand, enhances user experience and personalization by maintaining session

information.

The choice between these two will depend on the requirement of the application.

Now that we have covered the fundamentals of client server model, let's look at some real world examples

where the architecture of client server is used daily.

I think almost every digital interaction that we see nowadays relies on some form of client server interactions.

The examples could be web applications.

The web application, traditionally and even nowadays relies on the client server model for communication.

Then web APIs, web APIs and microservices, mobile applications.

They also often communicate with backend services to get the data.

Another example is databases.

In case of database servers, the web server acts as the client and the database server acts as the

server.

And whenever the application needs to retrieve or store the data, it will make a call to the database

server and retrieve the Information and there are messaging systems like WhatsApp, slack.

These use WebSockets to maintain a persistent connection between client and the server, and this allows

messages to be sent and received instantly and asynchronously.

So you can see that the client server model is everywhere, from a simple web browsing to API driven

apps to databases to real time messaging systems.

And understanding these practical applications will actually help us in designing better systems in

an efficient way.

Now that we have covered the core concepts of the client server model, let's shift our focus to interview

preparation.

Many system design and back end engineering interviews include questions on this topic, and everything

we have discussed so far will help you confidently answer these questions so you can see a list of questions

I have listed on the slide.

I have also compiled the answer for these questions, so make sure to review these concepts as the solid

understanding of these concepts on client server model is essential for designing scalable and efficient

system.

The PDF is attached in the resources section of this lecture.

Feel free to refer it if you want to have quick reference for the answer of these questions.

Now, before we close, let's take a moment to recap what we have learned today about the client server

model.

First, we saw that the client server model is the foundation of most modern computing.

Whether you are browsing a website, using a mobile app, or interacting with a database.

This model enables seamless communication between clients and servers.

We have also explored different communication patterns such as synchronous and asynchronous communication,

and we also looked at stateless and stateful servers.

The design choices play a very crucial role in optimizing performance, scalability and user experience.

When it comes to designing your server infrastructure and most importantly, understanding this model

is essential for system design and scalability planning.

Whether you are building a small application or a large distributed system, these principles will guide

your architectural decisions.

So what's next?

In our upcoming lecture, we will dive deeper into an important system design topic called Forward Proxy

and Reverse Proxy.

These components play a key role in security, load balancing and performance optimization.

And understanding those will actually help you further enhance your system design skills.

So thank you for joining this lecture.

Keep exploring, keep learning, and I will see you in the next one.