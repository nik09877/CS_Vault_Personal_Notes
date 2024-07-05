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
				- one shard might get filled , so we need to do sharding of this shard, tree like structure, so use consistent hashing
				- Join is difficult, so denormalize it
