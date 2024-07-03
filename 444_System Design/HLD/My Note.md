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
	1. Database per service
	2. Shared database
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
3. CQRS

##### Strangler Pattern
- Used when we need to refactor a monolithic service to microservice
- We slowly slowly strangle the monolithic service. How?
	- We don't completely convert the monolithic to microservices at once
	- We initially route 10% API traffic to microservice and 90% to monolithic
	- Then after refactoring some more modules, we increase the API traffic for microservice and we keep on doing it till the API traffic of microservice is 100% and for monolithic 0%

##### Saga Pattern
- 