# RDS

## Security

- Encryption at rest - AES256.
- TLS enabled.
- Public or Private IP.
- RDS and SQL server can use TDE (may have performance impact).
- KMS to manage encryption keys.
- Encrypted replicas of encrypted databases etc.

## Promotion

- Read Replicas can be manually promoted to a standalone database instance for RDS MySQL
- Read Replicas for Aurora MySQL can be promoted to the primary instance
- Primary and standby DB instances are upgraded at the same time for RDS MySQL Multi-AZ. 
- All instances are upgraded at the same time for Aurora MySQL

## Oracle to Aurora Migration

Use Database migration service (DMS)

- Configure DMS data validation on the migration task so it can compare the source and target data for the DMS task and report any mismatches.
- AWS DMS data validation ensures the data has migrated accurately from the source to the target. 
- DMS compares the source and target records and then reports any mismatches. 
- For a CDC-enabled task, AWS DMS compares the incremental changes and reports any mismatches.
- As part of data validation, DMS compares each row in the source with its corresponding row at the target and verifies that those rows contain the same data. 
- DMS issues appropriate queries to retrieve the data. These queries consume additional resources at the source and the target as well as additional network resources.

## Aurora

- 64TB
- Point in time recovery
- MySQL and Postgres
- Aurora replicas (in region read-scaling max 15) and MySQL read-replicas (cross region cluster max 5). Each MySQL read replica can have 15 aurora replicas.
- Global database - Cross region cluster with read-scaling (Fast replication/Low latency read). 
- Multi-master (write forwarding). Scales out writes within a region.
- Serverless, does not support read replicas or public IPs. Supports VPC or DX - not VPN!
- Aurora replication is ms, no impact on primary, MySQL replica is seconds, heavier on primary.
- Aurora replication is In-region, MySQL replication can be X-Region.
- Aurora replication promotion for failover, no data loss, MySQL possibly minutes of data loss.
- Aurora replication - automated failover, no support for replication delay, or different data schemas.


## When not to use RDS

|Requirement|More suitable service|
| --- | --- | 
|BLOBs|S3|
|Automated Scalability|DynamoDB|
|Name/Value Data structure| DynamoDB|
|Data not structured or unpredicatable| DynamoDB|
|SAP HANA|EC2|
|Complete control, patching, login|EC2|


