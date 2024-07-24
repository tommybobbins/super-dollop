# Kinesis Data Firehose

Load streams into S3, Redshift, Elasticsearch, Splunk

- No Admin
- Autoscaling
- Serverless
- Pay for Data Flow

## Sources

- Kinesis Data Streams
- SDK
- Cloudwatch
- Kinesis Agent
- AWS IoT

## Destinations

- S3 
- Redshift
- Elasticsearch/Opensearch (ES/OS)
- Splunk etc.

## Use Case - centralized logging

You can configure Amazon Kinesis Data Firehose to aggregate and collate CloudWatch Logs from different AWS accounts and receive their log events in a centralized logging AWS Account (this is known as cross-account data sharing) by using a CloudWatch Logs destination and then creating a Subscription Filter. This log event data can be read from a centralized Amazon Kinesis Firehose delivery stream to perform downstream processing and analysis.

You can collaborate with an owner of a different AWS account and receive their log events on your AWS resources, such as an Amazon Kinesis or Amazon Kinesis Data Firehose stream (this is known as cross-account data sharing). You can use a subscription filter with Kinesis Streams, Lambda, or Kinesis Data Firehose. Logs that are sent to a receiving service through a subscription filter are Base64 encoded and compressed with the gzip format.