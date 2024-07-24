# Design Rate Limiter

## Why do we need it?

- To prevent DDOS attacks on the server, due to which all the resources of the server are used up and server goes down

## Algorithms

1. Token bucket
	1. There is bucket which holds tokens
	2. Bucket has capacity which we can define in config file
	3. Bucket has a refiller which will fill the bucket every configured minute
	4. If bucket is full , token is discarded
	5. Whenever req comes
		1. condition is checked "is there a token present?"
			1. If yes this req will consume one token
			2. If no token, req will be denied, 429 HTTP code is returned, excess request 
	6. So for each user, make 3 tokens per minute for post API
2. Leaking bucket
	1. fixed capacity bucket, reqs are processed in a constant rate
	2. Implemented through Queue
	3. When req comes
		1. Is queue full?
			1. If no request is added
			2. Else req is denied and 429 code is sent
	4. Disadv is at sale time constant burst of requests come or for amazon prime not feasible 
3. Fixed window counter
	1. Time line is divided into fixed size window
	2. Each time window is assigned a fixed counter
	3. At end of one window (say 2 min )and start of another window(say 3 min) we might get double the amount of requests
4. Sliding window log
	1. We log the timestamps
	2. Let's say 3 req per minute
	3. We do sliding window on timestamps
	4. Disadv is even if req is denied we log the timestamp
5. Sliding window counter
	1. Fixed window counter + Sliding window log


### Design

![](Pasted_image_20240724120912.png)

### Follow up

- If the Rate Limiters are distributred i.e multiple Rate limitters, client can send req to any one, then how to handle 429 too many requests?
	- Use Redis cache, it is a centralized data source, all rate limitters use a single redis cache
- Redis doesn't maintain atomicity, how to maintain atomicity?
	- We can bring atomicity to Redis, because there's already present, but there will be a bit of latency 

