# Gateway Endpoints

Gateway VPC endpoints provide reliable connectivity to Amazon S3 and DynamoDB without requiring an internet gateway or a NAT device for your VPC. Gateway endpoints do not use AWS PrivateLink, unlike other types of VPC endpoints.

https://docs.aws.amazon.com/vpc/latest/privatelink/gateway-endpoints.html

- Requires route table changes for each service.
- Region specific.