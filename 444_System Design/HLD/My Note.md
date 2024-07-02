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

