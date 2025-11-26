Welcome to this lecture on web sessions and managing State in Web Applications.

In this lecture we will explore how web applications handle user state despite HTTP being stateless.

We will dive into techniques like cookies, sessions, and tokens and discuss security challenges like

session hijacking and CSRF.

By the end of this lecture, you will understand how session management works, its role in scalable

systems, and how to answer related interview questions.

So let's get started.

So have you ever wondered how websites remember your login?

You remember your shopping carts and preferences even after navigating between pages.

This is where web session comes in.

By default, HTTP is stateless, meaning every request is independent and the server doesn't remember

anything between them.

So without a way to maintain state, every interaction would feel like a fresh start, forcing you to

log in repeatedly or lose the cart items.

But to solve this, web applications use a session management technique, something like a cookie or

server side sessions or tokens to track users data.

These techniques enable seamless user experience while ensuring security and scalability.

So first try to understand the stateless nature of HTTP.

We have talked about it earlier also, but just to recap, HTTP is a stateless protocol, meaning it

does not remember past interactions between the client and the server.

Each request is treated as independent with no built in mechanism to track user state.

This means that every request must include all necessary information like authentication details or

session identifiers.

Because the server does not retain any memory of previous request.

Now why is this a challenge?

Well, imagine logging into a website without session management.

The server would forget you after every page load, forcing you to login repeatedly.

Similarly, shopping carts, user preferences, and personalized experiences would not work.

So to solve this, we use session management techniques like cookies, server side sessions, and tokens

to maintain state while working with a stateless nature of HTTP.

So what mechanism we use?

We need mechanisms to track user sessions.

So there are two primary approaches.

One is session based tracking and another is token based.

So first let's talk about session based authentication.

Here what happens is that the server maintains the session data.

While the client holds only a session ID, which is usually stored in a cookie.

So every time the client makes a request, it sends the session ID, allowing the server to retrieve

the corresponding session data.

This approach is commonly used in traditional web applications, but it can be challenging to scale

in a distributed system as session data must be shared across multiple servers.

So if a session data is stored in a database or in a server memory, the challenge is how to make this

memory available to multiple servers.

It is not a very scalable solution.

The second approach is token based authentication, where the session state is embedded inside the token

itself.

So we have tokens like JWT tokens which are JSON web tokens.

So this server in this approach does not need to store any session data, making it much easier to scale.

Instead, what happens is that the token carries all the necessary information and is verified on each

request.

This token based approach is widely used in microservices and API driven architecture, where stateless

authentication is preferred over having a stateful server.

Both these techniques have their pros and cons, and choosing the right one will depend on factors like

scalability, security, and performance requirements of our application.

So let's dive a little deeper into the first approach.

The most common ways to manage user sessions, which is the session based authentication.

This approach relies on server side session storage and cookies on client to keep track of users.

So here is how it works.

When a user logs in, the server, creates a session, and assigns a unique ID.

This ID is then sent to the client and stored in a cookie.

Now, for every subsequent request, the client sends the session ID back to the server.

The server then looks up the session data in its storage to authenticate the user and maintain the user's

state.

This method is simple and widely used in traditional web applications.

However, since the session data is stored on server side, since it is stored in the memory of the

server, it can become difficult to scale in a distributed system.

Because the session data needs to be shared across multiple systems, but there are ways to make it

scalable to make it scalable.

Strategies like sticky sessions.

Session replication or external session stores like Redis cache can be used where the session information,

instead of being saved on each server in its memory, it can be stored in an external cache.

Server could be a redis, so that when we are scaling, every server can access the session data.

Then comes the token based authentication.

Unlike session based authentication, token based authentication does not rely on the server to store

session data.

Instead, all necessary session information is encoded inside the self contained token.

So how it works when a user logs in a server.

Issues a token such as JWT token, which contains user identity and permissions.

This token is then sent to the client and included in every request.

Typically it comes as an authorization header.

Now, since the server does not need to store session data, this method is stateless and highly scalable.

It is widely used in modern authentication systems, including OAuth API tokens and microservices based

architecture.

However, since tokens contain sensitive information.

They must be securely stored on the client side and properly validated to prevent security risks like

token theft or replay attack.

That means this approach, in terms of security, is not as secure as the session based approach.

So since we are talking about security, well, let's talk about the security concerns in session management.

