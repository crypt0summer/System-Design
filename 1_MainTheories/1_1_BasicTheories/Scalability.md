# Scalability

**WHY Scalability?** Scalability has been a problem for a long time for big companies. For example, Instagram has **over 2 billion** monthly active users. Additionally, it has **over 500 million** daily active users, making it the world's 4th largest social media network. Creating a small website, perhaps with under 1,000 MAUs, might be relatively easy. In contrast, building a nationally or globally popular application is an entirely different challenge. All the keywords are the result of the hard work of senior engineers. Let's dive in!

## 1. From Vertical Scaling to Horizontal scaling
### Vertical scaling
increasing the resources (such as CPU, memory, or storage) of a single machine to improve its performance or handle higher workloads.  
Pro: Easy.  
Con: 
- There are limits(ceiling) to computing power, size of SSD and so on
- Cost
  + Example: AWS t4g container
    - 2xlarge: USD 0.2688 per Hour, 8 Core , 32GiB Memmory
    - medium: USD 0.0336 per Hour, 2 Core, 4GiB Memory

### Horizontal scaling
Adding more servers to a system to distribute the workload, using cheaper and slower machines instead.  
Horizontal scaling leads to load balancing

## 2. Load balancing (DNS setup)
A load balancer is a network device or software that evenly distributes incoming network traffic across multiple servers or resources to optimize performance and ensure high availability.
only Load balancer has a public address as a DNS
and servers behind gets private adress

-> decide where to send this packet (DNS server)
 - based on load(who is busy and who is not) <- optimizing
 - divide by function(HTML, Images, Video ... )
   + con: data is saved duplicated every disc
 - Round Robin (DNS server just send different one after the other)
   + con: just by bad luck one cpu can get a heavy, long job but RR doesn't know that
   
1 Traffic Distribution:

Round Robin: Distributes requests sequentially to each server in the pool.
Least Connections: Directs traffic to the server with the fewest active connections.
IP Hash: Routes requests based on the client's IP address.
Weighted Distribution: Assigns more traffic to servers with higher capacities.

Health Monitoring:

Regularly checks the health of servers to ensure they can handle requests.
Automatically removes unhealthy servers from the pool and reintroduces them once they are back online.

Session Persistence:

Ensures that requests from a single user are always routed to the same server, maintaining session data.

SSL Termination:

Offloads the SSL decryption from application servers, improving performance and simplifying certificate management.

Failover:

Provides high availability by automatically rerouting traffic in case of server failure.
  
## 3. CDN
Content Delivery Networks (CDNs) are distributed networks of servers located geographically closer to end users, designed to deliver web content efficiently by caching and serving it from nearby locations

## 4. Caching
OS, Browser, DNS caches ip and data to prevent from looking up everytime   
Problem:  
Session can break caching. Session is a serialized text file. If RR send you to other server, the server don't know you're logged in.  
Cookie works for the same way too.   
Solution:  
(1) Factorization session -> Make a file server(extrnal hard drive) that is connected all servers and store all session data (share state)  
(2) Load balancer -> put session in here 
RAID : redundant array of independent discs  
RAID0 -> 2 hard, identical options, striping data (doubling speed)
RAID1 -> 2 hard, mirror. simultaniously 


## 5. DNS
a decentralized naming system that translates human-readable domain names into IP addresses
-  TCP : TCP (Transmission Control Protocol) is a communication protocol that ensures reliable, connection-oriented transmission of data by dividing it into smaller packets, numbering them, and reassembling them at the receiving end.


## 6. Communication Protocols
- HTTP and REST
  + General-purpose protocol for web communication. 
  + JSON parsing can be slower compared to Protobuf.
  + REST (Representational State Transfer) is an approach to designing web services that uses standard HTTP methods and URLs to facilitate communication between clients and servers.
- GraphQL
  + Designed to allow clients to request only the data they need. 
  + Highly flexible
- gRPC
  + Focuses on performance and efficiency for service-to-service communication, often within microservices architectures. 
  + Uses Protobuf
  + Generally faster and more efficient due to binary serialization and HTTP/2.
- WebSockets
 + WebSockets is a communication protocol that provides full-duplex, real-time, and bidirectional communication between a client and a server over a single, long-lived connection.WebSockets can be used in applications such as chat systems or real-time collaboration tools, where instant and continuous data exchange between clients and servers is required.

## 7. SQL(RDBMS) VS NoSQL
- SQL :  SQL (Structured Query Language) is a programming language used for managing and manipulating relational databases, 
  + ACID (Atomicity, Consistency, Isolation, Durability) compliance: is a set of properties that ensure reliability and integrity
- NoSQL 
  + provide flexible, schema-less data models and horizontal scalability, making them suitable for handling large volumes of unstructured or semi-structured data.

## 8. Sharding (NOSQL) 
Scaling DB horizontally
a technique in database management where data is horizontally divided and distributed across multiple servers or nodes to improve performance, scalability, and load balancing.  
if there is no foreign key constraints, that means break up DB with diffrent machines horizontally.  
Shard key -> where to put what  

## 9. DB Replication, Database partitioning(Federation)
Easier ver of sharding
- Replication : 
  + Leader- follower app : Leader(R,W), Follower is a copy version,read only
  + Leader - Leader app : Both can R,W . complex
Replication is the process of creating and maintaining identical copies of data across multiple servers or nodes, providing redundancy, fault tolerance, and improved data availability in distributed systems.

## 10. CAP theorem:
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

## TODO
TTL
time to live (hour~day)