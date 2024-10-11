### WAL (Write-Ahead Log)
![[pliki_wal.jpg]]

Every operation shown in the image above is logged to WAL. It saves original data block, so when it crashes, we can go back to last working version of database. The changed data is first saved to shared_buffers as dirty blocks and then it's saved to data files. Every time a checkpoint is created all the dirty blocks are saved to data files by bgWriter. If the PostgreSQL server crashes before all the dirty blocks are written to the data files, after the restart of the server, PostgreSQL will launch in recovery mode and go back to last checkpoint.