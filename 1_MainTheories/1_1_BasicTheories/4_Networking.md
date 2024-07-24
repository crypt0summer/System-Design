
# 4. Networking

## 4-1. Lv 4 in OSI 7 layer Model : TCP vs UDP
A connection is controlled at the transport layer(lv 4), and therefore fundamentally out of scope for HTTP. HTTP doesn't require the underlying transport protocol to be connection-based; it only requires it to be reliable, or not lose messages (at minimum, presenting an error in such cases). Among the two most common transport protocols on the Internet, TCP is reliable and UDP isn't. 
![img](https://github.com/user-attachments/assets/140d1e60-313d-408f-bb81-1f84d6a951c3)   

### TCP
- Connection-Oriented   
    TCP establishes a connection between the sender and receiver before data transmission. This ensures that data is delivered reliably and in order.
- Reliable  
    Ensures that data is received correctly and in the correct order. If data is lost or corrupted, TCP handles retransmission.
### UDP
- Connectionless  
    UDP does not establish a connection. It sends data packets directly to the recipient without ensuring delivery or order.
- Unreliable  
    Does not guarantee delivery, order, or error checking. Packets may be lost, duplicated, or arrive out of order.
- Best Effort  
    Suitable for applications where speed is crucial and occasional data loss is acceptable.


## 4-2. Lv 7 in OSI 7 layer Model : HTTP and Websocket
These will be at 5_Communication_Protocols.

## 4-3. BONUS : DNS
a decentralized naming system that translates human-readable domain names into IP addresses