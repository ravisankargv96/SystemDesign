Hello everyone, and welcome to this lecture on Content Delivery Networks CDNs for short.

In today's session, we will explore how CDNs enhance performance, reduce latency and ensure seamless

content delivery across the globe, from websites to APIs to video streaming to gaming platforms, CDNs

power the modern internet.

So let's dive in and understand how they work.

So imagine you are trying to load a website hosted on a server halfway across the world.

Without a CDN.

Every request must travel that entire distance, leading to slow load times and poor performance.

But with a content delivery network or CDN, that experience changes dramatically.

So what is a CDN?

A CDN is a globally distributed network of servers that works together to efficiently deliver content

to the user.

CDN strategically placed servers around the world to store and serve content closer to the user, and

thereby reducing the latency and improving the performance.

Why do we need CDNs?

First is very clear to reduce the latency.

The content is delivered from the nearest CDN node and thus reducing the delays.

Second, it also enhances the content availability.

If one server fails, traffic is rerouted to the next available server.

Next nearest available server.

Third, it improves the load handling.

So in case any of the CDN server is overloaded, the CDN will distribute the traffic across multiple

servers, preventing the overload of a single CDN server or of the origin server.

And finally, security CDNs provide protection against DDoS attacks.

It encrypts traffic and it prevents malicious access.

So in modern system design, CDNs are essential for fast, reliable, and secure content delivery.

Whether it's a website, it's a video streaming service, or an API response, CDNs are very critical.

So why are Syrians needed to understand this?

You have to understand the problem that exists without CDN.

First is high latency due to geographic distance.

If a website is hosted on a single server across the globe, let's say you are trying to access from

India and the website is hosted in New York, then the user will experience noticeable delays because

the data has to travel across the globe.

Second is if there is a single server, even if it is geographically close to me, with thousands and

thousands of requests that are coming to it Great.

Sometimes what happens is that the origin server which hosts the content, gets overloaded and it could

cause crashes and slow performances.

And the third reason is bandwidth constraints and slow load times.

Without CDN, every user request must be handled by a same origin server, which will end up consuming

large amounts of bandwidth and increase cost.

So to overcome these issues, we need a better approach one that reduces latency, offloads traffic

from the origin server to other servers, and ensures a smoother user experience.

And this is exactly where CDNs come into play.

So now that we understand why CDNs are essential, let's break down how they work.

A CDN consists of multiple components that work together to deliver the content Efficiently while reducing

latency and the server load.

So there are three main components of CDN network.

First is origin server.

This is the source of truth.

The origin server is where the original content is stored.

It could be hosted in a data center or a cloud provider or on premises also.

However, relying on a single origin for every request creates performance bottlenecks like we have

seen in the previous slide.

Then the second components are edge servers or they are also called points of presence pops.

This is a global distribution network.

CDNs introduce edge servers, which are also known as Point of presence servers.

These servers are strategically placed around the globe to store the cached content closer to the user.

And then the entire system is actually configured by a request routing system.

When a user makes a request, the request routing system determines the best edge server to serve the

content.

This decision is based on factors like geographic locations, network latency, and the load on the

actual server.

So together, these components form the backbone of a CDN, ensuring that the users get fast, reliable,

and optimized content delivery.

So how CDN works and it handles the request from the user.

So every time you visit a website, watch a video, or make an API call, your device makes a request

for content without a CDN.

This request travels to the origin server, causing delays, but with CDN.

How things work.

Let's look at it.

So the first step the user requests the content.

The content could be a web page, a video, or an API data.

In second step, the CDN directs the request to the nearest edge server, so when the user makes a request,

the domain gets resolved to the servers and the CDN directs the request to the nearest edge server.

Instead of sending the request to the distant origin server, the CDN intelligently routes it to the

closest edge server.

This decision is based on factors like the user's geographic location, network latency, and current

server load.

Step three if the requested content is already stored on the edge server.

I mean, if it is already cached on the edge server, it is delivered instantly to the user, so it

reduces the latency and it improves the performance.

But if the content is not available on the edge server, the request is forwarded to the origin server.

The origin retrieves the contents, sends it back, and also caches it on the CDN server for the next

upcoming request.

So what happens is, once the data is fetched from the origin server, the content is stored on the

edge server's cache.

This ensures that the future user's requesting the same content will at least experience the faster

load times.

So in short, CDN acts as a smart middleman.

It ensures that the users get their content faster and with less load on the origin server.

This process significantly improves website speed, and it reduces the bandwidth usage and enhances

the overall user experience.

So let's try to explore the key features that make it so powerful.

CDNs do much more than just caching the content.

They optimized for performance, balanced traffic, reduce costs and enhanced security.

