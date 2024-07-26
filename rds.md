# RDS

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