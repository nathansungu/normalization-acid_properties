# Normalization And Acid Properties

## Normalization
Database normalization is the process of organizing the attributes of the database to reduce or eliminate data redundancy 

 **Redundancy** -having the same data but at different places.

Normalization generally involves splitting a table into multiple ones which must be linked each time a query is made requiring data from the split tables.

### Reasons For Normalization
- It eliminates redundant data.
- Flexibility: Normalized databases are more flexible when it comes to accommodating changes in data requirements or business rules.
- Saves up on disck space.
- Increased performance.
- Improved data integrity and consistency.
- database structure is clearer and easier to understand.


### Database Normalization Concepts
The elementary concepts used in database normalization are:

- Keys. Column attributes that identify a database record uniquely.
- Functional Dependencies. Constraints between two attributes in a relation.
- Normal Forms. Steps to accomplish a certain quality of a database.

### Types of Normalization

1. **First Normal Form (1NF)**: In the 1NF stage, each column in a table is unique, with no repetition of groups of data. Here, each entry has a unique identifier known as a primary key.

### example
<b>Consider an unnormalized table that stores customer orders:</b>

|orderId| customer | products
|-------|----------|-------------------------|
|1      |John      |Apples, Bananas, Oranges |
|2      | James    |Grapes, Strawberries     |

### first nomalization
|orderId| customer | products
|-------|----------|-------------------------|
|1      |John      |Apples                   |
|1      |John      |Bananas                  |
|1      |John      |Oranges                  |
|2      |James     |Grapes                   |
|2      |James     | Strawberries            |

Now, each cell contains an atomic value, and the table is in 1NF.


2. **Second Normal Form (2NF)**: Building upon 1NF, at this stage, all non-key attributes are fully functionally dependent on the primary key. In other words, the non-key columns in the table should rely entirely on each candidate key.

Consider a table that stores information about students and their courses:

|StudentID	    |CourseID	 |CourseName	|Instructor|
|---------------|------------|--------------|-----------|
|1	            |101         |Math	        |Prof. Smith|
|1	            |102         |Physics   	|Prof. Johnson|
|2              |101	     |Math	        |Prof. Smith|
|3	            |103         |History       |Prof. Davis|

This table violates 2NF because the Instructor attribute depends on both StudentID and CourseID. To achieve 2NF, we split the table into two separate tables:

Students Table:

|StudentID|	StudentName|
|---------|------------|
|1  	  |John        |
|2        |Alice       |
|3	      |Bob         |

Courses Table:

|CourseID   |	CourseName	|Instructor|
|-----------|---------------|-----------|
|101	    |Math	        |Prof. Smith|
|102        |Physics        |Prof. Johnson|
|103        |History        |Prof. Davis|

Now, the Instructor attribute depends only on the CourseID, and the table is in 2NF.





3. **Third Normal Form (3NF)**: 
This stage takes care of transitive functional dependencies.  A table is in 3NF if it’s in 2NF and all non-key attributes are functionally dependent on the primary key, but not on other non-key attributes.

Consider a table that stores information about employees and their projects:

|EmployeeID|	ProjectID|	ProjectName	|Manager|
|----------|-------------|--------------|-------|
|1	|101|	ProjectA|John|
|1|	102	|ProjectB|	Alice|
|2	|101|	ProjectA|	John|
|3|	103	|ProjectC	|Bob|

This table violates 3NF because the Manager attribute depends on the EmployeeID, not directly on the primary key. To bring it to 3NF, we split the table into two separate tables:

Employees Table:

|EmployeeID	|EmployeeName|
|-----------|------------|
|1|	John|
|2|	Alice|
|3|	Bob|

Projects Table:

|ProjectID|	ProjectName|
|---------|------------|
|101	|ProjectA|
|102	|ProjectB|
|103	|ProjectC|

EmployeeProjects Table:

|EmployeeID|	ProjectID|
|----------|--------------|
|1|	101|
|1|	102|
|2|101|
|3|	103|

Now, the Manager attribute depends on the ProjectID, and the table is in 3NF.

4. BCNF <br> In DBMS, often known as 3.5NF, is a higher level of normalisation than the third normal form (3NF). It is based on functional dependencies between attributes in a relation.  

    1. It should already follow the properties of 3NF 

    2.  A must be a super key or candidate key for a functional dependency.  
    

# ACID PROPERTY

- ***A*** - Atomicty 
- ***C*** - Consistency
- ***I*** - Isolation 
- ***D*** - Durability

These key properties define how a transaction should be processed in a reliable and predictable manner, ensuring that the database remains consistent, even in cases of failures or concurrent accesses.

A` transaction `in DBMS refers to a sequence of operations performed as a single unit of work.

1. <b>Atomicity</b><br>
Atomicity is also called an “All or Nothing” rule.
Ensures that all the operations in a transaction must be either successfully completed or aborted.In Atomicity, there are only two possibilities of the transaction – commit everything or abort everything. When aborted, no changes should be reflected in the database is taken care of by the Atomicity property.<br><br>
Example<br>
Sending Ksh 5, 000 on Mpesa to a friend, your account must be debited and credited to the receiver else the transaction will fail.

1. <b>Consistency</b><br>
Consistency property ensures that the value should be consistent and always correct. When there is a change in the database, data integrity should be maintained. This means the database must be consistent before and after the transaction.
<br><br>Example<br>
Tony and John have $100 and $200 in their bank accounts respectively. The total of their amount is $300. So, even after the thousands of transactions between them, the total amount should remain $300. If any problem occurs, like system failure, the total amount must not change. Otherwise, we can say the database is not consistent.

1. <b>Isolation </b><br>
Ensures that no two transactions of the same database interfere with each other. If two transactions are running concurrently on the same database, the second transaction must not read the values from the database until the first transaction is completed.<br><br>Example<br>With three bank accounts of Tom, John, and Ross with the amount $100, $200, and $500.<br>
Now, Ross needs to send $100 to Tom and $200 to John. Here, we have two independent transactions that must not interfere with each other.<br>
When the first transaction is completed (After sending $100 to Tom), Ross will have $400 in his account, and then he will send $200 to John and end up with $200.

1. <b>Durability</b><br>
Ensures that the changes after transaction completion should persist forever and must be available in the future.<br>
After successfully transferring money from Account A to Account B, the changes are stored on disk. Even if there is a crash immediately after the commit, the transfer details will still be intact when the system recovers, ensuring durability.
