# Load Balancing


## What's the source Address the App Sees:

- In a CLB/ALB, it will *always* be the private IP of the ENI associated with the ALB.
- In an NLB, *if the target instance is specified by Instance ID*, the source IP will be the *Real-IP (client IP)*.
- In an NLB, *if the target instance is specified by IP address*, the source IP will be the IP of the NLB (TCP and TLS). For UDP and (TCP_UDP) it will be the Real-IP. 

When using an NLB with a VPC endpoint or AWS GA, source IPs are the private IPs of the NLB nodes.

## SSL/TLS Termination

- ALB TLS (ACM Certificate)
- NLB can terminated TLS at NLB or passthrough.
