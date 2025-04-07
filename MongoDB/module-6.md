# Querying Documents in MongoDB (In-Depth with Examples)

MongoDB provides a flexible and powerful query language to retrieve documents from collections. This guide explains how to use **comparison operators**, **logical operators**, and **result modifiers** like **sorting**, **limiting**, and **skipping** — all with practical examples.

---

## 🧮 Comparison Operators
Used to compare field values with specified criteria.

### `$eq` – Equal To
Returns documents where the value of the field equals the specified value.
```js
// Find users whose age is exactly 25
{ age: { $eq: 25 } }
```

### `$gt` – Greater Than
Finds documents with values greater than the specified number.
```js
// Find products priced above $100
{ price: { $gt: 100 } }
```

### `$lt` – Less Than
Finds documents with values less than the specified number.
```js
// Find students with scores below 60
{ score: { $lt: 60 } }
```

### `$in` – Value in Array
Matches documents where the field’s value matches any value in an array.
```js
// Find employees in the 'HR' or 'Finance' departments
{ department: { $in: ["HR", "Finance"] } }
```

---

## 🧠 Logical Operators
Used to combine or negate conditions.

### `$and` – All Conditions Must Match
```js
// Find active users over the age of 30
{ $and: [ { isActive: true }, { age: { $gt: 30 } } ] }
```
You can also write it as:
```js
{ isActive: true, age: { $gt: 30 } }
```

### `$or` – At Least One Condition Must Match
```js
// Find users who are either students or under 18
{ $or: [ { isStudent: true }, { age: { $lt: 18 } } ] }
```

### `$not` – Negate a Condition
```js
// Find users not older than 40
{ age: { $not: { $gt: 40 } } }
```

### `$nor` – None of the Conditions Should Match
```js
// Find users who are not students and not under 18
{ $nor: [ { isStudent: true }, { age: { $lt: 18 } } ] }
```

---

## 📊 Sorting Results
Organizes the returned documents based on specified field(s).

### Syntax:
```js
db.collection.find(query).sort({ field: 1 }) // ascending
```
```js
db.collection.find(query).sort({ field: -1 }) // descending
```

### Example:
```js
// Sort products by price ascending
{ } // no filter
.sort({ price: 1 })
```
```js
// Sort by category ascending and stock descending
.sort({ category: 1, stock: -1 })
```

---

## 📏 Limiting Results
Restricts the number of documents returned.

### Syntax:
```js
db.collection.find(query).limit(n)
```

### Example:
```js
// Get top 5 most expensive products
.find({}).sort({ price: -1 }).limit(5)
```

---

## ⏩ Skipping Results
Skips a number of results, useful for pagination.

### Syntax:
```js
db.collection.find(query).skip(n)
```

### Example:
```js
// Skip first 10 records and show next 5 (pagination)
.find({}).skip(10).limit(5)
```

---

## 🔄 Combined Example
```js
// Get the first 3 active users over 25, sorted by name

db.users.find({
  isActive: true,
  age: { $gt: 25 }
}).sort({ name: 1 }).limit(3)
```

---

By mastering these operators and modifiers, you gain full control over data retrieval in MongoDB — enabling powerful, efficient queries tailored to your application’s needs.

