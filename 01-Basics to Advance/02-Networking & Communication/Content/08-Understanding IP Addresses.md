Imagine trying to send a letter without an address, the Postal Service wouldn't know where to deliver

it and your letter would never reach its destination.

The same principle applies to the internet.

Every device needs an address to send and receive data.

This is where IP addresses come in picture.

Hello and welcome to this session on understanding IP addresses in System Design.

In this lecture, we will break down one of the most fundamental networking concepts how IP addresses

work.

The difference between IP version four and IP version six, and the role of private and public IPS in

system architecture.

Why does it matter to understand about IP addresses?

Well, whether we are designing a distributed system, working with cloud infrastructure, or preparing

for system design interviews, understanding IP addressing is essential.

Every online service, be it Netflix, Amazon or even a simple website relies on a well structured IP

management system to ensure seamless communication and scalability.

So let's get started by first understanding what an IP address is and why it is so important in networking.

So every time you open a website, sends an email or stream a video, your device is communicating with

other machines across the internet.

But how does it know where to send this request?

The answer lies in IP address.

So what is an IP address?

An IP address or Internet protocol address is a unique identifier assigned to every device connected

to the internet.

Just like your home is an address, your mail carriers find you using that home address.

Your computer also has an IP address, which allow computers, servers, and other devices to locate

and communicate with each other when they are connected to the internet.

Why are IP addresses important?

Without IP addresses, there would be no way to send or receive data online.

They are the foundation of all networking.

They enable devices to exchange information seamlessly.

There are primarily two versions of IP addresses IP version four and IP version six, and they can be

classified as public IP and private IP.

We will understand all of them very in our coming lectures in very detail.

But just for this slide, let's look at this diagram.

Here is a simple diagram of a network.

Each device in the network here as an IP address, be it a computer be it a printer, be it a server,

or if there are smartphones also connected in this network, every device in this network will have

an IP address, and this allows data to flow correctly between different systems, ensuring seamless

communication.

So now that we understand what an IP address is and why it matters to have a unique address in the form

of IP address, let's explore IP version four, the most commonly used IP version and its structure.

So what is IP version four?

IP version four or Internet Protocol version four is the most commonly used version of IP addressing,

and it was actually created decades ago when people were actually designing a solution for giving addresses

to every computer on the network.

It uses a 32 bit addressing scheme, which means that it can support approximately 4.3 billion unique

addresses.

Now, when the internet was first designed, no one expected the number of connected devices to explode

at it has today.

So the original IP addressing scheme, the IP version four so far has been the backbone of internet

and it has been for decades.

But now, since it's there is a limitation of only supporting 4.3 billion unique addresses.

It is actually falling short.

Don't get me wrong, despite its all limitations, IPV four is still widely used because it is deeply

embedded in the networking infrastructure, cloud services and corporate networks.

However, due to the rapid growth of the internet, IP version four addresses are running out and which

led to the development of IP version six.

Just to give you an idea of the overall structure of an IP address, the IP version four address is

typically written in a dotted decimal format.

It consists of four groups of numbers separated by dots, and each group can have number ranging from

0 to 255.

And these are actually called octets.

And every octet has a specific responsibility like the first one.

Represent the class of the network.

The second one and the third one represent what subnet it belongs to, and the fourth one represent

what actual device is on the network that it is identifying.

But yes, the format of the IP version four is this.

And IP version four can support up to 4.3 billion unique devices.

Now that we know what is IP version four, let's explore its successor IP version six and try to understand

how it solves the address shortage problem of IP version four.

Now, in today's context, imagine trying to fit the entire internet into just 4.3 billion addresses.

It sounds impossible, right?

Well, that's exactly the challenge IPv4 faced as the internet expanded.

And to solve this, we introduced IP version six, IP version six, or Internet Protocol.

Version six is the next generation IP addressing system, which is designed to replace the IP version

four.

It uses a 128 bit address instead of a 32 bit address, which allows for an almost infinite number of

unique addresses.

Three.

40 Undecillion to be exact.

That is 340 trillion.

Trillion.

Trillion.

Three times trillion.

So it is actually infinite.

If you look at it, and unlike IP version four, which is written in dotted decimal format, IP version

six addresses use hexadecimal notations which are separated by colons, as you can see here in the diagram.

Each IP version six consists of eight groups of four hexadecimal digits, making it much, much longer

than the IP version four.

And this format provides enough addresses for every device on this Earth to have a unique address.

And IP version six isn't just about more addresses, it is also bringing some key improvements in the

IP addressing scheme.

Improvements like there is better performance and security, there is a simplified network management,

and there is also faster data processing because there is more efficient routing and packet handling

that is happening.

And with the growth of cloud computing devices, IoT devices and global internet expansion, IP version

six adoption is actually increasing very, very rapidly.

If you look at this diagram, you can actually look at how IP version six is different from IP version

four.

It shows IP version six larger address space, which eliminates the need for address translations from

private addresses to public IP addresses.

We'll come to that in the next section.

But right now understand that IP version six actually removes the limitation of IP version four, that

it can only support 4.3 billion devices, and IP version six supports 340 trillion, trillion trillion

devices.

Now that we understand IP version four and IP version six, to understand what is network address translation,

let's look at another critical concept the public IPS and private IPS.

And we try to understand what is their role in the system design.

Now let's try to look at the private IPS versus public IPS.

So to do that, think of the entire internet as a big city, your home as a street address and identifies

it to the world that is like the public IP address, but inside your home, your device has their own

local addresses, like apartment numbers.

