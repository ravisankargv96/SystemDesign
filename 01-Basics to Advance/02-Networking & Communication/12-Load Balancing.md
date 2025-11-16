## ⚖️ Load Balancing in System Design


![[Pasted image 20251115150647.png]]

**Load balancing** is the process of distributing incoming network traffic efficiently across a group of backend servers, known as a server farm or pool. It is essential for ensuring **high availability, scalability, and reliability** in modern applications.

---
### Why Load Balancing is Essential

- **High Availability & Reliability**: Ensures the system stays operational even when traffic spikes or if one server fails, by redirecting traffic to healthy servers (failover).
- **Prevents Overload**: Spreads requests evenly to prevent any single server from becoming overwhelmed and crashing under heavy load.
- **Improves Performance**: Reduces overall latency and response times by sending requests to the least busy or fastest responding server.
- **Supports Scalability**: Allows system capacity to be increased simply by adding more servers, as the load balancer automatically includes them in the distribution pool.

---
### Types of Load Balancers


Load balancers are categorized by the network layer they operate on and their deployment model.

![[Pasted image 20251115150716.png]]
#### 1. Based on Network Layer

| **Type**    | **Layer of Operation**             | **Routing Decision Based On**                                                        | **Use Case & Speed**                                                                                           |
| ----------- | ---------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| **Layer 4** | **Transport Layer** (TCP/UDP)      | **Network-level data**: IP addresses and port numbers. Does **not** inspect content. | **Extremely fast** and efficient; ideal when speed is the highest priority.                                    |
| **Layer 7** | **Application Layer** (HTTP/HTTPS) | **Request content**: HTTP headers, cookies, query strings, URL paths.                | **Intelligent routing** (e.g., sending product traffic to one set of servers and checkout traffic to another). |
#### 2. Based on Deployment

- **Hardware**: Physical devices built for **high performance** and low latency in large enterprises (e.g., F5, Citrix NetScaler).    
- **Software**: Applications running on general-purpose servers, offering **flexibility** and cost-effectiveness (e.g., Nginx, HAProxy, Envoy).
- **Cloud-based**: Managed services that **automatically scale** and distribute traffic across regions, eliminating manual management (e.g., AWS ELB, Google Cloud Load Balancing).

---
### Load Balancing Strategies

Strategies are categorized as either static (predefined rules) or dynamic (real-time performance).


![[Pasted image 20251115150743.png]]
#### Static Strategies (Predefined Rules)

- **Round Robin**: Sends requests **sequentially** to each server in a circular order. Simple, but doesn't account for server load.
- **Least Connections**: Directs new requests to the server with the **fewest active connections**. Useful when request processing times vary.
- **IP Hashing (Session Affinity/Sticky Session)**: Routes requests from the **same client IP address** consistently to the same backend server. Essential for maintaining user session data.
#### Dynamic Strategies (Real-Time Performance)

- **Least Response Time**: Sends requests to the server with the **lowest response time**, ensuring the fastest possible user experience.
- **Adaptive Load Balancing**: Continuously analyzes **real-time data** (CPU usage, memory) to dynamically shift traffic to healthier servers, preventing overload.
- **Weighted Load Balancing**: Assigns different **weights** (e.g., a more powerful server receives twice the requests) to servers based on their processing capacity.

---
### Choosing the Right Load Balancer

The optimal choice depends on the application's specific needs:

- **Layer Choice**: Use **Layer 4 for speed** (TCP/UDP traffic) and **Layer 7 for intelligent routing** (HTTP, APIs, microservices).
- **Scalability**: Use cloud-based balancers for unpredictable spikes or global scale, and hardware balancers for mission-critical, low-latency enterprise needs.
- **Security**: Choose a load balancer that provides **SSL termination** (offloading encryption) and **DDoS mitigation** to protect backend servers.

---

**What's Next**: The next lecture will cover the **API Gateway**, its role in modern architecture, and how it differs from traditional load balancers.