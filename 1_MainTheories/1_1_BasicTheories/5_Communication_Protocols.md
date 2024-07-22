
# 5. Communication Protocols (APIs)
Lv 7 in OSI 7 layer Model : HTTP, Websocket, GraphQL, gRPC
## 5-1. HTTP and REST, API
### HTTP
HTTP is generally designed to be simple and human-readable, even with the added complexity introduced in HTTP/2 by encapsulating HTTP messages into frames.    
A connection is controlled at the transport layer, and therefore fundamentally out of scope for HTTP. HTTP doesn't require the underlying transport protocol to be connection-based; it only requires it to be reliable, or not lose messages (at minimum, presenting an error in such cases). Among the two most common transport protocols on the Internet, TCP is reliable and UDP isn't. HTTP therefore relies on the TCP standard, which is connection-based.   

  + General-purpose protocol for web communication. 
  + JSON parsing can be slower compared to Protobuf.
  + REST (Representational State Transfer) is an approach to designing web services that uses standard HTTP methods and URLs to facilitate communication between clients and servers.

### REST(Representational State Transfer), Restful API
REST is a set of architectural constraints.
- Uniform interface
  + Requests should identify resources. They do so by using a uniform resource identifier.(The endpoint contains the resource you manipulate.) 
- Statelessness
  + Clients can request resources in any order, and every request is stateless or isolated from other requests. 
- Layered system
- Cacheability

### API (Application Programming Interface)
contract that defines the relationship between two systems in order to exchange information
API contains these methods.
![img](https://github.com/user-attachments/assets/e467658b-3b20-41f9-b54c-5743a3f909d7)   
POST is an important method because it is used to trigger data handling process. Like making a bank account.
On the other hand, it is not ``Idempotent`` and it should be.
- An Idempotent API operation: A request can be retried with no side effects
- Resiliency : The recovery ability of the API from failure
  + Usually done by "retry" but its pre-requisite is an ``Idempotent`` API operation

### Idempotent of Methods
![img](https://github.com/user-attachments/assets/f6f4117d-a7c8-452b-a9f6-3fc17236deb9)   

1. Client generates a request token(e.g. uuid). This should be the same when requesting the same messages.
2. Send it to the resource server
3. The resource server saves uuid in the state store which leads to the queue.
4. If the same request token comes, return the error code.
5. Eventhough the first response of the request token was an error code, if the client sent the very same request (and the token), resource server should send success code if the token was successfully saved in the state store. This is called "returning syntactically identical response"




## 5-2. GraphQL
  + Designed to allow clients to request only the data they need. 
  + Highly flexible
## 5-3. gRPC
  + Focuses on performance and efficiency for service-to-service communication, often within microservices architectures. 
  + Uses Protobuf
  + Generally faster and more efficient due to binary serialization and HTTP/2.
## 5-4. WebSockets
 + WebSockets is a communication protocol that provides full-duplex, real-time, and bidirectional communication between a client and a server over a single, long-lived connection.WebSockets can be used in applications such as chat systems or real-time collaboration tools, where instant and continuous data exchange between clients and servers is required.


