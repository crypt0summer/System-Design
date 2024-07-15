# Scalability:  vertical scaling vs Horizontal

## Vertical Sacling
Pro: Easy.  
Con: 
- There are limits(ceiling) to computing power, size of SSD and so on
- Cost
  + Example: AWS t4g container
    - 2xlarge: USD 0.2688 per Hour, 8 Core , 32GiB Memmory
    - medium: USD 0.0336 per Hour, 2 Core, 4GiB Memory

## Horizontal scaling
There will be ceiling one day,
use cheaper and slower machines instead.  
Horizontal scaling leads to load balancing

## Load balancing (DNS setup)
Distribute or balance backend servers 
only Load balancer has a public address as a DNS
and servers behind gets private adress

-> decide where to send this packet (DNS server)
 - based on load(who is busy and who is not) <- optimizing
 - divide by function(HTML, Images, Video ... )
   + con: data is saved duplicated every disc
 - Round Robin (DNS server just send different one after the other)
   + con: just by bad luck one cpu can get a heavy, long job but RR doesn't know that
 

## Caching
