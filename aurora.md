# Aurora

## Aurora Write Forwarding

Can do multi-region active-active writes using write forwarding (which forward any write requests on a replica to the primary) which are then replicated back.


## Oracle RAC

Can migrate Oracle RAC to Aurora PostgresSQL using DMS and SCT

# Using Failover in Amazon Aurora Global Database.

Managed Planned Failovers are now called switchovers.

# Setting RPO for Aurora

With an Aurora PostgreSQL–based global database, you can manage the recovery point objective (RPO) for your Aurora global database by using the rds.global_db_rpo parameter. RPO represents the maximum amount of data that can be lost in the event of an outage.

https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/aurora-global-database-disaster-recovery.html#aurora-global-database-manage-recovery

The RPO is used when your database resumes operations in a new AWS Region after a failover. Aurora evaluates RPO and RPO lag times to commit (or block) transactions on the primary as follows:

- Commits the transaction if at least one secondary DB cluster has an RPO lag time less than the RPO.
- Blocks the transaction if all secondary DB clusters have RPO lag times that are larger than the RPO. It also logs the event to the PostgreSQL log file and emits "wait" events that show the blocked sessions.