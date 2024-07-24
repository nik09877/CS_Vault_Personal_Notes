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
