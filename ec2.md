# EC2

## Placement Groups

- *Cluster* – Packs instances close together *inside an Availability Zone*. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of high-performance computing (HPC) applications.

- *Partition* – Spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka.

- *Spread* – Strictly places a small group of instances across distinct underlying hardware to reduce correlated failures.

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html

## Dedicated Hosts

Physical server dedicated for your use; Socket/Core Visibility, host affinity. Pay per host. Workloads with server-bound software licences. MAC address/ hardware identifiers will not change.

## Dedicated instances

Physical isolation at the host hardware level rom instances belonging to other customers. Pay per instance. Hardware may change, but you will not share it. MAC address/ hardware identifiers may change.
"Dedicated Instances are Amazon EC2 instances that run in a virtual private cloud (VPC) on hardware that's dedicated to a single customer... Dedicated Instances may share hardware with other instances from the same AWS account that are not Dedicated Instances."

## Billing

- Billed per second, minimum of 1 minute (AL2, Ubuntu in on-demand, reserved and spot instances).
- Commercial Linux distributions use hourly pricing.
- Per second billing is now also available in Windows.


| Placement Group Type | Use Case |
| --- | --- | 
| Cluster|Tightly coupled application that requires low latency, high throughput network traffic between instances.|
| Partition|Distributed and replicated NoSQL database; requires separate hardware for node groups|
| Spread|Small number of critcial instances that should be kept separate from each other|

## ENI

Elastic Network Interface.

- Basic adapter type, don't need high performance. 
- Can have additional ENIs from subnets in the same AZ. 
- You cannot attach ENIs from different AZs.
- Supported by all instance types.
- Can be remapped to a different instance within same AZ.

## ENA

Elastic Network Adapter.

- Enhanced networking performance. 
- Higher bandwidth and lower inter-instance latency
- Must choose supported instance type.

## EFA

Elastic Fabric Adapter.

- High performance
- HPC, MPI (Message passing interfaces) and ML.
- Tightly coupled applications
- Can be used with all instance types.

## Patching

- Set up Systems Manager Agent on all instances to manage patching. 
- Test patches in pre-production and then deploy as a maintenance window task with the appropriate approval.
- Apply patch baselines using the ````AWS-RunPatchBaseline```` SSM document.