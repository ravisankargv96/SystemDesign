### **Learning Objectives**

* **Topic**: Introduction to Distributed Systems and their business relevance.
* **Focus**: How components are placed and interact in a distributed setup.
* **Example used**: E-commerce website (users can view & buy products).
* **Purpose**: Understand real-world design patterns, tools, and scalability needs.
* **Target audience**: Startups, engineers, and technical managers.
* **Outcomes**:

  * Learn to design distributed systems.
  * Understand design patterns, algorithms, and tools.
  * Improve technical communication for design reviews and interviews.

---

### **Evaluation Metrics**

All system designs are evaluated using **three core metrics**:

1. **Simplicity** – Is the design clear, maintainable, and adaptable?
2. **Fidelity** – Does the design meet all business and technical requirements?
3. **Cost Effectiveness** – Is the design affordable and feasible in implementation?

> Throughout the course, every design decision should be evaluated against these metrics.

---

### **Example: E-commerce App**

* **Scenario**: Friend selling T-shirts wants to move online.
* **Goal**: Simple, complete, and cost-effective solution.

#### **Initial Recommendations**

* Use existing platforms:

  * **Amazon** – not customizable.
  * **Shopify** – good balance of control and integrations (payments, delivery).
* **Lesson**: The architect’s job is to solve business problems, not just create new systems.

  * Prefer existing, proven solutions if they meet needs.

#### **Challenges Identified Later**

4. **Tracking issue** – Can’t see detailed order-to-delivery status on Shopify.
5. **Payment limitation** – International cards not accepted.

#### **Decision Process**

* Check if issues can be fixed within Shopify (support tickets, integrations).
* When existing providers cannot meet requirements → build **custom solutions**.

#### **Transition to Custom System**

* Create **technical wrappers**:

  * Custom **payment page** using gateways like Razorpay, PayPal, Stripe.
  * Custom **delivery tracking page** integrated with order data.
* **Principle**: Extract key functions from existing tools → gain more control, reduce dependency, and meet evolving business needs.

---

### **Basic Design**

#### **High-Level Design Overview**

* Integrate custom components with Shopify:

  * **Payment Page** → Redirect from Shopify → choose payment provider.
  * **Delivery Tracking Page** → Users enter order ID → see delivery status.

#### **Data Requirements**

* Store:

  * Payment success/failure for each order.
  * Delivery state updates.

#### **Client–Server Interaction**

* Achieved through **APIs (Application Programming Interfaces)**:

  * Define **contracts** between client & server.
  * Exchange data in **JSON** format (`order_id`, `status`, etc.).
  * Example:

    * `GET /payment-status` → returns payment info.
    * `GET /delivery-status` → returns delivery progress.

#### **API Functionality**

* Works like a function: takes inputs (parameters), returns outputs (responses).
* Can be written in any backend language (Python, Go, Java).

#### **Deployment**

* Write code locally → deploy to **cloud servers** (manual or via automation).
* Use **CI/CD pipelines** (e.g., GitHub Actions) for continuous integration & deployment.

#### **Core Idea**

* APIs form the backbone of system communication.
* Design focuses on functionality, modularity, and business alignment — not just coding.

