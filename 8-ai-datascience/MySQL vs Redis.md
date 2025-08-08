### 1. MySQL VS Redis
- Redis is a high-performance in-memory key-value store mainly used for caching, distributed locks, and real-time data scenarios. It features fast reads/writes, supports multiple data structures, offers persistence but with weaker consistency guarantees.
- MySQL is a relational database supporting complex transactions and SQL queries, suitable for structured data and long-term storage.
They are often used together: Redis alleviates MySQL load, enabling high concurrency and low latency access.

#### Redis vs MySQL Comparison

##### Core Differences

| Feature       | MySQL                                      | Redis                                      |
|---------------|--------------------------------------------|--------------------------------------------|
| Type          | Relational Database (RDBMS)                | In-memory Key-Value Store (NoSQL)           |
| Data Model    | Tables (structured schema + rows)          | Key-Value (supports lists, sets, hashes)   |
| Storage       | Disk-based (with memory caching)            | Memory-based with optional persistence      |
| Main Usage    | Persistent data storage, transactional processing | Caching, high-performance data access, message queue, distributed locks |
| Query Language| SQL                                         | Custom commands (`GET`, `SET`, `HGET`, etc.)|

##### Performance Comparison (QPS)

| Aspect       | MySQL                    | Redis                      |
|--------------|--------------------------|----------------------------|
| Latency      | Milliseconds (ms)        | Microseconds (μs)          |
| Throughput   | Thousands to tens of thousands per second | Hundreds of thousands+ per second |
| Concurrency  | Depends on connection pools and threads   | Single-threaded with I/O multiplexing  |

**Conclusion**: Redis offers much higher performance but cannot replace MySQL's data integrity and complex query capabilities.

##### Data Consistency & Persistence

| Aspect         | MySQL                      | Redis                                        |
|----------------|----------------------------|----------------------------------------------|
| Persistence    | Default disk persistence   | RDB snapshots or AOF (append-only file) options |
| Consistency    | ACID compliant, supports transactions | Eventual consistency by default, transactions supported but no rollback |
| Crash Recovery | Redo/undo logs enable recovery | Possible data loss of last operations depending on config |

##### Use Case Comparison

| Scenario                     | Suitable for Redis                   | Suitable for MySQL                 |
|------------------------------|-------------------------------------|----------------------------------|
| Caching hot data (e.g. user profiles) | ✅                               | ❌ (slower)                      |
| Leaderboards, counters         | ✅ (fast ZSet, INCR commands)       | ❌ (heavy locking overhead)      |
| E-commerce order storage       | ❌ (risk of data loss)               | ✅ (strong transaction guarantees)|
| User login logs               | ✅ (lightweight)                    | ✅ (long-term analytics)         |
| Real-time queues, pub/sub     | ✅ (List, SortedSet, Pub/Sub)       | ❌                               |
| Complex queries (JOIN, GROUP BY) | ❌ (no SQL support)                  | ✅                               |

##### Redis Cannot Replace MySQL (But They Complement Each Other Well)

Many high-performance systems use a combination of **MySQL + Redis**:

Flow: Check Redis → If miss, query MySQL → Write result back to Redis (cache penetration protection)


