Hello everyone, and welcome to this lecture on concurrency and parallelism in system design.

This is one of those foundational topics that has direct impact on performance, scalability, and responsiveness

of any system we build.

Whether you are designing a high throughput web server, a back end task runner, or a microservice

that handles hundreds of simultaneous requests, you need to understand how to work with multiple things

happening at once.

So let's get started.

So let's dive into the core of today's topic concurrency and parallelism.

Both are essential concepts in system design, but they have different meaning and purpose.

So first let's start with concurrency.

Concurrency is when multiple tasks start, run, and complete in overlapping time periods, but not

necessarily simultaneously.

It's all about managing several tasks at once, even if they are not executing at the same time.

So concurrency is about task management, not task execution.

You can achieve concurrency even on a single core CPU.

The system switches between tasks rapidly to give you the illusion that you are running simultaneously.

The goal here is responsiveness.

You want to handle many tasks and respond quickly, even though they may not be running at the exact

same moment.

An example could be a web server handling multiple incoming HTTP requests using async IO.

The server is not processing every request at once, but it can respond to many requests efficiently

by switching between them.

On the other hand, when we talk about parallelism, parallelism is when multiple tasks are actually

executed simultaneously, typically on multiple CPU cores.

So parallelism is all about task execution, where all the tasks run at the same time to improve speed

and performance.

True parallelism requires a multicore processor.

Each task can run independently on its own CPU core, allowing for increased throughput and better performance.

An example could be a matrix computation, where different parts of the matrix are calculated simultaneously

across multiple threads.

This is a good use case for parallelism, because it allows you to break the problem into smaller chunks

and run them at the same time on different CPU cores.

So in short, concurrency is about managing tasks, especially when you have one CPU core and parallelism

is about executing tasks at the same time, but it requires multiple CPU cores.

So this distinction is crucial for designing systems that are both responsive and fast.

Now let's look at difference between processes and threads.

The two fundamental building blocks in concurrency and parallelism.

So process A process is an independent program running at its own memory space.

So processes are very heavier.

They are heavier to create and manage because each process needs its own resources like memories, file,

etc. since processes are isolated, they are safer.

If one process crashes, it doesn't affect other.

Each process runs in its own protected environment.

So think of running two separate applications on your computer, like a web browser and a word processor.

They don't share any memory directly, so even if one crashes, the other one is unaffected because

each of them is a separate process.

Thread, on the other hand, is a smaller unit of execution within a process.

Threads share memory within the same process, meaning they can easily communicate with each other.

Threads are lightweight and much faster to create and switch between them, because they are within

the same process and they share the same resources, so it is much easier to switch between them.

So um, but they can lead to the complex bugs like race condition.

If the same memory is being accessed by multiple threads, there could be a possibility that both of

them want to access that piece of memory causing the race conditions.

Think of threads.

Is, uh, Something in the same application, like web server handling multiple requests.

So these threads work together, share the same resource which allow for quick task execution, but

it requires careful management to avoid issues like race condition.

In summary, processes are more isolated and safer, but they are slower to create and manage.

Threads, on the other hand, are faster and lighter, but they come with the potential for concurrency

related bugs due to shared memory.

Understanding when to use a process versus thread is crucial in system design at.

This helps the balancing of efficiency and complexity in our system.

Now there are two more important concepts in managing threads and improving system performance thread

pool and worker model.

Thread pools are a collection of pre-created threads that can be reused to execute multiple tasks,

which help in optimized thread management.

So thread pool avoids the overhead of creating and destroying threads each time a task is supposed to

be executed, because the thread pool has already created threads in it.

This saves valuable system resources and improve system efficiency.

So instead of creating a new thread for every task, the system will take an available thread from the

pool, execute the task, and then return the thread to the pool when it is done.

One very good example of this is in ASP.Net core.

The system uses a thread pool to handle HTTP request.

So instead of creating a new thread every time a request comes in, the framework uses the pre-existing

thread from the pool.

Improving response time and system throughput.

Then we have worker models.

So a worker model involves a system where tasks are distributed to idle workers from the shared queue.

This model helps to improve the scalability and CPU utilization.

So what happens is that workers we have many workers which are often idle waiting for tasks to arrive

in the queue.

These are just waiting.

So when a task arrives, they are picked up by the available workers.

This ensures that CPU resources are efficiently utilized, especially under varying load.

So thread pools.

We know they help to reduce the overhead by reusing threads for multiple tasks and worker model distribute

tasks across workers in a queue, ensuring better scalability and CPU utilization.

Both models are critical for improving performance and efficiency in systems, Especially when dealing

with large scale concurrent workloads.

Now let's explore asynchronous processing, a very powerful concept that helps improve the efficiency

and performance of system, especially when dealing with IO bound tasks.

So why is async programming important?

Well, it allows us to avoid blocking threads during IO operation, which helps us keep the system responsive

and improves throughput.

So what happens in a traditional synchronous system is that when a thread performs an I o operation,

like reading a file or querying a database, the control has to wait for the operation to complete.

Because it can continue, the thread has to wait.

So this causes the thread to block and we call it a blocking operation.

But in contrast, asynchronous processing allows the task like IO operation to happen in the background.

So what it does is that whenever we reach to a point where any I o operation, like reading a file or

querying a database is required, that operation will start and we will free up the thread to do the

other work instead of waiting there idly.

