Hello and welcome to this lecture on caching for Speed optimization.

In this lecture, we are going to explore one of the most effective ways to supercharge performance

in modern systems caching.

From reducing latency and offloading databases to improving scalability, caching plays a very crucial

role in fast, responsive applications.

We will cover what caching is, why it matters the different types of caches and the smart strategies

of caching.

We will also look at the real world caching powerhouse Redis and how the companies use it to build the

blazing fast systems.

So let's get started.

So when it comes to building fast, scalable systems, caching is your best friend.

Why?

First, caching reduces latency.

Instead of hitting a slower database or recomputing results, the system can fetch data instantly from

a fast in-memory store like Redis.

This is crucial for real time user experiences.

Think search suggestions, feed rendering and product recommendations.

If they are from cache, they will get served faster.

Second, it lightens the load on your backend services and databases.

Fewer calls to these services means reduced strain on your infrastructure, helping it serve more users

with fewer resources.

Third, it dramatically improves the scalability when more users come.

A good caching strategy can absorb the impact and prevent downstream systems from being overwhelmed.

And finally, in low latency, high throughput architectures, caching isn't optional.

It is foundational.

Whether it's the CDN caching, static assets, or API responses being cached at the edge, server caching

is the secret behind the speed of all modern applications.

So when we talk about caching, it is important to recognize that it exists across multiple layers in

the system, each of which has its own purpose and benefits.

So first we have client side caching.

This lives in the user's browser.

Tools like local storage, indexeddb or service workers can cache data right on the device, reducing

the need for round trips to the server.

This is great for things like offline support or speeding up navigation in single page applications.

Next, we move to server side caching.

So typically in the form of in-memory data like Reddis or memcached, we keep some data cached.

These caches sit close to the application server and store frequently accessed data such as user session,

authentication, token, or Precomputed result.

Then there is CDN caching for static assets like images, scripts, or even API responses.

Content delivery networks or CDN.

Fastly cache data geographically distributed closer to the user.

This massively improves the load times and reduce the origin traffic.

And finally, there is database level caching.

This could mean result set caching.

What I mean by result set caching is that storing the output of frequently used queries in cache.

So it is a very powerful way to reduce the database computation time for expensive joins or analytics

queries.

So we looked at these four types of caching together.

These caching layers form a performance shield around your system.

Each layer catching requests before they hit deeper and much slower component and return the result

from cache itself.

So let's look at some of the caching strategies.

So for this example let's assume that we are caching some data from the database.

And our application is trying to write that data into that database.

So there is a cache in between your application server and your database servers.

With this we will try to understand some of the caching strategies and how data flows between the cache

and the database.

So first up is write through caching.

So in this approach the data is written to the cache and the database.

At the same time it ensures consistency that the cache is always fresh, but it adds a bit of latency

to write operations since both operations must be complete in order to say that your right operation

is complete.

Next is write back or write behind caching.

Here, data is written only to the cache initially and the response goes back to the user asynchronously.

This cached data gets synced to the database later.

This boost up write performance, but introduce the risk of data loss if the cache goes down before

the database is updated.

Then we have lazy loading or cache aside.

This strategy first checks in the cache.

So this is typically in the time of reads.

So when we are reading it will first check the cache.

If the data isn't there it fetches it from the DB, returns it and stores it in the cache.

This keeps the cache hot with only what is actually used.

But there might be a cache miss delay on the first access because the item was not in the cache.

So we looked at two types of write caching and one type of read caching.

But there is also another type which is called explicit or manual caching.

So this is where developers take full control, deciding when to cache something, when to invalidate,

and how to handle cache inconsistency.

This offers flexibility but can be complex to maintain, especially when the system scales.

So in this strategy, we are not relying on the system usage behavior, but the developers are anticipating

that this data is probably going to be used a lot.

So they decide to cache it explicitly.

So each of these strategies has tradeoffs in terms of latency, consistency and complexity.

And choosing the right one depends on your system's read write patterns and your system's tolerance

for stale data.

Now let's talk about the cache eviction policies.

So what should happen when your cache fills up?

You need a way to decide what gets kicked out.

And that's where the eviction policies comes in.

So first is LRU least recently used.

Think of it like a refrigerator.

The item you haven't touched in weeks get thrown out first.

It assumed that recently access data is more likely to be used again soon.

