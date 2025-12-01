Hello and welcome to section eight of our course in this section is all about performance.

In this section we will dive into the heart of system performance, not just how fast a system runs,

but how well it scales, responds, and delivers under pressure.

So let's get started.

So in this section, we will cover six core topics that will sharpen your understanding of system performance

from multiple angles.

The first one will be introduction to system performance.

We will start by defining what performance really means in system design.

We will explore things like latency, throughput, SLAs and SLOs.

Then we will learn how caching can dramatically reduce response time and load.

Then we look at how asynchronous communication using queues and brokers improve scalability, fault

tolerance and performance across distributed systems.

Then we will go and explore how modern systems handle multiple tasks efficiently.

Looking at thread pools, non-blocking, I o and other things.

Then we will look at database performance optimization techniques.

This lecture will focus on optimizing your database layers by indexing, denormalization, partitioning,

sharding, and other things.

And then finally we will tie up everything together, revisiting key concepts, common interview scenarios,

and tips for designing systems that stay fast under scale.

So let's get started.

So let's start with the first lecture which is Introduction to System Performance.

In this lecture, we will lay the foundation for everything else that we will explore.

In the complete section, we will learn what performance really means in the context of system design

and why it is much more than just speed.

We'll break down the key concepts like latency versus throughput, responsiveness versus scalability,

and how engineers measure performance in the real world using SLAs, SLOs and percentiles.

You will also see why performance isn't just a technical concern, it directly impacts user experience,

business metrics and engineering priorities.

Finally, we will touch on performance testing, monitoring, and how to think about performance holistically,

not just as an optimization, but as part of system architecture itself.

So let's dive in.

So what exactly is performance when we talk about system design?

At its core, performance is about efficiently running a system and that system meeting its functional

requirement, especially when it is under load.

It is not just about speed, it is also about how well the system holds up as the demand grows.

Users increase or data gets large.

There are three key dimensions to consider here.

The first is speed.

How quickly does the system respond to request?

This is often measured in terms of latency or response time.

Second is capacity.

How much work can the system handle at once?

Think of this as throughput request per second.

How many concurrent users in terms of all those things?

Then we have efficiency.

How efficiently does the system use resources like CPU, memory and network under stress?

The important thing to know here is that performance is not a single number or metric.

It is a multi-dimensional goal where you balance speed, scale, and resource usage to meet both technical

and business expectations.

So two of the most critical performance metrics in system design are latency and throughput.

And understanding the difference between them is the key.

Latency is the time it takes to process a single request from start to finish.

It is typically measured in milliseconds or seconds, and it directly affects responsiveness how fast

your system feels to the end user.

Then throughput, on the other hand, is the number of requests a system can handle per second.

You will often see this measured as requests per second or transaction per second.

And it reflects your system's capacity and scalability.

A very common misconception is that low latency means higher throughput, but that is not always true.

You can have a fast system that only handles a few user, or a high throughput system that slows down

the individual request.

The real challenge in system design is to balance both of them, keeping latency low and throughput

high.

Based on our application specific needs, we will have to achieve this balance.

Now in system design, we often hear about scalability and responsiveness also.

And while they are related, they are not exactly the same thing.

So let's try to understand what they are.

Scalability is all about your system's ability to handle increased load.

More users, more data, more requests without degrading performance.

It answers the question can this system grow smoothly as demand increases?

There are two main types of scaling.

We have already seen horizontal scaling and vertical scaling, so we will not go into that again.

Second is responsiveness.

Responsiveness, on the other hand, refers to how quickly your system responds to each request.

It is tightly linked to latency, even under heavy load.

A responsive system should feel snappy and reactive.

But there is a catch.

A system can be scalable but not responsive.

For example, it might handle 10,000 users, but each user has to wait several seconds for a response.

And that is not good enough for real time or interactive applications.

So what should be the goal of our system?

The goal of a good system design is to ensure responsiveness at scale.

You want systems that not only grows with demand, but also maintains a great user experience as they

grow.

Now, to improve performance, first we should be able to measure it.

Measure it clearly, consistently and accurately.

That's where these terms like SLAs, SLOs and Slis come in.

These three key terms form the foundation of performance tracking and production systems.

So what is an SLA?

SLA service level agreement.

This is an external contractual guarantee made to the users or clients.

For example, we guarantee 99.9% uptime each month.

So whatever is external contract with the end user is SLA.

Failing an SLA may have real business consequences, including financial penalties and legal actions.

Then we have service level objectives SLO.

This is for internal performance target.

What the engineering team aim for is called SLA.

It is more flexible than SLA and helps guiding the operational goals of the system.

An example could be 95% of the request should complete under 300 milliseconds.

Then we have SLA, SLA or service level indicator is the actual measured value of the performance metric.

For instance, currently only 93% of the requests are under 3300 milliseconds.

That tells us that we are falling short of our SLO and we need to investigate to optimize the system.

So in short, SLA is what you promise to the customer.

SLO is what you aim for internally and SLA is what you are achieving right now.

Together, these help you monitor, analyze, and improve performance in a way that's transparent and

accountable both to you and for your users.

Now, we should also try to understand about percentiles, because when it comes to performance metrics,

especially latency, relying on the averages or means can be dangerously misleading.

Why?

Because mean latency doesn't tell you how bad the worst experiences are in the real world system.

It is often the tail latency, the slowest responses that frustrates the user and breaks the experiences.

That's where percentile comes in.

They give you a much clearer picture of how performance distribution is.

