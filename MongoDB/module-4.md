
# 🧠 In-Depth Guide to MongoDB CRUD Operations

MongoDB provides robust methods to perform CRUD (Create, Read, Update, Delete) operations. These allow for flexible interaction with your NoSQL document data.

---

## 🔹 Create Operations

### `insertOne()`

Inserts a single document into a MongoDB collection.

```js
db.students.insertOne({
  name: "John Doe",
  age: 22,
  major: "Computer Science"
});
```

**Returns**:

- `acknowledged`: Boolean indicating operation success
- `insertedId`: ObjectId of the new document

### `insertMany()`

Inserts multiple documents simultaneously.

```js
db.students.insertMany([
  { name: "Alice", age: 20 },
  { name: "Bob", age: 21 }
]);
```

**Returns**:

- `insertedCount`
- `insertedIds`: List of inserted document IDs

---

## 🔹 Read Operations

### `find()`

Retrieves all documents that match a query.

```js
db.students.find({ age: { $gte: 21 } });
```

This returns a **cursor**. To convert to an array in Node.js:

```js
const result = await db.collection("students").find({}).toArray();
```

**Options**:

- Projections: `{ name: 1, _id: 0 }` — includes `name`, excludes `_id`

### `findOne()`

Returns the **first** document matching the query.

```js
db.students.findOne({ name: "Alice" });
```

---

## 🔹 Update Operations

### `updateOne()`

Updates the **first** document that matches the filter.

```js
db.students.updateOne(
  { name: "John Doe" },
  { $set: { age: 23 } }
);
```

**Returns**:

- `matchedCount`
- `modifiedCount`
- `upsertedId` (if `upsert` is true)

### `updateMany()`

Updates **all** documents that match the filter.

```js
db.students.updateMany(
  { age: { $lt: 21 } },
  { $inc: { age: 1 } }
);
```

**Update Operators**:

- `$set`: Assign new value
- `$unset`: Remove a field
- `$inc`: Increment numerical field
- `$push`, `$pull`: Modify array fields

---

## 🔹 Delete Operations

### `deleteOne()`

Deletes the **first** document that matches the filter.

```js
db.students.deleteOne({ name: "Alice" });
```

### `deleteMany()`

Deletes **all** documents that match the filter.

```js
db.students.deleteMany({ age: { $lt: 20 } });
```

**Returns**:

- `deletedCount`

---

## 📝 Best Practice

- Use specific filters to avoid accidental deletion or updates
- Always validate data before inserting
- Consider indexing fields that are frequently queried

---

By mastering these CRUD operations, you're well on your way to building powerful and efficient applications with MongoDB. 🚀

