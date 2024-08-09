# Monitoring Architecture

| Requirement | Solution |
| --- | --- |
| Need to stream logs from EC2 instances in an Autoscaling group | Cloudwatch Agent |
|Need to collect metrics from EC2 instances with 1 second granularity| Custom metric- High resolution metrics in Cloudwatch Agent|
|Application logs from on prem must be processed by Lambda in real time|Install unified Cloudwatch agent on the servers and use a subscription filter in Cloudwatch to connect to a lambda function|
|Cloudwatch log entries must be transformed with Lambda and then loaded into S3|Kinesis Firehose, transform with Lambda and load into S3.|
|Cloudwatch log entries must be analyzed and centrally stored|Cross account sharing and configure a Kinesis data stream in the security account to collect the log files and then use lambda to analyze and store in S3 bucket|
|Access auditing must be enabled and stored for a minimum of 5 years. Any attempts to modify the log files must be identified|Create a trail in Cloudtrail that stores the data in an S3 bucket and enable log file integrity validation.|
|API Actitivty must be captured from multiple accounts and stored in a central security account.|Use Cloudtrail in each account to record API activity and use cross account access to a security account to store the log files in a central S3 bucket.|
|Trace and debug an application with distributed components|X-ray.|
