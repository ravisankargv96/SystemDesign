Hello everyone and welcome to this lecture on Rest and Restfulness.

In this lecture we will dive deep into Rest architecture, its core constraints and best practices for

designing efficient, scalable, and secure RESTful APIs.

Understanding Rest is crucial for system design interviews as its the foundation of modern web services

and APIs.

By the end of this lecture, you will have a clear grasp on how Rest works, how to structure an API,

and have a look at the real world applications like Twitter and GitHub APIs.

So let's get started.

So let's start by understanding what is rest.

Rest or representational state transfer is an architectural style used for designing networked applications.

Instead of relying on complex protocols, Rest leverages standard web protocols like HTTP to enable

communication between clients and servers.

The main idea behind Rest is that it operates on stateless communication, meaning each request from

a client contains all necessary information, and server does not store any session data between requests.

This makes Rest scalable, reliable, and very easy to implement.

The concept of Rest was introduced by Mr. Roy Fielding in his year 2000 doctoral dissertation.

His work laid the foundation of how modern web services, including APIs and other services used by

big companies like Twitter, GitHub and Google, are built today.

Understanding Rest is fundamental to designing efficient and scalable APIs, which is why it plays a

major role in system design interviews.

Now, let's try to explore the key constraints that defines the RESTful architecture.

So why does this matter, and why is it widely used in modern web applications and system design?

The first reason is it's simplicity and scalability.

Rest is built on standard HTTP methods like get, post, put, and delete, making it easy to understand

and implement.

Because Rest follows a stateless architecture, it scales efficiently, allowing multiple servers to

handle requests without maintaining any session data.

Next, interoperability is a key advantage.

Rest APIs are platform independent, meaning they can be consumed by clients running on different devices,

different operating systems, and implemented in different programming languages, whether it's a web

application, mobile application, or even IoT devices.

Rest can be used everywhere.

And finally, efficiency is a major reason why rest is widely adopted.

By leveraging caching, Rest can introduce lower latencies.

It reduces unnecessary requests, it improves response times, and it reduces the overall server loads.

Since Rest is stateless, it avoids overhead associated with maintaining client sessions, making it

highly efficient for distributed systems.

So because of these benefits, Rest has become the backbone of modern API design, and it powers everything

from social media platforms to cloud services.

Now, to truly understand Rest, we need to explore its core principles, also known as Rest constraints.

These constraints define how RESTful systems should be designed to ensure scalability, reliability,

and simplicity.

The first principle is client server architecture.

Rest separates concerns between the clients and the server.

That means a request and a response.

This separation allows for independent development and scalability, meaning the front end and back

end can evolve separately.

Next is statelessness.

Each request from a client must contain all the necessary information for the server to process it.

The server does not store session data, which ultimately improves scalability and simplifies system

management.

This is why Rest is ideal for distributed systems and cloud based applications.

Then we have Cacheability.

Rest allows responses to be cached to improve the performance and reduce the unnecessary request to

the server.

This is particularly important for high traffic APIs because caching helps speeding up the responses

and reduces the server load.

The fourth principle is the layered system.

Rest APIs can have multiple layers such as security, load balancing, and proxy servers without affecting

how clients interact with the API.

These layers can function independently.

This layered approach enhances the overall flexibility, security, and scalability.

And then finally, we have the uniform interface, which is one of the most defining characteristic

of rest.

It ensures that all the resources are accessed in a consistent manner using standard HTTP methods like

get, post, put, and delete.

This uniformity simplifies the development as APIs follow a very predictable structure.

So by following these constraints, RESTful APIs achieve scalability, flexibility, and efficiency

and thus making them the preferred choice for modern web services.

Now that we understand the Rest core constraints, let's talk about RESTful API design principles.

These are the best practices for designing well structured and efficient RESTful APIs.

The first principle is the resource based approach.

In Rest, everything is treated as a resource such as users, orders, products.

If you have these entities, these objects in your application, these are treated as resource.

These resources are identified using URIs which are the Uniform Resource Identifiers.

So instead of thinking in terms of actions like get user or update order, we focus on resources.

For example, doing a get on user ID, we retrieve a user with that ID, doing a post on slash orders.

A new order will be created.

Next we have the proper HTTP methods.

Usage rest API leverage standard HTTP verbs to perform operations on resources.

So get to retrieve the data.

Post to create a new resource.

Put to update an existing resource.

Patch for partial updates.

Delete for removing a resource from the server.

Using the correct method makes the API much more intuitive, predictable, and aligned with RESTful

principles.

Another key principle is stateless interaction.

Each request must contain all the necessary information, and the server does not store any client session

data between requests.

This simplifies scaling because any request can be handled by any available server.

Authentication and session related things.