So what are the key benefits of using a CDN?

First, obvious that we have already talked about caching and replication.

This is one of the primary benefits of CDNs.

Storing frequently accessed content on edge server closer to the user.

This reduces the load on the origin server and it minimizes latency.

Second is about load balancing.

To prevent the overloading of any single server, CDNs use load balancing and smart request routing

strategies depending on the user's location and the network conditions.

CDNs direct traffic to the appropriate server.

The strategy could be geo based routing, latency based routing, or load aware routing.

We'll talk about them in a second.

Third, it offers the benefit of compression and optimization.

CDNs also can optimize the content by compressing files and reducing the bandwidth consumption.

There are technologies like gzip shrinking HTML, CSS and JavaScript files.

Image optimization.

Lazy loading.

Minification bundling which CDNs can do, which will actually compress the actual content going to and

fro, and then optimize the actual data transfer that is happening across servers.

And then finally there are security features.

So beyond performance, students also provide the essential security features to protect the websites

from threats like DDoS protection, um, SSL encryption.

And there are also things like bot mitigation that can happen at the CDN.

Send a well architected CDN not only speeds up the content delivery, but also ensures reliability,

reduces the bandwidth cost, and strengthens security.

So now let's try to look at each of these key benefits of CN in a little bit detail.

We will start by the content caching and replication.

CDNs work by storing the copies of frequently accessed content on servers, which ensures fast delivery,

and it reduces the load on the origin server.

But how does a CDN decide what to cache and for how long?

So let's try to break it down.

So first, how close are caching the content?

So when a user requests the content for the first time, the CDN fetches it from the origin server and

stores a copy on the nearest server.

This cached copy is then served instantly to the future users, so there could be a hit for the first

time user, but the future users will get the benefit of accessing the data from the cache server,

and thus eliminating the need to repeatedly contact the origin servers.

Cache content isn't stored forever, but because the content on the original server could change frequently.

So there is a setting called TTL Time to Live that determines how long an object stays in the cache

before it is refreshed.

Websites can define TTL values based on how frequently their content changes.

For example, static content can be cached for days or weeks because it does not change dynamic content

like API responses or personalization.

Data can be cached for shorter period of time.

Then how will this cache data be invalidated?

Sometimes what happens is that content needs to be updated before the TTL expires, so CDNs offer multiple

ways of cache invalidation also.

So these techniques will ensure the freshness of the cached content Without waiting for TTL to expire.

So there are techniques like manual purge, where the website owner manually removes the outdated content

from the cache.

There could be things like stale while revalidate the CDN server and the CDN server will actually serve

the expired cached version, but it will also check with the origin server whether there is a new version

available.

So there could be a hit that will be taken by one user where it serves a stale content, but at the

same time it will refetch the content from the origin server asynchronously so that the future request

will get the fresh content.

And then there is this technique called cache control headers.

So where what we can do is that the developers can define the caching rules in the HTTP headers to get

more control on the cache behavior of CDNs.

So caching is important, and by effectively caching and replicating content, CDNs improve load times,

reduce bandwidth usage, and minimize the overload of origin servers.

Next is load balancing.

So CDNs actually have intelligent traffic management rules baked inside them.

And this is done through load balancing, failover strategies and request routing strategies.

So let's quickly look at how these mechanisms work together.

So first is load balancing a CDN consists of multiple points of presence worldwide.

So instead of overloading a single server, the CDN balances incoming requests across the multiple pops,

ensuring that the smooth performance is there and there are no failures.

In case there is a server failure, what load balancing will do is that CDN will failover to an alternate

server in case it finds that any of that pop is failing, the traffic is seamlessly redirected to the

next closest pop.

Now there are multiple request routing strategies.

So one strategy is geo based routing.

So CDNs use geographic routing to direct users to the closest pop.

This ensures low latency and faster load times.

Then there is latency based routing.

So rather than just using the geography, what it does is that it redirects the user to the pop with

the fastest response time at this point of time.

And it is all based on the real time network conditions.

And then third is the load aware routing.

So to prevent the congestion for a single CDN server.

The load aware routing distributes the request to the least busy pop.

This will ensure that no single server gets overloaded a lot.

So we now know that the CDNs use intelligent load balancing, failover handling, and request routing

to ensure that the users always get the fastest and the most reliable content delivery.

Now briefly talk about compression and minification.

One of the key ways CDNs improve performance is by reducing the size of the files before delivering

them.

Smaller files means faster load times, lower bandwidth usage, and a smoother user experience.

So how can we achieve all these things?

So there are few techniques like using gzip for reducing the text base file size, optimizing images

to faster formats like WebP Web minifying the CSS and JS files before sending it back to the user.

So there are multiple techniques.

