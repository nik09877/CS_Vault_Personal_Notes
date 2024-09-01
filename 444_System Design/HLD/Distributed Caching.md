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