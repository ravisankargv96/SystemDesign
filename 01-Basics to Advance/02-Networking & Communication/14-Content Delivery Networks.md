### **1. Introduction to CDNs**

**Definition**
* A **Content Delivery Network (CDN)** is a globally distributed network of servers that work together to efficiently deliver content to users.
* Instead of a single server handling all traffic, the workload is spread across thousands of servers worldwide.

![[01-Introduction to CDNs.png]]

**Why CDNs Exist**
* **Reduces Latency:** By serving content from a location physically closer to the user, data travels a shorter distance, speeding up load times.
* **Enhances Content Availability:** If one server goes down, traffic is automatically rerouted to the next available server, ensuring the site remains online.
* **Improves Load Handling:** Prevents any single server (especially the origin) from being overwhelmed by traffic spikes.
* **Security:** Acts as a buffer against attacks like DDoS, protecting the core infrastructure.

---

### **2. Why are CDNs Needed?**

![[02-Why are CDNs needed.png]]

**The Problem Without CDNs**
* **High Latency:** If a user in India accesses a website hosted in New York, the data must travel halfway across the globe, causing noticeable delays.
* **Overloaded Origin Servers:** A single server handling all global traffic can easily become a bottleneck, leading to crashes during high-traffic events.
* **Bandwidth Constraints:** Streaming high-definition video or large files from one central location consumes massive bandwidth and increases costs significantly.

---

### **3. CDN Architecture Overview**

![[03-CDN Architecture Overview.png]]

A CDN is built on three main components:
1.  **Origin Server:** The "source of truth." This is where the original, definitive version of the content (website files, videos, images) lives.
2.  **Edge Servers (Points of Presence - PoPs):** These are the distributed servers placed strategically around the globe. They store cached copies of the content.
3.  **Request Routing System:** The "brain" of the operation. It determines the best Edge Server to handle a specific user's request based on location and load.

---

### **4. How a CDN Works and Handles a User Request**

![[04-How a CDN Works and Handles a User Request.png]]

The process of fetching content with a CDN follows these steps:
1.  **User Request:** A user attempts to load a video or webpage.
2.  **Routing:** The CDN's routing system analyzes the user's location and network conditions to find the nearest Edge Server.
3.  **Cache Check:**
    * **Cache Hit:** If the Edge Server already has the content, it delivers it instantly to the user.
    * **Cache Miss:** If the content is missing, the Edge Server fetches it from the Origin Server, delivers it to the user, and **saves a copy** for future requests.

---

### **5. Key CDN Features & Benefits**

* **Caching & Replication:** Stores frequently accessed files at the edge. This is the primary mechanism for reducing latency.
* **Load Balancing:** Distributes traffic across multiple PoPs to ensure reliability. It prevents any single point in the network from becoming a bottleneck.
* **Compression & Optimization:** Automatically reduces file sizes using techniques like Gzip/Brotli for text and specialized formats (WebP) for images, lowering bandwidth costs.
* **Security:** Provides a shield against DDoS attacks by absorbing malicious traffic at the edge, keeping the origin server safe. It also handles SSL/TLS encryption.

---

### **6. Content Caching and Replication**

![[05-Content Caching and Replication.png]]

**Mechanism**
* **Storage:** Frequently accessed static assets (images, CSS, JS) are replicated across thousands of Edge Servers.
* **Freshness (TTL):** "Time-To-Live" settings determine how long a file stays in the cache before it is considered "stale".
    * *Static content* (like logos) has a long TTL.
    * *Dynamic content* (like news feeds) has a short TTL.
* **Invalidation:** If content changes before the TTL expires, strategies like **Manual Purge** (force deleting the cache) or **Stale-While-Revalidate** (serving old content while fetching new content in the background) are used.

---

### **7. Load Balancing, Failover, and Routing**

![[06-Load Balancing - Failover Handling and Request Routing.png]]

**Request Routing Strategies**
* **Geo-based:** Directs the user to the physically nearest PoP (e.g., a Paris user connects to the Paris node).
* **Latency-based:** Ignores geography and simply chooses the server that responds quickest at that moment (useful if the "nearest" server is congested).
* **Load-aware:** Distributes traffic based on the current capacity of the servers, avoiding those that are near their limit.

**Failover Handling**
* If a specific Edge Server or entire Data Center (PoP) goes offline, the CDN automatically reroutes users to the next best available location, ensuring high availability.

---

### **8. Compression & Minification**

CDNs actively optimize the "payload" being delivered:
* **Compression:** Uses algorithms like **Gzip** and **Brotli** to shrink text-based files (HTML, CSS, JS).
* **Image Optimization:** Converts images to modern, efficient formats like **WebP** or **AVIF** on the fly.
* **Minification:** Removes unnecessary characters (whitespace, comments) from code files to reduce file size without changing functionality.

---

### **9. Security Features**

* **DDoS Mitigation:** The massive capacity of a CDN network can absorb "volumetric" attacks, preventing them from overwhelming the origin server.
* **Traffic Filtering:** Can block malicious bots and scrapers using a Web Application Firewall (WAF).
* **SSL/TLS Offloading:** The CDN handles the handshake and encryption process for HTTPS connections, reducing the computational load on the origin server.

---

### **10. Use Cases of CDNs**

* **Static Content Delivery:** The most common use case—delivering images, videos, and stylesheets for websites.
* **Dynamic Content:** Accelerating non-cacheable content (like personalized dashboards) by optimizing the *route* back to the origin server.
* **API Acceleration:** Caching common API responses at the edge to reduce the load on backend databases.
* **Edge Computing:** Running lightweight code (like video transcoding or image resizing) directly on the Edge Servers, closer to the user.

---

### **11. Interview Questions on CDNs**

**Basics & Architecture**
* What is a CDN, and why is it critical for modern system design?
* Explain the roles of Origin Servers vs. Edge Servers.
* What is a Point of Presence (PoP)?

**Caching & Strategy**
* Difference between a Cache Hit and a Cache Miss?
* What is TTL, and how does it impact content freshness?
* How do you handle "Cache Invalidation" when data changes?

**Performance & Security**
* How does a CDN protect against DDoS attacks?
* Explain Geo-based vs. Latency-based routing.
* What is "Edge Computing," and how does it differ from traditional cloud computing?

---

### **12. Wrap-Up & Key Takeaways**

* **Performance:** CDNs are essential for reducing latency and speeding up load times globally.
* **Reliability:** They provide robust failover and load balancing to keep sites online.
* **Security:** They act as a first line of defense against attacks like DDoS.
* **Cost:** By offloading traffic and optimizing file sizes, they significantly reduce bandwidth costs for the origin infrastructure.

**What’s Next:**
We have completed the **Networking & Communication** module. The next section will focus on **Protocols** (TCP, UDP, HTTP, etc.) to understand *how* data actually moves across these networks.