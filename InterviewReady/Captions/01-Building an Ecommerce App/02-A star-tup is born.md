## Chapters
* 00:00 - On-premise, or Cloud?
* 01:09 - Cost-Benefit Analysis
* 01:52 - Server or Serverless?
* 02:47 - Cost-Benefit Analysis

## Transcript
00:00:00.000 --> 00:00:02.685 And it is at this point that we make our first major tech
00:00:02.885 --> 00:00:05.845 decision, and that is whether you should host your code on a
00:00:06.005 --> 00:00:08.605 computer that you own or should you host your code on
00:00:08.645 --> 00:00:09.725 a computer which is rented.
00:00:09.725 --> 00:00:12.445 When I say rented, I mean cloud solution providers.
00:00:12.475 --> 00:00:14.965 They have compute capacity, which they're providing
00:00:14.985 --> 00:00:16.285 for a particular amount.
00:00:16.285 --> 00:00:18.325 So if you take more compute capacity
00:00:18.325 --> 00:00:19.485 from them, they charge you more.
00:00:19.485 --> 00:00:21.205 If you take less, then they charge you less so.
00:00:21.265 --> 00:00:22.645 But if you have your own computer,
00:00:22.735 --> 00:00:25.405 let's say you have a spare laptop or a desktop lying around
00:00:25.465 --> 00:00:27.445 and you think that I can connect this with the internet,
00:00:27.445 --> 00:00:29.245 people can send me requests on this computer
00:00:29.265 --> 00:00:30.645 and I can give them back responses.
00:00:30.665 --> 00:00:32.725 Why don't I just use this spare computer capacity?
00:00:32.725 --> 00:00:33.965 Lying around. Most of us have this,
00:00:34.065 --> 00:00:36.445 why would you choose a cloud solution provider at all?
00:00:36.585 --> 00:00:39.165 The answer is the cloud solution is a little more reliable.
00:00:39.425 --> 00:00:41.885 If a computer for them crashes, then they're able
00:00:41.885 --> 00:00:44.085 to spin up a new one very quickly in case your computer
00:00:44.085 --> 00:00:46.205 crashes, it has a hardware fault, then it's not very easy
00:00:46.205 --> 00:00:48.565 for you to just go and move that code somewhere else.
00:00:48.705 --> 00:00:50.765 If you have a electricity outage, if you have some sort
00:00:50.765 --> 00:00:51.925 of issue, you're logged out of your house.
00:00:51.985 --> 00:00:54.405 You know these are actual problems where you are not able
00:00:54.425 --> 00:00:55.965 to restart your computer
00:00:56.145 --> 00:00:58.805 and that can affect your service for a very small service.
00:00:58.835 --> 00:01:01.485 This is fine. Customers can understand the losses less,
00:01:01.665 --> 00:01:04.405 but if you want a professional reliable service,
00:01:04.675 --> 00:01:07.605 then you are heading more towards managed instances,
00:01:07.735 --> 00:01:09.285 which cloud solution providers give you.
00:01:09.345 --> 00:01:11.045 In our case, we are looking at three parameters,
00:01:11.045 --> 00:01:12.685 which define a good system design.
00:01:12.785 --> 00:01:14.765 The first one being the simplicity.
00:01:14.825 --> 00:01:17.925 And in our case, the simplicity will be higher if we allow
00:01:17.925 --> 00:01:19.325 someone else to manage our instance,
00:01:19.395 --> 00:01:20.725 take care of deployments.
00:01:20.745 --> 00:01:23.405 The operating system, how is the code going to run on that?
00:01:23.505 --> 00:01:24.885 Any kind of version upgrades
00:01:24.885 --> 00:01:26.725 that we want in the operating system can be taken care of.
00:01:26.725 --> 00:01:28.805 These are benefits that cloud solution providers give us.
00:01:28.825 --> 00:01:30.005 So we go with that. Fidelity
00:01:30.005 --> 00:01:32.005 or completeness to the requirements would be managed
00:01:32.005 --> 00:01:33.285 by both, so we don't care about it.
00:01:33.465 --> 00:01:36.085 And cost of implementation here is lesser, uh,
00:01:36.085 --> 00:01:37.205 when it's a managed service
00:01:37.205 --> 00:01:39.685 because implementation costs are much higher than any kind
00:01:39.685 --> 00:01:41.365 of cost you are saving for tooling at.
00:01:41.365 --> 00:01:43.045 At such small scale. And even in the cloud,
00:01:43.045 --> 00:01:44.045 you have multiple solutions.
00:01:44.105 --> 00:01:46.765 So like a good technical architect, you have the approach
00:01:46.785 --> 00:01:48.365 of manual being rejected at this point
00:01:48.365 --> 00:01:49.405 because it's too complex
00:01:49.465 --> 00:01:50.965 and it's going to be expensive to implement.
00:01:50.985 --> 00:01:52.445 In the cloud solution that we have chosen,
00:01:52.625 --> 00:01:54.125 you have two major approaches.
00:01:54.265 --> 00:01:57.405 The first one is hosting a server by yourself on the cloud
00:01:57.415 --> 00:01:58.805 where many things are managed.
00:01:58.855 --> 00:02:01.125 Let's say the operating system, installation, versioning,
00:02:01.125 --> 00:02:03.525 upgrades, those things are managed, but you have to go
00:02:03.525 --> 00:02:05.525 and deploy the code by yourself on this server.
00:02:05.585 --> 00:02:07.645 If the server crashes, then you'll have to turn it on.
00:02:07.645 --> 00:02:10.485 Turning it on is easy, much easier than doing it manually,
00:02:10.545 --> 00:02:11.725 but you'll have to do it through
00:02:11.725 --> 00:02:12.805 some graphical user interface.
00:02:12.865 --> 00:02:16.205 The second approach is having the entire instance
00:02:16.205 --> 00:02:17.405 managed end to end.
00:02:17.425 --> 00:02:19.485 So all you do is write code, take this code
00:02:19.625 --> 00:02:22.365 and tell AWS that please run it on a server.
00:02:22.565 --> 00:02:23.965 I don't know what type of server it is.
00:02:24.125 --> 00:02:25.405 I don't know what is the operating system.
00:02:25.605 --> 00:02:26.845 I don't even know whether the server
00:02:26.845 --> 00:02:27.965 is currently running or not.
00:02:28.125 --> 00:02:31.045 I just want to know that when a request comes to you,
00:02:31.145 --> 00:02:33.885 you are able to respond to it within a given timeframe.
00:02:33.885 --> 00:02:35.765 Maybe within 10 seconds is acceptable.
00:02:35.925 --> 00:02:38.645 AWS takes this code and manages the execution of this code
00:02:38.745 --> 00:02:40.125 by itself, end to end, right?
00:02:40.185 --> 00:02:42.125 So you are just focused on writing code.
00:02:42.125 --> 00:02:44.685 You're not even focused on the compilation and deployment.
00:02:44.685 --> 00:02:46.245 That's the benefit. And so when it comes
00:02:46.245 --> 00:02:47.805 to server versus serverless,
00:02:47.955 --> 00:02:50.085 there's just two parameters which help us make a decision.
00:02:50.145 --> 00:02:52.925 The first one is ease of use, ease of setup, ease
00:02:52.925 --> 00:02:54.485 of scaling, ease of maintenance.
00:02:54.625 --> 00:02:55.925 All of these are a positive.
00:02:55.925 --> 00:02:58.045 For serverless, it's very easy to scale.
00:02:58.045 --> 00:02:59.830 With serverless, you don't need need to care about
00:02:59.830 --> 00:03:01.005 how AWS is scaling.
00:03:01.115 --> 00:03:03.485 It's going to scale up if the number requests increase.
00:03:03.505 --> 00:03:04.685 So if more customers come,
00:03:04.685 --> 00:03:06.205 then you have more compute capacity
00:03:06.205 --> 00:03:07.245 automatically assigned to you.
00:03:07.295 --> 00:03:08.485 Let's say after the value sale
00:03:08.485 --> 00:03:10.165 or a new year sale, you have the number
00:03:10.165 --> 00:03:11.685 of customers dramatically reduced.
00:03:11.685 --> 00:03:13.125 You don't have to pay for that capacity.
00:03:13.365 --> 00:03:14.885 AWS is not going to charge you.
00:03:14.915 --> 00:03:16.645 They're internally going to manage it,
00:03:16.705 --> 00:03:19.365 and you as a business person don't need to care about it.
00:03:19.385 --> 00:03:20.565 So this is a clear positive.
00:03:20.565 --> 00:03:21.965 For serverless, there are two small
00:03:21.965 --> 00:03:23.405 drawbacks to serverless technologies.
00:03:23.405 --> 00:03:25.805 These small ones become really large as your app skills,
00:03:25.945 --> 00:03:27.925 but at this point, because your app is really small,
00:03:27.985 --> 00:03:29.445 the drawbacks are also quite small.
00:03:29.455 --> 00:03:30.925 First one is efficiency.
00:03:30.985 --> 00:03:32.285 If you are paying $10
00:03:32.585 --> 00:03:35.525 for 10,000 requests in a serverless architecture, maybe
00:03:35.635 --> 00:03:37.805 with a managed instance, you can do with $5.
00:03:37.995 --> 00:03:40.005 Managed instances are usually cheaper
00:03:40.225 --> 00:03:44.005 or can manage more requests for the same amount of money.
00:03:44.105 --> 00:03:46.725 The second point is serverless can sometimes be less
00:03:46.735 --> 00:03:48.925 responsive because AWS takes some time
00:03:48.925 --> 00:03:50.285 to scale up and scale down.
00:03:50.465 --> 00:03:52.765 You may be able to manually do this job better.
00:03:52.945 --> 00:03:54.045 So during a Diwali sale
00:03:54.045 --> 00:03:55.605 or a new year sale, you know that there's a,
00:03:55.605 --> 00:03:56.765 a rush of incoming requests.
00:03:56.905 --> 00:03:58.485 You pre-book capacity,
00:03:58.545 --> 00:03:59.765 and when the requests come in,
00:03:59.765 --> 00:04:01.485 there's no delay, you know, low latency.
00:04:01.585 --> 00:04:03.605 But with the serverless piece of technology,
00:04:03.605 --> 00:04:05.085 when the requests come in, that's when
00:04:05.085 --> 00:04:06.205 aw WS is going to react.
00:04:06.225 --> 00:04:07.605 And so by the time it reacts
00:04:07.605 --> 00:04:09.805 and gives responses, customers may be held
00:04:09.865 --> 00:04:11.925 and they may not like that and drop off.
00:04:12.025 --> 00:04:14.325 The chance of either of this happening in a low volume,
00:04:14.695 --> 00:04:16.005 small business is very low.
00:04:16.025 --> 00:04:18.525 So at this point we will head with serverless technology.
00:04:18.555 --> 00:04:19.965 When we go for managed servers,
00:04:19.965 --> 00:04:21.485 we will look at scaling in more detail.
00:04:21.545 --> 00:04:22.965 But right now your business is happy.
00:04:23.105 --> 00:04:24.005 We are going ahead with this. 