# MongoDB Security  

Security is a critical component of any production-grade MongoDB deployment. This guide covers essential MongoDB security features including **authentication**, **authorization**, **role-based access control**, **data encryption**, and **IP whitelisting**.

---

## 🔐 Authentication and Authorization

### 🔑 Authentication
Authentication verifies the identity of a user or application.

### Enabling Authentication (mongod.conf)
Edit your MongoDB config file (e.g., `/etc/mongod.conf`):
```yaml
security:
  authorization: "enabled"
```

### Creating an Admin User
Start MongoDB **without** authentication temporarily:
```bash
mongod --port 27017 --dbpath /data/db
```
Create the admin user:
```js
use admin

db.createUser({
  user: "admin",
  pwd: "strongpassword",
  roles: [ { role: "userAdminAnyDatabase", db: "admin" } ]
});
```
Restart MongoDB **with** authentication:
```bash
mongod --auth --port 27017 --dbpath /data/db
```

### Logging in with Authentication
```bash
mongo -u admin -p strongpassword --authenticationDatabase admin
```

---

## 🧑‍💼 Role-Based Access Control (RBAC)

RBAC ensures that users have access only to what they need.

### Built-In Roles Examples
| Role                    | Scope        | Description                             |
|-------------------------|--------------|-----------------------------------------|
| `read`                  | DB-specific  | Read-only access to a database          |
| `readWrite`             | DB-specific  | Read and write access to a database     |
| `dbAdmin`               | DB-specific  | Admin operations on a database          |
| `userAdmin`             | DB-specific  | Create and modify roles/users           |
| `clusterAdmin`          | Cluster      | Cluster-level administrative access     |

### Creating a Read-Only User
```js
use mydatabase

db.createUser({
  user: "readonlyuser",
  pwd: "readonlypass",
  roles: [ { role: "read", db: "mydatabase" } ]
});
```

---

## 🔒 Data Encryption

### 🔐 At Rest
MongoDB supports encryption of data at rest via the **WiredTiger storage engine**.

#### Enable Encryption (Enterprise Only)
Edit `mongod.conf`:
```yaml
security:
  enableEncryption: true
  encryptionKeyFile: /etc/mongodb-keyfile
```

Generate the key file:
```bash
openssl rand -base64 756 > /etc/mongodb-keyfile
chmod 600 /etc/mongodb-keyfile
```

> ❗ Requires MongoDB Enterprise

### 🔐 In Transit
Enable TLS/SSL for encrypted connections.

#### Start mongod with SSL
```bash
mongod --tlsMode requireTLS \
       --tlsCertificateKeyFile /etc/certs/mongodb.pem \
       --tlsCAFile /etc/certs/ca.pem
```

#### Connect with SSL
```bash
mongo --tls \
      --tlsCertificateKeyFile /etc/certs/client.pem \
      --tlsCAFile /etc/certs/ca.pem
```

---

## 🌐 IP Whitelisting
Restricts access to trusted IP addresses only.

### Method 1: Cloud Deployment (MongoDB Atlas)
- Navigate to **Network Access** in Atlas dashboard
- Add IP addresses or CIDR blocks

### Method 2: Self-Hosted Firewall Rules
Use firewall rules (e.g., UFW on Ubuntu):
```bash
sudo ufw enable
sudo ufw allow from 192.168.1.100 to any port 27017
```

---

## ✅ Summary
| Feature                   | Description                                      |
|---------------------------|--------------------------------------------------|
| Authentication            | Verifies identity using usernames/passwords     |
| Authorization             | Grants access using roles                       |
| Role-Based Access Control | Controls actions based on roles                 |
| Encryption at Rest        | Protects stored data (MongoDB Enterprise only)  |
| Encryption in Transit     | TLS/SSL protects data over the network          |
| IP Whitelisting           | Restricts access to trusted IPs only            |

Securing your MongoDB deployment is essential. Use a layered approach: enable authentication, assign minimal privileges, encrypt data, and restrict access to known sources.

