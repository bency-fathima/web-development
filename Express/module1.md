# 📁 Express.js File Organization Guide


## 🧩 1. Basic Single-File Structure

```
project/
│
├── server.js
└── package.json
```

**server.js**
```js
const express = require("express");
const app = express();
const port = 5000;

app.get("/", (req, res) => {
  res.send("Hello World");
});

app.listen(port, () => console.log(`Server running on port ${port}`));
```

---

## 🧱 2. Basic Modular Structure

```
project/
│
├── server.js
├── routes/
│   └── userRoutes.js
└── package.json
```

**server.js**
```js
const express = require("express");
const app = express();
const port = 5000;

const userRoutes = require("./routes/userRoutes");

app.use(express.json());
app.use("/api/users", userRoutes);

app.listen(port, () => console.log(`Server running on port ${port}`));
```

**routes/userRoutes.js**
```js
const express = require("express");
const router = express.Router();

router.get("/", (req, res) => {
  res.send("All users");
});

router.post("/", (req, res) => {
  res.send("User created");
});

module.exports = router;
```

---

## 🧭 3. MVC (Model–View–Controller) Pattern

```
project/
│
├── server.js
├── config/
│   └── db.js
├── controllers/
│   └── userController.js
├── models/
│   └── userModel.js
├── routes/
│   └── userRoutes.js
├── middlewares/
│   └── authMiddleware.js
└── package.json
```

### **server.js**
```js
const express = require("express");
const dotenv = require("dotenv");
const connectDB = require("./config/db");
const userRoutes = require("./routes/userRoutes");

dotenv.config();
connectDB();

const app = express();
app.use(express.json());

app.use("/api/users", userRoutes);

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
```

### **config/db.js**
```js
const mongoose = require("mongoose");

const connectDB = async () => {
  try {
    const conn = await mongoose.connect(process.env.MONGO_URI);
    console.log(`MongoDB Connected: ${conn.connection.host}`);
  } catch (error) {
    console.error(`Error: ${error.message}`);
    process.exit(1);
  }
};

module.exports = connectDB;
```

### **models/userModel.js**
```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: { type: String, required: true },
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true }
});

module.exports = mongoose.model("User", userSchema);
```

### **controllers/userController.js**
```js
const User = require("../models/userModel");

const getUsers = async (req, res) => {
  const users = await User.find();
  res.json(users);
};

const createUser = async (req, res) => {
  const { name, email, password } = req.body;
  const user = new User({ name, email, password });
  const savedUser = await user.save();
  res.status(201).json(savedUser);
};

module.exports = { getUsers, createUser };
```

### **routes/userRoutes.js**
```js
const express = require("express");
const router = express.Router();
const { getUsers, createUser } = require("../controllers/userController");

router.get("/", getUsers);
router.post("/", createUser);

module.exports = router;
```

### **middlewares/authMiddleware.js**
```js
const authMiddleware = (req, res, next) => {
  console.log("Authentication checked");
  next();
};

module.exports = authMiddleware;
```

---

## ⚙️ 4. With Utilities & Helpers

```
project/
│
├── server.js
├── config/
│   └── db.js
├── controllers/
├── models/
├── routes/
├── middlewares/
├── utils/
│   ├── errorHandler.js
│   └── generateToken.js
├── services/
│   └── emailService.js
└── package.json
```

---

## 🧩 5. Full Example Tree (Professional MERN Backend)

```
project/
│
├── server.js
├── package.json
├── .env
│
├── config/
│   └── db.js
│
├── controllers/
│   ├── userController.js
│   └── productController.js
│
├── models/
│   ├── userModel.js
│   └── productModel.js
│
├── routes/
│   ├── userRoutes.js
│   └── productRoutes.js
│
├── middlewares/
│   ├── authMiddleware.js
│   └── errorMiddleware.js
│
├── utils/
│   └── generateToken.js
│
├── services/
│   └── emailService.js
│
└── logs/
    └── app.log
```

---

## 📦 Folder Purpose Summary

| Folder | Purpose |
|--------|----------|
| `config/` | Database connections, environment configs |
| `controllers/` | Business logic for routes |
| `models/` | Mongoose schemas or ORM models |
| `routes/` | Route definitions for each module |
| `middlewares/` | Authentication, validation, error handling |
| `utils/` | Helper functions (tokens, file uploads, etc.) |
| `services/` | External services (email, SMS, APIs) |
| `logs/` | Store application logs |
| `.env` | Store environment variables (DB_URI, PORT, etc.) |

---

## 🚀 Best Practices

✅ Keep controllers small and focused  
✅ Handle all errors using a global error middleware  
✅ Use environment variables for sensitive data  
✅ Use async/await for DB operations  
✅ Don’t put logic directly inside routes  
✅ Follow RESTful route naming conventions
