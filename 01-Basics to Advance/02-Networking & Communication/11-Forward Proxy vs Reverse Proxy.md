### **1. Forward Proxy vs. Reverse Proxy**

**Concept Overview**
* **Definition:** A proxy server acts as an intermediary between a client (like your computer or phone) and another server (like a website).
* **Role:** Instead of communicating directly, the traffic passes through this middleman.
* **Core Functions:** Proxies are essential in modern system design for enhancing security, managing traffic, caching content to improve speed, and ensuring anonymity.

![[01-What is Proxy.png]]

**Two Main Types**
While all proxies act as intermediaries, they are classified based on where they sit in the network and who they protect:
* **Forward Proxy:** Protects the Client.
* **Reverse Proxy:** Protects the Server.

---

### **2. What is a Forward Proxy?**

**Definition & Workflow**
* **Position:** A forward proxy sits **in front of the client** (the user).
* **Flow:** When you try to access a website (like Google), your request goes to the forward proxy first. The proxy then forwards the request to the internet on your behalf, gets the response, and sends it back to you.
* **Perspective:** From the internet's point of view, the request looks like it came from the proxy server, not from your specific device.

![[02-what is forward proxy.png]]

**Key Use Cases & Benefits**
* **Privacy & Anonymity:** It masks the client's real IP address. This is how VPNs work—websites see the VPN's IP, not yours.
* **Content Filtering:** Organizations and schools use forward proxies to block access to specific websites (e.g., blocking social media on a corporate network).
* **Bypassing Geo-Restrictions:** If content is blocked in your country, you can route your traffic through a proxy located in a different country to access it.
* **Client-Side Caching:** It can store frequently accessed resources (like a company logo) locally, saving bandwidth for the entire local network.

![[02-what is forward proxy 2.png]]

---

### **3. What is a Reverse Proxy?**

![[03-what is reverse proxy.png]]

**Definition & Workflow**
* **Position:** A reverse proxy sits **in front of the backend servers**.
* **Flow:** When a client sends a request to a website, the request hits the reverse proxy first. The proxy then decides which specific backend server should handle that request, retrieves the data, and sends it back to the client.
* **Perspective:** The client thinks they are talking directly to the server, but they are actually talking to the proxy. The client never sees the actual IP address of the backend server.

![[04-what is reverse proxy.png]]

**Key Use Cases & Benefits**
* **Load Balancing:** This is a critical function. The proxy distributes incoming traffic across multiple servers to prevent any single server from crashing due to overload.
* **Security & DDoS Protection:** It acts as a shield. Attackers hit the proxy, not the sensitive database or application servers behind it.
* **SSL Termination:** Encrypting and decrypting data (HTTPS) requires high computational power. A reverse proxy can handle this "handshake," freeing up the backend servers to focus purely on processing application logic.
* **Caching:** It stores static content (images, CSS) so the backend servers don't have to generate the same data repeatedly.

---

### **4. Key Differences - Forward vs. Reverse Proxy**

The following table summarizes the distinctions between the two:

| Feature | Forward Proxy | Reverse Proxy |
| :--- | :--- | :--- |
| **Position** | Sits between the **Client** and the Internet. | Sits between the Internet and the **Backend Servers**. |
| **Primary User** | **Clients** (users, browsers, internal networks). | **Servers** (web servers, APIs, app servers). |
| **Primary Goal** | Protects the client (Anonymity, Filtering). | Protects the server (Load Balancing, Security). |
| **Visibility** | The server does not know who the actual client is. | The client does not know who the actual server is. |
| **Real-World Examples** | VPNs (NordVPN), School Content Filters. | Nginx, Cloudflare, AWS Application Load Balancer. |

---

### **5. Interview Questions on Forward vs. Reverse Proxy**

Be prepared to answer these common system design questions:

* **Basic Concepts:**
    * What is a proxy server, and why do we use it?
    * Explain the fundamental difference between a forward and reverse proxy.
* **Technical Deep Dive:**
    * How does a forward proxy provide anonymity?
    * How does a reverse proxy assist with SSL termination?
    * In a Distributed Denial of Service (DDoS) attack, how does a reverse proxy protect the backend infrastructure?
* **Architecture:**
    * When designing a system like Netflix or Facebook, where would you place a reverse proxy?
    * Why is Nginx preferred as a reverse proxy?

---

### **6. Wrap-Up & What’s Next**

* **Summary:** Both proxies are intermediaries, but they serve opposite sides of the communication bridge. Forward proxies are the "bodyguards" for the client, while Reverse proxies are the "receptionists and bodyguards" for the server.
* **Importance:** Knowing when to implement which proxy is crucial for designing architectures that are secure, scalable, and efficient.
* **Next Topic:** We will dive deeper into one of the most critical functions of a reverse proxy: **Load Balancers**, exploring how they distribute traffic to keep systems reliable.