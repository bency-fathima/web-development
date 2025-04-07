# Indexing in MongoDB  

Indexes in MongoDB improve the performance of search queries by allowing the database to find documents efficiently without scanning every document in a collection. This guide covers **default indexing**, **creating indexes**, **compound indexes**, and **text indexes** with practical examples.

---

## 📌 Default Index on `_id`

Every MongoDB document has a unique `_id` field, and MongoDB automatically creates an index on this field.

### Characteristics:
- Ensures uniqueness.
- Cannot be removed.
- Used for fast document retrieval by ID.

### Example:
```js
// Efficient query due to default _id index

db.users.find({ _id: ObjectId("507f1f77bcf86cd799439011") })
```

---

## 🛠️ Creating Indexes

Indexes can be created on any field to improve query performance.

### Syntax:
```js
db.collection.createIndex({ field: 1 })  // 1 for ascending, -1 for descending
```

### Example:
```js
// Create an ascending index on the 'name' field

db.users.createIndex({ name: 1 })
```

### Viewing Indexes:
```js
db.users.getIndexes()
```

### Dropping Indexes:
```js
db.users.dropIndex({ name: 1 })
```

---

## 🧩 Compound Indexes

A compound index includes multiple fields in a specific order.

### Syntax:
```js
db.collection.createIndex({ field1: 1, field2: -1 })
```

### Use Cases:
- Efficient for queries that filter or sort on multiple fields.
- Order of fields matters.

### Example:
```js
// Create a compound index on age (asc) and name (desc)

db.users.createIndex({ age: 1, name: -1 })

// Query that benefits from the compound index

db.users.find({ age: { $gt: 25 } }).sort({ name: -1 })
```

> ⚠️ Queries should match the order of fields in the compound index to take full advantage of it.

---

## 📝 Text Indexes

Text indexes allow for efficient search of string content within documents.

### Syntax:
```js
db.collection.createIndex({ field: "text" })
```

### Example:
```js
// Create a text index on the 'description' field

db.products.createIndex({ description: "text" })

// Search for documents containing the word "wireless"

db.products.find({ $text: { $search: "wireless" } })
```

### Multi-field Text Index:
```js
// Create a text index on multiple fields

db.articles.createIndex({ title: "text", content: "text" })
```

### Special Features:
- Case-insensitive
- Supports stemming (e.g., searching "run" matches "running")

### Text Score Sorting:
```js
// Return search score and sort by relevance

db.products.find(
  { $text: { $search: "wireless headphones" } },
  { score: { $meta: "textScore" } }
).sort({ score: { $meta: "textScore" } })
```

> ⚠️ Only one text index allowed per collection.

---

## 🚀 Summary
- **`_id` Index**: Always present, fast lookup by ID.
- **Single-field Indexes**: Improve query speed on individual fields.
- **Compound Indexes**: Useful for multi-field queries and sorting.
- **Text Indexes**: Enable powerful full-text search features.

Creating and optimizing indexes is key to maintaining high performance in MongoDB applications, especially with large datasets.

