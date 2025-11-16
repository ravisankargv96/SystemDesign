So welcome to this lecture on TCP and UDP.

TCP and UDP are two of the most fundamental communication protocols in networking and system design.

If you have ever wondered how data travels across the internet, how messages are reliably delivered,

or why some of your applications work faster than others, then this session is for you.

Today we will break down the core differences between TCP and UDP.

We'll explore their strengths and weaknesses and understand when to use what.

By the end of this lecture, you will have a clear understanding of why some applications prioritize

reliability while others focus on speed.

This knowledge is crucial for designing scalable, efficient, and robust systems.

So whether you are preparing for system design interviews or working on real world distributed applications,

this knowledge is going to help you.

Let's dive into the fascinating world of TCP and UDP.

So what is TCP or Transmission Control protocol?

Let's begin by understanding the Transmission Control Protocol, which is one of the most widely used

protocol for communication over the internet.

And it plays a critical role in ensuring that data is transmitted accurately and in order.

The first thing that we need to know about this is that this is a connection oriented protocol.

This means that before any data is exchanged, a connection must be established between the sender and

the receiver.

Think of it like making a phone call.

You don't start talking unless the other person picks up and acknowledges the connection.

So how TCP does it?

TCP achieves this by using a process called three way handshake.

This ensures that both sides are ready to communicate before data transfer begins.

This setup process makes TCP reliable, but it also adds a bit of overhead, which we will discuss in

some time.

Second, the biggest advantage of TCP is that it ensures reliable and ordered communication.

Every piece of data sent via TCP is checked for errors.

It is acknowledged by the receivers and reassembled in the correct order before being delivered to the

application.

For example, imagine you are downloading a file or watching a video on YouTube.

The data packets might take different routes to reach you, but TCP ensures that they all arrive and

they are pieced together correctly in the correct sequence so that you don't end up with missing or

scrambled content.

If, let's say any packet is lost or corrupted on the way, TCP will automatically request the sender

to resend it.

This ensures that no data is lost or delivered incorrectly.

Because of this reliability, TCP is used in applications where accuracy is critical.

Think of scenarios like online banking, emails, web browsing, or file transfers where even a small

piece of missing or incorrect data could cause major issues.

The trade off here is that TCP is error checking, retransmission, and ordering mechanism at some extra

processing time, which makes it slightly slower than the other protocols like UDP.

But for applications where accuracy matters more than speed, TCP is the perfect choice.

So to summarize, TCP is a connection oriented protocol that ensures reliable, ordered, and error

free communication.

It establishes a secure connection.

It verifies data integrity and guarantees that the information is delivered correctly.

This makes it the backbone of many critical internet applications.

Now let's try to understand what is UDP User Datagram Protocol or UDP.

So we looked at TCP.

And while TCP focuses on reliability UDP is designed for speed and efficiency.

It's a very lightweight protocol that sacrifices some reliability related features to achieve lower

latency.

So first thing to know is that it is a connectionless protocol.

Unlike TCP, UDP is connectionless.

This means that there is no need to establish a connection before sending data.

Imagine you are throwing a bunch of postcards into a mailbox without even waiting for confirmation that

they are getting received or not.

That's how UDP works.

It simply sends data and does not check whether it was successfully delivered or not.

Because UDP does not require a handshake or maintain a session, it significantly reduces the overhead

and speeds up the communication.

But we will see that it comes at the cost of reliability.

So it is faster, but there are no delivery guarantees.

Speed.

The biggest advantage of UDP is speed since it doesn't waste time on error checking, acknowledgment

and retransmissions.

It's much faster than TCP.

This makes it ideal for real time applications like online gaming, live streaming, voice chat, video

call where speed is more important than perfect accuracy.

However, there is a small catch UDP does not guarantee that data will arrive at its destination.

So packets can get lost in the transit packets might arrive out of order or even duplicated when they

are reaching to the destination.

But there are applications that can tolerate minor data loss, or they have their own error handling

mechanism where they can put these packets in sequence.

And that's where UDP is a better choice.

But since UDP doesn't provide delivery guarantees, lost packets are never retransmitted like they get

retransmitted in the TCP.

This means that if a data packet is dropped due to network congestion or any other issue, it is simply

gone forever.

Imagine you are watching a live sport stream.

If one video frame is lost, the stream will keep on going and you wouldn't mind it.

