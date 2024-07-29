# Serverless Architecture Patterns

| Requirement | Solution |
| --- | --- |
| Application includes EC2 and RDS. Spikes in traffic causing writes to be dropped by RDS | SQS queue below EC2, use lambda to process records in the queue and write to RDS |
| Migrate decoupled on-premise web app. Users upload files and processing tier stores in NFS filesystem. Should scale dynamically | EC2 instances, SQS and EFS. Use Autoscaling to scale and manage the processing tier based on the SQS queue length. |
| Lambda function execution time has increased significantly with the number of records to process has increased. | Optimize execution time by increasing memory available to the function which will increase the CPU.|
| API Gateway forwards streaming data to AWS Lambda to process and TooManyRequestsException is experienced | Send the data to Kinesis data stream and then configure lambda to process in batches|
|Migrating app with highly variable load to AWS. Must be decoupled and orders must be processed in the order they are received| SQS FIO queue.|
|Company needs to process large volume of media files with lambda which takes 2+ hours. Need to optimize the time and automate the whole process.|Configure a lambda function to write jobs to a queue. Configure the queue as input to step functions which will co-ordinate multiple functions to process in parallel.|
|Objects uploaded to an S3 bucket must be processed by Lambda| Use S3 event source notificatios to trigger a lambda function.|
|Company requires API events that involve the root user to be captured in a third party ticketing system | Create a cloudtrail trail and an eventbridge rule that looks for API events that involve root, put events on an SQS queue, process queue and write to 3rd party using lambda.|
|Legacy application uses batch scripts that process data and pass on to the next script. This is complex and difficult to maintain| Step functions and Lambda|
|Lambda processes objects created in bucket. Large volumes of objects can be uploaded. Must ensure function does not affect other critical functions|Configure reserved concurrency to set the maximum limit for the function. Monitor critical functions Cloudwatch alarms for the Throttles Lambda metric.|
|EC2 instance processes images using Javascript code and stores in S3. Load is highly variable. Needs a more cost effective solution|Replace EC2 with lambda.|
|Solutions architect needs to update Lamdba function code using canary|API Gateway weights to Lambda function aliases.|
|API Gateway REST API. Just gone global and performance has suffered.|Convert API to an edge optimized API to optimize for the global user base (uses cloudfront point of presence).|
|API Gateway + Lambda - many requests fail, no errors in Lambda| Throttle limit could be too low. Increase throttle limit in API GW.|
|Need to ensure only authorized IAM users can access REST API on API Gateway|Set authorization to AWS_IAM for API Gateway method. Grant execute api:Invoke permissions in the IAM policy.|