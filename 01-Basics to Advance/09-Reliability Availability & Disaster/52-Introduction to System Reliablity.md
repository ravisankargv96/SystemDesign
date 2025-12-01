Hello and welcome back to section nine of this course on Mastering System Design.

In this section, we will explore how modern systems maintain stability, recover from failures, and

stay online under pressure.

These concepts are critical when designing production grade systems, especially in cloud native and

distributed environments.

So welcome again to this section on reliability, availability and disaster recovery.

So let's get started.

So here is what we will be covering in this section.

We will begin with an introduction to system reliability.

Understanding key concepts like mtbf, Mttr and SLAs and how reliability impacts system design.

Next we will dive into high availability, fault tolerance and failover mechanisms, all essential for

minimizing downtime and service disruptions.

Then we will move on to backup and recovery strategies, exploring how to protect data and ensure recoverability

in case of failures.

After that, we will look at disaster recovery in practice.

Discussing real world strategies and cloud based solutions.

And finally, we will wrap it all with a summary and recap.

Focused on designing reliable distributed systems that can stand the test of scale, load and failure.

So let's start with lecture one of this section Introduction to System Reliability.

In this lecture, we will lay the foundation for understanding what reliability really means in the

context of system design.

We will define core concepts like mtbf Mttr and SLAs.

And we will clarify the difference between availability and durability.

The two terms that are often confused but mean very different things.

You will also see how reliability plays a crucial role in building distributed systems and cloud native

architecture, especially as systems, scale and complexity grows.

By the end of this lecture, you will have a solid grasp of reliability principles and how they shape

the real world system behaviors.

So let's talk about why reliability really matters.

Well, in today's world, users expect systems to be always available, consistent, and trustworthy.

Whether it's a banking application, an e-commerce application, or a communication tool, any amount

of downtime can cost money, reputation and erode users trust.

Reliability isn't just about preventing failures, it is also about how quickly and gracefully a system

can recover when something goes wrong.

So there is a saying systems will fail.

Reliability is how gracefully they will handle it.

And that's the mindset we need to adopt when designing systems at scale.

So what exactly is system reliability?

Well, in simple terms, reliability is a system's ability to operate continuously without failure.

And it's not just about being available.

It's also about working correctly and consistently all the time.

So when we talk about reliability we are looking into several key concepts.

First is correctness.

Correctness means the system performs the intended function without errors.

Then consistency behavior is predictable and repeatable across requests and over time.

Then we have fault tolerance.

It is the ability to withstand failures without complete service disruption.

And of course, the uptime or availability where the amount of time the system is up and running.

All these things come together to define how reliable your system actually is.

Now how to measure reliability?

Well, there are two key metrics that are often used.

Mtbf and mttr.

So what exactly these two things mean?

First, Mtbf it means mean time between failures.

This is the average amount of time your system runs without encountering a failure.

The higher the mtbf, the more stable your system is.

And then we have mttr, which is mean time to recovery.

This tells us how long it typically takes to recover when something goes down.

The lower the NTR, the faster you are able to bounce back.

So in a perfect world, we want high mtbf and low mttr, meaning our systems rarely fail.

And even if they fail, it recovers quickly.

Together, these two metrics give a powerful picture of how reliable your system really is.

Then SLAs.

What are SLAs or service level agreements?

I think we have looked at it briefly in one of the previous lectures.

SLAs are formal commitments, contractual commitments that define the expected level of service from

a system.

So they typically focus on measurable performance guarantees.

So performance guarantees like availability percentage like 99.9% uptime is guarantee response time.

How fast your system respond to request error rate, how frequently the system fails to deliver correct

results.

So let's take 99.9% availability as an example.

It sounds impressive, but it still means that you will get more than eight hours of downtime per year.

So understanding SLA is very critical not just to meet user expectation, but to define clear boundaries

between teams, vendors, and clients.

When it comes to reliability and SLA.

Does help in that.

Now let's talk about availability and durability.

The two key concepts that, although are related, focus on different aspects of system reliability.

So what is availability?

Availability refers to the system being accessible and responsive when user needs it.

So it's all about ensuring that the system is up and running with minimal downtime.

Durability, on the other hand, focuses on ensuring that data is safe and not lost.

Even if the system goes down, the data must remain intact in case of failures also.

And there should be no corruptions or data loss.

So to sum it up, availability is about keeping the system online and durability is about keeping the

data safe even in the event of failure.

Now let's look at how reliability impacts system design.

So there are several design decisions that directly affect the reliability of system.

So first is redundancy.

So by implementing multiple instances and failover strategies we ensure that if one component fails

another one can take over.

This minimizes downtime and improves scalability.

Then we need to implement health checks and monitoring.

Continuous health check and monitoring allow us to detect failures early and trigger alerts or automatic

recovery process, preventing prolonged outages.

Then we have retry mechanism and circuit breaker patterns for system that interact with external services.

Retry mechanism can help recover from transient failures.

Circuit breakers, on the other hand, prevent cascading failures by temporarily halting the request

to unhealthy services.

So it breaks the circuit by not calling the unhealthy services again and again and then.

Use of distributed design patterns.

Using patterns like replication and quorum based approaches help ensure that data is available and consistent

across nodes, even when one or more component fails.

It will be available, so each of these decisions are crucial to ensure that your system is reliable

