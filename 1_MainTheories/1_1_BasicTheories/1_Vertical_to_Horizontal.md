## 1. From Vertical Scaling to Horizontal scaling
### Vertical scaling
increasing the resources (such as CPU, memory, or storage) of a single machine to improve its performance or handle higher workloads.  
Pro: Easy.  
Con: 
- There are limitations(ceiling) to improving computing power, size of SSD and so on
- Cost more
  + Example: AWS t4g container
    - 2xlarge: USD 0.2688 per Hour, 8 Core , 32GiB Memmory
    - medium: USD 0.0336 per Hour, 2 Core, 4GiB Memory

### Horizontal scaling
Adding more servers to a system to distribute the workload, using cheaper and slower machines instead.  
Horizontal scaling leads to load balancing