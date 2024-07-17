## 2. Load balancing & Proxies
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

Session Persistence(Sticky Session):
Ensures that requests from a single user are always routed to the same server, maintaining session data.


SSL Termination:
Offloads the SSL decryption from application servers, improving performance and simplifying certificate management.

Failover:
Provides high availability by automatically rerouting traffic in case of server failure.