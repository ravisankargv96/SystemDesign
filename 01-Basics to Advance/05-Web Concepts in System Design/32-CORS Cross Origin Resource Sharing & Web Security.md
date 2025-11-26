Here are the comprehensive notes on CORS (Cross-Origin Resource Sharing) and Web Security based on the provided lecture materials.

### **Introduction: The Problem & Solution**

The Problem: Same-Origin Policy (SOP)

Modern browsers enforce the Same-Origin Policy (SOP), a security measure that restricts a web page from making requests to a different domain than the one that served the web page.

- _Example:_ A frontend hosted on `app.com` cannot, by default, request data from an API on `api.com`.
    

The Solution: CORS

CORS (Cross-Origin Resource Sharing) is a mechanism that allows servers to explicitly permit browsers to load resources from a different origin. It provides a controlled way to bypass SOP while maintaining security boundaries.

---

### **How CORS Works**

CORS is server-driven. When a browser makes a cross-origin request, the server responds with specific headers to grant or deny access.

**1. Types of Requests**

- **Simple Requests:** Standard requests like `GET` or `POST` without custom headers. These do not trigger a preflight check.
    
- **Preflight Requests:** Required for complex operations (e.g., `PUT`, `DELETE`) or requests with custom headers. The browser first sends an `OPTIONS` request to check permissions before sending the actual request.
    

**2. Key CORS Headers**

- `Access-Control-Allow-Origin`: Defines which domains can access the resource (e.g., `https://example.com`).
    
- `Access-Control-Allow-Methods`: Specifies allowed HTTP methods (e.g., `GET`, `POST`).
    
- `Access-Control-Allow-Headers`: Lists permitted custom headers (e.g., `Authorization`).
    

---

### **Security Risks & Best Practices**

Improper CORS configuration can lead to severe security vulnerabilities.

**Common Risks**

- **Overly Permissive Origins:** Setting `Access-Control-Allow-Origin: *` allows _any_ website to access your API, potentially exposing sensitive data.
    
- **Allowing Credentials with Wildcards:** Setting `Access-Control-Allow-Credentials: true` alongside a wildcard origin (`*`) is dangerous and often blocked by browsers due to security risks.
    

**Mitigation Strategies**

- **Whitelist Origins:** Always specify trusted domains (e.g., `https://app.com`) instead of using `*`.
    
- **Granular Policies:** Apply different CORS policies for different API endpoints based on their specific security needs.
    
- **Centralize Handling:** Use API Gateways or reverse proxies to enforce uniform CORS policies across services.
    

---

### **Alternatives to CORS**

Sometimes it is more efficient to bypass browser CORS restrictions entirely using backend infrastructure.

- **Reverse Proxy:** Tools like **Nginx** or **Apache** forward client requests to the backend server. To the browser, the request appears to be coming from the same origin, bypassing CORS checks.
    
- **API Gateways:** Services like **AWS API Gateway** allow centralized control of CORS policies. This removes the need to configure CORS individually for every microservice.
    

**Benefits:**

- Enhances security by hiding internal API structures.
    
- Improves performance by reducing unnecessary preflight requests.
    

---

### **Common Interview Questions**

- What is the Same-Origin Policy, and why does it exist?
    
- How does CORS enable cross-origin requests?
    
- What is a preflight request, and when is it required?
    
- What are common security risks associated with CORS (e.g., wildcard origins)?
    
- How do API Gateways and Reverse Proxies help with CORS?
    

---

### **Section Summary: Web Concepts in System Design**

This section covered the foundational principles of web applications:

- **Web Sessions:** Managing state in a stateless HTTP environment using Cookies, Sessions, and JWTs.
    
- **Serialization:** Formatting data for storage and exchange (JSON vs. XML vs. Protobuf) and their trade-offs regarding efficiency and readability.
    
- **CORS & Security:** Understanding the Same-Origin Policy, configuring secure cross-origin access, and mitigating risks through proper headers and infrastructure.
    

**Next Step:** The next section will focus on **Scalability in System Design**.