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

| Horizontal | Vertical |
| ---------- | -------- |
|            |          |
