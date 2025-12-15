### **1. Introduction to DNS**

**Concept Overview**
* **Definition:** DNS (Domain Name System) is often referred to as the "phonebook of the internet."
* **Function:** It translates human-readable domain names (like `google.com`) into machine-readable IP addresses (like `142.241.90.78`).
* **Analogy:** Just as you look up a contact's name in your phone to find their number without memorizing it, DNS allows computers to find servers without users needing to memorize complex IP strings.

![[01-Introduction to DNS.png]]

**Why is DNS Important?**
* **Usability:** It prevents users from needing to memorize long strings of numbers for every website they visit.
* **Scalability:** It organizes domain names into a structured, distributed system, allowing the internet to scale efficiently to billions of devices.

---

### **2. Types of DNS Servers**

The DNS system relies on a hierarchy of different servers to resolve a request.

![[02-Types of DNS Servers.png]]

* **Root Name Servers:**
    * These are the top-level servers in the hierarchy.
    * They do not store the actual domain records (like the specific IP for Google).
    * Instead, they direct requests to the appropriate Top-Level Domain (TLD) server based on the extension (e.g., directing a `.com` request to the `.com` TLD server).

* **TLD (Top-Level Domain) Name Servers:**
    * These servers manage specific domain extensions, such as `.com`, `.org`, or `.net`.
    * When a request reaches a TLD server, it redirects the query to the specific Authoritative Name Server that holds the records for that domain.

* **Authoritative Name Servers:**
    * These are the final destination in the lookup chain.
    * They store the actual DNS records (such as A records, CNAME records, or MX records) and possess the mapping of the domain name to its specific IP address.
    * They return the correct IP address to the requester.

* **Recursive Resolvers:**
    * These servers sit between the user and the rest of the DNS hierarchy, typically set up by Internet Service Providers (ISPs).
    * They handle the heavy lifting of queries on behalf of the user, contacting the Root, TLD, and Authoritative servers as needed.
    * Crucially, they also cache results to speed up future requests for the same domain.

---

### **3. DNS Caching and Performance Optimization**

**Why Caching Matters**
* **Reduces Latency:** Instead of performing a full lookup through the entire server hierarchy every time, cached records allow devices to resolve names almost instantly.
* **Reduces Load:** Fewer queries traveling to the Root and TLD servers means less traffic congestion and better overall internet performance.

**Where Caching Occurs**
* **Browser Cache:** The first place checked. If you have visited a site recently, your browser stores the IP locally.
* **Operating System (OS) Cache:** If the browser doesn't have it, the computer's OS also keeps a local cache of recent DNS records.
* **Recursive Resolver Cache:** The ISP's server keeps a cache of resolved domains for all its users.

**Time-To-Live (TTL)**
* **Definition:** An expiration timer attached to every DNS record.
* **Function:** It determines how long a record can be stored in the cache before it must be discarded and refreshed.
* **Trade-off:**
    * **Short TTL:** Ensures data is up-to-date (good for changing IPs) but increases load on servers.
    * **Long TTL:** Improves speed and reduces server load but delays updates (users might see old data after a change).

---

### **4. The Domain Name Resolution Process**

![[03-Domain Name Resolution Process.png]]

This is the step-by-step journey of a DNS query when you type `google.com` into your browser:

1.  **User Request:** You type the domain name and hit enter.
2.  **Browser Cache Check:** The browser checks if it already knows the IP. If yes, the site loads immediately.
3.  **OS Cache Check:** If not in the browser, the request moves to the Operating System's local cache.
4.  **Query to Local DNS Resolver:** If missing from the OS, the query is sent to the ISP's Recursive Resolver.
5.  **Root Server Lookup:** If the Resolver doesn't have it cached, it asks a Root Server (e.g., "Where is `.com`?").
6.  **TLD Server Lookup:** The Root Server points to the `.com` TLD Server, which then points to the specific Authoritative Server for Google.
7.  **Authoritative Server Lookup:** The Authoritative Server looks up its records and finds the exact IP address for `google.com`.
8.  **Response & Caching:** The IP address is sent back to the Resolver, then to the OS, and finally to the Browser. It is cached at each step for future use.
9.  **Website Loads:** The browser connects to the IP address and retrieves the webpage.

---

### **5. Importance of DNS in Large-Scale Systems**

In complex distributed systems, DNS is used for more than just simple lookups.

![[04-Importance of DNS in LargeScale System.png]]

* **Load Balancing:** DNS can distribute incoming traffic across multiple servers (e.g., using Round-Robin DNS). Instead of overloading one server, DNS rotates the IP addresses returned to users.
* **Anycast DNS:** This allows multiple geographically distributed servers to share the same IP address. The network routes the user's request to the physically nearest server, significantly reducing latency.
* **Failover Strategies:** Systems use Primary and Secondary DNS servers. If the primary server fails or becomes unhealthy, DNS automatically routes traffic to the backup secondary server to prevent downtime.
* **Content Delivery Networks (CDNs):** When accessing a global site (like Netflix), DNS directs the user to the nearest CDN edge server (e.g., a user in India is directed to a Mumbai server rather than New York) to speed up content delivery.

---

### **6. DNS Security Risks**

Because DNS is central to internet traffic, it is a frequent target for attacks.

* **DNS Spoofing (Poisoning):** Attackers inject fake DNS records into a cache. When a user types a legitimate domain (like a bank's URL), the poisoned cache redirects them to a malicious fraudulent site instead.
* **DDoS Attacks:** Attackers flood DNS servers with a massive volume of requests, overwhelming them and making websites unreachable because users cannot resolve the domain names.
* **Mitigation:** Protocols like **DNSSEC** (Domain Name System Security Extensions) add cryptographic signatures to DNS records to verify authenticity and prevent tampering.

---

### **7. Summary & Takeaways**

![[05-Summary & Takeaways.png]]

* **Foundation:** DNS is the critical infrastructure that makes the internet usable by translating names to IPs.
* **Performance:** Caching at the browser, OS, and ISP levels is essential for a fast browsing experience.
* **System Design:** For large-scale applications, DNS is a tool for load balancing, geographic routing (Anycast), and high availability (Failover).
* **Security:** Awareness of threats like Cache Poisoning and implementing security measures is vital for protecting users and infrastructure.

***

**Would you like me to generate a similar set of notes for the "Client-Server Model" mentioned as the next topic?**