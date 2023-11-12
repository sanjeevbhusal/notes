
Mongodb is a document database. This means every record stored inside mongodb is treated as a standalone document. 

However, you cannot put whatever you want in that document. That document stores data in a JSON format.  There will be keys and values. Values can be integer, string, array, links to other documents etc.

![[Pasted image 20231112100831.png]]


## Advantages of document schema

Since a value can refer to another document, this eliminates the need for join operations like SQL databases. You could store a document with blog information with fields such as title, content, created date etc. In case of SQL databases, you would also store author_id which will be a foreign key to id field in the User table. In case of mongodb, you can store a field called author which point to the document storing the actual author itself. 

Since, each document is a different entity, you could store different key value pairs. This means there is no schema to be defined beforehand. Hence, they are more flexible than  SQL databases.

Mongodb is also extremely fast due to less Input/Output operations. Since a document can contain a field which value is another document, it reduces the read time needed for JOIN operations in relational databases. 

Mongodb also supports indexes which lets it speed up a query.


## Collection

MongoDB stores documents inside a collection. A collection is similar to table in a relational database. 


## Database

A Database in Mongodb stores one or more collection.


## High availability

Mongodb can store the same data across various nodes. This increases data redundancy and provides high availability. This replication technique is called replica set. 

A replica set is a collection of computers/nodes running mongodb which store the same data.


## Horizontal Scalability

Horizontal Scalability refers to the ability to scale a software by provisioning more nodes/computers instead of increasing the current computers capability.

Mongodb uses a technique called Sharding, which distributes data across many nodes.


## Data Insertion

When you insert a document 