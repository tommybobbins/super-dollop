# Eventbridge

## Event Sources

- AWS Services
- Custom Apps
- SaaS Apps

## Targets

- Lambda
- Kinesis
- SNS

## Example
Look for EC2 termination to trigger an SNS event->Email.
CloudTrail->S3:PutBucketPolicy->Eventbridge->SNS->Email.

Trigger SSM run command to patch Windows server when the Instance State reaches Runnigng.