If you want to have in your Rest APIs.

It can typically be done using tokens like JWT tokens instead of session based storage.

Lastly, maintaining consistency in URL structures is very crucial for a well-designed API resource.

URL should be clear, hierarchical, and predictable.

So there are some principles like use plural nouns for collections like slash users.

Slash orders.

Avoid including actions in the URL like activate or deactivate.

Implement versioning in your URL systems so that your application and services are backward compatible.

So what happens is by following these principles, we can ensure that RESTful APIs are intuitive, scalable,

and easy to use.

A well-structured API follows clear and logical endpoint patterns to ensure consistency and usability

by structuring resources and endpoints.

This way, we ensure the API is clean, predictable, and easy to use.

Now, when we are designing a RESTful API, choosing the right data format for request and response

payload is also very crucial.

The two most commonly used formats are JSON and XML.

So when to use JSON.

So JSON nowadays has become a standard for the Rest APIs because of several advantages.

First, it is lightweight.

It uses fewer characters and simpler structure.

Second, it is faster.

JSON is natively supported in JavaScript and can be quickly passed by the modern web applications and

mobile applications.

Third, it is readable the JSON key value format is easy for both developers and machines to understand.

But there could be some scenarios where we want to use the XML.

Even though the JSON is more popular, XML is still used in specific use cases.

Use cases like if you have legacy systems, many older enterprise applications and Soap based services

still rely on XML.

Second, there could be some data validation needs.

XML supports schemas xsds which do strict data validations, making it useful for scenarios where formal

data structures are required.

So how to decide?

Most modern Rest APIs use JSON due to its simplicity and efficiency.

XML is still relevant for legacy integrations and scenarios requiring strict schema validations, so

keep this in mind next time you are going to choose it.

There are some APIs that offer both JSON and XML support, which allows the client to specify their

preferred format using an accept header in the actual calls.

That is called the content negotiation of the actual format.

Now that we have covered the principles of RESTful API, let's look at a real world example of Rest

APIs used by the major platforms like Twitter and GitHub.

These APIs follow RESTful principles to provide a structured, scalable, and efficient interaction

with their services.

So if you look at the Twitter API example, we have two examples here one to fetch the tweets using

get tweets, and another one to post a tweet using post tweets.

Then GitHub has some repos to get the repo details and to create the issues in GitHub.

As we move forward, let's go over some best practices that will help you ensure that APIs are well

designed, scalable and secure.

And we will also look at some of the pitfalls.

So the first best practice is that use proper HTTP status codes.

HTTP status code provides clear feedback on the outcome of API requests using the right status code.

Improves error handling and debugging for both developers and clients.

Second is versioning your APIs.

APIs evolve over time, so versioning prevents breaking changes.

A common approach to versioning is in the URLs, but there could be alternative approaches where you

can actually put version information in the header.

Then next implement authentication and authorization.

Secure APIs with authentication mechanisms like Oauth2 or JWT tokens.

And it will be always better.

Also try to always use Https for protecting your sensitive data.

Next, if you have a large set of data, always try to implement pagination.

Large data sets should be paginated to improve the performance.

You can use query string parameters like page and limit to actually specify the paging parameters and

get paginated data.

This reduces server load and improves the API responsiveness.

Now there are some pitfalls to avoid also, and one of the example of such pitfalls is that we should

avoid using verbs in the URL.

So users is a resource.

Every time you want to create a user, you should just do a post on the users resource.

Rather than having a verb in your URL that says something like a create user.

By following these best practices, we can ensure that API's are robust, scalable, and secure.

Now, I have listed down some of the important interview questions of Rest and RESTful APIs.

These questions are commonly asked in system design interviews, especially when evaluating API design

principles.

So far, everything we have covered, from Rest constraints to API design best practices, it should

be able to help you answer these questions confidently.

To help you with your interview preparation, I have also attached a PDF document containing detailed

answers to these questions.

Feel free to refer to it whenever you need a quick review.

Now, before we conclude our discussion on RESTful API, let's summarize the key points we have covered

and what's next in our learning journey.

First, we looked at rest.

A powerful API design style, which is widely adopted, is a style for designing scalable web APIs.

It follows a stateless communication model, making it efficient for distributed systems.

Then we looked at best practices for RESTful design, like proper endpoint structures using HTTP methods,

response formats for JSON and XML, how to do security and versioning.

Understanding RESTful APIs is a fundamental skill for system design and back end engineering.

Mastering these concepts will help you design scalable, efficient, and secure APIs.

So this wraps up this lecture on RESTful RESTful architecture.

What's next for us?

Now that we have explored RESTful API design, we'll move on to some real time communication protocols

that are there and that you need to know for a good system design.

So I will see you in the next one.