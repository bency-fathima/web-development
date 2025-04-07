# MongoDB Data Validation  

Data validation ensures that documents stored in a MongoDB collection conform to a specific structure or set of rules. MongoDB supports two main approaches:

- **Built-in JSON Schema validation** (at the database level)
- **Mongoose validations** (at the application level)

---

## 🧾 JSON Schema Validation (MongoDB Native)

MongoDB allows validation rules using JSON Schema when creating or updating a collection.

### ✅ Benefits:
- Ensures schema consistency at the database level
- Enforced regardless of the application

### 🛠 Creating a Collection with JSON Schema Validation
```js
// Mongo shell or Node.js driver

db.createCollection("products", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name", "price"],
      properties: {
        name: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        price: {
          bsonType: "number",
          minimum: 0,
          description: "must be a non-negative number"
        },
        inStock: {
          bsonType: "bool",
          description: "must be a boolean if present"
        }
      }
    }
  },
  validationLevel: "strict",
  validationAction: "error"
});
```

### 🔄 Modifying Validation Rules
```js
db.runCommand({
  collMod: "products",
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["name"]
    }
  }
});
```

---

## 🧬 Mongoose Validations (App-Level)

Mongoose provides a powerful way to validate data through schema definitions. These validations run before saving documents to MongoDB.

### ✅ Benefits:
- Easy to use
- Integrated with application logic
- Supports custom validation functions

### 🔧 Example Schema with Validations
```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: {
    type: String,
    required: [true, "Name is required"]
  },
  email: {
    type: String,
    required: true,
    unique: true,
    match: [/^\S+@\S+\.\S+$/, "Email is invalid"]
  },
  age: {
    type: Number,
    min: [18, "Must be at least 18"],
    max: 65
  },
  password: {
    type: String,
    validate: {
      validator: function(v) {
        return v.length >= 6;
      },
      message: "Password must be at least 6 characters long"
    }
  }
});

const User = mongoose.model("User", userSchema);
```

### 🚀 Using the Model
```js
const newUser = new User({
  name: "",
  email: "notanemail",
  age: 16,
  password: "123"
});

newUser.save()
  .then(doc => console.log("Saved:", doc))
  .catch(err => console.error("Validation Errors:", err.message));
```

---

## 🧠 Summary

| Feature             | JSON Schema (MongoDB)     | Mongoose ORM              |
|---------------------|-----------------------------|----------------------------|
| Level               | Database                    | Application                |
| Enforced by         | MongoDB engine              | JavaScript (Mongoose)      |
| Custom messages     | Limited                     | Supported                  |
| Custom validation   | No                          | Yes                        |
| Use case            | General enforcement         | App-level & pre-processing |

Both approaches can be used together: use **JSON Schema** for critical backend enforcement and **Mongoose** for more dynamic, user-friendly validation in your Node.js app.

