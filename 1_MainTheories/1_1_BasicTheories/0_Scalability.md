# Scalability

**WHY Scalability?** Scalability has been a problem for a long time for big companies. For example, Instagram has **over 2 billion** monthly active users. Additionally, it has **over 500 million** daily active users, making it the world's 4th largest social media network. Creating a small website, perhaps with under 1,000 MAUs, might be relatively easy. In contrast, building a nationally or globally popular application is an entirely different challenge. All the keywords are the result of the hard work of senior engineers. Let's dive in!


## 1. Vertical to Horizontal
Of course, choosing any technology has pros and cons, but at least for scalability, horizontal scalability is winning. Let's see why.

## 2. Load Balancing and Proxies
When there is heavy traffic, who distributes the load? Who guarantees high availability and reliability if a server fails?
Who is responsible for security and caching?

## 3. Caching
Let's talk more about caching. Do we really have to look up some regularly accessed data every time?
How about images and videos? How can we provide those quickly? (spoiler alert: CDN)

## 4. Networking
Every component (servers, load balancers, databases...) needs to communicate. But how?

## 5. Communication Protocols (APIs)
In real life, there are some grammars to communicate.
If there are rules for sending messages, parsing them will be much easier and faster.

## 6. Storage
The maximum connection number for [Postgres is 100](https://www.postgresql.org/docs/current/runtime-config-connection.html#GUC-MAX-CONNECTIONS).
But MongoDB can [connect up to 128,000 per node.](https://www.mongodb.com/docs/manual/reference/limits/#mongodb-atlas-connection-limits-and-cluster-tier)
Of course each DB has different pros and cons, but NoSQL outperforms RDBMS in case of scalability.  