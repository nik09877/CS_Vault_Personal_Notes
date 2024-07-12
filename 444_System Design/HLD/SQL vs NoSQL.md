# SQL vs NoSQL

1. Structure
2. Nature
3. Scalability
4. Properties

## SQL
- Structured Query Language
- Queries / stores and retrieves data from RDBMS 
- which stores data in a structured form which has tables => rows and columns and there are relations among different tables

### Structure
- Maintains tables, rows, columns
- Pre-determined schema
	- Before inserting data you have to come up with schema / structure of data to be stored
- Relations among different tables

### Nature
- Lets say there is a DB server and there are 3 tables and they are linked
- Nature of SQL is concentrated/centralized, data is stored in a server

### Scalability
- Vertical scaling is possible, well supported
- Horizontal scaling is not supported well

### Properties
- ACID properties make sure of Data Integrity and Consistency
	- Atomicity
	- Consistency
	- Isolation
	- Durability

## NoSQL
- Not Only SQL

### Structure
- Works on Unstructured data
	- Key-Value DB
		- value is Opaque i.e can be anything, so we can not query on the value 
		- Very fast due to searching using key
		- Dynamo DB
	- Document DB
		- key-value DB
		- Inside value it can be JSON or XML
		- search based on key and you can query on the value
		- MongoDB
	- Column wise DB
		- Key-Value DB
		- Inside value we have List<Pair<Column,Value>>
		- Number of Columns is not fixed, it can vary, some can have more columns and some have less
	- Graph DB
		- Data is stored in nodes and edges represent relations
		- Social Network, Recommendation Engine
		- Very very fast for finding relations

### Nature
- Distributed in nature

### Scalability
- Horizontal scaling because data is unstructured and no relations

### Properties
- BASE property
	- Basically available 
		- Highly available DB, data is stored in distributed manner and also replicated across different nodes
	- Safe State
		- State of data can be changed without interaction of user, sync across DB nodes happen, so the stale data is updated
	- Eventual Consistency
		- If you query you might get stale data, but after some time you will get latest data

## When to use SQL and NoSQL ?

1. If we need flexible query functionality => use SQL
	- NoSQL doesn't support complex queries / Joins
2.  If you know in advance which columns you need to query which are not very complex => use NoSQL

3. If data is relational in nature i.e too many dependencies, hierarchies => use SQL
4. Large amount of data / which are changing => NoSQL

5. Data integrity is required i.e you can't afford to lose consistency => use SQL in financial constitutions
6. If you want high availability / performance (search, query) + some inconsistency => NoSQL
