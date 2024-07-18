# 2. Load balancing & Reverse Proxies
Load balancers and reverse proxies are closely related, and while they both manage and distribute incoming network traffic, they serve slightly different primary purposes.  


## 2-1. Load balancing

A load balancer is a network device or software that evenly distributes incoming network traffic across multiple servers or resources to optimize performance and ensure high availability.  

### Traffic Distribution:

Round Robin: Distributes requests sequentially to each server in the pool.
Least Connections: Directs traffic to the server with the fewest active connections.
IP Hash: Routes requests based on the client's IP address.
Weighted Distribution: Assigns more traffic to servers with higher capacities.

 - Least busy : based on load(who is busy and who is not) 
 - By request parameter: divide by function(HTML, Images, Video ... )
   + con: data is saved duplicated every disc
 - Round Robin (DNS server just send different one after the other)
   + con: just by bad luck one cpu can get a heavy, long job but RR doesn't know that
 - Sticky Session : 
 - Random

### Health Monitoring:

Regularly checks the health of servers to ensure they can handle requests.
Automatically removes unhealthy servers from the pool and reintroduces them once they are back online.

### SSL Termination:
Offloads the SSL decryption from application servers, improving performance and simplifying certificate management.

### Failover:
If one server fails, the load balancer can redirect traffic to healthy servers, ensuring continuous ``availability`` of services.



## 2-2 Reverse Proxy
A reverse proxy acts as an intermediary for requests from clients seeking resources from servers. It forwards client requests to appropriate servers and returns the server's response to the client. While it can distribute traffic, its primary roles are written below.

### Load Distribution
It can balance the load, but this is typically a secondary function.
### Caching
It can cache content to reduce server load and improve response times.
### Security 
It can hide the details of the backend servers, provide SSL termination, and protect against threats.
### Compression 
It can compress responses to reduce bandwidth usage.


## 2-3. Practical Example

- Load Balancer: 
  Ensures that incoming HTTP requests are evenly distributed across several web servers to optimize resource use and avoid overloading any single server.
   + AWS Load balancer, Google Cloud Load Balancer
- Reverse Proxy: 
  Handles the requests from clients, forwarding them to the appropriate web server, caching static content, compressing data, and managing SSL certificates to offload these tasks from the backend servers.
   + Nginx