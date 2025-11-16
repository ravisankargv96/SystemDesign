Here are **short, structured notes** for the transcript, organized under your provided chapters 👇

---

## 🕒 **00:00 – Where are webpages stored?**

* Once the **server** is set up, users should access webpages via a domain (e.g., `fancytshirts.io`).
* Webpages are made of:

  * **HTML/CSS** → structure & style
  * **JavaScript** → interactivity
* These **static files** (webpages) must be **stored** somewhere.

  * Option 1: On your own **AWS server** (serve via API).
  * Option 2: Use a **Content Delivery Network (CDN)**.

---

## 🕒 **01:03 – CDN vs Backend Server**

### **CDN (Content Delivery Network)**

* Global network of distributed servers (e.g., **Akamai**, **AWS CloudFront**).
* Users connect to the **nearest geographic server** for low latency.

  * Example:

    * Indian users → India server
    * U.S. users → U.S. East or West servers

### **Advantages**

* **Faster page loads** (less latency).
* **Highly available** (redundant global servers).
* **Cheaper** due to shared infrastructure and economies of scale.

### **Disadvantages**

* **Costly** to build/maintain if self-hosted.
* **Static content only** (not suitable for fast-changing data).

✅ **Choice:** Use a **CDN** (e.g., CloudFront, Akamai) for hosting webpages and static assets (images, CSS, JS).

---

## 🕒 **02:46 – Why STATIC content?**

* CDNs are **best for static files** — images, product descriptions, UI elements.
* **Dynamic data** (e.g., inventory, prices, user info) changes frequently → must stay on **backend servers**.
* Example issue:

  * 50 T-shirts in stock.
  * U.S. and India CDNs both show “50 remaining”.
  * 40+11 orders placed → **overselling (51 total)** due to delayed updates.

👉 Keep **dynamic content** on the server (database).
👉 Keep **static content** (images, layout) on the CDN.

---

## 🕒 **03:57 – Datastore: File System**

* To upload & sync static files globally → need a **shared file system**.
* Example flow:

  * You add files → CDN auto-detects changes → distributes globally.

### **Options:**

| Type              | Example                       | Notes                                |
| ----------------- | ----------------------------- | ------------------------------------ |
| **Local**         | Hadoop FS, Ceph (open-source) | Self-managed, complex                |
| **Cloud-managed** | **Amazon S3**                 | Highly durable, consistent, scalable |

✅ **Choice:** Use **Amazon S3** for file storage + **AWS CloudFront** for CDN distribution.

---

## 🕒 **05:12 – How do users find us?**

* Domain example: `fancytshirts.io`.
* Need users’ browsers to point to **your** new CDN/webpages, not Shopify’s.
* This routing is handled by **DNS (Domain Name System)**.

---

## 🕒 **05:56 – DNS Route Resolution**

### **How it works**

1. User types `fancytshirts.io` in browser.
2. Browser → Router → ISP → **DNS Server**.
3. DNS resolves `fancytshirts.io` → IP address (e.g., `192.0.2.15`).
4. Browser caches IP → makes request → webpage served from CDN.

### **Key Concepts**

* **DNS** = Internet’s “phonebook” (domain → IP).
* **Providers**:

  * AWS → Route 53
  * GoDaddy, Cloudflare, etc.
* DNS servers communicate to find unknown domains.

✅ **Setup Example:**

* Domain bought from **GoDaddy**.
* Forward DNS queries → **AWS Route 53**.
* Route 53 returns IP of your **CloudFront CDN** → webpage is rendered.

---

## 🕒 **08:30 – What Database is right?**

### **For startups / small apps:**

* Don’t overthink database choice — pick what you know.
* Both **SQL** and **NoSQL** can work initially.

### **Recommendation:**

* If unsure → **SQL (e.g., PostgreSQL, MySQL)**

  * Mature, reliable, well-documented.
  * Easier for analytics & data queries.
  * Easier to hire engineers familiar with SQL.

### **Evaluation (3 metrics):**

| Metric                 | SQL DB                  | Justification                       |
| ---------------------- | ----------------------- | ----------------------------------- |
| **Fidelity**           | ✅ Meets requirements    | Handles structured data easily      |
| **Simplicity**         | ✅ Simple to learn & use | SQL is widely known                 |
| **Cost-effectiveness** | ⚖️ Depends on usage     | Generally affordable at small scale |

✅ **Conclusion:** Use **SQL database** initially; migrate later if needed.

---

### **🌐 Final Architecture Summary**

| Layer                 | Technology                        | Purpose                         |
| --------------------- | --------------------------------- | ------------------------------- |
| **Frontend (Static)** | CDN (AWS CloudFront)              | Host webpages, images           |
| **File Storage**      | Amazon S3                         | Source for CDN content          |
| **Backend**           | Serverless functions (AWS Lambda) | Handle dynamic data             |
| **Database**          | SQL (e.g., RDS)                   | Store user, product, order data |
| **DNS**               | Route 53                          | Map domain to CDN/backend       |

