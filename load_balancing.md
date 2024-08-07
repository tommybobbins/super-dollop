# Load Balancing


## What's the source Address the App Sees:

- In a CLB/ALB, it will *always* be the private IP of the ENI associated with the ALB.
- In an NLB, *if the target instance is specified by Instance ID*, the source IP will be the *Real-IP (client IP)*.
- In an NLB, *if the target instance is specified by IP address*, the source IP will be the IP of the NLB (TCP and TLS). For UDP and (TCP_UDP) it will be the Real-IP. 

When using an NLB with a VPC endpoint or AWS GA, source IPs are the private IPs of the NLB nodes.

## SSL/TLS Termination

- ALB TLS (ACM Certificate)
- NLB can terminated TLS at NLB or passthrough.


## NLB Static IPs and Whitelisting

- Allocate elastic IPs up front, then allocate these to the NLB


## Session State and Stickiness

- Network load balancers do not support least outstanding requests routing.

## Dynamic Scaling 

- Target tracking scaling—Increase and decrease the current capacity of the group based on a Amazon CloudWatch metric and a target value. It works similar to the way that your thermostat maintains the temperature of your home—you select a temperature and the thermostat does the rest.
- Step scaling—Increase and decrease the current capacity of the group based on a set of scaling adjustments, known as step adjustments, that vary based on the size of the alarm breach.
- Simple scaling—Increase and decrease the current capacity of the group based on a single scaling adjustment, with a cooldown period between each scaling activity
