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

### 2. NoSQL VS SQL
#### Relational Databases (SQL): MySQL, PostgreSQL, or Oracle
1. You have structured data with clear relationships
Data fits neatly into tables with rows and columns.
You need joins between multiple tables (e.g., users, orders, products).

2. ACID compliance is important
Transactions must be Atomic, Consistent, Isolated, and Durable.
For example: financial applications, banking systems, inventory tracking.

3. Your schema is well-defined and doesn’t change frequently
You know ahead of time what your data model will look like.
Schema enforcement is important to maintain data integrity.

4. Data integrity and consistency are critical
You need foreign key constraints, unique keys, etc.
Ex: e-commerce order systems, airline booking systems.

5. Complex querying and reporting is needed
You need powerful querying with SQL, aggregations, subqueries, etc.

#### Non-Relational Databases (NoSQL): MongoDB, Cassandra, or Redis
1. Your data is semi-structured or unstructured
JSON, XML, or other flexible formats.
Schema-less, or schema evolves often (e.g., dynamic fields).

2. You need high scalability and availability
Horizontal scaling (distribute data across many servers easily).
Good for big data and real-time applications (e.g., analytics, logs, IoT).

3. You prioritize performance over strict consistency
Eventual consistency is acceptable (ex: social media feeds).
Useful in distributed systems or microservices.

4. Your application requires a flexible schema
Frequent changes to data structure.
Ex: content management systems, product catalogs.

5. Specific use cases:
MongoDB (Document DB): For nested data (e.g., blog posts with comments).
Redis (Key-Value store): Caching, real-time leaderboards.
Cassandra (Wide-column): Time-series data, large-scale analytics.
Neo4j (Graph DB): Social networks, recommendation engines.

| Feature             | Relational DB (SQL)     | Non-Relational DB (NoSQL)         |
| ------------------- | ----------------------- | --------------------------------- |
| Data Structure      | Tables (rows & columns) | Documents, key-value, graph, etc. |
| Schema              | Fixed & predefined      | Dynamic / flexible                |
| Relationships       | Strong (joins)          | Usually avoided or embedded       |
| Transactions (ACID) | Full support            | Limited or eventual consistency   |
| Scalability         | Vertical (scale-up)     | Horizontal (scale-out)            |
| Query Language      | SQL                     | Varies (Mongo query, CQL, etc.)   |
| Use Case Examples   | Banking, ERP, inventory | Social media, IoT, analytics      |


### 3. Object-relational impedance
Object-relational impedance mismatch refers to the conceptual and technical mismatch between object-oriented programming languages (like Java, Python, C#) and relational databases (like MySQL, PostgreSQL, Oracle).

#### Why does this mismatch happen?
Because:
- Object-oriented programming (OOP) uses objects, classes, inheritance, encapsulation, etc.
- Relational databases use tables, rows, foreign keys, and relations.
These two systems are based on very different paradigms, so translating between them is not always straightforward.

#### Key Mismatches
| Concept           | Object-Oriented Model                      | Relational Model                     | Mismatch                                                                                  |
| ----------------- | ------------------------------------------ | ------------------------------------ | ----------------------------------------------------------------------------------------- |
| **Structure**     | Objects with fields                        | Rows in tables                       | Objects can have nested or complex structures; SQL tables are flat                        |
| **Relationships** | Object references                          | Foreign keys and joins               | Object references are in-memory; RDBs need JOINs                                          |
| **Inheritance**   | Classes can extend other classes           | No built-in inheritance              | You must manually design table structures to simulate inheritance (e.g., Table-per-Class) |
| **Identity**      | Object identity (`==` or object reference) | Primary key values                   | Two rows with same values may or may not be same “object”                                 |
| **Navigability**  | Object graphs are navigated via references | Need joins to navigate relationships | Join performance and complexity is different from pointer-based navigation                |
| **Encapsulation** | Objects encapsulate both data and behavior | Tables store only data               | Methods and behavior are lost in the database layer                                       |

#### Example:
In Java
```
class Customer {
    String name;
    Address address;
}

class Address {
    String street;
    String city;
}
```

In MySQL
```
CREATE TABLE Customer (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    address_id INT
);

CREATE TABLE Address (
    id INT PRIMARY KEY,
    street VARCHAR(100),
    city VARCHAR(100)
);
```
In this example, Class Customer has a field named address, while Address also is a Class. In SQL, to connect these 2 classes we need 3 tables (2 for each enity, 1 for associative entity). But in Java, we just need 2 classes.
In code, we just call: `customer.getAddress().getCity()`

In SQL, you need a JOIN:
```
SELECT city FROM Address a
JOIN Customer c ON c.address_id = a.id
WHERE c.name = 'Alice';
```
##### Solutions 
1. Object-Relational Mappers (ORMs)
Tools like:
- Hibernate (Java)
- SQLAlchemy (Python)
- Entity Framework (C#) https://learn.microsoft.com/en-us/ef/core/ 
- Django ORM
They try to bridge the gap between objects and tables automatically.

2. Design patterns like:
- Data Mapper
- Active Record

3. Hybrid approaches
- Sometimes using NoSQL for object-like storage (like MongoDB) can reduce this mismatch.

Anyway, Object-relational impedance mismatch is the difficulty in translating between the object model (OOP) and the relational model (SQL DBs), due to their fundamental differences in structure, relationships, identity, and behavior.
