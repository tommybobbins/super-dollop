# Direct Connect (DX)

- DX is a physical fibre connecting to AWS running at 1Gb/s, 10Gb/s, 100Gb/s.
- A cross connect between the AWS DX and the customer/partner router.
- A DX Port must be allocated in a DX location.
- The customer router is connected to the DX Router in the DX location.
- Private connectivity between AWS and DC/Office.
- Consistent network experience - increased speed/latency and bandwidth/throughput.
- Lower costs for organizations that transfer large volumes of data.
- VPN->DX Locations are connected by redundant connections.
- Customer DC -> DX is a single connection.
- Better to have a different DX Location if possible (expensive).
- Use VPN if cost is a factor and you can manage with < 1Gbps
- Not encrypted, use a IPSec S2S VPN over a VIF.
- LAGs can be used to combine multiple physical connections into a single logical connection using LACP - improved speed, but not availability.

Link aggregation groups must be:
- Dedicated
- Same Bandwidth
- Terminate at the same Direct Connect endpoint
- It is possible to set the minumum number of connections for the LAG to function, so can increase resilience this way

## Setup

- Create a VGW which has a Private VIF between VPC and AWS Cage/Direct Connect endpoint. A private VIF connects a *single VPC* in the the *same AWS region* using a VGW.
- A VIF is a virtual interface (802.1Q VLAN) and a BGP session.
-  A Public VIF can be used to connect to AWS Public services (DynamoDB, S3, Cloudfront) in *any Region* but not the internet.
- *VPC Interface Endpoints* can be accessed throught a private VIF.

## What if you have more than one VPC?

- For each VPC create a VGW
- Multiple Private VIFs can be used to connect to Multiple VPCs in the region.
- VIFs can also be shared with other AWS accounts, known as hosted VIFs.

## Hosted Connections

- 50Mb/s, 500Mb/s, 10Gb/s can be accessed via an APN partner (uses hosted VIFs or hosted connections).
- Capacity can be increased on demand.
- Hosted VIF is a single VIF that is shared with other customers.
- Hosted connection is a DX Connection with a single VIF dedicated to you.

# Direct Connect Gateway

Solve Direct Connect -> Multiple Regions problem. Reduces complexity and cost.
Single office location, but you want to route to multiple AWS regions.

- DX Gateway is associated with the Private VIF.
- DX Gateway is associated with a VGW in each of the Regions.
- BGP used to advertise routes.
- Network traffic can be routed from on-premise to any VPC.
- DX Gateway *does not allow VGWs to send traffic to each other*

# AWS Transit Gateway (TGW)

Cloud router which connects VPCs, VPNs, 3rd party appliances, other TGWs in other regions and accounts and DX together. Solves the VPC<->VPC peering connection when there are 4 VPCs to connect and other complex routing problems.

- Transit Gateway is a network transit hub that interconnects VPCs and on-premises networks.
- VPCs->TGW->DX Gateway->DX Endpoint (via transit VIF)->Customer router->Corporate HQ.
- When using a TGW->DX Gateway-> DX Connection endpoint, use a Transit VIF.
- Transit VIF is only used when attaching a DX Gateway to a TGW.