
# 4. Networking

## 4-1. Lv 4 in OSI 7 layer Model : TCP vs UDP
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