and can handle failures gracefully.

And that is why reliability is so important from a system design perspective.

Because based on your system requirements, you will have to take decisions on following things that

we are seeing on screen.

Now.

Most of the modern systems are distributed systems.

So let's dive into reliability in distributed systems where the challenges and solutions are more complex

due to the nature of multiple independent components working together.

So what are the challenges in distributed systems?

First is network partition.

Communication between nodes may fail, causing parts of the system to be temporarily not available.

This can lead to inconsistencies and data loss.

If we are not handling them properly, then there could be node failures itself.

Individual nodes or services may fail unexpectedly, which can impact the availability of the system.

If redundancy is not properly set up.

Then there is this notion of eventual consistency.

So in distributed systems, achieving strong consistency can be difficult due to network delays and

failures.

So instead, systems often implement eventual consistency where updates propagate through the system

over time instead of them propagating right away.

So what could be the solutions to improve reliability in Distributed systems.

First is we have seen cap theorem.

Our solution should be cap aware.

Always implement cap aware design.

The Cap theorem helps us in designing systems, especially in case of distributed systems, depending

on whether we want consistency or whether we want availability depending on system needs.

So understanding which of these aspects are important for your system and prioritize in different scenarios

is key to ensuring system reliability.

Second is fault tolerance.

We should always ensure that our systems are fault tolerant.

How can we do that?

We can do that by doing fault isolation.

This strategy ensures that a failure in one part of the system doesn't affect other parts.

So by isolating faults, we can limit the impact of failures and allow the systems to recover more effectively.

Then we have something called replication and consensus algorithms.

So to ensure that data is available and consistent replication across multiple nodes is vital.

Consensus algorithm ensures that distributed nodes agree on the state of the data, even in case of

network failure.

So by applying these solutions, we can significantly improve the reliability of distributed systems

and ensure they handle failures gracefully.

Now let's talk about reliability in cloud native systems.

Why?

Because the cloud infrastructure brings its own set of challenges and a different set of solutions.

So the very first thing that is important to understand is that cloud infrastructure is inherently unreliable.

While cloud providers offer high level of availability, they cannot guarantee that every component

will always be up.

Therefore, we need to design for failovers, not just avoid failovers.

So here are key design principles for achieving reliability in cloud native systems.

First is always designed for transient failures.

So in the cloud failure can happen intermittently.

But they often recover very quickly.

So these failures are brief and recoverable.

So by designing systems that can handle short transient failures, by using logic like retry timeouts

and circuit breaker, we can ensure that these failures don't cause long term issues.

So the first thing always design for transient failure.

Then second is about auto scaling and self-healing.

So cloud native systems should be designed to automatically scale based on demand.

Auto scaling allows the system to maintain performance during peak spikes.

And self-healing is a mechanism where automatic restarts of failed Field service help maintain uptime

by resolving issues without any human intervention.

Then there is this thing called chaos engineering to test resilience of our systems.

So one of the best practice for building reliable cloud native system is chaos engineering.

This involves intentionally introducing failures like shutting down services or causing network failures

in a controlled manner to see how the system reacts and ensure whether it can recover or not.

It helps to uncover hidden weaknesses and improve system robustness.

So the gist is that design for failure mindset should always be there.

The core philosophy in cloud native environment is to design for failure.

Since failures are inevitable, designing systems that can gracefully handle failure is critical.

This means creating systems that can continuously function With partial outages, still maintain data

integrity, and are able to recover quickly.

So by embracing these principles, cloud native systems can be more resilient and reliable, even in

the case of unexpected failures and disruptions.

So now we have some important interview questions, uh, visible on the screen.

So these questions test both your conceptual understanding and your ability to apply reliability principles

in real world scenarios.

If you have gone through the content we have covered so far, you should be able to answer these confidently.

Also, a detailed answer PDF is attached with this lecture which can help you review and prepare more

effectively.

Now, before wrapping up, let's look at the summary and key takeaways of today's lecture.

First we looked at that.

reliability is foundational to user trust.

Without reliability, systems fail to meet user expectations.

Ensuring that systems are available, resilient, and trustworthy is key to maintaining a positive user

experience and your brand reputation.

Then we looked at metrics metrics like Mtbf, Mttr, and SLAs that are vital to quantify reliability.

We use these metrics to measure system performance and failure recovery.

High mtbf and low mttr are indicators of a reliable system.

Service level indicators and service level agreements set the expectations with users and provide benchmark

for availability and performance.

Then we discussed that design choices must anticipate and tolerate failures.

In any system, failure is inevitable.

It is not about avoiding failures, but about designing systems that gracefully handle failures.

Redundancy retries, health checks, and fault tolerant mechanisms are essential to reliability.

Then we looked at how in distributed and cloud systems, reliability is an active design challenge.

Distributed and cloud native systems face unique reliability challenges due to their complexity and

inherent unreliability.

Designing for transient failures.

Putting auto scaling and self-healing ensure resilience.

Then we looked at how chaos engineering helps uncover hidden weaknesses.

This brings an end to this lecture on Introduction to Reliability.

What is next?

In the next lecture, we will dive deeper into high availability, fault tolerance and failover strategies.

All key techniques for ensuring that your systems remain available even during failure.

So I will see you in the next one.
