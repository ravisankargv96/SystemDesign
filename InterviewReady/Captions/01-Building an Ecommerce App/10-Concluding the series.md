## Chapters
* 00:00 - Many, many complaints!
* 02:30 - Decoupling Teams
* 04:00 - High Level Design
* 06:24 - Stakeholder Confirmation
* 08:28 - Concluding the series!

## Transcript
00:00:00.000 --> 00:00:02.605 As time passes, your team scales from 15 engineers,
00:00:02.605 --> 00:00:03.965 you move to 15 engineers
00:00:03.985 --> 00:00:06.245 and from 50 you move to 70 engineers.
00:00:06.245 --> 00:00:09.525 This is a huge set of engineers, so you have multiple teams,
00:00:09.525 --> 00:00:12.405 maybe 10 or 12 teams managing the 17 engineers
00:00:12.405 --> 00:00:14.205 that you have, and you are their CTO.
00:00:14.305 --> 00:00:16.325 So you are now speaking mainly to managers,
00:00:16.725 --> 00:00:18.925 engineering managers who get updates on their teams.
00:00:19.025 --> 00:00:20.085 So maybe there's five
00:00:20.145 --> 00:00:22.525 or 10 managers that you have who directly report to you.
00:00:22.545 --> 00:00:23.765 The interesting thing though is
00:00:23.765 --> 00:00:25.805 that the managers are rather upset
00:00:26.115 --> 00:00:28.165 with different parts of the organization.
00:00:28.165 --> 00:00:29.925 There's always some communication error
00:00:29.955 --> 00:00:32.845 between the sales team, the operations team,
00:00:32.905 --> 00:00:34.485 the product team, and the engineering team.
00:00:34.485 --> 00:00:36.405 So what you do is you call a board meeting,
00:00:36.505 --> 00:00:38.325 you get all the CXOs involved
00:00:38.385 --> 00:00:40.845 and you start asking them, can you tell us any way
00:00:40.845 --> 00:00:42.085 that the engineering team can improve?
00:00:42.385 --> 00:00:43.285 Is there something that you
00:00:43.285 --> 00:00:44.405 would like the engineering team to do?
00:00:44.425 --> 00:00:46.245 And you get feedback. The feedback is this,
00:00:46.605 --> 00:00:49.005 whenever we ask your engineers for any kind of data,
00:00:49.075 --> 00:00:50.085 they take a lot of time
00:00:50.105 --> 00:00:53.685 to execute those queries which results in delayed insights
00:00:53.945 --> 00:00:55.205 and therefore there are lost
00:00:55.205 --> 00:00:56.565 opportunities in business sometimes.
00:00:56.865 --> 00:00:59.485 The second problem is whenever we have a slightly complex
00:00:59.765 --> 00:01:01.165 business query, like tell us the people
00:01:01.225 --> 00:01:03.685 who purchase t-shirts at least three days after signing up,
00:01:03.885 --> 00:01:04.965 whenever we ask this kind of a query,
00:01:05.035 --> 00:01:06.365 your engineering team doesn't know
00:01:06.365 --> 00:01:07.565 where this query is to be done.
00:01:07.665 --> 00:01:10.845 So we have to go to one team, which is the profile team
00:01:10.875 --> 00:01:12.565 that tells us when registrations were made.
00:01:12.565 --> 00:01:13.845 Then we have to go to another team,
00:01:13.845 --> 00:01:15.365 which is the orders team, and they tell
00:01:15.365 --> 00:01:16.485 us when the order was complete.
00:01:16.545 --> 00:01:17.845 And then you also have a delivery team,
00:01:17.845 --> 00:01:19.605 which tells us when the order was received.
00:01:19.705 --> 00:01:21.565 As a sales manager or a product manager
00:01:21.585 --> 00:01:23.685 or operations team manager, this is very,
00:01:23.685 --> 00:01:24.725 very hard to coordinate.
00:01:24.785 --> 00:01:26.445 You have a simple business query in your head
00:01:26.505 --> 00:01:27.605 and you have to go
00:01:27.665 --> 00:01:29.685 and connect with multiple teams, coordinate with them, get
00:01:29.685 --> 00:01:31.005 that data, and then work on
00:01:31.005 --> 00:01:33.285 that data In Excel sheets, it's a real pain.
00:01:33.285 --> 00:01:34.405 So you accept the feedback.
00:01:34.405 --> 00:01:36.285 You say, okay, these two are serious
00:01:36.285 --> 00:01:37.565 problems, is there anything else?
00:01:37.705 --> 00:01:39.725 The product officer then tells you something specific
00:01:39.745 --> 00:01:42.125 to product managers, which is often they need
00:01:42.125 --> 00:01:43.685 to run complex business queries.
00:01:43.785 --> 00:01:45.525 It is not something that you would want
00:01:45.665 --> 00:01:46.805 the engineer to run, right?
00:01:46.805 --> 00:01:47.885 They want to play with the data.
00:01:47.885 --> 00:01:49.325 They want to slice and dice the data,
00:01:49.475 --> 00:01:50.805 look at different patterns.
00:01:50.865 --> 00:01:53.085 And for that they have to connect with various teams.
00:01:53.235 --> 00:01:55.325 They all give their data at different points in time
00:01:55.325 --> 00:01:56.565 and then they have to put it all
00:01:56.725 --> 00:01:57.805 together and then work with it.
00:01:57.805 --> 00:01:59.765 This is a pain. It would be really nice if
00:01:59.765 --> 00:02:00.845 they could download the data.
00:02:00.875 --> 00:02:03.005 They would have periodic downloads as CSV files.
00:02:03.105 --> 00:02:05.325 And then the chief of operations says often, I want
00:02:05.325 --> 00:02:07.485 to find out if something is wrong in the delivery
00:02:07.625 --> 00:02:09.285 or in the order management phase.
00:02:09.305 --> 00:02:11.325 If you could gimme some dashboards telling me
00:02:11.505 --> 00:02:13.765 how many sales were made, how many people registered,
00:02:13.865 --> 00:02:14.965 how many deliveries are pending,
00:02:14.985 --> 00:02:16.845 how many deliveries have been executed today,
00:02:16.845 --> 00:02:19.045 that is something I want to see on a daily basis.
00:02:19.045 --> 00:02:21.845 Unfortunately, right now I have to either connect
00:02:21.845 --> 00:02:23.765 with the engineer to fire those SQL queries
00:02:23.785 --> 00:02:25.285 or I get credentials to their database
00:02:25.305 --> 00:02:28.125 and my team actually files those sq l queries periodically.
00:02:28.125 --> 00:02:29.845 So with these requirements, you thank them
00:02:29.905 --> 00:02:31.205 and you move to your team
00:02:31.265 --> 00:02:33.165 and looking at these requirements, you realize
00:02:33.165 --> 00:02:34.485 that the core problem is
00:02:34.485 --> 00:02:36.885 that the business teams are heavily coupled
00:02:36.955 --> 00:02:39.565 with your tech team when they want to draw data insights.
00:02:39.825 --> 00:02:41.885 If the sales team wants to find out
00:02:41.885 --> 00:02:43.165 how many sales they have made, they have
00:02:43.165 --> 00:02:45.285 to first figure out which tech team they have to connect to.
00:02:45.285 --> 00:02:47.165 Then they have to wait on them to fire the query.
00:02:47.195 --> 00:02:48.885 Here you can get rid of two problems.
00:02:49.105 --> 00:02:51.005 One is the dependency in terms of time
00:02:51.065 --> 00:02:52.325 and the type of query to fire.
00:02:52.345 --> 00:02:54.765 And the second thing is finding out which team to connect
00:02:54.765 --> 00:02:55.925 to Finding out which team to connect
00:02:55.925 --> 00:02:57.165 to is especially a problem
00:02:57.165 --> 00:02:59.045 because in some business queries you're seeing seeing
00:02:59.245 --> 00:03:00.365 multiple teams being connected and
00:03:00.365 --> 00:03:01.445 you have to coordinate between them.
00:03:01.465 --> 00:03:03.005 So what do you do? You have many tech teams.
00:03:03.225 --> 00:03:05.325 All of them have their own production database.
00:03:05.325 --> 00:03:07.485 They're using the same database technology of Postgres,
00:03:07.485 --> 00:03:09.445 but each of the 12 teams that we talked about has a
00:03:09.445 --> 00:03:10.605 Postgres database in itself.
00:03:10.605 --> 00:03:12.485 What you want to do is collect all
00:03:12.485 --> 00:03:14.685 of the data in these 12 production databases
00:03:14.785 --> 00:03:16.765 and move it to a single data source.
00:03:16.955 --> 00:03:19.005 This copy will have the data
00:03:19.145 --> 00:03:20.965 for all 12 production databases.
00:03:20.995 --> 00:03:22.405 It's a very large copy. The benefit
00:03:22.465 --> 00:03:24.325 of having this large collected copy is
00:03:24.325 --> 00:03:26.645 that business teams can now connect with this copy.
00:03:26.675 --> 00:03:28.565 They can fire the queries that they want to
00:03:28.585 --> 00:03:30.365 and they can build dashboards on top of it.
00:03:30.435 --> 00:03:32.765 None of these queries will impact the tech team.
00:03:32.785 --> 00:03:34.245 It won't impact the engineers
00:03:34.345 --> 00:03:36.525 and it won't even impact the database loads.
00:03:36.625 --> 00:03:38.965 You have these production databases running in case someone
00:03:38.965 --> 00:03:40.205 files a heavy analytics query.
00:03:40.275 --> 00:03:42.165 It's possible that it takes a big lock
00:03:42.225 --> 00:03:43.445 or it takes time to execute.
00:03:43.445 --> 00:03:44.845 The database may have been overloaded.
00:03:44.865 --> 00:03:45.925 Now that problem is resolved.
00:03:45.945 --> 00:03:48.245 You will have a copy of all the databases.
00:03:48.245 --> 00:03:49.565 People are making read queries here
00:03:49.565 --> 00:03:51.045 and your production systems continue running.
00:03:51.045 --> 00:03:53.285 Then your architecture is split into two pieces.
00:03:53.625 --> 00:03:56.005 One is the live production serving system
00:03:56.145 --> 00:03:59.045 and the other is a place where data is collected
00:03:59.185 --> 00:04:01.725 and later varied by people as in when they want.
00:04:01.745 --> 00:04:03.125 Now, how do you do this? Creating
00:04:03.125 --> 00:04:04.285 the dashboards is rather simple.
00:04:04.465 --> 00:04:07.325 You need some engineering effort to create the dashboards,
00:04:07.325 --> 00:04:08.405 the UI, and maintain it.
00:04:08.405 --> 00:04:09.925 But conceptually it's not very hard.
00:04:09.985 --> 00:04:12.045 As long as you can build graphs which are relevant
00:04:12.045 --> 00:04:13.485 and asked for by the business,
00:04:13.505 --> 00:04:14.645 you can create those dashboards.
00:04:14.715 --> 00:04:16.885 Also, serving the dashboards is not very difficult.
00:04:17.025 --> 00:04:19.845 You are going to have a server which is going to run queries
00:04:19.845 --> 00:04:21.805 through APIs called for by the dashboard.
00:04:21.905 --> 00:04:23.325 In this data side, you need some UI
00:04:23.485 --> 00:04:24.685 engineers to create the dashboards.
00:04:24.685 --> 00:04:27.285 You'll also need some server side engineers to expose APIs
00:04:27.285 --> 00:04:29.605 so that the commonly fired queries can actually
00:04:29.605 --> 00:04:30.725 hit this new database copy.
00:04:30.785 --> 00:04:33.405 For example, select account star sum
00:04:33.405 --> 00:04:36.005 of amount from payment stable group by date.
00:04:36.035 --> 00:04:38.605 This means for every day, tell me the amount
00:04:38.605 --> 00:04:40.165 of sales you have made, the total amount
00:04:40.185 --> 00:04:41.485 and the number of sales you have made.
00:04:41.485 --> 00:04:42.885 This might be useful for the sales team.
00:04:42.905 --> 00:04:45.045 You can have similar queries for emails and so on,
00:04:45.065 --> 00:04:46.685 and all of this can be aggregated
00:04:46.685 --> 00:04:47.685 and shown a single dashboard.
00:04:47.685 --> 00:04:49.965 If the product managers are looking to five custom queries,
00:04:50.125 --> 00:04:52.565 then you can expose a SQ query interface
00:04:52.625 --> 00:04:56.045 and describe the way in which all the tables are existing
00:04:56.045 --> 00:04:57.165 in this database copy.
00:04:57.305 --> 00:05:00.325 Now the product managers may hire a data analyst who's
00:05:00.325 --> 00:05:01.845 firing queries through this interface,
00:05:01.905 --> 00:05:04.365 or they may learn SQ themselves or they may use chat g pt.
00:05:04.365 --> 00:05:05.845 It doesn't really matter as long as you give them the
00:05:05.845 --> 00:05:07.805 capability, they'll find solutions for themselves.
00:05:07.945 --> 00:05:10.685 As a CTO, you are enabling many teams instead
00:05:10.685 --> 00:05:12.045 of just solving that problem solver.
00:05:12.045 --> 00:05:14.125 So the only problem which exists now is
00:05:14.185 --> 00:05:15.925 how do you create this database copy?
00:05:16.035 --> 00:05:18.525 What would be the most efficient, easy way to do it?
00:05:18.845 --> 00:05:20.045 Remember that we want to do three things.
00:05:20.265 --> 00:05:21.925 One is keep the solution simple.
00:05:22.105 --> 00:05:23.685 Two is we want to meet all the
00:05:23.685 --> 00:05:25.245 requirements of the customers.
00:05:25.245 --> 00:05:26.885 We have made sure that this architecture seems
00:05:26.885 --> 00:05:28.045 to meet all the requirements.
00:05:28.065 --> 00:05:30.045 And the third thing is we want to make it cost effective.
00:05:30.105 --> 00:05:31.685 So how do you do this in a simple way
00:05:31.745 --> 00:05:33.205 and yet it is cost effective?
00:05:33.205 --> 00:05:34.485 Let's deal with simplicity first.
00:05:34.485 --> 00:05:37.085 There are existing solutions for data warehousing.
00:05:37.085 --> 00:05:38.885 What we are trying to do right now create a copy
00:05:39.025 --> 00:05:40.525 of various database tables
00:05:40.525 --> 00:05:42.165 and give the capability of querying on top
00:05:42.165 --> 00:05:43.645 of them is a very common use case.
00:05:43.875 --> 00:05:46.485 It's required across all organizations, almost,
00:05:46.485 --> 00:05:47.965 which are of a decent size.
00:05:48.145 --> 00:05:52.405 Amazon Kinesis can help you stream the data from your data
00:05:52.405 --> 00:05:55.885 sources, your services into this single data warehouse.
00:05:55.985 --> 00:05:58.405 Amazon Athena can help you query the data
00:05:58.545 --> 00:06:00.685 so the product managers can use Amazon Athena
00:06:00.685 --> 00:06:02.765 to query the data in your warehouse.
00:06:03.165 --> 00:06:05.645 Kinesis is the one which is helping you stream data from
00:06:05.885 --> 00:06:07.365 services and making this data copy.
00:06:07.425 --> 00:06:08.685 In terms of cost effectiveness,
00:06:08.685 --> 00:06:11.285 this is probably the best solution that you can come up with
00:06:11.285 --> 00:06:13.085 because you are charged not for storage,
00:06:13.265 --> 00:06:16.325 but for the bandwidth that you use from Amazon Athena.
00:06:16.325 --> 00:06:18.005 Amazon Kinesis is extremely cheap.
00:06:18.065 --> 00:06:20.045 All of your services, when they're making any kind
00:06:20.045 --> 00:06:22.485 of changes to the data can also send an event
00:06:22.485 --> 00:06:24.165 through Kinesis to this data copy.
00:06:24.225 --> 00:06:25.645 So now you host a new board meeting.
00:06:25.785 --> 00:06:27.205 You don't take the requirements
00:06:27.205 --> 00:06:28.285 immediately to the engineering team.
00:06:28.285 --> 00:06:30.165 You host a meeting and you say that this is
00:06:30.165 --> 00:06:32.645 what I'm thinking about having a separate data store,
00:06:32.655 --> 00:06:34.605 which is going to be populated from time
00:06:34.605 --> 00:06:35.645 to time through streams.
00:06:35.745 --> 00:06:37.605 Amazon Kinesis is what we are going to use,
00:06:37.665 --> 00:06:39.245 and then we are going to give you the capability
00:06:39.305 --> 00:06:40.765 to query this data copy.
00:06:40.825 --> 00:06:42.565 The teams agree. They say, this is wonderful,
00:06:42.625 --> 00:06:43.965 except for the product management team.
00:06:43.965 --> 00:06:45.725 They say that, I've never heard of Kinesis,
00:06:45.795 --> 00:06:47.045 I've never heard of Athena.
00:06:47.145 --> 00:06:48.685 It seems very specific
00:06:48.825 --> 00:06:52.005 to AWS can be instead use Apache Technologies
00:06:52.155 --> 00:06:54.725 because hiring for Apache technologies is easier.
00:06:54.785 --> 00:06:55.845 So you say, what do you mean by that?
00:06:55.845 --> 00:06:59.045 Well, there are people who are experts at data streaming.
00:06:59.045 --> 00:07:00.285 What you're using is Kinesis.
00:07:00.285 --> 00:07:02.085 Instead, we can use Apache, which is open source,
00:07:02.225 --> 00:07:04.645 and that is Apache Kafka streaming data,
00:07:04.645 --> 00:07:06.325 sending data from one place to another.
00:07:06.455 --> 00:07:07.525 Kafka manages that really well.
00:07:07.605 --> 00:07:09.725 I can get a person who's a expert at Kafka.
00:07:09.725 --> 00:07:10.805 You don't even need to look into it.
00:07:10.885 --> 00:07:12.805 You say, oh wow, that should save me some time.
00:07:12.945 --> 00:07:15.605 And then they say, instead of having uh,
00:07:15.605 --> 00:07:17.885 this data warehouse being queried by Amazon Athena,
00:07:18.025 --> 00:07:21.085 we could use again an open source technology like Hadoop
00:07:21.085 --> 00:07:23.365 file system or Amazon S3 Cs three files.
00:07:23.465 --> 00:07:24.765 So you say, that's also fine with me.
00:07:24.805 --> 00:07:26.685 I don't have any preference for a data store.
00:07:26.685 --> 00:07:28.125 And then they tell you that they're going
00:07:28.125 --> 00:07:30.325 to query this data using Apache Spark.
00:07:30.395 --> 00:07:32.765 They want to run some complex machine learning algorithms.
00:07:32.765 --> 00:07:34.085 They want to run some complex
00:07:34.085 --> 00:07:35.925 transformation or something simple.
00:07:36.115 --> 00:07:37.445 Also, they know Spark. They're
00:07:37.445 --> 00:07:38.525 comfortable with Apache Spark.
00:07:38.525 --> 00:07:39.445 It's an open source project.
00:07:39.505 --> 00:07:40.685 That's what they want to go for.
00:07:40.705 --> 00:07:42.205 Hiring is easy, training is easy.
00:07:42.265 --> 00:07:45.045 If we go for something specific to AWS tomorrow, if we move
00:07:45.045 --> 00:07:46.405 to GCP, it may be a problem.
00:07:46.545 --> 00:07:48.725 So you hear the suggestions, you think over,
00:07:48.905 --> 00:07:50.205 is this meeting all the requirements?
00:07:50.385 --> 00:07:52.565 Yes, it is. Is this as simple as earlier?
00:07:52.695 --> 00:07:54.005 Maybe it's a bit more complex,
00:07:54.185 --> 00:07:56.165 but the complexity is being managed by another team.
00:07:56.185 --> 00:07:57.645 The operations, the product management team
00:07:57.665 --> 00:07:58.885 are going to take care of this for you.
00:07:58.985 --> 00:08:00.285 And what about cost effectiveness?
00:08:00.355 --> 00:08:02.525 It's difficult to say without knowing the exact amount
00:08:02.525 --> 00:08:03.605 of data that will be used.
00:08:03.665 --> 00:08:05.525 You may do some capacity estimation here.
00:08:05.625 --> 00:08:08.365 But the basic idea is since the solutions are extremely
00:08:08.365 --> 00:08:09.485 similar and Kinesis
00:08:09.485 --> 00:08:12.085 and Athena seems to be wrappers around the open source
00:08:12.605 --> 00:08:13.725 solution that you would have otherwise,
00:08:13.865 --> 00:08:15.405 it should be affordable at this point.
00:08:15.405 --> 00:08:16.565 You go back to your engineering team
00:08:16.565 --> 00:08:18.445 and say, this is the solution that we have.
00:08:18.585 --> 00:08:20.885 Our existing microservices will have no changes.
00:08:21.145 --> 00:08:24.485 All you have to do is publish events to Apache Kafka.
00:08:24.575 --> 00:08:27.405 Kafka will ensure that the data streams are all collected
00:08:27.405 --> 00:08:28.925 into a single data source later on.
00:08:28.985 --> 00:08:30.285 And that's it. This is how system
00:08:30.285 --> 00:08:31.645 design works in the real world.
00:08:31.645 --> 00:08:33.565 There are business requirements which are
00:08:33.565 --> 00:08:34.965 converted to technical requirements.
00:08:34.995 --> 00:08:36.085 Then they're confirmed
00:08:36.085 --> 00:08:38.405 with business stakeholders whether this is making sense
00:08:38.405 --> 00:08:40.005 or not, and then they come to the engineering team.
00:08:40.025 --> 00:08:42.845 The benefit of this kind of an approach is at every point,
00:08:42.915 --> 00:08:45.445 it's not only that the business stakeholders are aware of
00:08:45.515 --> 00:08:47.045 what is the impact of this project,
00:08:47.185 --> 00:08:49.805 but the engineers are also aware of how their changes,
00:08:50.145 --> 00:08:52.205 how their code impacts the business.
00:08:52.385 --> 00:08:54.325 And with that, we conclude this example,
00:08:54.475 --> 00:08:58.125 this rather large example of building a t-shirts website.
00:08:58.145 --> 00:09:00.845 We moved from a very simple project which used serverless
00:09:00.845 --> 00:09:02.565 technologies to a complex project,
00:09:02.565 --> 00:09:05.245 which has caching load balancing rate limiting
00:09:05.345 --> 00:09:06.605 and multiple microservices.
00:09:06.755 --> 00:09:09.565 From this point on, we will go into the examples
00:09:09.585 --> 00:09:11.525 and the existing technologies in detail,
00:09:11.525 --> 00:09:13.005 whether it is databases or networks,
00:09:13.005 --> 00:09:15.085 we'll go into the subtopics in detail
00:09:15.105 --> 00:09:17.205 and list them out so that as an engineer,
00:09:17.305 --> 00:09:19.325 you are well equipped with what exists out there.
00:09:19.425 --> 00:09:21.765 But the good news is you are now aware of how
00:09:21.765 --> 00:09:23.405 to design a simple distributed system.
00:09:23.405 --> 00:09:25.205 You're also aware of the common algorithms
00:09:25.205 --> 00:09:26.605 and design patterns, which are used
00:09:26.605 --> 00:09:27.765 to serve business requirements,
00:09:27.785 --> 00:09:30.045 and you are able to effectively communicate your ideas,
00:09:30.195 --> 00:09:32.565 your thoughts in business meetings and team meetings.
00:09:32.665 --> 00:09:34.565 You have finished a significant portion of the series.
00:09:34.765 --> 00:09:37.765 I hope that you finish 100% complete the entire course,
00:09:38.045 --> 00:09:39.005 'cause it's going to be fun and
00:09:39.005 --> 00:09:40.045 it's going to be educational.
00:09:40.115 --> 00:09:41.965 Well done and keep going. I'll see you next time. 