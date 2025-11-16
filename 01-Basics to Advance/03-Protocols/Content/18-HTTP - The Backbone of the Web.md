Welcome to this next lecture of our System Design Fundamentals series.

In this session, we are diving into one of the most essential protocols in the modern computing HTTP

or Hypertext Transfer Protocol.

HTTP is the foundation of data communication on the web.

Whether you are loading a web page, making an API call, or streaming content, HTTP is working behind

the scenes.

Understanding how HTTP operates, its request response cycle, and its key features like statelessness

methods, status codes is very crucial for designing scalable and efficient systems.

By the end of this lecture, you will have a solid grasp on how HTTP powers the web and how to use it

efficiently in system design.

So let's get started.

So let's start with the basics.

What is HTTP?

HTTP stands for Hypertext Transfer Protocol, and it serves as the foundation of web communication.

It defines the rules of how clients like web browsers or mobile apps, request resources, and how these

servers respond with the necessary data, whether that data is a web page, an API response, or an

image, the response will go back to the client.

HTTP operates over TCP protocol, and it typically uses port 80 for standard HTTP communication.

It is a text based protocol, which means that its messages are human readable, making it easy to debug.

A key characteristic of HTTP is that it is stateless.

Each request is treated independently without remembering previous interactions.

This simplifies server design, but also means some additional mechanism is required to maintain the

statefulness if it is required.

Mechanism.

Like cookies, session tokens are sometimes needed for maintaining state's HTTP supports.

Multiple methods that allow getting different types of interaction and data with from the server, like

get for retrieving data or Post for submitting the information.

These core principles make HTTP the backbone of web communication.

Now let's try to look at how it actually works.

So the first thing that we need to understand is that it follows the client server model where the client,

like a web browser or a mobile application, initiates a request.

And the server, whether it's a web server or an API server or a database server, processes the request

and send back the response.

This simple request response cycle is the foundation of web communication.

So what are the components of an HTTP request?

When a mobile client sends an HTTP request, it consists of several key parts.

First is method.

Method specifies the action that we need to perform like get to fetch the data post to send the data.

Second is URL.

URL identifies the resource that is being requested from the server.

Third is header.

Header contains metadata like user agent, authentication, tokens and content type that the client

is requesting for.

And there is a body also which is optional.

But in case you want to send back some data, like in methods like post or port to send additional information

back to the clients, then the body can also be sent from the server to the client.

So what are the components of an HTTP response?

So when the server is sending the request response back to the client, what are its main components.

So the first is status code.

Status code is a numeric code that indicates whether the request is a successful or a failure.

Like 200 is for success.

404 is for not found and 500 is for some.

Internal server error has occurred.

Then headers also comes back.

In response, these headers provide the details about the response such as content type or some caching

information.

And if the response has a body, the actual content is in the body like an HTML web page, a JSON response,

or an image.

So you can see that this interaction between the client and server happens within milliseconds, and

it powers everything from loading a web page to making the API call in mobile apps.

Next, let's try to break down the request response cycle in more detail.

So let's dive a little deeper into the HTTP request response cycle, which is the core of how web communication

works.

This process happens every time you visit a website, load an image, or interact with a web app.

So step one the browser client sends a request and the web browser actually requests the web server

to get some resource.

This request includes an HTTP method, whether I want to get something or whether I want to post something,

the URL of the resource that is being requested, and a header with additional information like user,

agent and cookies.

It can also send a body in case of put and post if I want to send some data to the web server.

In second step, the web server will process the request.

When the request reaches the web server, it parses the request to understand what the client needs.

It checks the authentication and authorization, if at all it is required.

It queries the database or retrieves the static content.

Then it processes the data and prepares a response to send back.

Then in step three, the server generates the response and sends it back.

After processing, the server creates an HTTP response, which will contain a status code stating whether

it is successful, failure or not found.

It will have response headers which will have the information about content type and cache control,

and a body which could be an HTML web page, a JSON data, or an image.

Finally, in step four, the browser renders the response once the client receives the response.

If it's an HTML web page, the browser will render it.

If it's an API response, the client processes the data and, if required, updated the updates, the

web browser or mobile application if at all required.

The browser can make additional requests like fetching CSS, JavaScript or images.

All this happens in milliseconds, enabling the fast and seamless web experiences that we rely on every

day.

Now that we understand the request response cycle, let's talk about the important characteristic of

HTTP, which is its stateless nature.

So this stateless nature has a very big impact on how web applications manage user sessions and data.

So to understand first try to explain what stateless means.

So when we say HTTP is stateless, it means that each request is treated as an independent transaction.

The server does not retain memory of the previous request.

So if you visit a website, every page request is separate.

The server does not remember whether you have been here before or not.

Each request must contain all the necessary information for processing that request.

That is statelessness.

Now what are the challenges of statelessness?

Well, statelessness makes HTTP simple and scalable.

It also introduces challenges, especially when building interactive web applications.

So in HTTP there is no built in session management.

So the server doesn't know if the same user is making multiple requests.

So what it means that it is very hard to maintain the login states if you login, the server won't remember

whether you have logged in or not, so you need some extra mechanism to be able to do that.

Then each request must carry the full context.

Clients must include authentication details and other necessary details in every request, so that the

server is capable of identifying and knowing that okay, you are a returning user and you have already

logged in before.

So how do we do that?

How do we enable sessions and login states in a stateless application protocol?

