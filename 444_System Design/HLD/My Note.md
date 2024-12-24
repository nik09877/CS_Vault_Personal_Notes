# To Do Problems
### 📌 System Design Key Concepts
- [x] Scalability  
- [x] Availability  
- [x] CAP Theorem  
- [x] ACID Transactions  
- [x] Consistent Hashing  
- [x] Rate Limiting  
- [x] SPOF (Single Point of Failure)  
- [x] Fault Tolerance  
- [x] Consensus Algorithms  
- [x] Gossip Protocol  
- [x] Service Discovery  
- [x] API Design  
- [x] Disaster Recovery  
- [x] Distributed Tracing  

---

### 🛠️ System Design Building Blocks
- [x] Content Delivery Network (CDN)  
- [x] Proxy vs Reverse Proxy  
- [x] Domain Name System (DNS)  
- [x] Caching  
- [x] Caching Strategies  
- [x] Distributed Caching  
- [x] Load Balancing  
- [x] Database Types  
- [x] SQL vs NoSQL  
- [ ] Database Indexes  
- [ ] Consistency Patterns  
- [ ] Heartbeats  
- [ ] Circuit Breaker  
- [ ] Idempotency  
- [ ] Database Scaling  
- [ ] Data Replication  
- [ ] Data Redundancy  
- [ ] Database Sharding  
- [ ] Database Architectures  
- [ ] Failover  
- [ ] Bloom Filters  
- [ ] Message Queues  
- [ ] WebSockets  
- [ ] Checksums  
- [ ] API Gateway  
- [ ] Microservices Guidelines  
- [ ] Distributed Locking  

---

### ⚖️ System Design Tradeoffs
- [ ] Top 15 Tradeoffs  
- [ ] Vertical vs Horizontal Scaling  
- [ ] Stateful vs Stateless Design  
- [ ] Batch vs Stream Processing  
- [ ] Strong vs Eventual Consistency  
- [ ] Read-Through vs Write-Through Cache  
- [ ] Push vs Pull Architecture  
- [ ] Long-polling vs WebSockets  
- [ ] REST vs RPC  
- [ ] Synchronous vs Asynchronous Communications  
- [ ] Latency vs Throughput  

---

### 🖇️ System Design Architectural Patterns
- [ ] Client-Server Architecture  
- [ ] Microservices Architecture  
- [ ] Serverless Architecture  
- [ ] Event-Driven Architecture  
- [ ] Peer-to-Peer (P2P) Architecture  

---

### ✅ How to Answer a System Design Interview Problem
- [ ] Read the Full Article  

---

### 💻 System Design Interview Problems
#### Easy  
- [ ] Design URL Shortener like TinyURL  
- [ ] Design Text Storage Service like Pastebin  
- [ ] Design Leaderboard  
- [ ] Design Content Delivery Network (CDN)  
- [ ] Design Parking Garage  
- [ ] Design Vending Machine  
- [ ] Design Distributed Key-Value Store  
- [ ] Design Distributed Cache  
- [ ] Design Authentication System  
- [ ] Design Unified Payments Interface (UPI)  

#### Medium  
- [ ] Design WhatsApp  
- [ ] Design Spotify  
- [ ] Design Distributed Job Scheduler  
- [ ] Design a Scalable Notification Service  
- [ ] Design Instagram  
- [ ] Design Tinder  
- [ ] Design Facebook  
- [ ] Design Twitter  
- [ ] Design Reddit  
- [ ] Design Netflix  
- [ ] Design Youtube  
- [ ] Design Google Search  
- [ ] Design E-commerce Store like Amazon  
- [ ] Design TikTok  
- [ ] Design Shopify  
- [ ] Design Airbnb  
- [ ] Design Autocomplete for Search Engines  
- [ ] Design Rate Limiter  
- [ ] Design Distributed Message Queue like Kafka  
- [ ] Design Flight Booking System  
- [ ] Design Online Code Editor  
- [ ] Design Stock Exchange System  
- [ ] Design an Analytics Platform (Metrics & Logging)  
- [ ] Design Payment System  
- [ ] Design a Digital Wallet  

#### Hard  
- [ ] Design Location-Based Service like Yelp  
- [ ] Design Uber  
- [ ] Design Food Delivery App like Doordash  
- [ ] Design Google Docs  
- [ ] Design Google Maps  
- [ ] Design Zoom  
- [ ] Design Distributed Counter  
- [ ] Design File Sharing System like Dropbox  
- [ ] Design Ticket Booking System like BookMyShow  
- [ ] Design Distributed Web Crawler  
- [ ] Design Code Deployment System  
- [ ] Design Distributed Cloud Storage like S3  
- [ ] Design Distributed Locking Service  
- [ ] Design Slack  
- [ ] Design Live Comments  

---

### 📚 Books
- [ ] Designing Data-Intensive Applications  

---

### 📺 YouTube Channels
- [ ] Tech Dummies Narendra L  
- [ ] Gaurav Sen  
- [ ] codeKarle  
- [ ] ByteByteGo  
- [ ] System Design Interview  
- [ ] sudoCODE  
- [ ] Success in Tech  

---

### 📜 Must-Read Engineering Articles
- [ ] How Discord stores trillions of messages  
- [ ] Building In-Video Search at Netflix  
- [ ] How Canva scaled Media uploads from Zero to 50 Million per Day  
- [ ] How Airbnb avoids double payments in a Distributed Payments System  
- [ ] Stripe’s payments APIs - The first 10 years  
- [ ] Real time messaging at Slack  

---

### 🗞️ Must-Read Distributed Systems Papers
- [ ] Paxos: The Part-Time Parliament  
- [ ] MapReduce: Simplified Data Processing on Large Clusters  
- [ ] The Google File System  
- [ ] Dynamo: Amazon’s Highly Available Key-value Store  
- [ ] Kafka: a Distributed Messaging System for Log Processing  
- [ ] Spanner: Google’s Globally-Distributed Database  
- [ ] Bigtable: A Distributed Storage System for Structured Data  
- [ ] ZooKeeper: Wait-free coordination for Internet-scale systems  
- [ ] The Log-Structured Merge-Tree (LSM-Tree)  
- [ ] The Chubby lock service for loosely-coupled distributed systems  

# Quick Review of Problems and Solutions
### **System Design Questions with Brief Answers :**

1. **Design a URL shortening service like Bitly.**  
    Use a hash function to generate short codes and store the mapping in a database for fast redirection.
    
2. **Design a file storage system like Google Drive.**  
    Use cloud storage for files and a relational database for metadata, with access control and versioning.
    
3. **Design a cache system (e.g., LRU cache).**  
    Use a hash map and doubly linked list to implement the LRU eviction policy.
    
4. **Design a simple social media platform (e.g., Instagram).**  
    Store user data in a NoSQL database, with image storage in the cloud and real-time notifications via WebSockets.
    
5. **Design an e-commerce checkout system.**  
    Use a transactional system with a relational database for orders, payment gateway integration, and inventory management.
    
6. **Design a real-time messaging system (e.g., WhatsApp).**  
    Use WebSockets for real-time communication and store messages in a distributed database.
    
7. **Design a video streaming service (e.g., YouTube).**  
    Store videos in cloud storage, use CDN for content delivery, and relational databases for user interactions.
    
