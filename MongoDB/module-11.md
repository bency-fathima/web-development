# MongoDB Transactions  

MongoDB supports **multi-document ACID transactions**, providing atomicity, consistency, isolation, and durability. Transactions are especially useful in scenarios involving multiple updates that must either **all succeed or none at all**.

---

## 🔐 What Are ACID Transactions?

**ACID** stands for:
- **Atomicity**: All operations in a transaction succeed or none do.
- **Consistency**: The database remains in a valid state before and after the transaction.
- **Isolation**: Transactions do not interfere with each other.
- **Durability**: Once committed, changes persist even in the case of a failure.

MongoDB ensures ACID compliance for transactions across a single replica set (and sharded clusters since v4.2).

---

## 🧪 Enabling Transactions

Transactions require:
- MongoDB replica set (even if single-node)
- WiredTiger storage engine

---

## 🚀 Using Transactions in Node.js

### Step 1: Start a Session
```js
const { MongoClient } = require("mongodb");
const client = new MongoClient("mongodb://localhost:27017");

async function runTransaction() {
  await client.connect();
  const session = client.startSession();
```

### Step 2: Define Transaction Logic
```js
  const ordersCollection = client.db("shop").collection("orders");
  const inventoryCollection = client.db("shop").collection("inventory");

  try {
    session.startTransaction();

    // Example operations
    await ordersCollection.insertOne({
      item: "Headphones",
      quantity: 2,
      status: "pending"
    }, { session });

    await inventoryCollection.updateOne(
      { item: "Headphones" },
      { $inc: { stock: -2 } },
      { session }
    );

    await session.commitTransaction();
    console.log("Transaction committed.");
  } catch (err) {
    await session.abortTransaction();
    console.error("Transaction aborted due to error:", err);
  } finally {
    await session.endSession();
    await client.close();
  }
}

runTransaction();
```

---

## 🧠 Key Transaction Methods

### `startSession()`
- Begins a client session.
- Used to group operations under a single transactional context.

### `startTransaction()`
- Begins a transaction under the current session.

### `commitTransaction()`
- Commits all operations inside the transaction.

### `abortTransaction()`
- Rolls back all operations if an error occurs.

### `endSession()`
- Ends the session and releases resources.

---

## 📝 Important Notes
- Transactions **add overhead** — use only when necessary.
- Each write operation must explicitly include the `{ session }` option.
- You can only use transactions on **replica sets or sharded clusters**.
- **Retry logic** is recommended for transient errors.

---

## ✅ Summary
| Concept             | Purpose                                  |
|---------------------|-------------------------------------------|
| `startSession()`     | Initiates a client session                |
| `startTransaction()` | Begins a transaction                      |
| `commitTransaction()`| Commits all operations in a transaction   |
| `abortTransaction()` | Aborts on error to maintain atomicity     |

MongoDB transactions provide a robust mechanism for ensuring data integrity across multiple operations. Use them wisely in critical financial, inventory, or complex relational scenarios.

