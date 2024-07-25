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


| NAT Instance | NAT GW |
| --- | --- |
| Managed by you (software updates) | Fully-managed by AWS |
| Scale up (instance-type)/Use enhanced networking | Elastic scalability to 45 Gbps|
| No HA - scripted/auto-scaled HA possible if using multiple NATs in multiple subnets | Automatic HA within AZ and can be placed in multiple AZs|
| Need to assign SG | No SGs |
| Can use as a bastion | No SSH access |
| Use an EIP or public IP | Choose an Elastic IP address at creation |
| Can implement port forwarding through manual customisation | Does not support port forwarding |