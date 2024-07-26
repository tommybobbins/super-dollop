# VPC

- Corporate Data Centre - Outposts
- Mobile endpoints - AWS Wavelength Zone
- AWS Local Zone - Single digit millisecond latency to end users
- CloudFront Regional Edge Caches.

## IGW

IGW can have a gateway route table in case packets within the VPC need routing via a Security VPC (GLB, packet inspection).

## NACL at the subnet level

- Stateless (worry about ephemeral ports)

## Security Group at the Instance/Resource Level

- Stateful - allows the return traffic to return automatically.

## NAT Instance

- Can't NAT forward unless you disable source/destination checks.

## NAT Gateway

- Obviously use in most cases.

## Comparison chart 

| NAT Instance | NAT GW |
| --- | --- |
| Managed by you (software updates) | Fully-managed by AWS |
| Scale up (instance-type)/Use enhanced networking | Elastic scalability to 45 Gbps|
| No HA - scripted/auto-scaled HA possible if using multiple NATs in multiple subnets | Automatic HA within AZ and can be placed in multiple AZs|
| Need to assign SG | No SGs |
| Can use as a bastion | No SSH access |
| Use an EIP or public IP | Choose an Elastic IP address at creation |
| Can implement port forwarding through manual customisation | Does not support port forwarding |

## Egress only Internet Gatway is a NAT GW for Ipv6.

## VPC Endpoints

Use a private endpoint to connect to Amazon S3, DynamoDB etc.

### VPC Interface Endpoint

ENI is created in the subnet. Each interface endpoint can connect to one AWS service. 
Interface endpoint can connect to PrivateLink.

### VPC Gateway Endpoint

Used for S3 and DynamoDB. Route table entry - required with the prefix list for S3 and the Gateway ID.
IAM policies can be applied to endpoints and bucket policies can limit access to the endpoint source.

### Comparison chart

|| Interface Endpoint | Gateway Endpoint |
| --- | --- | --- |
|What | ENI with a Private IP | Gateway that is a target for a specific route|
|How| DNS entries to redirect traffic | Prefix lists in the route table to redirect|
|Which services| API GW, CF, Cloudwatch etc. | S3, DynamoDB|
|Security| Security Groups | VPC Endpoint policies |


### Service Provider Model
````
[Consumer VPC->EC2->Interface Endpoint] ----------------[ Service Provider VPC->NLB->Webserver]
````

