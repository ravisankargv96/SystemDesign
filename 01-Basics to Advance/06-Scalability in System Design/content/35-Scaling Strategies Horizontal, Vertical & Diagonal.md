Hello and welcome to this lecture on scaling Strategies horizontal, vertical and Diagonal Strategies.

So in the previous lecture we explored how scalability works, what scalability means, why it matters,

and the challenges it introduces.

Now we are moving from concept to execution.

In this lecture we will break down the three core scaling strategies you will encounter in system design.

Vertical scaling, which means scaling up by adding more power to a single machine.

Horizontal scaling which means adding more machines, and diagonal scaling, which is a hybrid.

We'll analyze when to use which, how they impact cost, complexity and performance, and what trade

offs architects and engineers must make in real systems.

If you are preparing for interviews or designing real time systems at scale, this is a must know material.

So let's get started.

Before we dive into the details, let's do a quick recap of the three types of scalability we introduced

in the last lecture.

The first is vertical scaling, also known as scaling up.

This means adding more CPU, Ram, or storage to a single machine to make it more powerful.

Second is horizontal scaling or scaling out.

Here, instead of upgrading one machine, we add more machines to distribute the load across them.

This is the foundation of most cloud native architectures.

Then we have this hybrid approach called diagonal scaling.

A combination of two.

You scale vertically until it is no longer making sense or you are now hitting the limit.

Then you scale horizontally.

It's a flexible strategy which is used in real world systems that grows incrementally.

So now that we are aligned on terms, let's go deeper on each of these scaling strategies.

Okay.

Now let's have a closer look at the three main types of scalability and how they work in practice.

So first is vertical scaling.

Scaling up.

This is where you upgrade your existing server adding more CPU power, memory or disk.

The big advantage here is that it is simple to implement and no need for distributing data or syncing

across nodes, but it has some limitations.

We can only go so far because we will hit the physical hardware limits.

And more importantly, our system is still a single point of failure if we keep using only one server.

So we have horizontal scaling, which is also known as scaling out.

This is where you add more machines or nodes to handle the load.

But in this we will need to have tools like load balancers to distribute traffic.

And your architecture must be stateless or properly coordinated by some mechanism, so that if you have

some state in your servers, all the servers can access it.

Horizontal scaling is powerful and flexible, but it introduces complexity like data replication, synchronization,

and system orchestration.

Then we have this approach of diagonal scaling the best of both worlds.

This is the hybrid strategy we were talking about.

So we start by scaling vertically.

It is simple and cost effective early on.

Then as your system grows, you scale horizontally to handle real load.

This approach is actually very common in cloud native apps because it gives you early simplicity and

long term scalability without wasting money upfront.

So what are the key takeaways?

Vertical scalability.

It is easy to start with, but it has limited growth, horizontal scalability.

It is very powerful, but there is some inherent complexity involved.

Then diagonal scalability.

It is practical, flexible and scalable over time because it takes the best of both worlds.

Now, when it comes to choosing a scaling strategy, there is no one size fits all.

It all comes down to the classic system design triangle.

Cost, complexity and performance.

So let's break down what each means and how they compete.

So let's start with cost.

Vertical scaling often starts cheaper.

Just upgrade your machine.

No need for extra infrastructure.

But eventually high end hardware gets very expensive.

Horizontal scaling adds more infrastructure cost.

More machines, more networks, more cloud service overheads means extra cost for all these things,

plus operational cost Orchestration, monitoring, load balancing.

All this add up to the cost.

So while horizontal scales better in the long run, it comes at a higher cost.

Then second thing to consider is complexity.

Vertical scaling is simple.

Upgrade a box and you're done.

No distributed coordination.

No replication, no sharding.

But horizontal scaling brings in a lot.

We need to have load balancing, state management, data consistency, service discovery.

So horizontal scaling even though it is more robust.

But it requires thoughtful architecture and operational excellence procedures because it brings complexity

in your system.

Then we have the third pillar called performance.

