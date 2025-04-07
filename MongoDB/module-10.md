# MongoDB with Node.js  

Integrating **MongoDB with Node.js** is a common choice for building scalable and flexible applications. This guide covers connecting MongoDB using both the **native driver** and **Mongoose ORM**, including schema definitions and CRUD operations.

---

## 📡 Connecting with MongoDB Native Driver

### Step 1: Install MongoDB Driver
```bash
npm install mongodb
```

### Step 2: Connect to MongoDB
```js
const { MongoClient } = require("mongodb");

const uri = "mongodb://localhost:27017";
const client = new MongoClient(uri);

async function connectDB() {
  try {
    await client.connect();
    const db = client.db("mydatabase");
    console.log("Connected to MongoDB");
  } catch (err) {
    console.error(err);
  } finally {
    await client.close();
  }
}

connectDB();
```

---

## 🔗 Using Mongoose ORM

### Step 1: Install Mongoose
```bash
npm install mongoose
```

### Step 2: Connect to MongoDB using Mongoose
```js
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/mydatabase", {
  useNewUrlParser: true,
  useUnifiedTopology: true,
});

const db = mongoose.connection;
db.on("error", console.error.bind(console, "connection error:"));
db.once("open", () => {
  console.log("Connected to MongoDB with Mongoose");
});
```

---

## 📄 Schema and Models in Mongoose

### Defining a Schema
```js
const { Schema, model } = require("mongoose");

const userSchema = new Schema({
  name: String,
  email: { type: String, required: true, unique: true },
  age: Number,
  isActive: Boolean,
}, { timestamps: true });

const User = model("User", userSchema);
```

---

## ✏️ CRUD Operations in Node.js

### 🔍 Create
```js
const newUser = new User({
  name: "Alice",
  email: "alice@example.com",
  age: 28,
  isActive: true,
});

newUser.save()
  .then(doc => console.log("User Created:", doc))
  .catch(err => console.error(err));
```

### 📄 Read
```js
// Find all users
User.find()
  .then(users => console.log(users))
  .catch(err => console.error(err));

// Find by ID
User.findById("someObjectId")
  .then(user => console.log(user))
  .catch(err => console.error(err));
```

### 🛠 Update
```js
// Update a user's age
User.findByIdAndUpdate("someObjectId", { age: 30 }, { new: true })
  .then(user => console.log("Updated User:", user))
  .catch(err => console.error(err));
```

### ❌ Delete
```js
User.findByIdAndDelete("someObjectId")
  .then(() => console.log("User deleted"))
  .catch(err => console.error(err));
```

---

## 🧠 Summary
| Task                   | Native Driver           | Mongoose ORM         |
|------------------------|--------------------------|-----------------------|
| Connection             | `MongoClient`            | `mongoose.connect()`  |
| Schema Definition      | Manual                   | `Schema` & `Model`    |
| Data Validation        | Manual                   | Built-in with schema  |
| CRUD Operations        | Verbose                  | Simplified            |

Mongoose is preferred for applications needing schema validation, relationships, and model abstraction. The native driver is ideal for lightweight or low-level control needs.

With this setup, you’re ready to build full-stack applications using Node.js and MongoDB!

