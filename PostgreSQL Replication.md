PostgreSQL allows creating a replica, a server which will contain a copy of data, from the primary server. We can create physical and logical replication.

### WAL shipping
Method of replication which will replicate the server, every time a WAL file is archived. Which creates 1:1 copy of the primary server, although the primary server does not know of it's existence.

### Logical replication
Only replicated dml operations, like insert delete update. For example, when we want to add a column to the primary server, we have to first add it to replica, and then to the primary, so when we run logical replication it will know where to insert the data. 

### Physical replication with streaming
Every time a WAL file is saved, it's transferred to the replica to be restored there. There are two options. Synchronous and Asynchronous. In synchronous the primary server waits for the replica to get the changes before commiting them, in asynchronous it goes on without waiting.