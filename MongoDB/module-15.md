# MongoDB Backup & Restore  

Backing up and restoring data is essential for disaster recovery and data migration. MongoDB supports backup through command-line tools like `mongodump`/`mongorestore` and provides automated options in **MongoDB Atlas**.

---

## 🧰 Using `mongodump`

The `mongodump` tool creates a binary export of the contents of a database.

### 🔧 Syntax:
```bash
mongodump --db <database-name> --out <backup-folder>
```

### 📌 Example:
```bash
mongodump --db myapp --out ./backups/myapp-backup
```
This creates a folder named `myapp` in `./backups/myapp-backup` containing BSON and metadata files.

### 💡 Other Options:
- `--collection <name>`: Backup specific collection
- `--gzip`: Compress output
- `--uri`: Use connection string (e.g., MongoDB Atlas)
```bash
mongodump --uri="mongodb+srv://user:pass@cluster.mongodb.net/myapp" --gzip --archive=backup.gz
```

---

## 🔁 Using `mongorestore`

The `mongorestore` tool restores a binary backup created with `mongodump`.

### 🔧 Syntax:
```bash
mongorestore --db <target-db> <backup-folder>/<db-folder>
```

### 📌 Example:
```bash
mongorestore --db myapp ./backups/myapp-backup/myapp
```
This restores the `myapp` database from the specified backup.

### 💡 Other Options:
- `--drop`: Drops the collection before restoring
- `--gzip`: Use if dump is compressed
- `--archive`: Restore from archive file
```bash
mongorestore --uri="mongodb+srv://user:pass@cluster.mongodb.net/myapp" --gzip --archive=backup.gz --drop
```

---

## ☁️ MongoDB Atlas Backups

Atlas offers **automated, cloud-managed backups** for all production clusters.

### 🎯 Features:
- Point-in-time recovery (PITR)
- Daily snapshots (retained for a defined period)
- Restore to same or new cluster

### 🔒 Enable Backups:
1. Go to your Atlas cluster
2. Click on **Backup** tab
3. Enable **Cloud Backup** if not already enabled

### ♻️ Restore from Backup:
1. Go to **Backups** > **Snapshot Schedule**
2. Select snapshot and click **Restore**
3. Choose restore type:
   - To a **new cluster**
   - To **existing cluster** (overwrite)

### 📘 Downloading a Backup (Optional)
Atlas also allows downloading backup snapshots for local storage (for M10+ clusters).

---

## ✅ Summary
| Tool/Method         | Use Case                          | Key Commands/Features                                 |
|---------------------|------------------------------------|--------------------------------------------------------|
| `mongodump`         | Manual backup (binary)             | `--db`, `--out`, `--gzip`, `--archive`, `--uri`        |
| `mongorestore`      | Restore backup data                | `--drop`, `--gzip`, `--archive`, `--db`, `--uri`       |
| Atlas Snapshots     | Auto cloud backups (recommended)   | Daily snapshots, PITR, restore to cluster              |

Whether using command-line tools or Atlas cloud services, regular backups are essential to protect your data from accidental loss or corruption.

