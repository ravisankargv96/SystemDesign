Hello everyone, and welcome to section six of this course on Mastering System Design.

This section is all about scalability in system design.

As systems grow, so does the pressure on performance, reliability and cost.

In this section, we will explore how to design systems that can scale smoothly and efficiently.

Whether you are dealing with 1000 users or a million users, your system should be performing efficiently.

We will kick off things by defining what scalability means, the types of scalability, and why it is

a must have property for modern systems.

Then we will take a deep dive into the strategies for scaling from vertical and horizontal scaling to

a lesser known but practical diagonal scaling, along with the trade offs to consider when choosing

the right approach.

Once we understand how systems scale, we will turn our attention to load balancers, the unsung heroes

that distribute traffic and keep system responsive under pressure.

You will learn about the types of load balancers, popular algorithms, and how industry giants like

AWS and Azure implements them.

Next up, we will explore auto scaling the engine behind elastic infrastructure.

We'll walk through how it works.

The solution cloud providers offer the best practices for monitoring, proactive scaling and cost management

in cloud environments.

Finally, we will wrap it all up with the summary, insights and key takeaways for whatever we have

learned in this section.

So let's get started.

So let's start with lecture one introduction to scalability.

So in today's world where systems need to handle millions of users global traffic and dynamic workloads,

designing for scalability is no longer optional, but it is essential.

In this lecture we will explore the core concept of scalability.

What it is, why it matters, and how it impacts every part of your system design.

You will learn about the different types of scalability, from vertical and horizontal to the challenges

that comes with scale like latency, cost, and downtime.

Whether you are preparing for interviews or designing production ready systems, this is the foundation

you need.

By the end of this lecture, you will have a clear understanding of the why behind scaling, which will

prepare you for the how in the upcoming lectures.

So what exactly is scalability?

Well, simply put, scalability is the ability of a system to handle increasing amounts of work gracefully

without breaking, slowing down, or becoming unreliable.

It's not just about adding more users, it's about making sure your systems can maintain performance,

availability, and reliability even as load increases, whether that's more traffic, more data, or

more transactions.

Think of scalability as your system's growth potential.

A well-designed, scalable system can start small and grow big without a complete overhaul.

When a system scales well, users won't feel the pressure.

Even if the system is serving ten times or 100 times the usual traffic.

So in system design interviews or real world architectural decisions, always ask this question can

this system scale when needed and how will it behave under stress?

So let's talk about why systems need to scale in the first place.

Most systems start small.

A few users manageable data, predictable traffic.

But as they grow, so do the demands.

So first there is user base growth.

Maybe your app goes viral or expands into new regions.

Suddenly, thousands or millions of users are logging in daily.

Next could be data volume.

With more users, more devices and more sensors, more data gets generated, especially from things

like IoT or analytics.

This can actually increase exponentially.

Then there could be a possibility of having peak events.

Think of an event like Black Friday concert hall ticket sales or trending news events.

Traffic can spike ten times in seconds.

If your system can't scale, it crashes.

You also want to avoid service degradation or downtime when a system can't keep up with demand.

It slows down or fails completely, and the users get unhappy and leave.

Finally, many systems must meet performance SLAs.

SLAs are service level agreements like responding within 200 milliseconds or maintaining 99.99% uptime.

You can't hit these targets without scalability.

So bottom line, if your system can't scale, it can't grow, and in many cases it won't even survive

if it cannot grow.

So now that we know why systems need to scale, let's quickly look at the main types of scalability.

First is vertical scaling, also known as scaling up.

This means adding more power to a single server, like increasing CPU, Ram, or disk space.

It is simple and fast, but comes with limits and it can get expensive.

Then there is horizontal scaling or scaling out.

This involves adding more servers and distributing the load across them.

It's how big systems handle huge traffic.

Think of microservices architecture and distributed architecture and they will implement horizontal

scaling.

Both approaches have trade offs, and in the real world systems often use a hybrid strategy.

But don't worry, we will go deep into these scaling methods and when to use each one of them in our

next lecture.

But for now, keep in mind vertical scaling means getting a bigger box.

Horizontal scaling means getting more boxes.

So while scalability sounds great in theory, scaling systems isn't easy.

Let's walk through some of the most common challenges you will face as your system grows.

First is latency.

This is the delay between a user making a request and getting a response.

It could be due to network hops, slow database queries, or synchronous communication between services.

The more services you add, especially in microservices or distributed systems, the more latency starts

to creep in.

Second is bottlenecks.

Your system is only as fast as the slowest part.

A single component, like a log database, limited memory, or a single threaded task can bring everything

to a crawl.

And here is the tricky part bottlenecks often don't show up until you are under load.

Then third is downtime.

As your system scale, you add more servers, more services, and there are more chances of failures.

Routine actions like code deployments, scaling events, or updates can take down parts of your system.

So designing for high availability becomes much, much harder and much more important when you have

multiple servers in place.

Then there is this cost.

Scaling is not free.

More servers mean more CPU, more Ram, bandwidth, storage and it all adds up.

If you use auto scaling without any control, you risk runaway cost.

But if you overprovision, you waste money on unused resources.

So the key is to balance performance with efficiency and always monitor what your system is doing and

scale accordingly.

Now let's take a quick look at some of the interview questions you might face that are directly tied

to what we have learned so far, only in this lecture.

These questions aren't just academic.

They test your understanding of real world system behaviors under load.

If you have followed this lecture closely, you already know how to approach all of these.

Also, a PDF with answers is attached in the resources section of this lecture in case you want to refer.

So before closing, let's quickly wrap up what we have covered in this lecture.

First, scalability is the ability of a system to grow to handle more users, more traffic, more data

without crashing or slowing down.

Then we looked at there are two primary ways to scale vertical scaling, which is adding more power

to a single machine.

Horizontal scaling, which is adding more machines to share the load.

Then we looked at the scaling related complexities.

We looked at how scaling is not free.

It comes with challenges like increased latency, bottleneck downtime, and rising infrastructure costs.

So what's next?

In the next lecture, we will go from theory to practice.

You will learn about scaling strategies, how to actually implement horizontal, vertical and even diagonal

scaling, and how to make smart choices based on cost, complexity and performance tradeoffs.

So we are now stepping into the how part of designing the scalable systems in the next lecture.

So I will see you in the next one.