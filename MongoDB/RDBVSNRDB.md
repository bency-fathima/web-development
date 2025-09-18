# Relational vs Non-Relational Databases

## 📊 Relational Database (RDBMS)

-   Stores data in **tables (rows & columns)**.\
-   Requires a **fixed schema** (structure must be defined before
    inserting data).\
-   Uses **SQL** (Structured Query Language) for queries.\
-   Good for **structured data** and **complex relationships**.\
-   Examples: **MySQL, PostgreSQL, Oracle, SQL Server**.

## 📂 Non-Relational Database (NoSQL)

-   Stores data in **various formats**:
    -   **Documents** (JSON) → MongoDB\
    -   **Key-Value** → Redis\
    -   **Wide-Column** → Cassandra\
    -   **Graph** → Neo4j\
-   **Schema-less** (flexible, can add new fields anytime).\
-   Designed for **scalability** and **handling unstructured / big
    data**.\
-   No fixed query language (varies by database).\
-   Examples: **MongoDB, Cassandra, Redis, Neo4j**.

## ⚖️ Quick Comparison

  ------------------------------------------------------------------------
  Feature              Relational DB (SQL)      Non-Relational DB (NoSQL)
  -------------------- ------------------------ --------------------------
  Data Model           Tables (rows & columns)  Documents, key-value,
                                                graph, etc.

  Schema               Fixed                    Flexible (schema-less)

  Query Language       SQL                      Varies (e.g., Mongo
                                                queries, Gremlin)

  Relationships        Strong (joins, FK)       Usually weaker (embedded
                                                docs, references)

  Scalability          Vertical (scale up)      Horizontal (scale out)

  Best For             Structured data,         Big data, real-time apps,
                       transactions             flexibility
  ------------------------------------------------------------------------

------------------------------------------------------------------------

👉 **In short:**\
- Use **Relational (SQL)** when you need structured data, strict
consistency, and complex queries.\
- Use **Non-Relational (NoSQL)** when you need scalability, flexibility,
and work with large/unstructured data.
