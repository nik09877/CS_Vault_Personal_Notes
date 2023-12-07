# Basics
## Monoliths vs Micro services
- In Monolith architecture the clients connect to machines which then communicate with databases. It is not mandatory for there to be only one huge machine which is running the entire system. It can horizontally scale.
- Microservice is a single business unit. All data, functions related to a business unit are put into one service. These microservices talk to their own dedicated databases. The clients are connected to a gateway which communicates with the microservices.
- 90% of time for large systems microservice architecture is better in interviews.
### Monolith Adv
1. Good for small teams 
2. There are lesser moving parts and no need to think about how to break down this system. Deployment is easy.
3. Less Duplication of code (like testing)
4. Faster because you are not making any Remote Procedure Call
### Monolith Disadv
1. Nightmare for new dev
2. Code deployment
3. Tight coupling
4. Single Point of Failure
### Microservice Adv
1. Easier to scale (set of services)
2. Easier for new dev
3. Parallel development is easy (decoupling)
### Monolith Disadv
1. Difficult to design
2. If service 1 is talking to only one other service then those services should be merged
3. Easier to know which service is being used more and scale accordingly.

## Horizontal vs Vertical Scaling
- Cloud is a set of computers somebody provides to you (Remote Login)
- The ability to handle more requests by buying 
	- more machines (Horizontal scaling)
	- bigger machines (Vertical scaling) is called scalability

| Horizontal                                            | Vertical                             |
| ----------------------------------------------------- | ------------------------------------ |
| More machines                                         | Huge machine                         |
| Load Balancing required                               | Not required                         |
| Resilient (recover from failure quickly)                                            | Single point of failure              |
| Remote Procedure calls (Network calls) (slower)       | Inter Process communication (faster) |
| Data consistency is real issue (eventual consistency) | Consistent                           |
| Scales well as users increase                         | Hardware limit                       |
 

## Load Balancing
- Server has load and requests are what they need to process
- The concept of taking N servers and balancing the load evenly is called Load Balancing.
- Every request has Request Id -> 0 to M-1 (Uniformly random)
- Load Balancer Hashes it => `h(r1) -> m1 % n` where n is no. of servers and sends it to respective server
- If each servers have `X` requests they will have `X / n` Load and Load Factor is `1 / n`
- What if we need to add more servers?
	- r1 that was previously going to server 2 might go to some other server
	- Cost of adding a new server is 100% reassignment of requests
	- That's why we need Consistence Hashing
## Distributed Systems
### Make a Pizza Shop
###### Focus on 3 things
1. Scalability
2. Fault Tolerance
3. Extensibility
###### Example
- Initially has 1 chef
- How to handle more orders? **(Scaling)**
	- Optimise processes and increase throughput with the same resources which is called vertical scaling
	- Preparing before hand at non peak hours
- Now let's make it **Resilient** (recover from failure quickly).
- What if the chef is sick?
	- Keep backup
	- avoid single point of failure
	- Hire more chefs / resources (horizontal scaling)
- Time for expansion
- Let's say we have 3 chefs (2 are good in making pizza and 1 in garlic bread). On receiving an order which chef should we assign it to?
	- Garlic bread to a team who are specialists in making garlic bread and same for pizza (use microservices)
- What if there is electricity outage in your shop ? **(Fault tolerance)**
	- Set up a whole new shop in another place (backup)
	- Distributed System
	- Fault tolerant
	- quicker responses
- Customer orders a pizza , which pizza shop to route it to ?
	- The central authority (Load Balancer) decides where the request goes, either to pizza shop 1 or 2
- Can it be future proof ? **(Extensibility)**
	- Decoupling everything (separation of concerns)
	- Logging and Metrics calculation (if failure occurs logs help us know what happened when)
## Single Point of Failure
- SPF are those points where the entire system can crash if those points crash.
- Backup services don't make sense, backup databases make sense.
#### How to get rid of SPF?
![](Pasted_image_20231205120213.png)

## Sharding
- Partitioning the data based on certain key attributes is called Database Sharding. (based on userId or location)
- Read and Write performance goes up because each query falls on one shard
- You can use indexing in shards which are different than the attribute used to create shards
	- Find count of people who are in the age range of 20 to 60 in New York
	- Shards are done using cityId and indexing is done using age, so faster read operation
- 2 types
	- Horizontal Partitioning
	- Vertical Partitioning
### Problems
1. Joins across Shards
	- Query goes to 2 different shards => they need to pull out the data => join data across the network => very expensive
2. Fixed no. of shards
	1. Use Hierarchical sharding => Partition a shard into dynamic smaller shards
3. Single point of failure
	1. Use Master Slave Architecture
	2. Write operation always goes to Master and slaves continuously poll the Master to stay updated
	3. If Master fails, slaves choose one Master among themselves

## Service discovery and Heartbeats
- Two way asking `are you alive?`

## Capacity Planning and Estimation: How much data does YouTube store daily?
-

## CDN
- Content Delivery Networks are a bunch of servers spread across the globe to serve information. These networks are available on rent to deliver static content quickly to nearby users.

