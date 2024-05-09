
Transaction in database means persisting a set of changes together or discarding all of them. If there are 5 database queries to make, either all 5 of them will be persisted or none of them will.  
This is helpful when you want to make sure all the queries have been successful. If any query is unsucessful, you would rather have all of the successful ones revert. 

Example: In a banking system while moving money from account A to account B, you usually do 2 queries. 
- First query: Deduct x amount of money from account A
- Second query: Add x amount of money to account B. 

If first query succeeds but second fails, you would deduct the money from account A but not add it to account B. In this case, you should revert the deducted money of account A. If you run both these queries within the transaction, the database will only be updated if both of them run successfully.

When you are inside a transaction, all the changes from the queries will only be stored in some temporary storage and not persisted to the permanent location where the data is stored. If the transaction fails, the storage is simply dropped. If the transaction succeeds, the data in temporary storage will be persisted in the permanent location where the data is stored.


**Concurrency Issue in Database**

Lets take the same banking example as above. In the backend, you will first check if account A has more money than what is requested to be transfered to account B. If not, the backend will reject the request. 

![[Pasted image 20240509140353.png]]


If the balance is greater than the amount, the code proceeds forward. We then deduct the balance from account A and add it to account B. 

![[Pasted image 20240509140441.png]]

Lets imagine we send 2 api calls at the same time to the above `/transfer` endpoint. Lets assume account A has enough balance to send to account B.

The first api call will proceed with the balance check condition. The e