### **1. Introduction to Load Balancing**

**Concept Overview**
* **Definition:** Load balancing is the process of efficiently distributing network traffic across multiple servers. It acts as a traffic cop, sitting in front of your servers and routing client requests.
* **Goal:** To ensure that no single server bears too much demand. By spreading the work evenly, load balancing improves application responsiveness and availability.

![[01-why load balancing is needed.png]]

**Why Load Balancing is Needed**
* **High Availability:** It ensures the system stays online even if traffic spikes. If one server goes down, the load balancer redirects traffic to remaining healthy servers, minimizing downtime.
* **Traffic Distribution:** It spreads requests evenly so that no single machine is overwhelmed while others sit idle.
* **Prevents Overload:** Without it, a sudden surge (like a Black Friday sale) could crash a single server. Load balancers distribute this surge intelligently.
* **Improves Performance:** By routing requests to the least busy or fastest-responding server, it reduces latency for the end user.
* **Handles Failures Gracefully:** It actively monitors server health. If a server becomes unresponsive, the load balancer stops sending traffic to it.
* **Supports Scalability:** As traffic grows, you can simply add more servers to the pool, and the load balancer will automatically start sending requests to them.

---

### **2. Types of Load Balancers**

Load balancers are categorized in two ways: by the Network Layer they operate on, and by their Deployment Model.

![[02-types of load balancers.png]]

**Based on Network Layer (OSI Model)**
* **Layer 4 (Transport Layer):**
    * **How it works:** Makes routing decisions based on network-level data like IP addresses and TCP/UDP ports.
    * **Pros:** Extremely fast and efficient because it does not inspect the actual content of the request.
    * **Best for:** Scenarios where speed is the highest priority.
    * **Examples:** AWS Network Load Balancer, HAProxy (in TCP mode).
* **Layer 7 (Application Layer):**
    * **How it works:** Inspects the actual content of the request (HTTP headers, cookies, URLs, query strings).
    * **Pros:** Allows for "intelligent routing." For example, routing `/checkout` traffic to a secure transaction server and `/images` traffic to a media server.
    * **Cons:** Requires more processing power than Layer 4.
    * **Examples:** AWS Application Load Balancer, Nginx.

**Based on Deployment Model**
* **Hardware Load Balancers:** Physical devices (appliances) built specifically for high-performance traffic management.
    * *Use Case:* Large enterprise data centers.
    * *Examples:* F5 Big-IP, Citrix NetScaler.
* **Software Load Balancers:** Applications that run on standard servers (virtual machines or containers).
    * *Use Case:* Flexible, cost-effective modern architectures.
    * *Examples:* Nginx, HAProxy.
* **Cloud-based Load Balancers:** Managed services provided by cloud vendors.
    * *Use Case:* Automatic scaling without manual infrastructure management.
    * *Examples:* AWS Elastic Load Balancer (ELB), Google Cloud Load Balancing.

---

### **3. Load Balancing Strategies**

Strategies are the rules the load balancer follows to decide which server gets the next request.

**Static Load Balancing**
*Best for predictable workloads where servers have similar capacity.*
* **Round Robin:** Distributes requests sequentially (Server 1 -> Server 2 -> Server 3 -> Server 1). It ensures even distribution but ignores server load.
* **Least Connections:** Sends the new request to the server with the fewest active connections. Ideal when some requests take much longer to process than others (e.g., a long database query vs. a quick image load).
* **IP Hashing:** Uses the client's IP address to determine the server. This ensures a specific user always connects to the same server, which is useful for maintaining "session persistence" (e.g., keeping a user logged in).

![[03-Load balancing strategies.png]]

**Dynamic Load Balancing**
*Best for fluctuating workloads and real-time optimization.*
* **Least Response Time:** Routes traffic to the server that is responding the fastest and has the fewest active connections.
* **Adaptive Load Balancing:** Monitors real-time server health (CPU usage, memory) to avoid sending traffic to servers that are struggling.
* **Weighted Load Balancing:** Assigns a "weight" to servers based on their capacity. A powerful server might receive 2x the traffic of a weaker server.

---

### **4. Load Balancer in Action**

![[04-Load balancer in Action.png]]

**Workflow Example**
1.  **User Request:** A user visits a high-traffic e-commerce site.
2.  **Intermediary:** The request hits the Load Balancer, not the backend server directly.
3.  **Decision:** The Load Balancer applies a strategy (e.g., Round Robin).
4.  **Routing:** It forwards the request to one of the healthy backend servers.
5.  **Failover:** If that backend server crashes, the Load Balancer detects the failure and immediately routes new requests to a backup server, ensuring the user sees no error.

---

### **5. Choosing the Right Load Balancer**

When selecting a solution, consider:
* **Layer 4 vs. Layer 7:** Do you need simple speed (Layer 4) or smart routing based on URL/Cookies (Layer 7)?
* **Scalability:** For high traffic that spikes unpredictably, Cloud-based load balancers (AWS ELB) are ideal because they auto-scale.
* **Security:**
    * **SSL Termination:** The load balancer handles the heavy lifting of encrypting/decrypting HTTPS traffic, freeing up backend servers.
    * **DDoS Protection:** Enterprise and cloud load balancers often have built-in features to filter out malicious attack traffic.

---

### **6. Interview Questions on Load Balancing**

**Fundamentals**
* What is load balancing, and why is it important?
* Explain the difference between Layer 4 and Layer 7 load balancing.
* How does a load balancer handle high availability and failover?

**Strategies & Use Cases**
* Compare Round Robin and Least Connections strategies. When would you use one over the other?
* What are the advantages of Weighted Load Balancing?
* When would you use a software load balancer (Nginx) over a hardware one (F5)?

**Real-World Scenarios**
* How would you design a scalable load balancing solution for a large e-commerce site?
* How does a load balancer improve security (SSL termination, DDoS mitigation)?

---

### **7. Summary & Key Takeaways**

* **Core Benefit:** Load balancing is non-negotiable for scalable systems. It enhances reliability, prevents bottlenecks, and ensures high availability.
* **Variety:** Options range from simple Transport Layer (L4) distribution to intelligent Application Layer (L7) routing.
* **Adaptability:** Strategies like Round Robin are simple, while Adaptive/Dynamic strategies are smarter for complex loads.
* **Resilience:** It is the primary defense against server failure, ensuring users always have a seamless experience.

**What’s Next:**
Now that we understand how to distribute traffic, the next lecture will cover **API Gateways**—a component that often sits *in front* of load balancers to handle authentication, rate limiting, and API management.