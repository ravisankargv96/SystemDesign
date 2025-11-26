## 📓 Lecture Notes: HTTP - The Backbone of the Web

This lecture covers HTTP (Hypertext Transfer Protocol), the foundational protocol for data communication on the web. It is essential for understanding how web pages are loaded, APIs are called, and content is streamed.

---
### 1. What is HTTP?

- **Stands For:** Hypertext Transfer Protocol.    
- **Role:** It's the foundation of web communication, defining the rules for how clients (like browsers) request resources and how servers respond.
- **Operates Over:** TCP/IP, using **Port 80** for standard HTTP.
- **Key Features:**
    - **Text-based:** Messages are human-readable, making it easier to debug.
    - **Stateless:** Each request is treated as an independent transaction. The server does not remember previous interactions.
    - **Supports Methods:** Uses various methods (like GET, POST) to define the desired action.

---
### 2. How HTTP Works: The Client-Server Model

HTTP follows a request-response cycle between a client and a server.
- **Client:** The entity making the request (e.g., web browser, mobile app).
- **Server:** The entity processing the request and sending a response (e.g., web server, API server).

#### Components of an HTTP Request

1. **Method:** The action to be performed (e.g., `GET`, `POST`).
2. **URL:** The resource being requested.
3. **Headers:** Metadata about the request (e.g., `Content-Type`, authentication tokens, `User-Agent`).
4. **Body (Optional):** The data being sent to the server, typically used with `POST`, `PUT`, or `PATCH` methods.

#### Components of an HTTP Response

1. **Status Code:** A 3-digit number indicating the result of the request (e.g., `200 OK`, `404 Not Found`).
2. **Headers:** Metadata about the response (e.g., `Content-Type`, caching information).
3. **Body (Optional):** The actual content being returned (e.g., HTML, JSON, an image).

---
### 3. The HTTP Request-Response Cycle

1. **Step 1: Client Sends Request:** The browser sends an HTTP request (method, URL, headers, optional body) to the server.    
2. **Step 2: Server Processes Request:** The server receives and parses the request, checks authentication, and retrieves or processes the necessary data (e.g., queries a database).
3. **Step 3: Server Sends Response:** The server generates an HTTP response (status code, headers, optional body) and sends it back to the client.
4. **Step 4: Client Renders Response:** The browser receives the response. If it's HTML, it renders the page. If it's data (like JSON), the application processes it.

---
### 4. The Stateless Nature of HTTP

- **What "Stateless" Means:** The server does not retain any memory or context from previous requests. Each request is treated as completely new and independent.    
- **Challenges:** This makes it difficult to maintain user-specific information, such as login status or shopping cart contents.
- **Solutions for Maintaining State:**
    - **Cookies:** Small pieces of data stored by the browser and sent with every request to identify the user.
    - **Sessions:** The server stores user data and gives the client a unique Session ID (often stored in a cookie). The client sends this ID with each request, allowing the server to look up the user's state.
    - **Tokens (e.g., JWT):** Authentication information is stored in a token, which the client sends in the request headers to verify its identity.

---
### 5. Common HTTP Methods

| **Method** | **Purpose**                                                                  | **Idempotent?***         |
| ---------- | ---------------------------------------------------------------------------- | ------------------------ |
| **GET**    | Retrieve a resource (e.g., load a web page, fetch API data).                 | **Yes**                  |
| **POST**   | Send data to create a new resource (e.g., submit a form, create a new user). | **No**                   |
| **PUT**    | Update an existing resource (replaces the entire resource).                  | **Yes**                  |
| **DELETE** | Remove a resource.                                                           | **Yes**                  |
| **PATCH**  | Partially update a resource (updates only specific fields).                  | **No** (not necessarily) |

***Idempotent:** Means that making the same request multiple times will result in the same state as making it once. (e.g., deleting a resource twice has the same result as deleting it once).

---
### 6. HTTP Status Codes

Status codes are grouped into categories:

- **1xx (Informational):** Request received, continuing process.    

- **2xx (Success):** The request was successfully processed.
    - **200 OK:** Standard successful response.
    - **201 Created:** A new resource was successfully created.

- **3xx (Redirection):** Further action is needed to complete the request.    
    - **301 Moved Permanently:** The resource has a new, permanent URL.
    - **304 Not Modified:** The resource has not changed since the last request (used for caching).
        
- **4xx (Client Errors):** The request contains a mistake or cannot be fulfilled.
    - **400 Bad Request:** Incorrect request format.
    - **401 Unauthorized:** Authentication is required.
    - **403 Forbidden:** The client does not have permission to access the resource.
    - **404 Not Found:** The requested resource doesn't exist.
        
- **5xx (Server Errors):** The server failed to fulfill a valid request.
    - **500 Internal Server Error:** An unexpected server failure.
    - **503 Service Unavailable:** The server is overloaded or down for maintenance.

---
### 7. What About HTTPS?

- **HTTPS:** Stands for **Hypertext Transfer Protocol Secure**.    
- **How it Works:** It is the secure version of HTTP that uses **SSL/TLS encryption** to protect data.

- **Key Benefits:**
    
    1. **Confidentiality:** Encrypts data to prevent eavesdropping.        
    2. **Integrity:** Ensures data is not altered during transmission.
    3. **Authentication:** Verifies the website's identity, protecting against phishing.
        
- **Port:** Uses **Port 443** (instead of HTTP's Port 80).
- **Importance:** Essential for any site handling sensitive data (e.g., banking, e-commerce, logins).

---
### 8. Summary & Key Takeaways

- HTTP is the stateless, text-based foundation of all web communication.    
- It operates on a **request-response** model.
- Because it's **stateless**, mechanisms like **cookies, sessions, and tokens** are required to manage user state.
- **Methods** (GET, POST, etc.) define the _action_, while **Status Codes** (200, 404, etc.) indicate the _response_.
- **HTTPS** is the secure, encrypted version that is standard for all modern web applications.

**Next Lecture:** REST & RESTfulness - API Design Principles.