Vertical scaling can give you great performance, especially for CPU heavy or memory bound workloads,

but it can also create single points of failure and bottlenecks.

On the contrary, horizontal scaling allows for parallelism and redundancy and can serve many concurrent

users.

But performance depends on how well your app is built for scale, so you need to have mechanisms to

handle statelessness, statefulness, concurrency, etc..

So what is the key difference?

Well, every scaling decision is a trade off.

If you are a early stage company or working with a monolith, vertical scaling might be enough.

If you are building for growth and already at scale, horizontal scaling is the future.

And the diagonal scaling gives you the realistic path to scale.

This is where we get the best of both worlds.

Growing smartly over time is the philosophy of diagonal scaling.

So most organizations try to use diagonal scaling as the preferred choice.

Now let's bring this all together with some real world examples of how companies scale and how you can

decide what to use when.

So let's start with this example of Twitter.

Twitter.

Early on days, Twitter ran as a monolithic app, which was fine but for limited users.

But as the user base exploded, they hit performance and reliability issues.

So they moved to horizontal scaling.

We breaking the monolith into microservices, added load balancing, caching, and distributed databases.

This shift allowed them to handle massive global traffic with resilience, usually small startups and

MVPs.

If you are building products from scratch, you probably don't need the complexity of distributed systems.

So just start with vertical.

One app, one database and scale it up as it is needed.

It is cheaper, it is faster to deploy and it is easier to maintain early on.

Then there is this example of AWS Lambda are.

These apps often begin small, but they are designed to scale automatically.

They start vertically with minimal infrastructure, but these cloud platforms allow them to diagonally

scale so they can automatically handle the spikes in traffic and also horizontally scale whenever required.

So this is great for cost control while being ready for big scale.

So when to choose what.

So startups choose vertical scaling initially because of the minimal complexity fireside ration.

And it is good enough for the small user base that they have.

But as they grow, they actually choose horizontal scaling.

Also, they choose redundancy, throughput, reliability, load balancer, stateless services and distributed

databases in their applications.

If you look at cloud native products, they usually adopt diagonal scaling.

They start simple, they scale elastically as the load increases, and they use auto scaling groups

to automatically scale up or scale out.

So the main idea is that do not overengineer too early, but don't wait too long to prepare for growth.

Your scaling strategy should match your current stage and be ready to evolve as the traffic demand increases.

So let's take a quick look at some of the interview questions that you might face that are related to

whatever we have learnt in this lecture.

Um, these questions are not just academic.

They test your understanding of real world systems also.

So whatever we have covered so far, you should be able to answer these questions.

Also there is a PDF with answers attached with this lecture.

So let's recap what we have learned in this lecture on scaling strategies.

First, we looked at vertical scaling.

The simplest way to scale just add more power to one machine, more CPU, Ram, storage and we are done.

It's great when we are small or starting out, but it has limitations.

Physical limitations are there.

You cannot scale vertically after a limit.

Then we looked at horizontal scaling, the go to strategy for the large systems.

Add more machines.

Distribute the load.

We get better performance and higher availability.

But it needs careful planning because it brings in extra complexity.

So we need things like load balancing, data replication, stateless services and much more.

Then we looked at the diagonal scaling, which is a hybrid approach used by many cloud native systems.

They start by scaling vertically when small and then add horizontal scale as the system grows.

So balancing simplicity City early on and future proofing.

The cost control is something that diagonal scaling provides.

So what is the key takeaway of all these scaling strategies?

Well, your scaling approach should evolve as your systems and user base grows.

Each method has a trade off in terms of cost, complexity, and scalability.

So choose what fits your stage and need.

So that's it for this lecture on scaling strategies.

What is next?

In the next lecture, we zoom in to one of the key enablers of horizontal and diagonal scaling, which

is load balancing.

We will try to look at what load balancers do and different types of algorithms they have, and how

cloud providers offer load balancing solutions like AWS Elastic Load Balancer, Azure Load Balancer,

and many more.

So I will see you in the next one.