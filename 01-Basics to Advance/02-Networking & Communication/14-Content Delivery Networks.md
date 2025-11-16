## 🌎 Content Delivery Networks (CDN) in System Design

A **Content Delivery Network (CDN)** is a globally distributed network of servers that work together to efficiently deliver content to users. CDNs are essential for modern web applications to enhance performance, reduce latency, and ensure reliable content delivery.

![[Pasted image 20251115151155.png]]

---
### Why CDNs are Needed

Without a CDN, content requests often travel long geographic distances to a single **origin server**, leading to:
- **High Latency**: Due to the vast geographic distance between the user and the server.
- **Origin Overload**: The single origin server can be overwhelmed by numerous requests, leading to slow performance or crashes.
- **High Bandwidth Costs**: Every request must be handled by the origin server, increasing bandwidth consumption.

---
### CDN Architecture and Functionality

![[Pasted image 20251115151526.png]]

A CDN consists of three main components:
1. **Origin Servers**: Store the **original content** (the source of truth).
2. **Edge Servers (PoPs - Points of Presence)**: Servers strategically placed worldwide that store **cached copies** of content closer to the user.
3. **Request Routing System**: Directs user requests to the **nearest** and **best performing** Edge Server.
#### How a Request is Handled

1. A user requests content (e.g., a web page or an image).
2. The CDN's routing system directs the request to the nearest **Edge Server**.
3. **Cache Hit**: If the content is on the Edge Server, it's delivered instantly, ensuring low latency.
4. **Cache Miss**: If not, the Edge Server forwards the request to the **Origin Server**, fetches the content, and then caches it at the Edge Server before delivering it to the user.

![[Pasted image 20251115151547.png]]

---
### Key CDN Features and Benefits

CDNs provide multiple optimization and security layers beyond simple caching:
#### 💨 Performance Optimization

![[Pasted image 20251115151651.png]]

- **Caching & Replication**: Storing frequently accessed content at the edge minimizes origin server load and latency.    
    - **TTL (Time-To-Live)**: Determines how long a cached object remains valid before it must be refreshed from the origin.
    - **Cache Invalidation**: Techniques like manual purge or **stale-while-revalidate** ensure content freshness without waiting for TTL expiration.
- **Compression & Minification**: Reduces file sizes using techniques like **Gzip** and **Brotli** compression, or image optimization, leading to faster load times and lower bandwidth costs.
#### 🗺️ Intelligent Routing & Load Balancing

CDNs use sophisticated routing strategies to optimize content delivery:
- **Geo-based Routing**: Directs users to the **closest PoP** based on geographic location.
- **Latency-based Routing**: Chooses the PoP with the **fastest real-time response time** based on network conditions.
- **Load-aware Routing**: Distributes requests to the **least busy PoP** to prevent congestion and overload.
- **Failover Handling**: If an Edge Server fails, traffic is seamlessly rerouted to the next closest healthy PoP, ensuring high availability.
![[Pasted image 20251115151735.png]]

#### 🔒 Security

- **DDoS Mitigation**: CDNs protect against Distributed Denial of Service (DDoS) attacks by implementing rate limiting and traffic filtering.    
- **SSL/TLS Offloading**: They handle the heavy task of SSL encryption and decryption, securing data transmission while reducing the load on the origin server.

---
### CDN Use Cases

CDNs are used for various types of content:
- **Static Content**: Common assets like images, videos, CSS, and JavaScript files.    
- **Dynamic Content**: Can be optimized via routing, compression, and short-TTL caching for personalized pages or API responses.
- **API Acceleration**: CDNs reduce API response times by caching common responses and ensuring requests take the fastest path to the origin.
- **Edge Computing**: Modern CDNs enable lightweight processing (e.g., video transcoding) to occur closer to the user, reducing the burden on the origin.

---

**Next Steps**: This concludes the dedicated topics on Networking Fundamentals. The next lecture will summarize these concepts and discuss best practices for system design interviews.

Would you like a summary of all the Networking Fundamentals topics covered in this section?