# 01/21/2026

Concurrency control is a DBMS feature that coordinates the simultaneous execution of transactions in a multiprocessing database system while preserving data integrity
	the objective is to ensure serializability of transactions in a multi user database environment
concurrency control is important because the simultaneous execution of transactions over a shared database can create several data integrity and consistency problems
the three main problems are lost updates, uncommitted data, and inconsistent retrievals

The lost update problem occurs when two concurrent transactions are updating the same data elements and one of the updates are lost
the uncommitted data problem occurs when two transactions are executed concurrently and the first transaction is rolled back after the second transaction has already accessed the uncommitted data
Inconsistent retrievals occur when a transaction accesses data before and after one or more other transactions finish working with such data

Establishes the order in which th operations are execute within concurrent transactions
	interleaves the execution of database operations to ensure serializability and isolation of tranactions
Bases actions on concurrent control algorithms
	determines appropriate order
create serailization schedule
	serializable schedule interleaved execution of transactions yields the same results as the serial execution of the transactions


locking methods facilitiate the isolation of data items used in concurrently executing transactions
a lock gujanrtees exclusive use of a data ite to a current transaction
the use of locks based on the asumption that conflct between transactions is likely tis usually referedd to asessimisstic locking
a lock manager is responsible for assigning and policing the locks used by the transactinos
MKXCV
	as,dfl,




# February 06, 2026
ACID

# February 06, 2026
ACID

Atomicity
- Once a transaction is started, it must be completed or rolled back, but never partially complete.
Consistency
- Database must begin in a consistent state, and must end in a consistent state.
Isolation
- When a datum is accessed, it may not be accessed by another transaction until the current transaction is complete
Durability
- When a transaction is complete, its effects are permanent, and cannot be rolled back. # February 06, 2026
ACID

Atomicity
- Once a transaction is started, it must be completed or rolled back, but never partially complete.
Consistency
- Database must begin in a consistent state, and must end in a consistent state.
Isolation
- When a datum is accessed, it may not be accessed by another transaction until the current transaction is complete
Durability
- When a transaction is complete, its effects are permanent, and cannot be rolled back. 