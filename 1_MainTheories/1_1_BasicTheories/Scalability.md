# Scalability

**WHY Scalability?** Scalability has been a problem for a long time for big companies. For example, Instagram has **over 2 billion** monthly active users. Additionally, it has **over 500 million** daily active users, making it the world's 4th largest social media network. Creating a small website, perhaps with under 1,000 MAUs, might be relatively easy. In contrast, building a nationally or globally popular application is an entirely different challenge. All the keywords are the result of the hard work of senior engineers. Let's dive in!

## 1. From Vertical Scaling to Horizontal scaling
### Vertical scaling
Pro: Easy.  
Con: 
- There are limits(ceiling) to computing power, size of SSD and so on
- Cost
  + Example: AWS t4g container
    - 2xlarge: USD 0.2688 per Hour, 8 Core , 32GiB Memmory
    - medium: USD 0.0336 per Hour, 2 Core, 4GiB Memory

### Horizontal scaling
There will be ceiling one day,
use cheaper and slower machines instead.  
Horizontal scaling leads to load balancing

## 2. Load balancing (DNS setup)
Distribute or balance backend servers 
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
(Includes TCP/IP, IP address)


## 6. HTTP and REST

## 7. GraphQL 

## 8. gRPC and WebSockets

## 9. SQL(RDBMS) VS NOSQL

## 10. Sharding (NOSQL) 
Scaling DB horizontally
if there is no foreign key constraints, that means break up DB with diffrent machines horizontally.  
Shard key -> where to put what  



## 11. Replication
Easier ver of sharding
- Replication : 
  + Leader- follower app : Leader(R,W), Follower is a copy version,read only
  + Leader - Leader app : Both can R,W . complex


## 12. CAP theorem:
Data consistency vs Contraint consistency
- CAP Theory (because of Replication design) : Can pick only two
  + Consistency
  + Availability
  + Partition(Network)
  C is a MUST
  AC : PAC
  Latencty+C = ELC

## TODO
TTL
time to live (hour~day)
I you are a power user of server 1 , <-?