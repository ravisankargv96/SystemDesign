## Chapters
* 00:00 - You are the new CTO!
* 02:00 - There be changes...
* 05:35 - What could go wrong?
* 07:04 - Decision: SMALL TEAMS
* 08:48 - Spicy Microservices!
* 12:48 - API Spaghetti

## Transcript
00:00:00.025 --> 00:00:01.565 In a few months you hear some good news.
00:00:01.825 --> 00:00:03.405 The company that you have been supporting for
00:00:03.405 --> 00:00:06.085 so long on the sidelines is now heavily funded
00:00:06.545 --> 00:00:08.365 or it's made a lot of profits
00:00:08.665 --> 00:00:12.005 and uh, they have decided to go ahead with you as the CTO.
00:00:12.005 --> 00:00:13.805 So you get the offer letter, you are very happy,
00:00:14.105 --> 00:00:16.445 you charge into the company and now you're the CTO.
00:00:16.445 --> 00:00:19.685 What they're expecting of you is to make very large impact,
00:00:20.085 --> 00:00:22.605 positive impact in the organization, you should be able
00:00:22.605 --> 00:00:24.005 to scale this small team
00:00:24.025 --> 00:00:26.205 of five engineers currently in this startup
00:00:26.505 --> 00:00:28.085 to a large organization,
00:00:28.205 --> 00:00:29.725 a large organization would be something like
00:00:29.845 --> 00:00:30.885 a hundred engineers.
00:00:30.945 --> 00:00:32.645 That's a massive, massive project.
00:00:32.865 --> 00:00:34.245 Now why are they looking for this?
00:00:34.275 --> 00:00:36.645 Well, they're looking to expand into multiple spaces.
00:00:36.955 --> 00:00:38.685 They no longer want to sell t-shirts.
00:00:38.685 --> 00:00:40.685 They want to sell uh, accessories.
00:00:40.685 --> 00:00:42.605 They want to sell t-shirts on subscriptions.
00:00:42.605 --> 00:00:44.685 So you know, every year you get a new T-shirt
00:00:44.825 --> 00:00:47.245 or maybe every month we'll be sending you a new T-shirt
00:00:47.245 --> 00:00:48.325 depending on what's trending.
00:00:48.325 --> 00:00:49.765 These are all ideas that they have.
00:00:49.835 --> 00:00:52.165 They need fast technical support
00:00:52.305 --> 00:00:53.605 and so you pick up these charters
00:00:53.705 --> 00:00:57.165 and in two months time you have expanded your existing team
00:00:57.165 --> 00:00:58.405 of five to a team of 15.
00:00:58.505 --> 00:01:00.285 So you've hired 10 new engineers.
00:01:00.505 --> 00:01:03.045 Now here are some people problems that you'll be facing
00:01:03.465 --> 00:01:05.565 and this has some technical relevance,
00:01:05.585 --> 00:01:06.925 so bear with me over here.
00:01:06.995 --> 00:01:10.085 Your team has moved from a size of five to 15, which means
00:01:10.085 --> 00:01:13.325 that all the new engineers in the team need some training,
00:01:13.555 --> 00:01:15.645 need to understand how the existing system works.
00:01:15.865 --> 00:01:17.445 The second thing is a team
00:01:17.445 --> 00:01:19.085 of 15 is very difficult to manage.
00:01:19.115 --> 00:01:21.925 What happens is you as the CTO, you attend the standups
00:01:22.025 --> 00:01:25.205 and then you start taking updates from every member.
00:01:25.345 --> 00:01:26.525 You notice that there's a lot
00:01:26.525 --> 00:01:29.245 of non-overlapping updates from person A
00:01:29.245 --> 00:01:30.445 when compared to person B.
00:01:30.445 --> 00:01:33.165 So a may working on a feature for payments
00:01:33.425 --> 00:01:34.805 to integrate another payment gateway.
00:01:34.855 --> 00:01:37.885 While we may be working on inventory management for example,
00:01:38.105 --> 00:01:40.005 how many t-shirts are currently available?
00:01:40.055 --> 00:01:41.605 These two things are rather separate.
00:01:41.675 --> 00:01:43.205 They don't have any relation with each other,
00:01:43.545 --> 00:01:45.085 but every time they need to come to the meeting.
00:01:45.185 --> 00:01:47.605 So here you notice that you know the symptom is
00:01:47.605 --> 00:01:48.845 that the pace of development has gone down
00:01:48.845 --> 00:01:49.885 and people are a bit upset.
00:01:49.885 --> 00:01:51.685 They no longer find the culture very nice.
00:01:51.825 --> 00:01:54.085 You sit down with all the team members, have a pizza party
00:01:54.225 --> 00:01:55.285 and start asking them
00:01:55.515 --> 00:01:57.565 what are the ways in which our technical
00:01:57.565 --> 00:01:58.725 team can perform well?
00:01:58.795 --> 00:02:00.485 Here you notice some problems.
00:02:00.635 --> 00:02:03.925 Firstly, all of your engineers agree that the time it takes
00:02:04.025 --> 00:02:05.245 to develop a feature
00:02:05.465 --> 00:02:07.245 and ship it is much longer than it should be.
00:02:07.245 --> 00:02:08.885 So the deployments are not frequent enough.
00:02:08.965 --> 00:02:12.045 Secondly, new engineers need tremendous amount
00:02:12.105 --> 00:02:15.565 of handholding despite us hiring very talented engineers.
00:02:15.595 --> 00:02:17.365 They need to go through a lot of code
00:02:17.365 --> 00:02:18.885 before they can start developing.
00:02:18.905 --> 00:02:21.325 And finally, when a change is being made in the system,
00:02:21.435 --> 00:02:23.565 it's difficult to have a single point of contact.
00:02:23.785 --> 00:02:25.405 For example, if you're looking at payments
00:02:25.625 --> 00:02:28.325 and you look at the number of changes in payments,
00:02:28.415 --> 00:02:31.285 every person in the team has some context around payments,
00:02:31.305 --> 00:02:33.085 but nobody is an expert at it.
00:02:33.145 --> 00:02:35.285 If you look at the commit commits, there'll be 15 people
00:02:35.285 --> 00:02:36.405 who have committed on payments.
00:02:36.465 --> 00:02:38.285 And so if you really need to understand
00:02:38.305 --> 00:02:39.765 how a particular piece of code runs,
00:02:40.025 --> 00:02:41.165 you are doing a right click.
00:02:41.225 --> 00:02:43.645 Get blame and then figuring out who should you go to.
00:02:43.645 --> 00:02:46.965 This is called coupling or lack of isolation of concerns.
00:02:46.995 --> 00:02:49.165 Everybody is trying to manage everything and
00:02:49.165 --> 00:02:51.245 therefore they're not really being experts at anything.
00:02:51.265 --> 00:02:52.765 Now these symptoms have a root cause.
00:02:52.985 --> 00:02:55.725 The basic problem is that your single system,
00:02:56.045 --> 00:02:58.605 a single server code is too complex.
00:02:59.115 --> 00:03:00.805 It's having too many people trying
00:03:00.805 --> 00:03:02.925 to change it at the same time, what probably needs
00:03:02.925 --> 00:03:05.205 to happen is that your teams have to be split up
00:03:05.265 --> 00:03:08.525 and since code usually mimics the organization structure,
00:03:08.705 --> 00:03:10.285 you will have to split up your code.
00:03:10.395 --> 00:03:11.845 Also, you don't have to do this,
00:03:11.845 --> 00:03:13.365 but it's better to do this as we'll.
00:03:13.365 --> 00:03:15.285 See why the first thing that happens if you split up your
00:03:15.285 --> 00:03:17.445 team is that your standups are shorter.
00:03:17.655 --> 00:03:19.845 There are teams now which can manage
00:03:20.145 --> 00:03:21.685 entire business functions.
00:03:21.825 --> 00:03:23.525 For example, payments can be managed
00:03:23.545 --> 00:03:24.565 by a team of five people.
00:03:24.665 --> 00:03:26.125 If you have a team size of 15,
00:03:26.275 --> 00:03:27.605 five people can manage payments.
00:03:27.615 --> 00:03:29.405 Maybe six people can manage inventory,
00:03:29.405 --> 00:03:30.645 which is a complex operation,
00:03:30.785 --> 00:03:32.045 has quite a few things happening.
00:03:32.275 --> 00:03:33.685 Support new features,
00:03:33.875 --> 00:03:36.085 just optimizing on the current algorithms,
00:03:36.385 --> 00:03:39.685 and you have four people working on analytics, emails.
00:03:39.905 --> 00:03:41.885 Any kind of communication that has to be done
00:03:41.885 --> 00:03:44.885 through dashboards or through email is managed by this team.
00:03:44.905 --> 00:03:46.485 So you have orders and payments team,
00:03:46.515 --> 00:03:48.405 inventory team and communications team.
00:03:48.435 --> 00:03:50.445 This brings in an isolation of concerns.
00:03:50.765 --> 00:03:54.525 Whenever you as the CTO want a new feature, you first decide
00:03:54.565 --> 00:03:55.765 where does this feature belong?
00:03:55.945 --> 00:03:58.245 If it belongs in any of these three teams, just give it
00:03:58.245 --> 00:03:59.805 to them and now you can follow up with
00:03:59.805 --> 00:04:00.845 that team individually.
00:04:00.845 --> 00:04:02.085 You don't have to get everyone along
00:04:02.085 --> 00:04:04.485 and say that, okay, in the standup now you tell me your
00:04:04.485 --> 00:04:05.525 update, you tell me your update,
00:04:05.625 --> 00:04:06.885 you can connect with them separately.
00:04:06.945 --> 00:04:08.165 The second thing is each
00:04:08.165 --> 00:04:11.165 of these teams can have their own deployment cycles.
00:04:11.305 --> 00:04:13.845 If you have, let's say three servers, one for each team,
00:04:13.875 --> 00:04:16.685 then whenever a team wants to deploy their code,
00:04:16.835 --> 00:04:19.565 they don't have to wait for the rest of the people's changes
00:04:19.665 --> 00:04:21.045 to be added to the main branch.
00:04:21.265 --> 00:04:23.325 You can just go ahead and deploy your code.
00:04:23.345 --> 00:04:24.605 The rest of the teams can connect
00:04:24.605 --> 00:04:26.005 with your code using API calls.
00:04:26.075 --> 00:04:27.605 Okay, we'll get into more details about
00:04:27.605 --> 00:04:29.165 how communication happens across services,
00:04:29.185 --> 00:04:32.125 but at a high level, if you had your own independent company
00:04:32.145 --> 00:04:34.725 of five engineers, then you could just hit their API
00:04:34.725 --> 00:04:36.245 and get a response and life would be good.
00:04:36.245 --> 00:04:38.085 There wouldn't be so much context needed
00:04:38.145 --> 00:04:39.485 and so much dependency on each other.
00:04:39.485 --> 00:04:42.605 Finally, each of these teams can scale up their services
00:04:42.745 --> 00:04:44.325 as required and they can choose the
00:04:44.325 --> 00:04:45.645 technologies which best suit them.
00:04:45.665 --> 00:04:47.005 For example, the email service
00:04:47.145 --> 00:04:49.885 and the dashboarding service may be a small service.
00:04:50.505 --> 00:04:52.605 It runs every hour, five emails
00:04:52.745 --> 00:04:54.645 and the dashboards are updated every half an hour.
00:04:54.665 --> 00:04:56.125 So you need a small server for this.
00:04:56.305 --> 00:04:58.365 You may be looking at a lot of pre computation,
00:04:58.385 --> 00:05:00.045 you may be looking at technologies which are
00:05:00.045 --> 00:05:03.085 around data analytics or distribution of messages.
00:05:03.145 --> 00:05:04.405 The other services don't need
00:05:04.405 --> 00:05:05.805 to have these libraries in their service.
00:05:06.105 --> 00:05:07.805 The technologies that are being used
00:05:08.185 --> 00:05:10.005 by each service may be different.
00:05:10.065 --> 00:05:11.605 You may be using different databases.
00:05:11.605 --> 00:05:13.085 Also, one team is using Postgres,
00:05:13.085 --> 00:05:14.325 the other team is using MySQL.
00:05:14.355 --> 00:05:16.165 That is possible not advisable
00:05:16.165 --> 00:05:17.565 because then you need a lot of context
00:05:17.965 --> 00:05:19.325 whenever a person moves from one team to another.
00:05:19.345 --> 00:05:21.605 But for now, you can imagine that these awesome
00:05:22.445 --> 00:05:24.485 benefits will come if you are able to isolate concerns.
00:05:24.585 --> 00:05:26.205 And so it seems to make sense
00:05:26.265 --> 00:05:28.965 to split up this large team into smaller teams.
00:05:29.155 --> 00:05:31.965 Okay? Most large organizations have a bunch of small teams
00:05:32.565 --> 00:05:35.205 managing various different parts of the organization.
00:05:35.235 --> 00:05:36.325 What are the drawbacks here?
00:05:36.425 --> 00:05:37.885 Are there any problems that we face
00:05:37.885 --> 00:05:38.925 when we are splitting up teams?
00:05:39.065 --> 00:05:41.405 The first thing is that earlier the context was
00:05:41.405 --> 00:05:42.485 shared closely, right?
00:05:42.765 --> 00:05:44.845 Everyone knew what another person is doing.
00:05:45.145 --> 00:05:46.725 Uh, and they could also see the code
00:05:46.725 --> 00:05:47.725 of another person easily.
00:05:47.945 --> 00:05:50.365 So it would be a single service, meaning the code,
00:05:50.385 --> 00:05:52.125 the project files would all be put together.
00:05:52.425 --> 00:05:54.685 Now the servers will be deployed independently.
00:05:54.785 --> 00:05:57.045 The project files of that code will be all separate.
00:05:57.045 --> 00:05:59.165 Separate. So you are just going to be knowing the API calls
00:05:59.345 --> 00:06:01.245 the API signatures of those services.
00:06:01.385 --> 00:06:03.005 You won't know really how the code
00:06:03.005 --> 00:06:04.765 inside is functioning earlier for one service.
00:06:04.905 --> 00:06:08.005 You had set up the cache, you had set up the logging, uh,
00:06:08.025 --> 00:06:10.325 the dashboards, everything was kept together.
00:06:10.505 --> 00:06:12.565 Now every team has its own concerns.
00:06:12.595 --> 00:06:15.125 Logging has to be set up for every single team.
00:06:15.275 --> 00:06:18.005 Caching may be managed by three different teams, so the code
00:06:18.075 --> 00:06:20.165 that they have around caching may have to be duplicated
00:06:20.265 --> 00:06:22.445 and so the there is going to be a duplication
00:06:22.445 --> 00:06:24.245 of effort across servers, okay?
00:06:24.245 --> 00:06:25.605 Especially for things which are common.
00:06:25.605 --> 00:06:27.885 Common functionalities usually end up having
00:06:27.885 --> 00:06:29.205 duplicated effort across teams.
00:06:29.345 --> 00:06:30.485 And the third thing, which is a bit
00:06:30.485 --> 00:06:32.285 of a performance issue is earlier
00:06:32.885 --> 00:06:35.205 whenever the inventory code wanted to talk
00:06:35.225 --> 00:06:38.005 to the payments code, it could do so with a function call,
00:06:38.005 --> 00:06:40.325 which would be really fast because you would be calling the
00:06:40.765 --> 00:06:41.925 function within the same computer.
00:06:42.185 --> 00:06:44.405 Now you are going to be making a network call.
00:06:44.405 --> 00:06:45.925 The inventory service may be in a separate
00:06:45.955 --> 00:06:47.285 machine, separate computer.
00:06:47.465 --> 00:06:49.245 The payment service may be in a different computer.
00:06:49.345 --> 00:06:50.965 And so whenever the inventory service has
00:06:50.965 --> 00:06:53.685 to query some data from the payment service, it's going
00:06:53.685 --> 00:06:54.845 to be making an API call
00:06:54.905 --> 00:06:56.765 and that API call will be across the network.
00:06:56.945 --> 00:06:58.165 By the time you make the call
00:06:58.305 --> 00:07:00.485 and get a response, sometime will have passed.
00:07:00.625 --> 00:07:03.165 So this splitting into services will make your communication
00:07:03.165 --> 00:07:04.165 less efficient than earlier.
00:07:04.305 --> 00:07:06.085 So what should you do? Should you split up the teams
00:07:06.225 --> 00:07:07.965 or should you keep them as a single big unit
00:07:08.075 --> 00:07:09.165 with 15 members?
00:07:09.545 --> 00:07:11.965 It becomes very difficult to manage a single team.
00:07:12.145 --> 00:07:14.525 And since you have the goal
00:07:14.705 --> 00:07:16.445 of getting a hundred members, right?
00:07:16.545 --> 00:07:18.885 In reality, you know there's always talk about a hundred
00:07:18.885 --> 00:07:21.045 members, but then you, you probably stop at 25.
00:07:21.105 --> 00:07:23.245 But since you are going to be expanding the team further,
00:07:23.465 --> 00:07:27.005 it probably makes sense to break up the teams into separate
00:07:27.525 --> 00:07:30.805 business units and giving them each their own code base,
00:07:30.975 --> 00:07:32.565 which they can deploy independently.
00:07:32.715 --> 00:07:34.885 This makes the organization more efficient,
00:07:34.885 --> 00:07:36.085 the developers more efficient,
00:07:36.275 --> 00:07:38.725 even if the code gets a little less efficient, it's okay.
00:07:38.725 --> 00:07:40.125 Just a few things to keep in mind.
00:07:40.125 --> 00:07:43.205 Something that you don't want in your tiny organization
00:07:43.205 --> 00:07:46.645 of 15 members is different members, different teams working
00:07:46.645 --> 00:07:48.405 with different programming languages.
00:07:48.405 --> 00:07:49.725 This is going to be a nightmare
00:07:49.965 --> 00:07:51.485 whenever you need to debug something,
00:07:51.685 --> 00:07:52.765 whenever you need to just go and check
00:07:52.765 --> 00:07:54.325 what the algorithm is like in the other service.
00:07:54.465 --> 00:07:55.925 If you have different programming languages,
00:07:56.165 --> 00:07:58.005 everyone will need to learn all programming languages.
00:07:58.005 --> 00:08:00.325 Another thing that we mentioned is you ideally want
00:08:00.325 --> 00:08:02.045 to keep the same technology throughout the organization
00:08:02.045 --> 00:08:03.885 because managing it is easier.
00:08:04.065 --> 00:08:06.085 So let's say one team says, I want
00:08:06.085 --> 00:08:07.605 to have Postgres as a database.
00:08:07.605 --> 00:08:09.245 Other team says, I want my sql.
00:08:09.265 --> 00:08:10.845 Let them talk to each other and decide on one.
00:08:10.865 --> 00:08:12.885 The entire organization is going to be using that.
00:08:12.945 --> 00:08:15.125 And finally your DevOps effort may go up.
00:08:15.125 --> 00:08:16.605 Since you have multiple servers being deployed
00:08:16.605 --> 00:08:18.365 simultaneously, there is a need
00:08:18.425 --> 00:08:19.925 to actually maintain these servers.
00:08:19.925 --> 00:08:21.045 Some of the duplication of code
00:08:21.045 --> 00:08:23.125 that we are talking about maybe can be taken up by DevOps.
00:08:23.185 --> 00:08:25.605 So it becomes a common team which is able
00:08:25.605 --> 00:08:28.485 to provide services like logging, like caching
00:08:28.485 --> 00:08:29.645 to all the teams that you have.
00:08:29.665 --> 00:08:31.485 But for a team of size 15,
00:08:31.485 --> 00:08:34.085 maybe you can just let the DevOps effort into the engineers
00:08:34.085 --> 00:08:36.725 themselves if it scales up, if it becomes like 50, 60,
00:08:36.885 --> 00:08:39.125 a hundred people makes sense to have DevOps engineers
00:08:39.125 --> 00:08:40.325 who are specialized at this
00:08:40.345 --> 00:08:43.205 and who are handling common functionalities across teams.
00:08:43.385 --> 00:08:45.285 Now that we have made the decision, we go ahead
00:08:45.305 --> 00:08:47.405 and have three teams for communications,
00:08:47.475 --> 00:08:48.925 inventory and payments.
00:08:48.985 --> 00:08:51.405 You immediately notice a problem the next day the founder
00:08:51.405 --> 00:08:53.205 comes and says that, you know, there's a lot of users
00:08:53.305 --> 00:08:55.570 who are giving awesome reviews for t-shirts.
00:08:55.665 --> 00:08:57.645 We should have this somewhere on the product page.
00:08:57.665 --> 00:08:59.565 So whenever a person is clicking on a t-shirt,
00:08:59.565 --> 00:09:01.245 they should be able to see the reviews of the t-shirt.
00:09:01.265 --> 00:09:02.765 Now what is this exactly? Is it
00:09:02.765 --> 00:09:04.045 inventory doesn't seem to fit?
00:09:04.045 --> 00:09:06.405 Is it payments? Certainly no, is it communications,
00:09:06.505 --> 00:09:09.005 but communications is more on communicating with the users
00:09:09.005 --> 00:09:11.365 through email or communicating through dashboards.
00:09:11.465 --> 00:09:13.365 So maybe you can fit this into communications,
00:09:13.385 --> 00:09:15.325 but it doesn't seem like, it seems like feedback.
00:09:15.335 --> 00:09:17.005 Seems like discussions, reviews.
00:09:17.225 --> 00:09:21.205 So you could force this new business feature into one
00:09:21.205 --> 00:09:23.045 of the business teams in this case communications
00:09:23.225 --> 00:09:25.365 or you can build a new team.
00:09:25.425 --> 00:09:27.325 If you take some engineers from communications
00:09:27.345 --> 00:09:29.925 and ask them to create a new service,
00:09:30.235 --> 00:09:32.165 this service will be basically a new project.
00:09:32.395 --> 00:09:34.445 They create the files, they'll set up everything
00:09:34.445 --> 00:09:36.765 around dependence, injection, logging, everything,
00:09:36.785 --> 00:09:40.525 and here the APIs that the service will expose are specific
00:09:40.585 --> 00:09:42.645 to the business requirement of discussions,
00:09:42.755 --> 00:09:44.485 reviews, feedback, all of this stuff.
00:09:44.485 --> 00:09:46.445 What does a user feel? What does a user want to convey?
00:09:46.475 --> 00:09:48.685 What do they say? Maybe even surveys in future.
00:09:48.865 --> 00:09:51.565 So you see that you are able to draw a boundary
00:09:51.665 --> 00:09:53.205 around this business feature
00:09:53.305 --> 00:09:54.885 and you are able to assign a team
00:09:54.945 --> 00:09:56.725 to work on these features tomorrow.
00:09:56.865 --> 00:09:59.165 If a related feature comes, then you know
00:09:59.165 --> 00:10:00.725 that this team is responsible for it.
00:10:00.785 --> 00:10:02.685 As the business expands, you will be needing
00:10:02.685 --> 00:10:04.365 to make such decisions frequently
00:10:04.425 --> 00:10:07.045 and one potential anti-patent that you can have here.
00:10:07.105 --> 00:10:08.405 One mistake that a lot
00:10:08.405 --> 00:10:11.285 of senior engineers make is they break teams too quickly.
00:10:11.385 --> 00:10:13.725 If there's a new feature, they look at the existing teams,
00:10:13.725 --> 00:10:15.245 they really don't feel like any
00:10:15.265 --> 00:10:16.885 of them can manage this new feature.
00:10:16.905 --> 00:10:18.365 It doesn't really fit in perfectly.
00:10:18.365 --> 00:10:20.005 So instead of trying to fit in the
00:10:20.005 --> 00:10:21.405 feature, they split the team.
00:10:21.405 --> 00:10:22.605 This is generally a good idea.
00:10:22.785 --> 00:10:25.925 It isolates concerns, but you may overdo this. Also.
00:10:26.065 --> 00:10:28.125 One thing that I've noticed, especially young senior
00:10:28.365 --> 00:10:29.725 engineers, what they do or young tech leads,
00:10:29.725 --> 00:10:31.765 what they do is they get a new feature, they see
00:10:31.765 --> 00:10:34.445 that it doesn't perfectly fit into their team's requirements
00:10:34.465 --> 00:10:36.005 and they talk about splitting the team
00:10:36.105 --> 00:10:37.525 or at least creating a new project.
00:10:37.525 --> 00:10:39.445 They'll use the same team, but they'll create a new project
00:10:39.505 --> 00:10:41.005 and habits deployment managed,
00:10:41.115 --> 00:10:42.925 this is called a microservice, right?
00:10:42.925 --> 00:10:46.285 You have various teams with various services, all
00:10:46.285 --> 00:10:48.285 of them having their own deployment cycles, all
00:10:48.285 --> 00:10:49.645 of them having their own setup
00:10:49.825 --> 00:10:51.685 and the benefit is isolation of concerns.
00:10:51.705 --> 00:10:54.485 But microservices can devolve to nano services also,
00:10:54.485 --> 00:10:55.845 which is not something that you want.
00:10:56.035 --> 00:10:58.245 It's a very fine splitting
00:10:58.505 --> 00:11:00.885 of business responsibilities across various people.
00:11:01.085 --> 00:11:03.085 A single person may be managing two projects.
00:11:03.085 --> 00:11:04.965 That's when you know that things have gone wrong
00:11:05.065 --> 00:11:07.245 and there are more projects than there are people
00:11:07.425 --> 00:11:08.445 you know, things have gone wrong.
00:11:08.475 --> 00:11:09.765 Okay, so you don't want this to happen.
00:11:09.905 --> 00:11:11.205 Now how do you avoid this? One
00:11:11.205 --> 00:11:13.125 of the things is just plain simple approach
00:11:13.125 --> 00:11:15.685 that if anything remotely related to a team comes,
00:11:15.785 --> 00:11:17.805 you first add it and later on you see
00:11:17.805 --> 00:11:20.205 that if the business requirement is sufficient,
00:11:20.265 --> 00:11:22.045 if there's a lot of work happening on
00:11:22.045 --> 00:11:23.765 that particular feature, then you split it.
00:11:23.765 --> 00:11:24.765 That's just common sense.
00:11:24.905 --> 00:11:26.685 The second thing you can do is look at
00:11:26.705 --> 00:11:28.525 how this particular service
00:11:28.745 --> 00:11:30.805 or this new set of features is going
00:11:30.805 --> 00:11:32.445 to be interacting with the rest of the services.
00:11:32.625 --> 00:11:34.965 If you see that this service often interacts
00:11:34.965 --> 00:11:36.485 with different services, then that's okay.
00:11:36.545 --> 00:11:38.885 If you see that reviews only talks to communications
00:11:38.945 --> 00:11:40.925 and for every single thing has to communicate
00:11:40.925 --> 00:11:42.165 with communications, data response
00:11:42.265 --> 00:11:44.445 and then give a response to the client, it probably means
00:11:44.445 --> 00:11:46.245 that the reviews can move to communications.
00:11:46.385 --> 00:11:48.365 All you have to do is change the name of communications.
00:11:48.425 --> 00:11:50.285 You have to find the right name there,
00:11:50.545 --> 00:11:51.965 but the concept seems similar.
00:11:52.105 --> 00:11:53.925 That's the reason why the business use case
00:11:53.935 --> 00:11:55.085 seems to be merging together.
00:11:55.235 --> 00:11:58.365 With this, we can roughly draw service boundaries in
00:11:58.425 --> 00:11:59.565 an existing organization.
00:11:59.595 --> 00:12:02.245 Then we can split these into multiple services,
00:12:02.245 --> 00:12:03.525 which is basically multiple teams
00:12:04.125 --> 00:12:05.285 managing each individual service.
00:12:05.605 --> 00:12:07.485 A major concern with this, we are able
00:12:07.485 --> 00:12:10.325 to look at the capabilities of an organization as a set
00:12:10.325 --> 00:12:11.805 of interactions between different teams
00:12:12.025 --> 00:12:14.125 and each team works in parallel, so you're able
00:12:14.125 --> 00:12:16.125 to get more throughput, more work done out
00:12:16.125 --> 00:12:18.605 of them without them having to get stuck in communication.
00:12:18.605 --> 00:12:20.445 There is one major drawback though,
00:12:20.465 --> 00:12:23.005 and this is both in code and in person.
00:12:23.485 --> 00:12:24.885 Whenever a person has to interact
00:12:24.885 --> 00:12:27.645 with a person in another team that is expensive, okay?
00:12:27.745 --> 00:12:30.005 Uh, they have to go and talk to the other person.
00:12:30.005 --> 00:12:31.365 They usually have document sharing.
00:12:31.515 --> 00:12:32.685 It's no longer just code.
00:12:32.685 --> 00:12:34.045 It's no longer that they're sitting together,
00:12:34.105 --> 00:12:36.525 so they're no longer effective in terms of communication.
00:12:36.525 --> 00:12:37.605 And as teams get larger,
00:12:37.825 --> 00:12:39.445 the decisions they make are quite complex.
00:12:39.665 --> 00:12:42.005 You will need to document your decisions better, whether
00:12:42.005 --> 00:12:43.365 through architecture diagrams
00:12:43.365 --> 00:12:44.885 or through just email communication.
00:12:44.945 --> 00:12:47.365 You will need to document your decisions better.
00:12:47.385 --> 00:12:49.125 That's one part, that's the human part,
00:12:49.185 --> 00:12:52.285 but there is a equally critical coding part which comes in,
00:12:52.285 --> 00:12:54.605 and that is when you are communicating with another service,
00:12:54.705 --> 00:12:56.805 you're communicating over API, which means
00:12:56.805 --> 00:12:59.045 that the APIs have to be clearly defined.
00:12:59.145 --> 00:13:02.365 The API contracts by every team has to be set up
00:13:02.385 --> 00:13:03.725 and made public to other teams.
00:13:03.985 --> 00:13:07.285 How do you do this? Whenever a team adds an API changes an
00:13:07.285 --> 00:13:09.285 API removes an API, it makes an update
00:13:09.285 --> 00:13:10.565 to an API contract this.
00:13:10.605 --> 00:13:11.845 API contract is just like code.
00:13:11.945 --> 00:13:15.285 It says the function name, it says the parameters it takes,
00:13:15.425 --> 00:13:17.005 and what is the expected response
00:13:17.105 --> 00:13:19.285 and also expected error codes just like
00:13:19.295 --> 00:13:20.965 interfaces in many programming languages.
00:13:20.965 --> 00:13:24.205 This tells you what a function takes and what it returns.
00:13:24.305 --> 00:13:25.765 It doesn't tell you how it works internally.
00:13:25.865 --> 00:13:29.005 And so what you want to do is you want a repository of all
00:13:29.005 --> 00:13:30.325 of these API contracts.
00:13:30.325 --> 00:13:31.765 If you have three teams, then all
00:13:31.765 --> 00:13:33.525 of the API contracts should be kept in one place.
00:13:33.665 --> 00:13:36.645 Why is that the case? Whenever I want to deploy my service,
00:13:37.045 --> 00:13:39.205 I ensure that I'm using the latest version
00:13:39.305 --> 00:13:40.685 of the API contract of each team.
00:13:40.745 --> 00:13:43.845 So if the order service was earlier, taking a T-shirt ID
00:13:43.845 --> 00:13:45.165 to tell you the status of an order,
00:13:45.345 --> 00:13:48.645 and now it has changed it to item ID comma item type,
00:13:48.645 --> 00:13:49.925 because now you're selling not
00:13:49.925 --> 00:13:51.045 just T-shirts, but other stuff.
00:13:51.115 --> 00:13:53.445 Also, all of its dependent services, whoever talks
00:13:53.445 --> 00:13:55.245 to it need to be notified about this.
00:13:55.465 --> 00:13:58.285 And since it's not a code change, since it's not going
00:13:58.285 --> 00:14:00.245 to give you a compilation error, you will only figure out
00:14:00.245 --> 00:14:01.285 that the a p has changed
00:14:01.375 --> 00:14:02.885 after you have deployed the service.
00:14:03.025 --> 00:14:05.845 That's a bad idea. If I had a API contract publicly visible,
00:14:05.915 --> 00:14:09.005 then as an engineer I would check if my API actually
00:14:09.005 --> 00:14:10.205 exists in that new contract.
00:14:10.305 --> 00:14:12.485 And if it didn't exist, then I would get a error.
00:14:12.625 --> 00:14:14.045 How do we make this happen? In practice,
00:14:14.185 --> 00:14:15.925 we use something called client libraries.
00:14:16.025 --> 00:14:18.965 You remember the import or include statement you add on top.
00:14:19.225 --> 00:14:20.245 The basic idea is
00:14:20.245 --> 00:14:22.605 that every service will have its client library,
00:14:22.815 --> 00:14:25.645 which is some software that allows other services
00:14:25.745 --> 00:14:27.645 to make API calls to your service.
00:14:27.865 --> 00:14:29.925 For example, if I am the order service
00:14:30.145 --> 00:14:32.005 and I made a change in my function,
00:14:32.045 --> 00:14:34.485 I made a change in my A PII no longer just take t-shirt.
00:14:34.565 --> 00:14:36.205 I actually take item ID and item type.
00:14:36.325 --> 00:14:38.365 I will go ahead and make a change in my contract
00:14:38.465 --> 00:14:41.205 and publish this to the contract repository when other
00:14:41.485 --> 00:14:43.325 services update their client version number.
00:14:43.475 --> 00:14:47.565 When they say that oh gov is no longer on version 1.2, I see
00:14:47.565 --> 00:14:49.805 that 1.3 has come in, let me download that software.
00:14:49.805 --> 00:14:51.325 So they say 1.3 and they see
00:14:51.325 --> 00:14:52.605 that their code has compilation letters.
00:14:52.865 --> 00:14:54.685 Why? They go and they see that, oh,
00:14:54.715 --> 00:14:56.285 just the T-shirt ID is not good enough.
00:14:56.435 --> 00:14:59.325 He's expecting me to send item ID and item type fine.
00:14:59.395 --> 00:15:01.405 I'll do that. So in this way, you are able
00:15:01.405 --> 00:15:04.125 to notify other services to change their contract.
00:15:04.125 --> 00:15:06.685 This is called a software client or client libraries.
00:15:06.745 --> 00:15:09.925 It helps dependent services make changes to their code,
00:15:10.015 --> 00:15:11.925 which interacts with your API.
00:15:11.925 --> 00:15:13.685 And one of the things we want to avoid here is
00:15:13.685 --> 00:15:16.485 to bring surprises to the people using our client library.
00:15:16.595 --> 00:15:19.565 Just imagine you changed your version from 1.2 to 1.3
00:15:19.565 --> 00:15:21.485 and you see that you have a compilation error that's going
00:15:21.485 --> 00:15:24.085 to irritate you as a engineer who's using the order status,
00:15:24.245 --> 00:15:25.165 API, you're going to say, oh
00:15:25.165 --> 00:15:26.125 my God, now I have to make changes.
00:15:26.345 --> 00:15:28.765 Now my old code doesn't work. You want to avoid this.
00:15:28.835 --> 00:15:31.165 Your customers, your clients, people who interact
00:15:31.165 --> 00:15:33.965 with you should not have their code broken just
00:15:33.965 --> 00:15:35.445 because you made a API change,
00:15:35.465 --> 00:15:36.885 and this is called a breaking change.
00:15:36.905 --> 00:15:39.405 You want avoid this, you want to be backward compatible.
00:15:39.625 --> 00:15:41.605 You want your existing customers to be able
00:15:41.605 --> 00:15:44.045 to use the same code and still have their code work.
00:15:44.065 --> 00:15:45.765 So what code you do here, I understand
00:15:45.765 --> 00:15:47.085 that you're taking an item ID
00:15:47.085 --> 00:15:48.725 and you're taking a item type now,
00:15:48.865 --> 00:15:52.525 but if a person is looking to just send you the item id,
00:15:52.525 --> 00:15:53.605 then you can check that.
00:15:53.605 --> 00:15:56.365 If item type equal to null, then automatically assume
00:15:56.365 --> 00:15:59.005 that the item type is T-shirts and give a response.
00:15:59.145 --> 00:16:02.005 In this way, existing clients can continue behaving in the
00:16:02.005 --> 00:16:03.005 same way that they were earlier
00:16:03.225 --> 00:16:05.605 and gradually migrate to your new APIs.
00:16:05.605 --> 00:16:08.165 While newer clients can get the benefits of a new API,
00:16:08.165 --> 00:16:09.685 you learn more about service registry
00:16:09.685 --> 00:16:11.365 and contracts in the Gmail chapter.
00:16:11.545 --> 00:16:14.005 For now, at a practical level, this is great.
00:16:14.185 --> 00:16:16.125 You have taken an existing service
00:16:16.225 --> 00:16:17.885 broken into microservices.
00:16:18.075 --> 00:16:21.205 Your team is able to work in parallel and things look fine.
00:16:21.205 --> 00:16:23.725 Congratulations, you have done your first job as a CTO.
00:16:23.725 --> 00:16:25.805 It's been a success. You are scaling up your team
00:16:25.945 --> 00:16:28.605 and the efficiency per engineer has not really gone down.
00:16:28.705 --> 00:16:30.165 You are also happy that you're able
00:16:30.165 --> 00:16:32.605 to work on various features without engineers stepping on
00:16:32.605 --> 00:16:34.765 each other's toes and keeping the deployment cycle fast. 