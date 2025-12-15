
### **1. Understanding IP Addresses in System Design**

**Concept Overview**

  * **Definition:** An IP (Internet Protocol) address is a unique numerical label assigned to every device on a network.
  * **Purpose:** Just as a postal service needs a home address to deliver a letter, the internet needs IP addresses to know where to deliver data. They enable communication between different machines, servers, and services across the internet.
  * **Relevance:** Understanding IP addressing is critical for designing distributed systems, cloud infrastructure, and ensuring scalability for services like Netflix or Amazon.

![[01-Introduction to IP Addresses.png]]

**Classification**
IP addresses are categorized in two main ways:

  * **Versions:** IPv4 and IPv6.
  * **Visibility:** Public and Private.

-----
### **2. What is IPv4?**

**Structure and Limitations**

  * **Format:** IPv4 (Internet Protocol Version 4) uses a **32-bit address format**.
  * **Representation:** It is typically written in "dotted decimal" notation (e.g., `192.168.1.1`), consisting of four groups of numbers (octets) ranging from 0 to 255.
  * **Capacity:** It supports approximately **4.3 billion unique addresses**.
  * **Usage:** It remains the backbone of the internet, used widely in traditional networking, web servers, and most current internet devices.

![[02-What is IPv4.png]]

**The Problem**

  * **Exhaustion:** When IPv4 was designed, 4.3 billion addresses seemed sufficient. However, with the explosion of connected devices (phones, laptops, IoT), we are running out of unique addresses.
  * **Challenges:** Aside from limited IPs, IPv4 faces issues with fragmentation and requires additional security protocols to be safe.

-----

### **3. What is IPv6?**

**The Next Generation Solution**

  * **Format:** IPv6 uses a **128-bit address format**, drastically increasing the available address space.
  * **Representation:** It uses hexadecimal notation separated by colons (e.g., `2001:0db8:85a3:0000...`).
  * **Capacity:** It supports **340 undecillion addresses** (essentially infinite—340 trillion trillion trillion), ensuring we never run out again.
  * **Target Use:** It is designed to support the massive scale of IoT devices, mobile networks, and future internet expansion.

![[03-What is IPv6.png]]

**Key Benefits over IPv4**

  * **Built-in Security:** It includes security features like IPSec natively, rather than as an add-on.
  * **Efficiency:** It offers improved routing efficiency and packet handling, leading to faster data processing.

-----

### **4. IPv4 vs. IPv6 – Key Differences**

The following table summarizes the structural and functional differences between the two protocols.

| Feature | IPv4 | IPv6 |
| :--- | :--- | :--- |
| **Address Size** | 32-bit | 128-bit |
| **Format** | Decimal (e.g., 192.168.1.1) | Hexadecimal (e.g., 2001:db8::1) |
| **Address Space** | \~4.3 billion addresses | Virtually unlimited (340 undecillion) |
| **Security** | Relies on additional protocols | Built-in security (IPSec) |
| **Performance** | Limited due to NAT & fragmentation | More efficient routing & handling |
| **Adoption** | Still widely used (legacy/cloud) | Slowly being adopted globally |

-----

### **5. Private vs. Public IPs**

To manage the limited number of IPv4 addresses, the internet uses a "City vs. Home" addressing logic.

![[04-Private vs Public IPs.png]]

**Public IP Addresses**

  * **Definition:** These are globally unique addresses assigned by Internet Service Providers (ISPs).
  * **Role:** They act like your "Street Address," allowing devices to communicate directly over the public internet.
  * **Example:** `192.203.23.45`.

**Private IP Addresses**

  * **Definition:** These are used within local networks (LANs), such as home Wi-Fi, corporate offices, or data centers.
  * **Role:** They act like "Apartment Numbers" inside a building. They are reusable across different networks and **cannot be accessed directly from the internet**.
  * **Common Ranges:**
      * `10.0.0.0` - `10.255.255.255`
      * `172.16.0.0` - `172.31.255.255`
      * `192.168.0.0` - `192.168.255.255`

-----

### **6. Why Do We Need Private IPs?**

If every smart bulb, fridge, and phone had a public IP, we would have exhausted IPv4 years ago. Private IPs solve this through:

![[05-Why do we need Private IPs.png]]

  * **Conservation:** They allow organizations and homes to reuse the same IP ranges internally, saving public IPs for the router/gateway only.
  * **Security:** Since private IPs are not routable over the internet, external attackers cannot directly access internal devices (like a database or a laptop).
  * **Network Address Translation (NAT):** This technology allows multiple devices with private IPs to share a *single* public IP to access the internet.
      * *Example:* In a home network, your laptop (192.168.x.x) and phone (192.168.x.y) both talk to the internet using the router’s one public IP.
  * **Cost Efficiency:** Public IPs often cost money; private IPs are free to use internally.

-----

### **7. The Role of IPs in System Design**

In large-scale system architecture, IP management is foundational for:

![[06-Role of IPs in System Design.png]]

  * **Scalability:** Essential for designing distributed, multi-region, and cloud-based architectures where thousands of instances need to communicate.
  * **Security:** Private IPs allow architects to "hide" servers behind firewalls. VPNs utilize private networking to secure data.
  * **Load Balancing:** Load balancers use IPs to distribute incoming traffic efficiently across multiple servers (e.g., using Round-robin DNS or Anycast IPs).
  * **Cloud Networking:** Platforms like AWS, GCP, and Azure rely heavily on managing Public IPs (for external users) and Private IPs (for internal communication between virtual machines).
  * **Microservices:** Containers and microservices communicate with each other using internal private IPs to reduce latency and exposure.

-----

### **8. Common System Design Interview Questions on IPs**

When preparing for interviews, ensure you can articulate answers to the following:

  * How do IPv4 and IPv6 addresses differ?
  * Why do we need private IPs in system design?
  * How does NAT help in addressing the IPv4 shortage?
  * Explain how a load balancer distributes traffic using IPs.
  * How does DNS resolve IP addresses in a large-scale system?

-----

### **9. Summary & What’s Next**

  * **Recap:** IPv4 and IPv6 are the fundamental protocols of the internet, with IPv6 being the long-term solution for scalability.
  * **Strategy:** The distinction between Public and Private IPs allows us to manage internal security and external connectivity efficiently.
  * **Importance:** Proper IP management is essential for system performance, security, and scaling.
  * **Next Step:** Now that we understand *addresses*, the next session will cover **DNS (Domain Name Systems)**—the system that translates human-readable names (like https://www.google.com/search?q=google.com) into these IP addresses.

-----

**Would you like me to create a comparison table specifically for "Private vs Public IP" use cases in a cloud environment (AWS/Azure)?**
