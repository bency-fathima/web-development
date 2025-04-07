# MongoDB Performance Tuning (In-Depth with Examples)

Performance tuning in MongoDB involves optimizing queries, designing effective indexes, and analyzing execution plans using `.explain()`. These strategies help you avoid slow queries and ensure scalability.

---

## 🚀 Query Optimization

### ✅ Best Practices
- **Use projections** to return only necessary fields
- **Avoid `$where`** clauses and JavaScript expressions
- **Use indexed fields in filters and sort** operations
- **Avoid large `$in` arrays** and regex queries without anchors

### Example
```js
// Inefficient: returns full documents
const result = await db.users.find({ age: { $gt: 25 } });

// Optimized: returns only name and email
const result = await db.users.find({ age: { $gt: 25 } }, { name: 1, email: 1 });
```

### Use Batching
```js
// Fetch data in smaller chunks
const cursor = db.users.find({}).batchSize(100);
while (await cursor.hasNext()) {
  console.log(await cursor.next());
}
```

---

## 📚 Indexing Strategies

Indexes are critical for performance but should be planned carefully to avoid overhead.

### ⚙️ Single Field Index
```js
// Index on 'email'
db.users.createIndex({ email: 1 });
```

### ⚙️ Compound Index
```js
// Index on 'status' and 'createdAt'
db.orders.createIndex({ status: 1, createdAt: -1 });
```
- Use compound indexes when queries frequently filter/sort by multiple fields.

### ⚙️ Covered Queries
A query is "covered" if all the fields it accesses are in the index.
```js
// Index
{ name: 1, email: 1, _id: 0 }

// Query
find({ name: 'Alice' }, { name: 1, email: 1, _id: 0 });
```

### ⚠️ Avoid These
- Too many indexes → slows down writes
- Indexes on low-selectivity fields (e.g., boolean)
- Duplicate/unused indexes

---

## 🔍 Using `.explain()`

The `.explain()` method shows how MongoDB executes a query.

### Syntax
```js
db.collection.find({ field: value }).explain("executionStats");
```

### Key Metrics
- `nReturned`: Number of documents returned
- `totalDocsExamined`: Total scanned documents
- `totalKeysExamined`: Index keys scanned
- `executionTimeMillis`: Query execution time
- `indexName`: Name of the index used (if any)

### Example
```js
// Check if index is used
const stats = await db.users.find({ email: "alice@example.com" }).explain("executionStats");
console.log(stats.executionStats);
```

#### Output Sample
```json
{
  "nReturned": 1,
  "totalKeysExamined": 1,
  "totalDocsExamined": 1,
  "executionTimeMillis": 0,
  "executionStages": {
    "stage": "IXSCAN",
    "indexName": "email_1"
  }
}
```

If the stage is `COLLSCAN`, it means a full collection scan was done (likely missing an index).

---

## 📌 Summary
| Topic                 | Tip/Tool                          |
|----------------------|-----------------------------------|
| Query Optimization   | Use projections, filters, batching|
| Indexing Strategies  | Use compound & covered indexes    |
| Explain Plans         | Use `.explain("executionStats")`  |

With proper indexing, thoughtful query design, and execution analysis, you can significantly enhance MongoDB performance and scalability.