And by applying these compression techniques, image optimization techniques minification techniques.

Bundling techniques can significantly reduce the size and speed of the content delivery, thus improving

the user experience and reducing the bandwidth cost.

Then we have the security features.

We talked about it that it's not just the performance optimization.

CDN also plays a critical role in security by protecting websites and applications from cyber attacks.

The key security features of CDNs could be DDoS mitigation.

There could be a possibility that the CDNs implement rate limiting.

It implements traffic filtering.

It implements anomaly detection so that anytime there is a DDoS attack being tried on the origin server,

the CDs will mitigate it.

Also, there is a possibility of SSL offloading.

So every time you enter sensitive data like passwords and payment details, that data gets encrypted

and this encryption ensures that your information is protected.

CDNs can actually enhance the security by handling the SSL encryption.

This will ensure that the data remains private and safe during the transmission.

So there are things like these things like DDoS protection, traffic filtering, and SSL encryption.

CDNs will actually provide a lot of security along with the performance optimizations for your application.

Now what are the use cases of CDNs?

So CDNs are used by almost every major online platform today, from streaming services to e-commerce

sites to APIs and web applications.

It is being used everywhere.

So let's explore some of the most common use cases where CDNs make a huge impact.

First is static content.

Faster loading for common assets like static images, videos, JavaScript, CSS, HTML files.

This these things don't change that frequently on our servers.

And these are our static content CDN store these at the edge and it will ensure that the ultra fast

delivery is happening.

An e-commerce site will cache the product images on CDN because the product images will not change that

frequently.

That could be an example.

On the other hand, dynamic content, the API responses are an example of dynamic content, so optimizing

the API responses and personalized pages.

That is something that CDNs can also do.

So the dynamic content is very user specific and frequently changing.

So what can can do is that even though it can't cache all the dynamic content, it can actually optimize

it at least by doing compression, minification, or bundling.

For example, a banking application can actually use CDNs to route API requests through the fastest

path.

So there could be a possibility that the origin server is very far away, but the CDNs can determine

the fastest route to reach there.

So even though we have the dynamic content being load, the intelligent request routing kicks in and

it ensures that the shortest path and the fastest route is being taken.

Then API acceleration and edge computing is something that we should talk about.

APIs power modern applications, but very frequently API requests lead to the latency issues and server

overload.

CDNs can help by caching the common API responses at the edge and thus reducing the unnecessary round

trip to the origin.

But we need to implement very careful cache invalidation techniques, because the data that it is returning

from the API could get changed at the origin very frequently.

Then edge computing is something like processing the data closer to the user rather than processing

it on the origin server.

So what modern students can do is that they can actually also have this feature of edge computing,

where lightweight processing can actually happen at the CDN end.

Also, rather than going to the origin server.

A good example of this is a video streaming platform, where it can actually use the edge servers to

transcode the videos in real time, and thereby optimizing the playback on your different devices.

So speeding up static content delivery to optimizing APIs and enabling edge computing CDNs are essential

for modern web applications, and we have just looked at some of the use cases of CDNs.

So now that we have covered the key concepts of CDNs, it's time to focus on the type of interview questions

you might face in a system design interviews.

On this slide, I have listed some of the most important questions covering CDN basics, architecture,

caching strategies, load balancing, security, and real world challenges.

The good news is, almost everything that we have covered so far will help you confidently tackle these

questions.

If you have followed along, you already have the solid foundation to explain how CDN work and why they

are essential in modern system design.

However, if you like the detailed answers and explanation to these questions.

Don't worry.

A PDF guide with all the answers is available in the resources section of this lecture.

Feel free to download it and use it for your own interview preparation.

So before we close, let's look at the key takeaways.

So what are the key takeaways?

First, CN improves performance and reduce latency by caching content at a globally distributed edge.

Server networks.

CDNs ensure that users receive content from the nearest location.

Second, bandwidth cost and origin load reduction CDNs minimize unnecessary traffic to the origin server

by caching frequently requested content, leading to lower bandwidth cost and improved scalability.

Third is enhanced security.

CDNs are more than just performance boosters.

They also protect applications from cyber threats.

They do DDoS mitigation.

They do SSL encryption, and they do things like web application firewalls.

And all this helps in securing the content that is being delivered to the user.

Then we looked at some of the use cases for CNNs.

CNNs are used in static content.

They are used to serve dynamic content.

They are used for API acceleration.

Edge computing.

They are used in all these varieties of scenarios.

What's next for us?

Well, we will actually look at most of the networking fundamental topics in this section.

So now what we will do is that we will try to summarize what we have looked at so far.

What are the best practices when it comes to networking fundamentals in terms of a system design interview?

So I will see you in the next one.