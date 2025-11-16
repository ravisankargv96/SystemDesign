## 🌐 Understanding IP Addresses in System Design

**IP (Internet Protocol) addresses** are unique numerical labels assigned to devices on a network, enabling communication between machines, servers, and services across the internet.

![[Pasted image 20251115144600.png]]

---
### 1. Versions of IP

There are two primary versions of IP addresses:

| **Feature**        | **IPv4 (Internet Protocol Version 4)**           | **IPv6 (Internet Protocol Version 6)**    |
| ------------------ | ------------------------------------------------ | ----------------------------------------- |
| **Address Size**   | **32-bit**                                       | **128-bit**                               |
| **Address Format** | Dotted decimal (e.g., `192.168.1.1`)             | Hexadecimal (e.g., `2001:0db8:85a3...`)   |
| **Address Space**  | $\sim$**4.3 billion** unique addresses (Limited) | **340 undecillion** (Virtually unlimited) |
| **Security**       | Relies on additional protocols                   | **Built-in security** (IPSec)             |
| **Use Case**       | Traditional networking, web servers              | IoT, mobile networks, future scalability  |

**IPV4**
![[Pasted image 20251115144740.png]]

**IPV6**
![[Pasted image 20251115144659.png]]

---
### 2. Categories of IP

IP addresses are classified into two categories: **Public** and **Private**.

| **Feature**       | **Public IPs**                                                 | **Private IPs**                                              |
| ----------------- | -------------------------------------------------------------- | ------------------------------------------------------------ |
| **Assignment**    | Assigned by ISPs (Internet Service Providers)                  | Used within local networks (LANs, enterprises, homes)        |
| **Accessibility** | **Unique worldwide**; used for communication over the internet | **Not accessible** directly from the internet (Not routable) |
| **Purpose**       | To locate internet-facing services globally                    | To allow devices within a local network to communicate       |
| **Common Ranges** | N/A (Globally unique)                                          | $10.0.0.0 - 10.255.255.255$                                  |
|                   |                                                                | $172.16.0.0 - 172.31.255.255$                                |
|                   |                                                                | $192.168.0.0 - 192.168.255.255$                              |

![[Pasted image 20251115144917.png]]
#### Why Private IPs are Needed:

- **Address Conservation**: They conserve public IPv4 addresses by allowing organizations and homes to reuse the same IP ranges (IPv4 limitation).
- **Enhanced Security**: They isolate the internal system from external threats, as they are not directly reachable from the internet.
- **NAT Enablement**: They enable **Network Address Translation (NAT)**, which allows multiple private devices to share a single public IP address for external communication.

---

### 3. Role of IPs in System Design

![[Pasted image 20251115144957.png]]


IP addressing is fundamental to modern distributed systems:

- **Scalability**: Essential for designing distributed, multi-region, and cloud-based architectures.
- **Security**: Used to enable firewall rules, VPNs, and private networking.
- **Load Balancing**: Utilized for traffic distribution, such as with Round-robin DNS or Anycast IPs.
- **Cloud Networking**: Crucial for managing public, private, and hybrid cloud IP structures (e.g., AWS, GCP, Azure).
- **Microservices**: Internal **private IPs** are used for communication between microservices and containers.

---

**Coming Up Next**: The next topic will explore **How DNS Works** and its critical role in system design.
