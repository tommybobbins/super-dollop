# Application Integration Services Comparison

|Service|What it does|Example Use case|
| --- | --- | --- |
| SQS | Messaging queue, store and forward patterns | Building distributed/decoupled applicaitons|
| SNS | Notification service | Send email notifictions from Cloudwatch alarm|
| Step Functions| Co-ordination of AWS service componenents | Order processing workflow|
| Simple Workflow Service | Support external processes or specialized execution logic| Human enabled workflows, Amazon warehouse (use Step functions instead).|
| Amazon MQ | Replacement for Apache Active MQ/ Rabbit MQ| Support industry tandard APIs and protocols, migrate to AWS|
| Kinesis| Collect process and analyze streaming data | Collect data from IoT devices for later processing|


## Kinesis versus SQS versus SNS

|Kinesis|SQS|SNS|
| --- | --- | --- |
| Consumers pull data | Consumers Pull data | Push data to many subscribers|
| As many consumers as required | Data is deleted after consumption | Pub/Sub |
| Routes related records to same processor| As many consumers as required | Integrates with SQS for fan-out|
| Multiple application can access stream concurrently |No ordering guarantee (except FIFO)| Up to 10^7 subscribers|
| Ordering at the shard level | Messaging semantics | Up to 100,000 topics|
| Can consume records in correct order at later time | Individual message delay | Data is not persisted|
| Must provision throughput | Dynamically scales |No need to provision throughput|


