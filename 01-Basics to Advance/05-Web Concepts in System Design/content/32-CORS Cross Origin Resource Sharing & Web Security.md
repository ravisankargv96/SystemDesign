Hello and welcome to this lecture on cross origin resource sharing and web security.

So in modern web applications, APIs often need to be accessed from different domains.

However, security policies like same origin policy prevent unauthorized cross origin request.

This is where Cors cross origin request sharing comes in.

In this lecture we will explore why courses are needed, how it works and what are the common security

risks and best practices for handling Cors in system design.

So imagine you are building a web application where the front end is hosted on some domain, let's say

app.com, but your back end API is on api.com for example.

So by default the browser blocks these cross origin requests due to the same origin policy.

It's a security measure designed to prevent malicious attacks.

But modern applications rely heavily on APIs across different domains.

This is where a course or cross origin request sharing comes in.

It provides a controlled way to allow securing the cross-origin communication while maintaining security

boundaries.

So in this lecture we will break down how Cors work, why it's necessary, and the best practices for

implementing it.

So let's start with how course work.

So first thing is course is a server driven mechanism meaning the backend must explicitly allow cross

origin request.

When a browser makes a request to a different origin, the server responds with specific course headers

to either grant or deny the access.

There are two types of course request first is a simple request and second is a preflight request.

Simple request include common methods like get post without any custom headers.

However, more complex operations like put, delete, or request with custom headers.

The browser first sends a preflight options request to check if the server allows it.

If the server approves, the request is sent.

So what are the two types?

First are simple request where we are not looking for the options header request, and second pre-flight

request where we will send the options request to check whether the server allows Cors or not.

Key Cors headers controls this process and what are these key Cors header controls?

First is access control allow origin.

It defines which domain can access the resources.

Second is access control allow method.

This specifies allowed HTTP methods like get or post that someone can access from another domain.

And then we have access control allow headers.

The third one.

This lists the permitted custom headers.

What all options and what all origins are allowed.

If you want to list it then we can use this one.

So by properly configuring these headers, we can enable secure Cross-origin communication while maintaining

control over who can access our API.

So not all Cross-origin requests are treated the same way.

Some require a pre-flight check like we talked in the previous slide before they can be processed.

So simple request response is clear.

We know that we are requesting for something and the response will come.

But we need to understand what are these pre-flight request.

So this happens when a request uses a method like put or delete, and it includes a custom header,

or it wants to send some credentials.

In such cases, the browser sends an options request to ask the server if the actual request is allowed

or not.

If the server responds with the correct course header, the browser proceeds with the actual request,

and these headers include that access control allow origin, which specifies which domain, allowed

methods to specify allowed HTTP methods, and allow headers to list the permitted custom headers like

we talked about in the previous slide.

So by properly handling preflight request servers can ensure secure cross-origin communication while

preventing unauthorized access.

So while Cors help enabling cross-origin Communication.

Improper configuration can introduce security risks.

One common mistake is using an overly permissive course policy, for example by setting the access control

allow origin to star.

This will allow any website to access your API.

This can expose sensitive data to even malicious sites.

Also, another major risk is allowing credentials with a wildcard origin.

If access control allow credentials is set to true, while access control allow origin is set to star.

Browsers will block the request, but attackers may still find a way to exploit this misconfiguration.

So you don't have to exactly remember this misconfiguration, but keep in mind that you will have to

refer to the right configuration before setting it.

Another risk is exposing sensitive APIs without proper course restriction can also be dangerous if that

API should never be exposed.

For example, if an internal API meant for authorized users is accidentally open to external origins,

it can be exploited.

So how can we mitigate these risks?

To mitigate these risks?

Always use a whitelist of trusted origins instead of star.

You should always list actual whitelist in the access control allowed.

Origins.

Also set different course policies for different API endpoints based on their security needs, rather

than one course policy dictating all the APIs, every API should see what users what domains can actually

call it and have their own specific course policy.

And wherever possible, use reverse proxies or API gateways to centralize the course handling.

We will look at this in the upcoming slide.

So first let's look at how to handle calls in APIs.

So course we know plays a very crucial role in enabling secure Cross-origin requests for both Rest and

GraphQL APIs.

Since modern web applications often interact with APIs hosted on different domains, properly handling

course is essential.

So in Rest, API calls is commonly used because API returns JSON response to clients.

Most backend frameworks like Express.js Spring Boot Django provides built in ways to configure course

headers.

Developers must explicitly allow Trusted Origins methods and headers in their API responses, rather

than just setting it to star and allowing everything.

Then GraphQL API also requires cross handling since they operate over HTTP only.

However, they often trigger preflight requests due to the complex queries and mutations that include

custom headers or use methods like put and delete.

So properly configuring Cors header and GraphQL servers also ensures smooth cross-origin communication.

Ultimately, both Rest and GraphQL APIs need secure course policies to prevent unauthorized access while

allowing legitimate clients to interact seamlessly with the APIs.

So are there any alternatives to course?

We have just touched upon one fact that we said that API gateways and reverse proxies use it, and centralized

course handling.

So while course is a common solution for handling cross-origin requests, it's not the only approach.

So there are alternative methods that can bypass or centralize other Uh, cause issues more efficiently.

One effective alternative is using a reverse proxy, a reverse proxy such as Nginx or Apache forward

client request to the backend server, making it appear as if the request is coming from the same origin.

Since the request is now handled internally, the browser's course restrictions don't apply.

This is a very popular approach for microservices and API driven architecture.

Another solution for managing courses at the API gateway level, API gateways like AWS API Gateway or

Azure API gateway allows centralized control of course policies.

So instead of configuring course separately for each microservice, the API gateway enforces a uniform

policy, improving the security and consistency across all our microservices.

So how do API gateways and reverse proxies help?

First, they allow cross origin request to be handled internally, avoiding cause issues totally, and

second, they enforce cross policies at a centralized point, ensuring security.

And finally, they optimize performance by reducing unnecessary preflight requests, making API interactions

much more efficient.

So now that we have covered Cors and its role in web security, let's go over some of the key interview

questions on this topic.

I have some questions listed on the screen.

These questions are important because they test your understanding, of course, security risks and

practical implementation, of course, in APIs.

Many system design and back end development interviews include course related questions, especially

when dealing with APIs and security best practices.

Now, whatever width we have covered, you should now be able to answer these questions.

But for your reference, I have also attached a PDF with detailed answers to these questions.

Make sure to review it and solidify your understanding.

Now let's quickly recap and look at the key takeaways from this lecture.

First, the same origin policy is a crucial security measure that restricts cross origin request to

prevent malicious access to sensitive data.

However, modern applications often require cross origin communications, which is where Cors come in.

What is coarse?

Coarse is a server side mechanism that allows controlled access between different origins by setting

appropriate headers.

Servers can specify which domain, which method and which headers are permitted, thus ensuring secure

and seamless cross origin interactions.

However, they can be misconfigured and misconfigured.

Cors cards can introduce security vulnerabilities, overly pessimistic settings, or overly optimistic

settings.

Both are bad.

That is why it is essential to configure course carefully and use alternatives when needed.

So what are the alternatives?

Techniques like reverse proxies and API gateways can help manage cross origin request much more efficiently

by handling them internally.

These approaches not only enhance security, but also improve performance by reducing unnecessary pre-flight

requests.

With that, we wrap up our discussion, of course what's in the next section?

Up next, we will move to the summary and practical applications of all the web concepts we have looked

at, tying them together and see what we have learned so far.

So I will see you in the next one.