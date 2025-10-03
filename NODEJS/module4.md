# ⚡ Node.js Asynchronous Programming – Complete Notes

---

## 📌 Introduction to Asynchronous Programming
- **Asynchronous programming** allows multiple tasks to run **without blocking** the main execution thread.  
- In Node.js, this is very important because Node.js is **single-threaded** and relies on the **event loop** to handle concurrent tasks.  
- Common async tasks: reading files, database queries, API calls, timers.

---

## ⏳ Callbacks

### 📖 What is a Callback?
- A **callback** is a function passed as an argument to another function.  
- It is executed once the async operation completes.  

**Example:**
```js
const fs = require("fs");

fs.readFile("file.txt", "utf-8", (err, data) => {
  if (err) {
    console.error("Error reading file:", err);
    return;
  }
  console.log("File content:", data);
});
⚠️ Problem: Callback Hell
When callbacks are nested too deeply, code becomes unreadable.

js
Copy code
doSomething((result) => {
  doSomethingElse(result, (newResult) => {
    doThirdThing(newResult, (finalResult) => {
      console.log(finalResult);
    });
  });
});
📜 Promises
📖 What is a Promise?
A Promise represents the eventual completion (or failure) of an asynchronous operation.

It has three states:

Pending

Fulfilled

Rejected

Example:

js
Copy code
const fetchData = () => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data fetched successfully!");
    }, 2000);
  });
};

fetchData()
  .then((data) => console.log(data))
  .catch((err) => console.error(err));
⏩ Async/Await
📖 What is Async/Await?
async/await is built on top of Promises.

It makes asynchronous code look like synchronous code.

async keyword makes a function return a promise.

await pauses execution until the promise is resolved.

Example:

js
Copy code
function fetchData() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      resolve("Data loaded!");
    }, 2000);
  });
}

async function getData() {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (err) {
    console.error("Error:", err);
  }
}

getData();
🛑 Error Handling in Asynchronous Code
1. Error Handling in Callbacks
Error is usually the first parameter in callback functions.

js
Copy code
fs.readFile("nofile.txt", "utf-8", (err, data) => {
  if (err) {
    console.error("Error occurred:", err);
    return;
  }
  console.log(data);
});
2. Error Handling in Promises
Use .catch() to handle errors.

js
Copy code
fetchData()
  .then((data) => console.log(data))
  .catch((err) => console.error("Promise error:", err));
3. Error Handling in Async/Await
Use try...catch block.

js
Copy code
async function runTask() {
  try {
    const result = await fetchData();
    console.log(result);
  } catch (err) {
    console.error("Async/Await error:", err);
  }
}
runTask();
🔄 Comparison Table
Feature	Callbacks	Promises	Async/Await
Syntax	Nested functions	.then().catch()	Looks synchronous
Readability	Hard (Callback Hell)	Better	Best
Error Handling	Check err param	.catch()	try...catch
Modern Usage	❌ Outdated	✅ Common	✅ Most Preferred

📑 Summary
Callbacks → Basic async handling, but may lead to callback hell.

Promises → Provide cleaner .then/.catch chaining.

Async/Await → Most modern and readable approach.

Error Handling → Always handle using try...catch or .catch() to avoid crashes.

yaml
Copy code

---

Do you also want me to **combine this with your previous Node.js notes (Basics, Modules, FS, etc.)** into **one big complete `.md` file** for easy studying?











