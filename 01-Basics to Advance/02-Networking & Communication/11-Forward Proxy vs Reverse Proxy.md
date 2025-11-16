## 🛡️ Forward Proxy vs. Reverse Proxy

![[Pasted image 20251115150222.png]]

A **proxy server** is an intermediary server that sits between a client and another server, helping with security, caching, traffic control, and anonymity. There are two main types of proxies, each serving a distinct purpose in the network architecture:

---
### 1. Forward Proxy (Client-Side)

![[Pasted image 20251115150318.png]]
A **Forward Proxy** sits between a **client** and the **internet**. It handles **outgoing requests** on behalf of the client. The target server sees the request coming from the proxy's IP address, not the client's.

|**Feature**|**Details**|
|---|---|
|**Position**|Between the **Client** and the **Internet**.|
|**Who Uses It**|Clients, individual users, and organizations.|
|**Primary Purpose**|**Anonymity**, **privacy**, content filtering, and access control.|
|**Use Cases**|* **Anonymous browsing** (Hides user IP, e.g., VPNs, TOR).<br><br>  <br><br>* **Content Filtering** (Restricts access to certain websites).<br><br>  <br><br>* **Bypassing Geo-restrictions** (Accessing region-blocked content).<br><br>  <br><br>* **Caching** web pages to speed up browsing.|
|**Example**|VPN, Web Proxy.|
![[Pasted image 20251115150257.png]]

---
### 2. Reverse Proxy (Server-Side)

![[Pasted image 20251115150359.png]]

A **Reverse Proxy** sits between **users** and **backend servers**. It handles **incoming requests** on behalf of the server infrastructure. The client communicates only with the reverse proxy, which then routes the request to an appropriate backend server.

| **Feature**         | **Details**                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Position**        | Between **Users/Internet** and **Backend Servers**.                                                                                                                                                                                                                                                                                                                                                                      |
| **Who Uses It**     | Web servers, application servers, and backend infrastructure.                                                                                                                                                                                                                                                                                                                                                            |
| **Primary Purpose** | **Load balancing**, **security**, caching, and performance optimization.                                                                                                                                                                                                                                                                                                                                                 |
| **Use Cases**       | * **Load Balancing** (Distributes incoming traffic across multiple servers).<br><br>  <br><br>* **Security & DDoS Protection** (Hides actual backend IP addresses and filters malicious traffic).<br><br>  <br><br>* **SSL Termination** (Offloads the heavy task of encrypting/decrypting HTTPS traffic from backend servers).<br><br>  <br><br>* **Caching** content to improve response time and reduce backend load. |
| **Example**         | Nginx, Cloudflare, AWS Application Load Balancer (ALB).                                                                                                                                                                                                                                                                                                                                                                  |

![[Pasted image 20251115150412.png]]

---
### Key Takeaways for System Design

- A forward proxy is client-centric, helping the client interact with the internet securely and anonymously.
- A reverse proxy is server-centric, protecting and optimizing backend servers to ensure scalability and high availability.
- Understanding these roles is essential for designing scalable and secure architectures.

The next core topic is **Load Balancers**.
