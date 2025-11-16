## Chapters
* 00:00 - Traffic Estimation
* 02:26 - Scaling Strategy
* 04:57 - Sale Day!
* 07:16 - Finding the Root Cause
* 08:27 - DDOS Prevention
* 15:32 - Head of Line Blocking
* 18:18 - Another Sale!
* 19:08 - Rate Limiting

## Transcript
00:00:00.065 --> 00:00:01.045 Now a few months have passed.
00:00:01.185 --> 00:00:03.565 The founder is very happy with how the system performs.
00:00:03.735 --> 00:00:05.925 Fancy t-shirts IO starts getting very popular
00:00:06.185 --> 00:00:09.085 and they decide to host their first flash sale.
00:00:09.245 --> 00:00:11.445 A flash sale is something where the T-shirts
00:00:11.445 --> 00:00:13.565 that fancy t-shirts io sells is going
00:00:13.565 --> 00:00:15.565 to be available at 50% discount
00:00:15.705 --> 00:00:17.685 for just two hours on a particular day.
00:00:17.685 --> 00:00:21.165 This is a big deal because everyone is expected to come
00:00:21.165 --> 00:00:22.205 during those two hours.
00:00:22.205 --> 00:00:24.365 Quickly browse through the T-shirts that are available
00:00:24.625 --> 00:00:25.845 and buy the t-shirts.
00:00:25.995 --> 00:00:29.045 Okay, so you will be having a lot of visits to the page,
00:00:29.055 --> 00:00:31.285 maybe a lot of registrations also, certainly,
00:00:31.285 --> 00:00:32.445 hopefully a lot of orders
00:00:32.825 --> 00:00:35.725 and maybe a lot of status checks also happening at the same
00:00:35.725 --> 00:00:38.325 time for making sure that this sale goes smoothly,
00:00:38.625 --> 00:00:40.805 the founder comes to you and asks you for advice.
00:00:40.955 --> 00:00:42.205 What kind of advice should you give?
00:00:42.345 --> 00:00:44.565 The first thing you want to do is understand
00:00:44.715 --> 00:00:46.445 what is the scale that we are talking about.
00:00:46.465 --> 00:00:48.085 We are saying yes, there'll be a lot of users,
00:00:48.345 --> 00:00:50.285 but how much exactly is a lot?
00:00:50.385 --> 00:00:52.005 So you talk to the founder and they tell you
00:00:52.005 --> 00:00:54.645 that our social media page has around 20,000 followers.
00:00:54.825 --> 00:00:57.405 We also have the emails of roughly 50,000 users
00:00:57.625 --> 00:00:59.725 and we also run Google ads, which get
00:00:59.725 --> 00:01:01.005 around 1 million impressions.
00:01:01.075 --> 00:01:02.645 This is all product information.
00:01:02.905 --> 00:01:05.125 So you ask them, okay, what's the daily sale like?
00:01:05.145 --> 00:01:07.685 And they say, well, we get around 2000 sales a day,
00:01:07.685 --> 00:01:08.845 and you tell them how much are you
00:01:08.845 --> 00:01:10.205 expecting to happen in these two hours?
00:01:10.305 --> 00:01:11.565 So they say, we don't really know.
00:01:11.565 --> 00:01:14.045 It could be anything You ask them, what about nx?
00:01:14.045 --> 00:01:15.565 The number of sales that you have per day?
00:01:15.585 --> 00:01:18.445 2000 becomes 20,000 in these two hours. Is that possible?
00:01:18.465 --> 00:01:20.405 And they tell you yes, it very much is possible.
00:01:20.405 --> 00:01:22.925 Then you tell them that is more than 10 x possible
00:01:22.925 --> 00:01:24.125 is a hundred x possible.
00:01:24.125 --> 00:01:26.765 And they say, maybe not a hundred x is maybe too much.
00:01:26.865 --> 00:01:29.925 10 x is probably the amount that we are expecting.
00:01:29.925 --> 00:01:31.405 So as an engineer, what should you do?
00:01:31.425 --> 00:01:33.405 Should you get 10 x the capacity
00:01:33.405 --> 00:01:35.765 that you have right now preemptively so that they,
00:01:35.765 --> 00:01:38.045 when the users come, they have a smooth experience
00:01:38.145 --> 00:01:39.405 or should you increase the capacity
00:01:39.405 --> 00:01:41.285 but to a lesser extent so that the cost
00:01:41.385 --> 00:01:42.805 of increasing capacity is low.
00:01:42.805 --> 00:01:45.165 While you are also making sure that when new users come,
00:01:45.165 --> 00:01:48.125 their experience is okay, so maybe you increase capacity
00:01:48.125 --> 00:01:49.725 by five x or three x.
00:01:49.915 --> 00:01:52.525 This is also a business decision
00:01:52.525 --> 00:01:56.485 because the cost of increased capacity can be maybe offset
00:01:56.485 --> 00:01:57.645 by the number of sales you're making,
00:01:57.745 --> 00:01:59.405 but it's best to talk to the founder
00:01:59.585 --> 00:02:01.765 and get to know how much is the profit margin,
00:02:01.905 --> 00:02:04.205 how much are they okay with the customers having a slightly
00:02:04.225 --> 00:02:07.005 poorer experience once the capacity is exceeded
00:02:07.145 --> 00:02:08.365 and in how much time do they
00:02:08.365 --> 00:02:09.645 expect all these customers to come?
00:02:09.715 --> 00:02:12.445 Just remember, in reality when it comes to startups
00:02:12.445 --> 00:02:14.765 or even medium sized companies, it's very, very hard
00:02:14.765 --> 00:02:15.885 to predict the number of
00:02:16.045 --> 00:02:17.205 customers will be coming for an event.
00:02:17.305 --> 00:02:19.205 And even large companies make mistakes here.
00:02:19.205 --> 00:02:21.525 Even large companies have servers which are not able
00:02:21.525 --> 00:02:22.845 to take the request load.
00:02:22.865 --> 00:02:24.965 You may have failures With that happy note, let's start
00:02:24.965 --> 00:02:27.325 with some of the remedies that we have around this.
00:02:27.505 --> 00:02:29.845 The first thing that we discussed is very obvious.
00:02:30.105 --> 00:02:32.965 You preemptively scale. So maybe you have 10 servers.
00:02:33.185 --> 00:02:36.085 You see that you're expecting 10 x capacity one day
00:02:36.085 --> 00:02:38.205 before the sale or five hours before the sale.
00:02:38.265 --> 00:02:40.285 You ramp up your capacity to 10 x
00:02:40.425 --> 00:02:42.165 or even three x during the sale.
00:02:42.165 --> 00:02:45.445 You monitor key metrics like request latency, like amount
00:02:45.445 --> 00:02:46.765 of memory being used in the server,
00:02:46.945 --> 00:02:50.445 and if request latency is starting to increase steadily,
00:02:50.545 --> 00:02:52.485 you start adding more and more capacity so
00:02:52.485 --> 00:02:54.805 that the request can be served parallelly
00:02:54.825 --> 00:02:56.085 and you get responses quickly.
00:02:56.225 --> 00:02:58.885 The second thing you want to do is look at the access
00:02:59.045 --> 00:03:00.525 patterns of this system.
00:03:00.665 --> 00:03:03.645 Access patterns basically means the patterns in which data
00:03:03.785 --> 00:03:04.925 is accessed in your system.
00:03:04.925 --> 00:03:06.605 When it comes to fancy t-shirts dot io,
00:03:06.625 --> 00:03:09.565 you are looking at the way a user is
00:03:09.635 --> 00:03:11.245 accessing T-shirt information.
00:03:11.545 --> 00:03:14.125 The way a user is making payments the way they are looking
00:03:14.125 --> 00:03:16.965 at statuses and maybe even connecting customer support.
00:03:17.035 --> 00:03:19.125 Look at each of these requests individually.
00:03:19.155 --> 00:03:20.205 What is the request path?
00:03:20.205 --> 00:03:23.565 Like taking the example of looking at T-shirts, the T-shirts
00:03:23.565 --> 00:03:24.645 that will be available for sale.
00:03:24.745 --> 00:03:27.445 You see that the T-shirts are common across users.
00:03:27.705 --> 00:03:30.405 You don't want to be storing this information in the
00:03:30.565 --> 00:03:31.605 database, which will be
00:03:31.615 --> 00:03:33.285 increasing the latency of the request.
00:03:33.345 --> 00:03:34.965 You probably want to cache this information
00:03:35.185 --> 00:03:36.725 so you cache the information on the server.
00:03:36.725 --> 00:03:39.125 Another thing you can do is cache this information
00:03:39.125 --> 00:03:40.245 on the content delivery network.
00:03:40.415 --> 00:03:42.245 Since the content delivery network is much closer
00:03:42.245 --> 00:03:44.485 to the user, it's a distributed set of servers globally.
00:03:44.745 --> 00:03:48.085 If a user is looking for the T-shirts which are available
00:03:48.085 --> 00:03:49.845 during this sale, the content delivery
00:03:49.845 --> 00:03:51.245 network can have that information.
00:03:51.275 --> 00:03:52.285 This is going
00:03:52.285 --> 00:03:54.085 to be updated very rarely in fact you
00:03:54.085 --> 00:03:55.445 don't see an update happening.
00:03:55.505 --> 00:03:57.325 So that information can be populated
00:03:57.465 --> 00:03:58.845 and when a user says,
00:03:59.225 --> 00:04:01.565 get me all the T-shirts which are available in this sale,
00:04:01.745 --> 00:04:05.165 you give them all the T-shirt Iris from the CDN itself.
00:04:05.265 --> 00:04:07.885 So the CDN doesn't just store purely static content.
00:04:08.065 --> 00:04:10.005 It can store web pages, it can store images,
00:04:10.145 --> 00:04:13.005 it can store videos, it can also store information.
00:04:13.265 --> 00:04:15.525 Any kind of information can be stored in A CDN
00:04:15.545 --> 00:04:18.085 and as long as the browser is smart enough to be able
00:04:18.085 --> 00:04:19.165 to pass that information.
00:04:19.185 --> 00:04:20.725 So your UI should be able
00:04:20.725 --> 00:04:22.045 to render that information quickly.
00:04:22.145 --> 00:04:24.365 You know these t-shirts are available. These are the IDs.
00:04:24.425 --> 00:04:27.005 Let me go and fetch each of those IDs. Thumbnails.
00:04:27.025 --> 00:04:29.325 You should be fine. So our basic idea has three steps.
00:04:29.575 --> 00:04:32.445 First, estimate the number of requests
00:04:32.465 --> 00:04:34.565 or the number of users who will be using your system
00:04:34.625 --> 00:04:35.965 during this flash sale.
00:04:35.985 --> 00:04:39.085 Second, preemptively scale the servers that you have so
00:04:39.085 --> 00:04:40.485 that you can serve the requests quickly.
00:04:40.705 --> 00:04:44.125 And third, look at the access patterns of the users
00:04:44.345 --> 00:04:46.765 of these requests to cache effectively
00:04:46.905 --> 00:04:49.005 and maybe even optimize piece of code
00:04:49.195 --> 00:04:50.765 that are coming in this critical path.
00:04:50.795 --> 00:04:53.525 This is something you should absolutely do if you have any
00:04:53.525 --> 00:04:56.005 kind of event coming up where you see the number
00:04:56.005 --> 00:04:57.365 of requests will have a spike.
00:04:57.465 --> 00:04:59.725 So now your founder friend is quite happy, they go back
00:04:59.725 --> 00:05:01.565 to the engineers, they tell them that we are going
00:05:01.565 --> 00:05:02.765 to preemptively scale the system.
00:05:03.025 --> 00:05:05.845 We are also going to be caching all the critical data in the
00:05:06.045 --> 00:05:07.845 critical paths and maybe we are also going
00:05:07.845 --> 00:05:09.165 to be doing something called load testing
00:05:09.335 --> 00:05:12.045 where we hit our server with a bunch of requests
00:05:12.185 --> 00:05:14.325 and we see how many responses successfully come
00:05:14.325 --> 00:05:15.925 through in the required latency.
00:05:16.065 --> 00:05:18.925 If latency is exceeded for the requests, then we believe
00:05:18.925 --> 00:05:21.045 that the server is not performing up to the mark,
00:05:21.145 --> 00:05:22.165 we will need to scale up.
00:05:22.225 --> 00:05:24.645 An example of this would be you send 10,000 requests
00:05:24.645 --> 00:05:26.085 to the server, the server responds
00:05:26.085 --> 00:05:27.885 with an average latency of one millisecond.
00:05:27.935 --> 00:05:29.725 Since you allow a hundred milliseconds
00:05:29.785 --> 00:05:31.645 as average latency, this is totally fine.
00:05:31.705 --> 00:05:34.365 Now you scale up the requests to one lack requests.
00:05:34.545 --> 00:05:37.885 The same server is now taking one second to answer requests.
00:05:38.025 --> 00:05:39.445 So one lack is way too high.
00:05:39.465 --> 00:05:41.005 You probably need to come somewhere in between.
00:05:41.005 --> 00:05:43.445 You come to 20,000 requests, the server is able to respond
00:05:43.445 --> 00:05:45.965 to those in a hundred milliseconds average time at this
00:05:46.045 --> 00:05:48.125 point, you're quite happy and you say one server
00:05:48.185 --> 00:05:50.525 of mine can manage 20,000 requests
00:05:50.715 --> 00:05:52.285 with the acceptable latency.
00:05:52.345 --> 00:05:54.885 So tomorrow, if I have to serve 40,000 requests,
00:05:55.075 --> 00:05:57.005 then I need two servers in this way.
00:05:57.155 --> 00:06:00.845 When you test your system by progressively scaling the load,
00:06:00.845 --> 00:06:03.485 you're able to see how many requests can one server serve.
00:06:03.545 --> 00:06:06.405 So when the situation arises, you can scale up as required.
00:06:06.465 --> 00:06:08.005 Now the day of the flash sale is here.
00:06:08.225 --> 00:06:09.445 The founder is very excited.
00:06:09.515 --> 00:06:11.045 They have invited you to their home
00:06:11.105 --> 00:06:12.805 and you know you're looking at all the metrics,
00:06:12.805 --> 00:06:14.485 you're looking at all the graphs hoping
00:06:14.485 --> 00:06:16.565 that this flash sale goes successfully.
00:06:16.665 --> 00:06:19.765 The sale starts and you see a massive spike
00:06:19.825 --> 00:06:22.085 of users come in completely unnatural.
00:06:22.545 --> 00:06:24.125 You see that the number of users
00:06:24.225 --> 00:06:26.565 who are concurrently accessing your system is like
00:06:26.625 --> 00:06:27.765 1 million users.
00:06:27.985 --> 00:06:29.565 That's crazy. 1 million requests.
00:06:29.705 --> 00:06:32.045 You had 2000 sales earlier, now you have hundreds
00:06:32.045 --> 00:06:33.845 of thousands of users who are creating orders.
00:06:34.065 --> 00:06:35.645 That's crazy. You didn't expect this.
00:06:35.665 --> 00:06:37.645 You didn't expect more than 10 x load.
00:06:37.785 --> 00:06:39.685 And so your system collapses.
00:06:39.775 --> 00:06:42.045 There is way too much load on the servers.
00:06:42.045 --> 00:06:44.845 They're taking a very long time to respond to requests.
00:06:44.845 --> 00:06:46.965 Their request queues are getting longer and longer
00:06:47.225 --> 00:06:48.765 and users are getting more and more upset.
00:06:48.835 --> 00:06:51.165 They're retrying, they're refreshing the page.
00:06:51.485 --> 00:06:54.445 Everyone is unhappy. The flash sale is a complete disaster.
00:06:54.665 --> 00:06:56.965 That's not good. Your friend is disappointed.
00:06:57.035 --> 00:06:59.005 They are connecting with the customer success teams
00:06:59.345 --> 00:07:01.765 to call people up, tell them that, hey, you know,
00:07:01.765 --> 00:07:04.165 even though the flash sale is over, maybe we can give you
00:07:04.165 --> 00:07:06.005 that T-shirt outside the sale time
00:07:06.005 --> 00:07:07.685 because you weren't able to make that request.
00:07:08.025 --> 00:07:09.965 And so they're digging through the logs, digging
00:07:09.965 --> 00:07:12.125 through the payment systems, trying to find
00:07:12.455 --> 00:07:15.325 where things went wrong and how they can fix it quickly.
00:07:15.465 --> 00:07:17.405 But you as an engineer are going to be connecting
00:07:17.405 --> 00:07:20.325 with the tech team after this firefighting phase is over.
00:07:20.385 --> 00:07:21.365 And then you're going to ask them
00:07:21.365 --> 00:07:22.325 some interesting questions.
00:07:22.425 --> 00:07:24.685 The first question is, you had a few million users,
00:07:24.915 --> 00:07:27.445 were they all real users or were they bots?
00:07:27.595 --> 00:07:30.165 It's hard to say for an engineer, it's difficult
00:07:30.185 --> 00:07:31.525 to look at a request
00:07:31.745 --> 00:07:35.045 and then say, this is correct, this is real or this is fake.
00:07:35.185 --> 00:07:36.765 But the engineers dig through the logs
00:07:36.765 --> 00:07:40.565 and they see that the same users made thousands of requests
00:07:40.715 --> 00:07:42.765 with the same user ID People made thousands
00:07:42.765 --> 00:07:44.125 of requests in seconds.
00:07:44.265 --> 00:07:45.845 That's crazy. Okay, that's, that's not natural.
00:07:46.025 --> 00:07:47.045 No human can do this.
00:07:47.465 --> 00:07:49.685 It is probably a script which has been written
00:07:49.745 --> 00:07:51.165 to take down your service, okay,
00:07:51.165 --> 00:07:52.885 to cause a denial of service.
00:07:53.185 --> 00:07:55.285 And since you see multiple IP addresses
00:07:55.285 --> 00:07:57.565 and multiple users who have sent these requests,
00:07:57.705 --> 00:07:59.605 you can call it a distributed denial
00:07:59.625 --> 00:08:01.325 of service attack on your system.
00:08:01.425 --> 00:08:02.685 Who would do this? Could be anybody.
00:08:02.695 --> 00:08:05.565 Maybe a competitor who doesn't like fancy t-shirts io.
00:08:05.565 --> 00:08:07.445 It could be someone who thinks that this is a joke.
00:08:07.455 --> 00:08:10.165 Maybe non maliciously, someone was just testing your server,
00:08:10.165 --> 00:08:12.045 wrote some code and just blasted it.
00:08:12.185 --> 00:08:14.845 But at the end of the day, as an engineer, you will have
00:08:14.845 --> 00:08:16.685 to protect your system from such actors.
00:08:16.905 --> 00:08:18.765 So what can you do? Well, the sale is a loss
00:08:18.945 --> 00:08:20.005 and the founder decides
00:08:20.005 --> 00:08:22.765 that since this has been such a disaster, we are going
00:08:22.765 --> 00:08:24.365 to have the same flash sale in a week.
00:08:24.505 --> 00:08:25.925 So in a week we'll make our system
00:08:25.985 --> 00:08:27.285 robust and we'll try again.
00:08:27.285 --> 00:08:28.845 So that's the second chance. What you do,
00:08:28.865 --> 00:08:31.565 the first thing you want to do is you want to stop bots
00:08:31.785 --> 00:08:34.245 or bad actors from taking down your system.
00:08:34.385 --> 00:08:36.605 For this, you are looking for something like a firewall,
00:08:36.795 --> 00:08:38.605 some sort of gatekeeper, which makes sure
00:08:38.605 --> 00:08:40.565 that the requests which are coming into the system are real.
00:08:40.565 --> 00:08:42.885 Requests are not malicious, are not there
00:08:43.065 --> 00:08:45.885 to take down your server, but actually need to be processed.
00:08:46.065 --> 00:08:48.285 So cloud solution providers do give you this content.
00:08:48.525 --> 00:08:49.765 Delivery networks also give you this.
00:08:49.785 --> 00:08:50.925 If you look at CloudFlare
00:08:50.925 --> 00:08:52.165 or you look at AWS,
00:08:52.165 --> 00:08:55.085 there are specific technologies which will stop users from
00:08:55.205 --> 00:08:57.165 sending an obscene number of requests to your system.
00:08:57.235 --> 00:09:00.045 When it comes to CloudFlare, you can actually write code
00:09:00.185 --> 00:09:02.805 to check the request parameters, the headers,
00:09:02.985 --> 00:09:04.765 and accept or reject the request.
00:09:05.005 --> 00:09:06.605 AWS also provides something similar.
00:09:06.785 --> 00:09:10.205 Uh, the technology is called web application firewall, WAF.
00:09:10.315 --> 00:09:12.045 This works in two phases.
00:09:12.425 --> 00:09:13.925 One is when a person is trying
00:09:13.925 --> 00:09:16.405 to fetch your web page from the content delivery network.
00:09:16.515 --> 00:09:20.325 Your CDN delivery network can have checks to make sure
00:09:20.325 --> 00:09:23.045 that bots are not able to bombard the service.
00:09:23.115 --> 00:09:25.165 Genuine users will be able to fetch the page,
00:09:25.225 --> 00:09:27.165 but bots will be blocked from accessing the page
00:09:27.185 --> 00:09:28.645 and basically eating into your bandwidth.
00:09:28.705 --> 00:09:30.445 The second part is a very similar solution.
00:09:30.445 --> 00:09:32.405 On the server side, you have some sort
00:09:32.405 --> 00:09:33.765 of a gateway which makes sure
00:09:33.765 --> 00:09:36.845 that every incoming request is looked into by the gateway.
00:09:37.105 --> 00:09:39.325 It does increase latency a little bit
00:09:39.545 --> 00:09:41.725 and you know this service uh, has a charge.
00:09:41.725 --> 00:09:43.885 There is a premium that the cloud solution provider will
00:09:43.885 --> 00:09:45.885 take from you, but the premium is very, very less.
00:09:46.185 --> 00:09:49.245 And if you have a genuine concern of DDoS attack,
00:09:49.245 --> 00:09:51.285 it's better to have some sort
00:09:51.285 --> 00:09:53.685 of a firewall blocking, malicious requests.
00:09:53.825 --> 00:09:55.405 The second thing you want to do is
00:09:55.405 --> 00:09:56.765 gracefully degrade the system.
00:09:57.025 --> 00:09:59.645 If you have too many requests to process, for example,
00:09:59.785 --> 00:10:01.205 you may have one user who wants
00:10:01.205 --> 00:10:03.085 to see the T-shirts that they saw recently.
00:10:03.185 --> 00:10:04.845 You may have another user who wants
00:10:04.845 --> 00:10:06.205 to see the status of an order.
00:10:06.205 --> 00:10:07.325 What do you think is more important?
00:10:07.465 --> 00:10:10.045 The status of an order, right? This order has been placed.
00:10:10.185 --> 00:10:12.165 If you want to see the T-shirts you have seen earlier,
00:10:12.465 --> 00:10:13.685 in case the request fails,
00:10:13.905 --> 00:10:15.205 it doesn't really irritate too much.
00:10:15.425 --> 00:10:17.605 You might say, request failed, please try again.
00:10:17.625 --> 00:10:19.525 Or you, you might just take them to the default tab.
00:10:19.525 --> 00:10:21.085 So you might show them the wrong T-shirts.
00:10:21.085 --> 00:10:23.045 Also just show them the popular t-shirts that they have seen
00:10:23.065 --> 00:10:24.525 or you could give them a message about that.
00:10:24.545 --> 00:10:26.485 You know, right now we are having too much server load.
00:10:26.485 --> 00:10:29.245 This didn't go through. So given a choice, you choose
00:10:29.385 --> 00:10:32.805 to serve the more important requests and choose to ignore
00:10:32.945 --> 00:10:35.405 or deprioritize the less important requests.
00:10:35.675 --> 00:10:37.765 This is called request priority.
00:10:37.905 --> 00:10:40.045 The higher priority requests are served
00:10:40.145 --> 00:10:42.765 and the lower priority requests if needed, are rejected.
00:10:42.865 --> 00:10:44.005 And the overall strategy
00:10:44.025 --> 00:10:46.485 or idea is called graceful degradation.
00:10:46.485 --> 00:10:48.365 Another example of this would be WhatsApp.
00:10:48.395 --> 00:10:51.885 When you are sending a Happy New Year text on New Year's
00:10:51.885 --> 00:10:54.245 Eve, it's important, it's nice to know it's, it's good
00:10:54.245 --> 00:10:55.765 to have the read receipts
00:10:55.985 --> 00:10:58.205 or the delivery receipts are not very important.
00:10:58.205 --> 00:11:00.525 Delivering the message to the device is more important.
00:11:00.625 --> 00:11:04.125 So WhatsApp, when it has a bunch of messages that it has
00:11:04.125 --> 00:11:06.845 to send, it's going to look at delivery and read receipts
00:11:06.865 --> 00:11:08.405 and probably ignore them or put them
00:11:08.405 --> 00:11:09.485 in the backlog of the queue.
00:11:09.545 --> 00:11:11.045 But then there is a sent message,
00:11:11.245 --> 00:11:12.565 a new message that has to be sent.
00:11:12.575 --> 00:11:14.125 Those will be processed first and
00:11:14.125 --> 00:11:16.045 therefore the system is degrading
00:11:16.045 --> 00:11:18.005 because of the massive number of messages,
00:11:18.145 --> 00:11:19.565 but it is degrading gracefully.
00:11:19.565 --> 00:11:21.525 People are not going to get too upset if
00:11:21.525 --> 00:11:22.645 they don't see a delivery receipt.
00:11:22.645 --> 00:11:23.845 They will get upset though
00:11:23.845 --> 00:11:24.965 if their message is not going through.
00:11:24.985 --> 00:11:27.165 In our case, payments, customer support
00:11:27.225 --> 00:11:29.645 and order status are critical, so we are going
00:11:29.645 --> 00:11:30.725 to keep them at the highest track.
00:11:30.725 --> 00:11:34.045 Another idea for gracefully degrading requests is not making
00:11:34.045 --> 00:11:35.205 the requests in the first place.
00:11:35.225 --> 00:11:37.405 Simply put, let's say you go to your browser,
00:11:37.405 --> 00:11:38.685 you're looking at the fancy T-shirts
00:11:38.685 --> 00:11:41.045 and this results in a call to the server.
00:11:41.185 --> 00:11:43.205 The server goes and fetches data from the cache.
00:11:43.205 --> 00:11:45.325 The cache tries to fetch their data from the database.
00:11:45.325 --> 00:11:46.565 Another person does the same thing.
00:11:46.565 --> 00:11:47.765 So another request goes to a server,
00:11:47.765 --> 00:11:49.125 another request goes to cache.
00:11:49.135 --> 00:11:51.205 Cache tries to fetch from the database and so on.
00:11:51.205 --> 00:11:53.260 If there's a lot of users that's going to put a, put a lot
00:11:53.260 --> 00:11:55.500 of load on the server, which is going to in turn put a lot
00:11:55.500 --> 00:11:57.805 of load on a downstream service like a cache
00:11:57.905 --> 00:12:00.725 and even more downstream will you see a database which is
00:12:00.725 --> 00:12:02.045 going to be under a lot of load.
00:12:02.145 --> 00:12:04.205 All of these services are in the critical path.
00:12:04.225 --> 00:12:05.485 All of them are under heavy load.
00:12:05.515 --> 00:12:07.965 What if the database stops responding
00:12:08.105 --> 00:12:09.485 or starts becoming really slow?
00:12:09.485 --> 00:12:11.005 Let's say there's a lot of update queries
00:12:11.025 --> 00:12:12.845 or select queries on the database.
00:12:12.995 --> 00:12:15.165 It's not able to manage the latency requirements.
00:12:15.305 --> 00:12:17.365 It starts getting slow. What should the cache do?
00:12:17.365 --> 00:12:19.245 Should it go ahead with business as usual
00:12:19.345 --> 00:12:21.005 and just continue making queries?
00:12:21.065 --> 00:12:23.085 Or should it let the database relax for a while,
00:12:23.305 --> 00:12:25.445 let it recover and once it's fine,
00:12:25.445 --> 00:12:26.685 then start making queries again.
00:12:26.745 --> 00:12:28.405 The second idea is more mature idea.
00:12:28.465 --> 00:12:32.365 If a service is not able to meet your latency requirements,
00:12:32.585 --> 00:12:34.725 it probably means that it is overloaded
00:12:34.785 --> 00:12:36.085 or it's trying to fix itself.
00:12:36.305 --> 00:12:38.285 Let it breathe. Don't send the number requests
00:12:38.285 --> 00:12:40.205 that you were sending earlier, short circuit it.
00:12:40.205 --> 00:12:41.645 Kill the requests on your end.
00:12:41.695 --> 00:12:44.525 Don't let them reach the destination service if the
00:12:44.525 --> 00:12:45.805 cache is overloaded.
00:12:45.805 --> 00:12:47.325 If the cache is responding slowly,
00:12:47.355 --> 00:12:50.205 what the server can do is stop making the request
00:12:50.205 --> 00:12:52.605 to the cache, fail the requests on the spot
00:12:52.665 --> 00:12:54.885 and give a response to the client saying that,
00:12:55.145 --> 00:12:56.645 I'm sorry, I can't fetch this data.
00:12:56.745 --> 00:13:00.405 Why is this better? Because your system is under heavy load.
00:13:00.625 --> 00:13:02.725 It is performing too poorly to be acceptable.
00:13:02.775 --> 00:13:03.805 Maybe it's has two
00:13:03.825 --> 00:13:06.205 or three seconds of latency, the database or the cache.
00:13:06.265 --> 00:13:07.925 If this is the case, your customers
00:13:07.925 --> 00:13:09.045 are going to be upset anyway.
00:13:09.065 --> 00:13:10.685 The requests are going to time out anyway.
00:13:10.685 --> 00:13:12.805 There's no point in making requests
00:13:12.805 --> 00:13:15.765 to the downstream systems and continuing to overload them.
00:13:15.875 --> 00:13:17.245 It's better to remove the pressure,
00:13:17.395 --> 00:13:18.605 fail the requests on the spot,
00:13:18.675 --> 00:13:21.525 make the customers get the same response of error or timeout
00:13:21.585 --> 00:13:23.125 and let the systems recover.
00:13:23.195 --> 00:13:26.005 This is called short circuit where requests are failed.
00:13:26.025 --> 00:13:28.325 In the upstream services, there's also a mirror image
00:13:28.325 --> 00:13:31.165 of this called back pressure, where downstream services,
00:13:31.235 --> 00:13:33.845 when they get a lot of requests, stop processing them.
00:13:33.845 --> 00:13:36.765 What happens is, let's say the cash is getting a lot
00:13:36.765 --> 00:13:38.245 of requests gets a thousand requests,
00:13:38.465 --> 00:13:39.885 and the average latency
00:13:39.885 --> 00:13:42.245 of the cache it notes is two seconds.
00:13:42.505 --> 00:13:44.925 The cache knows that it should be responding requests
00:13:44.925 --> 00:13:45.965 in just a hundred millisecond.
00:13:46.145 --> 00:13:48.325 So what does it do? It starts dropping requests.
00:13:48.545 --> 00:13:51.965 It starts failing requests the moment it gets it from the
00:13:51.965 --> 00:13:53.005 upstream service, okay,
00:13:53.005 --> 00:13:54.925 so if you get a new request from the upstream service,
00:13:55.105 --> 00:13:57.205 you immediately say, request fail, try again later.
00:13:57.355 --> 00:13:58.765 What does this tell the upstream service?
00:13:58.945 --> 00:14:01.805 It tells them that maybe I should stop sending requests.
00:14:01.805 --> 00:14:03.245 That's that's definitely one thing.
00:14:03.265 --> 00:14:05.485 But the second thing is even if they don't do that,
00:14:05.485 --> 00:14:06.845 even if the upstream service is adamant
00:14:07.025 --> 00:14:08.845 and continue sending requests, even if,
00:14:08.845 --> 00:14:10.285 if it doesn't have the logic of you know,
00:14:10.285 --> 00:14:12.805 giving it breathing time, the cash itself is able
00:14:12.805 --> 00:14:14.685 to ignore the requests which are coming in new
00:14:14.705 --> 00:14:15.925 and able to recover quickly.
00:14:16.025 --> 00:14:17.445 So it's not processing requests anymore,
00:14:17.555 --> 00:14:19.205 it's just focusing on recovery.
00:14:19.235 --> 00:14:21.045 It's just focusing on answering the
00:14:21.045 --> 00:14:22.205 requests that it has right now.
00:14:22.205 --> 00:14:24.325 Maybe the top hundred. This is called back pressure
00:14:24.325 --> 00:14:27.085 where the system reacts to upstream systems.
00:14:27.465 --> 00:14:28.805 It ignores the requests,
00:14:28.805 --> 00:14:31.285 it drops the requests immediately on arrival so
00:14:31.285 --> 00:14:33.285 that it can start performing according
00:14:33.285 --> 00:14:34.485 to the service level agreements.
00:14:34.485 --> 00:14:36.325 Usually when it comes to short circuiting
00:14:36.325 --> 00:14:38.965 or back pressure, the error that you send back as a response
00:14:39.105 --> 00:14:42.125 to the client to the upstream service has the information
00:14:42.125 --> 00:14:43.805 that you know, this is back pressure.
00:14:43.835 --> 00:14:46.645 It's not really a failure. I have failed it preemptively.
00:14:46.695 --> 00:14:48.005 Maybe you can try in 10 seconds,
00:14:48.095 --> 00:14:49.525 maybe you can try after a minute.
00:14:49.745 --> 00:14:52.125 So the upstream service knows that, okay,
00:14:52.475 --> 00:14:53.685 this is not a permanent failure.
00:14:53.755 --> 00:14:55.525 It's not like password is wrong, okay?
00:14:55.555 --> 00:14:57.565 It's more like, oh, I couldn't fetch the data.
00:14:57.565 --> 00:14:59.845 Could you try after a minute? So the client on the mobile
00:14:59.865 --> 00:15:02.445 device or the browser, if it's having that logic,
00:15:02.465 --> 00:15:04.765 if it's intelligent enough, will stop making requests
00:15:04.765 --> 00:15:07.005 for a while and one minute later it'll automatically
00:15:07.015 --> 00:15:08.245 start making those requests.
00:15:08.345 --> 00:15:09.405 You can do that kind of stuff.
00:15:09.545 --> 00:15:12.045 So in this way, your system is able to react
00:15:12.185 --> 00:15:13.445 to extreme pressure
00:15:13.445 --> 00:15:15.565 and it's able to gracefully degrade the service
00:15:15.825 --> 00:15:17.765 and eventually again, come back when it can.
00:15:17.825 --> 00:15:19.325 The engineers are happy to listen to this.
00:15:19.325 --> 00:15:21.765 They say that we are going to implement this kind
00:15:21.765 --> 00:15:23.605 of a system where when requests come in,
00:15:23.605 --> 00:15:25.165 we'll look at the priority of the requests
00:15:25.265 --> 00:15:27.485 and we'll also set up a web application firewall
00:15:27.545 --> 00:15:29.845 to make sure that the system continues performing
00:15:29.955 --> 00:15:31.165 despite malicious attacks.
00:15:31.265 --> 00:15:32.925 And you stop them before they go away
00:15:32.945 --> 00:15:35.285 and you, you ask them, well, there's another thing.
00:15:35.355 --> 00:15:37.685 When you had all of these millions of requests coming
00:15:37.685 --> 00:15:39.485 to your system, how did your system perform?
00:15:39.485 --> 00:15:42.045 Like was it trying to process all the requests
00:15:42.185 --> 00:15:43.645 or was it doing some sort of filtering
00:15:43.645 --> 00:15:44.765 on the incoming requests?
00:15:44.905 --> 00:15:46.805 So the engineers say, well, we just have a
00:15:46.805 --> 00:15:48.085 first and first out policy.
00:15:48.235 --> 00:15:49.925 It's like a queue. Whenever a request comes,
00:15:49.925 --> 00:15:51.005 we try to process it.
00:15:51.025 --> 00:15:53.525 If it works, great. If it doesn't work, that's also fine.
00:15:53.525 --> 00:15:55.725 We just give a response of success or error
00:15:55.865 --> 00:15:57.205 and then we go to the next request.
00:15:57.205 --> 00:15:59.085 Everything is happening in a queue one by one.
00:15:59.145 --> 00:16:00.405 Now do you notice a problem here?
00:16:00.405 --> 00:16:01.605 What happens if one
00:16:01.605 --> 00:16:04.085 of the requests takes a long time to process?
00:16:04.475 --> 00:16:05.565 What happens if one
00:16:05.565 --> 00:16:08.805 of the requests is making a complex query to a database?
00:16:08.985 --> 00:16:10.565 The rest of the requests will be waiting
00:16:10.625 --> 00:16:11.685 on that request to complete.
00:16:11.755 --> 00:16:13.525 This is like being in an airport queue
00:16:13.585 --> 00:16:14.845 and the person at the head
00:16:14.845 --> 00:16:17.205 of the line is taking a long time to get the luggage through.
00:16:17.225 --> 00:16:19.805 You are going to get irritated in fancy t-shirts io
00:16:19.805 --> 00:16:21.005 amongst all the requests that you have.
00:16:21.225 --> 00:16:22.805 One of them may be complex, one
00:16:22.805 --> 00:16:25.885 of them may be taking a while, so the rest of requests, all
00:16:25.885 --> 00:16:28.245 of them will have to wait while this one completes.
00:16:28.355 --> 00:16:31.285 It's called head offline blocking the average latency
00:16:31.345 --> 00:16:34.485 of all requests because of head offline blocking increases.
00:16:34.485 --> 00:16:35.685 There are two ways to solve this.
00:16:35.785 --> 00:16:38.445 One is parallelism, where you have parallel queues, you have
00:16:38.965 --> 00:16:41.125 parallel computers processing the requests.
00:16:41.345 --> 00:16:43.045 You can increase the number of computers you.
00:16:43.045 --> 00:16:44.605 That is like opening up a new queue
00:16:44.785 --> 00:16:45.965 of requests to be processed.
00:16:46.065 --> 00:16:48.605 The other thing that you can do is in the same computer,
00:16:48.625 --> 00:16:50.285 if you have multiple virtual computers,
00:16:50.285 --> 00:16:52.085 which is multiple cores, then those can
00:16:52.085 --> 00:16:53.245 process requests in parallel.
00:16:53.245 --> 00:16:55.605 This is where two lines or four lines
00:16:55.625 --> 00:16:56.965 or eight lines are moving together.
00:16:57.075 --> 00:16:59.445 Another thing you can do is called concurrency.
00:16:59.795 --> 00:17:00.925 Here there's the concept
00:17:00.945 --> 00:17:03.165 of threads in many programming languages.
00:17:03.305 --> 00:17:05.965 The basic idea is if I am at the head of the queue
00:17:06.065 --> 00:17:08.645 and I'm taking a long time, I can be asked to step aside
00:17:08.825 --> 00:17:11.965 for a while and the next person's request can be processed.
00:17:11.985 --> 00:17:13.405 So they can submit their luggage
00:17:13.405 --> 00:17:15.885 and maybe they just took 10 seconds to give their luggage.
00:17:15.885 --> 00:17:16.925 They just had a single bag and
00:17:16.925 --> 00:17:18.005 they're done and they go home.
00:17:18.145 --> 00:17:20.325 Now I'm processed again for the next 10 seconds.
00:17:20.585 --> 00:17:23.525 If I complete, great. If I don't, I again move to the side.
00:17:23.525 --> 00:17:25.925 Another person comes, has the luggage processed,
00:17:25.985 --> 00:17:28.365 and if they complete, that's great in 10 seconds,
00:17:28.365 --> 00:17:30.805 otherwise I'll be again asked to come forward.
00:17:30.985 --> 00:17:32.525 So this is called concurrency.
00:17:32.715 --> 00:17:35.605 This is the same queue is being used,
00:17:35.785 --> 00:17:38.885 but the requests are being processed out of auto one by one
00:17:38.945 --> 00:17:41.725 so that the overall wait time of the queue reduces.
00:17:41.755 --> 00:17:44.885 When it comes to fancy t-shirts, io, maybe I'm making a lot
00:17:44.885 --> 00:17:46.165 of IO calls, a lot
00:17:46.165 --> 00:17:47.885 of network calls, a lot of database calls.
00:17:48.065 --> 00:17:49.765 That's taking a long time to process.
00:17:50.345 --> 00:17:53.165 So my request is waiting from time to time while the rest
00:17:53.165 --> 00:17:54.765 of the people are being served from memory,
00:17:54.835 --> 00:17:56.205 they are being processed really fast
00:17:56.345 --> 00:17:58.925 and so they don't have to wait for my completion.
00:17:58.945 --> 00:18:01.885 And so your solution to the engineers is process the request
00:18:01.885 --> 00:18:03.765 concurrently using multiple threads.
00:18:03.835 --> 00:18:06.805 This should reduce the average latency of each request.
00:18:06.985 --> 00:18:08.045 The second thing you ask them
00:18:08.045 --> 00:18:10.365 to do is use a network protocol,
00:18:10.375 --> 00:18:13.445 which supports having multiple queues request queues.
00:18:13.475 --> 00:18:15.485 Here you're looking at something like GRPC.
00:18:15.485 --> 00:18:16.885 They avoid head of line blocking
00:18:16.985 --> 00:18:18.565 by processing requests out of order.
00:18:18.625 --> 00:18:19.765 So the day of the sale comes,
00:18:19.865 --> 00:18:21.605 you are again excited looking at dashboards,
00:18:21.665 --> 00:18:25.085 the sales starts, things smoothly flow forward.
00:18:25.345 --> 00:18:28.685 You see an increase in sales up to 10,000 T-shirts sold
00:18:28.905 --> 00:18:30.565 and the sale lens, the flash sale lens,
00:18:30.755 --> 00:18:31.805 it's a complete success.
00:18:31.945 --> 00:18:33.125 The engineering team is very happy,
00:18:33.185 --> 00:18:34.205 the founder is very happy.
00:18:34.275 --> 00:18:35.325 They congratulate you
00:18:35.425 --> 00:18:38.605 and your simple idea of trying to estimate capacity.
00:18:38.705 --> 00:18:41.365 If that didn't work, then you went for some basic approaches
00:18:41.365 --> 00:18:43.405 of preemptively scaling, of caching,
00:18:43.625 --> 00:18:44.805 the important request parts
00:18:45.025 --> 00:18:46.685 of optimizing on the critical parts
00:18:46.825 --> 00:18:48.045 to avoid malicious actors.
00:18:48.225 --> 00:18:50.205 You had head of line blocking removed,
00:18:50.305 --> 00:18:52.325 you had a web application firewall added
00:18:52.505 --> 00:18:54.765 and you were ready to gracefully degrade the system.
00:18:54.865 --> 00:18:56.805 Now the engineers are completely on your side
00:18:56.805 --> 00:18:59.605 and they say that in case we have future issues,
00:18:59.795 --> 00:19:01.325 what do you think we should keep in mind?
00:19:01.325 --> 00:19:03.885 Things that would be required at extreme scale?
00:19:03.915 --> 00:19:05.245 What are the things that Google does
00:19:05.245 --> 00:19:07.325 or Facebook does to manage flash sales?
00:19:07.545 --> 00:19:09.325 You tell them that there is just one simple rule.
00:19:09.325 --> 00:19:12.285 Making some customers happy is more useful than
00:19:12.285 --> 00:19:13.485 making all of them unhappy.
00:19:13.485 --> 00:19:16.485 Making some customers happy, meaning processing the requests
00:19:16.485 --> 00:19:20.125 of some customers is more useful than making all
00:19:20.125 --> 00:19:22.085 of the customers wait for a long time
00:19:22.185 --> 00:19:23.285 and see a failure screen.
00:19:23.425 --> 00:19:26.165 How do you do this engineering wise? There's just one way.
00:19:26.295 --> 00:19:28.645 Start dropping requests, which you cannot process.
00:19:28.945 --> 00:19:31.005 If your system can manage just a hundred requests
00:19:31.145 --> 00:19:33.205 and you get a thousand, then you have to drop 900.
00:19:33.275 --> 00:19:35.725 It's not that you are going to scale up in milliseconds,
00:19:35.725 --> 00:19:37.965 that's not going to happen and you can't just take requests
00:19:37.965 --> 00:19:38.965 and pass it to the next server
00:19:38.965 --> 00:19:40.965 because the other server may also be overloaded.
00:19:41.025 --> 00:19:43.685 All you can do is look out for yourself.
00:19:43.865 --> 00:19:45.965 You make a decision. If you get a thousand requests
00:19:45.965 --> 00:19:47.605 and you can only manage a 10th of it,
00:19:47.605 --> 00:19:49.805 then you either take every 10th request
00:19:49.985 --> 00:19:51.085 or you take the first hundred
00:19:51.225 --> 00:19:53.285 or you take the last hundred, whatever be the case,
00:19:53.285 --> 00:19:54.445 900 have to be dropped.
00:19:54.445 --> 00:19:56.565 There's no other way to solve this problem.
00:19:56.715 --> 00:19:58.165 This is called rate limiting,
00:19:58.575 --> 00:20:02.485 where the number requests which a server is processing stays
00:20:02.725 --> 00:20:03.925 constant stays at max level,
00:20:04.395 --> 00:20:07.125 despite the incoming load being higher than the max
00:20:07.125 --> 00:20:08.285 level that it can process.
00:20:08.335 --> 00:20:10.045 There are many rate limiting algorithms.
00:20:10.045 --> 00:20:12.365 We'll just be talking about the two most popular ones.
00:20:12.505 --> 00:20:15.125 The easiest one to understand is token bucket.
00:20:15.265 --> 00:20:19.245 You basically have a cache which has a number 1000.
00:20:19.605 --> 00:20:21.605 Whenever a request is going to be processed,
00:20:21.665 --> 00:20:24.125 it looks at the cash and decrements the value of the cash.
00:20:24.185 --> 00:20:25.845 So from a thousand it becomes 9, 9, 9.
00:20:25.845 --> 00:20:27.885 Meanwhile, because you have concurrent systems,
00:20:27.995 --> 00:20:30.485 another request may come in and it may be processed.
00:20:30.505 --> 00:20:31.565 So it may start processing.
00:20:31.625 --> 00:20:35.325 The cache is decreed, it becomes 9, 9, 8, up to what point?
00:20:35.465 --> 00:20:38.325 Up to zero. So maybe each request takes a hundred
00:20:38.325 --> 00:20:39.805 milliseconds to resolve.
00:20:39.905 --> 00:20:42.445 So at most 1000 requests will be resolved
00:20:42.545 --> 00:20:43.925 in parallel or concurrently.
00:20:43.995 --> 00:20:46.925 This cache ensures that the thousand one request,
00:20:47.175 --> 00:20:49.325 which tries to be processed concurrently
00:20:49.325 --> 00:20:50.445 or in parallel will be stopped.
00:20:50.505 --> 00:20:52.365 You cannot process the thousand one request
00:20:52.365 --> 00:20:54.485 because the cash value will be zero decrementing,
00:20:54.485 --> 00:20:56.325 it will result in a negative number.
00:20:56.355 --> 00:20:58.165 That can't happen. That check will stop
00:20:58.185 --> 00:20:59.405 the request from being processed.
00:20:59.405 --> 00:21:02.245 It'll be kept in queue till at least one request is freed up
00:21:02.315 --> 00:21:03.405 till it completes processing.
00:21:03.405 --> 00:21:05.485 When it completes processing it increments,
00:21:05.485 --> 00:21:07.285 the value in cash makes it positive one,
00:21:07.345 --> 00:21:09.565 and now the request is just waiting and move in
00:21:09.565 --> 00:21:11.045 because the cash value will again be
00:21:11.045 --> 00:21:12.405 decremented to zero and it goes through.
00:21:12.425 --> 00:21:14.685 The benefit of this is at any point in time,
00:21:14.705 --> 00:21:16.725 you know the maximum number requests that you're processing.
00:21:16.725 --> 00:21:17.725 This is called token bucket.
00:21:17.785 --> 00:21:19.765 You have a limited number of tokens in a bar.
00:21:19.795 --> 00:21:21.165 When users come in, you know
00:21:21.165 --> 00:21:23.045 that at most a hundred requests are inside.
00:21:23.045 --> 00:21:25.805 At any point in time when people leave, tokens re-up
00:21:25.805 --> 00:21:27.405 and you give that to the rest of the users.
00:21:27.625 --> 00:21:29.205 The second idea is called leaky bucket.
00:21:29.235 --> 00:21:32.605 Instead of having tokens, you now have timestamps here.
00:21:32.605 --> 00:21:35.325 You say that every one 10th of a second, I'm going
00:21:35.325 --> 00:21:36.925 to be taking one request into the system.
00:21:36.985 --> 00:21:39.085 So the rate of requests which are flowing into
00:21:39.085 --> 00:21:40.125 the system are constant.
00:21:40.125 --> 00:21:41.485 Even if you get a thousand requests,
00:21:41.505 --> 00:21:42.925 if you're allowing a request only
00:21:42.925 --> 00:21:45.365 after a hundred milliseconds for a thousand requests,
00:21:45.505 --> 00:21:48.205 you will have 1000 into 100 milliseconds,
00:21:48.335 --> 00:21:50.045 which is 100 seconds.
00:21:50.385 --> 00:21:53.285 As total time to process these requests, you see that many
00:21:53.285 --> 00:21:54.925 of these requests will actually time out.
00:21:54.925 --> 00:21:56.445 That's one of the problems with leaky bucket.
00:21:56.505 --> 00:21:59.325 It has a consistent rate of allowing requests inside.
00:21:59.425 --> 00:22:00.685 It is useful in some cases
00:22:00.695 --> 00:22:02.805 where you don't want the system overloaded at all
00:22:02.825 --> 00:22:05.205 and you want a constant stream of requests.
00:22:05.305 --> 00:22:08.005 But in cases where your system has a max capacity,
00:22:08.005 --> 00:22:10.445 which is higher than your leaky bucket capacity,
00:22:10.505 --> 00:22:11.925 it seems like a waste, but it's
00:22:11.925 --> 00:22:13.005 an algorithm that you may use.
00:22:13.145 --> 00:22:14.805 So usually token bucket is used.
00:22:14.805 --> 00:22:17.005 Usually rate limiting is performed locally
00:22:17.545 --> 00:22:18.645 inside one server.
00:22:18.825 --> 00:22:20.685 So as requests come into a single server,
00:22:21.025 --> 00:22:22.405 it makes a decision for itself.
00:22:22.405 --> 00:22:24.485 Should I process this request right now or no?
00:22:24.505 --> 00:22:25.805 Is a decision that it makes.
00:22:26.025 --> 00:22:28.805 But in some cases you may have a distributed rate limiter.
00:22:28.915 --> 00:22:31.365 Also, a single server decides whether
00:22:31.545 --> 00:22:33.445 or not a request should be processed.
00:22:33.445 --> 00:22:35.405 So let's say you have servers 1, 2, 3, 4, and five.
00:22:35.405 --> 00:22:37.845 Server number three has a distributed rate limiter.
00:22:38.125 --> 00:22:40.405 Whenever a request comes to one or two or four
00:22:40.425 --> 00:22:42.045 or five, they first talk to three.
00:22:42.055 --> 00:22:44.645 Check with it whether I should process this request or no.
00:22:44.705 --> 00:22:46.525 So it may have a token bucket counter
00:22:46.625 --> 00:22:48.445 or a leaky bucket algorithm inside it.
00:22:48.585 --> 00:22:50.725 If three tells them yes, you should process it,
00:22:50.725 --> 00:22:53.125 the request is processed, otherwise the request is rejected.
00:22:53.225 --> 00:22:55.765 So here you have some sort of central server,
00:22:55.815 --> 00:22:56.845 which is making sure
00:22:56.845 --> 00:23:00.325 that the rate remitting algorithm has data in one place.
00:23:00.465 --> 00:23:03.525 Uh, the benefit of this is you can add global controls here
00:23:03.665 --> 00:23:06.525 you can say that the total number of requests for t-shirts
00:23:06.525 --> 00:23:09.445 that I can process, uh, in 10 seconds is so and so.
00:23:09.445 --> 00:23:11.445 If you had it locally in the servers, then each
00:23:11.445 --> 00:23:12.725 of the servers would have their own data
00:23:12.865 --> 00:23:14.605 and the total count may not have matched.
00:23:14.675 --> 00:23:16.445 I'll take an example here. Let's say you have a central
00:23:16.445 --> 00:23:18.125 server three with a maximum count
00:23:18.125 --> 00:23:19.645 of a hundred requests processed per second.
00:23:20.005 --> 00:23:21.845 Whenever a request comes to any of these five servers,
00:23:21.845 --> 00:23:24.005 three ensures that at most 100
00:23:24.005 --> 00:23:25.245 requests are processed per second.
00:23:25.275 --> 00:23:27.045 Okay? So it's a central source of truth.
00:23:27.225 --> 00:23:29.685 On the other hand, if we try to distribute this logic
00:23:29.685 --> 00:23:30.885 amongst all five servers,
00:23:30.885 --> 00:23:32.685 which will make the rate limiting fast
00:23:32.685 --> 00:23:35.045 because it'll be processed locally, that information,
00:23:35.075 --> 00:23:38.245 then we might set a limit of 20 requests per server.
00:23:38.345 --> 00:23:40.485 Now take the scenario where 1, 2, 3
00:23:40.485 --> 00:23:42.165 and four get 20 requests each,
00:23:42.305 --> 00:23:43.845 and number five gets no requests.
00:23:43.945 --> 00:23:46.645 What's happening here is you have processed 80 requests per
00:23:46.645 --> 00:23:48.965 second, although you had a max capacity of a hundred
00:23:48.965 --> 00:23:50.285 because 1, 2, 3,
00:23:50.305 --> 00:23:51.645 and four don't know
00:23:51.645 --> 00:23:53.445 that five is not processing any requests.
00:23:53.515 --> 00:23:55.805 They could have gone all the way to 25, but they didn't.
00:23:55.865 --> 00:23:58.965 So a central place gives you more global control.
00:23:59.165 --> 00:24:02.045 A distributed implementation requires lesser coordination
00:24:02.045 --> 00:24:03.525 and therefore it's simpler to implement.
00:24:03.525 --> 00:24:06.925 99% of the time that I have seen rate limiting happening,
00:24:06.995 --> 00:24:08.005 it's all local. 