Well, there are multiple ways of doing it.

So to work around this HTTP stateless nature developers actually use various techniques to maintain

state across multiple requests.

First technique is using cookies.

Cookies are small pieces of data stored in the user browser, and they are sent with each request and

they help to track the user activity.

They are commonly used for session management and saving user preferences.

Second is server side sessions.

So in server side sessions the server will store the user data.

It will send back a session ID to the client, and the client will keep that session ID in the cookie.

This session ID will be passed to the server with every user request, and using this, the server will

identify which user data should be used with this request.

And then third is tokens.

There are tokens like JSON web tokens or OAuth tokens which can store the authentication information.

So what happens is that tokens are sent with each request to verify user identity.

They are widely used in the modern API and authentication systems.

So to summarize, while HTTP is stateless, we can use mechanisms like cookies, sessions, and tokens

to manage state and create seamless user experience.

So now that we understand how HTTP works, let's dive into some of the HTTP methods.

These are the different ways that clients and servers interact with each other.

So there is this method called get.

So this is most commonly used method.

And it requests data from a server.

It can be used to open a web page.

And it can be used to fetch some data from the API.

The best part about get is gets are saves and idempotent.

Idempotent means repeating the same request again and again won't change anything on the server.

Then we have post.

Post is being used to create a new resource on the server.

It sends some data to the server to create something new.

Posts are not idempotent.

If you send same data again and again to the server, the server will end up creating those many resources.

Then we have put.

Put is being used to update an existing resource.

It will replace some of the properties of already existing object or resource on the server, with whatever

the user is trying to send.

An example could be user wants to update their user profile.

They can do it.

Post are idempotent.

If we send the same request multiple times, it should result in the same state.

So if you're updating the email ID and sending the new value.

If you make a put call multiple times, it will end up in the same result.

Delete removes the resource.

It completely removes the resource from the server.

Deletes are also idempotent.

If you send the same delete request multiple times, it will not cause any additional side effects because

in the first request, the resource will get deleted.

In the second one, it will find that there is nothing to delete, so there are no side effects to it.

Then finally there is patch.

Patch is being used to partially update the resource.

It is similar to put, but it only updates specific fields instead of replacing the complete resource

on the server.

Not necessarily idempotent, the same request could have different effect depending on the previous

values that were there.

So each of these methods play a crucial role in web development and API design.

Choosing the right method ensures clarity, security, and efficiency in communication between clients

and servers.

Now let's look at the HTTP status codes.

So every time you send an HTTP request, the server responds with a status code that tells you whether

your request has been successful or something went wrong.

So on this slide I am listing a lot of status codes.

We are not going to go through each one of them, but understand that there are key categories in status

codes.

So if you look at the 100 category you can see that these are informational messages.

200 series will tell you about the success related HTTP codes.

The 300 series is for redirection.

The 400 series is for client errors.

So if the client is requesting for a bad resource or the client is not authorized, you will get a 400

series error and the 500 series errors are called server errors.

These are the errors that comes back from the server whenever anything goes wrong.

Understanding these status codes is crucial when debugging issues in web applications and APIs.

They help diagnose problems and ensure smooth communication between clients and servers.

So what about Https?

So far we have only talked about HTTP, but what about Https?

Https or Hypertext Transfer Protocol?

Secure is simply the secure version of HTTP.

It uses SSL encryption to protect the data as it travels between clients and server.

So this encryption requires three critical security aspects.

First is confidentiality.

Your data is encrypted, and preventing the data from hackers is essential nowadays.

Second is integrity.

It ensures that the data isn't altered during the transmission.

And third is authentication.

It verifies that the website's identity is actually genuine and thus attacking the phishing attacks.

Websites that handle sensitive data such as online banking, e-commerce and login pages must must use

HTTP to keep users safe.

Another key difference is that Https runs on 443 instead of port 80.

So with the increasing security concerns, most modern browsers flag HTTP websites as not secure right

now, and search engines like Google and other search engines actually prioritize Https for better ranking

also.

So whenever you are designing web applications, APIs, or any system that handles private data, make

sure that you are always, always using Https.

Now that we have covered the fundamentals of HTTP, let's look at some important interview questions

for this topic.

These questions test your understanding of how HTTP work, the request response cycle, HTTP methods,

status code, and even some advanced topics like caching and security.

You should be able to answer most of these questions based on what we have covered so far.

However, if you need a quick reference or a deeper explanation, don't worry.

I have attached a detailed PDF with answers in the resources section.

Make sure to go through it and solidify your understanding.

Now let's quickly recap what we have learned about HTTP and why it is so important in web communication.

First, HTTP is the foundation of web communication.

It defines how data is requested and transferred between the clients and servers.

Second, it follows a request response model.

The client sends the request and the server processes it and returns the response.

Third, it is stateless by design.

Each request is independent of each other.

So if you want to maintain some sort of state between requests, you will have to have mechanisms like

cookies, sessions or tokens to maintain this user state.

Then we looked at HTTP methods and actions methods like get, post, put, delete, patch, etc. every

method serves a specific purpose.

Then we looked at status codes.

Status codes provide feedback to the client, whether the request has been successful, whether there

is a redirection, whether there are client errors, or whether there are server errors.

That concludes our lecture on HTTP.

What's next?

In the next lecture, we will dive into rest and Restfulness.

We'll explore the principles of designing scalable and efficient APIs using Rest.

So I will see you in the next one.