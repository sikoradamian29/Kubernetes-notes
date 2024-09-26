It is a distributed and reliable key value store used by Kubernetes to store all data used to manage the cluster. When you have multiple nodes and multiple masters in the cluster, etcd stores all that information on every node in the cluster in a distributed manner. (Every master node?)

Key-value store keeps information in form of document (or pages) so each individual gets his own document with all related information.

### Regular database

| Name        | Age | Location  | Salary | Grade |
| ----------- | --- | --------- | ------ | ----- |
| John Doe    | 34  | New York  | 5000   |       |
| Dave Smith  | 45  | New York  | 4000   |       |
| Aryan Kumar | 10  | New York  |        | A     |
| Lauren Rob  | 13  | Bangalore |        | C     | 

### Key value store

| Key      | Value    |
| -------- | -------- |
| Name     | John Doe |
| Age      | 34       |
| Location | New York |
| Salary   | 5000     | 

| Key      | Value       |
| -------- | ----------- |
| Name     | Aryan Kumar |
| Age      | 10          |
| Location | New York    |
| Grade    | A           |

##### This way there is no global change to a table, but only a change to a single individual.
##### **Data Encoding**: While etcd itself only stores data in key-value pairs, the values can be complex. Kubernetes uses JSON or Protobuf to encode and store more complex structures. For instance, a Kubernetes object like a Pod is serialized into JSON format before being stored in etcd.