It doesn't wait to retrieve the missing frame because that could cause unnecessary lags in the stream.

The same principle applies to online gaming, VIP calls, and financial market updates.

We are receiving the latest data quickly is more important than getting the last single packet.

So to summarize, UDP is connectionless.

Its high speed protocol that doesn't provide guarantee of delivery is perfect for real time applications

where speed is more critical than perfect accuracy like gaming, video streaming, and voice communication.

But if you need reliable ordered data transmission, TCP is a better option.

Now that we have explained both TCP and UDP individually, let's compare them side by side to understand

their key differences and when to use each protocol.

So first is about reliability.

The biggest difference between TCP and UDP is reliability.

TCP ensures that every packet sent reaches its destination correctly and in order It does through this

acknowledgment and retransmission if the packages are getting locked.

UDP, on the other hand, does not guarantee delivery.

It simply sends packets without checking if they have arrived.

This makes it less reliable, but much faster.

Second is speed because TCP has to establish a connection, confirm deliveries and recent lost packets.

It is slower than UDP.

UDP is much faster since it skips all these extra steps and just fires off data packets.

This is why UDP is often used in time sensitive applications where a bit of data loss is acceptable,

but delays are not acceptable.

Third is connection type.

TCP is a connection oriented protocol.

It means that the connection must be established between the sender and the receiver before data transfer

begins.

UDP, in contrast, is connectionless.

It just sends the data without setting up any session.

This makes it lightweight and ideal for scenarios where maintaining a continuous connection isn't necessary.

So to summarize, TCP prioritizes reliability and accuracy, making it ideal for critical data transfers,

whereas UDP sacrifices reliability for speed, making it perfect for real time applications.

So now that we have covered the differences between TCP and UDP, let's look at some of the real world

applications of these protocols.

Choosing the right one will depend on whether you prioritize data integrity or speed.

So when to use TCP?

TCP is the preferred choice where accuracy and reliability are more important than speed.

If a packet of data is lost or corrupted, DCP ensures it is retransmitted.

This makes it perfect for applications where every bit of data must arrive correctly.

So web browsing the protocols like HTTP and Https are written on top of TCP.

File transfer protocols like FTP and SftP are on top of TCP.

Email communication SMTP, iMap, Pop3.

All these protocols are using TCP.

Underlying.

Then UDP UDP is a better choice when speed is more important than reliability.

A few lost packets won't matter as much if the real time responsiveness is maintained for the application.

Best use cases are video streaming like YouTube and Netflix uses this.

Online gaming.

Many of the online games like Fortnite, Call of Duty, PUBG are using it.

VoIP calls, WhatsApp calls, Skype calls, all of them are using it.

In fact, DNS lookup also uses UDP underline because when a website wants to resolve IP for a given

domain name, it wants the response to be quick rather than late.

So to summarize, when accuracy matters, TCP is used and use UDP when speed is priority.

Ultimately, all comes down to the trade off between reliability and speed.

If you need guaranteed delivery and data integrity, TCP is the way to go.

But if you need low latency and real time performance, UDP is a better choice.

Understanding this trade off is very essential for system design, as choosing the right protocol can

make or break the performance of your application.

Now that we have covered the fundamentals of TCP and UDP, let us look at some of the interview questions.

So I have listed down some of the basic interview questions here.

And so far whatever we have covered, I think you should be able to answer these questions easily.

But in case you want to refer to the answers, we have already attached a detailed PDF with the answers

in the resources section.

Make sure to review it.

Make sure to prepare for the interview questions related to TCP and UDP, as these topics thoroughly

can make a big difference in your next system design interview.

So before we wrap up, let's quickly look at the key takeaways that we have taken from this lecture.

First, TCP is reliable but slower, ensuring error free order delivery.

It is perfect for web browsing, file transfer emails anywhere where the data integrity matters.

On the contrary, UDP is faster but unreliable, making it ideal for real time applications like video

streaming, online gaming, and VoIP calls wherever speed is more important than perfect accuracy.

Choose UDP.

Choosing between TCP and UDP in system design is all about trade off.

Trade off between speed and reliability.

The correct user experience will depend on which protocol you use for your application.

So what's next?

Now that we have covered the fundamentals of TCP and UDP, let's move on to the next protocol HTTP,

which is the backbone of the web.

So in the next lecture we will explore how the web communicates using HTTP and how HTTP powers the modern

applications.

So I will see you in the next one.