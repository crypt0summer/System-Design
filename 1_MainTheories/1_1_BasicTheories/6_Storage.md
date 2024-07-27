
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

## 6-3. (Horizontal) Sharding (NOSQL) 
Also known as sharding, horizontal data partitioning involves dividing a database table into multiple partitions or shards, with each partition containing a subset of rows.   
Each shard is typically assigned to a different database server, which allows for parallel processing and faster query execution times.   

For example, consider a social media platform that stores user data in a database table. The platform might partition the user table horizontally based on the geographic location of the users, so that users in the United States are stored in one shard, users in Europe are stored in another shard, and so on. This way, when a user logs in and their data needs to be accessed, the query can be directed to the appropriate shard, minimizing the amount of data that needs to be scanned.  

The key problem with this approach is that if the value whose range is used for partitioning isn’t chosen carefully, then the partitioning scheme will lead to unbalanced servers.  
For instance, partitioning users based on their geographic location assumes an even distribution of users across different regions, which may not be valid due to the presence of densely or sparsely populated areas.  


Similar to the advantages of federation, sharding results in less read and write traffic, less replication, and more cache hits. Index size is also reduced, which generally improves performance with faster queries. If one shard goes down, the other shards are still operational, although you'll want to add some form of replication to avoid data loss. Like federation, there is no single central master serializing writes, allowing you to write in parallel with increased throughput.   

Common ways to shard a table of users is either through the user's last name initial or the user's geographic location.  

Disadvantage(s): sharding  
- You'll need to update your application logic to work with shards, which could result in complex SQL queries.   
- Data distribution can become lopsided in a shard. For example, a set of power users on a shard could result in increased load to that shard compared to others.  
- Rebalancing adds additional complexity. A sharding function based on consistent hashing can reduce the amount of transferred data.  
- Joining data from multiple shards is more complex.  
- Sharding adds more hardware and additional complexity.  


### 6-4. DB Replication, Database partitioning(Federation)
Easier ver of sharding
- Replication : 
  + Leader - follower app : Leader(R,W), Follower is a copy version,read only
      - The master serves reads and writes, replicating writes to one or more slaves, which serve only reads. Slaves can also replicate to additional slaves in a tree-like fashion. If the master goes offline, the system can continue to operate in read-only mode until a slave is promoted to a master or a new master is provisioned.
      - The more read slaves, the more you have to replicate, which leads to greater replication lag.

  + Leader - Leader app : Both can R,W . complex
    - Both masters serve reads and writes and coordinate with each other on writes. If either master goes down, the system can continue to operate with both reads and writes.
    - Disadvantages  
    There is a potential for loss of data if the master fails before any newly written data can be replicated to other nodes.
    Writes are replayed to the read replicas. If there are a lot of writes, the read replicas can get bogged down with replaying writes and can't do as many reads.

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