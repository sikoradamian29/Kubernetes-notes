It's main PostgreSQL directory, where it keeps all it's data, configuration and the rest of the files needed for cluster to work, **besides binary files, because all clusters use the same binaries**. Every cluster has it's own PGData directory.

![[cala_struktura.jpg]]

### - base/\* - Keeps all data files created by users. In base we have a separate directory for every database. Each directory holds all objects of the specified database.
### - global/\* - Keeps definitions of global objects, which are common for every database in the cluster
### - configuration files - postgresql.conf, postgresql.auto.conf (keeps configuration created from postgresql managment, like with alter command), pg_hba.conf (hba - host based authentication)
### - other files - pg_wal/\* (wal - write ahead logs), log/\*
### Even though /ssd/\*, /archive/\* are in different directories than PGData, the PGData directory keeps symbolic links to those directories
