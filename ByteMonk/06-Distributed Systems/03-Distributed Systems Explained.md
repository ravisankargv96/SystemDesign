# **System Design: Introduction to Distributed Systems - Short Notes**  

## **1. What is a Distributed System?**  
- A **distributed system** consists of multiple computers (nodes) working together over a network to appear as a single system.  
- **Examples:**  
  - Online shopping (Amazon), video streaming (Netflix), search engines (Google).  
  - Even simple cloud-hosted websites run on distributed systems.  
- **Key Goal:** Provide a **seamless user experience** while handling **millions of users & petabytes of data**.  

### **Centralized vs. Distributed Systems**  
| **Centralized System** | **Distributed System** |  
|------------------------|------------------------|  
| Runs on a single machine. | Runs on multiple machines (nodes). |  
| Limited scalability (vertical scaling). | Scales **horizontally** (add more machines). |  
| **Single point of failure** (if the machine crashes, the whole system fails). | **Fault-tolerant** (if one node fails, others take over). |  
| High latency for global users. | Reduced latency (servers distributed globally). |  

## **2. Why Distributed Systems?**  
### **Problems with Centralized Systems**  
- **Vertical Scaling (Upgrading a single machine):**  
  - Limited by max CPU, RAM, and storage.  
  - Only delays performance issues, doesn’t solve them.  
- **Single Point of Failure:**  
  - Power outage, hardware failure, or network issues can crash the entire system.  
- **High Latency for Remote Users:**  
  - Users far from the server experience slow responses.  

### **Advantages of Distributed Systems**  
✔ **Horizontal Scaling:** Add more machines to handle increased load.  
✔ **Fault Tolerance:** No single point of failure.  
✔ **Low Latency:** Servers placed globally reduce response time.  
✔ **High Availability:** Even if some nodes fail, the system remains operational.  

## **3. Key Concepts in Distributed Systems**  
### **Processes & Communication**  
- A **process** is an instance of a running program (e.g., a Java application loaded into memory).  
- **In a centralized system:**  
  - Processes run on the same machine and communicate via memory, file system, or network.  
  - Limited to the capacity of one machine.  
- **In a distributed system:**  
  - Processes run on **different machines** and communicate **only via network**.  
  - Must maintain a **shared state** and work towards a **common goal**.  

### **Challenges in Distributed Systems**  
1. **Network Communication:**  
   - Messages can be **lost, delayed, or duplicated**.  
2. **Coordination & Consistency:**  
   - Ensuring all nodes **agree on shared data** (e.g., database consistency).  
3. **Fault Tolerance:**  
   - Handling **node failures** without disrupting the system.  
4. **Scalability:**  
   - Adding more nodes should improve performance without bottlenecks.  

## **4. Future Topics in Distributed Systems**  
- **Best practices** for designing distributed systems.  
- **Algorithms** for coordination (e.g., consensus algorithms like Paxos, Raft).  
- **Patterns** for scalability & fault tolerance (e.g., sharding, replication).  

---
### **Key Takeaways**  
✅ Distributed systems **eliminate single points of failure** and **scale horizontally**.  
✅ **Processes communicate via network** and must maintain a shared state.  
✅ **Challenges include** network reliability, consistency, and fault tolerance.  
✅ **Next:** Explore distributed algorithms, CAP theorem, and replication strategies.  

---
**Action Items:**  
🔹 Understand **vertical vs. horizontal scaling**.  
🔹 Learn about **latency & fault tolerance** in distributed systems.  
🔹 Watch for future videos on **distributed algorithms & system design patterns**.  
