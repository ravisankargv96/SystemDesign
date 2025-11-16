## Chapters
* 00:00 - A costly mistake
* 01:44 - Cache Setup
* 04:01 - Cache Consistency
* 09:56 - Cache Policies

## Transcript
00:00:00.125 --> 00:00:01.325 A few weeks passed without incident,
00:00:01.385 --> 00:00:02.525 but then the founder comes back
00:00:02.525 --> 00:00:04.445 and says, I didn't know Redis is so expensive.
00:00:04.545 --> 00:00:05.565 So you ask them, what do you mean?
00:00:05.665 --> 00:00:08.085 And they say, well, it's costing me about $2,000
00:00:08.145 --> 00:00:09.685 to host these Redis instances.
00:00:09.825 --> 00:00:12.845 And then you ask them, $2,000 is quite a bit for your scale.
00:00:12.985 --> 00:00:14.205 How many instances do you need?
00:00:14.205 --> 00:00:16.645 And he tells you, well, I need around three large instances.
00:00:16.955 --> 00:00:18.925 Whoa, that's a lot. That's a lot.
00:00:18.925 --> 00:00:20.685 So there's something wrong here. Okay?
00:00:20.685 --> 00:00:22.365 As an engineer, your instinct
00:00:22.665 --> 00:00:25.525 for using very large instances in small companies should
00:00:25.525 --> 00:00:27.445 kick in and you should feel like
00:00:27.445 --> 00:00:28.965 you're probably using the tool wrong.
00:00:29.065 --> 00:00:31.005 If you need this much compute capacity.
00:00:31.025 --> 00:00:32.525 You then ask them, what exactly
00:00:32.585 --> 00:00:33.765 are you doing in these caches?
00:00:33.785 --> 00:00:36.645 Uh, we talked about using maybe consistent hashing.
00:00:36.645 --> 00:00:38.245 We talked about using a global cache,
00:00:38.245 --> 00:00:40.445 which is why they're gone with Redis as a global instance.
00:00:40.585 --> 00:00:41.965 So what are you doing? And they say
00:00:41.965 --> 00:00:44.605 that we are using these caches to store T-shirts data,
00:00:44.785 --> 00:00:46.845 and what we do is we have three types
00:00:46.905 --> 00:00:48.325 of queries in these caches.
00:00:48.385 --> 00:00:50.685 The first one is when a user comes to the webpage
00:00:50.685 --> 00:00:53.285 and they want to see the most popular T-shirts ever,
00:00:53.285 --> 00:00:54.365 evergreen T-shirts,
00:00:54.365 --> 00:00:56.405 things which are always popular throughout all seasons.
00:00:56.585 --> 00:00:59.325 The second kind of query that a user has is show me the
00:00:59.565 --> 00:01:00.765 recently added T-shirts.
00:01:00.825 --> 00:01:02.965 So T-shirts, which have come new to the platform.
00:01:02.995 --> 00:01:04.805 Some people want to get their hands on them quickly.
00:01:04.875 --> 00:01:07.605 That is also filter, and so we store it in cache.
00:01:07.705 --> 00:01:10.925 The third kind of query that we have is a user's last seen
00:01:11.085 --> 00:01:13.405 T-shirts, meaning if I have gone through some shirts
00:01:13.505 --> 00:01:16.365 and I want to see them again, then if I go to the platform,
00:01:16.475 --> 00:01:18.965 I'll be able to see the T-shirts that I recently accessed
00:01:18.965 --> 00:01:20.445 that recently viewed T-shirts.
00:01:20.445 --> 00:01:23.525 So let's say I viewed these T-shirts as A, B, C, D.
00:01:23.525 --> 00:01:26.285 When I come back to the platform, I'll see them sorted
00:01:26.425 --> 00:01:28.925 as DCBA last recent,
00:01:29.035 --> 00:01:31.765 most recently viewed second most recently viewed and so on.
00:01:31.765 --> 00:01:33.405 So in that sorted order also.
00:01:33.405 --> 00:01:35.485 So you ask them, okay, that's interesting.
00:01:35.625 --> 00:01:39.005 You have user level T-shirt viewing information also in the
00:01:39.005 --> 00:01:40.005 cache, and they tell you yes.
00:01:40.145 --> 00:01:42.045 So at this point you have a rough idea of
00:01:42.045 --> 00:01:43.045 what is being stored.
00:01:43.105 --> 00:01:45.165 You can look at the code now to figure out what's wrong,
00:01:45.165 --> 00:01:46.925 looking at the code, you discover the following.
00:01:46.925 --> 00:01:48.645 The first thing is whenever there's a query
00:01:48.865 --> 00:01:50.805 for getting the most popular T-shirts,
00:01:50.945 --> 00:01:53.085 you are running an SQL query on the database,
00:01:53.265 --> 00:01:56.005 not on the cache, but on the database saying Select count
00:01:56.005 --> 00:01:59.205 star comm t-shirt Idy from T-shirt Views, group
00:01:59.225 --> 00:02:00.925 by t-shirt Idy order by Views.
00:02:01.185 --> 00:02:03.445 The count star Ls is views,
00:02:03.535 --> 00:02:05.885 which means basically you are querying the database
00:02:05.945 --> 00:02:08.325 to get the number of views on every T-shirt.
00:02:08.325 --> 00:02:09.765 You're grouping by the T-shirt Idy.
00:02:09.765 --> 00:02:10.765 So you're getting the number
00:02:10.845 --> 00:02:13.045 of views on every T-shirt every time a user tries
00:02:13.045 --> 00:02:14.725 to see the most popular T-shirts.
00:02:14.945 --> 00:02:16.405 Why is this happening? Why aren't you
00:02:16.525 --> 00:02:17.605 storing all this stuff in cache?
00:02:17.605 --> 00:02:18.725 Well, the founder tells you that.
00:02:18.745 --> 00:02:22.045 My engineers told me if you do that, then there is a chance
00:02:22.045 --> 00:02:23.125 of consistency loss,
00:02:23.215 --> 00:02:25.525 which means if I store these results in cache
00:02:25.545 --> 00:02:27.685 and somebody else comes and views the result,
00:02:27.825 --> 00:02:28.925 the answer in the database
00:02:28.925 --> 00:02:30.765 and the answer in the cache may mismatch.
00:02:30.905 --> 00:02:33.045 At this point, you realize that there is a problem maybe
00:02:33.045 --> 00:02:34.165 with the engineers also, so
00:02:34.165 --> 00:02:35.245 you can speak to them in a minute.
00:02:35.245 --> 00:02:37.765 Another thing that you notice is that the objects
00:02:37.765 --> 00:02:39.445 that are being stored in cache are very heavy.
00:02:39.535 --> 00:02:42.525 Every time a person is storing a T-shirt in cache,
00:02:42.655 --> 00:02:45.445 let's say I am the user, I enter your website,
00:02:45.805 --> 00:02:47.685 I look at the popular T-shirts here,
00:02:47.825 --> 00:02:49.245 and I access some T-shirts here.
00:02:49.315 --> 00:02:51.405 What will happen is those T-shirt objects,
00:02:51.495 --> 00:02:53.405 which can have a lot of metadata in it,
00:02:53.405 --> 00:02:56.085 will be stored in the cache against my user id.
00:02:56.105 --> 00:03:00.005 So the key is going to be user ID of the value is going
00:03:00.005 --> 00:03:02.285 to be a sorted array of T-shirts.
00:03:02.435 --> 00:03:05.645 Okay? And each of these T-shirt objects is a heavy object.
00:03:05.755 --> 00:03:07.285 Instead, what you can do is
00:03:07.285 --> 00:03:09.085 because cash memory is expensive, you want
00:03:09.085 --> 00:03:11.605 to keep the objects light, just store the T-shirt IDs,
00:03:11.665 --> 00:03:14.325 go access T-shirt id, A, B, C, and D.
00:03:14.505 --> 00:03:18.285 So in the order of DCBA, you'll be storing it in the ari,
00:03:18.285 --> 00:03:20.245 you won't be storing the info of the T-shirt there.
00:03:20.245 --> 00:03:22.765 If you want the info, then go and fetch it from the database
00:03:22.945 --> 00:03:25.525 or fetch it from a separate T-shirts cache itself.
00:03:25.625 --> 00:03:28.285 So every time now that you get a query for Gora wants
00:03:28.285 --> 00:03:29.925 to see the T-shirts that he's accessed,
00:03:29.925 --> 00:03:31.685 you get the IDs first from Cache,
00:03:31.685 --> 00:03:33.925 then you get the T-shirt information from cash.
00:03:34.145 --> 00:03:37.445 You merge these two responses and give a result to the user.
00:03:37.585 --> 00:03:39.765 How is this useful? Well, now for lots of users,
00:03:39.765 --> 00:03:41.325 you're not storing duplicate information.
00:03:41.355 --> 00:03:43.365 Okay? If go has seen the T-shirts, A, B, C, D,
00:03:43.365 --> 00:03:45.765 and you have seen the T-shirts, B, C, D, then,
00:03:45.795 --> 00:03:48.325 then the information for BC and D is not duplicated.
00:03:48.435 --> 00:03:49.605 Just the IDs are being stored,
00:03:49.625 --> 00:03:51.805 the metadata is not being stored in cache again and again.
00:03:51.825 --> 00:03:54.805 The benefit of this is you can basically store more
00:03:54.805 --> 00:03:55.965 information in lesser space.
00:03:56.065 --> 00:03:57.165 So you need fewer nodes
00:03:57.185 --> 00:03:59.525 or smaller nodes to store the same amount of information
00:03:59.555 --> 00:04:00.685 that reduces costs.
00:04:00.945 --> 00:04:03.005 Now these changes can only be made by an engineer.
00:04:03.185 --> 00:04:05.365 So you tell the founder that, listen, I need to speak
00:04:05.365 --> 00:04:07.165 with your engineers to affect these changes.
00:04:07.385 --> 00:04:09.165 And also I want to give them some theoretical
00:04:09.165 --> 00:04:10.525 understanding of how Cache works.
00:04:10.715 --> 00:04:13.085 What they have made here is a mistake calling the database
00:04:13.085 --> 00:04:15.205 every time they want to fetch an entry from Cache,
00:04:15.205 --> 00:04:17.005 which defeats the entire purpose of the cache.
00:04:17.025 --> 00:04:18.805 You don't want to be making the same number
00:04:18.805 --> 00:04:19.845 of queries to the database.
00:04:19.865 --> 00:04:21.645 If you are getting the value from database
00:04:21.645 --> 00:04:23.605 and storing it in cache and fetching it from the cache,
00:04:23.705 --> 00:04:25.725 you might as well just fetch it from the database directly.
00:04:25.725 --> 00:04:26.765 You schedule a meeting and
00:04:26.765 --> 00:04:27.965 now you're speaking with an engineer.
00:04:28.025 --> 00:04:29.445 The first thing you do is ask them,
00:04:29.705 --> 00:04:30.845 why did you write this query
00:04:30.945 --> 00:04:32.965 and populate the cache when you could fetch
00:04:32.965 --> 00:04:34.045 it directly from the database?
00:04:34.105 --> 00:04:36.765 So they tell you that the cache is here to make things fast,
00:04:36.905 --> 00:04:40.045 but unfortunately, I'm not able to use the data in the cache
00:04:40.045 --> 00:04:41.845 because the data can become stale.
00:04:41.865 --> 00:04:43.845 If I fetch the most popular T-shirts from Cache
00:04:43.955 --> 00:04:47.085 with their view count, it's possible that a new user goes
00:04:47.105 --> 00:04:50.485 and views one of these T-shirts changing the ordering
00:04:50.545 --> 00:04:52.045 of this rank list of popularity.
00:04:52.065 --> 00:04:54.485 So maybe the fifth most popular T-shirt now becomes the
00:04:54.485 --> 00:04:55.525 sixth most popular T-shirt,
00:04:55.525 --> 00:04:57.325 and the sixth one moves to the fifth position.
00:04:57.355 --> 00:04:58.405 This is possible, and
00:04:58.405 --> 00:05:00.165 because the latest data is in the database,
00:05:00.485 --> 00:05:01.925 I fet it directly from the database.
00:05:01.985 --> 00:05:03.125 So here you explain to them
00:05:03.125 --> 00:05:04.925 that you don't need the latest information.
00:05:04.925 --> 00:05:07.645 When it comes to popular t-shirts, it's possible
00:05:07.645 --> 00:05:10.045 that the fifth position has been beaten
00:05:10.105 --> 00:05:11.285 by the sixth position, but
00:05:11.285 --> 00:05:13.125 that can reflect in the cash one hour later.
00:05:13.235 --> 00:05:15.845 Also, as long as you're getting the top 10 most popular
00:05:16.085 --> 00:05:17.685 T-shirts, it's not going to affect the business.
00:05:17.835 --> 00:05:20.285 It's possible that the 11th t-shirt beats the 10th T-shirt.
00:05:20.285 --> 00:05:22.125 Is that a big deal? No, not really. Right?
00:05:22.125 --> 00:05:23.805 If the 11th T-shirt beats the 10th T-shirt
00:05:23.825 --> 00:05:26.685 and you get that update in two hours, that's fine.
00:05:26.745 --> 00:05:30.045 So the cache update should happen infrequently because
00:05:30.045 --> 00:05:32.005 otherwise you are just overriding the cache,
00:05:32.005 --> 00:05:34.605 getting the data and overriding it again in the next read
00:05:34.605 --> 00:05:37.485 query, and the engineer agrees, yes, if the owner wants this
00:05:37.485 --> 00:05:38.685 to happen, if they're okay
00:05:38.685 --> 00:05:41.165 with slightly scaled data, slightly old data, that's fine.
00:05:41.185 --> 00:05:43.885 If it's one hour old or six hours old, depends on
00:05:43.885 --> 00:05:47.005 what the product wants, we will be expiring the cash
00:05:47.005 --> 00:05:48.285 after one hour or six hours.
00:05:48.355 --> 00:05:49.885 This is known as cash expiry.
00:05:50.065 --> 00:05:52.485 You can expire the entire cache like we are doing here,
00:05:52.545 --> 00:05:55.005 or you can expire entries of particular keys.
00:05:55.145 --> 00:05:57.580 For example, if I'm not logged into the website for three
00:05:57.580 --> 00:05:59.565 or four hours, or if I'm not logged in for a day,
00:05:59.745 --> 00:06:00.885 you might expire my entry
00:06:00.885 --> 00:06:02.405 because I'm not a very active user.
00:06:02.545 --> 00:06:04.885 The second thing to note here is that the engineer thought,
00:06:05.105 --> 00:06:06.965 if I'm making updates, I need
00:06:06.965 --> 00:06:08.445 to make the updates in the database.
00:06:08.585 --> 00:06:10.325 And if I'm making read queries,
00:06:10.425 --> 00:06:12.325 that's the only time I can read from Cache.
00:06:12.425 --> 00:06:14.285 So to get the latest data, I actually need
00:06:14.285 --> 00:06:16.325 to query the database and populate the cache.
00:06:16.355 --> 00:06:20.245 Here you explain to them that caches can also be consistent.
00:06:20.355 --> 00:06:22.525 They can also have the latest data copy
00:06:22.735 --> 00:06:23.805 along with the database.
00:06:23.905 --> 00:06:25.645 So that would be called a consistent cache.
00:06:25.865 --> 00:06:28.365 The number of views that you see per T-shirt in the cache is
00:06:28.365 --> 00:06:30.045 the same that you'll see in a database,
00:06:30.105 --> 00:06:31.485 but fetching it from cache is faster.
00:06:31.585 --> 00:06:33.685 So this is great if you have a consistent cache
00:06:33.705 --> 00:06:35.525 and the way you keep the cache updated
00:06:35.625 --> 00:06:36.765 is called a write policy.
00:06:36.915 --> 00:06:38.525 It's also known as an update policy.
00:06:38.575 --> 00:06:39.765 There are many ways to do this,
00:06:39.985 --> 00:06:41.405 but since we are using Redis here,
00:06:41.425 --> 00:06:43.405 we will talk about the two things which are offered
00:06:43.405 --> 00:06:44.645 by Redis automatically.
00:06:44.705 --> 00:06:46.525 So the implementation will be extremely easy.
00:06:46.585 --> 00:06:48.605 The first one is called write through,
00:06:48.605 --> 00:06:50.205 which means all updates
00:06:50.545 --> 00:06:53.645 to the cache are also updated in the database.
00:06:53.745 --> 00:06:55.765 The way Redis ensures consistency is
00:06:55.925 --> 00:06:58.125 whenever you get an update query, you're going to first go
00:06:58.225 --> 00:06:59.525 and update the database.
00:06:59.635 --> 00:07:01.685 Only after you get an acknowledgement are you going
00:07:01.685 --> 00:07:04.165 to update your cache, and then you can go
00:07:04.305 --> 00:07:05.645 and give a response to the client.
00:07:05.665 --> 00:07:08.765 So all subsequent read queries will see the new data
00:07:08.765 --> 00:07:09.925 reflected in the cache.
00:07:10.075 --> 00:07:11.245 Also, this solves our problem.
00:07:11.255 --> 00:07:13.325 There is another approach that you can take here.
00:07:13.395 --> 00:07:15.645 When Redis gets an update query, it's going
00:07:15.645 --> 00:07:17.925 to update the cache first, and it's going to wait.
00:07:17.955 --> 00:07:19.285 It's going to wait and wait
00:07:19.345 --> 00:07:20.845 and wait till there is a point
00:07:20.845 --> 00:07:22.925 where you remove the entry from Cache.
00:07:23.095 --> 00:07:24.685 We'll see what are the times when you need
00:07:24.685 --> 00:07:25.725 to remove an entry from Cache.
00:07:25.785 --> 00:07:28.885 But whenever the cache is full, there's too much data here.
00:07:29.065 --> 00:07:30.565 You just can't take that kind of load,
00:07:30.625 --> 00:07:32.125 and you have limited the size of the cache.
00:07:32.195 --> 00:07:34.445 Some data has to be kicked out when it is kicked out,
00:07:34.445 --> 00:07:36.965 when it is evicted from Cache, you make sure
00:07:36.965 --> 00:07:39.045 that the changes are reflected in the database.
00:07:39.105 --> 00:07:41.765 So let's say there's a T-shirt, which was viewed 15 times,
00:07:41.835 --> 00:07:43.365 then 20 times, then 30 times.
00:07:43.545 --> 00:07:45.485 The total number of views is 65.
00:07:45.635 --> 00:07:47.365 That is not going to be updated in the cache.
00:07:47.465 --> 00:07:50.685 The moment the entry is evicted from Cache, you will go
00:07:50.905 --> 00:07:53.085 and add 65 to the database in one shot.
00:07:53.085 --> 00:07:54.205 Okay? Or you can make three queries
00:07:54.205 --> 00:07:56.045 of 15, 20, 30 doesn't really matter.
00:07:56.225 --> 00:07:57.445 The good thing about this is
00:07:57.445 --> 00:07:59.325 that the database is not being heavily
00:07:59.395 --> 00:08:00.965 bombarded with constant updates.
00:08:01.145 --> 00:08:03.165 So the load on the database is reduced.
00:08:03.495 --> 00:08:04.845 Redis manages most of the load.
00:08:04.845 --> 00:08:06.885 Since Redis has in memory data structures,
00:08:06.915 --> 00:08:09.205 it's usually much faster to update the in-memory data
00:08:09.365 --> 00:08:11.525 structures than to go and make updates in a db.
00:08:11.525 --> 00:08:13.805 And in this way, the engineers can ensure
00:08:13.805 --> 00:08:15.645 that the users get the latest entries.
00:08:15.835 --> 00:08:18.125 This is known as right behind caching,
00:08:18.125 --> 00:08:20.245 which means when a entry is being evicted,
00:08:20.305 --> 00:08:22.885 that's the time when you make a update to the database.
00:08:22.995 --> 00:08:26.365 It's a bit risky because if Red Redis crashes in
00:08:26.365 --> 00:08:29.285 between all the updates to those T-shirt views will be lost.
00:08:29.465 --> 00:08:31.525 As a founder, maybe you don't really care about it.
00:08:31.525 --> 00:08:33.285 You call the founder, you tell them, you know what?
00:08:33.285 --> 00:08:35.165 If we miss those views, the maximum number
00:08:35.165 --> 00:08:36.445 of views we'll miss is maybe an hour.
00:08:36.505 --> 00:08:37.645 So we'll expire the entry.
00:08:37.645 --> 00:08:40.405 That's also a time when you can go and update the database
00:08:40.425 --> 00:08:41.925 or it'll be affected from cache.
00:08:41.925 --> 00:08:43.805 That's a time when we'll go and update the database.
00:08:43.805 --> 00:08:46.165 Is it okay if you lose an hour worth of use
00:08:46.225 --> 00:08:47.565 and the founder says, yeah, that's fine.
00:08:47.585 --> 00:08:48.845 An hour is is not a problem.
00:08:48.945 --> 00:08:51.245 If this is a payments database, if there's a payments cash,
00:08:51.245 --> 00:08:53.405 then maybe you would want to write through policy.
00:08:53.545 --> 00:08:54.925 In this case, write back is good.
00:08:55.065 --> 00:08:58.245 It reduces costs because the db io calls have reduced.
00:08:58.275 --> 00:08:59.285 When it comes to caching,
00:08:59.285 --> 00:09:00.805 you can have many, many write policies.
00:09:00.805 --> 00:09:02.485 There's something called Write Aside.
00:09:02.485 --> 00:09:03.805 There's something called Write Around.
00:09:03.945 --> 00:09:05.845 You can read about these in the description.
00:09:05.965 --> 00:09:07.485 I have rarely seen them being used.
00:09:07.665 --> 00:09:08.925 The other thing that you can do
00:09:08.925 --> 00:09:10.725 with the cache is you can treat the cache
00:09:10.725 --> 00:09:13.125 as a separate entity and the database as a separate entity,
00:09:13.245 --> 00:09:14.285 meaning that interaction
00:09:14.285 --> 00:09:16.285 to the database happens directly from the app
00:09:16.285 --> 00:09:17.645 instead of happening through Redis.
00:09:17.745 --> 00:09:19.765 So whenever you're making an update to the database,
00:09:19.785 --> 00:09:21.325 you talk to it directly with an SQ query.
00:09:21.325 --> 00:09:23.285 When you're making an update to Redis, you talk
00:09:23.285 --> 00:09:24.485 to it directly when you're reading,
00:09:24.555 --> 00:09:27.045 then you may read from the database or from the cache.
00:09:27.045 --> 00:09:28.845 That is an application developer choice.
00:09:28.995 --> 00:09:30.965 This makes implementation a little more complicated.
00:09:31.485 --> 00:09:33.805 Facebook famously uses something called Mem Cache.
00:09:33.875 --> 00:09:36.645 Over there, they have this cache as a separate entity,
00:09:36.665 --> 00:09:38.245 and the database is a separate entity.
00:09:38.245 --> 00:09:39.845 They call it a look aside cache,
00:09:39.845 --> 00:09:41.485 meaning first you try the cache.
00:09:41.505 --> 00:09:43.285 If you don't get data, then you go
00:09:43.285 --> 00:09:44.485 and query the database yourself.
00:09:44.625 --> 00:09:46.045 Why in Redis, very often
00:09:46.045 --> 00:09:47.565 what happens is first you try the cache.
00:09:47.665 --> 00:09:50.045 If the cache doesn't have the entry, it goes
00:09:50.185 --> 00:09:53.045 and populates that entry from the database onto itself
00:09:53.065 --> 00:09:54.085 and then gives your response.
00:09:54.145 --> 00:09:56.525 So all of this is taken care of by the cache itself.
00:09:56.585 --> 00:09:57.605 Now, the engineer is happy.
00:09:57.675 --> 00:10:00.365 They have a much clearer idea of how to use the cache and
00:10:00.365 --> 00:10:02.365 therefore bring down the costs on the tech side.
00:10:02.365 --> 00:10:03.685 Should probably save the job soon.
00:10:04.305 --> 00:10:06.085 But there's one final piece of information you want
00:10:06.085 --> 00:10:07.645 to give them around caching, which is
00:10:07.795 --> 00:10:10.045 what is the access pattern that you're looking
00:10:10.045 --> 00:10:11.165 for In the cache, we know
00:10:11.165 --> 00:10:12.845 that the cache is storing three types of entries.
00:10:12.955 --> 00:10:15.805 Most popular T-shirts most recently added T-shirts
00:10:15.945 --> 00:10:17.605 and T-shirts, which are most recently
00:10:17.605 --> 00:10:18.645 being seen by the user.
00:10:18.745 --> 00:10:19.765 The first two are fine
00:10:19.765 --> 00:10:22.685 because they are shared across all users popularity
00:10:22.685 --> 00:10:24.045 and recently added T-shirts is not going
00:10:24.045 --> 00:10:25.485 to cause memory problems.
00:10:25.585 --> 00:10:27.085 But the third one is a little tricky.
00:10:27.385 --> 00:10:29.565 As you have more and more users, the number
00:10:29.565 --> 00:10:32.405 of cash entries you'll need will increase up to the point
00:10:32.405 --> 00:10:34.725 that the size of the cache may become very, very large.
00:10:34.785 --> 00:10:36.405 So let's say you have a million users,
00:10:36.555 --> 00:10:38.325 that means you'll have a million entries
00:10:38.465 --> 00:10:40.605 and each of them will be areas of IDs.
00:10:40.605 --> 00:10:41.805 That's a bit excessive.
00:10:41.825 --> 00:10:44.445 Can we reduce the size of this cache? Yes, absolutely.
00:10:44.645 --> 00:10:46.845 A logical thing to do is to look at users
00:10:46.945 --> 00:10:49.605 who are active users and just store their entries.
00:10:49.705 --> 00:10:51.285 Now, what do we mean by active users?
00:10:51.455 --> 00:10:54.525 There are two major ways to look at users who are active.
00:10:54.785 --> 00:10:57.845 One is people who keep coming back to the platform.
00:10:57.845 --> 00:10:59.845 So that will be the users who log in the most,
00:11:00.145 --> 00:11:02.605 who are the most frequent users of the platform.
00:11:02.705 --> 00:11:05.925 And the second way of thinking about activeness in a user is
00:11:05.925 --> 00:11:08.725 to look at who are the most recently active users.
00:11:08.825 --> 00:11:10.085 People who came yesterday.
00:11:10.085 --> 00:11:12.325 People who came today are probably more likely
00:11:12.345 --> 00:11:14.845 to look at their T-shirts than people who came a week back.
00:11:14.985 --> 00:11:17.645 So if you had to remove certain entries from the cache,
00:11:17.645 --> 00:11:20.765 if you had to store just the top most active users entries,
00:11:20.915 --> 00:11:23.645 then you would sort them in one of these ways.
00:11:23.905 --> 00:11:26.365 The number of times that they have logged into the website
00:11:26.465 --> 00:11:28.605 and the last time they logged into the website,
00:11:28.675 --> 00:11:31.445 once you have sorted them, you just take the top 10%
00:11:31.445 --> 00:11:33.885 of users, or you just take the top thousand entries.
00:11:33.975 --> 00:11:35.285 These will be stored in cash.
00:11:35.355 --> 00:11:37.525 Everybody else will be removed from cache.
00:11:37.545 --> 00:11:40.045 So the size of the cache is fixed at 1000
00:11:40.185 --> 00:11:42.645 and the memory requirements dramatically reduce.
00:11:42.905 --> 00:11:45.765 Now, what happens when a new user logs into the system?
00:11:45.975 --> 00:11:48.485 Let's say you want to add this user to the cache,
00:11:48.585 --> 00:11:50.365 and the cache has a thousand entries already.
00:11:50.515 --> 00:11:51.845 What entry will you remove?
00:11:51.865 --> 00:11:54.685 If you're looking at the most recent logins,
00:11:54.865 --> 00:11:58.005 the most recent usage of the platform, then you are going
00:11:58.005 --> 00:12:00.845 to use a policy called least recently used.
00:12:01.025 --> 00:12:02.205 Why is it least recent use?
00:12:02.235 --> 00:12:03.725 Well, you are going to evict the entry,
00:12:03.725 --> 00:12:05.285 which is least recently used in cache,
00:12:05.285 --> 00:12:06.805 meaning if you have a thousand entries
00:12:06.905 --> 00:12:09.765 and you have the last login time of all of those users,
00:12:09.985 --> 00:12:12.405 the user with the earliest login time will be removed from
00:12:12.405 --> 00:12:14.965 the cache, and this new user will be added to the cache.
00:12:14.995 --> 00:12:16.205 This is called an eviction.
00:12:16.305 --> 00:12:17.965 The old user was evicted,
00:12:17.985 --> 00:12:20.605 and the policy we used here is least recently used.
00:12:20.705 --> 00:12:22.445 You may also use a different policy called
00:12:22.535 --> 00:12:24.165 least frequently used here.
00:12:24.345 --> 00:12:26.525 If you have all the total number of logins
00:12:26.525 --> 00:12:29.685 of every user stored in cache, then when a new user logs in,
00:12:29.705 --> 00:12:31.805 the number of logins they I've had in total is just one
00:12:31.825 --> 00:12:34.605 and the cache entries, the top thousand entries may have
00:12:34.605 --> 00:12:36.045 hundreds of logins each.
00:12:36.185 --> 00:12:38.725 So this new user is not added to the cache.
00:12:38.825 --> 00:12:40.445 Do you see any problem here when it comes
00:12:40.445 --> 00:12:41.685 to least frequently used?
00:12:41.825 --> 00:12:44.125 The latest data or hot data takes a
00:12:44.125 --> 00:12:45.245 long time to reach the cache.
00:12:45.245 --> 00:12:48.045 This is one of the reasons why social media platforms prefer
00:12:48.045 --> 00:12:50.365 using least frequently used caches when it comes
00:12:50.365 --> 00:12:52.445 to activity than least frequently used
00:12:52.685 --> 00:12:54.885 'cause frequency of usage may long while back.
00:12:54.905 --> 00:12:56.765 You may have made many posts earlier,
00:12:56.905 --> 00:12:58.285 you may have made many videos earlier,
00:12:58.465 --> 00:13:00.485 but since you're not creating videos recently,
00:13:00.585 --> 00:13:02.005 we don't want to promote your content.
00:13:02.005 --> 00:13:03.085 Similarly, if you have users
00:13:03.105 --> 00:13:04.325 who have used your platform a lot,
00:13:04.345 --> 00:13:06.965 but in last, last Christmas, you don't want them in your,
00:13:07.385 --> 00:13:09.325 you want to get the users who have recently used
00:13:09.325 --> 00:13:10.765 your platform to be served better.
00:13:10.865 --> 00:13:12.525 The algorithm which decides on
00:13:12.555 --> 00:13:15.725 what entry should be depicted from cash so that the amount
00:13:15.725 --> 00:13:17.405 of memory used by the cash is constraint is
00:13:17.405 --> 00:13:18.725 called an eviction policy.
00:13:18.725 --> 00:13:21.005 Eviction policies determine to a large extent
00:13:21.005 --> 00:13:22.125 how well a cash performs.
00:13:22.255 --> 00:13:24.885 Right? Policies also determine how well a cash performs,
00:13:24.935 --> 00:13:27.165 along with the consistency of the cache.
00:13:27.265 --> 00:13:29.725 The placement and data distribution also affect
00:13:29.745 --> 00:13:30.805 the performance of a cache.
00:13:30.835 --> 00:13:33.325 With these four factors, you can design a very,
00:13:33.325 --> 00:13:34.805 very good cache for any system
00:13:34.825 --> 00:13:37.485 and for fancy t-shirts dot io, the engineer is now convinced
00:13:37.515 --> 00:13:39.245 that their cache is going to perform well. 