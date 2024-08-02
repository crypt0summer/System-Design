
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

### Denormalization
Denormalization attempts to improve read performance at the expense of some write performance. Redundant copies of the data are written in multiple tables to avoid expensive joins. 
- Pros of Denormalization:
  + Retrieving data is faster since we do fewer joins
  + Queries to retrieve can be simpler(and therefore less likely to have bugs), since we need to look at fewer tables.
- Cons of Denormalization:
  + Updates and inserts are more expensive.
  + Denormalization can make update and insert code harder to write.
  + Data may be inconsistent.
  + Data redundancy necessitates more storage.

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
![screen](https://github.com/user-attachments/assets/2ef71534-5ad9-4cff-845e-6981d4db0d99)

consistency, availability, and partition tolerance, and therefore, trade-offs must be made between these three properties.
- CAP Theory (because of Replication design) : Can pick only two
  + Consistency - Every read receives the most recent write or an error
  + Availability - Every request receives a response, without guarantee that it contains the most recent version of the information
  + Partition Tolerance - The system continues to operate despite arbitrary partitioning due to ``network failures``
  
### CP Example - MongoDB
![screen](https://github.com/user-attachments/assets/6306557b-cd04-4446-8135-296b373a60cb)
MongoDB is a NoSQL database that stores data in one or more Primary nodes in the form of JSON files. Each Primary node has multiple replica sets that update themselves asynchronously using the operation log file of their respective primary node. The replica set nodes in the system send a heartbeat (ping) to every other node to keep track if other replicas or primary nodes are alive or dead. If no heartbeat is received within 10 seconds, then that node is marked as inaccessible.   

If a Primary node becomes inaccessible, then one of the secondary nodes needs to become the primary node. Till a new primary is elected from amongst the secondary nodes, the system remains unavailable to the user to make any new write query. Therefore, the MongoDB system behaves as a Consistent system and compromises on Availability during a partition.   

### AP Example - Cassandra
![screen](https://github.com/user-attachments/assets/ea7e864e-d9e7-4c3f-acee-c809b8415f76)
The Cassandra database is called a highly available database.   

Cassandra is a peer-to-peer system. It consists of multiple nodes in the system. And each node can accept a read or write request from the user. Cassandra maintains multiple replicas of data in separate nodes. This gives it a masterless node architecture where there are multiple points of failure instead of a single point.   

The replication factor determines the number of replicas of data. If the replication factor is 3, then we will replicate the data in three nodes in a clockwise manner.   

CAP_theorem AP with Cassandra
A situation can occur where a partition occurs and the replica does not get an updated copy of the data. In such a situation the replica nodes will still be available to the user but the data will be inconsistent. However, Cassandra also provides eventual consistency. Meaning, all updates will reach all the replicas eventually. But in the meantime, it allows divergent versions of the same data to exist temporarily. Until we update them to the consistent state.   

Therefore, by allowing nodes to be available throughout and allowing temporarily inconsistent data to existing in the system, Cassandra is an AP database that compromises on consistency.   



### Conclusion
1. In a distributed system, it's impossible to achieve all three aspects of the CAP theorem simultaneously. However, partition tolerance (P) is essential in a distributed environment.
2. AP System: Even if a node is temporarily out of sync due to being turned off and on, let's provide a response for now.
3. CP System: Let's wait until synchronization is achieved.