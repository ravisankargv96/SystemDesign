## 📓 Lecture Notes: TCP & UDP

This lecture covers the two fundamental communication protocols in networking: TCP and UDP. The focus is on their core differences, strengths, weaknesses, and when to use each in system design.

---
### TCP (Transmission Control Protocol)

TCP is a protocol focused on **reliability and accuracy**.

- **Connection-Oriented:** It must establish a connection between the sender and receiver before any data is sent.    
    - This is done using a **three-way handshake** (SYN, SYN/ACK, ACK) to ensure both sides are ready.
- **Reliable & Ordered:** TCP guarantees that all data packets are delivered, checked for errors, and reassembled in the correct order.
    - **How it works:** The receiver sends acknowledgments (ACKs) for data. If a packet is lost or corrupted, TCP automatically requests the sender to retransmit it.
- **Trade-off:** This process of establishing a connection, checking for errors, and retransmitting packets adds overhead, which makes TCP **slower** than UDP.
- **Summary:** TCP is the backbone for applications where data integrity is critical and no data loss is acceptable.

---

### UDP (User Datagram Protocol)

UDP is a protocol designed for **speed and efficiency**.
- **Connectionless:** It does not establish a connection before sending data. It simply sends packets (datagrams) to the destination.
- **Unreliable:** UDP provides **no guarantees** for data delivery.
    - Packets can be lost in transit, arrive out of order, or be duplicated.
    - There is **no retransmission** of lost packets at the protocol level.
- **Lightweight & Fast:** By skipping the handshake and all reliability checks, UDP has very low overhead and is much faster, resulting in lower latency.
- **Summary:** UDP is ideal for real-time applications where speed is more important than perfect accuracy, and minor data loss is acceptable.

---

### 📊 Key Differences: TCP vs. UDP

|**Feature**|**TCP (Transmission Control Protocol)**|**UDP (User Datagram Protocol)**|
|---|---|---|
|**Reliability**|**Reliable** (guarantees delivery)|**Unreliable** (no guarantee of delivery)|
|**Connection**|**Connection-oriented** (establishes a connection first)|**Connectionless** (sends data without setup)|
|**Speed**|**Slower** (due to error checking & retransmission)|**Faster** (no retransmission overhead)|
|**Ordering**|**Ensures packets arrive in order**|**No guarantee of packet order**|
|**Error Handling**|Built-in error checking & retransmission|Minimal error checking, no retransmission|
|**Overhead**|High (due to handshake, ACKs, sequencing)|Low (minimal protocol overhead)|

---

### 💡 Use Cases

Choosing the right protocol involves a trade-off between **reliability and speed**.

#### When to use TCP (Data Integrity is Critical)

- **Web Browsing:** HTTP and HTTPS    
- **File Transfers:** FTP and SFTP
- **Email:** SMTP, IMAP, POP3
- **Database Communication**
    
#### When to use UDP (Speed is Critical)

- **Video Streaming:** YouTube, Netflix (minor frame loss is better than buffering)
- **Online Gaming:** Multiplayer games (latest update is more important than an old, lost packet)
- **VoIP Calls:** Skype, Zoom, WhatsApp calls
- **DNS Lookups:** Speed is essential for resolving domain names quickly

---
### Key Takeaways

- **TCP is reliable but slower.** Use it when you need every bit of data to arrive correctly and in order (e.g., file transfers, web pages).
- **UDP is fast but unreliable.** Use it for real-time applications where low latency is crucial and you can tolerate some packet loss (e.g., video streaming, online gaming).
- The choice directly impacts the performance and user experience of your application.
- Common interview questions focus on these differences, the three-way handshake, and justifying protocol choices for specific system design scenarios (like gaming or DNS).

**Next Lecture:** HTTP - The Backbone of the Web.