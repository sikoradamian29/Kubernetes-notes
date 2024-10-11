## Physical Backup
PostgreSQL does not allow making a backup of a single database, you have to backup the whole cluster, so if you have 3 databases, where 2 are 50GB in size and one is 20TB, then you have to make a backup of size 20.1TB to restore a database of 50GB. But it allows restoring database to selected point in time.

## Logical Backup
Logical backup allows creating a backup of single database, but doesn't allow restoring to selected point in time.