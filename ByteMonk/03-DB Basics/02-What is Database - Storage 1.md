# **System Design: Foundational Storage Concepts - Short Notes**  

## **1. Introduction to Storage in System Design**  
- Every system (e.g., Facebook, Google, Amazon, Netflix) requires storage to manage data.  
- Storage is needed for:  
  - User information (name, date of birth, credit card details).  
  - System-related data.  
- **Database** is the primary component used for storage.  

## **2. What is a Database?**  
- A database serves two main purposes:  
  - **Store (Write/Set/Record) data.**  
  - **Retrieve (Read/Get/Query) data.**  
- **Misconception:** Databases are not "magical boxes" but simply servers that store and retrieve data.  
- **Example:** A regular computer can act as a database if configured to allow clients to read/write data.  

## **3. Persistence in Databases**  
- **Persistence** ensures data remains intact even after failures (power outage, network issues, crashes).  
- **Key Insight:** Not all databases guarantee persistence by default.  

### **Storage Mechanisms:**  
1. **Disk Storage (Persistent Storage)**  
   - Data written to **disk (hard drive/SSD)** remains even after a server reboot.  
   - **Example:** Saving a file on a computer—it stays unless the disk is physically damaged.  
   - **Trade-off:** Slower access compared to memory.  

2. **In-Memory Storage (Non-Persistent Storage)**  
   - Data stored in **RAM (arrays, hash tables)** is lost if the server crashes/reboots.  
   - **Advantage:** Extremely fast read/write operations.  
   - **Use Case:** Caching, real-time processing.  

## **4. Types of Databases**  
- There are **hundreds of database types**, broadly categorized as:  
  1. **Relational Databases (SQL)** – Structured, ACID-compliant (e.g., MySQL, PostgreSQL).  
  2. **NoSQL Databases** – Flexible, scalable (e.g., MongoDB, Cassandra).  
- **Trade-offs exist** (discussed in **CAP Theorem** – Consistency, Availability, Partition Tolerance).  

## **5. Key Takeaways**  
- Databases are essential for **storing and retrieving data** in any system.  
- **Persistence** determines whether data survives failures (disk = persistent, memory = volatile).  
- **Performance vs. Durability:**  
  - **Disk = Slower but durable.**  
  - **Memory = Faster but temporary.**  
- Future discussions will cover **relational vs. NoSQL databases** in system design.  

---
**Next Steps:**  
- Explore **CAP Theorem** for database trade-offs.  
- Learn about **latency & throughput** in storage systems.  
- Stay tuned for videos on **relational vs. NoSQL databases**.  

---
