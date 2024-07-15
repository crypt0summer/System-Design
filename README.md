# System-Design

## Motivation

> Learn how to design large-scale systems.  
> Learn production-quality, scalable software architecture


## Index
### 1. Architecture Main Theories
#### 1-1 Basic Theories
- Scalability: Horizontal vs. vertical scaling.
- CAP Theorem: Consistency, Availability, and Partition Tolerance.
  - Consistency: Patterns
  - Availability: Failover, redundancy, and load balancing.
- Caching
  - Client, CDN, WebServer, DB, Application
  - Update Cach
- Load balancing
- VS Reverse Proxy
- DB(RDBMS)
  - Database replication
  - Database partitioning(Federation)
  - Sharding
  - Denormalization
- NoSQL
- DNS 
- CDN
  - Pull
  - Push
- Application Layer
  - Microservices: Advantages, challenges, communication (REST, gRPC).
  - Monolithic: When to use, benefits, and drawbacks.
- HTTP, REST


#### 1-2 High-level Trade-offs
- Performance vs scalability
- Latency vs throughput
- Availability vs consistency

### 2. Case Studies
Scalability, API, Tech Stack, Security, Handling Transactions, High Availability and Disaster Recovery.
- Circle
- Stripe
- Paypal

### 3. Into the Specific Technologies
- DB : Relational(PostgreSQL, MySQL) VS NoSQL (MongoDB, Cassandra)
- Security : 
  - Encryption: Techniques, best practices.  
  - Authentication: OAuth, JWT.  
  - Compliance: PCI DSS standards.  

### 4. Practical Excercises
- Create small projects or code snippets using the technologies studied.
