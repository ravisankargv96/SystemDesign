
# System Design: Understanding Latency and Throughput

## Introduction

- Lag or slowness in video games is often caused by a combination of **high latency** and **low throughput**.
- **Latency** and **throughput** are key performance measures in software systems but are often misunderstood.
- This document clarifies these concepts for better understanding in technical discussions and system design interviews.
---
## **Latency**

### Definition:

- **Latency** refers to the time taken for data to travel from one point in a system to another.
- It can manifest in different forms:
    - **Network Latency**: Time taken for a network request to travel from the client (e.g., user) to the server (e.g., Google) and back.
    - **Machine Latency**: Time taken to read data from memory or disk.

### **Examples of Latency Measurements:**

| Operation                                                                  | Latency        |
| -------------------------------------------------------------------------- | -------------- |
| Sending a 1,000-byte IP packet from California to the Netherlands and back | **150,000 µs** |
| Reading 1MB from memory                                                    | **250 µs**     |
| Reading 1MB from an SSD                                                    | **1,000 µs**   |
| Transferring 1MB over a 1Gbps network                                      | **1,000 µs**   |
| Reading 1MB from a HDD                                                     | **20,000 µs**  |

- These numbers provide a sense of magnitude rather than values to memorize.    
### **Trade-offs in System Design:**

- Some systems are **sensitive to latency**, such as:
    - **Video games** (require fast response times).
    - **Real-time applications** (e.g., live streaming, stock trading).
- Other systems prioritize **accuracy and uptime over latency**, such as:
    - **Airline booking systems** (ensure correct reservations rather than instant response times).
- System designers must **consider these trade-offs** in architecture and implementation.
---

## **Throughput**

### Definition:
- **Throughput** measures how much work a computer system can perform in a given time.
- It represents the **amount of data** transferred or processed.
### **Examples of Throughput Measurements:**
- Internet download speed: **50 Mbps** means the ISP can transfer **50 megabits per second**.
- Server request processing: HTTP requests per second (RPS) a server can handle.
### **Factors Affecting Throughput:**

- **High traffic/load:** If too many requests hit a server, its throughput decreases.
- **Server scaling strategies:**
    - **Vertical Scaling:** Upgrading the server’s hardware to handle more requests (limited by physical constraints).
    - **Horizontal Scaling:** Adding more servers to distribute requests and process them in parallel (scalable approach).
    
---
## **Key Takeaways**
- **Latency and throughput are independent metrics.**
    - A system can have low latency but also low throughput.
    - They do not always correlate; improving one does not necessarily improve the other.
- **Optimizing system performance requires balancing both latency and throughput** based on system needs.
- Understanding these concepts is crucial for **designing scalable and efficient systems**, particularly in interviews and real-world applications.

---

### **Conclusion**
- Knowing when to prioritize latency vs. throughput is a crucial system design decision.
- Optimize latency for **real-time applications** and throughput for **high-load processing systems**.
- **Scaling strategies** (vertical vs. horizontal) help in managing throughput efficiently.

**Mastering these concepts will help you confidently approach system design discussions and technical interviews.**
