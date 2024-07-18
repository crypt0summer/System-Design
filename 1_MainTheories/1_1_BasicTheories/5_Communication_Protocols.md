
# 5. Communication Protocols (APIs)
## 5-1. HTTP and REST
  + General-purpose protocol for web communication. 
  + JSON parsing can be slower compared to Protobuf.
  + REST (Representational State Transfer) is an approach to designing web services that uses standard HTTP methods and URLs to facilitate communication between clients and servers.
### REST
- Identify resources (URI in HTTP) - use the same URI regardless of any operation.
- Change with representations (Verbs in HTTP) - use verbs, headers, and body.
- Self-descriptive error message (status response in HTTP) - Use status codes, don't reinvent the wheel.
- HATEOAS (HTML interface for HTTP) - your web service should be fully accessible in a browser.

## 5-2. GraphQL
  + Designed to allow clients to request only the data they need. 
  + Highly flexible
## 5-3. gRPC
  + Focuses on performance and efficiency for service-to-service communication, often within microservices architectures. 
  + Uses Protobuf
  + Generally faster and more efficient due to binary serialization and HTTP/2.
## 5-4. WebSockets
 + WebSockets is a communication protocol that provides full-duplex, real-time, and bidirectional communication between a client and a server over a single, long-lived connection.WebSockets can be used in applications such as chat systems or real-time collaboration tools, where instant and continuous data exchange between clients and servers is required.