That is sort of like private IP addresses.

So a public IP address is assigned to a device by an internet service provider that is globally unique,

and it allows the devices to communicate directly over the internet.

The example includes the IP addresses assigned to websites, cloud servers, and the router that is

actually in your home or in any business, whatever router that is actually connected facing the internet.

On the contrary, the private IP address is used within a local network and it is not accessible from

the internet.

These addresses have devices inside a local network, inside the same network to identify each other,

like in your home network.

You might have laptops, smart TVs, phones for all these devices to communicate with each other.

All of them will get a private IP addresses.

Now, you'll often see these private IP addresses in homes and office networks because private IPS are

reusable and they don't require global registration.

What I mean by that is that if I have a home, I can have a private IP address like 192.168.6.1, something

like this.

And my public IP address could still be this.

Now there could be another home where the public IP address will be different.

It could be 1922, zero three, 23 and 46.

But inside that home they could reuse the private IP address.

It could still use the same private IP address.

Now, understanding this difference between private IPS and public IPS is very crucial for designing

the scalable and secure systems.

Why?

First reason is security.

Private IPS actually isolate the internal system from external threats.

So even if anyone gets hold of your private IP address, since this device is not accessible from outside,

they will not be able to access this device just by knowing their private IP address.

Second is scalability.

It allows organizations to use many, many, many internal addresses without needing the public IP addresses.

And the third is network management.

It helps to manage the cloud networks, virtual private networks and enterprise systems much more efficiently.

Now look at this diagram.

This diagram shows a typical network the devices inside a home which are on the left side.

They use all private IP addresses to communicate with each other, and whenever they want to communicate

to the outside world, they give the private IP addresses as the referrer to the outside world.

While the router itself has a public IP address that is provided by your internet service provider.

So that is the crux of private IP addresses and public IP addresses.

Now that we understand the private and public IP addresses, let's explore how these address types play

an important role in the real world system design.

So imagine if every device in your home, your phone, your laptop, your smart TV, and even your smart

fridge needed a unique, globally accessible IP address meaning public IP address.

Now, with billions of devices that we have worldwide right now, we would run out of IP addresses almost

instantly like that.

This is why we need private IP addresses.

So there are four main reasons for having private IP addresses.

The first one is address conservation.

IP version four has a limited number of addresses, and using private IPS, allow organizations and

homes to reuse the same IP ranges without exhausting the global address pool.

The second one is enhanced security.

Private IP addresses are not directly reachable from the internet, making them much more secure.

This prevents direct external attacks on devices that are inside our network.

Next, efficient network management.

Businesses and homes can assign private IP addresses to multiple devices and manage their internal networks

efficiently without sending a separate public IP for each device.

And this is much more cost effective.

Also, using the private IP reduces the need to purchase multiple public IP addresses, which sometimes

can be very expensive, especially when it comes to large enterprises.

So how private IP is working?

System design.

Private IPS are used inside corporate networks, cloud infrastructures, and data centers.

And they ensure smooth communication between internal services while limiting exposure to the public

internet.

If you look at this diagram, this shows a typical home network where multiple devices which are inside

the home.

If you look at here, they use private IPS, while a single public IP is assigned to the router for

all the external communication needs.

Now this slide shows a little bit.

Double click detailed version of how IP addresses are important in system design.

First, it helps in scalability because we can use any number of private IP addresses within a region

or within a private network.

When we are actually hosting our applications on a cloud platform or on our on premises server.

So it is actually easier to scale.

It is also much more secure because we can enable firewall rules, create virtual private networks,

and we can have private networks within our hosting infrastructure to have better security.

Also it helps in load balancing.

So if we have IP addresses for this, these private IP addresses for three instances of our application,

the load balancer can actually efficiently do load balancing within the network using all the private

IP addresses.

So in cloud, the use of private IP addresses is actually much, much exhaustive.

And we will learn how we can design the system architectures that are leveraging the private IPS when

we're designing the large scale systems.

So now we understand a little bit about the important role of IP addresses in system design.

Now, before we move on to the next topic of domain name servers, let's try to look at some of the

common system design interview questions on IP addresses.

If you go through these questions knowing what we have seen so far in this section, you will be able

to answer these questions.

If you are interested in much more detailed answers to these questions.

I will provide a document with all the answers to these questions in the resources section of this lecture.

Mastering these questions will help you think like a system architect.

The key is not just memorizing these answers, but understanding the real world implications of IP addressing

in system design.

Now we have covered a lot about IP addresses, and by now you should have a solid understanding of how

they work in system design.

Let's quickly summarize the key takeaways.

Key takeaway number one IP version four and IP version six are two primary internet address protocols.

While IPv4 is still widely used, IPv6 was introduced to overcome its limitations, and it offers a

much larger address space.

It has built in security and it is much more efficient.

Second takeaway is that we looked at the difference between the private and public IP addresses, and

both of them play a very crucial role in managing internal and external networking.

Private IP's keep the internal network secure and reduce the need for large number of public IPS.

While the public IPS allow internet facing services to be accessible globally from the internet, the

third takeaway is that in a large scale system design, networking and IP management are essential for

ensuring scalability, security and performance.

Whether it is a load balancing, cloud, networking or microservices communication, IP addresses are

the foundation of modern distributed systems.

So now that we understand how IP addresses work, the next big question is how do we map human readable

domain names to these IP addresses?

And that's where DNS comes in.

In the next lecture we will explore how DNS works, why it is critical in system design, and how large

scale systems efficiently resolve domain names.

So I will see you in the next one.