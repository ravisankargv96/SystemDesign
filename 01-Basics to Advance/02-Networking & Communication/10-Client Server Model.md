## 💻 Client-Server Model Explained

The **Client-Server Model** is a fundamental computing framework where **clients request services** and **servers provide them**. It is the foundation of modern web, database, and application architectures, enabling efficient resource management.

![[Pasted image 20251115145705.png]]

---
### Key Components

The model involves three main components:
- **Client**: The user-facing application that initiates the request.    
    - _Examples_: Web browser, mobile app, API consumer.
- **Server**: A system that processes the request and returns the response.
    - _Examples_: Web server, database server, mail server.
- **Network**: The communication medium (e.g., Internet, LAN, Wi-Fi) that transmits the request and response between them.

### Communication Process

Communication follows a **Request/Response Model** (like HTTP or REST APIs) where the client initiates the interaction, or **Persistent Connections** (like WebSockets).

**Basic Steps (Request-Response Cycle):**

1. **Client sends a request** (e.g., HTTP GET request).
2. Request is **transmitted over the network**.    
3. **Server receives and processes** the request (e.g., fetches data from a database).
4. **Server sends a response** (e.g., HTTP response with a status code and content).
5. **Client receives and processes** the response (e.g., renders the webpage).

![[Pasted image 20251115145758.png]]

---

### Communication Patterns

The model uses different patterns depending on application needs:
#### Synchronous vs. Asynchronous Communication

| **Feature**         | **Synchronous (Blocking)**                                   | **Asynchronous (Non-Blocking)**                                              |
| ------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **Client Behavior** | **Waits** for a response before proceeding with other tasks. | **Doesn't wait** for a response; continues other tasks in the background.    |
| **Use Case**        | Traditional web apps, REST APIs (immediate result needed).   | Real-time chat (WebSockets), live updates, background requests (e.g., AJAX). |

![[Pasted image 20251115150006.png]]

![[Pasted image 20251115150030.png]]

#### Stateless vs. Stateful Servers

| **Feature**        | **Stateless Servers**                                            | **Stateful Servers**                                                               |
| ------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| **Session Memory** | **No memory** of past interactions; each request is independent. | **Maintains session information** across multiple requests (remembers user state). |
| **Key Benefit**    | **Scalability**, easy caching, works well with load balancing.   | **Personalization**, seamless user experience (e.g., maintaining a game session).  |
| **Examples**       | REST APIs, basic HTTP servers.                                   | WebSockets, multiplayer games, banking applications.                               |

![[Pasted image 20251115150057.png]]

---

### Role in System Design

Understanding the client-server model and its patterns is essential for system design and scalability planning:
- It forms the basis for **Web Applications**, **APIs & Microservices**, and **Database** interactions.
- The choice between stateless and stateful design is crucial for optimizing **performance, scalability**, and **user experience**.

---

**Next Steps**: The next lecture will dive into **Forward Proxy vs. Reverse Proxy**, which are components that build upon this model for security and performance optimization.