So first is P50.

This is the median half of the request are faster than this value.

It is a good general indicator but not good enough for high performance systems.

Then we have p95.

This means that 95% of the requests are faster than this latency value.

So if your p95 is 300 milliseconds, that would mean that 95% of your requests are less than 300 milliseconds.

Then we have p99.

99.

This is tail latency.

It shows the latency at the 99th percentile, or in other words, the slowest 1% of the request.

And these are often the most important to monitor, especially in real time systems, interactive UIs

and APIs.

So if you are only optimizing for the average, you are ignoring the outliers that might be causing

the real user pain.

So tracking P95 and P99 can help you design for consistent performance, not just fast enough.

For most of the time, we will say fast enough for 99% of our user requests.

So in short, percentiles are always a good measure compared to averages, especially when performance

really matters.

Now, performance in today's world is not optional.

It's a core feature.

So why is it a core feature?

Well, first, because of our users.

Users are nowadays using mobile and web platforms.

They expect instantaneous responses.

A few hundred milliseconds can be the difference between a seamless experience or a frustrated experience.

Then poor performance can actually have very bad consequences.

Users can abandon the slow responding websites, and especially for an e-commerce platform, every second

of delay can mean a lot of lost revenue under high load.

Remember, your app's reputation is at stake.

If it is slow, users won't just leave, they will remember and they will probably never come back.

That is why performance should be treated as a first class design goal citizen, and not something that

we can patch up later.

Always remember a fast, responsive system improves user satisfaction, operational efficiency, and

even infrastructure cost.

Because optimized systems waste very fewer resources.

So the bottom line is don't treat performance as an afterthought.

In modern applications, performance should be done right from the start.

Only now to build high performing systems, you can't just measure performance, you need to test it

under different conditions.

That is where performance testing comes in.

There are several types of performance testing, and each one has a different set of weaknesses and

behaviors that they reveal.

So first one is load testing.

This checks how your system performs under expected normal load.

So this creates a baseline.

Can your system handle what it is built for.

Second is stress testing.

This pushes your system beyond its normal limits.

To see how it behaves under pressure.

Does it crash gracefully?

Does it degrade predictably?

Then there is spike testing.

It simulates sudden bursts of high.

Traffic like flash sales or virtual traffic spikes.

You are testing how well the system can absorb and recover from quick surge of traffic.

Then we have endurance testing, also known as soak testing.

This checks if your system can run under load for a long time without memory leaks, slowdowns or crashes.

Think of it as testing for fatigue of the system, whether your system is getting tired, if it is under

load for a very long time.

So the goal of all these tests are very simple.

First, uncover the bottleneck before users do.

And then ensure that the system is reliable in real world conditions.

Performance issues usually hide until we are under pressure.

So these tests bring them into light before they become the actual user facing incidents.

Now we have talked about the performance testing, but testing is not just enough.

We also have to do performance monitoring.

Performance monitoring is an essential practice in running reliable systems.

So the first thing to understand is that monitoring is not same as testing.

While testing is done before deployment, monitoring is continuous.

Even after deployment, it happens in real time once your system is live and serving users.

So there are several categories of tools that can help you monitor performance.

So first there are APM tools.

APM means application performance monitoring.

APM platforms like Datadog help you doing the monitoring in terms of performance.

They give you deep insights into how your application behaves under load from slow endpoints to bottlenecking

services.

Then we have logs and metrics tools.

So logs and metrics tools help you collect, visualize and alert on the performance data across your

infrastructure.

So what they will do is they will just collect the logs across all the services that you are running

and then create insights from those logs.

And you can figure out where exactly the performance bottleneck is.

So what should you be tracking for performance?

Well first is latency and throughput.

How fast are responses and how many can you handle in a given time frame?

Second, you should measure error rates.

Our users seeing the failures and if yes, how often.

And third, you should check for resource usage.

How much CPU, memory, disk or database queries are being consumed.

All of these together will give you a real time pulse on your system health.

So what is the bottom line?

Bottom line is you can't improve what you don't measure.

And with the right monitoring, you are not just reacting to problems, you are preventing them because

you have the measurement numbers right?

Measurement numbers with you all the time.

So here on this slide we have some important interview questions related to system design.

Each of these questions is tied directly to the topic that we have covered in this lecture.

So if you have followed along you should now be able to answer these questions confidently.

Also, we have attached a reference PDF with detailed sample answers for each question in the resources

section of this lecture.

Now let's wrap up things by looking at the quick summary and key takeaways of this lecture.

First, remember that system performance is not just about speed.

It is about how well a system handles real world load while staying fast, efficient and scalable.

Then we explored the difference between latency and throughput.

How fast individual requests are processed is latency, and throughput is how many requests your system

can handle per second.

Then we looked at SLAs, SLOs and SLAs and how to quantify performance expectations.

We looked at percentiles and how p95 and P99 gives us real insight into the user experience, especially

because they are tail latency numbers.

Then we have covered how to test performance using load test, stress test, spike test and endurance

test.

And then we looked at how to monitor systems in production using APM tools, metrics and logs.

The big takeaway of this lecture is that performance must be designed, tested and continuously monitored.

It should always be the first thought in our mind when we are doing the system design.

It is not an afterthought.

It is a core feature of every modern, scalable and user focused system.

So that brings us to the end of this lecture on Introduction to Performance.

What's next?

In the next lecture, we will dive into one of the most effective ways to boost performance caching

how it works, caching strategies and when to use it.

So I will see you in the next one.
