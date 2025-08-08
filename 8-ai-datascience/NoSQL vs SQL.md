### NoSQL VS SQL
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

