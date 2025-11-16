## 📓 Lecture Notes: Section 3 Summary - Protocols

This lecture provides a high-level summary of all the key communication and API design protocols covered in this section, which are the fundamental building blocks of modern system design.

---
### Section Recap

- **TCP & UDP:** We started with the transport layer basics.    
    - **TCP:** Ensures **reliable**, ordered, and error-checked communication. It's ideal for applications where data integrity is critical (e.g., web browsing, email).
    - **UDP:** A **lightweight and faster** protocol that does _not_ guarantee delivery. It's suitable for real-time applications where speed is more important than perfect accuracy (e.g., VoIP, online gaming).
    
- **HTTP:** We covered the foundation of web communication.
    - It follows a **stateless, request-response** cycle.
    - We discussed its methods (e.g., GET, POST, PUT, DELETE, PATCH) and the role of status codes in handling responses.

- **REST & RESTfulness:** We dived into the principles of designing RESTful APIs.  
    - This included focusing on **resources**, defining endpoints, and using structured data formats like JSON and XML.

- **Real-Time Communication:** We moved beyond the traditional request-response model.    
    - **WebSockets:** Enables persistent, **full-duplex** (two-way) communication. It's perfect for chat applications and live stock price updates.
    - **Long Polling:** A technique that simulates real-time updates. It's useful for systems like notifications or social media feeds that need near-instant updates without continuous data flow.

- **Modern API Protocols (Beyond REST):** We explored modern alternatives.    
    - **gRPC:** A high-performance framework using **Protobuf and HTTP/2**. It's extremely fast and efficient, making it ideal for communication between microservices.
    - **GraphQL:** A query language that allows clients to fetch _only_ the data they need. This solves the problems of **over-fetching and under-fetching**, making it a great choice for frontend and mobile applications.

---

### 🚀 What’s Next?

With a strong foundation in communication protocols, the course will now shift focus to **Architectural Patterns**.

The next section will explore:

- How different system components interact.    
- How to design for scalability and performance.
- Different architectural styles, such as monolithic, microservices, and event-driven architecture.