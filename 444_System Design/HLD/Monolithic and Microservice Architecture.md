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
