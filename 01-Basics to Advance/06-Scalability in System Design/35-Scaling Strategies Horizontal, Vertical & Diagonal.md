Here are the notes for **Section 6: Scaling Strategies**, based on the provided lecture materials.

### **Overview of Scaling Strategies**

Scaling is the execution phase of system design, moving from concept to implementation. There are three core strategies used to handle system growth:

1. **Vertical Scaling (Scaling Up):** Upgrading the existing machine.
    
2. **Horizontal Scaling (Scaling Out):** Adding more machines to the pool.
    
3. **Diagonal Scaling:** A hybrid approach combining both methods.
    

---

### **Deep Dive: The Three Strategies**

#### **1. Vertical Scaling (Scaling Up)**

- **Definition:** Increasing the power of a single server by adding more CPU, RAM, or Disk space.
    
- **Pros:**
    
    - **Simplicity:** Easy to implement as there is no need for load balancing, distributed data, or synchronization across nodes.
        
    - **Performance:** Excellent for CPU-heavy or memory-bound workloads on a single node.
        
- **Cons:**
    
    - **Hardware Limits:** You eventually hit a physical cap where hardware cannot be upgraded further.
        
    - **Single Point of Failure (SPOF):** If that one powerful server goes down, the entire application goes down.
        

#### **2. Horizontal Scaling (Scaling Out)**

- **Definition:** Adding more machines or nodes to the infrastructure to distribute traffic and load.
    
- **Requirements:** Requires **Load Balancers** to distribute traffic and a **stateless architecture** (or robust coordination) to ensure all servers can access necessary data.
    
- **Pros:**
    
    - **Redundancy:** High availability; if one node fails, others take over.
        
    - **Unlimited Scale:** Theoretically, you can keep adding machines indefinitely.
        
- **Cons:**
    
    - **Complexity:** Introduces challenges regarding data replication, synchronization, and system orchestration.
        

#### **3. Diagonal Scaling**

- **Definition:** A hybrid strategy where you scale vertically until cost or hardware limits are reached, then scale horizontally.
    
- **Use Case:** Common in cloud-native applications. It offers the simplicity of vertical scaling early on while maintaining the long-term growth potential of horizontal scaling.
    

---

### **Trade-Off Analysis: Cost, Complexity, & Performance**

Choosing a strategy involves balancing the classic system design triangle.

|**Strategy**|**Cost**|**Complexity**|**Performance**|
|---|---|---|---|
|**Vertical**|**Low-Mid** (Starts cheap, high-end hardware gets expensive)|**Low** (No distributed coordination needed)|**Medium** (Good for single-threaded tasks, but has bottlenecks)|
|**Horizontal**|**High** (More infrastructure, network, and operational overhead)|**High** (Requires load balancing, sharding, replication)|**High** (Parallelism and redundancy)|
|**Diagonal**|**Medium** (Optimizes cost by maximizing individual nodes before adding more)|**Medium** (Balances simplicity with scale)|**High** (Flexible growth)|

---

### **Real-World Application: When to Choose What?**

- **Startups / MVPs:** Choose **Vertical Scaling**. It is cheaper, faster to deploy, and easier to maintain for small user bases.
    
- **Large Scale / Global Apps (e.g., Twitter):** Choose **Horizontal Scaling**. Necessary for resilience, high throughput, and massive global traffic. Twitter moved from a monolith (vertical) to microservices (horizontal) to handle growth.
    
- **Cloud-Native / Serverless (e.g., AWS Lambda):** Choose **Diagonal Scaling**. These platforms start small but can automatically scale up and out based on traffic spikes to control costs.
    

---

### **Common Interview Questions**

- What is the difference between horizontal and vertical scaling?
    
- What is diagonal scaling and when is it a good idea?
    
- What are the trade-offs between horizontal and vertical scaling in terms of performance and complexity?
    
- Can you describe a scenario where horizontal scaling wouldn’t help?
    
- When would you choose vertical scaling over horizontal?
    

---

**What's Next:** The next lecture will cover **Load Balancers**, examining types, algorithms, and cloud solutions essential for enabling horizontal scaling.