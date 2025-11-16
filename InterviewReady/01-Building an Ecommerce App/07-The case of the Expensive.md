Here’s a **concise set of short notes** under each chapter heading for quick reading and revision — based on your provided transcript:

---

## 🧾 Short Notes per Chapter

### **00:00 - A Costly Mistake**

* Founder notices Redis bills are ~$2,000/month — unusual for a small-scale setup.
* Indicates **misuse of caching**: using large Redis instances unnecessarily.
* Engineers storing **heavy objects** (full T-shirt metadata) instead of **lightweight references** (IDs).
* Queries to fetch “most popular T-shirts” run **directly on the database**, not cache — defeating cache purpose.
* Caching should reduce database hits and memory usage.

**Key takeaway:**
Optimize what and how data is cached — store IDs, not full objects. Cache exists to reduce DB load and cost, not increase them.

---

### **01:44 - Cache Setup**

* Problem: Engineers caching incorrectly due to fear of **data inconsistency**.
* Heavy caching of user-level data (recently viewed shirts).
* Fix: Use **light caches** — store only identifiers; metadata can be fetched separately.
* Example approach:

  * Cache user’s T-shirt IDs (A, B, C, D).
  * Fetch detailed info from a separate “T-shirt info cache” or DB as needed.
* Reduces duplication — multiple users referencing same T-shirt won’t duplicate heavy objects.

**Key takeaway:**
Design cache layers efficiently — separate user-specific lists from item data caches.

---

### **04:01 - Cache Consistency**

* Engineers avoid cache due to **stale data fears** (data in DB more recent).
* Solution: **Trade-off between freshness and performance.**

  * Perfect freshness not always required (e.g., top 10 T-shirts can be slightly outdated).
  * Use **cache expiry** (e.g., 1–6 hours).
* Types of cache consistency:

  * **Write-through:** Update DB first, then cache. Ensures strong consistency.
  * **Write-behind (write-back):** Update cache first; DB later when evicted. Better performance, riskier on crash.
* Redis supports both easily.
* Use write-through for critical data (e.g., payments), write-behind for tolerant data (e.g., views).

**Key takeaway:**
Consistency depends on use-case — choose a write policy balancing **speed, reliability, and cost.**

---

### **09:56 - Cache Policies**

* Discusses **cache access and eviction policies**.
* Problem: Growing cache size with more users.

  * Fix: Cache only **active users**.
* Define “active”:

  * **Frequently active** (most logins).
  * **Recently active** (last login time).
* Eviction strategies:

  * **LRU (Least Recently Used):** Remove least recently accessed entries.
  * **LFU (Least Frequently Used):** Remove least accessed overall.
* Trade-off:

  * LRU favors **recency** (good for current trends).
  * LFU favors **loyalty** (good for long-term engagement).
* These form part of **eviction policy**, which maintains memory limits and performance.

**Key takeaway:**
Use eviction policies (LRU/LFU) to manage limited cache space efficiently — ensure hot/recent data stays accessible.