8. **Design a content delivery network (CDN).**  
    Use globally distributed edge servers to cache content, reducing latency, and routing requests via DNS.
    
9. **Design a recommendation engine (e.g., Netflix recommendations).**  
    Use collaborative or content-based filtering with a NoSQL database to store user behavior and content metadata.
    
10. **Design a rate limiter system.**  
    Use token bucket or leaky bucket algorithms with Redis to limit requests and prevent abuse.
    
11. **Design a real-time analytics system (e.g., web traffic monitoring).**  
    Use stream processing frameworks like Kafka and Spark, and store data in time-series databases.
    
12. **Design a microservices architecture for a large application.**  
    Use REST APIs for communication, Docker for containerization, and Kubernetes for orchestration.
    
13. **Design a distributed job scheduler.**  
    Use a distributed queue (e.g., RabbitMQ), with worker nodes to process tasks concurrently.
    
14. **Design a highly available database system.**  
    Use replication, sharding, and consistent hashing to ensure fault tolerance and scalability.
    
15. **Design a search engine.**  
    Use an inverted index to map keywords to documents and employ ranking algorithms like PageRank.
    
16. **Design an online ticket booking system (e.g., for movies, flights).**  
    Use a relational database for seat reservations, with a real-time system for concurrency control.
    
17. **Design a payment gateway system.**  
    Use encryption for security, integrate with external payment providers, and implement fraud detection.
    
18. **Design a location-based service (e.g., Uber).**  
    Use real-time GPS data and geospatial indexing for ride dispatching and tracking.
    
19. **Design a real-time collaboration platform (e.g., Google Docs).**  
    Use WebSockets for live editing, CRDTs for conflict-free concurrent updates, and distributed storage.
    
20. **Design a video conferencing system (e.g., Zoom).**  
    Use WebRTC for peer-to-peer video/audio streaming and TURN/STUN servers for NAT traversal.
    
21. **Design a blogging platform.**  
    Use a NoSQL database for posts, tags, and comments, with caching for high-traffic content.
    
22. **Design a notification system.**  
    Use push notifications with a message queue to ensure scalability and delivery reliability.
    
23. **Design a URL redirection service (e.g., 301 redirect).**  
    Store original URLs and their redirection URLs in a key-value store and redirect based on the key.
    
24. **Design a voting system (e.g., elections).**  
    Use a relational database for votes, implement safeguards against duplicate voting, and ensure privacy.
    
25. **Design a file sharing service.**  
    Store files in cloud storage, use a database for user and permission management, and implement file versioning.
    
26. **Design a job queue system (e.g., for background tasks).**  
    Use a message broker like RabbitMQ or Kafka to manage queues, with workers to process jobs.
    
27. **Design a system for sending emails.**  
    Use an SMTP server to send emails, with a database for managing email queues and delivery logs.
    
28. **Design a cloud-based analytics dashboard.**  
    Use a distributed data storage system and a dashboard frontend that queries real-time analytics data.
    
29. **Design a file compression service.**  
    Use compression algorithms (e.g., gzip) to reduce file size and store compressed files in cloud storage.
    
30. **Design a monitoring system for server health.**  
    Use a distributed system to collect metrics, store them in a time-series database, and use alerts based on thresholds.
# Network Protocols

- Network Protocol defines a set of rules and regulations using which two systems can communicate over the network
- There are 7 layers
	- Application layer
	- Presentation layer
	- Session layer
	- Transport layer
	- Network layer
	- DataLink layer
	- Physical layer
- Application layer protocols
	- Client-Server protocols : Client makes a request and server gives the response back. It is a one way communication.
		- HTTP / HTTPS : 
			- Connection-oriented.
			- we access web pages.
		- FTP : 
			- 2 connections are maintained.
			- Control connection is maintained , data connection can be connected and disconnected when we need to send files through it.
			- Data connection is not encrypted, that's why it is not used.
		- SMTP : 
			- Used with IMAP, POP3. 
			- Used for sending the E-mail, IMAP is used for accessing the mail from server. POP3 is also used for accessing mails, downloads it, not used anymore.
			- User --> MTA (Message Transfer Agent) client --> MTA server --> user
		- WebSockets : Bi-directional communication, not peer-to-peer becuz clients don't talk to each other, only to the servers, use it when we need messaging app
	- Peer to Peer : client - client , client -server communication is possible, uses UDP, that's why it is faster
		- WebRTC

- Transport layer / Network layer
	- TCP/IP
		- connection oriented
		- virtual connection is maintained
		- data packets are sequenced and sent
		- ordering is maintained
		- every packet has ACK
		- If ACK is not received that packet is sent again
		- Slow
	- UDP/FC
		- Connection less protocol
		- multiple virtual connections
		- datagrams are sent parallelly 
		- no ordering is maintained
		- it's fast
		- No ACK, No ordering , No connection
		- Live streaming, Video calling


# CAP Theorum

- Defines desirable properties of distributed systems with replicated data.
	- Consistency
		- Data is consistent / same across all the DB nodes
	- Availability
		- All the DB nodes should respond
	- Partition Tolerance
		- System is up, even if the connection between any 2 DB nodes fails
- All 3 can't be used at once
- CA and CP, AP are possible, CAP is not possible
- In CA if Partition happens the system will be down 
- In CP if Partition happens we have to turn off a node
- In AP consistency can not be achieved
- Never trade off Partition tolerance in real world

# Monolithic vs Microservice and it's patterns

