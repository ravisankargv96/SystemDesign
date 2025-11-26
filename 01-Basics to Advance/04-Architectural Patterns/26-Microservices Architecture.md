Here are the comprehensive notes on Microservices Architecture based on the provided lecture materials.

### **Introduction to Microservices Architecture**

Definition

Microservices architecture is a software design pattern where an application is structured as a collection of small, independent services, each responsible for a specific business function.

**Microservices vs. Monoliths**

- **Monoliths:** All components are tightly integrated into a single unified system.
    
- **Microservices:** Components are loosely coupled, operate independently, and communicate via APIs.
    

**Key Characteristics**

- **Independently Deployable:** Each service can be updated, deployed, and maintained without affecting others.
    
- **Loosely Coupled & Modular:** Services interact through well-defined APIs but remain self-contained.
    
- **Scalable & Fault-Tolerant:** Individual services can be scaled based on demand, and failure in one service does not crash the entire system.
    

---

### **Identifying and Designing Microservices**

Deciding how to break down an application is a critical challenge. The following principles guide this process:

**1. Core Principles**

- **Business Capabilities:** Align services with specific business functions (e.g., Payment, Order, User) to ensure clear ownership.
    
- **Single Responsibility Principle:** A service should do one thing well; if it handles unrelated concerns, it should be decomposed further.
    
- **Data Ownership:** Each microservice must manage its own database. Shared databases create dependencies and reduce deployment independence.
    

**2. Structuring Strategies**

- **Domain-Driven Design (DDD):** Break the system into logical domains to group services based on business needs.
    
- **Granularity:** Choose the right size—too large results in a "monolith in disguise," while too small increases complexity.
    
- **Observability:** Implement logging, monitoring, and tracing to track interactions and identify issues early.
    

---

### **Communication Models**

Services must exchange data to process requests. There are two primary models:

1. Synchronous Communication

The service waits for a response before proceeding.

- **REST APIs:** The most common approach using HTTP standards (JSON/XML). It is easy to implement but can introduce higher latency due to text-based communication.
    
- **gRPC:** A high-performance protocol using binary format (Protocol Buffers). It is efficient and ideal for low-latency requirements.
    

2. Asynchronous Communication

Services do not wait for an immediate response; they rely on events.

- **Event-Driven Messaging:** Uses message brokers like **Kafka**, **RabbitMQ**, or **AWS SNS/SQS**.
    
- **Benefit:** Decouples services (e.g., an Order Service publishes an "order created" event, and Inventory Service reacts to it independently).
    

---

### **Challenges of Microservices**

While beneficial, microservices introduce specific complexities:

- **Data Consistency:** Distributed databases lead to **eventual consistency**, where changes take time to propagate across services.
    
- **Distributed Tracing:** Debugging is difficult because a single request spans multiple services over a network.
    
- **Network Overhead:** Heavy reliance on API calls introduces latency compared to in-memory calls in a monolith.
    
- **Security:** Requires decentralized security measures, including authentication and authorization for service-to-service communication.
    

---

### **Scaling Strategies**

Microservices allow for precise scaling of individual components rather than the whole system.

- **Horizontal Scaling:** Adding multiple instances of a specific microservice to distribute traffic.
    
- **Auto-Scaling:** Using cloud tools or Kubernetes to automatically add or remove instances based on CPU, memory, and load.
    
- **Sharding & Database Scaling:** Splitting databases into smaller partitions (sharding) or using read replicas to handle high traffic.
    

---

### **Real-World Examples**

- **Netflix:** Decoupled video streaming, personalization, and recommendations into separate services to scale for millions of users.
    
- **Uber:** independently scales ride-matching, payments, and navigation.
    
- **Amazon:** Runs functions like search and payments as modular services to handle massive traffic without downtime.
    

---

### **Common Interview Questions**

- What are microservices, and how do they differ from monolithic architecture?
    
- What are the benefits and challenges of microservices?
    
- Explain the role of an API Gateway in a microservices system.
    
- How do microservices communicate with each other?
    
- How can you ensure data consistency in a microservices-based system?
    

**What's Next:** The next lecture will cover **Event-Driven Architectures**.