# MongoDB Aggregation Framework  

The **Aggregation Framework** in MongoDB is used to process data records and return computed results. It works by passing documents through a **pipeline** that consists of multiple stages. Each stage transforms the documents and passes the results to the next stage.

## 🧰 The `aggregate()` Method

The `.aggregate()` method is used to run aggregation operations.

### Syntax:
```js
db.collection.aggregate([ /* pipeline stages */ ])
```
Each stage is an object in an array and uses a specific operator like `$match`, `$group`, etc.

---

## 🔍 Common Pipeline Stages

### `$match`
Filters documents based on a condition (similar to `find()`).
```js
// Find users older than 25
{
  $match: { age: { $gt: 25 } }
}
```

### `$group`
Groups documents by a specified field and can perform aggregate functions like `sum`, `avg`, `max`, etc.
```js
// Group orders by customer and sum the total amount
{
  $group: {
    _id: "$customerId",
    totalAmount: { $sum: "$amount" }
  }
}
```

### `$sort`
Sorts documents by a given field.
```js
// Sort by total amount in descending order
{
  $sort: { totalAmount: -1 }
}
```

### `$project`
Reshapes documents by including, excluding, or creating computed fields.
```js
// Project only name and email fields
{
  $project: {
    name: 1,
    email: 1,
    _id: 0
  }
}
```

### `$lookup`
Performs a left outer join with another collection.
```js
// Join orders with customer details
{
  $lookup: {
    from: "customers",
    localField: "customerId",
    foreignField: "_id",
    as: "customerInfo"
  }
}
```

### `$unwind`
Deconstructs an array field from the input documents to output a document for each element.
```js
// Unwind the items array in an order document
{
  $unwind: "$items"
}
```

### `$count`
Counts the number of documents that pass through the pipeline.
```js
// Count number of active users
[
  { $match: { isActive: true } },
  { $count: "activeUserCount" }
]
```

---

## 📊 Full Aggregation Example
```js
db.orders.aggregate([
  // Match orders placed in 2024
  { $match: { year: 2024 } },

  // Group by customer and calculate total spent
  { $group: {
      _id: "$customerId",
      totalSpent: { $sum: "$amount" }
  }},

  // Sort by total spent descending
  { $sort: { totalSpent: -1 } },

  // Limit to top 5 customers
  { $limit: 5 },

  // Lookup customer details
  { $lookup: {
      from: "customers",
      localField: "_id",
      foreignField: "_id",
      as: "customerDetails"
  }}
])
```

---

## 📝 Summary
| Stage    | Purpose                               |
|----------|----------------------------------------|
| `$match`   | Filter documents                      |
| `$group`   | Group and aggregate values            |
| `$sort`    | Sort results                          |
| `$project` | Include/exclude fields                |
| `$lookup`  | Join data from another collection     |
| `$unwind`  | Flatten array fields                  |
| `$count`   | Count documents in pipeline           |

The aggregation framework is extremely powerful for analytics and reporting use cases. You can combine multiple stages to transform and analyze large datasets with precision and flexibility.

