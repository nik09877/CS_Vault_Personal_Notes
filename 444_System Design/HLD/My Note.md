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
		- Increase already present DBs capabilities
	- Horizontal