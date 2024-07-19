# 2. Load balancing & Reverse Proxies
Load balancers and reverse proxies are closely related, and while they both manage and distribute incoming network traffic, they serve slightly different primary purposes.  
Both reverse proxies and load balancers improve website performance, but reverse proxies are more focused on caching and security, while load balancers are aimed at evenly distributing traffic and ensuring high availability.   

The choice between using a reverse proxy or a load balancer depends on specific needs, such as the desire for improved performance, security, scalability, or handling high volumes of traffic.


## 2-1. Load balancing

A load balancer is a network device or software that evenly distributes incoming network traffic across multiple servers or resources to optimize performance and ensure high availability. 
![screen](https://github.com/user-attachments/assets/1bbe6379-3a13-44c5-8905-243c08e13d45)


### Traffic Distribution:
 - Least busy : Directs traffic to the server with the most few active connections.
 - By request parameter: divide by function(HTML, Images, Video ... )
   + con: data should be saved duplicated every disc
 - Round Robin : Distributes requests sequentially to each server in the pool.
   + con: just by bad luck one cpu can get a heavy, long job but RR doesn't know that
 - IP Hash: Routes requests based on the client's IP address.
 - Weighted Distribution: Assigns more traffic to servers with higher capacities.

### Health Monitoring:
Regularly checks the health of servers to ensure they can handle requests.
Automatically removes unhealthy servers from the pool and reintroduces them once they are back online.

### SSL Termination:
Offloads the SSL decryption from application servers, improving performance and simplifying certificate management.

### Failover:
If one server fails, the load balancer can redirect traffic to healthy servers, ensuring continuous ``availability`` of services.



## 2-2 Reverse Proxy
Reverse proxies can also perform load balancing and SSL termination, but they are primarily used for caching content and improving security by concealing server IP addresses. Filtering incoming requests and protecting your backend servers from malicious traffic. By implementing access controls and monitoring requests for suspicious activity, reverse proxies can fortify your application’s security and safeguard sensitive data.

![screen](https://github.com/user-attachments/assets/f9314eb4-31d9-43d9-9f83-dde4f52ee6f6)


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