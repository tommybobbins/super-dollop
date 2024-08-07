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

## Application Migration service

AWS Application Migration Service (MGN) simplifies and expedites your migration to AWS by automatically converting your source servers from physical, virtual, or cloud infrastructure to run natively on AWS. It further simplifies your migration and reduces costs by enabling you to use the same automated process for a wide range of applications, without changes to applications, their architecture, or the migrated servers. You can use AWS Application Migration Service to perform non-disruptive tests before cutover. After testing, you can use AWS Application Migration Service to quickly lift and shift your applications to the cloud during a short cutover window, typically measured in minutes.

As of March 31, 2022, AWS has discontinued AWS Server Migration Service (AWS SMS). Going forward, AWS recommends AWS Application Migration Service (AWS MGN) as the primary migration service for lift-and-shift migrations.

## Packet tracing

VPC Flow logs show L4 detail,  but if you need to see the content of packets (wireshark):

Generally, the promiscuous mode allows the user to bypass the normal operation mode by forwarding all traffic it receives to the CPU. However for AWS, even if you can turn your NIC to Promiscuous mode, the hypervisor will never pass traffic intended for another virtual machine to your EC2 instance. You need to use traffic mirroring as it allows you to copy traffic passing through an elastic network adaptor and send it toward another instance for further investigation.

## Configure Traffic Mirroring

Configure Traffic Mirroring on elastic network interface of the EC2 instances. Send the mirrored traffic to a monitoring appliance for storage and inspection. Traffic Mirroring can copy network traffic from an elastic network interface and send it to a monitoring appliance for inspection.

PAYLOAD == TRAFFIC MIRRORING!

# EC2Rescue

- Diagnose and troubleshoot problems on Amazon EC2 Linux and Windows Server instances. You can run the tool manually, or you can run the tool automatically by using Systems Manager Automation and the AWSSupport-ExecuteEC2Rescue document. 
- The AWSSupport-ExecuteEC2Rescue document in Systems Manager Automation is designed to perform a combination of Systems Manager actions, AWS CloudFormation actions, and Lambda functions that automate the steps normally required to use EC2Rescue.

# Spot Fleet

A Spot Fleet is a set of Spot Instances and optionally On-Demand Instances that are launched based on criteria that you specify. The Spot Fleet selects the Spot capacity pools that meet your needs and launches Spot Instances to meet the target capacity for the fleet. By default, Spot Fleets are set to maintain target capacity by launching replacement instances after Spot Instances in the fleet are terminated. 

# HPC and EC2

Run the HPC within a single AZ, cluster PG, EFA and *disable hyperthreading*. Most HPC applications will benefit from disabling Hyperthreading:

```` 
AWS enables Intel Hyper-Threading Technology, commonly referred to as “hyperthreading,” by default. Hyperthreading improves performance for some applications by allowing one process per hyperthread (two processes per core). Most HPC applications benefit from disabling hyperthreading, and therefore, it tends to be the preferred environment for HPC applications. Hyperthreading is easily disabled in Amazon EC2. Unless an application has been tested with hyperthreading enabled, it is recommended that hyperthreading be disabled and that processes are launched and individually pinned to cores when running HPC applications. CPU or processor affinity allows process pinning to easily happen.
````

https://docs.aws.amazon.com/wellarchitected/latest/high-performance-computing-lens/compute.html

# Amazon Linux boot time

Boot time a problem? Don't want to use a minimum sized ASG because of this? You can always use Hibernation provide you enable it before you launch.
