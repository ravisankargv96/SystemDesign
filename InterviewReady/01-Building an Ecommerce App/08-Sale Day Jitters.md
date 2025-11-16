Here are **chapter-wise short notes** generated from your file **“08-Sale Day Jitters.md”** — clear, crisp, and ready for revision 👇

---

### 🕒 00:00 – Traffic Estimation

* Flash sale expected to create heavy, short-term spikes.
* Estimate load → talk to founder (followers, email users, ad impressions).
* Assume ~10× daily sales; plan accordingly.
* Decide capacity increase (3×–10×) balancing **cost vs performance**.
* Remember → even big companies mis-predict traffic.

---

### ⚙️ 02:26 – Scaling Strategy

* **Pre-emptive scaling:** add more servers before sale.
* **Monitor metrics:** latency, memory, CPU → add servers dynamically.
* **Analyze access patterns:**

  * Cache common reads (e.g., product list).
  * Use CDN to serve static + semi-static data.
* **Three-step approach:**

  1. Estimate load.
  2. Pre-scale infra.
  3. Cache & optimize critical paths.
* **Load testing:** find how many requests one server can handle within SLA.

---

### 💥 04:57 – Sale Day!

* Unexpected 1 million concurrent users → system crash.
* Queues overflow, requests retry → worse overload.
* Flash sale fails → logs analyzed to find abnormal traffic.

---

### 🔍 07:16 – Finding the Root Cause

* Identify bot traffic – multiple identical user IDs, rapid fire requests.
* It’s a **DDoS attack** (distributed denial of service).
* Must protect system from malicious actors before retrying the sale.

---

### 🔒 08:27 – DDOS Prevention

* Use **firewalls / WAFs** (Cloudflare / AWS WAF).
* Two layers:

  1. **CDN level** – block bots from fetching pages.
  2. **Server gateway** – inspect & filter incoming requests.
* **Graceful degradation:**

  * Prioritize critical requests (payments, orders).
  * Deprioritize or reject less important ones.
* **Short-circuiting:** fail early instead of overloading downstream.
* **Back-pressure:** downstream drops new requests to recover.
* Systems recover faster & remain partially functional.

---

### 🚧 15:32 – Head of Line Blocking

* FIFO queues → one slow request blocks all others.
* **Solutions:**

  * **Parallelism:** multiple queues / servers.
  * **Concurrency:** threads share CPU → others progress while one waits.
  * **Better protocols:** e.g., gRPC allows out-of-order handling.
* Outcome → reduced latency & smoother throughput.

---

### 🛍️ 18:18 – Another Sale!

* Sale retry → success after applying fixes:

  * WAF + CDN protection.
  * Graceful degradation & short-circuit logic.
  * Concurrency + gRPC to remove head-of-line blocking.
  * Proper scaling & caching.
* System stable → team & founder happy.

---

### 🚦 19:08 – Rate Limiting

* Goal → serve some users well vs none at all.
* Drop excess requests when capacity is full.
* **Token Bucket Algorithm:**

  * Maintain a fixed number of “tokens.”
  * Each processed request consumes a token; replenished as requests finish.
  * Ensures max N parallel requests.
* **Leaky Bucket Algorithm:**

  * Requests allowed at a constant rate (time-based).
  * Useful for steady flow, but slower for bursts.
* Rate limiting typically implemented per server or distributed via cache.


