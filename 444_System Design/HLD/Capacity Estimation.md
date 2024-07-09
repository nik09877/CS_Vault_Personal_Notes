# Back-of-the-envelope Estimation 

- It is what drives your design decisions
- Using this we determine if we need load balancers or caches or CDNs etc
- For estimation use numbers multiplied by 10 i.e 430Mil, 3Bil etc

## Cheat sheet 1

|          | Traffic    | Storage |
| -------- | ---------- | ------- |
| 3 zeros  | Thousand   | KB      |
| 6 zeros  | Million    | MB      |
| 9 zeros  | Billion    | GB      |
| 12 zeros | Trillion   | TB      |
| 15 zeros | Quadrillion | PB      |

- Char -> 2 bytes ASCII /  (1byte) Unicode
- Long / Double -> 8 Bytes
- Image -> 300KB 

## Cheat Sheet 2

- X Mil user * Y Mb size => XY TB Storage

## Which things to estimate
1. No. of servers
2. RAM
3. Storage Capacity
4. Trade off using CAP theorum

## Estimation of Facebook

### 1. Traffic Estimation

- Total Users : 1 Billion
- DAU (Daily active users) : 25% => 250 Million Users
- Requests per day
	- one user => 5 Read + 2 Write requests
	- 250 Mil => 250 * 7 Mil requests per day
	- 1 day = 86400 seconds = 100000 seconds = 1 lakh
	- Requests per second 
		- (250 * 7 Mil) /  100000 = 18k requests per second

### Storage Estimation

- Every user does 2 posts 
- Each post 250 characters
- 10% of users are uploading 1 image
- 1 image = 300KB
- 1 post => 250 chars => 500 Bytes
	- 2 posts => 1KB
	- 250 Mil users => 250Mil * 1KB = 250GB per day
	- similarly do for image 8TB
- We want to store for 5 years
	- 5 years = 2000 days
	- 1 day => 8TB / 250GB
	- 2000 days => 16 PB for image and 500TB 

### RAM Estimation

- For each user we are storing last 5 posts in cache
- 1 post = 500Bytes 
	- 5 posts = 2500Bytes = 3KB
- 250 Mil Users * 3 KB = 750 GB
- 75GB RAM= 1 server
	- 750DB RAM = 10 server will have cache

### Latency
- 95% time = 500ms per request
- 1 second = 2 * 500 ms => 2requests
- 1 server = 50 threads => 100 requests per second
- 18k requests => 18k / 100 => 180 servers

### Trade off
- I will go with AP
- No need for consistency because the data ain't changing very fast , we need consistency in systems like banking apps, trading apps etc