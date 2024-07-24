# PrivateLink

AWS PrivateLink is a highly available, scalable technology that you can use to privately connect your VPC to services as if they were in your VPC. You do not need to use an internet gateway, NAT device, public IP address, AWS Direct Connect connection, or AWS Site-to-Site VPN connection to allow communication with the service from your private subnets. Therefore, you control the specific API endpoints, sites, and services that are reachable from your VPC.

https://docs.aws.amazon.com/vpc/latest/privatelink/what-is-privatelink.html

- Service Provider VPC
- Service Consumer VPC - creates interface VPC endpoints powered by Private link to connect to endpoint services hosed by Service Providers. 
- Can help with clashing IP ranges and inter-account/region communication. PrivateLink uses ENI within the client VPC so there are no conflicts with the service provider. You can access PrivateLink endpoints over VPC peering, VPN and Direct Connect Connections.