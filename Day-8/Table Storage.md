# 📊 What is Azure Table Storage?

### ✅ Definition

**Azure Table Storage** is a **NoSQL key-value store** used to store large amounts of **structured, schema-less data**.

---

# 🧠 Simple Understanding

👉 Table Storage = **Excel-like table without fixed columns (flexible structure)**

---

# 🧩 Structure (Very Important 🔥)

```text id="2ng6rn"
Storage Account
     ↓
Table
     ↓
Entity (Row)
     ↓
Properties (Columns)
```

---

## 🔑 Key Elements

### 1️⃣ Table

* Collection of data

### 2️⃣ Entity (Row)

* Individual record

### 3️⃣ Properties (Columns)

* Attributes of entity

---

## 🔥 Special Keys (Important)

### 🔹 Partition Key

* Groups data
* Improves performance

### 🔹 Row Key

* Unique identifier

👉 Together → **Primary Key**

---

## 📌 Example

```text id="q8g4ch"
Table: Users

PartitionKey: India
RowKey: 101
Name: Khushal
Age: 22
```

---

# ⚙️ Key Features

1. **Schema-less**

   * No fixed structure

2. **Highly Scalable**

   * Handles large data

3. **Fast Access**

   * Key-based lookup

4. **Low Cost**

---

# 🚀 Use Cases

---

## 1️⃣ Logs & Monitoring

* Store application logs

---

## 2️⃣ Metadata Storage

* Store file info, configs

---

## 3️⃣ IoT Data

* Sensor data storage

---

## 4️⃣ User Profiles

* Store user information

---

# ⚠️ Important Points

1. Not relational (no joins ❌)
2. Best for simple queries
3. Use PartitionKey wisely
4. Not suitable for complex queries

---

# ⚖️ Table vs SQL Database

| Feature | Table Storage | SQL Database |
| ------- | ------------- | ------------ |
| Type    | NoSQL         | Relational   |
| Schema  | Flexible      | Fixed        |
| Query   | Simple        | Complex      |
| Cost    | Low           | Higher       |

---

# 🔐 Security

1. RBAC
2. Access keys
3. SAS tokens
4. Encryption

---

# 🏗️ Real Example

👉 IoT System:

* Device sends data
* Stored in Table Storage
* PartitionKey → Device ID
* RowKey → Timestamp

---

# 🎯 Interview One-Liner

👉 **Azure Table Storage is a NoSQL key-value store used to store large amounts of structured data with flexible schema.**

---

# 🚀 Quick Memory Trick

```text id="ntfryg"
Table Storage = NoSQL Table 📊
```

---

