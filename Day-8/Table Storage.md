# Azure Table Storage

## Overview

Azure Table Storage is a NoSQL key-value store used to store large amounts of structured, schema-less data.

## Simple Understanding

- Table Storage is like an Excel table without fixed columns.

## Structure

```text
Storage Account
   ↓
Table
   ↓
Entity (Row)
   ↓
Properties (Columns)
```

## Key Elements

### Table

Collection of data.

### Entity

Individual record.

### Properties

Attributes of an entity.

## Special Keys

### Partition Key

- Groups data
- Improves performance

### Row Key

- Unique identifier

Together, they form the primary key.

## Example

```text
Table: Users

PartitionKey: India
RowKey: 101
Name: Khushal
Age: 22
```

## Key Features

- Schema-less
- Highly scalable
- Fast access through key-based lookup
- Low cost

## Use Cases

### Logs and Monitoring

Store application logs.

### Metadata Storage

Store file information and configs.

### IoT Data

Store sensor data.

### User Profiles

Store user information.

## Important Points

- Not relational, so no joins
- Best for simple queries
- Use PartitionKey wisely
- Not suitable for complex queries

## Table vs SQL Database

| Feature | Table Storage | SQL Database |
| --- | --- | --- |
| Type | NoSQL | Relational |
| Schema | Flexible | Fixed |
| Query | Simple | Complex |
| Cost | Low | Higher |

## Security

- RBAC
- Access keys
- SAS tokens
- Encryption

## Real Example

IoT system flow:

- Device sends data
- Data is stored in Table Storage
- PartitionKey -> Device ID
- RowKey -> Timestamp

## Interview One-Liner

Azure Table Storage is a NoSQL key-value store used to store large amounts of structured data with a flexible schema.

## Quick Memory Trick

```text
Table Storage = NoSQL Table
```

