# ACID Properties and Transactions .

## Transaction

A unit of work done against the db in a logical sequence.

Sequence is very important in transactions.

A logical unit of work contains multiple SQL statements . Either the result of all those transactions gets completed successfully or if any failure is occurred then it gets rolled back ( all changes has to be undone ) .

### Properties

Every transaction in the database follows these properties.

1. **Atomicity** : Either all the transactions are reflected in the db or none of them. DB maintains a current state of the db as well as a old state of the db , incase of a roll back happens.
2. **Consistency** : Integrity constraints must be maintained before and after the transaction happens.
3. **Isolation** : It controls how the changes are made in the database .
   1. One of the goal of the isolation property is to allow multiple transactions without affecting the execution of each other .
   2. Multiple transaction can happen in the system in isolation.
4. **Durability** : After a transaction is successful then the changes make in the database should persist , even if their is a system failure .
   1. Recovery Management Component takes care of the durability property.
   2. System Logs also takes care of database durability property.

### States of transactions

![transaction-state.png](../assets/transaction-state.png)

1. **Active State** : State where all the read write operations takes place, If they execute without any error then they go to the partially committed state . Any Failure occurs then system goes to the Failed State.
2. **Partially Committed State** : After the successful read/write operation the changes are made to a local buffer first. If changes made are permanent then the system is moved to the committed state , if any failure occurs then system goes to the failed state.
3. **Committed State** : When a system is moved to committed state then all the changes made to duration the transactions cannot be roll-backed .
4. **Failed State** : When any system failure occurs then the system can only roll back to previous state .
5. **Aborted State** : All the previously done changes stored in the local buffer are reversed to a check point .

## Shadow Copy Scheme

1. Based on making copies of DB.
2. A pointer called dB_pointer , maintained on the disk , which at any instant points to the current copy of the DB.
3. Transaction that wants to update the DB , first create its copy in the temporary memory.
4. All the updates are made on the new copy of the DB stored in the temporary location , the original copy is left un-touched.
5. If at any point the , transaction is aborted then he new temporary copy the db is deleted and the original copy is restored .

- if Transaction Succeeded
  OS makes sure that all the pages of the new copy of db is written to the disk.
  DB system updates the db-pointer to point to the new copy of the db.
  New copy is now the current copy of the database.
  The Old copy is deleted from the memory.
  Transaction is said to be COMMITED when the db_pointer is updated and written to the disk.
- Transaction can be aborted by just deleting the new copy of the db.
  Hence either , all updates are reflected or none.

The dB_pointer lies only on a single sector , because in case of any Updation to the dB_pointer is a atomic operation.

RMC ( Recovery Mechanism Component ) supports atomicity and durability of the database.

## Log Based Recovery

Logs are the sequence of records . Logs are stored in a stable storage , so that in case of failure , then they can be recovered easily .

Any operation done in db is recorded in the log.

Logs are stored in the db , before the actual transaction takes place.

### Deferred DB Modifications

1. Deferring all the DB transactions by writing them in logs and executing one by one after reading the final action has been executed.
2. Logs are used to execute the deferred commands once the transaction is completed.
3. If the system crashes before the T completes then the all the information logs are ignored ( that's how atomicity is maintained ).

$$
 <   { T  }_{ 0  }  VNv >
$$

## Immediate DB Modifications

1. DB modifications done , while the Transaction is in active state.
2. DB modifications written by active T are uncommitted transactions .
3. In case of system failure the system uses the old value field to update the modified value.

$$
<   { T  }_{ 0  }  VOvNv >   
$$

## Indexing

Indexing is an technique to optimize the performance of the database by decreasing the number of disk access required when a query is being processed.

It is a type of data structure which used to access the original database quickly.

**Search Key** : Contains the primary key or the candidate key of the table.

**Data Reference** : Pointer heading to the actual block location of the key stored in the index data structure.

Index file is always sorted.

| Sparse Indexing | Dense Indexing |
| --------------- | -------------- |

| When each value in the index data structure represents a block in the actual storage table.
Indexing is created for some of the records. | When each value in the index data structure represents a unique tuple in the actual storage table.
Indexing is created for every of the records. |

Types of Indexing

1. Primary Indexing

   Criteria : Ordered File , has only Key value attribute .

   These criteria are important for applying primary indexing.

   Generally , it uses sparse indexing.

2. Clustered Indexing

Criteria : Ordered File , has only Non key value attribute .

Because of duplicate values in the tables we may have at the time complexity of the block hanker .

Block hanker pointer keeps the track of the duplicated values present in some other block

it also uses sparse indexing.

1.  Secondary Indexing

    Used when we have to search the data base using other attribute values , other than the key value used by primary indexing.

    There are two types

    1.  Key : Used when the attribute have unique values , Dense indexing is made for each index key value is made in the index table , to uniquely identify that attribute.
    2.  Non Key : Used when the attribute we are about to search has some duplicate values , in that case for each duplicate value is grouped into a intermediate table the value to that particular group is indexed to the original index table.  
        it contains the combination of dense and sparse indexing.
            From index table → intermediate table ( Sparse Indexing ) → original table ( Dense Indexing ) .
