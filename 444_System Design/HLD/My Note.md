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
4. Property

