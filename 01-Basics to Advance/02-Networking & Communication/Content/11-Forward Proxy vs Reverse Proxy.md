Welcome back everyone.

Today we are diving into an essential topic in network architecture.

Forward proxy versus reverse proxy proxies play a crucial role in modern system by enhancing security,

improving performance and managing traffic efficiently.

However, not all proxies work the same way some protects clients or other safeguard servers.

So in this lecture, we will break down the key difference between forward proxies and reverse proxies.

We will explore the real world, use cases and understand when to use each of them in the system design.

By the end of this discussion, you will have a solid understanding of how proxies function and how

they fit into scalable, secure, and high performance architectures.

So let's begin by defining what a proxy server is.

A proxy server is an intermediary that sits between the client, which is a browser or an app on your

device and the server.

Instead of the client communicating directly with the server, the proxy relies on the clients to send

the request to the proxy, and then it relays this request to the server, and when the response comes

from the server, it will get the response and send the response back to the client.

Proxies are widely used in these system architectures for several reasons.

First is security, so proxies help in protecting both clients and servers from threats caching.

They store frequently accessed content, which eventually reduces the latency and improve the overall

performance.

Traffic control they distribute requests efficiently, preventing the overloads of the back end systems

and anonymity.

Sometimes these proxies match the IP addresses of the client and help maintaining the user privacy.

So there are primarily two types of proxies and each serves a different purpose.

Forward proxy it is actually used to protect and manage the client requests.

So the forward proxy will always sit in front of the client reverse proxy.

On the other hand, it is used to manage and optimize server responses.

As we move forward, we'll explore these two types in much more detail and discuss their real world

applications also.

So let's start with forward proxy.

A forward proxy acts as an intermediary between clients and the internet.

Instead of a client directly accessing the website or an online service, it first sends a request to

the forward proxy, and the proxy then forwards this request to the destination server.

The proxy will retrieve the response and send it back to the client.

What are the advantages of this setup?

So the first advantage we can think of is the content filtering.

Many organizations use forward proxies to restrict access to certain websites or harmful content, which

are not supposed to be opened from their internal network.

Second benefit could be anonymity.

The proxies hide the client's IP address, which makes it very useful for anonymous browsing through

VPNs or Tor networks.

And the third obvious benefit is caching.

Frequently accessed web pages and resources can be stored in these proxies, which will reduce the load

time, and it will actually save the bandwidth a lot.

So common use cases of proxies are first could be bypassing the geo restrictions.

Users that are restricted from accessing some content in region can access blocked content by routing

traffic through a proxy that is in a different region.

That could be first thing.

Second, anonymous browsing VPN services and Tor networks allow the users to browse the internet without

revealing their actual identity.

Third could be performance optimizations.

Companies use proxies to cache these web pages, which will improve the overall loading speed, and

it will reduce the bandwidth usage.

So if we talk in simple terms, a forward proxy is mainly used by the clients to control and optimize

their access to the internet.

Next let's look at the other side.

The other proxy reverse proxy, which works in a completely different way.

So unlike a forward proxy that sits in front of the clients, reverse proxy sits in front of the back

end servers and handles requests on their behalf.

Clients don't directly communicate to the backend server, but all the requests from the clients actually

go to the reverse proxy first.

The reverse proxy is actually a very powerful tool.

It is used in system architecture for many, many reasons.

The first, most important reason is load balancing.

It distributes incoming requests across multiple backend servers, preventing overload of any single

server and keeping the performance smooth for the application.

Second, caching.

Frequently requested content is stored in this proxy, which reduces the response time and improve the

overall performance of the application.

Third is security.

The reverse proxy acts as a shield, hiding the actual backend server and filtering out malicious traffic.

In some cases, the SSL termination also happens at the reverse proxy level.

The reverse proxy handles encryption and decryption of the Https traffic.

Offloading this heavy task from the back end server.

The backend server need not worry about this SSL termination.

So what are the common use cases of reverse proxies?

We just looked at them I think load balancing, caching, security all these are the common use cases

and motivators for using a reverse proxy in front of our back end servers.

In summary, a reverse proxy is used by servers to optimize performance, security, and scalability.

It plays a critical role in the modern web architecture.

It ensures that applications can handle millions of requests efficiently.

Now let's try to compare the key differences.

The first key difference is, like we discussed position in the network.

A forward proxy sits in front of the clients handling the outgoing requests from users to internet.

A reverse proxy, on the other hand, sits in front of the back end server, managing incoming requests

from user to servers.

What are the use cases?

Forward proxies.

Forward proxies are used by clients, individual users and organizations to provide anonymity and security.

Reverse proxies are used by servers, web applications, APIs, and backend infrastructure.

The purpose we have already talked about purpose.

The client uses forward proxy for privacy, content filtering and bypassing the restrictions.

The servers, on the other hand, use reverse proxies for load balancing, caching, security, and

optimizing the overall performance.

Some examples of the forward proxy can be thought of as VPN and web proxies, and the examples of reverse

proxy are nginx, Cloudflare, and AWS Load Balancers.

In summary, both forward and reverse proxies act as intermediaries.

They serve very different roles in the network architecture, but they are intermediaries.

Forward proxies protect and manage client requests, whereas reverse proxies optimize and secure the

network back end services.

Now that we understand the concepts, the differences and the use cases of the forward and reverse proxies,

it's time to test your understanding with some interview questions.

So whatever we have seen so far, you should be able to confidently answer these questions based on

whatever we have covered so far.

However, if you need to review any concept, there is a detailed PDF attached in the resources section.

Feel free to refer to it for in-depth explanation.

Remember, understanding these topics isn't just useful for interviews.

It is essential for designing scalable, secure, and high performance system architectures.

So before we wrap up, let's quickly review the key advantages and key takeaways from the today's session.

A forward proxy helps clients interact with the internet securely by providing privacy, content filtering,

caching, and access control.

A reverse proxy protects the backend servers by handling load balancing, caching, security, and SSL

termination, optimizing the overall performance of the backend servers, and understanding when and

how to use these proxies is actually crucial for designing scalable, secure, and high performance

architecture.

But we are not stopping here in this.

In the next lecture, we will take this a step further by diving into load balancers.

Load balancers are critical components for distributing traffic efficiently across multiple servers

and improving the system reliability.

So thank you for joining this small lecture.

I look forward to seeing you in the next one.