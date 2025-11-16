## Chapters
* 00:15 - Payment Failures
* 00:49 - Logging and Observability
* 03:27 - Fault Tolerance
* 06:45 - Graceful Degradation

## Transcript
00:00:00.065 --> 00:00:01.605 At this point, you deploy your website
00:00:01.705 --> 00:00:02.965 and things seem to be going fine.
00:00:02.995 --> 00:00:06.365 Your webpages look nice, your orders API is integrated
00:00:06.365 --> 00:00:09.005 with Shopify, and you have a lot of customers
00:00:09.005 --> 00:00:10.325 who are coming, registering, logging in.
00:00:10.325 --> 00:00:11.925 Everything looks good, and the founder
00:00:11.925 --> 00:00:13.205 thanks you and goes away.
00:00:13.205 --> 00:00:14.525 But within a week they come back
00:00:14.525 --> 00:00:16.525 and they say that, you know, in the last week I have had a
00:00:16.525 --> 00:00:19.125 lot of orders and many of them did not go
00:00:19.245 --> 00:00:20.565 through the payment gateway failed.
00:00:20.565 --> 00:00:23.245 Could you help me debug these issues as an engineer?
00:00:23.265 --> 00:00:24.765 Now, your first task is
00:00:24.765 --> 00:00:27.205 to figure out why is the payment gateway failing so much?
00:00:27.275 --> 00:00:29.965 It's possible that the payment gateway gives you a agreement
00:00:30.035 --> 00:00:32.805 that only 98% of my payments on average will pass.
00:00:32.865 --> 00:00:34.725 2% are expected to fail. You see the metrics?
00:00:34.745 --> 00:00:37.565 You see that yes, 2% of the payments have failed,
00:00:37.585 --> 00:00:39.405 so things seem fine on the payment gateway side.
00:00:39.505 --> 00:00:41.285 The actual problem is that the founder
00:00:41.465 --> 00:00:43.765 or the customer support team is not able
00:00:43.765 --> 00:00:45.325 to address issues quick enough.
00:00:45.325 --> 00:00:46.645 They're not able to debug
00:00:46.745 --> 00:00:48.725 or find the root cause of problems quickly.
00:00:48.905 --> 00:00:51.485 So here you have two major things that you want to do.
00:00:51.545 --> 00:00:54.165 The first one is whenever you get a request in your system,
00:00:54.225 --> 00:00:55.565 you want to log that request.
00:00:55.665 --> 00:00:57.405 If there are any important operations
00:00:57.405 --> 00:00:59.765 that happen in the system, which are prone to failure,
00:00:59.975 --> 00:01:01.485 let's say a database entry,
00:01:01.545 --> 00:01:03.885 or you are talking to another system with that request,
00:01:03.945 --> 00:01:04.965 you log that event.
00:01:05.105 --> 00:01:07.285 And finally, when you give a response to that request,
00:01:07.305 --> 00:01:08.645 the original request, you log the
00:01:08.845 --> 00:01:10.005 response with the request id.
00:01:10.005 --> 00:01:12.525 This gives any distributed system the capability
00:01:12.625 --> 00:01:14.885 to trace a request from start to finish.
00:01:15.065 --> 00:01:17.205 The benefit of this is if a customer comes to you
00:01:17.205 --> 00:01:18.885 and says, my email ID is so and so,
00:01:18.885 --> 00:01:20.405 and you tell me what happened with my order,
00:01:20.625 --> 00:01:22.725 you can quickly dig into the database table,
00:01:22.795 --> 00:01:25.765 find the order id, which is corresponding to that email id,
00:01:25.765 --> 00:01:28.045 and now with that order id, you are able to go
00:01:28.045 --> 00:01:30.445 through your logs and do a regular expression check.
00:01:30.445 --> 00:01:32.125 This is standard engineering practice.
00:01:32.275 --> 00:01:34.005 It's just considered a best practice
00:01:34.005 --> 00:01:35.645 for logging since this is another
00:01:35.645 --> 00:01:36.725 operation that you have to do.
00:01:36.745 --> 00:01:38.925 You have to manage cloud solution providers take
00:01:38.925 --> 00:01:40.045 care of this to some extent.
00:01:40.045 --> 00:01:42.565 There is something called Amazon CloudWatch, GCP
00:01:42.565 --> 00:01:44.165 and Azure also have similar solutions.
00:01:44.165 --> 00:01:47.165 CloudWatch can take your logs as events from your system
00:01:47.225 --> 00:01:49.805 or system in a distributed store, a central store,
00:01:49.805 --> 00:01:51.485 and then you'll be able to query these logs
00:01:51.485 --> 00:01:52.565 with regex expressions.
00:01:52.785 --> 00:01:54.925 All of the things that I just said are already managed
00:01:54.925 --> 00:01:55.965 by CloudWatch because it's
00:01:55.965 --> 00:01:57.005 such a common engineering pattern.
00:01:57.035 --> 00:01:58.885 This is probably the first thing that you want to suggest.
00:01:58.945 --> 00:02:01.325 The second thing you want to suggest is something called
00:02:01.355 --> 00:02:04.325 observability, which means you are able to see
00:02:04.385 --> 00:02:05.725 how well the system is performing.
00:02:05.725 --> 00:02:09.005 Now, imagine that the founder expects on a daily basis sales
00:02:09.005 --> 00:02:10.405 to be something around 100
00:02:10.665 --> 00:02:12.045 and on a particular day they see
00:02:12.045 --> 00:02:13.325 that the sales has dropped down to 10.
00:02:13.325 --> 00:02:14.965 They want to know about this very quickly.
00:02:14.995 --> 00:02:17.365 They want to know about it as quickly as they possibly can.
00:02:17.465 --> 00:02:19.925 So what you can do for them is build a dashboard,
00:02:20.015 --> 00:02:22.605 which shows them the number of sales, the number of visits,
00:02:22.705 --> 00:02:24.285 the number of registrations early,
00:02:24.465 --> 00:02:26.325 and just looking at it visually, the founder
00:02:26.465 --> 00:02:29.685 or the person who's in the data analytics team can tell
00:02:29.685 --> 00:02:31.365 whether something is off or not.
00:02:31.505 --> 00:02:33.845 So they can detect anomalies manually at this time.
00:02:33.985 --> 00:02:36.165 For a startup, we will be looking at observability
00:02:36.225 --> 00:02:38.405 and anomaly detection in more detail later.
00:02:38.625 --> 00:02:40.325 So you can check out that chapter in the description.
00:02:40.465 --> 00:02:41.925 For now, just keep things simple.
00:02:42.065 --> 00:02:43.485 You have dashboards and graphs
00:02:43.535 --> 00:02:45.805 where you can visually see if things are going wrong.
00:02:45.825 --> 00:02:48.245 And again, over here, instead of building the solution
00:02:48.245 --> 00:02:50.285 by yourself, you might use an existing solution.
00:02:50.385 --> 00:02:52.925 So Google Analytics is something which gives
00:02:52.945 --> 00:02:54.125 you all of this inbuilt.
00:02:54.125 --> 00:02:56.965 You may also go for paid solutions, which are Power BI
00:02:57.225 --> 00:02:58.405 or Tableau for a startup.
00:02:58.415 --> 00:03:01.405 Again, Google Analytics, a free solution is usually enough
00:03:01.545 --> 00:03:03.725 for later on when you have scaled up a bit.
00:03:03.725 --> 00:03:05.565 You can have your own custom dashboards
00:03:05.625 --> 00:03:07.565 or you can go for these analytics solutions.
00:03:07.725 --> 00:03:11.285 AWS, I think does not have an inbuilt analytics solution,
00:03:11.305 --> 00:03:12.565 but you can of course check it out.
00:03:12.565 --> 00:03:14.365 And it's the same with any other cloud solution provider,
00:03:14.385 --> 00:03:16.285 but any cloud solution provider will give
00:03:16.285 --> 00:03:17.525 you an integration.
00:03:17.665 --> 00:03:21.285 So a way to emit events from your servers to a database,
00:03:21.335 --> 00:03:24.165 which is going to be having dashboards built on top of it.
00:03:24.265 --> 00:03:26.885 So we have tried to solve a problem quickly
00:03:26.915 --> 00:03:27.925 when it has occurred.
00:03:28.025 --> 00:03:30.525 Now comes the engineering challenge of making sure
00:03:30.525 --> 00:03:31.605 that problems don't occur.
00:03:31.605 --> 00:03:32.725 Prevention is better than cure.
00:03:32.825 --> 00:03:34.245 We will instead of reacting now,
00:03:34.415 --> 00:03:36.925 avoid the problem altogether by doing some sort
00:03:36.925 --> 00:03:38.205 of system design analysis.
00:03:38.225 --> 00:03:40.045 On this diagram right now, what you're able
00:03:40.045 --> 00:03:41.885 to see is the existing system
00:03:42.035 --> 00:03:44.285 with several black box integrations.
00:03:44.465 --> 00:03:46.605 You can see Shopify is there. You can see PayPal is there.
00:03:46.625 --> 00:03:47.925 You can see also Stripe,
00:03:47.925 --> 00:03:49.645 which is maybe a backup payment gateway
00:03:49.645 --> 00:03:50.885 that the founder has kept,
00:03:50.905 --> 00:03:53.325 and you can see that there is a CDN solution,
00:03:53.375 --> 00:03:55.245 which is serving the front end.
00:03:55.305 --> 00:03:57.805 You have a file system, which is Amazon S3 for us,
00:03:57.945 --> 00:03:59.605 and you have the server in the center.
00:03:59.755 --> 00:04:01.645 It's a single server. We are using a monolith
00:04:01.645 --> 00:04:04.085 because you know you don't really have that many APIs,
00:04:04.135 --> 00:04:05.205 expos, and microservice
00:04:05.205 --> 00:04:06.565 architecture's not making sense right now.
00:04:06.615 --> 00:04:08.565 We'll get into that a little later. Why or why not?
00:04:08.565 --> 00:04:09.485 We should go over that. But
00:04:09.485 --> 00:04:10.605 this is the architecture diagram.
00:04:10.665 --> 00:04:11.725 Now, looking at this diagram,
00:04:11.985 --> 00:04:14.925 can you tell me any crucial points in this system,
00:04:15.095 --> 00:04:17.725 which on failure will fail the entire system?
00:04:17.725 --> 00:04:19.405 Okay, so you're looking at these components.
00:04:19.545 --> 00:04:20.965 If I remove one of these components,
00:04:20.985 --> 00:04:23.165 or if I remove one of the wires which are connecting these
00:04:23.165 --> 00:04:24.365 components, you know the API
00:04:24.365 --> 00:04:25.605 requests which are happening between them.
00:04:25.705 --> 00:04:27.885 If they start failing, if the network stops,
00:04:27.885 --> 00:04:29.405 then the entire system collapses.
00:04:29.545 --> 00:04:30.685 Can you find such points?
00:04:30.905 --> 00:04:32.245 If your practice at this,
00:04:32.345 --> 00:04:34.805 you are probably finding points all around, and it's true.
00:04:34.945 --> 00:04:37.445 If the CDN solution that we have fails,
00:04:37.555 --> 00:04:39.005 then our webpages won't be served
00:04:39.065 --> 00:04:40.205 and we won't have any orders,
00:04:40.225 --> 00:04:41.765 we won't have any registration, nothing will work.
00:04:41.785 --> 00:04:43.325 We have a server. If our server
00:04:43.515 --> 00:04:44.965 crashes, everything's going to fail.
00:04:44.965 --> 00:04:46.885 If we are going with the serverless architecture, the chance
00:04:46.885 --> 00:04:48.365 of that happening is low as we get to.
00:04:48.425 --> 00:04:51.645 But if AWS has a problem, we have a problem. What else?
00:04:51.775 --> 00:04:54.085 Every integration that we have, whether it's Shopify,
00:04:54.085 --> 00:04:55.365 PayPal, stripe, anything.
00:04:55.425 --> 00:04:56.845 If it's an external integration,
00:04:56.985 --> 00:04:58.445 you have an external dependency,
00:04:58.505 --> 00:05:00.045 and if it is in the critical path,
00:05:00.045 --> 00:05:01.965 you have a critical external dependency.
00:05:02.065 --> 00:05:04.205 If they fail, then your critical path
00:05:04.305 --> 00:05:05.485 or your business shuts down.
00:05:05.665 --> 00:05:08.485 At this point, as an engineer, your primary job is
00:05:08.485 --> 00:05:11.565 to make sure that things continue working despite problems.
00:05:11.785 --> 00:05:14.645 If there's a bridge and one of the important parts
00:05:14.645 --> 00:05:16.165 of the bridge is blown up, the rest
00:05:16.165 --> 00:05:17.325 of the bridge shouldn't collapse.
00:05:17.585 --> 00:05:19.085 It should wastefully degrade,
00:05:19.145 --> 00:05:20.805 or it should actually continue holding.
00:05:20.805 --> 00:05:22.805 That's your job as an engineer, even in software systems.
00:05:22.905 --> 00:05:25.565 So how do we do this when we could have backups?
00:05:25.825 --> 00:05:29.605 If your database is out, then if you have a backup database,
00:05:29.605 --> 00:05:31.045 things will be working smoothly.
00:05:31.225 --> 00:05:32.725 The second thing is, when it comes
00:05:32.725 --> 00:05:35.325 to serverless architecture, if your server crashes,
00:05:35.605 --> 00:05:38.405 AWS will manage the restart of that server
00:05:38.585 --> 00:05:41.005 and managing the new requests automatically
00:05:41.035 --> 00:05:42.045 without you coming in.
00:05:42.045 --> 00:05:44.205 So this is one of the benefits of cloud solution provider.
00:05:44.235 --> 00:05:46.885 They manage reliability by themselves.
00:05:46.915 --> 00:05:49.165 Similarly, CloudFront, it's highly unlikely
00:05:49.165 --> 00:05:50.565 that CloudFront is going to go down.
00:05:50.595 --> 00:05:52.845 This is also one of the reasons why most people want
00:05:52.845 --> 00:05:55.205 to just move everything to a cloud solution provider under
00:05:55.205 --> 00:05:56.565 one umbrella because the thing
00:05:56.565 --> 00:05:58.125 that they're known for is reliability.
00:05:58.185 --> 00:06:00.125 If you have your technologies there, the chances
00:06:00.125 --> 00:06:01.165 of things failing are low.
00:06:01.165 --> 00:06:03.765 What about external integrations? What if PayPal fails?
00:06:03.905 --> 00:06:05.365 You could have Stripe also.
00:06:05.465 --> 00:06:07.525 You could have raise pay if raise pay fails.
00:06:07.525 --> 00:06:10.205 Maybe you have phone pay, maybe you have some other company.
00:06:10.205 --> 00:06:12.085 You're not just looking at technical solutions.
00:06:12.085 --> 00:06:13.485 You're looking at practical backup
00:06:13.485 --> 00:06:15.125 solutions in this architecture.
00:06:15.145 --> 00:06:17.685 But what if Shopify fails while your business stops?
00:06:17.835 --> 00:06:19.965 This is called a single point of failure.
00:06:20.145 --> 00:06:21.605 If there is a problem with Shopify,
00:06:21.605 --> 00:06:23.245 your business is going to stop.
00:06:23.345 --> 00:06:26.565 So even here, you can have maybe multiple providers,
00:06:26.965 --> 00:06:28.765 multiple order takers and delivery systems.
00:06:28.905 --> 00:06:30.685 But the more robust you try to make a system,
00:06:30.825 --> 00:06:32.605 the more involved it is for engineers
00:06:32.605 --> 00:06:34.565 to implement these backups.
00:06:34.565 --> 00:06:36.365 Right? So you have multiple integrations
00:06:36.465 --> 00:06:38.605 for payment gateways, multiple integrations for orders,
00:06:39.085 --> 00:06:41.125 multiple integrations for maybe delivery service providers.
00:06:41.125 --> 00:06:42.485 That's a lot of work that you have to do,
00:06:42.485 --> 00:06:43.765 and if any of the vendors fail,
00:06:43.765 --> 00:06:45.205 then you are back to square one.
00:06:45.205 --> 00:06:47.405 So here you may choose to have graceful degradation,
00:06:47.415 --> 00:06:50.605 which is if Shopify fails, you show on the front page
00:06:50.605 --> 00:06:52.965 of your fancy T-shirts io website
00:06:52.995 --> 00:06:54.725 that we are no longer able to serve you.
00:06:54.745 --> 00:06:57.605 We are sorry and we hope to resolve the issue very quickly.
00:06:57.865 --> 00:06:59.925 Now this is a good error message,
00:06:59.925 --> 00:07:01.125 which is right there in the front.
00:07:01.265 --> 00:07:03.365 In some cases, maybe your server is having issues
00:07:03.365 --> 00:07:04.645 or your database is having issues.
00:07:04.835 --> 00:07:06.445 It's best to propagate that error
00:07:06.505 --> 00:07:07.925 to a sensible message on the client
00:07:07.925 --> 00:07:09.485 that our database is failing.
00:07:09.485 --> 00:07:12.165 Please try and sometime so that when they take that error
00:07:12.165 --> 00:07:13.325 and send it to your customer team,
00:07:13.435 --> 00:07:15.125 it's easily readable and trackable.
00:07:15.145 --> 00:07:17.365 Now you have made the changes around logging and monitoring.
00:07:17.365 --> 00:07:19.005 Your founder is reasonably happy.
00:07:19.185 --> 00:07:21.485 At least the costs of managing support tickets has gone
00:07:21.485 --> 00:07:21.645 down. 