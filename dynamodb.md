# DynamoDB

- Fully managed serverless NoSQL
- KV-store/document store
- 400KB
- RCU/WCU
- Push button scaling
- TTL
- Provisioned RCU/WCU can still have auto-scaling enabled!
- DDB-IA is an option
- DDB Key, KMS, CMK

|DDB Feature|Benefit|
| --- | --- | 
|Serverless|Fully managed, fault tolerant service|
|HA|99.99% SLA- 99.999% for Global tables|
|NoSQL|Flexible schema, data can be poorly structured or unpredictable.|
|Horizontal Scaling|Push button or Auto scaling|
|Streams|Capture a time ordered sequence of item level modifications to a DDB table and store for 24 hours. Often used with lambda and KCL.|
|DAX|Fully managed in-memory cache increases performance.|
|Transaction options|Strongly consistent or eventually consistent reads/ACID transactions|
|Global Tables| Full managed multi-region, multi-master.|


## DDB Streams

- Application Inserts/Updates/Deletes item.
- A record is written to DDB stream.
- A Lambda function is triggered from the stream.
- Lambda-> CW Logs as an example.
- DDB Stream is a time-ordered sequence of item level modifications, stored for up to 24 hours. 
- KEYS_ONLY - Only the key attributes of the modified item.
- NEW_IMAGE - Entire item as it was after it was modified.
- OLD_IMAGE - Entire item before it was modified.
- NEW_AND_OLD_IMAGES - Both NEW_IMAGE and OLD_IMAGE.

## DAX

- READ PERFORMANCE improvement (not writes).
- DAX is actually running in VPC (on EC2!), choose an instance type.
- Cache's data in memory
- Add a SG and IAM Role.
- Optimized for DDB.
- DAX does not support lazy loading, uses write through caching.
- Elasticache you have more management overhead.

## DDB Global Tables

- Async replication between regions (uses DDB Streams under the covers)
- Multi-region, multi-Active.

