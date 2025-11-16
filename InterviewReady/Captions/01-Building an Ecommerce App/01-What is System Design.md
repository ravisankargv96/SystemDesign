## Chapters
* 00:00 - Learning Objectives
* 00:48 - Evaluation Metrics
* 01:15 - Example: Ecommerce App
* 04:31 - Basic Design

## Transcript
00:00:00.065 --> 00:00:02.205 In this series, we'll be talking about distributed systems
00:00:02.425 --> 00:00:04.725 and how they're designed to meet business requirements.
00:00:04.835 --> 00:00:06.805 When I say design, I mean the placement
00:00:06.825 --> 00:00:08.885 of different components in a distributed system
00:00:08.985 --> 00:00:10.445 and how they interact with each other.
00:00:10.575 --> 00:00:12.205 We'll be demonstrating this with an example
00:00:12.225 --> 00:00:13.525 of an e-commerce website.
00:00:13.525 --> 00:00:15.045 This is a website where users can view
00:00:15.045 --> 00:00:16.405 and purchase listed products.
00:00:16.625 --> 00:00:18.085 The example will help us understand
00:00:18.085 --> 00:00:20.165 how real world systems use design patterns
00:00:20.165 --> 00:00:21.485 and tools to serve customers.
00:00:21.545 --> 00:00:22.565 If you're working in a startup
00:00:22.745 --> 00:00:24.125 or a side project, you'll see
00:00:24.125 --> 00:00:26.405 that the course reflects real life scenarios,
00:00:26.425 --> 00:00:27.525 and if you're a software engineer
00:00:27.525 --> 00:00:29.645 or technical manager, these learnings will help you make
00:00:29.645 --> 00:00:30.725 good technical decisions.
00:00:30.865 --> 00:00:32.365 By the end of the series, you'll know how
00:00:32.365 --> 00:00:33.405 to design a distributed system.
00:00:33.425 --> 00:00:36.005 You also know the common design patterns, algorithms,
00:00:36.145 --> 00:00:38.365 and tools that help power a distributed system.
00:00:38.365 --> 00:00:40.485 Finally, you'll be able to effectively communicate your
00:00:40.485 --> 00:00:41.725 ideas in a team meeting
00:00:41.945 --> 00:00:43.325 or in a design interview,
00:00:43.325 --> 00:00:45.205 which will help your team make better decisions
00:00:45.265 --> 00:00:47.245 and will help you cover more ground in design.
00:00:47.245 --> 00:00:48.845 Interviews. All system design is
00:00:48.845 --> 00:00:50.165 evaluated using three metrics.
00:00:50.625 --> 00:00:52.005 One, the simplicity of the design.
00:00:52.005 --> 00:00:55.005 Is the design understandable? Can we change it if necessary?
00:00:55.225 --> 00:00:57.845 Two, fidelity, fidelity to the original requirements.
00:00:58.105 --> 00:01:00.645 Are all the requirements being met by the given design
00:01:00.665 --> 00:01:02.005 and three, cost effectiveness?
00:01:02.185 --> 00:01:04.685 Is this design affordable? Is it feasible?
00:01:04.715 --> 00:01:06.885 Here we look at the implementation costs of the design
00:01:06.945 --> 00:01:08.045 and any tooling that we have
00:01:08.045 --> 00:01:09.285 to purchase throughout the series.
00:01:09.355 --> 00:01:11.965 I'll encourage you to evaluate our design decisions
00:01:12.255 --> 00:01:13.445 based on these three metrics.
00:01:13.785 --> 00:01:15.005 All the best. Let's begin.
00:01:15.015 --> 00:01:17.085 Let's take an example of an e-commerce website,
00:01:17.085 --> 00:01:19.125 and I'll be building a small background story so
00:01:19.125 --> 00:01:20.165 that things make sense.
00:01:20.345 --> 00:01:22.605 We will be tying back to the story from time to time
00:01:23.125 --> 00:01:25.325 whenever we are introducing any new product requirement,
00:01:25.325 --> 00:01:26.445 any new business requirement.
00:01:26.445 --> 00:01:28.525 There may be times when we want to cut down on costs
00:01:28.585 --> 00:01:29.885 or make the design more extensible,
00:01:29.945 --> 00:01:31.925 but at all times we'll be using the same example
00:01:31.945 --> 00:01:33.085 of a e-commerce website.
00:01:33.085 --> 00:01:34.725 So let's begin. Let's say you meet a
00:01:34.725 --> 00:01:35.805 friend who sells T-shirts.
00:01:35.805 --> 00:01:37.365 Currently, they're selling T-shirts either
00:01:37.365 --> 00:01:38.845 through social media or offline,
00:01:38.865 --> 00:01:39.885 and what they're really looking
00:01:39.905 --> 00:01:42.045 to do is build an online presence.
00:01:42.115 --> 00:01:44.085 They should be able to sell t-shirts online.
00:01:44.185 --> 00:01:46.245 So they come to you as a technical expert
00:01:46.305 --> 00:01:49.325 and ask you what they should do to sell t-shirts online.
00:01:49.765 --> 00:01:51.685 Remember the three metrics? You want this to be simple.
00:01:51.865 --> 00:01:54.085 You want it to cover all requirements,
00:01:54.185 --> 00:01:55.725 and you want it to be cost effective.
00:01:55.825 --> 00:01:59.005 So the best solution is an existing solution.
00:01:59.005 --> 00:02:00.765 Maybe you can sell your T-shirts on Amazon.
00:02:00.825 --> 00:02:03.085 The person tells you that Amazon is not the best choice
00:02:03.085 --> 00:02:04.965 because they're not able to customize the
00:02:04.965 --> 00:02:06.085 look and feel of their shop.
00:02:06.085 --> 00:02:08.165 Things are sold as products on Amazon,
00:02:08.225 --> 00:02:10.845 and the recommendations may be completely different from
00:02:10.915 --> 00:02:11.925 what they want to recommend.
00:02:11.925 --> 00:02:13.045 If a person is buying a T-shirt,
00:02:13.045 --> 00:02:14.165 so at this point you tell them,
00:02:14.385 --> 00:02:17.485 why don't you host your T-shirt shop over Shopify?
00:02:17.505 --> 00:02:18.925 It gives you reasonable control.
00:02:19.025 --> 00:02:20.445 You have your own webpage,
00:02:20.545 --> 00:02:23.005 and there are lots of integrations that Shopify gives you
00:02:23.025 --> 00:02:24.925 for payment providers and delivery providers.
00:02:24.955 --> 00:02:27.485 Your friend checks out. Shopify looks at all the features
00:02:27.505 --> 00:02:28.925 and says, this is wonderful.
00:02:29.035 --> 00:02:31.245 I'll go ahead with it. You're looking at the core principle
00:02:31.245 --> 00:02:33.565 of a software architect is to solve the business problem.
00:02:33.715 --> 00:02:35.965 It's not to create a technical solution,
00:02:35.985 --> 00:02:37.885 but to actually solve the customer's problem.
00:02:38.105 --> 00:02:40.485 If the solution already exists, do
00:02:40.485 --> 00:02:41.925 what is already out there.
00:02:42.105 --> 00:02:43.525 Use the existing solution in three
00:02:43.525 --> 00:02:44.565 months time, your friend comes back.
00:02:44.565 --> 00:02:46.245 They say that Shopify is doing very well,
00:02:46.495 --> 00:02:49.125 their business is making around a hundred sales per day,
00:02:49.145 --> 00:02:50.725 but they have some serious issues.
00:02:50.865 --> 00:02:52.405 Number one, whenever they're looking
00:02:52.465 --> 00:02:55.525 for order details on Shopify, they're not able
00:02:55.525 --> 00:02:57.245 to get a detailed log of
00:02:57.425 --> 00:03:00.125 how the T-shirt was taken from order to delivery.
00:03:00.135 --> 00:03:02.405 Often they get customer calls saying, can you tell me
00:03:02.405 --> 00:03:03.885 where the T-shirt is right now?
00:03:04.085 --> 00:03:06.565 I mean, is it delivered? And what you have to do is you have
00:03:06.565 --> 00:03:08.485 to log in to a portal, you have
00:03:08.485 --> 00:03:09.565 to check the delivery status,
00:03:09.785 --> 00:03:11.125 and then you come back to the customer
00:03:11.125 --> 00:03:12.205 and you have to manually tell them,
00:03:12.205 --> 00:03:13.765 right now it's in processing,
00:03:13.765 --> 00:03:15.205 or right now it's out for delivery,
00:03:15.265 --> 00:03:16.685 or right now it has been delivered.
00:03:16.785 --> 00:03:17.925 I'm surprised you haven't got it.
00:03:17.985 --> 00:03:19.765 The support issues are expensive
00:03:19.765 --> 00:03:22.165 because any kind of delivery tracking is difficult.
00:03:22.265 --> 00:03:24.325 The second issue that customers are saying is
00:03:24.325 --> 00:03:26.205 that when they want international orders,
00:03:26.355 --> 00:03:29.045 when they are looking to pay through an international card,
00:03:29.155 --> 00:03:30.725 your payment gateway is not working.
00:03:30.825 --> 00:03:32.565 So let's say they're delivering the T-shirt
00:03:32.565 --> 00:03:33.845 to a person in your country,
00:03:34.145 --> 00:03:36.565 but they're ordering the T-shirt from outside your country,
00:03:36.745 --> 00:03:38.445 so they have a different credit card
00:03:38.445 --> 00:03:39.845 or debit card that they want to use.
00:03:39.875 --> 00:03:42.565 Your payment gateway is refusing to accept this currency.
00:03:42.705 --> 00:03:45.565 So it would be really nice if the payment gateway could be
00:03:45.565 --> 00:03:46.605 either changed
00:03:46.705 --> 00:03:49.405 and that's stopping let's say 10 to 20% of all sales.
00:03:49.585 --> 00:03:52.165 At this point. Again, you use your basic system design
00:03:52.165 --> 00:03:54.925 principles and say, let me not design the system.
00:03:55.185 --> 00:03:57.005 Is it possible for Shopify
00:03:57.145 --> 00:03:59.205 or any of its partners who are integrated
00:03:59.205 --> 00:04:00.445 with it to solve this problem?
00:04:00.625 --> 00:04:01.765 Can you create a support ticket
00:04:01.865 --> 00:04:03.525 and talk to the payment gateway provider?
00:04:03.635 --> 00:04:05.085 Have them accept different payments.
00:04:05.185 --> 00:04:07.325 The business person now says, I've already done that.
00:04:07.325 --> 00:04:09.405 They refuse to accept international cards.
00:04:09.505 --> 00:04:11.805 Unless you have your own website, any integration
00:04:11.805 --> 00:04:13.325 with Shopify is not going to work here.
00:04:13.395 --> 00:04:15.085 It's the same problem with the delivery provider.
00:04:15.155 --> 00:04:17.245 Both of these problems are going to last forever
00:04:17.545 --> 00:04:21.045 unless you are able to move out of these providers,
00:04:21.185 --> 00:04:22.845 the payment provider and the delivery provider.
00:04:22.895 --> 00:04:25.285 Since Shopify is not satisfying your requirements
00:04:25.305 --> 00:04:27.685 and has no clear deadline, when they will,
00:04:27.945 --> 00:04:30.725 you create a technical wrapper, a solution
00:04:30.825 --> 00:04:32.085 to solve these two problems.
00:04:32.235 --> 00:04:34.125 This is where system design begins.
00:04:34.125 --> 00:04:35.965 This is where most businesses start.
00:04:36.145 --> 00:04:37.965 You have a set of integrations.
00:04:37.965 --> 00:04:39.885 You have an existing solution which you're using now.
00:04:39.885 --> 00:04:42.765 You want to extract functionalities away from it,
00:04:42.815 --> 00:04:44.005 bring in more control
00:04:44.145 --> 00:04:46.405 and lesser bugs in your new implementation
00:04:46.465 --> 00:04:48.645 and meet necessary business requirements in
00:04:48.645 --> 00:04:49.805 your new implementation.
00:04:49.865 --> 00:04:51.445 At a high level, what do you really need?
00:04:51.545 --> 00:04:53.445 You need an integration with Shopify such
00:04:53.445 --> 00:04:56.045 that when a user wants to make a payment, they come
00:04:56.045 --> 00:04:57.125 to your custom page.
00:04:57.225 --> 00:04:59.205 In this page, you may have a different payment provider
00:04:59.265 --> 00:05:00.485 who allows international cards.
00:05:00.625 --> 00:05:02.765 For example, you may give the options of raise, pay, PayPal
00:05:02.905 --> 00:05:04.325 and Stripe in this payment page.
00:05:04.425 --> 00:05:07.445 The other thing you want is a page for delivery tracking.
00:05:07.625 --> 00:05:09.925 So once a payment has been completed,
00:05:09.925 --> 00:05:12.845 once an order has completed, once an order has been booked,
00:05:12.985 --> 00:05:16.405 you want a page where users can enter their user id,
00:05:16.405 --> 00:05:18.005 maybe they can enter the order ID,
00:05:18.025 --> 00:05:19.445 and they can see the delivery status.
00:05:19.705 --> 00:05:22.485 So let's draw this out as a bunch of block diagrams.
00:05:22.635 --> 00:05:24.005 Most of these are black boxes.
00:05:24.145 --> 00:05:25.405 You don't know how Shopify works.
00:05:25.405 --> 00:05:27.805 You don't know how PayPal or raise a pay works,
00:05:27.905 --> 00:05:30.565 but you do need to know how your system is going to interact
00:05:30.565 --> 00:05:33.245 with these existing systems to satisfy customer needs.
00:05:33.385 --> 00:05:35.085 So when a customer is looking to pay,
00:05:35.225 --> 00:05:38.005 you have this entry in Shopify, which tells you where
00:05:38.005 --> 00:05:39.085 to redirect the customer.
00:05:39.145 --> 00:05:40.645 So that's going to be your payment page.
00:05:40.665 --> 00:05:42.685 And when the customer is looking to track the status
00:05:42.705 --> 00:05:45.045 of an order, you have the link entered in Shopify.
00:05:45.065 --> 00:05:47.245 If they click that and your delivery tracking page
00:05:47.255 --> 00:05:48.325 opens up, okay, that's it.
00:05:48.325 --> 00:05:50.725 That's all you need. Now, if you're going to manage payments
00:05:50.865 --> 00:05:52.165 and delivery, then you need
00:05:52.165 --> 00:05:54.765 to store some data in your system for a particular order.
00:05:55.025 --> 00:05:56.325 Did the payment really go through?
00:05:56.395 --> 00:05:58.525 This information will need to be stored in your system.
00:05:58.625 --> 00:06:00.285 The second thing is for an order,
00:06:00.515 --> 00:06:01.805 what is the delivery state?
00:06:01.945 --> 00:06:04.885 You can only display this on the page if you have the
00:06:04.885 --> 00:06:06.325 information stored somewhere in your server.
00:06:06.425 --> 00:06:08.445 So the page is going to be asking your server
00:06:08.665 --> 00:06:10.365 for information and your server has
00:06:10.365 --> 00:06:11.765 to give the page that information.
00:06:11.865 --> 00:06:13.565 And the way in which this interaction happens
00:06:13.835 --> 00:06:16.565 between a mobile device, which has a browser running
00:06:16.585 --> 00:06:18.085 or a desktop which has a browser running
00:06:18.265 --> 00:06:21.165 and a server is called an API application
00:06:21.165 --> 00:06:22.205 programmable interface.
00:06:22.275 --> 00:06:23.285 This basically means
00:06:23.285 --> 00:06:26.765 that if you send the server information in a particular way,
00:06:26.825 --> 00:06:28.565 you can expect data to be returned
00:06:28.565 --> 00:06:29.645 to you in a particular way.
00:06:29.645 --> 00:06:31.005 And that's why this is called a call contract.
00:06:31.005 --> 00:06:33.725 An API contract defines exactly what kind
00:06:33.805 --> 00:06:35.845 of information needs to be sent to the server
00:06:36.025 --> 00:06:38.205 to get a response in a particular format.
00:06:38.425 --> 00:06:39.565 In your case, you are looking
00:06:39.585 --> 00:06:41.605 for delivery information and payment information.
00:06:41.705 --> 00:06:43.685 If you give the server the order ID,
00:06:43.685 --> 00:06:46.005 right the right spelling of order under id,
00:06:46.005 --> 00:06:48.245 and then you have the order ID given in double codes,
00:06:48.245 --> 00:06:49.845 this is A-J-S-O-N format, you are going
00:06:49.845 --> 00:06:51.205 to get a response telling you
00:06:51.205 --> 00:06:53.485 what is the payment status for that order right now?
00:06:53.485 --> 00:06:55.725 If you display this on the webpage, the customer is happy
00:06:55.725 --> 00:06:57.645 because they can see if their order passed or failed.
00:06:57.825 --> 00:06:59.845 If it failed, then they can connect with customer support.
00:06:59.865 --> 00:07:00.965 If it passed, things are good.
00:07:00.985 --> 00:07:03.325 So this is how the interaction between a server
00:07:03.545 --> 00:07:04.605 and a client happens.
00:07:04.875 --> 00:07:06.805 Similarly, delivery status can be managed
00:07:06.865 --> 00:07:07.885 by a different API.
00:07:07.885 --> 00:07:11.605 If you send A-J-S-O-N request to delivery status for now,
00:07:11.605 --> 00:07:12.845 just imagine that this is some sort
00:07:12.845 --> 00:07:14.045 of a port running on the server,
00:07:14.055 --> 00:07:16.805 which is taking electronic messages and izing them.
00:07:16.865 --> 00:07:19.085 The server will read this message, run a function,
00:07:19.105 --> 00:07:20.405 and finally return a response.
00:07:20.585 --> 00:07:22.965 So this is wonderful because an API basically
00:07:22.965 --> 00:07:24.045 for the server is a function.
00:07:24.185 --> 00:07:26.365 It takes some parameters as inputs
00:07:26.365 --> 00:07:27.565 and gives you an output, which is
00:07:27.565 --> 00:07:29.165 what any standard function does.
00:07:29.385 --> 00:07:31.925 So you can write the API in any language you like.
00:07:31.925 --> 00:07:34.685 You can write it in Python, you can like go in Java,
00:07:34.705 --> 00:07:36.805 and as long as the function executes successfully,
00:07:36.945 --> 00:07:38.165 the client gets a response.
00:07:38.385 --> 00:07:41.045 Now, all you need to do as a developer is just write this
00:07:41.045 --> 00:07:42.645 code, write these functions, flesh them out.
00:07:42.645 --> 00:07:45.005 Once you have them written locally, this can be notepad,
00:07:45.035 --> 00:07:47.125 this can be char, any ID that you like.
00:07:47.185 --> 00:07:49.565 You take this code, copy, paste it in a cloud server,
00:07:49.665 --> 00:07:50.845 and then you execute it.
00:07:50.865 --> 00:07:52.645 You just run that file and your server is running.
00:07:52.645 --> 00:07:54.805 If you have incoming requests, your code will execute
00:07:54.805 --> 00:07:55.885 and give back responses.
00:07:56.025 --> 00:07:57.165 That's all you need to do.
00:07:57.225 --> 00:07:59.485 And a lot of this is actually managed now
00:07:59.505 --> 00:08:00.805 by cloud solution providers.
00:08:00.805 --> 00:08:03.365 So you don't even have to do the copy pasting so much.
00:08:03.385 --> 00:08:04.605 You can write it on GitHub.
00:08:04.745 --> 00:08:06.805 And GitHub can have action runners,
00:08:06.805 --> 00:08:08.165 which are going to automatically deploy.
00:08:08.225 --> 00:08:10.405 We won't get too much into the CICD pipeline.
00:08:10.405 --> 00:08:11.765 We are looking at the high level design,
00:08:11.785 --> 00:08:13.885 but code execution is a thing that is very,
00:08:13.885 --> 00:08:16.085 very important if you want to make your life easy
00:08:16.145 --> 00:08:17.045 as a software engineer. 