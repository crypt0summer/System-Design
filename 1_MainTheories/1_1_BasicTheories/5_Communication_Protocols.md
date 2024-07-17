
## 5. Communication Protocols (APIs)
### 5-1. HTTP and REST
  + General-purpose protocol for web communication. 
  + JSON parsing can be slower compared to Protobuf.
  + REST (Representational State Transfer) is an approach to designing web services that uses standard HTTP methods and URLs to facilitate communication between clients and servers.
### 5-2. GraphQL
  + Designed to allow clients to request only the data they need. 
  + Highly flexible
### 5-3. gRPC
  + Focuses on performance and efficiency for service-to-service communication, often within microservices architectures. 
  + Uses Protobuf
  + Generally faster and more efficient due to binary serialization and HTTP/2.
### 5-4. WebSockets
 + WebSockets is a communication protocol that provides full-duplex, real-time, and bidirectional communication between a client and a server over a single, long-lived connection.WebSockets can be used in applications such as chat systems or real-time collaboration tools, where instant and continuous data exchange between clients and servers is required.