So what are the benefits of doing this?

Well, the key benefits of doing it is that, uh, the task can run concurrently without waiting for

each other, so there is no thread blocking happening.

Then it will improve the throughput because more tasks can be processed simultaneously now.

So increasing the overall throughput of the system.

And I think most of the programming languages also support asynchronous processing.

Nowadays we have async await in C sharp and JavaScript.

Uh, we have uh promises available in JavaScript.

And we can in our architecture also use something like message queues for asynchronous processing if

we want.

Async processing is a great way to improve the system performance, especially for IO bound tasks.

By avoiding thread blocking, we can keep the system responsiveness and improve the overall throughput

of the system.

Now let's explore the concurrency in web servers.

So traditional web servers like Apache and all, what they used to do is that, um, they used to spawn

a new thread or process for each incoming request, which is okay, but this approach consumes more

resources as traffic increases, leading to scalability issues.

So it works for low to moderate traffic, but it becomes inefficient under heavy load.

So the modern web servers like ASP.Net core, nginx and Node.js, what they do, they use asynchronous

Non-blocking I o to handle many requests concurrently.

So.

So they often employ things like event loop model in Node.js or Threadpool model that we have in ASP.Net

core or nginx to implement the asynchronous processing.

So whenever the control goes for IO, that thread is released and it is free to process other incoming

requests.

So these models allow handling many requests with less overhead by reducing the number of threads and

processes.

So what is the key difference between the traditional and modern web servers?

Traditional servers spawn new thread for each request, leading to inefficiency under high load.

On the contrary, modern servers rely on non-blocking I, o and async models, allowing for better scalability

and efficient resource utilization.

Let's take a look at some common pitfalls that can occur in concurrent systems, mainly race conditions

and deadlocks.

So what is a race condition?

A race condition happens when multiple threads try to access and modify shared data at the same time,

without proper synchronization.

This is bound to happen and this can cause unexpected behavior or even data corruption.

Imagine two threads trying to update the same piece of data at the same time.

One thread might override the other, leading to inconsistencies.

To avoid this, you need to ensure that the code that is accessing the shared resources is properly

logged or synchronized, so that only one thread can modify the data at any given point of time.

Then we have this problem of deadlocks.

A deadlock occurs when two or more threads are stuck waiting for each other to release the resource.

Essentially, they are stuck in a never ending loop of waiting for each other.

This can cause your system to freeze or become unresponsive.

It's like a traffic jam where every car is waiting for other to move first.

To prevent deadlocks, you can use techniques like resource ordering and make sure that the thread requests

the resources in a consistent order, or they use timeout to give a waiting for another thread.

This can help us in avoiding deadlocks.

Now let's dive into some best practices for handling concurrency and parallelism, along with some real

world examples.

So let's start with the best practices first.

Prefer async or non-blocking?

I o for tasks that are IO bound.

This way you can avoid blocking threads, allowing your system to handle more tasks concurrently without

running out of resources.

Second, for CPU bound tasks, consider using thread pool instead of raw threads.

Thread pool reuse threads, reducing the overhead of creating and destroying them constantly, which

help to improve the performance and scalability.

Next, always synchronize access to shared data when you are using threads.

Use locks, mutex or other synchronization mechanism to ensure that only one thread can modify shared

data at a time.

This helps in avoiding race conditions and then to detect and avoid deadlocks.

Always follow strategies like lock ordering, and if multiple threads need to acquire several locks,

make sure they acquire them in a consistent order.

You can also implement timeout strategies so that threads give up after waiting for some time.

Then what are the real world examples?

Well, a web server handling thousands of requests.

Modern web servers like ASP.Net Core or Node.js use a combination of thread pools and asynchronous I

o to handle high traffic efficiently, ensuring that requests can proceed without blocking the server.

Then we can have a lot of background job processing systems using message queues like rabbit, MQ or

Kafka.

And there could be parallel image rendering, where each frame of an image can be rendered on a different

CPU core, making the process faster by performing all these tasks in parallel.

So these are some of the examples of asynchronous processing in the real world.

Now we have some interview questions related to concurrency and parallelism.

And these kind of questions come up frequently in system design and back end engineering interviews,

especially when you are expected to build scalable and high performance system.

We have already covered the core concepts in this lecture, so you should be able to reason through

and answer these confidently.

Also, I have attached a PDF with detailed answers to all these questions.

Be sure to review what we have provided in the PDF.

Now, before we wrap up, let's review the key takeaways from today's lecture.

First and foremost, concurrency is not same as parallelism.

Both are tools for improving performance and scalability, but they work in different ways.

Concurrency is all about managing multiple tasks, while parallelism is all about executing them simultaneously.

Remember, threads are lighter than processes and allow for more efficient task management.

However, they comes with a challenge of needing careful handling, especially when they are working

on the shared resources and data then web servers.

Thread pool and asynchronous models are essential for web servers.

These help servers handle a large number of requests efficiently without blocking or overloading the

system.

Lastly, always be mindful of common pitfalls like race conditions and deadlocks.

These can introduce serious issues if they are not handled properly, but with proper synchronization

and awareness this can be avoided.

This concludes our lecture on concurrency and parallelism covering the essential topics.

What is next?

Next we will dive into database performance optimization technique, where we will discuss how to make

sure our databases are running as efficiently as possible.

So I will see you in the next one.
