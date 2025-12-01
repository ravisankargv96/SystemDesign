Welcome to this lecture on high availability, fault tolerance and failover.

This is a crucial topic in system design, especially as we aim to build highly resilient, reliable

systems that can withstand failures without causing downtime for end users.

So let's get started.

So let's start with redundancy.

Redundancy is at the core of any system designed for high availability and fault tolerance.

So essentially redundancy means adding additional components, systems or processes to prevent single

points of failure, ensuring that the system remains operational, even parts of it fail.

So why redundancy matter?

See, the main purpose of redundancy is to prevent single point of failure in a system without redundancy.

The failure of a single component could lead to the system wide outage, which can severely affect availability

and user experience.

But by introducing redundancy, we add backup systems or components that can take over the workload

in case of failures of the main component, ensuring the continuous operation of our system.

So what are the different types of redundancy?

So now let's try to break down the three key types of redundancies.

First is hardware redundancy.

This involves using multiple server or storage devices to ensure that if one fails, other can take

over.

For example, using a secondary server to handle requests.

If primary one goes down, or using a redundant hard drive in a Raid setup to prevent data loss from

a failed drive, then we have network redundancy.

Network redundancy ensures that system remains connected even if there is a failure in one network path

or route.

This could include having multiple data centers, network connections, or routers that can take over

in case of failure.

Ensuring there is no disruption in service due to connectivity issues.

Then we have service redundancy.

This is specially in microservices architecture.

So in microservices architecture it is important to have redundant services, whether it is a replicated

microservice or whether it is a database replication.

This ensures that if one service or database instance fails, another instance can continue processing

requests, reducing the downtime and improving the system resilience.

Remember, redundancy isn't just about having backup systems, it's about ensuring those backup systems

work seamlessly, taking over with minimal disruption when a failure happens.

Now let's dive into some specific redundancy strategies.

There are N plus one active active and active passive.

These are all strategies used to ensure availability, but each comes with its unique approach and trade

off.

So what is N plus one redundancy?

The idea behind N plus one redundancy is that you have one additional instance beyond what is strictly

required to meet your demands.

For example, if your system requires two instances to handle the load with n plus one, you would have

three instances.

So total two active that are required and one extra on standby.

This extra instance ensures that even if one instance fails, the system can continue to operate without

affecting service availability.

It adds an additional layer of fault tolerance, which is essential for critical systems when downtime

is not acceptable.

Then we have this model of active.

Active.

So in an active active setup, multiple nodes or instances are all active and work together to handle

the request.

Each node contributes to the processing load and the traffic is distributed across all available nodes.

If one node fails, the other nodes continue processing, providing high availability and balancing

the load evenly.

And there are some advantages to it.

So first is load balancing.

With multiple nodes actively handling traffic.

The load is shared, preventing any one server from becoming a bottleneck.

Then there is fault tolerance.

The failure of one node doesn't impact the overall system as other nodes are still operational, but

it does brings extra complexity because managing multiple active nodes requires sophisticated load balancing

and state synchronization mechanism to ensure that consistency is there and no data corruption is happening.

And the third model is active passive.

So an active passive configuration.

One configuration is active and handling all traffic, while other nodes are passive or standby state.

If the active node fails, one of the passive nodes is promoted to active to continue handling the load.

The advantage of this is that it is simple.

The setup is relatively simple to manage, as only one node is active at a time.

Also, it is cost effective.

The passive nodes don't handle traffic until a failure happens.

Making this approach less resource intensive than active active.

But there is a disadvantage.

It is less efficient for load balancing since only one node is actively serving traffic, leaving the

others idle most of the time.

Also, there is a failover latency involved in this model because when the active node fails, the system

need to switch to a passive node, which could introduce a short delay during the failover process.

So to summarize these three models, n plus one redundancy means adding an extra instance to ensure

that failure doesn't impact availability.

Active active model.

Multiple nodes work in parallel to share the load and handle failures seamlessly.

Active passive model one active node and other standby nodes that can kick in only when the active node

fails.

Offering simplicity, but it is less efficient when it comes to load balancing.

Each of these strategies offer a different balance of availability, cost, and complexity.

Now let's talk about a concept called graceful degradation.

What is graceful degradation?

Well, it refers to a system's ability to continue functioning during partial Failures, even if it

can't deliver its full set of features.

Instead of going completely down, the system degrades but does so gracefully by still offering core

functionality to the users.

Why is this important?

Because failures are inevitable.

Network issues, third party outages, traffic spikes.

These things are bound to happen with graceful degradation.

Your system is designed to absorb these shocks and continue to serve users in some meaningful ways.

Now let's take an example.

Imagine that you are running an e-commerce site during a high traffic event like Black Friday.

Your recommendation engine, which is powered by a separate microservice, starts failing.

So instead of bringing down the entire site, you temporarily disable the recommendation widget and

let users browse and checkout.

So the core functionality is still alive.

Life users can still shop.

