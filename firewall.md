# Network Firewall
Protecting resources in VPCs. Rules engine provides fine grained control over traffic in and out of the VPC. Firewall endpoint is a type of VPC endpoint.

- It uses a VPC Endpoint and Gateway load balancer.
- Stateful and stateless firewall
- Intrusion Prevention System (IPS)
- Web Filtering
- Works with AWS Network Firewall Manager for centrally applying policies across VPCs/accounts.
- Do not deploy resources in the firewall subnet.

# DNS Firewall (may not be on the exam yet)

- Filter and regulate outbound DNS traffic for VPCs.
- Requests route through R53 resolver for DNS
- Helps prevent DNS exfiltration of data.
- Monitor and control which domains can be queried.
- Can integrate with AWS Firewall Manager
- Can span VPCs and Accounts.