A good choice for most general use cases.

Then we have least frequently used.

This policy removes the item with the fewest access hits.

It is usually useful when some data is rarely accessed, and even if it was accessed recently, we know

that it is rarely accessed, so this becomes a candidate for eviction.

And think of old blog posts versus trending articles.

Old blog posts will be potential candidates for removal.

Then there is Fifo.

First in, first out.

This is the simplest strategy.

Just remove the oldest cached item regardless of how often or how recently it is used.

It is very easy to implement, it is less intelligent and it can evict valuable data if you are not

useful.

So it could be a possibility that something got added into the cache first, but it is very frequently

being used.

But since it was added first, you remove it so you will have to cache it again.

Along with these eviction policies, there is another important concept called TTL or Time to Live.

Time to live defines how a cached item stays valid for how long it stays valid, regardless of access

patterns or anything else?

For example, you might set a total of ten minutes on your user profile data.

So after ten minutes, the item expires and is evicted from the cache automatically.

This is especially useful for time sensitive data such as API responses or session tokens.

Time to live helps keep your caches fresh without complex logic, and works well in combination with

either least recently used or least frequently used.

So choosing the right eviction policy depends on your access pattern.

Least recently used is widely used as default, but least frequently used can outperform it in systems

where highly uneven data is there.

Now let's talk about Redis.

One of the go to tool for performance caching Discussion.

These days, Redis is an in-memory key value store which keeps everything in Ram.

So since everything is in Ram, it makes it blazingly fast for both reads and write.

But Redis is more than just a simple cache.

It supports feature like TTL for automatic expiry of keys, pub sub messaging for real time eventing

system, and even data persistence if you want to save the data to the disk.

Because of this flexibility, you can actually use it as a database also.

So Reddis is used in a variety of roles, from caching web responses to queuing background jobs to storing

session data.

And in some cases it is actually being used as a database.

Also, because the Redis cache content can be persisted on disk two.

It is open source, highly reliable and widely supported across cloud providers and frameworks.

This is the reason it became the cornerstone in many high performance architectures.

Now let's bring caching to life with some real world examples that you probably use every day.

First, CNNs images JavaScript CSS.

They get stored in CDN, they get cached in CDN so they load instantly no matter where you are in the

world.

Then, in e-commerce platforms, product pages for popular items often hit same database queries again

and again.

So instead of repeating them over and over, we cache the catalog results for quick rendering and reduced

back end load.

User session is another common use case.

Systems like Redis cache save user session data in memory making login and identity check lightning

fast.

Also search when users search frequently for similar terms like best budget laptops or budget mobile

phones.

These search results are often cached, reducing the compute cost and improving overall speed.

One use case we should talk about is about the microservices architecture.

In microservices architecture, it is common to cache API responses so that repeated calls do not result

in expensive recomputation or downstream service load.

So these are just a few places where caching turns slow, expensive operations into fast, scalable

experiences.

And it's often the difference between a good system and the great one.

So let's quickly go over some of the interview questions from this lecture.

These questions are not just theoretical, they are kind of questions.

Interviewer asked to assess your system, intuition and trade off thinking when it comes to caching.

So everything that we have covered in this lecture gives you the tools to answer them confidently.

And just like last time, there is a reference PDF attached with the detailed sample answers to help

you revise and practice these questions.

Okay, so let's wrap up this lecture by looking at the summary and key takeaways of this lecture.

First, caching dramatically improves response time, especially by avoiding repeated work or slow operations.

It reduces back end load and helps system scale gracefully under pressure.

The key is to choose the right cache type, whether you want client side caching, server side caching,

whether you want a CDN, or whether you want to cache the database contents.

That is something that you will have to choose.

Then you will have to apply the strategy strategies like, uh, read through, right through, right

back.

Lazy loading to get your desired results, then eviction policy LRU, lfu, Fifo and deciding TTL.

These things are also important to consider when it comes to caching.

Then we looked at Redis.

Tools like Redis make the caching implementation both powerful and production ready.

So caching is not an afterthought.

It should never be an afterthought.

It is foundational in any high performance, scalable architecture application.

So that concludes this lecture on caching.

What is next?

Next we will look at messaging and queues for decoupled architecture.

There we will explore how asynchronous communication help build scalable and fault tolerant systems.

So I will see you in the next one.