Your brand can maintain trust of the users.

This is the graceful degradation in action.

So what are the benefits of graceful degradation?

Well first is obviously user experience.

It keeps our users engaged and prevent frustration.

Second is resilience.

It shows the system was designed to anticipate and handle failures.

Then we have business continuity.

It prevents the total service outage and protect our revenue.

So in short, graceful degradation is all about prioritizing essential functionality and ensuring that

your system handles failure with elegance.

Now let's look at how availability is achieved in real world systems.

So first is load balancers.

We have talked about load balancers in previous lectures.

Also, load balancers are essential components in modern architecture.

They distribute incoming traffic evenly across multiple back end nodes or services.

This ensures that no single node gets overwhelmed.

If one node goes down, the load balancer reroutes traffic to healthy ones.

This pattern is especially important in active active setup where all nodes are handling requests simultaneously.

Second is replication.

This is about copying data across multiple servers or data centers so that even if one instance fails,

the data is still available elsewhere.

There are different kinds of replications, like synchronous and asynchronous.

Each comes with its own trade off in terms of latency and consistency, but the goal is the same ensuring

data availability even in case of partial failure.

Finally, we have failover.

This is a mechanism that detects failover and automatically switches to a standby node or system in

an active passive configuration, only the active node handles traffic, so when it fails, the passive

one steps in seamlessly.

If it is designed well.

These patterns load balancing, replication, and failover work together to create systems that can

withstand failures and continue to operate smoothly.

These things are the backbone of high availability.

Now, when we talk about building highly available and fault tolerant systems, redundancy is at the

core of that design.

So let's break down what that means in practice.

So first we need to have redundant components.

You want to ensure that no single failure can bring down the system.

That means having multiple instances of critical components.

It could be web servers databases message brokers, caches.

So have redundancy for all of them.

If one instance fails, the other continues to serve traffic seamlessly.

Second is geographical redundancy.

So it is not just enough to have multiple instances in the same data center.

What if the whole region goes down?

That's where geographical redundancy comes in.

Use multiple cloud regions or data centers.

Replicate data and services across these locations.

This is the key for disaster recovery and business continuity.

Third is automated failover.

Redundancy is only useful if we can switch over to backup resource quickly.

That is where failover mechanism should be automated.

We should be using health checks and monitoring so that it will automatically trigger the routing of

to new servers, spinning up of new resources, or switching to standby systems.

This removes the need for human intervention and ensures that the system remains available during failures

also.

So in short, designing for redundancy is about planning for failures and making sure that your systems

can recover on its own.

They can recover it fast and they can recover smoothly.

Now let's talk about something that is crucial in high availability architectures, and that is health

monitoring and self-healing system.

So what is health monitoring.

Well, it's all about continuously checking if different parts of your system are functioning properly.

You monitor things like server uptime, API response, error rate, CPU and memory usage, and you compare

them with the baseline.

If you think that they are not working as expected and something is going wrong, alerts are triggered

so that teams can act fast even before users even notice.

Now self-healing system.

Here's where things get even more interesting.

So instead of just detecting errors by those alerts that are coming from the monitoring, what if your

system could fix itself?

That is the idea behind self-healing system.

So if a server becomes unhealthy, the orchestrator can look at the alerts and take necessary action.

It can restart that instance.

Or if that node in the cluster became unreachable, traffic will be rerouted to a new instance also.

These practices are especially critical in cloud native environments where things can and will fail

all the time.

So instead of trying to prevent every failure, we focus on detecting and recovering from failures automatically.

So the bottom line is health monitoring keeps us informed.

And self-healing keeps us resilient.

Now you have a few questions visible on the screen.

These questions test your ability to design resilient production systems.

Topics like redundancy, failover, and graceful degradation are often deal breakers in designing reliable

systems.

Good news is, you should now be able to answer these questions based on everything we have covered

so far in this lecture.

Also, there is an answer PDF attached as a reference with this lecture, so you can refer that too.

Now let's quickly summarize this and look at the key takeaways of this lecture.

We started with the concept of high availability designing systems to remain operational even during

failures.

This is achieved through redundancy and automatic failover mechanism.

Then we explored fault tolerance, which is all about building systems that can gracefully handle partial

failures.

Strategies like n plus one redundancy and graceful degradation ensure that the user experience doesn't

completely break down.

We also talked about failover system mechanism that automatically switch to a backup component when

something goes wrong, with minimal or no user impact, of course.

Then we looked at load balancers, how load balancers emerged as critical infrastructure for distributing

traffic efficiently, especially in active active setups.

Then we close with the importance of health monitoring and self-healing systems, which help us proactively

detect and recover from issues without manual intervention, or at least with minimal manual intervention.

All of these things are essential practices for designing resilient, reliable systems that users can

count on.

So this brings us to the end of this lecture.

What is next?

Next we will look at backup and recovery strategies and how to prepare for the worst case scenario without

losing data or time.

So I will see you in the next one.
