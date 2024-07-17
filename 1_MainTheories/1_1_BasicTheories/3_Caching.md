## 3. Caching Basics

### 3-1. CDN
CDN
Content Delivery Networks (CDNs) are distributed networks of servers located geographically closer to end users, designed to deliver web content efficiently by caching and serving it from nearby locations

### 3-2. Caching
Caching improves page load times and can reduce the load on your servers and databases.
OS, Browser, DNS caches ip and data to prevent from looking up everytime   
Problem:  
When the program changes, cache can cause confusion because it shows the old information
Session can break caching. Session is a serialized text file. If RR send you to other server, the server don't know you're logged in.  
Cookie works for the same way too.   
Solution:  
(1) Factorization session -> Make a file server(extrnal hard drive) that is connected all servers and store all session data (share state)  
(2) Load balancer -> put session in here 
RAID : redundant array of independent discs  
RAID0 -> 2 hard, identical options, striping data (doubling speed)
RAID1 -> 2 hard, mirror. simultaniously 
Memcached: memory chache run on the server (store whatever you want on the RAM)
