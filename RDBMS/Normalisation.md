# Normalisation

**Functional Dependency :** is a constraint that determines the relationship of one single attribute or a set of attributes in database management system. 

A → B

means that A is determinant and B is dependent. 

Types of Functional Dependency : 

1. Trivial FD : A →  B. where B is a subset of A. 
2. Non-Trivial FD : A → B where B is not a subset of A. 

 Why Normalisation 

To avoid redundancy in the DB , not to store redundant data.

If we have redundant data in db : 

1. Insertion Anomalies.
    1. When a certain data , can not be inserted into the DB due to the presence of the other data.  
2. Deletion Anomalies.
    1. When a deletion in data , results in the unintended loss of some other important data. 
3. Updation Anomalies. 
    1. When a update of a single data attribute requires multiple rows to be updated. 

Due to these anomalies the size of the db increases and the performance of the db is also compromised. 

In Normalisation we should decompose the tables in the db until we reach a SRP ( Single Responsibility Principle ). 

If we add some attribute to the candidate key then it becomes a super key. 

**Prime attribute** : It is the key that is used to make the primary key.

**Non-prime attribute** : All the key that are not the part of candidate key.

## Normal Forms

1. 1NF 
    1. Every cell should have atomic values ( Single values ). 
2. 2NF
    1. Relation must be in 1NF. 
    2. Their should be no partial dependency .
        1. All non-prime attributes should be fully dependent on the primary key attribute.
        2. A non - prime attribute should never be dependent on prime attributes ( should be dependent to primary key only ) . 
3. 3NF 
    1. Relation must be in 2NF.
    2. No Transitivity dependency should exist. 
        1. Non - prime attribute should not be dependent  on/or derive   Non - prime attribute ( it may leads to redundant data in database ). 
4. BCNF
    1. Relation must be in 3NF.
    2. IF A→B , then A must be a super key.
        1. We must not derive prime attribute from any prime or non - prime attribute . 

## Attribute closure

It can be defined as the set of all those attributes that can be functionally determined by it. 

Denoted by $F^+$.