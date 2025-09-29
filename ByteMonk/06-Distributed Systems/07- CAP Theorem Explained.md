# **Distributed Systems & CAP Theorem - Short Notes**

## **1. Distributed Systems Fundamentals**
- **Definition:** Multiple computers working together to appear as a single system
- **Key Characteristics:**
  - Nodes can be physically close (LAN) or geographically distributed (WAN)
  - Goal: Provide unified computing experience despite distributed nature
- **Implementation:** Often uses microservices architecture
  - Application decomposed into specialized services
  - Each service handles one specific function

## **2. Network Partitions & CAP Theorem**
### **The Partition Problem**
- Networks fail unpredictably (temporary or permanent)
- When partition occurs, systems must choose between:
  1. **Consistency (CP Systems)**
     - Reject operations until partition resolves
     - Example: Payment systems where accuracy is critical
  2. **Availability (AP Systems)**
     - Continue operating with potentially stale data
     - Example: Shopping carts where continuity matters more

### **CAP Theorem Explained**
| Option | Description | Use Cases |
|--------|-------------|-----------|
| **Consistency** | All nodes see same data simultaneously | Financial transactions, booking systems |
| **Availability** | System remains operational during partitions | Shopping carts, social media feeds |
| *Partition Tolerance* | System continues despite network failures | (Required for all distributed systems) |

## **3. Database Selection for Distributed Systems**
### **SQL vs NoSQL**
| Type | Scalability | CAP Alignment | Examples |
|------|------------|--------------|----------|
| **SQL (CA)** | Vertical scaling | Consistency + Availability | MySQL, PostgreSQL |
| **NoSQL** | Horizontal scaling | CP or AP models | Cassandra (AP), MongoDB (CP) |

### **CA Databases Limitation**
- Assume no network partitions (unrealistic in distributed systems)
- Primarily single-node systems
- Best for non-distributed applications

## **4. Practical CAP Tradeoffs**
### **When to Choose CP**
- **Critical systems** where data must be 100% accurate
- Examples:
  - Payment processing
  - Airline reservations
  - Medical record systems

### **When to Choose AP**
- **User experience-focused** applications
- Examples:
  - E-commerce shopping carts
  - Social media platforms
  - Content delivery networks

## **5. Key Takeaways**
1. All distributed systems must handle **network partitions**
2. **CAP theorem** forces choice between consistency and availability
3. **NoSQL databases** generally better suited for distributed systems
4. **Business requirements** dictate CP vs AP choice
5. **CA databases** are for non-distributed use cases

**Next Steps:**
- Explore **eventual consistency** patterns
- Study **real-world distributed system architectures**
- Learn about **conflict resolution** in AP systems