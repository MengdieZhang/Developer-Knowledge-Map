# Network Security and Computer Fundamentals Q&A

---

## Computer Fundamentals

### 1. Difference Between Process and Thread  
- **Process:** An independent program with its own memory space.  
- **Thread:** The smallest unit of execution within a process sharing the same memory.  
- Threads run concurrently sharing resources; processes are isolated.

---

### 2. TCP Three-Way Handshake and Four-Way Handshake; Why These Numbers?  
- **Three-Way Handshake (Connection Establishment):**  
  1. Client sends SYN to server.  
  2. Server replies with SYN-ACK.  
  3. Client sends ACK.  
- **Purpose:** To synchronize sequence numbers and establish a reliable connection.

- **Four-Way Handshake (Connection Termination):**  
  1. Client sends FIN.  
  2. Server sends ACK.  
  3. Server sends FIN.  
  4. Client sends ACK.  
- **Purpose:** Graceful close allowing each side to close independently.

---

### 3. Differences Between TCP and UDP  
| TCP | UDP |
| --- | --- |
| Connection-oriented, reliable | Connectionless, unreliable |
| Guarantees delivery, ordering | No guarantee of delivery or order |
| Slower due to overhead | Faster, lightweight |
| Uses three-way handshake | No handshake |

---

## Network Communication & Security

### 4. Explain the Whole Process from Entering a URL to Page Display  
- DNS resolution → TCP handshake → HTTP request sent → Server processes request → Response returned → Browser renders HTML, CSS, JS → Page displayed.

---

### 5. What Is Cross-Origin? Why Does It Occur? How to Solve It? What Is JSONP?  
- **Cross-origin:** Browser security restricts scripts from different origins interacting.  
- **Reason:** Same-Origin Policy protects against malicious scripts.  
- **Solutions:** CORS headers, JSONP, proxy servers.  
- **JSONP:** Uses \<script> tag to load cross-origin JSON wrapped in a callback (only supports GET).

---

### 6. HTTP Versions and Their Improvements  
- HTTP/1.0 → HTTP/1.1: Persistent connections, chunked transfer encoding, better caching.  
- HTTP/1.1 → HTTP/2: Multiplexing, header compression, binary protocol, server push.  
- HTTP/2 → HTTP/3: Uses QUIC (UDP-based), faster connection setup, better loss recovery.

---

### 7. What Is HTTPS? Why Is It Secure?  
- HTTPS = HTTP + TLS/SSL encryption.  
- Uses certificates to authenticate server, encrypts data to prevent eavesdropping and tampering.

---

### 8. Common HTTP Status Codes  
- 200 OK, 301 Moved Permanently, 302 Found, 304 Not Modified, 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 500 Internal Server Error, 503 Service Unavailable.

---

### 9. HTTP Methods  
- GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS, TRACE.

---

### 10. Differences Between GET and POST  
| GET | POST |
| --- | --- |
| Data in URL (query string) | Data in request body |
| Limited data size | No practical size limit |
| Cacheable | Not cached |
| Used for retrieving data | Used for creating/updating data |

---

### 11. Explain HTTP Caching Mechanisms  
- Browser cache with validation via ETag, Last-Modified.  
- Cache-Control headers control freshness and expiration.  
- Strong vs weak validation.

---

### 12. What Is CDN? How Does It Work?  
- Content Delivery Network caches content on servers near users to reduce latency and server load.

---

### 13. Explain the 304 Not Modified Conditional Cache Process  
- Browser sends conditional request with If-None-Match or If-Modified-Since headers.  
- Server responds with 304 if resource is unchanged so browser uses cached copy.

---

### 14. Types of Browser Storage and Their Differences: localStorage, sessionStorage, cookies, sessions  
| Storage Type | Lifetime | Scope | Size Limit | Sent with Request? |
| --- | --- | --- | --- | --- |
| localStorage | Persistent | Per origin | 5-10MB | No |
| sessionStorage | Tab lifetime | Per tab | ~5MB | No |
| Cookies | Depends on expiry | Per origin | ~4KB | Yes |
| Session (server-side) | Server session | Server | Depends | N/A |

---

### 15. Common Network Attacks and Defenses  
- Attacks: DDoS, MITM, SQL Injection, XSS, CSRF.  
- Defenses: Firewalls, input validation, HTTPS, CORS, token-based authentication, rate limiting.

---

### 16. How Does HTTPS Ensure Security?  
- Encryption with symmetric keys negotiated via asymmetric cryptography.  
- Certificates verify server identity.  
- Integrity checks prevent tampering.

