# MongoDB Sharding  

Sharding is a **scalability** technique in MongoDB that distributes data across multiple servers or **shards**. It enables horizontal scaling by partitioning large datasets and high-throughput operations.

---

## 🔎 What is Sharding?

Sharding is the process of **splitting data across multiple machines** to handle large datasets that exceed the capacity of a single server.

### ✅ Benefits of Sharding
- Handles huge volumes of data
- Improves read/write throughput
- Distributes data storage across multiple servers
- Allows linear horizontal scaling

---

## 🏗️ Sharded Cluster Components

A **sharded cluster** in MongoDB consists of the following components:

### 1. **Shard**
- Each shard holds a subset of the sharded data.
- Each shard is a replica set (for high availability).

### 2. **Config Servers**
- Store metadata and configuration information about the cluster.
- Minimum of 3 config servers is recommended.

### 3. **Query Routers (mongos)**
- Interface between client applications and the sharded cluster.
- Route queries to the appropriate shard(s).

---

## ⚙️ Example: Setting Up a Sharded Cluster (Local Testing)
> ⚠️ This example assumes MongoDB is installed and running locally.

### 1. Start Config Servers
```bash
mkdir -p /data/config1 /data/config2 /data/config3
mongod --configsvr --replSet configReplSet --dbpath /data/config1 --port 27019 --fork --logpath /data/config1/log
mongod --configsvr --replSet configReplSet --dbpath /data/config2 --port 27020 --fork --logpath /data/config2/log
mongod --configsvr --replSet configReplSet --dbpath /data/config3 --port 27021 --fork --logpath /data/config3/log
```

### 2. Start Shards (as Replica Sets)
```bash
mkdir -p /data/shard1 /data/shard2
mongod --shardsvr --replSet shardReplSet1 --dbpath /data/shard1 --port 27018 --fork --logpath /data/shard1/log
mongod --shardsvr --replSet shardReplSet2 --dbpath /data/shard2 --port 27028 --fork --logpath /data/shard2/log
```

### 3. Start mongos Router
```bash
mongos --configdb configReplSet/localhost:27019,localhost:27020,localhost:27021 --port 27017 --fork --logpath /data/mongos.log
```

### 4. Connect and Configure Shards
```js
// Connect to mongos
mongo --port 27017

sh.addShard("shardReplSet1/localhost:27018")
sh.addShard("shardReplSet2/localhost:27028")
```

---

## 🔑 Sharding a Collection

To shard a collection, you must:
1. Enable sharding on the database
2. Choose a **shard key** (an indexed field used to distribute data)

### Example:
```js
use ecommerce
sh.enableSharding("ecommerce")
sh.shardCollection("ecommerce.orders", { customerId: 1 })
```

---

## 📦 Shard Key Design
A good shard key ensures even data distribution and query efficiency.

### ✅ Good Keys:
- High cardinality (many distinct values)
- Frequently used in queries

### ❌ Bad Keys:
- Low cardinality (e.g., boolean fields)
- Monotonically increasing (e.g., auto-increment IDs)

---

## 💼 Use Cases for Sharding

### 🛍 E-commerce Platform
- Large orders collection with millions of entries
- Shard by `customerId` or `region`

### 📈 Analytics System
- Time-series data with huge ingestion rates
- Shard by `deviceId` or `metricType`

### 🌐 Social Media Application
- Billions of users, posts, and interactions
- Shard by `userId` or `postId`

### 📚 Document Management
- Store and search millions of documents
- Shard by `documentId` or `department`

---

## ✅ Summary
| Component       | Description                               |
|----------------|-------------------------------------------|
| Shard          | Stores a portion of the data              |
| Config Server  | Manages metadata for cluster              |
| Mongos Router  | Directs queries to the correct shard      |
| Shard Key      | Determines how data is partitioned        |

Sharding enables MongoDB to scale out horizontally and handle massive amounts of data efficiently. However, shard key choice and cluster architecture must be carefully planned for optimal results.

