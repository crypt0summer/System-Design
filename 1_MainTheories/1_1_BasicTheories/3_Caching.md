# 3. Caching Basics


## 3-1. Caching
The cache is a high-speed storage layer that sits between the application and the original source of the data, such as a database, a file system, or a remote web service, in-memory caching, disk caching, database caching, and CDN caching..   
When data is requested by the application, it is first checked in the cache. If the data is found in the cache, it is returned to the application. If the data is not found in the cache, it is retrieved from its original source,

### Memcached VS (In-memory) Redis
- Sessions: Memcached and Redis are often used to store session data for web applications, which can be accessed quickly and reducing latency
- Persistence: Redis offers persistence options (saving data to disk), which can be useful if you need to recover session data after a restart

### Memcached
Made in 2003,
- Good at simple key-value caching. (static data)
- When you need a very high throughput of reads and writes and don’t require persistence.
- When your data set fits entirely in memory.


### Redis
Made in 2009,
- When you need more complex data structures.( various data structures like strings, hashes, lists, sets, sorted sets, bitmaps, hyperloglogs, and geospatial indexes)
- When you require persistence and data durability.
- When you need advanced features like Pub/Sub, transactions, replication, or Lua scripting.

### So, which DB should I use?
According to the paper [A performance evaluation of in-memory databases](https://www.sciencedirect.com/science/article/pii/S1319157816300453?via%3Dihub#t0015) 
- Memcached outperforms in write time, Redis is efficient in using memory when write
- Redis fairly provides better performance than Memcached for the read operation.
- If reading occurs more than writing, Redis is recommended.

Benchmark version:
![img](https://github.com/user-attachments/assets/bcbb47fe-0ba2-4122-a6fc-32b842fa6210)
 
The elapsed time to write value corresponding to a given key per database (ms)
![img](https://github.com/user-attachments/assets/ff46ce79-7c59-427e-bec2-21241ec6f600)   

Memory usages of in-memory databases for write operation (MB).
![img](https://github.com/user-attachments/assets/e9472f40-eb07-453c-8e29-b20abee6f051)  

The elapsed time to read value corresponding to a given key per database (ms)
![img](https://github.com/user-attachments/assets/ceb93945-418d-4d0f-8b29-9407b26a05de)  

Memory usages of in-memory databases for read operation (MB).
![img](https://github.com/user-attachments/assets/5c020b55-ff33-4bb9-9469-f1d80e53bddb)



## 3-2. CDN
A Content Delivery Network (CDN) is a distributed network of servers strategically located across various geographical locations to deliver web content, such as images, videos, and other static assets.   
When a user requests content from a web application, the request is routed to the nearest CDN server (also known as an edge server) based on factors such as network latency and server load.   

![screen](https://github.com/user-attachments/assets/f81c86cd-5781-46fc-ba38-efaa364b40b4)

### Terminologies
1. Point of Presence (PoP): A PoP is a physical location where CDN servers are deployed, typically in data centers distributed across various geographical locations. PoPs are strategically placed close to end-users to minimize latency and improve content delivery performance.

2. Edge Server: An edge server is a CDN server located at a PoP, responsible for caching and delivering content to end-users. These servers store cached copies of the content, reducing the need to fetch data from the origin server.

3. Time to Live (TTL) : TTL is a value that determines how long a piece of content should be stored in the cache before it is considered stale and needs to be refreshed from the origin server.


### Push CDNs
Push CDNs receive new content whenever changes occur on your server. You take full responsibility for providing content, uploading directly to the CDN and rewriting URLs to point to the CDN. 

### Pull CDNs
Pull CDNs grab new content from your server when the first user requests the content. You leave the content on your server and rewrite URLs to point to the CDN. 

### Benefits
1. Reduced latency: By serving content from geographically distributed edge servers, CDNs reduce the time it takes for content to travel from the server to the user, resulting in faster page load times and improved user experience.

2. Enhanced reliability and availability: With multiple edge servers in different locations, CDNs can provide built-in redundancy and fault tolerance. If one server becomes unavailable, requests can be automatically rerouted to another server, ensuring continuous content delivery.

3. Scalability: CDNs can handle sudden traffic spikes and large volumes of concurrent requests, making it easier to scale web applications to handle growing traffic demands.

