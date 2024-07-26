# AWS Client VPN

- PC -> VPN in VPC.
- Encrypted end-to-end.
- Create VPN Endpoint associated with Subnets in the VPC.
- VPC Endpoint then creates Network interfaces in subnets automatically (cf. ENI).
- Compatible with openVPN. 
- Connection over SSL/TLS 443.
- VPN Endpoint performs NAT.


# AWS Site-to-Site VPN

- Customer Datacentre into AWS. 
- Private Network established over the internet.
- End-to-end encrypted.
- Managed IPSEC VPN.
- Create Virtual Private Gateway (VGW) on the VPC side.
- Create Customer Gateway on the customer side (maps the corporate VPN into AWS).
- VPN Connection supports static routes or BGP peering and routing.
- Route table in subnets points to VGW.
- Two VPN connections(tunnels) are created on the AWS end to the CGW for HA.
- Need to use multiple CGW on the Customer site for resilience.
- Can optionally accelerate with Global Accelerator for Global Networks, routing traffic from on-prem to AWS' edge network endpoint closest to your CGW.

AWS recommend a separate VPN for each VPC. Direct connect is recommended if you need to connect to multiple VPC because it has a Direct Connect Gateway.

## Transitive routing and S2S VPN:

Be careful with transitive routing:

- Cannot route on-prem traffic destined for 0.0.0.0/0 via NATGW to the internet.
- Can route on-prem traffic destined for 0.0.0.0/0 via NAT Instance to the internet (have more control of a NAT instance).
- Can route VPC traffic destined for 0.0.0.0/0 through VGW->CGW.


# AWS VPN CloudHub

Not a service in the console. AWS Site-to-Site architecture.

- VGW is deployed on the AWS side.
- Multiple customer offices, want to connect them to each other.
- Hub and spoke model. VPC is the hub, offices are the spokes.
- Deploy CGW in each of the corporate offices.
- Use BGP in each of the offices. (unique ASN per office).
- One VGW->CGW1, CGW2, CGW3
- This will provide peer to peer routing between CGW1<->CGW2,CGW3 etc.
- IPSEC

