
# 📂 Node.js File System (fs) & Path Module – Complete Notes

---

## 📌 File System Module (fs)
- Node.js provides the **`fs` module** to interact with the file system.  
- It allows you to **read, write, update, delete, and manage files & directories**.  
- Supports both **synchronous** and **asynchronous** methods.

**Importing fs:**
```js
const fs = require("fs");
```

---

## 📖 Reading and Writing Files

### ✅ Writing to a File
```js
const fs = require("fs");

// Write (creates new file or overwrites existing)
fs.writeFileSync("example.txt", "Hello Node.js! (Sync)");

// Async version
fs.writeFile("example.txt", "Hello Node.js! (Async)", (err) => {
  if (err) throw err;
  console.log("File written successfully");
});
```

### ✅ Reading a File
```js
// Sync
const data = fs.readFileSync("example.txt", "utf-8");
console.log(data);

// Async
fs.readFile("example.txt", "utf-8", (err, data) => {
  if (err) throw err;
  console.log(data);
});
```

---

## 📂 Working with File Paths (`path` module)
- Node.js provides the `path` module to handle and transform file paths.  

**Importing path:**
```js
const path = require("path");
```

**Examples:**
```js
console.log(path.basename("/users/test/file.txt"));  // file.txt
console.log(path.dirname("/users/test/file.txt"));   // /users/test
console.log(path.extname("/users/test/file.txt"));   // .txt
console.log(path.join(__dirname, "files", "test.txt")); // combines paths
```

---

## 🛠️ Creating, Renaming, Deleting Files and Directories

### ✅ Create Directory
```js
fs.mkdirSync("myDir");  // Sync
fs.mkdir("myDir", (err) => {
  if (err) throw err;
  console.log("Directory created");
});
```

### ✅ Rename File
```js
fs.renameSync("example.txt", "newName.txt");
```

### ✅ Delete File
```js
fs.unlinkSync("newName.txt");
```

### ✅ Delete Directory
```js
fs.rmdirSync("myDir");
```

---

## 💡 Streams and Buffers

### 📌 What are Streams?
- Streams allow handling **large amounts of data efficiently**.  
- Instead of reading/writing entire files at once, streams work with **chunks**.  
- Types of Streams:  
  - **Readable** → Read data  
  - **Writable** → Write data  
  - **Duplex** → Both read & write  
  - **Transform** → Modify data while reading/writing  

### 📌 What are Buffers?
- Temporary memory storage for handling binary data.  
- Useful for working with streams.

**Example: Reading a file using streams**
```js
const fs = require("fs");

const readStream = fs.createReadStream("bigfile.txt", "utf-8");
readStream.on("data", (chunk) => {
  console.log("New chunk received:");
  console.log(chunk);
});
```

**Example: Writing using streams**
```js
const writeStream = fs.createWriteStream("output.txt");
writeStream.write("Hello, this is written using a stream!");
```

**Example: Pipe (Read → Write)**
```js
const readStream = fs.createReadStream("bigfile.txt");
const writeStream = fs.createWriteStream("copy.txt");

readStream.pipe(writeStream);
```

---

## 📑 Summary
- `fs` → For reading, writing, and managing files & directories.  
- `path` → For handling and manipulating file paths.  
- **Streams** → Efficient for large data (read/write in chunks).  
- **Buffers** → Temporary data storage used by streams.  

---
