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
- Initially has 1 chef
- How to handle more orders?
	- Optimise processes and increase throughput with the same resources which is called vertical scaling
	- Preparing before hand at non peak hours
- Now let's make it resilient (recover from failure quickly).
- What if the chef is sick?
	- Keep backup
	- avoid single point of failure
	- Hire more chefs / resources (horizontal scaling)
- Time for expansion
- Let's say we have 3 chefs (2 are good in making pizza and 1 in garlic bread). On receiving an order which chef should we assign it to?
	- 