- Some examples of CDNs are Amazon CloudFront and the Akamai CDN. They are (relatively) cheap to rent and have high availability. They also provide pluggable algorithms to invalidate and fetch data.

# API Design
## API Design Goals
- API is a software contract / documented way to define the expectations and interactions of a piece of code exposed to external users.
- It shows how to interact with your code.
- This includes the parameters, response, errors and API name.
### To Do
1. Naming 
2. Parameter defining of API endpoint functions
3. Giving only the data the user needs, don't stuff all the data in a response
## In Practice
- URL => `www.gkck.com/chat_messaging/Admins/1`
	- chat_messaging => the model which contains the api functions
	- Admins is the function / action
	- 1 refers to the version
- API Should have no side effects => Should do only one thing
- It should be Atomic
- Use Pagination
- Use Fragmentation of response 
- Use Caching (If you don't care about perfect consistency)

# Messaging and Event Handling
## The Message Queue: Problem Statement
- Messaging Queues are widely used in asynchronous systems. Message processing in an asynchronous fashion allows the client to relieve itself from waiting for a task to complete and hence, can do other jobs during that time. It also allows a server to process it's jobs in the order it wants to.
- Messaging Queues provide useful features such as persistence, routing and task management.
- A system having a message queue can move to higher level requirements while abstracting implementation details of message delivery and event handling to the messaging queue.
- The 'queue' is just a name for this data structure. In practice, it could be storing messages using any policy. Some examples of message queues are Kafka and RabbitMQ. They are widely used for various purposes such as command query request segregation (CQRS) and event sourcing.

## Publisher Subscriber Models
- Microservices benefit from loose data coupling, which is provided by a publish-subscribe model. In this model, events are produced by a publishing service and consumed by downstream services.
- Designing the microservice interactions involves event handling and consistency checks. We look into a pub-sub architecture to evaluate its advantages and disadvantages compared to a request-response architecture.
- This type of architecture relies on message queues to ensure event passing. An example would be rabbitMQ or Kafka.
- The architecture is common in real-life scenarios and interviews. If there is no strong consistency guarantee to be made for transactions, an event model is good to use in microservices.

### Here are the main advantages:
1. Decouples a system's services.
2. Easily add subscribers and publishers without informing the other.
3. Converts multiple points of failure to a single point of failure.
4. Interaction logic can be moved to services/ message broker.
### Disadvantages:
1. An extra layer of interaction slows services
2. Cannot be used in systems requiring strong consistency of data
3. Additional cost to the team for redesigning, learning, and maintaining the message queues.
- This model provides the basis for event-driven systems.
## Event Driven Architectures
- Event-Driven Systems pass and persist events. They have evolved from the publisher-subscriber model, and the design has some advantages. Events are immutable and can be replayed to allow the systems to take snapshots of their behavior. This allows services to 'self-heal' as explained in the video.

- A lot of transaction issues are alleviated once idempotency and retrial logic is added to a system. The system can retry messages an infinite number of times to the recipient till there is a message acceptance and acknowledgment from the receiver.

- Event-driven systems are closely related to event sources and CQRS. Greg Young and Martin Fowler have been talking about these systems for a while. Events are persisted in something like a message queue, and hence the responsibility to retrial and persistence is moved to it.

- These abstractions enable the programmer to focus on the business logic of a system and add subscribers to events with minimum coupling with other services. Decoupling the system is one of the advantages of event-driven systems.

- One major disadvantage of this system is that it is difficult to reason about the flow of a request. Services can independently register for an event and consume it without the publisher being aware of it.

- We talk about different applications using an event-driven architecture such as Git and Gaming Systems. We then discuss the advantages and disadvantages of such an architecture (Event Sourcing).

### ADV
1. Availability
2. Easy Roll-back
3. Easy Replacements
4. Transaction guarantee
5. Store intent
### Disadvantages
1. Consistency
2. N/A to Gateways
3. Lesser control
4. compaction
5. Hidden Flow
6. Not easy to move out of this architecture

# Consistency vs Availability
## Distributed Data Consistency
![](Pasted_image_20231207103401.png)
- use Leader-follower architecture which prevents the Two Generals Problem
- If your system is consistent, it suffers from availability and vice versa according to CAP theorum
- 2 phase commit protocol in Leader-Follower architecture
	- prepare (execute all statements of a transaction)
	- commit the transaction

# NoSQL Databases
## Difference between SQL and NoSQL
![](Pasted_image_20231207115732.png)
- NoSQL is a popular database storage method. 
- It keeps data as key value pairs. 
- The advantages and disadvantages of NoSQL compared with RDBMS (which uses SQL) are discussed here, using the Cassandra architecture as an example.
- We talk about sharding, redundancy, load balancing, compaction and some other features in NoSQL databases. This allows them to scale efficiently.
### ADV and Dis adv
- All relevant data are stored together in a document / blob, so insertion and retrieval of data is easier. While on the other hand in SQL, the pointer reaches the required row and starts reading the column data sequentially which takes more time.
- Schema is easily changable. The NoSql doesn't care about Schema, it is flexible. If the address field is null we don't need to include it in the document.
- 