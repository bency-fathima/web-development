# MongoDB Replication (In-Depth with Examples)

Replication in MongoDB provides high availability and data redundancy by maintaining **identical copies of data** across multiple servers using **replica sets**. This ensures that even if a server fails, another can take over seamlessly.

---

## 🔁 What is a Replica Set?
A **replica set** is a group of MongoDB servers that maintain the same data set. It consists of:

- **Primary**: Accepts all write operations
- **Secondary**: Replicates data from the primary
- **Arbiter**: Participates in elections but doesn’t store data

### ✅ Benefits of Replication
- High availability and redundancy
- Automatic failover
- Data consistency

---

## 🏗️ Replica Set Architecture

### Members:
- **Primary**: Only one per replica set; handles writes
- **Secondaries**: Any number; replicate from primary
- **Arbiters**: No data, but vote in elections (useful when avoiding even number of nodes)

### Example:
```txt
+-----------+     +------------+     +------------+
|  Primary  | <-- | Secondary  | <-- |  Arbiter   |
+-----------+     +------------+     +------------+
```

---

## ⚙️ Setting Up a Replica Set (Locally)

### 1. Start MongoDB Instances
```bash
mkdir -p /data/rs1 /data/rs2 /data/rs3

mongod --replSet "rs0" --port 27017 --dbpath /data/rs1 --bind_ip localhost --fork --logpath /data/rs1.log
mongod --replSet "rs0" --port 27018 --dbpath /data/rs2 --bind_ip localhost --fork --logpath /data/rs2.log
mongod --replSet "rs0" --port 27019 --dbpath /data/rs3 --bind_ip localhost --fork --logpath /data/rs3.log
```

### 2. Initiate Replica Set
```js
mongo --port 27017

rs.initiate({
  _id: "rs0",
  members: [
    { _id: 0, host: "localhost:27017" },
    { _id: 1, host: "localhost:27018" },
    { _id: 2, host: "localhost:27019", arbiterOnly: true }
  ]
});
```

### 3. Check Replica Set Status
```js
rs.status();
```

---

## 📖 Read Preferences
Read preferences define how MongoDB routes read operations in a replica set.

### Modes:
| Mode              | Description                                         |
|-------------------|-----------------------------------------------------|
| `primary`         | Default. Read from primary only                    |
| `primaryPreferred`| Read from primary, fallback to secondary           |
| `secondary`       | Read from secondary only                           |
| `secondaryPreferred`| Read from secondary, fallback to primary       |
| `nearest`         | Read from the nearest node based on latency        |

### Example:
```js
const client = new MongoClient(uri, {
  readPreference: "secondaryPreferred"
});
```

---

## 🔄 Failover Handling

When a **primary fails**, replica sets trigger an **automatic election**:
- One of the secondaries is promoted to primary
- Writes resume with minimal downtime
- The original primary re-joins as a secondary

### Election Process:
- Majority vote required
- Priority can influence election outcome

### Example Scenario:
1. Primary node (Node A) fails
2. Secondaries detect loss of heartbeat
3. Election occurs → Node B becomes new primary
4. Clients reconnect and continue operations

### Adjusting Member Priorities
```js
rs.reconfig({
  _id: "rs0",
  members: [
    { _id: 0, host: "localhost:27017", priority: 2 },
    { _id: 1, host: "localhost:27018", priority: 1 },
    { _id: 2, host: "localhost:27019", arbiterOnly: true }
  ]
});
```

---

## 🧠 Summary
| Component     | Description                              |
|----------------|------------------------------------------|
| Primary        | Accepts writes and replicates to others  |
| Secondary      | Read replica; eligible for promotion     |
| Arbiter        | Voting member without data               |
| Read Preference| Controls where reads go in the replica set |
| Failover       | Auto-switch to secondary if primary fails|

Replica sets are fundamental to MongoDB's high availability and disaster recovery strategy. Proper configuration and read preference tuning can help maximize performance and reliability.

