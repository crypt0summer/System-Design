
## 6. Storage
### 6-1. SQL :  SQL (Structured Query Language) is a programming language used for managing and manipulating relational databases, 
  + ACID (Atomicity, Consistency, Isolation, Durability) compliance: is a set of properties that ensure reliability and integrity
### 6-2. NoSQL 
  + provide flexible, schema-less data models and horizontal scalability, making them suitable for handling large volumes of unstructured or semi-structured data.

### 6-3. Sharding (NOSQL) 
Scaling DB horizontally
a technique in database management where data is horizontally divided and distributed across multiple servers or nodes to improve performance, scalability, and load balancing.  
if there is no foreign key constraints, that means break up DB with diffrent machines horizontally.  
Shard key -> where to put what  

### 6-4. DB Replication, Database partitioning(Federation)
Easier ver of sharding
- Replication : 
  + Leader- follower app : Leader(R,W), Follower is a copy version,read only
  + Leader - Leader app : Both can R,W . complex
Replication is the process of creating and maintaining identical copies of data across multiple servers or nodes, providing redundancy, fault tolerance, and improved data availability in distributed systems.

### 6-5. CAP theorem:
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