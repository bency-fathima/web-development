# 📘 MongoDB: Basic Concepts

## Database
A **MongoDB database** is a container for collections. It serves as the top-level organizational unit.

- Each database gets its own set of files on the disk.
- You can create multiple databases in a single MongoDB instance.
- Common operations:
  ```js
  use myDatabase  // Switches or creates the database
  db              // Shows the current database
  show dbs        // Lists all databases
  ```

Databases are isolated from each other, which allows for better organization of unrelated data.

---

## Collections
A **collection** is a group of MongoDB documents. It is the equivalent of a table in relational databases.

- Collections do **not** enforce a schema.
- Documents within a collection can have varying sets of fields.
- Collections are created implicitly when you insert a document.

Example:
```js
// This will create a new collection 'users' if it doesn't exist
db.users.insertOne({ name: "Alice", age: 25 });
```

Useful commands:
```js
show collections   // Lists all collections in the current database
db.createCollection("products")
db.products.drop()  // Deletes the collection
```

---

## Documents
Documents are the basic unit of data in MongoDB. Each document is stored in BSON format.

- Documents are similar to JSON objects.
- They support nested structures and arrays.
- Flexible and dynamic schema allows each document to differ.

Example document:
```json
{
  "name": "John",
  "email": "john@example.com",
  "age": 30,
  "address": {
    "city": "New York",
    "zip": "10001"
  },
  "skills": ["JavaScript", "MongoDB"]
}
```

Documents can be queried using key-value pairs and support powerful operators.

---

## BSON Format
**BSON (Binary JSON)** is a binary representation of JSON documents, designed to be more efficient for storage and traversal.

### Key Features:
- Supports additional data types like:
  - `ObjectId`
  - `Date`
  - `Binary data`
  - `Decimal128`
- Optimized for speed and space.

### Comparison:
| Feature          | JSON              | BSON              |
|------------------|-------------------|-------------------|
| Format           | Text              | Binary            |
| Data types       | Limited           | Rich (e.g., Date, ObjectId) |
| Parsing Speed    | Slower            | Faster            |
| Size             | Larger            | Compact           |

---

## Default _id Field
Every document in MongoDB must have a unique `_id` field. This field is automatically added if you don’t provide it.

### Features:
- Acts as the **primary key**.
- Default type is `ObjectId`.

Example:
```json
{
  "_id": ObjectId("507f191e810c19729de860ea"),
  "name": "Jane"
}
```

### ObjectId Structure:
- 12-byte identifier composed of:
  - 4 bytes: Timestamp
  - 5 bytes: Machine ID
  - 3 bytes: Incrementing counter

### Custom _id:
You can assign your own `_id` as long as it’s unique within the collection.
```json
{
  "_id": "user123",
  "name": "Emily"
}
```

Be cautious with custom `_id` fields, especially if you're building distributed systems.

---

**Understanding these basic MongoDB concepts is crucial before diving into CRUD operations, data modeling, and aggregation frameworks.**

Happy learning! 🚀

