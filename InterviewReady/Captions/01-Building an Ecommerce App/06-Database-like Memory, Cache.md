## Chapters
* 00:00 - The page is slow!
* 00:39 - Data Copies for Caching
* 02:38 - Implementing Caching
* 03:40 - Global vs. Local Cache
* 07:51 - Data Placement - Sharding
* 11:08 - Fault Tolerance
* 13:01 - Consistent Hashing
* 17:20 - Improvement: Virtual Servers

## Transcript
00:00:00.000 --> 00:00:02.165 Now fancy t-shirts dot io has a new situation.
00:00:02.225 --> 00:00:03.245 The founder has come to you
00:00:03.245 --> 00:00:05.805 and said, A lot of my customers claim that the app
00:00:05.905 --> 00:00:07.165 and the website are slow.
00:00:07.185 --> 00:00:09.125 So what you do is check the CDN solution.
00:00:09.125 --> 00:00:10.285 Things seem to be working fine.
00:00:10.345 --> 00:00:11.845 You try to load the page
00:00:11.985 --> 00:00:13.885 and the page load speed is pretty fast.
00:00:13.985 --> 00:00:15.005 So what exactly is slow?
00:00:15.025 --> 00:00:16.685 The founder then tells you that you realize
00:00:16.685 --> 00:00:19.285 that the products page, the place where you get
00:00:19.405 --> 00:00:22.045 to see all the T-shirts and get to buy them is quite slow.
00:00:22.145 --> 00:00:24.125 It loads slowly. So is this a CDN issue?
00:00:24.125 --> 00:00:26.765 Digging into the logs, digging into the network tab, you see
00:00:26.765 --> 00:00:28.165 that the call to the server
00:00:28.505 --> 00:00:31.165 to get the T-shirts is taking time.
00:00:31.205 --> 00:00:33.045 Fetching the images is not taking time,
00:00:33.185 --> 00:00:35.045 but just getting the list of T-shirts
00:00:35.145 --> 00:00:36.885 to show getting those URLs
00:00:36.945 --> 00:00:39.085 to fetch from the CDN that is taking time.
00:00:39.085 --> 00:00:40.765 Things are working fine on CloudFront,
00:00:40.825 --> 00:00:42.045 but the server is slow.
00:00:42.045 --> 00:00:43.525 What do you do? A fundamental approach
00:00:43.525 --> 00:00:46.765 to reducing latency in computer science is getting data
00:00:46.875 --> 00:00:48.845 that a system needs close to it.
00:00:48.905 --> 00:00:51.565 In our case, we are looking for getting the products data.
00:00:51.625 --> 00:00:54.165 We want our products data to be in the browser if possible.
00:00:54.165 --> 00:00:55.965 When the user loads the page, one
00:00:55.965 --> 00:00:58.845 of the things we can do is asynchronously make a call.
00:00:59.105 --> 00:01:01.085 The moment the user lands on our homepage,
00:01:01.145 --> 00:01:04.125 the front end makes a query immediately when the page is
00:01:04.125 --> 00:01:05.165 loaded, asynchronously,
00:01:05.185 --> 00:01:06.485 and when you get a response,
00:01:06.585 --> 00:01:08.685 the front end can store this in the local browser.
00:01:08.755 --> 00:01:10.485 When the user goes to the products page,
00:01:10.505 --> 00:01:11.605 the call is already resolved.
00:01:11.665 --> 00:01:13.085 All you have to do is get images from the
00:01:13.125 --> 00:01:14.285 CBN, which is fast enough.
00:01:14.385 --> 00:01:16.685 So this would be an asynchronous approach
00:01:16.705 --> 00:01:19.005 to solving the problem so that we can bring the data close
00:01:19.005 --> 00:01:20.325 to the user when they need it.
00:01:20.425 --> 00:01:22.925 In this case, we are getting the T-shirts data into their
00:01:22.925 --> 00:01:24.725 browser before they query for it.
00:01:24.875 --> 00:01:28.165 This concept of taking a temporary copy of the data
00:01:28.385 --> 00:01:32.445 and storing it somewhere for low latency is called caching.
00:01:32.505 --> 00:01:35.885 So your browser is not storing the T-shirts data.
00:01:35.985 --> 00:01:38.525 It doesn't know for sure how many T-shirts have been sold,
00:01:38.705 --> 00:01:41.165 how many are available, whether the T-shirt has
00:01:41.165 --> 00:01:42.245 been put out of stock.
00:01:42.345 --> 00:01:44.685 All of this stuff is not known by the browser,
00:01:44.945 --> 00:01:47.245 but it's making a calculated guess.
00:01:47.475 --> 00:01:49.845 It's saying that you know, in the next 10, 15 seconds,
00:01:50.205 --> 00:01:51.725 nobody's going to buy t-shirts,
00:01:51.905 --> 00:01:54.285 so I'll just fetch the T-shirts and show it on the browser.
00:01:54.355 --> 00:01:55.725 This concept is called caching
00:01:55.725 --> 00:01:57.525 and in our case, we are caching on the browser.
00:01:57.525 --> 00:02:00.205 However, caching is a fundamental concept
00:02:00.225 --> 00:02:02.765 of computer science and it can be brought in any level
00:02:02.945 --> 00:02:05.125 of the request path of the critical path.
00:02:05.145 --> 00:02:07.725 In our case, we are fetching products from a server.
00:02:07.905 --> 00:02:09.765 We can cache the data there.
00:02:09.955 --> 00:02:11.885 Also, the benefit of this is
00:02:12.285 --> 00:02:15.445 whenever a user requests the products, it's going
00:02:15.445 --> 00:02:17.005 to get a cached response.
00:02:17.005 --> 00:02:18.085 It's going to get the data
00:02:18.085 --> 00:02:19.485 that is temporally stored on the server.
00:02:19.635 --> 00:02:22.045 This means that even if they make an asynchronous request
00:02:22.045 --> 00:02:23.645 like they did earlier, the response of
00:02:23.645 --> 00:02:24.885 that asynchronous request will be faster.
00:02:24.985 --> 00:02:26.165 So the user comes to the homepage
00:02:26.165 --> 00:02:27.525 and quickly clicks on the product page.
00:02:27.525 --> 00:02:29.325 They'll still see data quickly populated.
00:02:29.325 --> 00:02:31.325 Another thing is if they go directly to the product switch,
00:02:31.325 --> 00:02:32.325 they'll see the data quickly.
00:02:32.385 --> 00:02:34.525 So in many ways this is a superior approach,
00:02:34.525 --> 00:02:37.925 having the data stored close to what really needs it.
00:02:37.985 --> 00:02:40.925 So you bring this idea forward to the founder, you tell them
00:02:40.925 --> 00:02:43.725 that you know you could cache data since this API is slow,
00:02:43.735 --> 00:02:46.245 maybe the a p is squaring for data, which is taking time.
00:02:46.585 --> 00:02:48.765 Why don't you take the data from the database
00:02:48.985 --> 00:02:51.525 and store it temporarily in your server in memory?
00:02:51.665 --> 00:02:52.845 So then they ask you, how can I
00:02:52.845 --> 00:02:54.005 store this data on the server?
00:02:54.265 --> 00:02:56.925 You can store it as a map, you can store it as key,
00:02:56.925 --> 00:03:00.045 which is product id, and then you have a value next to it.
00:03:00.045 --> 00:03:02.565 So in a map you have a key and a value of the product ID
00:03:02.565 --> 00:03:04.285 and then you have all the data for that product.
00:03:04.385 --> 00:03:06.325 If you store this as a map, it's quite safe,
00:03:06.425 --> 00:03:08.405 but there are libraries out there in the world.
00:03:08.405 --> 00:03:09.445 Caching is a, like I said,
00:03:09.445 --> 00:03:10.765 fundamentally concept of computer science.
00:03:10.765 --> 00:03:13.725 So there's a ton of libraries which manage caching for you.
00:03:13.825 --> 00:03:16.685 You don't have to think of how do I efficiently store
00:03:16.685 --> 00:03:18.005 data, retrieve data from it.
00:03:18.025 --> 00:03:19.885 You just have to do a get query and a set query.
00:03:20.205 --> 00:03:21.445 Whenever you want to update the cache,
00:03:21.645 --> 00:03:22.765 whenever you want to get the data and
00:03:22.765 --> 00:03:24.805 before your friend can head back, you stop them Say that.
00:03:24.955 --> 00:03:26.245 Look, before you create tickets,
00:03:26.305 --> 00:03:28.765 before you actually start working on this problem, it's best
00:03:28.765 --> 00:03:30.445 to know about this concept in detail
00:03:30.445 --> 00:03:32.605 because there's various approaches for caching.
00:03:32.605 --> 00:03:35.325 Just like we said, where do we place the cache is a problem.
00:03:35.435 --> 00:03:38.085 Similarly, there's a lot of questions which come up for
00:03:38.115 --> 00:03:39.485 what kind of cache do you want to use?
00:03:39.575 --> 00:03:42.725 Let's look into this. The first question is do you want your
00:03:42.725 --> 00:03:43.805 cache in your server
00:03:43.985 --> 00:03:45.965 or do you want to keep a separate server?
00:03:46.245 --> 00:03:47.565 A cache server, which is going
00:03:47.565 --> 00:03:50.245 to serve all cache requests by all servers.
00:03:50.265 --> 00:03:52.725 So when you horizontally scale from one server, you move
00:03:52.725 --> 00:03:55.045 to three servers from three to nine, nine to 20,
00:03:55.305 --> 00:03:56.565 you have all of these servers.
00:03:56.635 --> 00:03:58.405 Each of them could keep a cache inside them.
00:03:58.405 --> 00:03:59.845 Each of them could have a map inside them.
00:03:59.915 --> 00:04:02.845 This would be called an in-memory cache, a cache which is
00:04:02.845 --> 00:04:04.085 inside the memory of the server.
00:04:04.185 --> 00:04:06.925 The benefit of this is that this cache is extremely fast.
00:04:06.985 --> 00:04:10.005 The moment you get a request, all the server has to do is go
00:04:10.005 --> 00:04:12.125 and fetch a line from its cache memory.
00:04:12.265 --> 00:04:14.605 So this would be in microseconds
00:04:14.605 --> 00:04:15.645 and then you get a response.
00:04:15.785 --> 00:04:17.045 You don't even need a response.
00:04:17.045 --> 00:04:19.685 You're basically doing a function call, getting the data,
00:04:20.025 --> 00:04:21.165 and then working with it.
00:04:21.265 --> 00:04:23.245 The other benefit is that usually this cache
00:04:23.245 --> 00:04:24.285 is quite simple to implement.
00:04:24.315 --> 00:04:25.845 Like I said, you can have a simple map,
00:04:25.865 --> 00:04:27.485 but you can also use a library that stands
00:04:27.485 --> 00:04:29.925 of libraries which do this for you in all languages
00:04:29.945 --> 00:04:32.845 and Java Golang Python caching is something
00:04:32.845 --> 00:04:35.245 that you can find if you just start searching on GitHub.
00:04:35.265 --> 00:04:39.085 One drawback of this though is that if your server crashes,
00:04:39.145 --> 00:04:41.725 if your server stops when you bring it back up,
00:04:41.785 --> 00:04:43.365 the cache will have to be repopulated
00:04:43.365 --> 00:04:45.005 because this thing is in memory.
00:04:45.075 --> 00:04:46.965 When the server restarts, the memory is refreshed.
00:04:46.965 --> 00:04:48.925 If you have a ongoing order,
00:04:49.075 --> 00:04:50.765 that memory is going to be lost.
00:04:50.945 --> 00:04:53.165 You will have to fetch it back from the database
00:04:53.265 --> 00:04:54.925 so when the server comes back, it'll have
00:04:54.925 --> 00:04:56.605 to fetch all the products from the database
00:04:56.605 --> 00:04:58.085 before it can serve requests quickly.
00:04:58.225 --> 00:05:00.485 The other problem is whenever you have an update in your
00:05:00.685 --> 00:05:03.045 database, let's say a person buys a T-shirt.
00:05:03.065 --> 00:05:05.085 So the count of T-shirts which are available has
00:05:05.085 --> 00:05:07.085 to be updated since you have multiple servers
00:05:07.185 --> 00:05:09.445 and each of them have their own version of the cash.
00:05:09.625 --> 00:05:11.925 If a person buys a T-shirt, all of the servers
00:05:12.025 --> 00:05:15.325 who are having this key, this same T-shirt ID will have
00:05:15.325 --> 00:05:16.725 to decrement their count.
00:05:16.785 --> 00:05:18.725 So for example, you have server 1, 2, 3.
00:05:18.755 --> 00:05:21.165 Each of them know that the count of T-shirt ID one is five.
00:05:21.225 --> 00:05:23.165 So there are five T-shirt ID ones remaining
00:05:23.185 --> 00:05:24.805 and one, two and three know about it.
00:05:24.915 --> 00:05:28.005 When a person places a buy order on server number one,
00:05:28.145 --> 00:05:29.645 it decrements its count to four.
00:05:29.705 --> 00:05:31.045 But what about server two and three?
00:05:31.045 --> 00:05:32.245 Their account is still five.
00:05:32.305 --> 00:05:33.965 So you need a way for some sort
00:05:33.965 --> 00:05:35.445 of coordination between the caches.
00:05:35.555 --> 00:05:37.485 This can be rather complex, okay?
00:05:37.485 --> 00:05:38.925 Especially if you are managing it.
00:05:38.925 --> 00:05:40.365 There's a library to take care of this.
00:05:40.365 --> 00:05:41.845 If there's a black box, this would be really nice.
00:05:41.985 --> 00:05:44.845 The advantages of and in memory cache are it's fast
00:05:45.105 --> 00:05:46.205 and it's simple to implement.
00:05:46.305 --> 00:05:48.365 The drawback is that the coordination
00:05:48.365 --> 00:05:49.445 between caches is difficult
00:05:49.465 --> 00:05:51.965 and if you have any loss of server,
00:05:52.195 --> 00:05:54.445 then repopulating the cache could take time.
00:05:54.445 --> 00:05:55.525 There are two other benefits
00:05:55.525 --> 00:05:57.685 of having a separate cache server.
00:05:57.985 --> 00:06:00.605 One is that the data duplication is usually less so.
00:06:00.605 --> 00:06:02.125 So if you have a bunch of servers,
00:06:02.135 --> 00:06:04.725 let's say you have 10 servers, all of them having
00:06:04.725 --> 00:06:06.245 that in memory cache, then all
00:06:06.245 --> 00:06:08.965 of them will have duplicated data for T-shirt ID one,
00:06:09.055 --> 00:06:10.845 it'll have the product information and so on.
00:06:10.865 --> 00:06:13.365 But if you have just a single cache server
00:06:14.085 --> 00:06:15.365 storing T-shirt ID one data,
00:06:15.555 --> 00:06:18.325 then not only is updating it easier, but it's a single copy.
00:06:18.385 --> 00:06:20.165 So the amount of total memory, cache memory
00:06:20.165 --> 00:06:22.125 that you need in the entire system is less.
00:06:22.475 --> 00:06:24.445 Also architecturally, this is something
00:06:24.445 --> 00:06:25.485 that engineers will prefer.
00:06:25.625 --> 00:06:27.245 If you have a cache server
00:06:27.425 --> 00:06:29.285 and you have a bunch of application servers.
00:06:29.285 --> 00:06:31.245 Application servers are things which are taking your API
00:06:31.245 --> 00:06:33.165 requests and performing application duties.
00:06:33.345 --> 00:06:34.805 If you have those separated
00:06:34.805 --> 00:06:36.165 and you have a cache server separated,
00:06:36.265 --> 00:06:38.765 you can scale up the cache independently.
00:06:38.765 --> 00:06:40.005 You can vertically scale the cache.
00:06:40.005 --> 00:06:42.325 You can horizontally scale the cache without needing
00:06:42.325 --> 00:06:44.685 to restart the servers without having any effect on
00:06:44.685 --> 00:06:45.725 the application servers.
00:06:45.745 --> 00:06:46.805 If your team becomes really big
00:06:46.805 --> 00:06:47.805 and you start making profits,
00:06:47.875 --> 00:06:50.285 then maybe a team which manages caches
00:06:50.465 --> 00:06:53.725 or just optimizes on the caches looks at the access patterns
00:06:53.725 --> 00:06:56.205 the way that the cache is being used and optimizes on that.
00:06:56.265 --> 00:06:58.085 So it becomes a separate engineering product.
00:06:58.185 --> 00:06:59.205 The rest of your engineers,
00:06:59.205 --> 00:07:01.165 your application engineers are using this cache now.
00:07:01.265 --> 00:07:03.045 So looking at these two approaches,
00:07:03.355 --> 00:07:06.005 what do you think makes more sense If the total amount
00:07:06.005 --> 00:07:08.365 of products in the system is less?
00:07:08.585 --> 00:07:10.565 If you are looking for very low latency,
00:07:10.565 --> 00:07:12.445 that's not a real problem in our case here,
00:07:12.445 --> 00:07:14.125 but if you're looking for extremely low latency
00:07:14.265 --> 00:07:16.205 and in-memory cache makes a lot of sense.
00:07:16.385 --> 00:07:19.565 In our case, we are going to be having a global cache,
00:07:19.805 --> 00:07:21.405 a single cache, which is going
00:07:21.405 --> 00:07:24.085 to be serving requests from other servers for get input.
00:07:24.115 --> 00:07:25.285 This can be a Redis instance.
00:07:25.285 --> 00:07:27.485 You must have heard of Redis somewhere or the other.
00:07:27.485 --> 00:07:29.085 It can also be a mem cache instance.
00:07:29.425 --> 00:07:31.045 Mam C can actually be in memory cache.
00:07:31.045 --> 00:07:34.565 Also what we go for is a single global cache instance.
00:07:34.745 --> 00:07:36.805 It complicates our architecture to some extent
00:07:36.805 --> 00:07:39.965 because now a lot of requests have to first go to cache
00:07:39.985 --> 00:07:42.125 and then you have this network call which may pass
00:07:42.185 --> 00:07:43.685 or fail depending on the result.
00:07:43.905 --> 00:07:45.405 You go to the server and
00:07:45.405 --> 00:07:47.045 after getting the result, you return
00:07:47.085 --> 00:07:48.285 a response to the UI page.
00:07:48.465 --> 00:07:50.405 Now the second type of question which can come when you are
00:07:50.405 --> 00:07:53.525 using a cache is how is data distributed
00:07:53.715 --> 00:07:55.045 amongst cache servers?
00:07:55.185 --> 00:07:58.525 As your system scales, a single cache server may not be able
00:07:58.525 --> 00:08:00.645 to answer all of the queries that you have in the system.
00:08:00.785 --> 00:08:01.805 So instead of doing that,
00:08:01.805 --> 00:08:04.085 what you do is you distribute the load,
00:08:04.145 --> 00:08:06.525 you have multiple cache servers serving
00:08:06.745 --> 00:08:07.845 all the requests in the system.
00:08:07.955 --> 00:08:10.205 Just imagine you have one cache server for India
00:08:10.205 --> 00:08:11.445 and one cache server for the us.
00:08:11.705 --> 00:08:14.445 So you have distributed the load according
00:08:14.445 --> 00:08:15.765 to geographical region
00:08:15.865 --> 00:08:18.725 and now what kind of data should you store in these caches?
00:08:18.825 --> 00:08:20.845 That's a question. One option would
00:08:20.845 --> 00:08:22.245 be whatever the servers ask for.
00:08:22.305 --> 00:08:23.725 So when the Indian server asks
00:08:23.725 --> 00:08:25.365 for a T-shirt, go and fetch it.
00:08:25.385 --> 00:08:28.405 If the US server asks for a Indian T-shirt, go and fetch it.
00:08:28.405 --> 00:08:30.925 That's okay. I mean even if the US cache has a Indian
00:08:31.045 --> 00:08:32.605 T-shirt inside it, that's not a problem.
00:08:32.705 --> 00:08:35.085 And if the Indian cache has US T-shirts inside them,
00:08:35.145 --> 00:08:37.365 the data for that, that's not a problem That works.
00:08:37.625 --> 00:08:40.165 Uh, but here again you see the duplication happening.
00:08:40.345 --> 00:08:42.765 Indian caches have both US and Indian T-shirts.
00:08:42.865 --> 00:08:45.165 US caches have both Indian and US T-shirts.
00:08:45.385 --> 00:08:48.165 So maybe the cache is not being efficiently utilized.
00:08:48.185 --> 00:08:49.685 You could have reduced a duplication here
00:08:49.825 --> 00:08:52.125 and it's a one-off thing that the Indian cache is going
00:08:52.125 --> 00:08:53.845 to call for a US T-shirt and vice versa.
00:08:54.025 --> 00:08:56.605 So here you may strategically place your data close
00:08:56.605 --> 00:08:57.685 to where it is expected.
00:08:57.825 --> 00:09:00.405 The Indian cache has only Indian T-shirts data
00:09:00.465 --> 00:09:02.765 and the US cache has only US T-shirts data.
00:09:02.865 --> 00:09:05.285 If you want to get the other country's data, go
00:09:05.285 --> 00:09:06.325 and fetch it from the database
00:09:06.465 --> 00:09:08.725 or you can fetch it from the other country's cache.
00:09:08.795 --> 00:09:10.525 This is interesting, this algorithm
00:09:10.525 --> 00:09:11.765 where you take your data set
00:09:11.785 --> 00:09:15.005 and split it according to a property is called sharding.
00:09:15.005 --> 00:09:17.565 In our case, we are splitting according to country type
00:09:17.665 --> 00:09:18.885 or country type.
00:09:18.945 --> 00:09:21.125 You can also say that this cache is going
00:09:21.125 --> 00:09:23.845 to be storing data only for the user IDs from one 200.
00:09:23.995 --> 00:09:25.765 This cache is going to be storing data only
00:09:25.765 --> 00:09:27.365 for user IDs from a hundred plus.
00:09:27.515 --> 00:09:31.165 That assigns ranges to the data that each cache manages.
00:09:31.275 --> 00:09:32.965 This concept is called sharding,
00:09:32.965 --> 00:09:34.565 and within each of these regions you
00:09:34.565 --> 00:09:35.725 may need to scale the caches.
00:09:35.745 --> 00:09:37.645 So let's say the US region has a lot of load.
00:09:37.745 --> 00:09:40.125 You bring in from a single cache to two, two to three,
00:09:40.225 --> 00:09:42.725 and now when a request comes to the US region
00:09:42.785 --> 00:09:44.885 and it needs to fetch data from the cache, it needs
00:09:44.885 --> 00:09:47.765 to somehow identify which cache should I call internally.
00:09:47.865 --> 00:09:50.925 The entire cache system is managing all data IDs from a
00:09:50.925 --> 00:09:53.885 hundred plus, but internally it might be 102 hundred
00:09:53.885 --> 00:09:56.245 thirty three, a hundred thirty three, a hundred sixty six,
00:09:56.265 --> 00:09:57.925 and 166 to 200.
00:09:58.025 --> 00:10:01.245 So internally you might have split the data shards.
00:10:01.255 --> 00:10:04.205 Again, the practical way to do this in a system is
00:10:04.205 --> 00:10:05.645 to use the concept of hashing.
00:10:05.645 --> 00:10:07.325 So when a request comes to the US server,
00:10:07.395 --> 00:10:10.645 what you do is you take the hash of the T-shirt id.
00:10:10.645 --> 00:10:13.805 If you had got one to four, you would've gotten the modular
00:10:13.835 --> 00:10:14.925 with three as one.
00:10:14.945 --> 00:10:17.725 If it was one to five, the modular with three would be two.
00:10:17.745 --> 00:10:20.605 So the values are between zero to three.
00:10:20.605 --> 00:10:22.885 That's the total number of servers you have these act
00:10:22.905 --> 00:10:23.925 as server indexes.
00:10:23.945 --> 00:10:26.245 So you got a request for a T-shirt id.
00:10:26.265 --> 00:10:27.885 You took the hash of the T-shirt idy,
00:10:27.885 --> 00:10:30.725 you got a number modular with three, gave you the server id,
00:10:30.725 --> 00:10:32.005 which is going to solve this request.
00:10:32.025 --> 00:10:35.085 What's the benefit of this? Why? Well, it's load balancing.
00:10:35.145 --> 00:10:37.685 We are load balancing the caches, so we are sending requests
00:10:37.705 --> 00:10:39.765 to one of the caches all the time
00:10:39.915 --> 00:10:41.365 depending on the T-shirt idy.
00:10:41.365 --> 00:10:44.885 The benefit of this is that since the hash is constant,
00:10:45.015 --> 00:10:47.045 since the hash of a T-shirt, ID cannot change
00:10:47.045 --> 00:10:48.805 because the T-shirt ID itself cannot change.
00:10:48.945 --> 00:10:50.805 The cache server that is going to respond
00:10:50.805 --> 00:10:52.925 to these requests is always going to be the same.
00:10:52.945 --> 00:10:56.205 So there won't be any duplication of T-shirt data
00:10:56.275 --> 00:10:57.365 between the caches.
00:10:57.365 --> 00:11:00.445 They're going to individually serve a set of T-shirts, a set
00:11:00.445 --> 00:11:01.765 of T-shirts, a set of T-shirts.
00:11:01.765 --> 00:11:02.965 This is great. We are able
00:11:02.965 --> 00:11:04.605 to horizontally scale up our cache.
00:11:04.605 --> 00:11:06.445 We are able to load balance in our cache.
00:11:06.445 --> 00:11:08.005 We are using two fundamental concepts
00:11:08.005 --> 00:11:09.045 of computer science together.
00:11:09.045 --> 00:11:11.845 There is one problem though, what happens if one
00:11:11.845 --> 00:11:13.325 of your caches crashes?
00:11:13.385 --> 00:11:16.685 One of them fails. So cache server with ID one has failed.
00:11:16.785 --> 00:11:18.685 The one in the center has failed. This is a problem.
00:11:18.705 --> 00:11:20.885 You have cache server with ID zero
00:11:20.885 --> 00:11:22.645 and two working, but one has failed.
00:11:22.645 --> 00:11:26.085 So all requests which belong to one, all T-shirt IDs,
00:11:26.085 --> 00:11:28.085 which one hashed and modular three give
00:11:28.085 --> 00:11:29.165 you one, are now failing.
00:11:29.195 --> 00:11:31.285 What do you do? The smart thing to do would be
00:11:31.285 --> 00:11:33.405 to auto recover the system to say that, well,
00:11:33.405 --> 00:11:35.725 we had three servers earlier, now we just have to take half
00:11:35.725 --> 00:11:38.085 of the requests, send it to the first server, take half
00:11:38.085 --> 00:11:39.885 of the requests, send it to the second server.
00:11:39.985 --> 00:11:42.005 In this way, you can kind of autoscale your system.
00:11:42.105 --> 00:11:43.645 You can add and remove servers.
00:11:43.905 --> 00:11:46.285 So if tomorrow you add two more servers from two,
00:11:46.285 --> 00:11:47.965 you become four, then you'll take a quarter
00:11:47.965 --> 00:11:49.285 of the request and send them to each one.
00:11:49.305 --> 00:11:51.205 So the hash modular will become four.
00:11:51.385 --> 00:11:52.765 If you lose two servers,
00:11:52.765 --> 00:11:54.645 then the the hash modular becomes two as simple
00:11:54.705 --> 00:11:57.605 as take the hash of the T-shirt ID modular with the number
00:11:57.605 --> 00:11:59.805 of servers and you have the server ID in front of you.
00:11:59.905 --> 00:12:01.965 The problem with this is whenever you lose
00:12:02.105 --> 00:12:05.165 or add a server, some data has to be loaded into the system.
00:12:05.165 --> 00:12:07.565 When you lose a server, the remaining servers have
00:12:07.565 --> 00:12:09.405 to load the data that the server just lost.
00:12:09.425 --> 00:12:11.365 Either you lost the server or you shut it down
00:12:11.365 --> 00:12:12.445 because you were like, you know,
00:12:12.485 --> 00:12:13.605 I don't need to pay for this much.
00:12:13.665 --> 00:12:15.205 My remaining cash servers can manage
00:12:15.385 --> 00:12:16.565 the load that we have right now.
00:12:16.585 --> 00:12:18.205 So at night, you want to maybe reduce the number
00:12:18.205 --> 00:12:20.325 of cash servers that you have and during peak hours you want
00:12:20.325 --> 00:12:21.645 to increase the number of cash servers that you have.
00:12:21.925 --> 00:12:24.525 Whenever you're doing this, there is some data that has
00:12:24.525 --> 00:12:25.685 to be loaded from the database.
00:12:25.745 --> 00:12:27.685 Why is this the case? Well, if you lost a server,
00:12:28.035 --> 00:12:31.125 then it was serving some data and it has to distribute it.
00:12:31.145 --> 00:12:33.765 But if you added a server, some of the data from the rest
00:12:33.765 --> 00:12:35.325 of the servers has to be pulled out
00:12:35.425 --> 00:12:36.765 and sent to this new server
00:12:36.765 --> 00:12:38.565 because it's going to manage some requests.
00:12:38.705 --> 00:12:41.245 The overall load on the rest of the system will reduce
00:12:41.265 --> 00:12:43.405 and it has to migrate to this new cache.
00:12:43.515 --> 00:12:45.845 That is a heavy operation cache.
00:12:46.305 --> 00:12:49.605 Warmup or cache readiness is something which takes time.
00:12:49.705 --> 00:12:51.325 In some cases it can take seconds.
00:12:51.665 --> 00:12:53.365 In some cases, very large cases.
00:12:53.745 --> 00:12:56.045 It can take literally minutes and hours.
00:12:56.265 --> 00:12:58.685 So for example, Facebook mcast, I mean if you do it
00:12:58.685 --> 00:13:00.285 with simple algorithms, it can take hours.
00:13:00.465 --> 00:13:02.245 You don't want that. What do you want to do here?
00:13:02.245 --> 00:13:05.245 This is where a big famous algorithm makes its appearance.
00:13:05.355 --> 00:13:06.925 It's called consistent hashing,
00:13:06.925 --> 00:13:08.925 and the whole idea of consistent hashing is
00:13:08.925 --> 00:13:12.485 to reduce the amount of data migration of data loading
00:13:12.485 --> 00:13:14.965 that you need when your system scales up
00:13:14.985 --> 00:13:17.725 or scales down so you can reconfigure your number
00:13:17.725 --> 00:13:20.925 of cache servers without having to wait for a long time
00:13:21.025 --> 00:13:22.685 for the data to be loaded from the tv.
00:13:22.745 --> 00:13:24.005 That's its main idea, okay?
00:13:24.005 --> 00:13:25.725 That's the purpose of consistent hashing.
00:13:25.965 --> 00:13:28.445 Let's see how it works. Let's take all the T-shirts
00:13:28.445 --> 00:13:30.845 that we have with ID zero to N
00:13:30.985 --> 00:13:32.565 and plot them on a number line.
00:13:32.665 --> 00:13:34.885 So you have, let's say IDs from zero
00:13:34.885 --> 00:13:36.125 to two ways to power 64.
00:13:36.125 --> 00:13:38.805 That's a lot of T-shirts that you can have in your system.
00:13:38.875 --> 00:13:42.085 When you have three servers, you take this entire line range
00:13:42.305 --> 00:13:44.645 and you split it into three portions, right?
00:13:44.645 --> 00:13:46.485 Three parts, all numbers divisible by three.
00:13:46.505 --> 00:13:47.525 Go to cache ID zero.
00:13:47.625 --> 00:13:49.885 All numbers with remainder one, go to cache ID one
00:13:49.905 --> 00:13:52.165 and all numbers with remainder two go to cache ID two.
00:13:52.165 --> 00:13:53.685 When you model over with three, if we add
00:13:53.725 --> 00:13:54.845 a server, look what happens.
00:13:55.145 --> 00:13:57.965 All numbers divisible by four, go to cache ID zero.
00:13:58.105 --> 00:14:00.645 All numbers having remainder one with four, go
00:14:00.645 --> 00:14:03.565 to cache ID one, remainder two goes to cache ID two
00:14:03.565 --> 00:14:05.165 and remainder three goes to cache ID three.
00:14:05.355 --> 00:14:06.845 What are the intersections here?
00:14:06.945 --> 00:14:08.445 How many intersections can you expect?
00:14:08.595 --> 00:14:11.485 Look at the overlaps of this number line.
00:14:11.545 --> 00:14:13.885 Now, the keys that don't need migration need
00:14:13.885 --> 00:14:16.165 to have the same remainder with three and four.
00:14:16.165 --> 00:14:18.605 Simply put, if the hash has a remainder zero with three,
00:14:18.755 --> 00:14:21.405 then the hash needs to have a remainder of zero with four.
00:14:21.475 --> 00:14:23.765 Also, if the hash has a remainder of one with three,
00:14:23.795 --> 00:14:25.485 then the hash needs to have a remainder
00:14:25.485 --> 00:14:26.845 of one with four also.
00:14:26.945 --> 00:14:28.365 That's when there is an overlap,
00:14:28.385 --> 00:14:30.285 and those keys don't need to be migrated
00:14:30.285 --> 00:14:31.765 because the server ID is still the same.
00:14:31.825 --> 00:14:33.125 But if the server ID is different,
00:14:33.195 --> 00:14:34.565 then you need to migrate those keys.
00:14:34.665 --> 00:14:35.805 How many keys are those? Well,
00:14:35.865 --> 00:14:38.845 the chance offer key being zero with three.
00:14:38.985 --> 00:14:40.125 The chance of a number being visible
00:14:40.185 --> 00:14:41.325 by three is one by three.
00:14:41.455 --> 00:14:43.845 Since hashes are uniformly random, the chance
00:14:43.845 --> 00:14:46.565 of a request ID calling on server zero is one by three.
00:14:46.635 --> 00:14:49.125 Well, the chance of a key having remained a zero
00:14:49.125 --> 00:14:50.605 with four is one by four.
00:14:50.635 --> 00:14:53.005 Overall probability of this is one by three.
00:14:53.005 --> 00:14:54.885 First time your zero into one by four.
00:14:54.885 --> 00:14:57.125 Second time also your zero is one by 12.
00:14:57.465 --> 00:15:00.245 One 12 of the keys will remain where they are.
00:15:00.425 --> 00:15:02.445 The remaining keys will be migrated.
00:15:02.465 --> 00:15:03.645 That's a lot of migrations,
00:15:03.825 --> 00:15:05.445 and if you increase the number of servers here,
00:15:05.445 --> 00:15:08.365 like from 39, you go to 40, you see
00:15:08.365 --> 00:15:10.365 that this becomes a ridiculously low probability.
00:15:10.385 --> 00:15:12.845 You'll basically be migrating all of the data
00:15:12.945 --> 00:15:14.365 or you'll be basically loading all
00:15:14.365 --> 00:15:15.885 of the data fresh into cache.
00:15:15.945 --> 00:15:18.085 So that's, that's a lot of migration that you have to do.
00:15:18.085 --> 00:15:20.005 Consistent hashing helps us here. How.
00:15:20.025 --> 00:15:22.405 Now take the original number line that you had from zero
00:15:22.425 --> 00:15:24.005 to two, waste power 64.
00:15:24.015 --> 00:15:26.925 Those are the T-shirt IDs you had and make it a ring.
00:15:26.955 --> 00:15:28.205 Just wrap it around itself.
00:15:28.425 --> 00:15:29.685 It goes from zero to tourist
00:15:29.685 --> 00:15:31.245 to power 64, and then back to zero.
00:15:31.355 --> 00:15:34.645 What I want you to do is take all the servers that you have
00:15:34.745 --> 00:15:38.125 and hash their IDs and plot them on this ring.
00:15:38.145 --> 00:15:39.765 So you take the first server, server ID
00:15:39.875 --> 00:15:41.205 zero, take the hash of this.
00:15:41.205 --> 00:15:43.885 Maybe you get 5,623 plotted on this point.
00:15:43.935 --> 00:15:45.485 Comes somewhere on top.
00:15:45.505 --> 00:15:46.885 You take the rest of the servers
00:15:46.885 --> 00:15:48.645 and you plot them along this line.
00:15:48.775 --> 00:15:51.565 Since the hashes are uniformly random, you will see
00:15:51.565 --> 00:15:54.205 that they're being plotted approximately randomly,
00:15:54.205 --> 00:15:55.525 equally distant in this line.
00:15:55.825 --> 00:15:57.845 Now, whenever a request comes into your system,
00:15:57.995 --> 00:16:01.005 hash the request, find where it lies on this screen,
00:16:01.145 --> 00:16:03.845 and take the next clockwise server randomly.
00:16:03.845 --> 00:16:05.925 You can take anti-clockwise. Also, it's the same thing.
00:16:05.965 --> 00:16:07.485 I mean it's symmetrical, but we are just taking
00:16:07.645 --> 00:16:08.965 clockwise for convenience.
00:16:09.025 --> 00:16:11.605 And what happens is every request has a hash.
00:16:11.835 --> 00:16:13.885 That hash is plotted on this ring,
00:16:13.985 --> 00:16:15.845 and then the next clockwise server is picked up.
00:16:15.845 --> 00:16:18.805 Simply put in math terms, it's going to take the server,
00:16:18.895 --> 00:16:21.205 which is the minimum greater than itself.
00:16:21.305 --> 00:16:22.845 If you have a binary tree,
00:16:22.845 --> 00:16:24.765 finding this value is quite simple.
00:16:24.955 --> 00:16:28.005 Find a value, which is the next greatest as compared
00:16:28.005 --> 00:16:29.445 to the hash of this request id.
00:16:29.505 --> 00:16:31.045 Now, if a new server is added to the system,
00:16:31.145 --> 00:16:33.045 all you do is take that server hash,
00:16:33.145 --> 00:16:34.845 its Id plot it on the ring, and
00:16:35.045 --> 00:16:36.805 whenever requests come in, if it happens
00:16:36.805 --> 00:16:37.725 to be the next clockwise
00:16:37.725 --> 00:16:38.925 server, ask it to serve the request.
00:16:38.985 --> 00:16:41.165 Why is this working? Like how the hell is this working?
00:16:41.275 --> 00:16:42.605 Well, the chance
00:16:42.785 --> 00:16:46.045 of a server being picked in this ring is actually one
00:16:46.065 --> 00:16:47.365 by a number of servers, right?
00:16:47.365 --> 00:16:49.885 Because the ring is circular, uh,
00:16:49.905 --> 00:16:53.285 you have a uniformly random hash of the servers,
00:16:53.305 --> 00:16:55.725 so they're being plotted at roughly equal distant points.
00:16:55.825 --> 00:16:58.645 You can expect the load on every server to be roughly equal.
00:16:58.865 --> 00:17:01.725 The line segment between two servers is going
00:17:01.725 --> 00:17:02.805 to be roughly equidistant.
00:17:02.805 --> 00:17:04.405 As you have more and more servers, adding
00:17:04.665 --> 00:17:06.765 and removing servers becomes easy.
00:17:06.865 --> 00:17:09.405 If you remove a server, all the requests which belonged
00:17:09.505 --> 00:17:11.725 to it will now go to the next clockwise point,
00:17:11.725 --> 00:17:13.725 and so the impact will only be on one server.
00:17:13.825 --> 00:17:15.085 It won't be on the rest of the servers,
00:17:15.105 --> 00:17:17.405 and the size of the impact will just be the line segment.
00:17:17.585 --> 00:17:19.565 The entire system does not need to change.
00:17:19.675 --> 00:17:21.805 This algorithm is called consistent hashing.
00:17:21.805 --> 00:17:22.965 There is an improvement to this
00:17:22.965 --> 00:17:24.365 algorithm, a significant improvement.
00:17:24.365 --> 00:17:26.325 Basically, when you have few servers, let's say three
00:17:26.325 --> 00:17:28.605 or four, the chance of a skew is quite high.
00:17:28.705 --> 00:17:30.565 So if you have, let's say most
00:17:30.945 --> 00:17:33.565 of the requests going in clockwise fashion, two,
00:17:33.565 --> 00:17:35.685 server number one and two or three are really close to it.
00:17:35.715 --> 00:17:39.285 Then what happens is one is overheated, one is overloaded,
00:17:39.345 --> 00:17:40.725 and two and three are just relaxing,
00:17:40.795 --> 00:17:42.205 like they don't need to do that.
00:17:42.345 --> 00:17:43.685 So you can bring in the concept
00:17:43.825 --> 00:17:45.685 of virtual points on this ring.
00:17:45.685 --> 00:17:48.565 Basically, server one now has multiple points on the ring.
00:17:48.825 --> 00:17:51.445 You can imagine it to have multiple virtual IDs.
00:17:51.475 --> 00:17:53.845 Each of these virtual IDs is mapped onto the ring.
00:17:53.985 --> 00:17:55.685 If it's the same with server ID two
00:17:55.685 --> 00:17:57.565 and three, so let's say we plot 20
00:17:57.565 --> 00:17:58.805 points on the ring for each server.
00:17:58.945 --> 00:18:00.805 Now, when a request comes, all we have
00:18:00.805 --> 00:18:02.885 to do is find the next clockwise point.
00:18:02.985 --> 00:18:04.845 We find who this point belongs to,
00:18:04.845 --> 00:18:06.405 which server at this point belongs to,
00:18:06.585 --> 00:18:07.845 and then assign the server to them.
00:18:07.845 --> 00:18:11.125 Benefit of this is that the chance of a skew is less, and
00:18:11.325 --> 00:18:13.885 whenever you remove or add servers, the amount
00:18:13.885 --> 00:18:15.925 of load on a single server is reduced
00:18:15.925 --> 00:18:19.325 because a server now takes smaller segments of request load
00:18:19.425 --> 00:18:21.605 and distributes it across many servers.
00:18:21.625 --> 00:18:23.845 If you had just one server, you were hitting one server.
00:18:23.945 --> 00:18:26.365 If you have 20 points, then the chance
00:18:26.365 --> 00:18:28.565 of you hitting both other servers is much higher,
00:18:28.585 --> 00:18:31.125 and you can see this in the graphical space clearly,
00:18:31.225 --> 00:18:32.765 and the chance of you dumping all
00:18:32.765 --> 00:18:34.605 of your load onto a single server is less.
00:18:34.905 --> 00:18:36.805 So if you have 20 servers, let's say,
00:18:36.825 --> 00:18:38.205 and one of them goes down,
00:18:38.385 --> 00:18:39.925 it would send all of its data to a single server.
00:18:39.925 --> 00:18:41.845 If you have virtual servers, it's probably going
00:18:41.845 --> 00:18:44.485 to be connected to many other servers in a clockwise
00:18:44.485 --> 00:18:47.525 fashion, so the data is roughly distributed amongst them.
00:18:47.585 --> 00:18:49.045 You can see this clearly in the graph
00:18:49.105 --> 00:18:50.245 and in this way, we are able
00:18:50.245 --> 00:18:51.725 to reduce the cache warmup time.
00:18:51.745 --> 00:18:53.325 We are able to make a cache ready
00:18:53.325 --> 00:18:54.725 quickly and serve requests.
00:18:54.875 --> 00:18:56.805 This concept is used in multiple systems.
00:18:57.105 --> 00:18:59.405 For example, Amazon Dynamo db, which is a database,
00:18:59.405 --> 00:19:01.005 it's not a cache, it's a database.
00:19:01.195 --> 00:19:04.765 Also uses this for reducing the amount of data migration
00:19:04.765 --> 00:19:06.805 between its database servers in case one
00:19:06.805 --> 00:19:08.325 of the database servers crashes
00:19:08.325 --> 00:19:10.365 or has to be brought up for horizontal scaling.
00:19:10.465 --> 00:19:11.565 The same algorithm is used,
00:19:11.665 --> 00:19:14.285 and Redis also has consistent hashing as one
00:19:14.285 --> 00:19:15.965 of the load balancing algorithms that it offers.
00:19:16.025 --> 00:19:18.725 Google also uses a variation of consistent hashing.
00:19:18.725 --> 00:19:20.205 It's called backend subsetting.
00:19:20.265 --> 00:19:21.645 You can see the link in the description.
00:19:21.675 --> 00:19:23.005 It's a blog at interview ready.
00:19:23.035 --> 00:19:25.165 It's a pretty interesting thought by Google
00:19:25.305 --> 00:19:27.685 to improve on the consistent hashing algorithm even further.
00:19:27.785 --> 00:19:30.165 At this point, you have a decent idea of what caches are.
00:19:30.165 --> 00:19:31.165 You know where to place them,
00:19:31.345 --> 00:19:33.285 and you know what kind of algorithms can be used
00:19:33.285 --> 00:19:35.645 to distribute load, but we still haven't talked about
00:19:35.905 --> 00:19:38.565 how do we store and retrieve data from this cache?
00:19:38.595 --> 00:19:42.205 What could be the ideal access patterns to make sure
00:19:42.205 --> 00:19:44.005 that our caches are highly efficient?
00:19:44.005 --> 00:19:45.245 Okay. That's what we'll be discussing.
00:19:45.245 --> 00:19:46.725 We'll be talking about policies now,
00:19:46.725 --> 00:19:48.725 and your founder friend is probably at the level
00:19:48.745 --> 00:19:51.725 of patience, the end of their patience, so it's best
00:19:51.725 --> 00:19:53.005 to explain it in a simple manner.
00:19:53.005 --> 00:19:53.885 That's what we'll be doing. 