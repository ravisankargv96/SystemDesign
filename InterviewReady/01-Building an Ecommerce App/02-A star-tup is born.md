## **On-premise, or Cloud?**

### **Key Decision:**

Whether to **host code on your own computer (on-premise)** or **rent compute capacity from a cloud provider** (AWS, GCP, Azure).

### **Comparison:**

| Aspect          | On-Premise (Own Computer)                                | Cloud (Rented Compute)                              |
| --------------- | -------------------------------------------------------- | --------------------------------------------------- |
| **Ownership**   | Fully owned by you                                       | Rented on-demand                                    |
| **Cost Model**  | Fixed (hardware already owned)                           | Pay-as-you-go (per compute usage)                   |
| **Reliability** | Low — risk of hardware failure, outages, inaccessibility | High — providers can auto-replace crashed instances |
| **Maintenance** | You handle OS updates, power, uptime                     | Provider handles infra management                   |
| **Scalability** | Manual, limited to your machine                          | Scales automatically as needed                      |

### **Summary:**

* **Cloud** solutions are **more reliable and manageable**.
* For **professional and consistent services**, cloud hosting is preferred over local setups.

---

## **Cost-Benefit Analysis**

System design evaluated using **three key metrics**:

1. **Simplicity** → Higher when using managed cloud instances (provider handles infra, OS, updates).
2. **Fidelity** → Equal for both (both can meet requirements).
3. **Cost-Effectiveness** → Managed cloud cheaper in small-scale cases since development & maintenance costs are reduced.

### **Conclusion:**

Manual (on-prem) hosting is **rejected** for being complex and costly to maintain.
**Managed cloud instances** chosen for simplicity and cost-effectiveness.

---

## **Server or Serverless?**

After choosing the cloud, there are **two approaches**:

### **1. Server-based Cloud (Managed Instance)**

* You control a **virtual server**.
* Responsibilities: deploy code, restart on crash, handle scaling manually.
* Easier than on-prem but still needs some management.

### **2. Serverless Cloud (Fully Managed Execution)**

* Just **upload code**, provider handles execution.
* You don’t manage OS, server type, or deployment.
* Example: **AWS Lambda**.
* Focus entirely on writing business logic, not infrastructure.

---

## **Cost-Benefit Analysis**

### **Comparison: Server vs Serverless**

| Criteria          | Server                              | Serverless                                    |
| ----------------- | ----------------------------------- | --------------------------------------------- |
| **Ease of Setup** | Moderate                            | Very easy                                     |
| **Scaling**       | Manual / semi-automatic             | Fully automatic                               |
| **Maintenance**   | You manage uptime & restarts        | Provider-managed                              |
| **Cost**          | Fixed or reserved                   | Pay per request                               |
| **Performance**   | Consistent                          | Slight latency during scale-up (“cold start”) |
| **Efficiency**    | Can handle more requests per dollar | May cost more per request at scale            |

### **Serverless Drawbacks:**

4. **Efficiency** – Slightly higher cost per request.
5. **Responsiveness** – Small delays (cold starts) when traffic spikes suddenly.

### **Decision:**

* For **small-scale or low-volume systems**, these drawbacks are negligible.
* **Chosen solution:** **Serverless architecture** (e.g., AWS Lambda).
* Will revisit managed servers when scaling becomes significant.

---

✅ **Final Choice Summary:**

* **Hosting:** Cloud (not on-premise).
* **Deployment Type:** Serverless (for simplicity, scalability, and low maintenance).
* **Reason:** Small-scale business → prioritize ease & reliability over raw efficiency.
