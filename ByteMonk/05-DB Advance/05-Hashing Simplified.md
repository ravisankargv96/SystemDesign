# **System Design: Hashing & Load Balancing - Short Notes**  

## **1. What is Hashing?**  
- **Hashing** converts arbitrary data (usernames, IPs, files) into a **fixed-size integer value**.  
- Used in **load balancing, caching, distributed systems, cryptography**.  

## **2. Load Balancing & Server Selection Strategies**  
A **load balancer** distributes client requests across multiple servers. Common strategies:  

### **a) Random Selection**  
- Picks a server randomly.  
❌ **Problem:** Uneven distribution, cache inefficiency.  

### **b) Round Robin**  
- Cycles through servers in order (A → B → C → A → ...).  
❌ **Problem:** Cache misses if the same request goes to different servers each time.  

### **c) Hashing-Based Routing**  
- **Solution:** Use a **hash function** to map each client request to a **fixed server**.  
- Ensures **same client → same server**, maximizing **cache hits**.  

---
## **3. How Hashing Works in Load Balancing?**  
1. **Hash the client identifier** (e.g., client name, IP) → `hash("C1") = 11`.  
2. **Apply modulo operation** to determine the server:  
   - `server_index = hash_value % number_of_servers`.  
   - Example:  
     - `11 % 3 = 2` → Server C.  
     - `12 % 3 = 0` → Server A.  
     - `13 % 3 = 1` → Server B.  

✅ **Benefits:**  
- **Cache efficiency** (same request → same server).  
- **Even distribution** (if hash function is good).  

❌ **Problem: Adding/Removing Servers Breaks Hashing**  
- If a new server is added (`mod 4` instead of `mod 3`), most requests get remapped → **cache misses**.  
- **Solution:** **Consistent Hashing** (avoids full rehashing).  

---
## **4. Properties of a Good Hash Function**  
✔ **Deterministic** – Same input → same output.  
✔ **Uniform Distribution** – Avoids "hotspots" (one server overloaded).  
✔ **Fast Computation** – Low latency for real-time systems.  

### **Common Hash Functions**  
- **MD5, SHA-1, SHA-256** (for general-purpose hashing).  
- **Bcrypt** (for password hashing).  

---
## **5. Key Takeaways**  
✅ **Hashing ensures consistent routing** → better caching.  
✅ **Modulo-based hashing** works but fails when servers are added/removed.  
✅ **Consistent hashing** solves the scaling problem (see next video).  

---
