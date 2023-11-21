# Interview Questions SQL

Q Differentiate between DBMS and RDBMS ? 

A : DBMS is a software that is used to create , maintain and define a database and provide controlled access to database , where as RDBMS we store , maintain and define the database in the form of tables only. 

Q What is Primary Key ? 

A :  It is the group  or column with-in the relation that uniquely identifies each rows of data in that relation. 

Q What is Foreign Key ? 

A : It is a column or a group of columns of one table , that refers to the primary key  of another table. 
The table with the foreign key is called the child table and the table with the primary key is called parent table. 
It is used to maintain referential integrity in the database. 

Q What are Constraints & their types ? 

A :  **SQL Constraints** 

To specify the rules for the data that will be stored in the database. 

**NOT NULL** 

To specify that the column does not have null values. 

**UNIQUE** 

To specify that the column will only have different values. 

**PRIMARY KEY** 

NULL NULL + UNIQUE 

**CHECK** 

To check specific condition for each entry in a column. 

**DEFAULT** 

Sets a default value of column when no value is set. 

Q Explain different type of SQL commands ? 

A : Data Definition Commands 

Data Manipulation Commands 

Data Control Commands 

Transaction Control Language 

Constraints. 

Q Difference between Delete, Drop, Truncate ?

A : Delete : Removes rows from the table , single or multiple ( DML ) , it can be rolled back. 

Drop : Used to drop table or database ( DDL ). 

Truncate : Removes row from the table , single or multiple , it can’t be rolled back. ( DDL ). 

## All types of keys in DBMS

**Candidate key** : It is the set of all possible keys for a given relation.

**Composite key** : It is the combination of two or more columns in a table that can be used to uniquely identify each row..  

**Entity** : It is represented by rectangular shape , were as week entity is represented by double boundary rectangular shape. 

In ER diagram to total participation is presented by double lines between the entities. 

A entity without any primary attribute is called a weak entity. 

### Relational algebra

It is a procedural query language, it give us step by step process to obtain the result of the query. 

It uses operators to perform queries.