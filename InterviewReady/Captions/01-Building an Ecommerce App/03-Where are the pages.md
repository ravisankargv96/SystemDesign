## Chapters
* 00:00 - Where are webpages stored?
* 01:03 - CDN vs Backend Server
* 02:46 - Why STATIC content?
* 03:57 - Datastore: File System
* 05:12 - How do users find us?
* 05:56 - DNS Route Resolution
* 08:30 - What Database is right?

## Transcript
00:00:00.065 --> 00:00:02.285 Now that we have our server set up, we want our users
00:00:02.305 --> 00:00:05.125 to be able to access our website on their browser.
00:00:05.345 --> 00:00:07.925 So when they type, let's say fancy t-shirts io,
00:00:07.925 --> 00:00:09.685 they should be able to see the webpage
00:00:09.705 --> 00:00:11.005 for fancy t-shirts dot io,
00:00:11.005 --> 00:00:12.885 and they should be able to perform certain operations.
00:00:13.025 --> 00:00:14.885 For now, we are restricting to registrations.
00:00:14.885 --> 00:00:16.045 They should be able to log in
00:00:16.045 --> 00:00:18.125 and they should be able to register, create a new account.
00:00:18.125 --> 00:00:20.325 These are the things which will be affecting the server
00:00:20.435 --> 00:00:22.525 that will have requests and responses from the server.
00:00:22.665 --> 00:00:24.845 In our case, that's a serverless architecture.
00:00:24.845 --> 00:00:26.525 But the second part is quite important.
00:00:26.585 --> 00:00:28.805 We talked about a webpage. What really is a webpage?
00:00:28.835 --> 00:00:30.525 It's a static file, which tells you
00:00:30.545 --> 00:00:31.965 how it's going to look like.
00:00:31.965 --> 00:00:33.725 Maybe there is some HTML and CSS there
00:00:33.785 --> 00:00:35.245 and what it's going to behave like.
00:00:35.345 --> 00:00:36.965 You will have some JavaScript
00:00:37.065 --> 00:00:39.645 or some way in which the webpage can react
00:00:39.665 --> 00:00:40.805 to actions of a user.
00:00:40.955 --> 00:00:42.605 This page will need to be stored somewhere,
00:00:42.665 --> 00:00:44.365 and it can be stored in two places.
00:00:44.785 --> 00:00:46.565 One would be in AWS servers.
00:00:46.705 --> 00:00:48.525 If a user is trying to access a page,
00:00:48.555 --> 00:00:49.805 they just make a API call
00:00:49.805 --> 00:00:51.285 and your server says, here's the page.
00:00:51.285 --> 00:00:54.765 Okay, that's possible. The other way is to use a content
00:00:55.285 --> 00:00:57.405 delivery network and let's look at the pros and cons.
00:00:57.585 --> 00:00:59.365 In this case, I think by the end of it,
00:00:59.365 --> 00:01:00.445 the choice will be quite obvious,
00:01:00.465 --> 00:01:01.805 but let's look at the pros and cons.
00:01:01.805 --> 00:01:04.205 Content driven network versus actually serving the pages
00:01:04.205 --> 00:01:05.765 through a server to a machine,
00:01:05.785 --> 00:01:07.205 or maybe even a serverless function
00:01:07.205 --> 00:01:08.405 if you have a content driven network.
00:01:08.505 --> 00:01:09.805 The benefit of this is
00:01:09.805 --> 00:01:11.805 that these servers are spread across the globe
00:01:11.805 --> 00:01:15.245 that's already taken care of by companies like Akamai.
00:01:15.405 --> 00:01:17.525 AWS also gives its own solution and so on.
00:01:17.525 --> 00:01:20.125 So the benefit of having servers distributed across the
00:01:20.125 --> 00:01:22.285 globe is the pages can be fetched very quickly.
00:01:22.425 --> 00:01:23.725 So if you're staying in Mumbai
00:01:23.725 --> 00:01:26.205 and you have a server here in India, you can connect to
00:01:26.205 --> 00:01:28.125 that, but your customers in the US may connect
00:01:28.125 --> 00:01:29.125 to a server in New York
00:01:29.145 --> 00:01:31.085 and even there you may have a east and west region.
00:01:31.265 --> 00:01:32.885 So people in San Francisco may connect
00:01:32.885 --> 00:01:35.605 to a West Region server while the New Yorkers
00:01:35.605 --> 00:01:36.685 connect to a East region server.
00:01:36.785 --> 00:01:39.525 In India, you may have a single server in the uk,
00:01:39.525 --> 00:01:41.845 you may have a single server for the entire Europe region.
00:01:41.845 --> 00:01:43.605 You may have a single server depending on
00:01:43.605 --> 00:01:45.005 your user locality.
00:01:45.105 --> 00:01:46.525 If you see a lot of users in India,
00:01:46.525 --> 00:01:47.925 you might want to add more servers here.
00:01:47.925 --> 00:01:50.165 If you see fewer, then you have fewer servers here.
00:01:50.265 --> 00:01:53.045 All of this is largely managed by content delivery networks.
00:01:53.185 --> 00:01:55.725 If you try to implement this yourself, it's going
00:01:55.725 --> 00:01:57.725 to be quite a bit in terms of operation costs,
00:01:57.865 --> 00:01:59.645 set up testing, that's one drawback,
00:01:59.745 --> 00:02:01.205 and it may be a bit expensive
00:02:01.205 --> 00:02:03.285 because content delivery networks provide services
00:02:03.345 --> 00:02:07.045 to many customers and they're able to amortize the costs.
00:02:07.465 --> 00:02:09.445 You doing it individually is going to be difficult.
00:02:09.605 --> 00:02:10.885 A content delivery network doing it
00:02:10.885 --> 00:02:12.925 by themselves is usually cheaper.
00:02:13.065 --> 00:02:14.285 You get the benefits of scale,
00:02:14.345 --> 00:02:15.485 uh, when you tie up with them.
00:02:15.505 --> 00:02:16.925 So in this case, we will go
00:02:16.925 --> 00:02:18.045 ahead with the Content delivery network.
00:02:18.225 --> 00:02:20.645 We can use Akamai or Amazon CloudFront.
00:02:20.655 --> 00:02:22.605 These have servers distributed across the globe,
00:02:22.625 --> 00:02:24.405 and we are going to be storing static pages
00:02:24.665 --> 00:02:25.765 in these servers.
00:02:25.795 --> 00:02:29.245 That means images, files, videos are all going
00:02:29.245 --> 00:02:30.925 to be served from content delivery networks.
00:02:30.945 --> 00:02:33.885 The rest of this stuff, which is data, which can be changed,
00:02:33.915 --> 00:02:37.085 manipulated, will be kept on the server in a database.
00:02:37.145 --> 00:02:38.245 We are bifurcating the data.
00:02:38.345 --> 00:02:40.165 Why not keep everything in the Content delivery network?
00:02:40.195 --> 00:02:41.565 Like we said, content delivery networks
00:02:41.565 --> 00:02:42.685 are distributed across the globe.
00:02:42.685 --> 00:02:44.525 That's a benefit when you're looking at low latency.
00:02:44.525 --> 00:02:46.285 But if you're looking for updates,
00:02:46.595 --> 00:02:48.725 imagine you have a T-shirt, which is very popular,
00:02:48.865 --> 00:02:50.805 and you just have 50 of those pieces remaining.
00:02:50.805 --> 00:02:54.165 There are 40 orders placed in the US and 11 placed in India.
00:02:54.345 --> 00:02:57.325 The two databases, the two servers will show data
00:02:57.465 --> 00:02:58.485 of 50 remaining.
00:02:58.485 --> 00:03:00.360 50 remaining 40 will get booked here,
00:03:00.360 --> 00:03:02.820 11 will get booked here by the time they reconcile,
00:03:02.865 --> 00:03:04.085 by the time they talk to each other.
00:03:04.275 --> 00:03:07.165 It's possible that in total 40 plus 11 becomes 51.
00:03:07.305 --> 00:03:09.685 We have over placed the orders of T-shirts.
00:03:09.785 --> 00:03:12.805 So keeping data consistent, keeping the same view
00:03:12.805 --> 00:03:14.245 of data in a content delivery network
00:03:14.265 --> 00:03:15.485 is extremely difficult.
00:03:15.545 --> 00:03:18.485 Any kind of dynamic data is stuff that you want
00:03:18.485 --> 00:03:20.885 to keep in the server, so it would be much better if the
00:03:20.885 --> 00:03:22.965 webpage would go and fetch this information.
00:03:22.985 --> 00:03:24.045 How many T-shirts remaining
00:03:24.045 --> 00:03:25.165 for this product from the server?
00:03:25.305 --> 00:03:27.365 Get that information and in real time tell you
00:03:27.365 --> 00:03:28.565 how many T-shirts are remaining.
00:03:28.565 --> 00:03:30.485 If you try to push this to the content delivery networks,
00:03:30.555 --> 00:03:31.605 they update slowly
00:03:31.705 --> 00:03:32.805 and they are challenging
00:03:32.805 --> 00:03:35.085 to update in such a big distributed environment.
00:03:35.085 --> 00:03:38.365 So it's better to just keep static data like the banner
00:03:38.425 --> 00:03:41.205 of the page, the images, the product description,
00:03:41.205 --> 00:03:42.205 the information, all
00:03:42.205 --> 00:03:44.045 that stuff can be kept in the ary network.
00:03:44.045 --> 00:03:46.085 Everything else, you want to keep close to the server,
00:03:46.485 --> 00:03:47.805 wherever you need a single source of truth.
00:03:47.805 --> 00:03:49.085 And so this brings an interesting point.
00:03:49.145 --> 00:03:51.325 How do we add files to the content degree network?
00:03:51.435 --> 00:03:53.525 When you are adding files to tens
00:03:53.525 --> 00:03:55.125 of servers distributed across the globe,
00:03:55.185 --> 00:03:56.525 is there an easy way to do it?
00:03:56.625 --> 00:03:59.605 Yes, there is. So if you have a file system which is being
00:03:59.675 --> 00:04:02.165 read by the network consistently, then what's going
00:04:02.165 --> 00:04:04.605 to happen is whenever you add any file to this system,
00:04:04.755 --> 00:04:06.645 it's automatically going to be picked up by the content
00:04:06.665 --> 00:04:08.125 of your network and distributed across the globe.
00:04:08.125 --> 00:04:09.845 I'll take an example. Let's say you have your computer
00:04:09.945 --> 00:04:12.085 and you have a particular folder called public.
00:04:12.235 --> 00:04:14.405 This folder is being checked every 10
00:04:14.405 --> 00:04:15.845 seconds by some other computer.
00:04:16.165 --> 00:04:17.485 Whenever you add a new file to it,
00:04:17.485 --> 00:04:19.885 the other computer will see, oh, a new file has been added.
00:04:19.985 --> 00:04:21.765 You know, the idea of this file is different
00:04:21.765 --> 00:04:22.925 from all the other files that I have.
00:04:23.045 --> 00:04:25.285 I need to add this to my network. When to pick that file.
00:04:25.285 --> 00:04:26.525 It's going to take all the data, it's going
00:04:26.525 --> 00:04:27.485 to take the metadata, it's going
00:04:27.485 --> 00:04:28.445 to distribute it across the globe.
00:04:28.445 --> 00:04:29.645 The content delivery network is there.
00:04:29.755 --> 00:04:31.445 This file system needs to exist.
00:04:31.745 --> 00:04:33.205 You can host it in your computer,
00:04:33.345 --> 00:04:35.605 but like we said, it's better to have things on the cloud
00:04:35.625 --> 00:04:37.885 for high reliability and possibly lower cost.
00:04:37.945 --> 00:04:40.845 So an existing solution for this is Amazon S3.
00:04:40.845 --> 00:04:41.885 This is extremely popular.
00:04:42.075 --> 00:04:44.285 It's a distributed file system that you can use.
00:04:44.285 --> 00:04:45.325 If you're going to host this locally,
00:04:45.465 --> 00:04:47.005 you could have used Hadoop file system.
00:04:47.105 --> 00:04:48.685 You could have used other file systems.
00:04:48.715 --> 00:04:51.885 Also you could use CEF is also an open source file system,
00:04:51.945 --> 00:04:53.605 but we are going to use Amazon SC
00:04:53.605 --> 00:04:56.125 because it's completely managed as very high rates
00:04:56.125 --> 00:04:57.725 of durability and consistency.
00:04:57.725 --> 00:04:59.965 That's a solution that you'll propose as a tech expert
00:04:59.985 --> 00:05:02.325 and also the CDN that you're going to be using.
00:05:02.675 --> 00:05:05.405 It's better to have things all under one umbrella.
00:05:05.505 --> 00:05:08.045 So I'll be suggesting AWS CloudFront,
00:05:08.265 --> 00:05:10.405 but you can use Akamai or CloudFlare.
00:05:10.405 --> 00:05:12.645 These are very popular solutions to host your webpages.
00:05:12.735 --> 00:05:14.325 Until now. We have a server setup
00:05:14.425 --> 00:05:16.725 and we have our webpages distributed across the globe.
00:05:16.725 --> 00:05:19.445 There is one thing though. Your customer has this domain
00:05:19.445 --> 00:05:21.005 called fancy t-shirts dot io,
00:05:21.005 --> 00:05:23.525 but how do you make people point to your new webpages?
00:05:23.525 --> 00:05:25.245 Now, Shopify somehow magically was able
00:05:25.245 --> 00:05:28.285 to get people from fancy t-shirts dot io into their server,
00:05:28.285 --> 00:05:29.525 right into their webpages.
00:05:29.545 --> 00:05:31.285 But if you have to tell Shopify, Hey,
00:05:31.435 --> 00:05:32.965 stop sending your webpages.
00:05:32.965 --> 00:05:34.845 Your webpages are really bad, I want
00:05:34.845 --> 00:05:36.405 to show my nice looking webpages.
00:05:36.405 --> 00:05:38.525 Now how do you do that? Well, you need to be able
00:05:38.525 --> 00:05:41.485 to tell the customers on their browser to not point
00:05:41.485 --> 00:05:43.965 to Shopify, but to point to your new webpages.
00:05:43.965 --> 00:05:45.725 Now, how do you do that? Let's try to understand
00:05:45.825 --> 00:05:47.805 how the internet works at a high level.
00:05:47.875 --> 00:05:49.965 When a person types an address on the browser,
00:05:50.015 --> 00:05:51.725 fancy t-shirts io, what's going
00:05:51.725 --> 00:05:52.885 to happen is the browser tries
00:05:52.885 --> 00:05:54.925 to resolve this address using something
00:05:54.925 --> 00:05:56.285 called a domain name server.
00:05:56.425 --> 00:05:57.885 The way this works is you pay someone
00:05:57.985 --> 00:05:59.405 for your internet connection called the
00:05:59.445 --> 00:06:00.685 ISP Internet Service provider.
00:06:00.795 --> 00:06:02.245 Your request goes to your router.
00:06:02.265 --> 00:06:05.045 The router has a hardcoded address which goes
00:06:05.045 --> 00:06:06.685 and calls the internet service provider says
00:06:06.685 --> 00:06:07.805 that this person is trying
00:06:07.805 --> 00:06:09.605 to resolve the domain of this address.
00:06:09.675 --> 00:06:11.165 That request goes to a domain name server.
00:06:11.165 --> 00:06:12.525 They look at fancy t-shirts io
00:06:12.525 --> 00:06:15.165 and the domain name server is basically a massive
00:06:15.325 --> 00:06:16.725 distributed network similar
00:06:16.785 --> 00:06:19.005 to the content delivery network that we are talking about.
00:06:19.075 --> 00:06:21.605 It's a big distributed network of address maintainers
00:06:21.745 --> 00:06:23.005 for every website.
00:06:23.105 --> 00:06:25.325 It has a corresponding IP address.
00:06:25.335 --> 00:06:28.805 Fancy T-shirts do IO points to 1 92 0.15.
00:06:29.205 --> 00:06:32.365 facebook.com points to 1 92, do five, do 6.8.
00:06:32.365 --> 00:06:33.405 It's got a lot of domains
00:06:33.405 --> 00:06:34.925 and the corresponding IP addresses.
00:06:34.925 --> 00:06:37.005 So this is a dictionary. It's a map e value pad.
00:06:37.005 --> 00:06:38.205 The benefit of this is
00:06:38.205 --> 00:06:40.645 that different domain name servers for different companies.
00:06:40.725 --> 00:06:43.245 AWS has its own domain name server called Route 53.
00:06:43.395 --> 00:06:45.725 GoDaddy is a massive domain name server company.
00:06:45.795 --> 00:06:47.125 They can interact with each other
00:06:47.305 --> 00:06:49.285 and make sure that everybody can find
00:06:49.285 --> 00:06:50.445 the website that they're looking for.
00:06:50.445 --> 00:06:52.525 So if AWS doesn't know about it, it can just go
00:06:52.525 --> 00:06:53.925 and say, maybe GoDaddy knows about it.
00:06:53.925 --> 00:06:56.005 Let me go and check with them. When the domain name is
00:06:56.165 --> 00:06:57.205 resolved to an IP address,
00:06:57.305 --> 00:06:58.805 you get this back on your browser.
00:06:58.905 --> 00:07:00.965 The browser usually ces, this address
00:07:00.965 --> 00:07:02.765 because you are likely to use it further.
00:07:02.865 --> 00:07:04.205 Now you take this IP address
00:07:04.225 --> 00:07:06.285 and you go to your ISP again saying that I need
00:07:06.285 --> 00:07:08.205 to route a request to this address.
00:07:08.385 --> 00:07:10.285 So if you're trying to fetch the webpage of Facebook,
00:07:10.345 --> 00:07:11.725 you hit that IP address.
00:07:11.755 --> 00:07:13.205 That will be a CDN for Facebook,
00:07:13.205 --> 00:07:15.925 and it's going to return you a webpage, an HT ML page,
00:07:15.925 --> 00:07:17.725 which will be rendered on your browser.
00:07:17.725 --> 00:07:19.245 Fancy tshirts IO is going
00:07:19.245 --> 00:07:21.205 to have a similar webpage on the continuity network.
00:07:21.425 --> 00:07:23.965 We need the domain name server to have this mapping so
00:07:23.965 --> 00:07:25.285 that the internet can find us.
00:07:25.285 --> 00:07:26.805 Nobody can remember the IP address.
00:07:26.805 --> 00:07:28.405 They, they have to remember the domain name
00:07:28.405 --> 00:07:30.125 and the domain name mapping is managed
00:07:30.145 --> 00:07:31.365 by these domain name servers.
00:07:31.385 --> 00:07:34.005 The easiest way to do this is if you have a good ID website,
00:07:34.005 --> 00:07:36.245 then you can point it directly to the webpage.
00:07:36.345 --> 00:07:38.485 If you are using AWS Technologies anywhere,
00:07:38.485 --> 00:07:39.925 then you can tell God ID that.
00:07:40.245 --> 00:07:42.485 Whenever you get this domain name resolution request,
00:07:42.515 --> 00:07:44.605 just forward it to Amazon Route 53.
00:07:44.605 --> 00:07:47.205 That is Amazon's domain name server solution.
00:07:47.205 --> 00:07:48.485 That's going to resolve the address
00:07:48.665 --> 00:07:49.805 and give back a response.
00:07:50.105 --> 00:07:51.525 Now the user is going to go
00:07:51.525 --> 00:07:53.445 and fetch that webpage on that IP address,
00:07:53.445 --> 00:07:54.725 which is a CloudFront server,
00:07:54.825 --> 00:07:56.165 and that will render on the browser.
00:07:56.305 --> 00:07:59.045 So they see a nice beautiful t-shirts website
00:07:59.065 --> 00:08:00.685 and they can interact with this.
00:08:00.905 --> 00:08:04.325 How? Because whenever you press a button for register
00:08:04.345 --> 00:08:07.445 or anything in this website, the webpage is going
00:08:07.445 --> 00:08:10.485 to make a request to your server, that IP address, right,
00:08:10.485 --> 00:08:12.125 that will also be resolved in a similar way.
00:08:12.145 --> 00:08:15.525 The domain name server needs to have a mapping for server
00:08:15.585 --> 00:08:17.565 to IP address that's being called on the webpage.
00:08:17.565 --> 00:08:20.325 Once that's done, you will see responses being rendered On
00:08:20.325 --> 00:08:21.965 the webpage, you'll see data being manipulated.
00:08:21.985 --> 00:08:25.325 So at this point, you have a simple functioning webpage
00:08:25.425 --> 00:08:28.525 and server customers are able to come to your website.
00:08:28.525 --> 00:08:31.765 They're able to do actions, they're able to register login.
00:08:32.185 --> 00:08:34.845 One final thing though that we should just touch upon, uh,
00:08:34.845 --> 00:08:36.645 and I don't want to go into it too deep
00:08:36.645 --> 00:08:38.885 because we are doing a database deep dive later in one
00:08:38.885 --> 00:08:40.725 chapter, is what kind of database should be used?
00:08:40.795 --> 00:08:42.645 This question stumps people
00:08:43.065 --> 00:08:46.045 and I've seen real startups getting completely confused by
00:08:46.045 --> 00:08:47.085 what database should be used.
00:08:47.085 --> 00:08:48.165 They spent like three days,
00:08:48.165 --> 00:08:50.285 four days just thinking about databases, researching.
00:08:50.285 --> 00:08:52.685 If you ask my personal opinion, just go with a database
00:08:52.685 --> 00:08:53.805 that you are comfortable with.
00:08:53.865 --> 00:08:56.245 Any database like uh, NoSQL database
00:08:56.245 --> 00:08:58.285 or SQ database is fine for a startup.
00:08:58.385 --> 00:08:59.765 You can always change the database.
00:08:59.765 --> 00:09:01.725 Also later, if you're not sure, if you've never worked
00:09:01.725 --> 00:09:03.365 with databases, go with SQ database.
00:09:03.425 --> 00:09:06.165 The reason for this is it's a little more mature
00:09:06.165 --> 00:09:08.285 as a technology and if you are hiring someone
00:09:08.345 --> 00:09:09.485 for a data analyst position
00:09:09.585 --> 00:09:11.845 or if you're trying to run any analytics, it's easier
00:09:11.845 --> 00:09:13.565 to find those queries on the internet.
00:09:13.635 --> 00:09:15.725 Just learn. SQL is much easier than learning
00:09:16.125 --> 00:09:17.365 database specific language.
00:09:17.495 --> 00:09:20.125 Again, we are thinking like we are thinking like people
00:09:20.225 --> 00:09:21.805 who are on the business side of things.
00:09:21.865 --> 00:09:23.765 We are not just thinking about, oh, you know,
00:09:23.765 --> 00:09:25.805 this gives more scalability, this gives more performance.
00:09:25.825 --> 00:09:28.365 No three things. Does it meet all the requirements SQL does?
00:09:28.505 --> 00:09:30.765 Is it simpler? Yes, it is. And is it cheaper?
00:09:31.025 --> 00:09:33.245 That's hard to say. It depends a lot on the way you are
00:09:33.245 --> 00:09:35.925 dealing with things, but our original three parameters are
00:09:35.925 --> 00:09:36.965 still on top for us. 