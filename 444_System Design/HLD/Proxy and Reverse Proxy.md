
# Proxy vs Reverse Proxy

## What is a Proxy Server

- Proxy is what sits between client and server and acts as inermediary
- Proxy can handle requests from multiple clients and asks for data from the server and provides those to the clients.

### Types

1. Forward Proxy
	1. Default proxy
	2. [group of clients] <---> [Forward Proxy] <---> [Internet] <---> [server]
	3. Hides the client from outside world, no server can talk directly to any client
		1. because even if client Ip sends data , proxy intercepts it and sends it on client's behalf
	4. Groups similar request of clients
	5. Caching of requests
	6. Accessing blocked content
	7. Brings security
	8. Dis Adv
		1. Works on Application layer, i.e for each application you have to set up a proxy
2. Reverse Proxy
	1. [group of clients]  <---> [Internet] <---> [Reverse Proxy] <---> [Group of servers]
	2. Example is CDN
	3. Security of servers
		1. Because only proxy IP address is known
		2. DDOS attack preventition
	4. Caching
	5. Less Latency
	6. Load Balancing

## Proxy vs VPN
### Proxy
1. Annonymity
2. Caching
3. Logging

### VPN
1. [client] <--> [VPN Client] <--VPN Tunnel--> [VPN Server] <---> [Server]
2. VPN Client can encrypt / decrypt the data and send it through a safe tunnel


## Reverse Proxy vs Load Balancer
- Reverse Proxy can be a load balancer but load balancer can't be a reverse proxy

## Proxy vs Firewall

- In firewalls there are holes and for each hole we set up rules i.e through which hole which type of data can pass through to the internet
- Firewall also does packet scanning (checks header, port, Ip address of src and dest)
- But Proxy works on application level
- Proxy can act as a firewall also 
