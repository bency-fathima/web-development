# 🌐 HTTP Methods in Express.js — Complete Guide

Express.js allows you to handle various HTTP methods used in web development.  
Each method serves a different purpose in RESTful APIs.

---

## 🧩 1. What Are HTTP Methods?

HTTP methods define the type of operation you want to perform on a resource.

| Method | Purpose | Example |
|--------|----------|----------|
| **GET** | Retrieve data from the server | Get all users |
| **POST** | Send data to create something | Add new user |
| **PUT** | Update an existing resource (replace) | Update user details |
| **PATCH** | Partially update a resource | Update user email only |
| **DELETE** | Remove a resource | Delete user |
 

---

## 🚀 2. Basic Setup

**server.js**
```js
const express = require("express");
const app = express();
const port = 5000;

app.use(express.json());

app.listen(port, () => console.log(`Server running on port ${port}`));
```

---

## 🧠 3. Using GET Method

Used to fetch data (read operation).

```js
app.get("/", (req, res) => {
  res.send("Welcome to Express.js");
});

app.get("/users", (req, res) => {
  res.json([{ name: "Alice" }, { name: "Bob" }]);
});
```

### Example Output
```
GET /users
Response: [{"name": "Alice"}, {"name": "Bob"}]
```

---

## ✍️ 4. Using POST Method

Used to send data (create operation).

```js
app.post("/users", (req, res) => {
  const { name, email } = req.body;
  res.status(201).json({ message: "User created", name, email });
});
```

**Test using Postman:**  
- Method: `POST`  
- URL: `http://localhost:5000/users`  
- Body → JSON:
```json
{
  "name": "John",
  "email": "john@example.com"
}
```

**Response:**
```json
{
  "message": "User created",
  "name": "John",
  "email": "john@example.com"
}
```

---

## 🔁 5. Using PUT Method

Used to **replace** an existing resource.

```js
app.put("/users/:id", (req, res) => {
  const { id } = req.params;
  const { name, email } = req.body;
  res.json({ message: `User ${id} updated`, name, email });
});
```

**Example Request:**
```
PUT /users/1
Body: { "name": "New Name", "email": "new@example.com" }
```

---

## 🧩 6. Using PATCH Method

Used to **partially update** a resource.

```js
app.patch("/users/:id", (req, res) => {
  const { id } = req.params;
  const updates = req.body;
  res.json({ message: `User ${id} partially updated`, updates });
});
```

**Example Request:**
```
PATCH /users/1
Body: { "email": "updated@example.com" }
```

---

## 🗑️ 7. Using DELETE Method

Used to delete a resource.

```js
app.delete("/users/:id", (req, res) => {
  const { id } = req.params;
  res.json({ message: `User ${id} deleted` });
});
```

**Example Request:**
```
DELETE /users/3
```

**Response:**
```json
{
  "message": "User 3 deleted"
}
```

---

 

---

## 🧰 9. Example of All Methods Together

```js
const express = require("express");
const app = express();
app.use(express.json());

app.get("/data", (req, res) => res.send("GET - Retrieve Data"));
app.post("/data", (req, res) => res.send("POST - Create Data"));
app.put("/data", (req, res) => res.send("PUT - Replace Data"));
app.patch("/data", (req, res) => res.send("PATCH - Partial Update"));
app.delete("/data", (req, res) => res.send("DELETE - Remove Data"));

app.listen(5000, () => console.log("Server running on port 5000"));
```

---

## 📦 10. RESTful Example (CRUD Operations)

```
GET    /api/users        → Get all users
GET    /api/users/:id    → Get single user
POST   /api/users        → Create user
PUT    /api/users/:id    → Update user (replace)
PATCH  /api/users/:id    → Partial update
DELETE /api/users/:id    → Delete user
```

---

## 🚨 11. Handling 404 Errors (Invalid Routes)

```js
app.use((req, res) => {
  res.status(404).send("404 - Route Not Found");
});
```

---

## 🧠 12. Summary Table

| Method | Description | Common Use |
|--------|--------------|-------------|
| **GET** | Retrieve data | Reading data |
| **POST** | Add new resource | Creating data |
| **PUT** | Replace existing data | Updating entire data |
| **PATCH** | Update part of resource | Updating some fields |
| **DELETE** | Remove resource | Deleting data |
| **ALL** | Handle all requests | Middleware/Testing |

---

## ✅ Best Practices

- Use `express.json()` to parse JSON request bodies  
- Always send proper HTTP status codes (200, 201, 404, 500)  
- Use RESTful naming conventions  
- Separate routes into their own files (for scalability)  
- Use `async/await` and proper error handling

---
