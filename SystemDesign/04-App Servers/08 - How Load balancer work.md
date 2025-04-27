# **Load Balancers in System Design - Comprehensive Notes**

## **1. Fundamentals of Load Balancing**

### **Core Concept**
- Acts as a "traffic cop" distributing client requests across multiple servers
- Primary objectives:
  - Maximize server throughput
  - Minimize response latency
  - Prevent server overload

### **Scaling Context**
1. **Vertical Scaling** (Scale Up):
   - Increase single server resources (CPU, RAM)
   - Limited by physical hardware constraints

2. **Horizontal Scaling** (Scale Out):
   - Add more servers to the system
   - Requires load balancing for effective distribution
   - Can handle 3x more load with 3 servers (linear scaling)

## **2. Load Balancer Architecture**

### **Basic Operation**
```
Clients → Load Balancer → [Server1, Server2, Server3]
```
- Sits between clients and server pool
- Becomes system's public endpoint (reverse proxy)

### **Deployment Levels**
1. **Application Layer**: Between clients and web servers
2. **Database Layer**: Between app servers and databases
3. **DNS Layer**: Distributes requests at domain resolution

### **Implementation Types**
| Type            | Pros                         | Cons                       |
| --------------- | ---------------------------- | -------------------------- |
| **Hardware LB** | High performance             | Expensive, inflexible      |
| **Software LB** | Cost-effective, customizable | Slightly lower performance |

## **3. Server Selection Strategies**

### **Basic Methods**
4. **Random Selection**
   - Simple but can lead to uneven distribution

5. **Round Robin**
   - Cyclic distribution (S1→S2→S3→S1)
   - Ensures equal request count per server

6. **Weighted Round Robin**
   - Assigns weights based on server capacity
   - Example: Powerful server gets 2x requests

### **Advanced Methods**
7. **Least Connections**
   - Directs to server with fewest active connections
   - Ideal for variable request processing times

8. **IP Hash**
   - Consistent client→server mapping via IP hashing
   - Benefits:
     - Session persistence
     - Cache optimization (same client→same server)

9. **Health-Based**
   - Monitors server metrics (CPU, response time)
   - Avoids unhealthy servers

## **4. Practical Examples**

### **DNS Load Balancing (Google Example)**
- `nslookup google.com` returns different IPs
- Distributes traffic at domain resolution level
- Provides geographical load balancing

### **Cache Optimization Scenario**
10. ClientA → LB → Server1 (computes and caches)
11. Subsequent ClientA requests → Server1 (cache hit)
12. Avoids recomputation on other servers

## **5. Operational Considerations**

### **Server Management**
- Dynamic registration/deregistration
- Health checks and failover mechanisms

### **Advanced Architectures**
- Multi-tier load balancing
- Hybrid selection strategies
- Global server load balancing (GSLB)

## **6. Key Takeaways**

13. **Essential for horizontal scaling** - enables linear capacity growth
14. **Multiple deployment options** - from DNS to database layers
15. **Strategy depends on use case**:
   - Round Robin for equal distribution
   - IP Hash for session/cache needs
   - Least Connections for variable workloads
16. **Critical for high availability** - prevents single server overload

**Next Steps:**
- Explore sticky sessions vs stateless LB
- Study cloud LB services (AWS ALB, Nginx)
- Learn about LB algorithms in depth