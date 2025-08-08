#### Object-relational impedance
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
``` class Customer {
    String name;
    Address address;
}

class Address {
    String street;
    String city;
}
```

In MySQL
```CREATE TABLE Customer (
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
