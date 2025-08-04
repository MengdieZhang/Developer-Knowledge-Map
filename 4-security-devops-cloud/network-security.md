# Network Security and Computer Fundamentals Q&A

---

## Computer Fundamentals

### 1. Difference Between Process and Thread  
- **Process:** An independent program with its own memory space.  
- **Thread:** The smallest unit of execution within a process sharing the same memory.  
- Threads run concurrently sharing resources; processes are isolated.

---

### 2. TCP Three-Way Handshake and Four-Way Handshake; Why These Numbers?  
- HTTPS Handshake Process
1. Client sends `ClientHello`.
2. Server responds with `ServerHello` and certificate.
3. Client verifies certificate and sends pre-master key.
4. Both compute session key.
5. Encrypted communication starts.
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


#### 17. Describe the process from entering a URL to seeing a web page.

1. DNS resolution: Convert domain to IP address.
2. TCP handshake: Establish connection (3-way handshake).
3. TLS handshake (if HTTPS): Negotiate encryption.
4. HTTP request is sent.
5. Server processes and returns a response.
6. Browser parses and renders the page.

#### 18. Differences between WebSocket and HTTP

* HTTP: request-response, one-way.
* WebSocket: full-duplex, real-time communication.


#### 19. Why use CDN for static resources?

* Faster loading
* Reduced server load
* Improved reliability

#### 20. DNS Hijacking

* Intercepting or modifying DNS responses to redirect users.

#### 21. HTTP Message Structure

**Request:** `GET /path HTTP/1.1` + headers + body
**Response:** `HTTP/1.1 200 OK` + headers + body

#### 22. Why HTTPS is Secure

* Encryption
* Server identity verification
* Integrity protection

#### 23. Axios Principle

* Promise-based HTTP client using `XMLHttpRequest`
* Supports interceptors, auto JSON, cancellation

#### 24. HTTP/3 Overview

* Based on QUIC over UDP
* Built-in encryption (TLS 1.3)
* Multiplexing without TCP head-of-line blocking

#### 25. Handling Cookies in Cross-Origin

* Use `withCredentials: true`
* Server must allow credentials and set correct headers

#### 26. HTTP/3 Reliability on UDP

* QUIC handles packet loss, order, retransmission, and ACKs.

#### 27. WebSocket Connection Process

* Starts as HTTP handshake with `Upgrade: websocket` header
* Server responds with `101 Switching Protocols`
* Switches to full-duplex WebSocket

#### 28. HTTPS and MITM Protection

* TLS encrypts data
* Valid certificates from trusted CAs
* Prevents tampering

#### 27. WebSocket Handshake

* Initial HTTP upgrade request and response before WebSocket is established

#### 28. Secure Cookies over HTTPS

```http
Set-Cookie: name=value; Secure; SameSite=None
```

#### 29. HTTP Versions Comparison

| Feature      | HTTP/1.0 | HTTP/1.1 | HTTP/2 |
| ------------ | -------- | -------- | ------ |
| Persistent   | No       | Yes      | Yes    |
| Multiplexing | No       | No       | Yes    |
| Compression  | No       | No       | Yes    |
| Binary       | No       | No       | Yes    |

#### 30. DNS Prefetching

```html
<link rel="dns-prefetch" href="//example.com">
```

#### 31. Application Layer Protocols

* HTTP, HTTPS, FTP, SMTP, IMAP, POP3, DNS, WebSocket, MQTT, SSH, Telnet

#### 32. TCP Packet Loss Detection

* Retransmission timeouts
* Duplicate ACKs
* Selective ACKs (SACK)

#### 33. TCP and HTTP Relationship

* HTTP uses TCP to send/receive data reliably

#### 34. Browser Cache Types

* Memory cache
* Disk cache
* Service Worker cache
* Storage APIs: localStorage, sessionStorage, IndexedDB

#### 35. Common Cache-Control Values

* `no-cache`
* `no-store`
* `max-age=...`
* `public`, `private`
* `must-revalidate`

#### 36. TCP/IP Protocol Overview

* 4 layers: Application, Transport, Internet, Link
* IP handles addressing; TCP ensures reliability

#### 37. 304 Process

* Client sends `If-Modified-Since` or `If-None-Match`
* Server responds with `304 Not Modified` if content unchanged
* Browser uses cached version


