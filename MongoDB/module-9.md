# MongoDB Schema Design  

Designing a proper schema in MongoDB is essential for scalability, performance, and maintainability. Unlike traditional relational databases, MongoDB offers a flexible schema model. Choosing between **embedding** and **referencing**, and structuring relationships like **one-to-one**, **one-to-many**, and **many-to-many** are key decisions in this process.

---

## 📦 Embedding vs Referencing

### 📌 Embedding
Embedding means storing related data in the same document.

#### ✅ When to Use:
- Data is accessed together
- One-to-few relationships
- Atomicity is important

#### Example: Embedding comments in a blog post
```js
{
  _id: ObjectId("..."),
  title: "MongoDB Guide",
  content: "...",
  comments: [
    { user: "Alice", text: "Great post!" },
    { user: "Bob", text: "Thanks for sharing." }
  ]
}
```

### 🔗 Referencing
Referencing involves linking documents using ObjectIds.

#### ✅ When to Use:
- Data is accessed independently
- One-to-many or many-to-many
- Document size might exceed limit

#### Example: Referencing comments by ID
**Post document:**
```js
{
  _id: ObjectId("..."),
  title: "MongoDB Guide",
  commentIds: [ObjectId("abc"), ObjectId("def")]
}
```

**Comment documents:**
```js
{
  _id: ObjectId("abc"),
  user: "Alice",
  text: "Great post!"
}
```

---

## 👥 Relationships

### 1️⃣ One-to-One
Use embedding or referencing based on data usage.

#### Example: User and Profile
**Embedding:**
```js
{
  _id: ObjectId("..."),
  username: "jdoe",
  profile: {
    fullName: "John Doe",
    bio: "Developer"
  }
}
```

**Referencing:**
```js
// user document
{
  _id: ObjectId("..."),
  username: "jdoe",
  profileId: ObjectId("123")
}

// profile document
{
  _id: ObjectId("123"),
  fullName: "John Doe",
  bio: "Developer"
}
```

---

### 2️⃣ One-to-Many

#### Use Cases:
- Blog post → comments
- Product → reviews

**Embedding (when few items):**
```js
{
  _id: ObjectId("..."),
  name: "Product A",
  reviews: [
    { user: "Alice", rating: 5 },
    { user: "Bob", rating: 4 }
  ]
}
```

**Referencing (many items):**
```js
// product document
{
  _id: ObjectId("..."),
  name: "Product A"
}

// review document
{
  _id: ObjectId("..."),
  productId: ObjectId("..."),
  user: "Alice",
  rating: 5
}
```

---

### 3️⃣ Many-to-Many

#### Use Cases:
- Students ↔ Courses
- Authors ↔ Books

**Using references:**
```js
// student document
{
  _id: ObjectId("stu1"),
  name: "Alice",
  courseIds: [ObjectId("c1"), ObjectId("c2")]
}

// course document
{
  _id: ObjectId("c1"),
  title: "Math",
  studentIds: [ObjectId("stu1"), ObjectId("stu2")]
}
```

#### Alternative: Junction Collection
```js
// enrollment document
{
  studentId: ObjectId("stu1"),
  courseId: ObjectId("c1"),
  enrolledOn: ISODate("2024-09-01")
}
```

---

## 🧠 Tips for Schema Design
- Model based on **application needs**, not just data relationships.
- **Embed for performance**, reference for flexibility.
- Avoid deep nesting (limit to 2-3 levels).
- Consider **document size limits** (16MB).

A well-thought schema ensures efficient queries, minimal redundancy, and easier scalability in MongoDB.

