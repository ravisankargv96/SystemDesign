## Chapters
* 00:00 - A good problem
* 01:05 - Server Hosting Options
* 02:41 - Request routing
* 04:31 - Server setup
* 05:58 - Scaling servers!
* 08:37 - Distributed server challenges
* 10:53 - Load Balancing Algorithm
* 12:31 - Horizontal vs. Vertical Scaling

## Transcript
00:00:00.165 --> 00:00:02.725 A few months go by and your founder is very happy
00:00:02.755 --> 00:00:04.205 with the progress that they have made.
00:00:04.265 --> 00:00:06.645 You hear about the app from time to time on social media,
00:00:06.915 --> 00:00:08.125 even maybe on news media,
00:00:08.345 --> 00:00:11.645 and a lot of users are now regularly using the app,
00:00:11.645 --> 00:00:13.885 which means the number of requests that this app has
00:00:13.885 --> 00:00:15.805 to serve has increased up to the point
00:00:15.805 --> 00:00:17.125 that the founder comes back to you
00:00:17.125 --> 00:00:18.245 and says, the cost
00:00:18.245 --> 00:00:20.805 of hosting this app on the cloud is quite expensive.
00:00:20.965 --> 00:00:22.965 AWS is charging me a pretty large bill
00:00:22.965 --> 00:00:23.965 to host these servers.
00:00:24.025 --> 00:00:25.085 So then you remember
00:00:25.085 --> 00:00:27.405 that we are using a serverless technology over here,
00:00:27.455 --> 00:00:29.445 which means we don't really have servers.
00:00:29.565 --> 00:00:31.405 AWS manages those servers end to end
00:00:31.405 --> 00:00:33.885 and we use them as a black box not knowing when they'll be
00:00:33.885 --> 00:00:36.165 spun up, not knowing how many are running at any point in
00:00:36.165 --> 00:00:38.045 time because this is a cost question.
00:00:38.195 --> 00:00:40.365 It's not that the number requirements are lesser
00:00:40.365 --> 00:00:42.045 or the extensibility of this is lesser.
00:00:42.045 --> 00:00:44.085 It's just that it's a pure cost decision.
00:00:44.185 --> 00:00:45.725 You start looking at alternatives.
00:00:45.905 --> 00:00:48.565 One option would be to try to get credits from AWS.
00:00:48.665 --> 00:00:49.765 The founder has tried to do that,
00:00:49.765 --> 00:00:51.565 that hasn't worked out or those are exhausted.
00:00:51.565 --> 00:00:53.725 The second thing that you can do is you can run your
00:00:53.725 --> 00:00:54.765 code more efficiently.
00:00:54.865 --> 00:00:57.245 If you see that there's an opportunity of caching something
00:00:57.245 --> 00:00:58.645 or you see there's an opportunity
00:00:58.665 --> 00:01:02.085 of using lesser compute IO memory, then you try
00:01:02.085 --> 00:01:03.765 to basically reduce the impact
00:01:03.865 --> 00:01:05.405 of your serverless application.
00:01:05.515 --> 00:01:07.005 This is done sufficiently
00:01:07.105 --> 00:01:08.485 and you know you are not able
00:01:08.485 --> 00:01:09.765 to find any more optimizations.
00:01:09.855 --> 00:01:12.725 Let's start at what can you do at an infrastructure level?
00:01:12.825 --> 00:01:15.765 One factor here is that serverless is charging us a premium.
00:01:15.795 --> 00:01:17.805 They're managing the end-to-end deployments.
00:01:17.805 --> 00:01:19.045 The management of these servers,
00:01:19.105 --> 00:01:22.245 we are paying more than we would if we managed these
00:01:22.245 --> 00:01:23.485 servers by ourselves.
00:01:23.615 --> 00:01:24.845 Again, we have two options here.
00:01:24.905 --> 00:01:26.005 The ones that we discussed earlier
00:01:26.185 --> 00:01:29.165 to either host the servers in our own space on premise,
00:01:29.425 --> 00:01:30.845 so we might rent out some space.
00:01:30.905 --> 00:01:32.725 We might go to a cheaper service provider,
00:01:32.785 --> 00:01:33.725 but instead what you want
00:01:33.725 --> 00:01:34.845 to do is you want to keep things simple.
00:01:35.065 --> 00:01:37.525 If you are using an existing cloud solution provider,
00:01:37.545 --> 00:01:38.645 you don't want to migrate from
00:01:38.645 --> 00:01:40.125 that cloud solution provider just yet.
00:01:40.125 --> 00:01:42.525 Maybe you can use solutions which are offered by them,
00:01:42.525 --> 00:01:43.845 which are cheaper and let's start there.
00:01:43.905 --> 00:01:46.485 One of the solutions you can use is you can reserve
00:01:46.515 --> 00:01:50.565 instances, which means you reserve servers on AWS saying
00:01:50.565 --> 00:01:53.885 that nobody else is going to be using this server compute.
00:01:54.085 --> 00:01:56.165 I will be using it and I will reserve it for a year.
00:01:56.225 --> 00:01:59.445 So what happens with this is AWS has the servers
00:01:59.445 --> 00:02:00.565 rented out for a year.
00:02:00.675 --> 00:02:01.725 That is quite good.
00:02:01.845 --> 00:02:04.645 AWS has an upfront payment, so they give you a discount
00:02:04.665 --> 00:02:07.125 and you'll notice this happening even in large companies
00:02:07.125 --> 00:02:09.485 which are using compute power, uh, serverless.
00:02:09.485 --> 00:02:11.605 Eventually they move to this kind of a solution,
00:02:11.615 --> 00:02:14.725 which is rent out compute for a year or maybe even more.
00:02:14.725 --> 00:02:17.005 But what does this mean? It means that you will have
00:02:17.005 --> 00:02:20.045 to book some servers and those servers will have APIs
00:02:20.045 --> 00:02:21.685 exposed and everything just like serverless,
00:02:21.745 --> 00:02:24.365 but the management of these servers has to be done by you,
00:02:24.365 --> 00:02:26.605 which means starting the server, stopping the server,
00:02:26.795 --> 00:02:28.685 upgrading any kind of code that you have
00:02:28.685 --> 00:02:31.165 inside it doing the deployment has to be done by you.
00:02:31.165 --> 00:02:33.165 Now, since it is justified, the cost
00:02:33.225 --> 00:02:34.405 of serverless is too high.
00:02:34.505 --> 00:02:36.125 You go ahead with this. This is what you suggest.
00:02:36.155 --> 00:02:38.085 Reserve an instance of AWS
00:02:38.185 --> 00:02:39.325 and make sure that all
00:02:39.325 --> 00:02:40.965 of your clients are connecting to this instance.
00:02:41.015 --> 00:02:42.085 Let's look at the first part.
00:02:42.085 --> 00:02:44.125 When users are watching your page on the browser
00:02:44.185 --> 00:02:45.365 and they click on register,
00:02:45.365 --> 00:02:47.685 they want your API for registration to be hit.
00:02:47.825 --> 00:02:51.485 So that will be, let's assume API panc T-shirts IO
00:02:51.655 --> 00:02:52.685 slash purchase.
00:02:52.825 --> 00:02:55.045 That's the entire URL that they're going for
00:02:55.185 --> 00:02:57.525 and question mark, which means they're adding parameters
00:02:57.745 --> 00:02:58.885 ID equal to order id.
00:02:58.885 --> 00:03:00.365 Maybe the user ID is also sent.
00:03:00.365 --> 00:03:02.045 Maybe the timestamp is sent all of this stuff.
00:03:02.105 --> 00:03:04.245 So it's a request which is sent to a server.
00:03:04.385 --> 00:03:05.805 How is this routing exactly happening?
00:03:05.805 --> 00:03:07.005 How is this a P actually functioning?
00:03:07.005 --> 00:03:08.885 Look at the first part. The domain API
00:03:09.425 --> 00:03:11.725 dot fancy t-shirts dot io.
00:03:11.725 --> 00:03:15.125 This domain name will resolve to your server IP address.
00:03:15.225 --> 00:03:16.645 The reserve instance that you purchased,
00:03:16.665 --> 00:03:20.285 you got an IP address for it that is configured in Route 53.
00:03:20.285 --> 00:03:22.725 Your DNS provider, your domain name server.
00:03:22.825 --> 00:03:24.885 So against this domain name you have
00:03:24.885 --> 00:03:25.925 the server's IP address.
00:03:26.065 --> 00:03:28.085 The request is now going to be routed to the server.
00:03:28.225 --> 00:03:31.965 We said slash purchase slash purchase means when the server
00:03:31.965 --> 00:03:33.605 gets this request, it's going to say, oh,
00:03:33.605 --> 00:03:34.605 it's a purchase order.
00:03:34.765 --> 00:03:36.085 I need to route this request
00:03:36.225 --> 00:03:38.125 to the function which manages purchases.
00:03:38.265 --> 00:03:39.805 So that particular function is called
00:03:39.865 --> 00:03:42.525 and when you do something like a question mark, ID equal
00:03:42.545 --> 00:03:45.125 to order id and then you have the user ID also
00:03:45.125 --> 00:03:46.165 being passed with amp percent.
00:03:46.165 --> 00:03:47.325 These are all get requests.
00:03:47.325 --> 00:03:48.845 These are basically get parameters.
00:03:48.855 --> 00:03:50.125 Those can be read by the server.
00:03:50.145 --> 00:03:52.485 The things that you pass in here are like parameters
00:03:52.485 --> 00:03:55.125 to the function that is being called in our case purchase
00:03:55.145 --> 00:03:56.245 is the function that is being called.
00:03:56.275 --> 00:03:57.325 This is how you're able
00:03:57.325 --> 00:03:58.885 to basically call a function on the server
00:03:58.905 --> 00:04:00.125 and there is authentication also.
00:04:00.125 --> 00:04:02.605 So you may send your user id, you may send your password,
00:04:02.605 --> 00:04:04.965 stuff like that, but you are able to authenticate yourself
00:04:04.965 --> 00:04:07.445 and execute a function sitting at home with your browser.
00:04:07.445 --> 00:04:08.965 There are also tools which can allow you
00:04:08.965 --> 00:04:10.365 to make post requests comfortably.
00:04:10.545 --> 00:04:12.845 For example, postman is a tool which helps you do that.
00:04:12.995 --> 00:04:15.405 That helps you manipulate server entities,
00:04:15.415 --> 00:04:16.525 which you have access to.
00:04:16.525 --> 00:04:17.925 If you're looking for get requests,
00:04:17.925 --> 00:04:19.245 usually you can just do it on the browser.
00:04:19.385 --> 00:04:20.445 You might have already done it,
00:04:20.445 --> 00:04:22.685 you might have changed the parameters in the question mark a
00:04:22.685 --> 00:04:24.485 few times and you get different responses.
00:04:24.485 --> 00:04:26.805 Wonderful. We have made our configuration on the DNS.
00:04:26.865 --> 00:04:29.845 Now requests are being routed to this reserved instance,
00:04:29.845 --> 00:04:31.845 which is quite cheap as compared to what we had earlier.
00:04:32.025 --> 00:04:33.205 How do we set this up though?
00:04:33.345 --> 00:04:35.885 On Amazon, on Google, on Azure?
00:04:35.995 --> 00:04:37.725 This setup is extremely easy.
00:04:37.905 --> 00:04:41.005 All you have to do is just mention that I want
00:04:41.005 --> 00:04:44.045 to add a new server compute in the graphical user interface.
00:04:44.045 --> 00:04:46.085 You'll be asked, what is the size of this compute?
00:04:46.145 --> 00:04:49.605 Is it large? Is it small? Is it micro nano?
00:04:49.825 --> 00:04:50.925 Is it very, very large?
00:04:51.065 --> 00:04:52.565 So there are variations for this,
00:04:52.665 --> 00:04:53.845 and depending on
00:04:53.955 --> 00:04:56.165 what you believe is necessary, you can pick one.
00:04:56.565 --> 00:04:57.605 Remember, in small companies
00:04:57.605 --> 00:05:00.005 what usually happens is you over provision.
00:05:00.005 --> 00:05:02.405 So maybe you might buy a large, you might set up a large,
00:05:02.405 --> 00:05:04.925 and then when you see that almost no compute is being used,
00:05:05.025 --> 00:05:06.245 the memory is being heavily
00:05:06.245 --> 00:05:07.685 underutilized, you can bring it down.
00:05:07.715 --> 00:05:08.925 This is a manual way
00:05:08.925 --> 00:05:10.885 of finding out the right capacity required.
00:05:10.935 --> 00:05:13.765 Let's say you do this and you find that the amount
00:05:13.765 --> 00:05:15.285 of compute you need is large.
00:05:15.385 --> 00:05:16.405 You deserve the instance,
00:05:16.585 --> 00:05:17.885 and for the next three months,
00:05:17.885 --> 00:05:19.245 things are going perfectly fine.
00:05:19.265 --> 00:05:21.245 You have set up the server, you have added your code
00:05:21.245 --> 00:05:22.445 to it, you're able to log into it.
00:05:22.445 --> 00:05:24.605 Sometimes you're able to make changes through GitHub.
00:05:24.625 --> 00:05:26.445 As an engineer, all you have to do is go
00:05:26.445 --> 00:05:27.525 to your code repository.
00:05:27.595 --> 00:05:29.205 This could be GitHub and then mention
00:05:29.275 --> 00:05:32.605 that if I make changes in this code repository on my main
00:05:32.625 --> 00:05:34.325 branch or on my dev branch,
00:05:34.475 --> 00:05:37.245 what will happen is I will send an event to AWS,
00:05:37.375 --> 00:05:39.725 it'll do a git pull, which will get the latest code of main
00:05:39.725 --> 00:05:41.045 and then it'll just restart the server.
00:05:41.045 --> 00:05:42.205 Effectively what has happened is your
00:05:42.205 --> 00:05:43.245 code has been updated, okay?
00:05:43.245 --> 00:05:44.565 And when you restart the server, all
00:05:44.565 --> 00:05:46.605 of your in-memory stuff is deleted
00:05:46.745 --> 00:05:48.525 and you basically have an updated
00:05:48.885 --> 00:05:50.005 instance running wonderful.
00:05:50.005 --> 00:05:51.205 With this, you have reduced costs
00:05:51.425 --> 00:05:54.165 and a few months past, your founder friend is very happy
00:05:54.165 --> 00:05:55.405 because earlier they
00:05:55.405 --> 00:05:56.445 were paying, let's say a thousand dollars.
00:05:56.465 --> 00:05:57.925 Now they're paying, paying just $500,
00:05:58.185 --> 00:06:00.045 but users are saying that, you know,
00:06:00.045 --> 00:06:01.565 sometimes this server crashes
00:06:01.865 --> 00:06:04.645 and some of them are complaining that my app is too slow.
00:06:04.785 --> 00:06:06.285 I'm not able to get responses quick enough.
00:06:06.305 --> 00:06:08.685 You go to AWS, you see that the amount of memory
00:06:08.685 --> 00:06:10.005 that is being used is tremendous.
00:06:10.145 --> 00:06:12.205 You verify that this is not a bug or a problem.
00:06:12.235 --> 00:06:13.645 This is a real requirement,
00:06:13.745 --> 00:06:16.805 and so what you decide is you are using a large instance.
00:06:16.945 --> 00:06:18.445 You need a even bigger instance.
00:06:18.545 --> 00:06:20.765 So you go for X large, which is extra large,
00:06:20.785 --> 00:06:22.725 but that's not enough after a few weeks.
00:06:22.785 --> 00:06:24.405 So you go for extra, extra large,
00:06:24.425 --> 00:06:25.645 and that itself is not enough.
00:06:25.645 --> 00:06:27.445 After a few weeks, this app is scaling up,
00:06:27.445 --> 00:06:29.565 your friend is on a yacht calling you
00:06:29.565 --> 00:06:30.805 and saying that I'm making a lot of money,
00:06:30.805 --> 00:06:32.325 but I need a server instance upgrade.
00:06:32.385 --> 00:06:35.365 So you get a triple X large, a four X large,
00:06:35.465 --> 00:06:37.605 but at some point you realize this is ridiculous.
00:06:37.655 --> 00:06:39.645 There are two major issues with our approach
00:06:39.645 --> 00:06:40.845 of just scaling up the server,
00:06:40.895 --> 00:06:43.525 which is stopping the instance, starting a new instance
00:06:43.665 --> 00:06:44.805 and moving the code there.
00:06:44.825 --> 00:06:46.085 The first one is we are not able
00:06:46.085 --> 00:06:47.925 to reserve capacity efficiently.
00:06:47.985 --> 00:06:49.845 If we want to reserve for the entire year,
00:06:49.845 --> 00:06:52.005 then our app is scaling much faster than that.
00:06:52.105 --> 00:06:54.245 So the large instance is not being utilized.
00:06:54.345 --> 00:06:57.045 The second thing is there are times in the day when the
00:06:57.045 --> 00:06:59.045 large instance is being heavily underutilized
00:06:59.145 --> 00:07:00.405 and times in the day when the
00:07:00.405 --> 00:07:01.765 large instance is not good enough.
00:07:01.865 --> 00:07:04.645 So let's say T-shirts are purchased during festivals.
00:07:04.675 --> 00:07:07.125 When there are festivals, there's massive demand on normal
00:07:07.125 --> 00:07:09.845 days, on weekdays, especially when people are sleeping,
00:07:09.845 --> 00:07:10.845 there is almost no demand.
00:07:11.045 --> 00:07:13.805 You're paying the bill for a large instance while in the
00:07:13.805 --> 00:07:15.965 night you're actually just using the compute capacity
00:07:15.965 --> 00:07:17.485 of 10% of that large instance.
00:07:17.505 --> 00:07:20.045 So it's not auto-scaling, which was happening earlier.
00:07:20.045 --> 00:07:22.645 Another problem with this is if your major server
00:07:22.715 --> 00:07:24.085 crashes, then there is no backup.
00:07:24.195 --> 00:07:26.165 There's no other server which can take the
00:07:26.165 --> 00:07:27.285 load from them temporarily.
00:07:27.425 --> 00:07:29.725 No, you just have one big server. If it crashes, it's gone.
00:07:29.725 --> 00:07:31.925 Your service is down. People are not able to buy T-shirts.
00:07:31.985 --> 00:07:35.565 And finally, one point which is usually missed is the amount
00:07:35.665 --> 00:07:38.245 of virtual servers you can get for the same amount
00:07:38.245 --> 00:07:40.125 of money if you use a fleet
00:07:40.145 --> 00:07:42.885 of servers is higher than if you would use
00:07:43.085 --> 00:07:44.125 a single large instance.
00:07:44.225 --> 00:07:47.245 For example, if you have 32 small computers, each
00:07:47.245 --> 00:07:49.445 of them giving you two virtual computers, you are going
00:07:49.445 --> 00:07:51.885 to get 64 parallel requests going through the system.
00:07:52.065 --> 00:07:54.165 But if you use one very large instance,
00:07:54.305 --> 00:07:55.685 you'll just get 32 virtual
00:07:56.005 --> 00:07:57.325 computers for the same amount of money.
00:07:57.345 --> 00:07:59.565 Why is this the case? Well, in general, if you want
00:07:59.565 --> 00:08:01.085 to Alize things, then a bunch
00:08:01.085 --> 00:08:03.085 of small computers usually are more efficient than
00:08:03.305 --> 00:08:04.365 one large computer.
00:08:04.585 --> 00:08:06.365 All the requests are going to be sent over there.
00:08:06.645 --> 00:08:08.085 A single large computer having
00:08:08.265 --> 00:08:10.565 so many courses just becomes impractical.
00:08:10.565 --> 00:08:13.045 So instead of having all of them in a single place
00:08:13.265 --> 00:08:14.445 for the same price, it's cheaper.
00:08:14.505 --> 00:08:16.205 You get almost double or Forex,
00:08:16.205 --> 00:08:18.605 the compute if you use a bunch of small computers, a fleet
00:08:18.605 --> 00:08:20.485 of servers as compared to one large computer.
00:08:20.515 --> 00:08:22.205 Okay? So with all of these points, with all
00:08:22.205 --> 00:08:24.725 of your technical clarity, you go back to the founder
00:08:24.745 --> 00:08:26.645 and you say that, look, you know, we have tried
00:08:26.645 --> 00:08:27.685 to really, really scale this up.
00:08:27.685 --> 00:08:29.285 We have tried to keep the architecture very, very simple.
00:08:29.465 --> 00:08:31.765 The simplicity that the single computer was giving us is
00:08:31.765 --> 00:08:32.845 no longer affordable.
00:08:33.025 --> 00:08:34.405 We have to move to multiple server.
00:08:34.585 --> 00:08:37.125 The founder is happy that you know costs are going
00:08:37.125 --> 00:08:40.485 to go down, and now what you do is you have two or three
00:08:40.625 --> 00:08:43.685 or eight instances running smaller sized instances,
00:08:43.805 --> 00:08:46.525 running parallel requests, which brings a new problem.
00:08:46.635 --> 00:08:48.845 What if one of these servers crashes? What do you do?
00:08:48.905 --> 00:08:51.085 How do you redirect these requests which are going
00:08:51.085 --> 00:08:52.605 to the server, to the remaining servers?
00:08:52.625 --> 00:08:54.565 You want to redirect the requests so that you can serve them
00:08:54.625 --> 00:08:56.685 and the customers have a good experience despite
00:08:56.705 --> 00:08:57.725 one of the servers crashing.
00:08:57.725 --> 00:08:59.285 The second part is you want
00:08:59.285 --> 00:09:01.565 to judiciously utilize these resources
00:09:01.565 --> 00:09:03.685 that you have the multiple servers for that you have
00:09:03.685 --> 00:09:06.365 to send the requests roughly evenly to all servers.
00:09:06.365 --> 00:09:07.765 If you get 3000 requests
00:09:07.785 --> 00:09:09.365 and you have three servers, you want
00:09:09.365 --> 00:09:10.445 to send a thousand requests to each server.
00:09:10.545 --> 00:09:13.125 Why? Because the wait time of each request is roughly,
00:09:13.355 --> 00:09:15.485 even if you send the same number requests everywhere
00:09:15.665 --> 00:09:16.845 by not overloading a server,
00:09:16.845 --> 00:09:19.405 you're not overloading its bandwidth, its memory,
00:09:19.785 --> 00:09:21.125 its attack on the database.
00:09:21.345 --> 00:09:24.125 The latency of this server is usually low if you're able
00:09:24.125 --> 00:09:26.485 to judiciously distribute the requests across.
00:09:26.705 --> 00:09:29.085 For this, we need something called a load balance.
00:09:29.105 --> 00:09:31.085 So AWS already provides this off the shelf.
00:09:31.145 --> 00:09:33.565 The basic idea here is that if you get a request
00:09:33.625 --> 00:09:35.045 and you have a set of resources
00:09:35.045 --> 00:09:36.365 that you can send the request to,
00:09:36.425 --> 00:09:37.885 you choose the one which is most
00:09:38.165 --> 00:09:39.285 optimal for managing the request.
00:09:39.385 --> 00:09:42.365 One of the ideas is to just randomize. Just get a request.
00:09:42.885 --> 00:09:44.365 Randomly choose a server, send it to it.
00:09:44.365 --> 00:09:46.805 Maybe you have an internal counter of I have four servers,
00:09:46.905 --> 00:09:48.765 1, 2, 3, 4, 1, 2, 3, 4.
00:09:48.865 --> 00:09:50.845 The requests keep going to 1, 2, 3,
00:09:50.865 --> 00:09:52.045 and four in a cyclic fashion.
00:09:52.115 --> 00:09:54.125 This is good. This is called round robin.
00:09:54.275 --> 00:09:56.685 It's a very popular algorithm used in many places,
00:09:56.865 --> 00:09:59.045 but since you're looking for low latency, you may want
00:09:59.045 --> 00:10:00.125 to take some of your servers
00:10:00.125 --> 00:10:02.245 and put them in the US region for US customers
00:10:02.265 --> 00:10:04.045 and some of the servers and put them in the Indian
00:10:04.045 --> 00:10:05.205 region for Indian customers.
00:10:05.205 --> 00:10:06.405 So let's say you have three servers.
00:10:06.515 --> 00:10:08.405 Most of your users are in India.
00:10:08.465 --> 00:10:11.005 You are assigned two of them to India and one to the us.
00:10:11.185 --> 00:10:13.605 Now, if the US server crashes, the load balancer,
00:10:13.605 --> 00:10:15.565 which is a central load balancer in AWS,
00:10:15.565 --> 00:10:17.285 should have the intelligence to understand,
00:10:17.385 --> 00:10:18.565 oh, this server is gone.
00:10:18.585 --> 00:10:20.365 We are going to redirect all American
00:10:20.365 --> 00:10:21.485 requests also to India.
00:10:21.485 --> 00:10:24.165 This is managed end to end by most cloud solution providers.
00:10:24.365 --> 00:10:26.805 AWS has something called elastic load balancer,
00:10:26.805 --> 00:10:28.165 which is going to do this for you.
00:10:28.225 --> 00:10:30.005 You just need to give them a set of servers
00:10:30.005 --> 00:10:31.965 that you're actually using, which is elastic compute,
00:10:31.965 --> 00:10:33.485 which are called EC2 instances,
00:10:33.745 --> 00:10:36.325 and ELB elastic load balancer will manage all
00:10:36.325 --> 00:10:37.485 of this for you automatically.
00:10:37.505 --> 00:10:38.605 The interesting thing though is
00:10:38.605 --> 00:10:40.445 that elastic load balancer gives you a bunch
00:10:40.465 --> 00:10:43.565 of load balancing algorithms in bit, so you can choose any
00:10:43.565 --> 00:10:44.685 of the algorithms that it gives you,
00:10:44.905 --> 00:10:46.685 or you can write your own algorithm,
00:10:46.685 --> 00:10:47.725 your own custom algorithm.
00:10:47.875 --> 00:10:49.165 When you get a request, where
00:10:49.165 --> 00:10:50.285 should I route this request to?
00:10:50.425 --> 00:10:51.805 You can enter the code for
00:10:51.805 --> 00:10:53.245 that in the elastic load balancer.
00:10:53.245 --> 00:10:55.005 I'll talk about some popular algorithms now,
00:10:55.105 --> 00:10:57.845 but roughly they can be broken into two major pieces.
00:10:58.065 --> 00:11:00.645 The first can be classified as stateless algorithms,
00:11:00.645 --> 00:11:03.085 and the other one is stateful algorithms.
00:11:03.335 --> 00:11:04.685 State here means memory.
00:11:04.785 --> 00:11:07.245 If I get a request and if I have the mapping
00:11:07.385 --> 00:11:09.005 of every request ID
00:11:09.005 --> 00:11:11.605 to its corresponding server like in A DNS, then
00:11:11.605 --> 00:11:15.285 that is a stateful algorithm, meaning I need memory, I need
00:11:15.285 --> 00:11:17.045 to manage state through route requests.
00:11:17.185 --> 00:11:19.605 If I do this without any memory, if I do this
00:11:19.635 --> 00:11:22.045 with just a pure function, that would be stateless.
00:11:22.165 --> 00:11:25.205 I don't store memory of each request to each server mapping.
00:11:25.445 --> 00:11:27.045 I don't have the ranges of which
00:11:27.045 --> 00:11:28.085 requests go to which server.
00:11:28.445 --> 00:11:29.925 I just do this with a pure function.
00:11:29.945 --> 00:11:31.485 If that was the case, then it would be called
00:11:31.485 --> 00:11:32.605 stateless first part.
00:11:32.625 --> 00:11:34.445 And if I have state, if I manage state
00:11:34.445 --> 00:11:36.245 and you know I don't want to have some fancy function
00:11:36.485 --> 00:11:38.085 floating around, then it would be stateful.
00:11:38.085 --> 00:11:39.765 These are the two classes of algorithms that are there.
00:11:39.765 --> 00:11:41.245 Both of them are useful. The first one
00:11:41.245 --> 00:11:42.925 that we talked about round robin
00:11:43.345 --> 00:11:44.685 is actually a stateless algorithm.
00:11:44.705 --> 00:11:46.085 You don't need to keep any state.
00:11:46.185 --> 00:11:49.205 You just randomly keep assigning them according to iterator,
00:11:49.305 --> 00:11:50.605 1, 2, 3, 4, 1, 2, 3, 4.
00:11:50.725 --> 00:11:53.005 A simple example of a stateful algorithm would be called
00:11:53.090 --> 00:11:55.445 called least connections, means if you have three servers
00:11:55.505 --> 00:11:58.645 and uh, they have 20, 30 and 40 requests being managed,
00:11:58.785 --> 00:12:00.525 and when you get a new request, you're going
00:12:00.525 --> 00:12:02.565 to look at the server with the least number of connections.
00:12:02.625 --> 00:12:05.485 In our case, that is 20. So you redirect the request to 20.
00:12:05.665 --> 00:12:07.205 Now that will be incremented to 21.
00:12:07.235 --> 00:12:09.445 It's possible that many people left the server,
00:12:09.445 --> 00:12:12.085 which was managing 40 requests, and it comes down to 18.
00:12:12.145 --> 00:12:13.925 So when the next request comes in, it's not
00:12:13.925 --> 00:12:16.285 that you're going to send it to 21 again, you're going
00:12:16.285 --> 00:12:18.565 to send it to the server having just 18 requests now,
00:12:18.565 --> 00:12:19.885 which will be incremented to 19.
00:12:19.945 --> 00:12:22.725 So in this way, you're able to manage load based on
00:12:22.745 --> 00:12:24.565 how many requests are being served by that server,
00:12:24.745 --> 00:12:26.685 how many responses have you gotten back will be minus,
00:12:26.825 --> 00:12:29.005 and how many requests have you sent will be plus.
00:12:29.185 --> 00:12:31.125 And so there are many such algorithms.
00:12:31.345 --> 00:12:33.605 At this point though, our load balance is going
00:12:33.605 --> 00:12:35.485 to have a simple algorithm, maybe round robin,
00:12:35.575 --> 00:12:36.605 maybe these connections.
00:12:37.005 --> 00:12:39.125 Interestingly, load balancing is such a fundamental concept
00:12:39.185 --> 00:12:41.685 of computer science that it comes up in multiple
00:12:41.685 --> 00:12:43.165 places of your architecture.
00:12:43.165 --> 00:12:44.205 Go to the absolute left of
00:12:44.205 --> 00:12:45.325 the architecture diagram that we have.
00:12:45.325 --> 00:12:48.485 When browsers are trying to resolve IP addresses
00:12:48.485 --> 00:12:49.605 through a domain name server.
00:12:49.785 --> 00:12:52.565 The domain name server actually has multiple IP
00:12:52.565 --> 00:12:54.125 addresses for the same website.
00:12:54.125 --> 00:12:57.365 Fancy t-shirts dot io will have multiple IP addresses, one
00:12:57.385 --> 00:12:59.805 for the Indian region and one for the US region.
00:12:59.945 --> 00:13:03.045 Why is this the case? In case the DNS is not able to connect
00:13:03.045 --> 00:13:05.405 to one of these regions, it can connect to another region.
00:13:05.435 --> 00:13:07.925 Even the domain name server has load balancing in it.
00:13:07.985 --> 00:13:09.565 It tries to connect to a nearby region.
00:13:09.595 --> 00:13:11.605 This is called geo-based load balancing
00:13:11.745 --> 00:13:13.045 nearby low latency place.
00:13:13.155 --> 00:13:15.845 I'll go there and if it can't, then it falls back
00:13:15.845 --> 00:13:17.525 to a backup and sends the request.
00:13:17.795 --> 00:13:19.605 Despite higher latency, it's okay,
00:13:19.605 --> 00:13:20.765 at least the request is being served.
00:13:20.785 --> 00:13:22.605 And this concept of adding more
00:13:22.625 --> 00:13:25.085 and more servers will serve more requests.
00:13:25.235 --> 00:13:26.685 It's called horizontal scaling.
00:13:26.865 --> 00:13:28.125 As your app gets bigger
00:13:28.145 --> 00:13:29.845 and bigger, eventually you can't
00:13:29.845 --> 00:13:31.085 manage things with a single computer.
00:13:31.385 --> 00:13:34.405 You have to buy more computers. It's called scaling the app.
00:13:34.425 --> 00:13:36.005 And since you're buying more computers,
00:13:36.085 --> 00:13:37.325 I think you're thinking in this way.
00:13:37.325 --> 00:13:38.405 This is horizontal scaling.
00:13:38.505 --> 00:13:41.365 Uh, and the other thing which you were doing was buying a
00:13:41.365 --> 00:13:44.085 bigger and bigger instance that is called vertical scaling.
00:13:44.265 --> 00:13:45.845 It doesn't complicate the architecture much.
00:13:45.905 --> 00:13:48.165 It keeps things confined to one box.
00:13:48.305 --> 00:13:50.565 But as you upgrade the server instances,
00:13:50.785 --> 00:13:53.365 you are basically getting more compute, more bandwidth,
00:13:53.435 --> 00:13:55.085 more power into a single computer
00:13:55.115 --> 00:13:56.285 that is called vertical scaling.
00:13:56.425 --> 00:13:58.445 So buying bigger machines is called vertical scaling.
00:13:58.445 --> 00:14:00.965 Buying more machines is called horizontal scaling.
00:14:00.985 --> 00:14:02.725 If you ask me, in my experience,
00:14:02.765 --> 00:14:05.005 I have always seen hybrid approaches picked up.
00:14:05.005 --> 00:14:07.405 I've never seen a supercomputer being purchased before.
00:14:07.405 --> 00:14:08.765 People start horizontally scaling.
00:14:08.995 --> 00:14:10.445 It's usually at large instance
00:14:10.445 --> 00:14:11.845 that people start horizontal scaling.
00:14:11.875 --> 00:14:14.325 They don't go for X, X, XL, that's not needed.
00:14:14.465 --> 00:14:16.405 You start using horizontal scaling before that,
00:14:16.405 --> 00:14:18.405 and if you see that your servers are small,
00:14:18.405 --> 00:14:20.165 like if you have small servers, very often
00:14:20.165 --> 00:14:22.045 what you do is instead of buying more and more
00:14:22.045 --> 00:14:23.365 and more, you may just say,
00:14:23.545 --> 00:14:25.725 let me make my small servers all medium, okay,
00:14:25.725 --> 00:14:28.645 or a few of them medium, and now I can use an algorithm like
00:14:28.645 --> 00:14:31.245 weighted round robin instead of using 1, 2, 3, 4.
00:14:31.345 --> 00:14:32.725 If the first server is large,
00:14:32.725 --> 00:14:35.925 then I'll say 1, 1, 2, 3, 4, 1, 1, 2, 3, 4.
00:14:36.075 --> 00:14:38.285 This is basically your iterator goes at
00:14:38.285 --> 00:14:39.445 the same server multiple times.
00:14:39.445 --> 00:14:41.365 There's a counter inside each server,
00:14:41.415 --> 00:14:44.325 which tells you the size or the capacity of that server.
00:14:44.325 --> 00:14:46.325 Wonderful. Now you know about load balancing.
00:14:46.375 --> 00:14:48.245 Let's see what challenges we are going to face in future
00:14:48.505 --> 00:14:50.125 as we create fancy T-shirts. 