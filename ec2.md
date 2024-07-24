# EC2

## Placement Groups

- *Cluster* – Packs instances close together inside an Availability Zone. This strategy enables workloads to achieve the low-latency network performance necessary for tightly-coupled node-to-node communication that is typical of high-performance computing (HPC) applications.

- *Partition* – Spreads your instances across logical partitions such that groups of instances in one partition do not share the underlying hardware with groups of instances in different partitions. This strategy is typically used by large distributed and replicated workloads, such as Hadoop, Cassandra, and Kafka.

- *Spread* – Strictly places a small group of instances across distinct underlying hardware to reduce correlated failures.

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/placement-groups.html