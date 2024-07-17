# Scalability

**WHY Scalability?** Scalability has been a problem for a long time for big companies. For example, Instagram has **over 2 billion** monthly active users. Additionally, it has **over 500 million** daily active users, making it the world's 4th largest social media network. Creating a small website, perhaps with under 1,000 MAUs, might be relatively easy. In contrast, building a nationally or globally popular application is an entirely different challenge. All the keywords are the result of the hard work of senior engineers. Let's dive in!


## 1. [Vertical to Horizontal](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/1_Vertical_to_Horizontal.md)
Of course, choosing any technology has pros and cons, but at least for scalability, horizontal scalability is winning. Let's see why.

## 2. [Load Balancing and Proxies](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/2_LoadBalancing_Proxies.md)
When there is heavy traffic, who distributes the load? Who guarantees high availability and reliability if a server fails?
Who is responsible for security and caching?

## 3. [Caching](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/3_Caching.md)
Let's talk more about caching. Do we really have to look up some regularly accessed data every time?   
1, it burdens the server and 2, it gives slower response to the user.
How about images and videos? How can we provide those quickly? (spoiler alert: CDN)

## 4. [Networking](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/4_Networking.md)
Every distributed component (servers, load balancers, databases...) needs to communicate. But how?

## 5. [Communication Protocols (APIs)](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/5_Communication_Protocols.md)
In real life, there are some grammars to communicate.
If there are rules for sending messages, parsing them will be much easier and faster.

## 6. [Storage](https://github.com/crypt0summer/System-Design/blob/main/1_MainTheories/1_1_BasicTheories/6_Storage.md)
The maximum connection number for [Postgres is 100](https://www.postgresql.org/docs/current/runtime-config-connection.html#GUC-MAX-CONNECTIONS).
But MongoDB can [connect up to 128,000 per node.](https://www.mongodb.com/docs/manual/reference/limits/#mongodb-atlas-connection-limits-and-cluster-tier)
Of course each DB has different pros and cons, but NoSQL outperforms RDBMS in case of scalability.  
Do you think comparing one database to another is not fair in terms of scalability because it is similar to the vertical scalability?   
Let's dig into the keys and structure of each database to see why.