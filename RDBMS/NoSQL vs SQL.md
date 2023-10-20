# NoSQL vs SQL

### SQL

Organize the data into columns and rows within a table , it uses a relational model which fits best for storing structured data. 

Tables are linked through primary keys of every table. 

These database are vertically scalable , which means you can increase the maximum load by increasing the components such as RAM , Disk Space and CPU . 

Note Vertical Scaling is not possible in case of SQL database. 

### NoSQL

It is suitable for structured , semi-structured and unstructured data.

Stores the data is a non-relational format , it does not follow a rigid schema , instead allows more flexible structures to accommodate multiple data types. 

> NoSQL databases are capable of vertical scaling as well as horizontal scaling.
> 

### Advantages

1. **Flexible Schema** : In case of SQL , change the schema is not a easy task. 
2. Better Scaling both horizontal and vertical. 
3. High availability : Due to auto replication feature the changes in a single server persist in other horizontal servers too , in case of failure of one server , other server can still provide the information.
4. **Easy read and insert operations.**  
5. NoSQL databases does not support ACID properties. 

If same data is stored in SQL database and a NoSQL database then NoSQL will require more space as compared to SQL database. 

> Interview Question ? 
Q what is the difference between SQL and NoSQL database.
> 

## Types of databases

Relational Databases

Based on Relational Model 

Commonly use SQL ( Structured Query Language ). 

Scalability Issues ( Horizontal Scaling not possible). 

When the database becomes huge , becomes more complex. 

Object-oriented Database 

Everything is defined in objects forms.

Based on Object Oriented Programming , Paradigm.

Objects can have , table , executable code. 

They communicate via methods. 

Information stored in DB can be retrieved  as an object. 

Hierarchical Database

When we have a information that is based on the concept of Hierarchy, such as employees belonging to a particular department in a big company . 

Disk storage system is also an example of , Hierarchical structure. 

It is easy to use , fast and simple data traversal , Information can be added and deleted easily. 

When the database becomes huge then the traversal in the database becomes very slow, because we always need to start searching from the root node of the hierarchical tree. 

Network Database

Extension to hierarchical database. 

Organized in a Graph Structure. 

Used when we have a situation of multiple parent. 

## Clustering

Combining multiple database instances or nodes into a single logical unit to improve performance, availability and fault tolerance. 

Allows to handle large volume of data , request providing redundancy and availability to the data. 

Load Balancing : 

Preventing only a single database to process and respond to thee request from the multiple users i.e. dividing the load of handling the requests made by user. 

### Partitioning

It is a technique which is used to divide stored database objects into separate servers, for increasing the performance and controllability of the data. 

**Types** 

1. Vertical Partitioning : 
    1. Slicing the relation vertically / column-wise. 
    2. We need to access different servers in order to get the complete tuples. 
2. Horizontal Partitioning :
    1. Slicing the relation horizontally  / row-wise. 
    2. Independent chunks of data tuples are stored in different servers. 

### Sharing

Technique to implement Horizontal Partitioning. 

When we split up our single database instance into multiple instances , and introduce a routing layer to route the particular request to the particular instance.