So while session management is essential for web applications, it also introduces several security

risks.

So let's look at the three major concerns and how to mitigate them.

So the first is session hijacking.

This can occur when an attacker steals a valid session ID allowing them to impersonate any user.

Attackers can capture session IDs through cross-site scripting or network sniffing, and they can actually

try to impersonate the user.

How to mitigate it?

Well, always use Https and regenerate session IDs after every login and set a very short expiration

time.

So what will happen is that user will not be able to look at the encrypted data after every login session,

ID will be different.

So even if someone has an old session ID, they will not be able to use it.

And if the expiration time is short, the session ID will expire after some time and will not be valid.

Second major risk is cross site request forgery or CSF.

CSF exploits the user's active session to make unauthorized requests on their behalf.

So if a user is logged in, an attacker can trick them into performing actions like changing their password

or making a purchase.

How can we mitigate it?

Well, we can implement CSRF tokens and we can use Samesite cookies, and we can confirm the actions

of the user using multifactor authentication to make sure that CSRF can be avoided.

Then there is this secure cookie handling cookies.

Storing session data can be vulnerable if not properly secured.

Attackers may steal session cookies through insecure transmission or script injections, but we can

mitigate it.

How?

Well, we can have secure cookies.

We can use HTTP cookies, and we can have flags like samesite flags to prevent the cookie theft and

unauthorized access.

So by understanding and mitigating these security risks, we can build more secure and reliable session

management systems.

So let's look at some of the best practices for scaling the session management.

So as our web applications grow, managing user sessions efficiently becomes a challenge.

So let's look at some of the best practices related to that.

So first is sticky sessions versus distributed sessions.

So the first approach is sticky session where a user's request is always routed to the same server.

This is simple but it can lead to uneven load distribution.

On the contrary, a more scalable approach is distributed session where session is stored centrally

on a separate server, allowing any server to access it like we talked about storing it in a radius

on a separate server.

This ensures better load balancing and fault tolerance.

So sticky sessions versus distributed sessions, then storing session data and Reddis or memcached.

We just talked about it.

To scale the session based authentication, we can store the session data in a distributed in-memory

database like Reddis or memcached.

These provide fast access, persistence, and the ability to share sessions across multiple servers.

Because now the session information is not on a specific server, but they are outside of a server on

a separate server.

Then using stateless authentication with JWT tokens.

So for even greater scalability, we can use JWT tokens instead of server side session storage.

Since JWT is are self contained, the server doesn't need to maintain any session data.

Making this approach ideal for microservices and API driven architectures.

So choosing the right session management strategy depends on your application, scalability, security

and performance needs.

By implementing these practices, we can build highly efficient and resilient authentication systems.

So now we have understand that, uh, understanding web sessions is crucial for system design interviews

and real world applications.

So let's look at some key questions that you should be prepared for.

You can see a list of questions on the screen.

These questions cover fundamental concepts like session management, security risk, and scalability.

Interviewers ask them to test your understanding of state management in web applications, and your

ability to design secure and scalable systems.

With whatever we have covered so far in this lecture, you should now be able to answer these questions.

But if you need a quick refresher, a detailed PDF with the answers is also attached with this lecture.

Now let's quickly recap what we have learned about session management in web applications.

First thing we talked about is HTTP is stateless.

Since HTTP doesn't remember previous interactions, we need session management techniques to track user

state.

Second, what are the common methods for maintaining this state?

Cookies, server side sessions and JWT tokens.

We looked at server side sessions where the session is stored on this server with a session ID, and

this session ID is sent back to the client in cookies.

And we looked at JWT based authentication or token based authentication, which is stateless, where

all the session information is inside the token itself.

And that is comparatively better for scalability.

Then we looked at some of the security risks and their mitigations.

Session management introduces some security risks like session hijacking and CSRF attacks using secure

cookies, Https, CSRF tokens and proper authentication mechanism is very crucial.

Then we looked at how to scale our sessions efficiently.

To handle large scale systems.

We use distributed session storage with some caching technologies like Redis or Memcached.

Or if we want completely stateless authentication, we can use JWT tokens for better scalability and

performance.

So that concludes our discussion on web sessions and managing state in web applications.

What's next?

In our next lecture, we will dive into serialization, the data exchange and storage formats, where

we will explore how the data is structured, transmitted and stored efficiently across the system.

So I will see you in the next one.