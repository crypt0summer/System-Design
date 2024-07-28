
# 6. Storage

DB
-SQL vs NoSQL
-scalability - horizontal sharding, replication, Federation and..?

## 6-1. SQL :  SQL (Structured Query Language) is a programming language used for managing and manipulating relational databases
- ACID (Atomicity, Consistency, Isolation, Durability) compliance 
  is a set of properties that ensure reliability and integrity
    + Atomicity : all or nothing. If transaction fails, everything is rollbacked.
    + Consistency : Preserving DB invariants
    + Isolation: Concurrent transactions are isolated from each other
        - serializable : give strongest consistency, but slow down the process
    + Durability : Once a transaction is committed, its permanent

## 6-2. NoSQL 
  + provide flexible, schema-less data models and horizontal scalability, making them suitable for handling large volumes of unstructured or semi-structured data.

## 6-3. (Horizontal) Sharding
Sharding involves dividing a database into smaller, more manageable pieces called shards. Each shard is an independent database that contains a subset of the data.

### Purpose:

- Scalability: By distributing data across multiple servers, sharding allows the database to handle more queries and larger datasets.
- Performance: Reduces the load on any single database instance by spreading the data and queries.

### How it works:

- Horizontal Partitioning: Each shard holds a unique subset of the data. For example, a customer database could be split by geographical region, with each shard containing customers from a specific region.
- Shard Key: A specific key (like a user ID or region) determines which shard a particular piece of data belongs to.

### Use cases:

- Large-scale applications where the dataset is too large for a single database instance.
- Applications with a high volume of read and write operations.


## 6-4. Replication 
Replication involves copying data from one database (the primary) to one or more databases (the replicas).

### Purpose:

- Availability: Ensures that the data is always available, even if one database instance fails.
- Read Scalability: Allows multiple read operations to be distributed across replicas, reducing the load on the primary database.
- Disaster Recovery: Provides data redundancy and helps in disaster recovery scenarios.

### How it works:

- Master-Slave Replication: The primary (master) database handles all the write operations, and changes are propagated to the secondary (slave) databases which handle read operations.
- Master-Master Replication: Multiple databases act as both primary and secondary, allowing read and write operations to be distributed across all instances.

### Use cases:

- Applications requiring high availability and minimal downtime.
- Systems that need to distribute read operations across multiple servers to improve performance.

### Key Differences
1. Functionality:
  - Sharding: Distributes different subsets of data across multiple databases.
  - Replication: Copies the same data across multiple databases.
2. Objective:
  - Sharding: Aims to handle larger datasets and higher throughput by splitting the data.
  - Replication: Aims to increase data availability and read performance through redundancy.
3. Implementation:
  - Sharding: Requires careful planning of the shard key and how data is partitioned.
  - Replication: Involves setting up a primary database and configuring replicas to synchronize data.

## 6-5. CAP theorem:
Data consistency vs Contraint consistency
consistency, availability, and partition tolerance, and therefore, trade-offs must be made between these three properties.
- CAP Theory (because of Replication design) : Can pick only two
  + Consistency
  + Availability
  + Partition Tolerance(Network)
  C is a MUST
  Availability: Failover, redundancy, and load balancing.
  AC : PAC
  Latencty+C = ELC