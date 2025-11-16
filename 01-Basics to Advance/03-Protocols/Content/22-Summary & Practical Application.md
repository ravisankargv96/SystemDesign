So finally, we have reached to the end of this section on protocols.

In this section, we explored the fundamental protocols that forms the backbone of modern system design.

So let's quickly recap what we have covered.

We started with TCP and UDP.

We started with understanding the basics of TCP and UDP, which are the two essential transport layer

protocols.

TCP ensures reliable, ordered and error checked communication, making it ideal for applications like

web browsing and email.

On the other hand, UDP is lightweight and faster but does not guarantee delivery, making it suitable

for real time applications like VoIP and online gaming.

Then we looked at HTTP, the foundation of web communication.

We discussed how HTTP follows a request response cycle, its stateless nature, and how different HTTP

methods like get, post, put, delete, patch are used in API design.

We also looked at HTTP status codes and their role in debugging and response handling.

Then we dived into the rest and rest constraints, understanding how RESTful APIs are designed from

resources, endpoints, and structured data formats like JSON and XML.

We explored how real time APIs such as Twitter and GitHub implement Rest principles effectively.

Then we started moving beyond traditional request response model and started looking at the real time

communication.

We discussed WebSockets, which enables persistent full duplex communication which is ideal for chat

application and stock price update application.

We have also covered long polling, which while not truly real time but is very useful for notification

system and social media feeds where updates are not continuous but still need to be near instant.

Then lastly, we looked at the modern API protocols that go beyond rest.

We explored gRPC, which leverages protobuf and Http2 for fast, efficient communication, making it

ideal for microservices and IoT.

We also discussed GraphQL, which allows clients to fetch only the data that they need.

Solving the problem of overfetching and under fetching in APIs, and thus making it a great choice for

front end optimization and mobile application.

So what's next?

The next section is about architectural patterns.

With our foundations in communication and API protocols in place, we will now shift our focus to architectural

patterns.

So in the next section we will explore how different components in the system interact.

How to design for scalability and performance, and how different architectural styles like monolithic

microservices and event driven architecture impact the system behavior.

So I will see you in the next one.