## 📞 How DNS Works: The Internet's Phonebook

The **Domain Name System (DNS)** is one of the fundamental building blocks of the internet, often called the **"phonebook of the internet"**. Its primary function is to **translate human-readable domain names** (like `google.com`) into numerical **IP addresses** (like `74.125.142.147`) that computers use to locate and communicate with each other.

![[Pasted image 20251115145129.png]]

---
### 1. Types of DNS Servers

The DNS system is distributed and relies on a hierarchy of servers to resolve a name:

- **Root Name Servers**: The top-level servers that handle queries for all domain extensions (like `.com`, `.org`, etc.) and direct requests to the appropriate TLD servers.
- **TLD (Top-Level Domain) Name Servers**: Handle specific domain extensions (e.g., the `.com` TLD server) and redirect the query to the authoritative server.
- **Authoritative Name Servers**: The final servers that **store the actual DNS records** (A, CNAME, MX records) mapping the domain name to its IP address.
- **Recursive Resolvers (Local DNS Resolver)**: Servers, typically provided by ISPs, that handle queries on behalf of the user, contact the hierarchy of DNS servers, and cache the results to improve efficiency.

![[Pasted image 20251115145256.png]]

---
### 2. The DNS Resolution Process

The process of translating a domain name into an IP address is a step-by-step lookup:

1. **User Input**: User types a domain name (e.g., `google.com`) into their browser.    
2. **Local Cache Check**: The browser and the Operating System (OS) check their local caches first to see if the IP is already known.
3. **Local Resolver Query**: If not found, a query is sent to the Local DNS Resolver (ISP or configured DNS server).
4. **Root/TLD/Authoritative Lookup**: The Resolver queries the Root DNS servers, which point to the TLD servers, which finally point to the Authoritative DNS server.
5. **IP Address Returned**: The Authoritative DNS server returns the correct IP address to the Resolver.
6. **Caching and Loading**: The IP is cached at the Resolver, OS, and Browser level, and the browser then connects to the IP address to load the website.

![[Pasted image 20251115145354.png]]

---
### 3. DNS Caching and Optimization

DNS caching significantly improves performance and efficiency:

- **Benefits**: Reduces latency and reduces the load on DNS servers.
- **Caching Locations**: Caching occurs at the **Browser cache**, **OS cache** (local machine), and **Recursive Resolver cache** (ISP level).
- **Time-To-Live (TTL)**: This is the expiration timer for a cached record, determining how long the cache is valid before it expires and needs a new lookup. Managing TTL balances speed (longer TTL) and accuracy (shorter TTL).

---
### 4. Role in Large-Scale Systems

In large systems, DNS plays a critical role in reliability, performance, and security:

- **DNS Load Balancing**: DNS can distribute requests across multiple servers worldwide (instead of a single server), which prevents overloading.    
- **Anycast DNS**: Multiple geographically distributed servers handle the DNS resolution request, ensuring the user is served by the nearest, fastest server to reduce latency.
- **DNS Failover Strategies**: If a primary DNS server fails, requests are automatically routed to a secondary backup server to ensure service continuity.
- **CDN Optimization**: DNS directs users to the nearest Content Delivery Network (CDN) node to serve content faster, improving load times.

![[Pasted image 20251115145502.png]]

---
### 5. Security Risks

DNS is a target for cyber attacks:

- **DNS Poisoning/Cache Poisoning**: Attackers can inject fake DNS records, redirecting users to malicious sites instead of the intended IP address.
- **DDoS Attacks**: Attackers can flood DNS servers with requests, making the website unreachable because the domain name cannot be resolved.
- **Mitigation**: Protocols like **DNSSEC** help verify authenticity and prevent tampering of DNS records.

---

![[Pasted image 20251115145528.png]]

The next fundamental concept is the **Client-Server Model**.
