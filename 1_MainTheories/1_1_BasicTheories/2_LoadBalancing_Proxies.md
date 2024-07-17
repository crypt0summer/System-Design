# 2. Load balancing & Proxies
A load balancer is a network device or software that evenly distributes incoming network traffic across multiple servers or resources to optimize performance and ensure high availability.  
only Load balancer has a public address as a DNS and servers behind gets private adress  


## 2-1. Load balancing
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
Provides high availability by automatically rerouting traffic in case of server failure.




### Distributing Traffic:

Even Distribution: Load balancers distribute incoming network traffic across multiple servers, ensuring no single server becomes overwhelmed. This helps maintain optimal performance and prevents downtime.
Scalability: By spreading the load, you can add more servers to handle increased traffic without affecting the user experience.
High Availability and Reliability:

### Failover: 
If one server fails, the load balancer can redirect traffic to healthy servers, ensuring continuous availability of services.
### Maintenance: 
Servers can be taken down for maintenance without affecting service availability, as the load balancer will route traffic to other servers.

## 2-2. Proxies
### Security:

Proxies can hide the IP addresses of backend servers, making it harder for attackers to target them directly.
Access Control: Proxies can enforce security policies, such as blocking certain types of traffic or authenticating requests before forwarding them.

### Caching:
Proxies can cache frequently requested content, reducing the load on backend servers and speeding up response times for users.
### Reduced Bandwidth Usage: 
By serving cached content, proxies reduce the amount of data that needs to be fetched from backend servers, saving bandwidth.

### Traffic Management: 
Proxies can manage and balance traffic loads across different servers or data centers, improving efficiency and reliability.
### SSL Termination: 
Proxies can handle SSL/TLS encryption and decryption, offloading this resource-intensive task from backend servers.

### Horizontal Scaling: 
Both load balancers and proxies facilitate horizontal scaling by allowing you to add more servers to handle increased load.
### Flexibility: 
They provide the flexibility to scale different parts of your architecture independently based on demand.
Enhanced User Experience:

### Consistent Performance: 
Users experience consistent performance and reliability, regardless of traffic fluctuations.

## 2-3 Reverse Proxy
A reverse proxy is a web server that centralizes internal services and provides unified interfaces to the public. Requests from clients are forwarded to a server that can fulfill it before the reverse proxy returns the server's response to the client.

Additional benefits include:

Increased security - Hide information about backend servers, blacklist IPs, limit number of connections per client
Increased scalability and flexibility - Clients only see the reverse proxy's IP, allowing you to scale servers or change their configuration
SSL termination - Decrypt incoming requests and encrypt server responses so backend servers do not have to perform these potentially expensive operations
Removes the need to install X.509 certificates on each server
Compression - Compress server responses
Caching - Return the response for cached requests
Static content - Serve static content directly
HTML/CSS/JS
Photos
Videos
Etc





Load balancer vs reverse proxy
Deploying a load balancer is useful when you have multiple servers. Often, load balancers route traffic to a set of servers serving the same function.
Reverse proxies can be useful even with just one web server or application server, opening up the benefits described in the previous section.
Solutions such as NGINX and HAProxy can support both layer 7 reverse proxying and load balancing.