## Reference
[Microservice patterns](https://microservices.io/patterns/index.html)

## Monolithic vs Microservice

### Monolithic
- Single application has all the features and functionalities

#### Disadv
1. Overload IDE (too difficult to load it in IDE)
2. Scaling is very hard, if 10GB app is there we need to scale the whole app i.e extra 10GB required 
3. Tightly coupled
4. Deploying is slow
5. Difficult to fix bugs

### Microservice
- An application is divided into different services

#### Adv
- Scaling is easy
- Loose Coupled
- Easy to fix bugs
- Deploying is fast

#### Disadv
- Proper decomposition of application into services:
	- There shouldn't be too much dependency among the services becuz the latency can increase, so it should be loosely coupled
- Monitoring / Debugging is tough:
	- Let's say S3 is going into prod after making some changes to it and dependency flow is S1 -> S2 -> S3 and the response received from S3 by S2 has changed, so S2 will break and S1 will also break
- Transaction management is difficult
	- Lets say S1 has DB1, S2 has DB2, and through some request S1 inserts data successfully into DB1 , but insertion into S2 fails, so we need to rollback both the insertion i.e the successful one and the failed one

## Different phases of Microservices (Convert a Monolithic architecture to Microservice architecture)

1. Decomposition 
	1. By business capability
	2. By subdomain
2. Database
	1. Database per service (mostly used)
		1. Local transaction posssible, but as a whole transaction across all DBs is not easy, we use SAGA pattern for this
		2. Query Join tables across multiple DBs, we use CQRS for this
		3. Rule is, one service can't directly access other service's DB, you can use API of other service for it. Adv is if one is using MySQL, another is using MongoDB, it doesn't matter.
		4. Scaling individual DB is cost effective and easy
	2. Shared database (not very successful)
		1. If one service is sending requests in millions and other services are not, we still need to scale the whole DB 
		2. You can't delete / modify the table in a DB that easily, becuz you have to check if other services will get impacted
		3. Adv is easy joining of tables and transaction management is also easy 
3. Communication
	1. Via API
	2. Via Events
4. Integration : UI and microservice
	1. API Gateways
5. Deployment
6. Cross Cutting
7. Observability / Monitoring

### Decomposition

- How much small our service should be
- 2 types
	- By subdomain (DDD -> Domain Driven Design)
	- By business capability / functionality

#### Business Functionality / Capability

- e.g Online Order Application
- Functionalities
	- Order management
	- Product management / inventory
	- Account management
	- Login
	- Payment
	- Billing
- Acc to these functionalities make these microservices
- Challenges
	- Good knowledge of business functionalities

#### By Subdomain
- A domain can have multiple microservices
- If order management is one domain
	- Order tracking (microservice)
	- Order placing
- Payment domain
	- Forward payment (microservice)
	- Reverse payment (microservice)

#### Decomposition Patterns
1. Strangler
2. Saga
3. CQRS (Command Query Request Segregation)

##### STRANGLER PATTERN
- Used when we need to refactor a monolithic service to microservice
- We slowly slowly strangle the monolithic service. How?
	- We don't completely convert the monolithic to microservices at once
	- We initially route 10% API traffic to microservice and 90% to monolithic
	- Then after refactoring some more modules, we increase the API traffic for microservice and we keep on doing it till the API traffic of microservice is 100% and for monolithic 0%

##### SAGA PATTERN
- Called Sequence of Local Transactions
- Used for transaction management for distributed DBs.
- Ex : place an order
	- change is required in Order DB, Inventory DB, Payment DB
	- What if DB calls for order DB, Inventory DB are successful, but for payment it is not
- In this we create a sequence of DBS like DB1 -> DB2 -> DB3
- Then when the transaction is successful in DB1 it publishes a success event which is listened by DB2 , then it performs it's transaction, if one DB transaction fails it publishes failure / compensation event , so other DB listening to it rollback its transaction and so on
- **Two types :**
	- Choreography
		- There is a message event block (for failure and success)
		- services publish events there and other services listen to the event and work accordingly
		- There can be cyclic dependency (Service1 publishes event , S2 listens and works and publishes, which is listened by S1 and so on)
	- Orchestrator
		- Orchestrator will call S1, S2, S3 if success or failure happens
###### Interview question
- Assume Person A has to pay Person B 10Rs, what is balance is deducted but payment fails
- Two microservices
	- Balance
	- Payment
- For this use SAGA Pattern

##### CQRS PATTERN (Command Query Request Segregation)
- Used for joining tables of distributed DBs
- In this create a new common view / DB which listens to changes in the local DBs and performs same operation in it or you can use DB triggers i.e when Command happens procedure will run and do the same in the common view
- Command -> do these operations on local DBs
	- create
	- update
	- delete
- Query -> Query the separately created view 
	- Select


# How to scale From 0 to 1Mil Users
1. Single Server
2. Application and DB server separation
3. Load Balancer + Multiple App servers
4. DB Replication
5. Cache
6. CDN
7. Data Centre
8. Messaging Queue
9. Database Scaling

## 1. Single Server

- In college we do Client (web + mobile) and server ( Application + DB )

## Application and DB server separation

- Client <-----> Application Server (Business Layer / Mid Tier) <-----> DB server (DB Tier)
- We do this so that we can grow the servers independantly

## 3. Load Balancer + Multiple App servers

- Client <-----> Load Balancer <-----> [App Server 1 , App Server 2 , App server 3 . . .] <----> Db Server
- Load Balancer decides which App server it will forward the request to
- Load Balancer brings privacy , it talks in private Ip with App servers 

## 4. Database Replication
- To handle if the DB fails
- Master Slave concept
	- Master DB (one)
		- write requests go to this
		- If this DB is down, any one of the slave DBs get promoted to become the Master DB
	- Slave DBs (multiple)
		- read requests go to these 

## 5. Cache

- When an App server talks with Db server, it is a network call, which is very expensive. 
- For network call there is overhead, latency issue
- When cache is set up TTL (Time To Live) is decided, after that data gets erased
- So App server can call the cache to check if data is present
	- If present Cache hit
	- Else cache miss
		- Do DB call
		- Save in cache

## 6. CDN

- Content Delivery Network
- CDN does caching , but all those who do caching aren't CDNs
- Where is it used
	- Lets say Data center is in India but users are present in multiple different countries, Indian user will get data fast, but other country's users will get data a bit late, so latency is location dependent here .
- One original data center / server
- Multiple CDN Nodes do the caching of static data or data which changes rarely, using URL as key
- User req will first check the nearest CDN, if data is not there it will ask it's nearest CDN, if the data is not even there, it will ask the original server
- It is smart enough to handle DDOS attacks
- The load on the original server is reduced 
- Performance is increased
- Cost cutting, due to reduced load on DB server 
- Client talks with CDN
## 7.Data Centre

- One Data centre is multiple app servers + multiple Db servers
- Client [<-----> CDN /OR/ <-----> Load Balancer] <-----depending on Geo location-----> [Data centre 1, Data Center 2 . . .]
- If suppose Data of India is stored in India Data Centre and it goes down , so all the requests are routed towards USA Data center, but USA data centre doesn't have Indian users data so how to tackle this problem?
	- DB replication among multiple Data centres take place

## 8. Messaging Queue

- RabbitMQ, Kafka
- There is a **Producer**
	- Pushes message in Messaging Queue / Topic
- There are multiple **Subscribers**
	- Subscribe to the Messaging Queue / Topic
- This brings Async nature in our codebase
- If fails there is a Requeue, so subscriber can pick it up from this queue
- App server talks with the Messaging queue
### Terminologies

![Architecture](Pasted_image_20240705134712.png)

#### 3 types of Routing keys
1. Direct
	1. Routing key == Binding key
	2. Exchange sends the message to only one messaging queue
2. Fan Out
	1. Sends the message to all the queues
	2. subscribers who require this message will work on it else ignore it
3. Topic 
	1. Wildcard matching of the routing key with the binding keys
	2. So the message can go to multiple queues if their binding keys contain the routing key

## 9. Database Scaling

- 2 types
	- Vertical
		- Increase already present DBs capabilities  (CPU, RAM)
		- But there is always a limit
	- Horizontal
		- Add more nodes
		- Sharding
			- Horizontal
				- We divide a table row wise into multiple tables
				- let's say in a table you have 1000 rows
				- divide it into mltiple tables T1 contains 1 to 500 rows, T2 contains 501 to 1000 rows
				- let's say there is a name column and name starting with a to p go in table T1, q to z go into T2
				- Generally better
			- Vertical
				- There are 10 columns
				- we divide table column wise into multiple tables, but each table contains all the rows
			- Drawback 
				- one shard might get filled if a lot of names start with letter (a to p) , so we need to do sharding of this shard, tree like structure, so use consistent hashing
				- Join is difficult, so denormalize it


# Consistent Hashing

### Hashing
- Hash function takes an arbitrary length input and gives a fixed length output.
- In modulo hashing we do hash(key) = key % table size, table size is fixed

#### Problem with hashing
- If the total size of nodes is not fixed, then it creates problems
- after increasing the total nodes, the modulo might not give the same node index, so we need to do rebalancing of all data in all the nodes
- Problem occurs in
	- Load balancer for App. servers
	- Horizontal Sharding

### Use of Consistent Hashing
- When the number of nodes used is dynamic / keeps changing, we use consistent hashing.
- Consistent Hashing improves upon simple hashing by reducing the reallocation of requests to servers when a new server is added or removed.
- Let's say node N1 contains data for Id 1-10, N2 -> 11 - 20, N3 -> 21 - 30 and if we add another new node N4 or remove a node .
- The **rebalancing of data = (1/n) % of total number of IDs**, where n = total number of nodes, which is very less

### How it works

- In consistent hashing we have a circular array ranging from 0 to N-1. 
- Each client and server have IDs. 
- So we hash these IDs and place the client and servers on the circular array. 
- For each client request we go clockwise and find the nearest server. 
- And route the request to that server So the load factor (on average) in this case is **1/N.**

![](Pasted_image_20240705152834.png)

#### Limitations of this approach
- Although load factor is 1/N in average case, practically we may have skewed (uneven) distribution. This might cause a few servers to be overloaded with a lot of requests while other servers are idle. 

- Consider the example below

![](Pasted_image_20240705153040.png)

- Server 1 receives 6 client requests whereas server 3 receives only 1. 
- This approach won't work if servers have different capacities since it distributes the load evenly.

#### Solution to prevent skewed distribution

- To solve this we can use the concept of virtual servers. 
- We want to increase the number of servers but getting actual servers is expensive, so for each server, instead of 1 we can generate K server IDs. 
- We then hash these K IDs and place them on the circular array. 
- Everything else remains the same. This reduces the chance of load being skewed.


# Design URL Shortener / Tiny URL

## 1. Requirement Analysis

1. How short our URL should be ?
2. Traffic per day ? 
	1. 10Mil URL per day -> 365 * 10Mil URL per year
	2. should support 100 years -> 365 * 1000 Mil URLs
3. how many characters should we use
	1. 0 - 9 , a - z , A - Z => 62 characters, so we need around 7 characters
4. key = Long URL , hash(key) = short URL, how to generate this hash value
	1. Use Hash Function
		1. MD5
			1. 128 bit hash function => 16 bytes
			2. 1 byte => 2 hexa digits so 16 bytes => 32 hexa digits 
			3. It's a lot more than we need
			4. Even if we take only first 7 characters , there will be a lot of collisions
		2. SHA-1
			1. 160 bit => 20 byte => 40 hexa digits
			2. Same problem as above
	2. Base62 Encoding
		1. decimal -> Base 62 => divide decimal number by 62, take remainder in reverse direction
		2. Issues
			1. Unique ID generator for storing the URLS ( creating primary key for table)
				1. Auto Increment, will fail if multiple DBs are there
				2. Snow Flake
					1. uses timestamp(41 bits), machine id, sequence no, 1 bit is reserved
					2. used in Twitter
				3. Zookeeper (By Apache)
					1. range of Ids are assigned to each application server, if one range is filled another range is assigned to it
			2. Length is not fixed, may vary
				1. As length can't exceed beyond 7 because 365billion = 62 ^ 7, so use padding
## Design

![](Pasted_image_20240705172139.png)


# Back-of-the-envelope Estimation 

- It is what drives your design decisions
- Using this we determine if we need load balancers or caches or CDNs etc
- For estimation use numbers multiplied by 10 i.e 430Mil, 3Bil etc

## Cheat sheet 1

|          | Traffic    | Storage |
| -------- | ---------- | ------- |
| 3 zeros  | Thousand   | KB      |
| 6 zeros  | Million    | MB      |
| 9 zeros  | Billion    | GB      |
| 12 zeros | Trillion   | TB      |
| 15 zeros | Quadrillion | PB      |

- Char -> 2 bytes ASCII /  (1byte) Unicode
- Long / Double -> 8 Bytes
- Image -> 300KB 

## Cheat Sheet 2

- X Mil user * Y Mb size => XY TB Storage

## Which things to estimate
1. No. of servers
2. RAM
3. Storage Capacity
4. Trade off using CAP theorum

## Estimation of Facebook

### 1. Traffic Estimation

- Total Users : 1 Billion
- DAU (Daily active users) : 25% => 250 Million Users
- Requests per day
	- one user => 5 Read + 2 Write requests
	- 250 Mil => 250 * 7 Mil requests per day
	- 1 day = 86400 seconds = 100000 seconds = 1 lakh
	- Requests per second 
		- (250 * 7 Mil) /  100000 = 18k requests per second

### Storage Estimation

- Every user does 2 posts 
- Each post 250 characters
- 10% of users are uploading 1 image
- 1 image = 300KB
- 1 post => 250 chars => 500 Bytes
	- 2 posts => 1KB
	- 250 Mil users => 250Mil * 1KB = 250GB per day
	- similarly do for image 8TB
- We want to store for 5 years
	- 5 years = 2000 days
	- 1 day => 8TB / 250GB
	- 2000 days => 16 PB for image and 500TB 

### RAM Estimation

- For each user we are storing last 5 posts in cache
- 1 post = 500Bytes 
	- 5 posts = 2500Bytes = 3KB
- 250 Mil Users * 3 KB = 750 GB
- 75GB RAM= 1 server
	- 750DB RAM = 10 server will have cache

### Latency
- 95% time = 500ms per request
- 1 second = 2 * 500 ms => 2requests
- 1 server = 50 threads => 100 requests per second
- 18k requests => 18k / 100 => 180 servers

### Trade off
- I will go with AP
- No need for consistency because the data ain't changing very fast , we need consistency in systems like banking apps, trading apps etc

# Design Key Value DB (Dynamo DB) #pending

## Uses
- Amazon uses in Add to Cart feature

## Goals
- Scalability
- Decentralization
- Eventual consistency

## Steps
1. Partition
2. Replication
3. Get and Put operation
4. Data Versioning
5. Gossip protocol
6. Merple Tree




# SQL vs NoSQL

1. Structure
2. Nature
3. Scalability
4. Properties

## SQL
- Structured Query Language
- Queries / stores and retrieves data from RDBMS 
- which stores data in a structured form which has tables => rows and columns and there are relations among different tables

### Structure
- Maintains tables, rows, columns
- Pre-determined schema
	- Before inserting data you have to come up with schema / structure of data to be stored
- Relations among different tables

### Nature
- Lets say there is a DB server and there are 3 tables and they are linked
- Nature of SQL is concentrated/centralized, data is stored in a server

### Scalability
- Vertical scaling is possible, well supported
- Horizontal scaling is not supported well

### Properties
- ACID properties make sure of Data Integrity and Consistency
	- Atomicity
	- Consistency
	- Isolation
	- Durability

## NoSQL
- Not Only SQL

### Structure
- Works on Unstructured data
	- Key-Value DB
		- value is Opaque i.e can be anything, so we can not query on the value 
		- Very fast due to searching using key
		- Dynamo DB
	- Document DB
		- key-value DB
		- Inside value it can be JSON or XML
		- search based on key and you can query on the value
		- MongoDB
	- Column wise DB
		- Key-Value DB
		- Inside value we have List<Pair<Column,Value>>
		- Number of Columns is not fixed, it can vary, some can have more columns and some have less
	- Graph DB
		- Data is stored in nodes and edges represent relations
		- Social Network, Recommendation Engine
		- Very very fast for finding relations

### Nature
- Distributed in nature

### Scalability
- Horizontal scaling because data is unstructured and no relations

### Properties
- BASE property
	- Basically available 
		- Highly available DB, data is stored in distributed manner and also replicated across different nodes
	- Safe State
		- State of data can be changed without interaction of user, sync across DB nodes happen, so the stale data is updated
	- Eventual Consistency
		- If you query you might get stale data, but after some time you will get latest data

## When to use SQL and NoSQL ?

1. If we need flexible query functionality => use SQL
	- NoSQL doesn't support complex queries / Joins
2.  If you know in advance which columns you need to query which are not very complex => use NoSQL

3. If data is relational in nature i.e too many dependencies, hierarchies => use SQL
4. Large amount of data / which are changing => NoSQL

5. Data integrity is required i.e you can't afford to lose consistency => use SQL in financial constitutions
6. If you want high availability / performance (search, query) + some inconsistency => NoSQL

# Design Chat Application (WhatsApp, FB, Discord, Slack, Telegram) #pending

## 1. Requirement gathering

### Functional (this should be there / first priority)
1. 1 to 1 send / receive msgs
2. Group message support
3. Last seen / online / offline
4. User Login / Authentication
### Non-Functional (It's good to have this / second priority)
1. scalability
2. Low latency
3. Avalability

## 2. Estimation

- Total user 1 mil
- DAU is 250Mil
- 1 user 10 msgs to 4 people in 1 day
- total msgs per day -> 250Mil * 40 msgs
- 1 msg 100 char
- chat history for 10 years -> 

## Core Concepts

- Peer-to-peer won't scale so we need something else

## 3 ways
1. Polling
	1. Client keeps asking is there a msg for me tcp connection is established, after every response tcp connection is closed
	2. Not scalable
2. Long Polling / Pushing
	1. Client asks Is there any msg for me, server waits threshold minutes and then it responds
	2. Blocking a request thread at server side
	3. Not Scalable
3. Web Socket
	1. Bi directional persistent connection
		1. connection will remain open and only gets closed when one shuts down connection or internet breakage happens


# Design RateLimiter

## Why do we need it?

- To prevent DDOS attacks on the server, due to which all the resources of the server are used up and server goes down

## Algorithms

1. Token bucket
	1. There is bucket which holds tokens
	2. Bucket has capacity which we can define in config file
	3. Bucket has a refiller which will fill the bucket every configured minute
	4. If bucket is full , token is discarded
	5. Whenever req comes
		1. condition is checked "is there a token present?"
			1. If yes this req will consume one token
			2. If no token, req will be denied, 429 HTTP code is returned, excess request 
	6. So for each user, make 3 tokens per minute for post API
2. Leaking bucket
	1. fixed capacity bucket, reqs are processed in a constant rate
	2. Implemented through Queue
	3. When req comes
		1. Is queue full?
			1. If no request is added
			2. Else req is denied and 429 code is sent
	4. Disadv is at sale time constant burst of requests come or for amazon prime not feasible 
3. Fixed window counter
	1. Time line is divided into fixed size window
	2. Each time window is assigned a fixed counter
	3. At end of one window (say 2 min )and start of another window(say 3 min) we might get double the amount of requests
4. Sliding window log
	1. We log the timestamps
	2. Let's say 3 req per minute
	3. We do sliding window on timestamps
	4. Disadv is even if req is denied we log the timestamp
5. Sliding window counter
	1. Fixed window counter + Sliding window log


### Design

![](Pasted_image_20240724120912.png)

### Follow up

- If the Rate Limiters are distributred i.e multiple Rate limitters, client can send req to any one, then how to handle 429 too many requests?
	- Use Redis cache, it is a centralized data source, all rate limitters use a single redis cache
- Redis doesn't maintain atomicity, how to maintain atomicity?
	- We can bring atomicity to Redis, because there's already present, but there will be a bit of latency 


# Design Idempotency Handler / Design Idempotent POST API / Handle Duplicate Request by Idempotency Handler

## Idempotency vs Concurrency

### Concurrency
- One Resource and there are multiple users trying to acquire the resource

### Idempotency
- Idempotency helps us to take care of duplicate requests
- It helps clients to safely retry an operation without worrying about the side effect of an operation
- For example POST request of addToCart multiple times same item
	- First time the row is created
	- Next all the times row shouldn't be created for the same item, instead the counter of that product in cart should increase
- By default GET, PUT, DELETE are idempotent in nature whereas POST is not

## Types
1. Sequential
	1. It means duplicate post requests come one after another
2. Parallel
	1. Duplicate post requests come at the same time

## How to handle ?
- Using Idempotency key (uuid) (universally unique id)
- Client should generate the Idempotency key
- For each different operation new Idempotency key should be generated

## Flow

### Sequential 
1. Generate Idempotency key
2. put it in request header and send it to server
3. Server will validate 
	1. if Idempotency key is not present in header , send 400 validation error
	2. Server will read the idempotency key from DB
		1. If present 
			1. check status
			2. If created , some req is already is getting processed , return 409 (conflict error)
			3. If consumed, don't do anything, return 200
		2. Else it will put an entry in DB table key,status
			1. Each key has a lifecycle created/acquired -> consumed/claimed
			2. after successfully executing request , it will change the status to consumed/claimed from created/acquired
			3. send 201 (resource created) status code

### Parallel
- Use Mutual Exclusion, Lock, using Mutex, Semaphore at the critical section
- Critical section is server reads the id from DB

### Follow up question
- If parallel requests go to different app servers and they have their own DB? By the time DB sync happens (sync takes minutes), 2 rows would have been created
- Answer is use cache
- client <-> server <-> cache <-> DB server
- As Cache sync happens in miliseconds , put lock on cache


# Design High Availability Architecture

- It can be asked in many other forms
	- Design Data Resilient Architecture
	- Design Architecture to achieve 99.999% Availibility
	- Design to avoid Single Point of Failure
	- Active-Passive vs Active-Active Architecture

## Active-Passive

- One Data Center will be Primary / Live / Read & Write 
- The others will be replicas and DR (Disaster Recovery) Data centers
- The App servers of DR Data Centers are connected to Live DB, any req going to DR servers , will be routed towards Live DB
- One directional Sync up happens of DBs
- If Master DB goes down, one of the DR DBs become master

### Disadv
- Oracle, MySQL, Postgres do not support multi master i.e Write to Single node
- Resources are not utilised properly
- Latency issue if any request goes to DR Data center
- If Live DB goes down, re routing and making another DB master takes time, during that time period failure happens

## Active - Active

- Nosql DBs, Cassandra support multi master architecture
- More than one Live DBs
- Bi directional sync up happens

# Distributed Messaging Queue (Kafka, RabbitMQ)

## What is it and why do we need it ?

- We have a producer which produces message , which goes into a queue and consumer consumes it

### Use case
 1. **Asynchronous** 
	1. Our latency gets reduced , because we don't directly communicate , we use an intermediary i.e Queue
2. **Retry capability** 
3. **Pace Matching**
	1. If many publishers are there and sending messages more than the consumer can consume at a time, we should use Messaging queue
	2. For example many cabs have gps tracking on, every 5 min they are sending their location to the server, and if server can handle only 5 at a time but 10 are coming, we use Messaging queue for pace matching

## What is P2P and Pub-Sub

### P2P
- In this a message can be consumed only once via only one consumer
- I.e if consumer1 is consuming it, it won't be available for consumer2

### Pub-Sub
- In this multiple consumers can consume the same message

## How it works?

### Kafka
- Uses Pull based approach i.e consumer keeps polling if there is a new message
#### components
1. Producer
2. Consumer
3. Consumer Group
	1. Every consumer belongs to a consumer group
	2. Any two consumers belonging to the same consumer group can not subscribe to the same partition
	3. If one consumer goes down other can pick up from the other has left, that's why it is used
4. Topic
	1. A broker has many topics
5. Partition
	1. A topic has many partitions
6. Offset
	1. Index of a partition is called an offset
7. Broker
	1. Nothing but a Kafka server
8. Cluster
	1. A group of Brokers is called a cluster
	2. A same topic can be stored in different brokers of a cluster i.e Topic1 P0 in Broker1 and Topic1 P1 in Broker2
	3. To handle the case if a Broker goes down, all the topics have replicas in different brokers
	4. The original ones are called **Leaders** and the replicas are called **Followers**
	5. All the Read / Write requests go to the leader and if it goes down, then the follower will take over
9. Zookeeper
	1. Zookeeper helps in internal communication among the brokers
	2. i.e which broker has which partition and all that info is stored in it
	3. Zookeeper stores consumer info like
		1. consumer of consumer group 1 Topic A partition P0 committed offset 3
		2. committed offset means up to which offset the messages are successfully read
		3. we are storing this info, because If a consumer goes down another consumer picks up the messages looking at the committed offset value
		

![](Pasted_image_20240725163026.png)

#### Flow of sending a message

##### Message
1. Key? : String / int Id (Not mandatory)
2. Value : actual message
3. Topic : Topic Name
4. Partition? : (Not mandatory)

##### How to send message to a particular partition?
- First we check if key is there, using this key we send it to it's respective partition
- If not we check if Partition is provided
- If not we see the topic and assign the message to a partition using round robin format

### RabbitMQ
- Uses Push based approach i.e queue pushes the message to the consumers
- There is a **Producer**
	- Pushes message in Messaging Queue / Topic
- There are multiple **Subscribers**
	- Subscribe to the Messaging Queue / Topic
- This brings Async nature in our codebase
- App server talks with the Messaging queue
- There can be multiple **Exchanges**
- If consumer fails to process a message, the message is requeued a no of times till the limit is reached, then it is put into a **Dead Queue**
### Terminologies
![Architecture](Pasted_image_20240705134712.png)

#### 3 types of Routing keys / Exchange
1. Direct
	1. Routing key == Binding key
	2. Exchange sends the message to only one messaging queue
2. Fan Out
	1. Sends the message to all the queues
	2. subscribers who require this message will work on it else ignore it
3. Topic 
	1. Wildcard matching of the routing key with the binding keys
	2. So the message can go to multiple queues if their binding keys contain the routing key

## What happens when Queue size limit is reached?
- We can use many different brokers for that 

## What happens to messages when queue goes down?
- Nothing happens because the follower takes over

## What happens when consumer goes down ?
- Another consumer from the same group takes over

## What happens when consumer is not able to process a message ?

- We can put retry limit for each message
- If limit is reached the message is put in **Failure Queue / Dead Queue**



# Proxy vs Reverse Proxy

## What is a Proxy Server

- Proxy is what sits between client and server and acts as inermediary
- Proxy can handle requests from multiple clients and asks for data from the server and provides those to the clients.

### Types

1. Forward Proxy
	1. Default proxy
	2. [group of clients] <---> [Forward Proxy] <---> [Internet] <---> [server]
	3. Hides the client from outside world, no server can talk directly to any client
		1. because even if client Ip sends data , proxy intercepts it and sends it on client's behalf
	4. Groups similar request of clients
	5. Caching of requests
	6. Accessing blocked content
	7. Brings security
	8. Dis Adv
		1. Works on Application layer, i.e for each application you have to set up a proxy
2. Reverse Proxy
	1. [group of clients]  <---> [Internet] <---> [Reverse Proxy] <---> [Group of servers]
	2. Example is CDN
	3. Security of servers
		1. Because only proxy IP address is known
		2. DDOS attack preventition
	4. Caching
	5. Less Latency
	6. Load Balancing

## Proxy vs VPN
### Proxy
1. Annonymity
2. Caching
3. Logging

### VPN
1. [client] <--> [VPN Client] <--VPN Tunnel--> [VPN Server] <---> [Server]
2. VPN Client can encrypt / decrypt the data and send it through a safe tunnel


## Reverse Proxy vs Load Balancer
- Reverse Proxy can be a load balancer but load balancer can't be a reverse proxy

## Proxy vs Firewall

- In firewalls there are holes and for each hole we set up rules i.e through which hole which type of data can pass through to the internet
- Firewall also does packet scanning (checks header, port, Ip address of src and dest)
- But Proxy works on application level
- Proxy can act as a firewall also 


# Load Balancer and Different Algorithms

- Main purpose is to properly distribute the load of requests to multiple servers

## Types

### Network LB ( L4 )
- Works at Transport Layer
- TCP Port, UDP port , IP address of src and dest
- Much more faster

#### Algorithms

##### Static
1. Round Robin
	1. Adv
		1. very easy
		2. Equal load to all servers
	2. Dis adv
		1. 2 servers, one with high capacity and low capacity are treated equally
2. Weighted Round Robin
	1. Weight represents capacity of server
	2. When req comes req goes to one server x times to one server having weight x and then y times to another server having weight y
	3. Adv
		1. Low capacity server gets less requests
		2. Easy to implement as weights are static here
	4. Dis adv
		1. If requests have different processing time, then it's possible that the low capacity server might get high processing requests and get overburdened
3. IP Hash
	1. Hash the IP address and map it to some server
	2. Adv
		1. Good for use cases, where same client need to connect to same server
		2. Easy to implement
	3. Dis adv
		1. If clients request is coming through proxy, then all clients will have the same source IP address and this will overload one server
		2. Can't ensure equal distribution
##### Dynamic
1. Least Connection
	1. Check which server has least active connections
	2. Adv
		1. dynamic, so chance of overburdening of server is less
	3. Dis adv
		1. TCP connection can be active but might have no traffic
		2. No difference between low and high capacity server
2. Weighted Least Connection
	1. Calculate the ratio of no. of active connections to its weight and server with minimum ratio gets the request
3. Least Response Time
	1. TTFB is Time to First Byre i.e time interval between sending a request and receiving the response from the server
	2. Pick the server which has less (no. of active connections * Least TTFB)
	3. If clash happens do round robin
	4. Adv
		1. Helps to increase the availability time of servers
	5. Dis adv
		1. Too much computition logic required
		2. TCP connection can be active but have no traffic

### Application LB ( L7 )
- Works at Application layer
- Can read your Header / Session / Data / Response 
- Can Cache also, much more advance


# Distributed Cache and Caching Strategies

## Caching
- Caching is a technique to store frequently used data in a fast access memory rather than accessing data every time from slow access memory
- This makes our system very fast
- It helps to reduce the latency
- It also helps to achieve the fault tolerance
- There are different types of caching present at different layers of the system like
	- Client side caching i.e Browser caching
	- CDN (used to store static data)
	- Load balancer
	- Server side application caching (like Redis etc)

## Distributed Caching

- If we use only one cache for multiple app servers disadvs are:
	1. Scalability
	2. SPF
- In Distributed caching there is a **Cache Pool**, there is a **Cache Client** for each App server, using which they get one Cache server allotted to them
- Cache Client uses Consistent Hashing for allotting the Cache servers


## Caching Strategies

### 1. Cache Aside
- Application first checks the cache.
- If data found in cache, it's called **Cache Hit** and data is returned to client.
- If data is not found in the cache, it's called **Cache Miss**. Application fetches the data from the DB, stores it in the cache and data is returned to the client.
- Adv
	- Good for Read Heavy Apps
	- Even if cache is down, request will not fail, as it will fetch the data from the DB
	- Cache Document data structure can be different than the Data present in the DB
- Dis Advs
	- For new data read, there will always be Cache Miss first, to resolve this we can pre-heat the cache
	- Without appropriate caching during write operation, there is a chance of inconsistency between cache and DB

### 2. Read through Cache
- Application first checks the cache.
- If data is found, it is returned to the client
- Else Cache library itself fetches the data from DB, stores it back into the cache and data is returned to the application
- Adv
	- Good for Read Heavy Applications
	- Logic of fetching the data form DB and updating cache is separated from the application
- Dis adv
	- For new data read there will always be cache-miss
	- cache document structure should be same as the db table
	- without appropriate caching during write operation, there is a chance of inconsistency between cache and DB

### 3. Write Around Cache
- Directly writes data into the DB
- Invalidate the data in the cache
- It doesn't update the cache
- Adv
	- Good for Heavy Read Applications
	- Resolves inconsistency problem between cache and DB
- Dis advs
	- For new data read, there will always be cache miss first
	- If DB is down, write operation will fail
### 4. Write Through Cache
- First write data into the cache
- Then in synchronous manner write data into the DB
- If any operation fails, we need to roll back
- Adv
	- cache and DB have consistent data
	- cache hit chance increases a lot
- Dis advs
	- Alone it is not useful, it will increase latency. (that's why it's always used with Read through or Cache aside cache)
	- 2 phase commit needs to be supported with this, to maintain the transactional property
	- If DB is down write operation will fail
### 5. Write Back ( or Behind) Cache
- First write data into the cache
- Then in async manner write data into the DB
	- For this push the message to queue
	- then get the message from the Queue and write into DB
- Adv
	- Good for write heavy applications
	- Improves the write operation latency, as writing into the DB happens asynchronously
	- Fault tolerance is achieved i.e even if DB fails and Turn Around Time is around 24hrs , the write will still happen as it is queued
	- Gives much better performance when used with read through cache
- Dis advs
	- Even when DB fails, write operation will still work
	- If data is removed from the cache and DB write still not happens, then there is a chance of an issue (it is handled by keeping the TAT of cache little higher like 2 days)


# Distributed Transactions

## 2 Phase Commit
- Transaction Coordinator manages the transactions / participants.
- Every participant knows each other and transaction coordinator knows about all.
- Prepare phase
	- After all the updates in microservices happen, it asks all of them are you ready to commit ?
- Commit phase
	-  If all the services say OK, then it gives order to commit else, it orders for Abort or Rollback

### Issues
1. what if Transaction coordinator fails
2. Participant fails
3. Prepare message / OK message / Abort / Commit message get lost due to above two issues

#### Solution
- Every System has a **log file**
- Prepare msg lost i.e a service didn't get the msg --> participant aborts the transaction / release lock , if after that it receives prepare msg , send back response NO
- If OK message is lost --> TC aborts the transaction
- If commit msg is lost -->blocking period happens, during which the participant thread is blocked , can't do anything else, to resolve this we use 3 Phase commit


## 3 Phase commit (Non Blocking)
1. Prepare phase
2. Pre-commit phase
	1. Whatever decision the Transaction coordinator has taken, it sends to the participants, that in case i go down this is the decision I have taken
3. Commit phase

### What if pre-commit phase fails
- participant asks neighbours has the TC sent you any pre-commit message?
- If not they Abort


## SAGA Pattern
- 2PC and 3PC are Synchronous in nature
- SAGA Pattern is used in a long chain of participants and long transactions

# Database Indexing
- How DBMS determines in which Data Page too store the row, if we have done indexing on a column ?
	- First it inserts the key into B+ tree, then it checks the neighbouring key, to which Data Page it is pointing to, if that Data Page is free it will insert the Row into that Data Page
	- Else DBMS does page splitting, it splits the Data Page into two and inserts equally into both of those pages.
- The way the rows are inserted, they are stored in that order in Data Pages. So if we create index on a column, the keys point to the Data Pages in which they are present, so we need a way to sort the Rows stored in Data Pages, that's why we need the Offset array
- Non-clustered indexing is made on secondary keys, composite keys, we can have many non-clustered index
- Dis adv
	- B+ trees need huge memory
	- B+ trees are stored in index pages, index pages are stored in Data blocks, so we need to manage the index page mapping to Data blocks also
- How searching happens
	- Load index pages that hold the B+ tree
	- search the key
	- find the data page
	- load the data block in memory
	- then search in that

# Concurrency Control in Distributed Systems: Movie Theatre Seat Booking Scenario

## Scenario: Concurrent Requests to Book the Same Movie Theatre Seat

- **Critical Section**: Code section where shared resources (like a seat) are accessed.
- **Synchronized Block**

```java
synchronized(){
    Read Seat Row with ID
    if free:
        change status of seat
        update DB
}
```

- **Problem**: Synchronized blocks work for multi-threading in a single process but won't work in a **distributed system** (multiple systems with multiple processes).

## Distributed Concurrency Control

Concurrency control ensures data consistency across multiple processes in a distributed system. Two main approaches:

### 1. **Optimistic Concurrency Control (OCC)**

- **Assumption**: Conflicts are rare, so data is read without locking.
- **Process**:
    1. **Start Transaction**: Read the data.
    2. **Compute**: Perform operations on fetched data.
    3. **Version Check**: If version matches, commit changes; otherwise, rollback.
- **Strengths**:
    - Higher concurrency.
    - No deadlocks.
- **Weaknesses**:
    - Rollback and retry overhead.
- **Uses**: Read Committed isolation level.

### 2. **Pessimistic Concurrency Control (PCC)**

- **Assumption**: Conflicts are frequent, so data is locked during access.
- **Process**:
    1. **Lock**: Acquire lock before reading/writing data.
    2. **Compute**: Perform operations.
    3. **Unlock**: Release lock after transaction.
- **Strengths**:
    - Prevents conflicts.
- **Weaknesses**:
    - Deadlocks possible.
    - Timeout issues.
- **Uses**: Repeatable Read and Serializable isolation levels.

## Database Transactions for Integrity

Transactions ensure **data integrity** in operations like seat booking. Example:

1. **BEGIN_TRANSACTION**
2. Debit money from Account A.
3. Credit money to Account B.
4. **COMMIT** if successful, **ROLLBACK** if failed.
5. **END_TRANSACTION**

### Types of Database Locks:

1. **Exclusive Lock (X)**: No other transactions can read/write.
2. **Shared Lock (S)**: Multiple transactions can read, but no write allowed.

## Isolation Levels & Locking Strategies

Isolation levels dictate how transactions interact with each other:

|**Isolation Level**|**Dirty Read**|**Non-Repeatable Read**|**Phantom Read**|**Locking Strategy**|
|---|---|---|---|---|
|**Read Uncommitted**|Yes|Yes|Yes|No locks acquired|
|**Read Committed**|No|Yes|Yes|Shared lock on read, exclusive lock on write|
|**Repeatable Read**|No|No|Yes|Shared lock till end, exclusive lock on write|
|**Serializable**|No|No|No|Range lock to prevent phantom reads|

### Definitions:

- **Dirty Read**: Reading uncommitted data from another transaction.
- **Non-Repeatable Read**: Reading different values when reading the same row multiple times.
- **Phantom Read**: Reading different row sets when running the same query multiple times.

## Optimistic Concurrency Control (OCC)

- Uses **Read Committed** isolation level.
- Version numbers are used to check if data has changed before committing.
- **Advantages**:
    - High concurrency.
    - No deadlocks.
- **Disadvantages**:
    - Rollback and retry overhead.

## Pessimistic Concurrency Control (PCC)

- Uses **Repeatable Read** and **Serializable** isolation levels.
- Locks data during transaction to prevent conflicts.
- **Advantages**:
    - Prevents conflicts.
- **Disadvantages**:
    - Possible deadlocks.
    - Timeout and rollback issues.

## Conclusion

For booking seats in a distributed system, use **transactions with appropriate isolation levels** and **optimistic or pessimistic concurrency control** depending on the expected conflict frequency.


/*  
* SCENARIO  
* -------------------  
* Many concurrent request tries to book the same Movie theatre seat  
*  
* CRITICAL SECTION :  
* ---------------------  
* Piece of code where you are trying to access a shared resource  
*  
* USING SYNCHRONIZED BLOCK  
* -----------------------------  
* synchronized(){  
*   Read Seat Row with ID  
*   if free:  
*       change status of seat  
*       update DB  
* }  
*  
* WILL THIS WORK FOR DISTRIBUTED SYSTEM?  
* ----------------------------------------  
* ONE PROCESS CAN HAVE MULTIPLE THREADS, SYNCHRONIZED CAN WORK IN THIS CASE  
* BUT IN DISTRIBUTED SYSTEM THERE CAN BE MULTIPLE SYSTEMS HAVING MANY PROCESSES, SO SYNCHRONIZED BLOCK WON'T WORK  
*  
* USING DISTRIBUTED CONCURRENCY CONTROL  
* -----------------------------------------  
* 1) Optimistic Concurrency Control (OCC)  
* 2) Pessimistic Concurrency Control (PCC)  
*  
* 1) USAGE OF TRANSACTION  
* -------------------------  
* -> Transaction helps us to achieve INTEGRITY. It helps us to avoid Inconsistency in our DB.  
*  
* EX:  
* -----  
* Debit the money from A and Credit the money to B  
*  
* BEGIN_TRANSACTION:  
* ------------------  
* Debit the money from A  
* Credit the money to B  
* If all success:  
*   COMMIT;  
* else  
*   ROLLBACK;  
* END_TRANSACTION  
* ------------------  
*  
* 2) DB Locking  
* ---------------  
* DB Locking makes sure that no other transaction updates the locked rows  
*  
* TYPES  
* --------  
* EXCLUSIVE LOCK (X) -> No other transaction can read/write , nor take shared lock nor exclusive lock  
* SHARED LOCK (S) -> called read lock, only read can happen, other transactions can take shared lock, but no exclusive lock  
*  
* 3) ISOLATION LEVELS  
* -------------------------  
* Isolation Level  | Dirty Read Possible | Non-Repeatable Read Possible | Phantom Read Possible|  
* Read Uncommitted |       Yes           |             Yes              |       Yes            |  Consistency High  
* Read Committed |         No            |             Yes              |       Yes            |      ^  
* Repeatable Read |       No             |              No              |       Yes            |      |  
* Serializable   |       No           |                No              |        No             |   Consistency Low  
*  
* ISOLATION  
* -------------  
* Isolation says that if you have multiple transactions running concurrently, it feels like they are executing alone, each one is independent of each other  
*  
*  
* DIRTY READ  
* -----------  
* If Transaction A is reading the data which is being written by B and not yet committed.  
* If Transaction B does a rollback, data read by A is known as dirty read.  
*  
* Non-Repeatable Read  
* ----------------------  
* If Transaction A reads the same row multiple times and there is a chance that it reads different value  
*  
* Phantom Read  
* -------------------  
* If Transaction A executes same query several times and there is a chance that the rows returned are different.  
*  
*  Isolation Level   | Locking Strategy |  
*  Read Uncommitted  | Read : No Lock acquired  
*                   |  write : No Lock acquired  
*  Read Committed   |  Read : Shared Lock acquired by row and released as soon as Read is done  
*                   |  write: Exclusive lock is acquired by row and kept till end of transaction  
*  Repeatable Read |   Read : Shared Lock acquired and kept till end of transaction  
 *                 |   write: Exclusive lock is acquired and kept till end of transaction *                 |  Even though Repeatable Read prevents previously read rows from being modified or deleted by other transactions, it doesn't prevent new rows from being inserted that match the query conditions.*  Serializable   |   Same as Repeatable read locking strategy + apply range lock and lock is released only at the end of transaction  
*                 | range lock means it will lock nearby rows also  
* SYNTAX  
* ------------  
* SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;  
* BEGIN TRANSACTION;  
*  
* END TRANSACTION;  
*  
*  
* OPTIMISTIC CONCURRENCY CONTROL  
* ------------------------------  
* -> uses Read committed isolation level  
* -> we use Version for each row, when you do any update that version increases  
* -> before doing any update version validation is done, if version read previously is not equal to the current version number, then ROLLBACK happens  
* -> CREATE TRANSACTION -> READ ROW(UNLOCKED TOO) -> COMPUTATION ON FETCHED ROW -> ROW MODIFIED ? -> YES -> ROLLBACK / NO -> UPDATE DB -> COMMIT  
*  
* POINTS TO NOTE  
* ------------------  
* Isolation level used below REPEATABLE READ  
* Much Higher Concurrency  
* No chance of Deadlock  
* In case of conflict, overhead of transaction rollback and retry logic is there  
*  
* PESSIMISTIC CONCURRENCY CONTROL  
* ------------------------------  
* -> uses Repeatable and Serializable isolation levels, Lock is acquired on row and never released till the end of trqnsaction  
* -> DEADLOCK can happen  
* -> T1 reads A, T2 reads B, T1 wants to Write B, T2 wants to write A, both are waiting for the other to release the shared lock, so deadlock happens, they will get aborted and they might have to start again  
* -> CREATE TRANSACTION -> READ ROW(UNLOCKED TOO) -> COMPUTATION ON FETCHED ROW -> ROW MODIFIED ? -> YES -> ROLLBACK / NO -> UPDATE DB -> COMMIT  
*  
* POINTS TO NOTE  
* -----------------  
* Isolation level used Repeatable Read and Serializable read  
* Less concurrency compared to Optimistic  
* Deadlock is possible, then transactions stuck in deadlock are forced to do rollback  
* Putting a long lock, sometimes timeout issue comes and rollback needs to be done  
* */

# Two Phase Locking (2PL)
