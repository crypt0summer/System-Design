# 1. From Vertical Scaling to Horizontal scaling
## Vertical scaling
scaling up resources (such as CPU, memory, or storage) on more expensive hardware to improve its performance or handle higher workloads. 
Pro: Easy.  
Con:  
- There are limitations(ceiling) to improving computing power, size of SSD, computing power...
- Costs more
  + Example: AWS t4g container
    - 2xlarge: USD 0.2688 per Hour, 8 Core , 32GiB Memmory
    - medium: USD 0.0336 per Hour, 2 Core, 4GiB Memory
    - Regarding number of cores and size of the memory, highier computing is twice expensive than the lower model.

## Horizontal scaling
Adding more servers to a system to distribute the workload, using cheaper and slower machines instead.  
Horizontal scaling leads to load balancing   
Pro: 
- Scaling out using commodity machines is more cost efficient and results in higher availability than scaling up a single server on more expensive hardware  
Con:
- Scaling horizontally introduces complexity and involves cloning servers
  + Servers should be stateless: they should not contain any user-related data like sessions or profile pictures
  + Session Persistence(Sticky Session) : Ensures that requests from a single user are always routed to the same server, maintaining session data.
    - Sessions can be stored in a centralized data store such as a database (SQL, NoSQL) or a persistent cache (Redis, Memcached)
- Downstream servers such as caches and databases need to handle more simultaneous connections as upstream servers scale out