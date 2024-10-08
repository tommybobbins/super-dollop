# EBS 

Replicated within an AZ for availability.


## EBS Multi-attach

- Not on exam yet, but might be.
- io1 volume only.
- Within a single-AZ.
- Available for Nitro based filesystems.
- Up to 16 instances.

 ## Disk comparison table

||General Purpose SSD| General Purpose SSD|Provisioned IOPS SSD|Provisioned IOPS SSD|
|---|---|---|---|---|
|Volume type|gp3|gp2|io2 Block Express 3|	io1|
|Durability|99.8% - 99.9% durability (0.1% - 0.2% annual failure rate)|99.999% durability (0.001% annual failure rate)|99.8% - 99.9% durability (0.1% - 0.2% annual failure rate)|
|Use cases| Transactional workloads, Virtual desktops, Medium-sized, single-instance databases, Low-latency interactive applications, Boot volumes, Development and test environments| As gp3| Workloads that require: Sub-millisecond latency, Sustained IOPS performance, More than 64,000 IOPS or 1,000 MiB/s of throughput| Workloads that require sustained IOPS performance or more than 16,000 IOPS: I/O-intensive database workloads|
|Volume size|1 GiB - 16 TiB|1 GiB - 16 TiB|4 GiB - 64 TiB 4|4 GiB - 16 TiB|
|Max IOPS per volume|16,000 (64 KiB I/O)|16,000 (16 KiB I/O)|256,000 (16 KiB I/O)|564,000 (16 KiB I/O)|
|Max throughput per volume|1,000 MiB/s|250 MiB/s |4,000 MiB/s|1,000 MiB/s|
|Amazon EBS Multi-attach|Not supported|Not supported|Not supported|Supported|
|NVMe reservations|Not supported|Not supported|Supported|Not supported|
|Boot volume|Supported|Supported|Supported|Supported|

- ````st1```` (HDD) is low cost.
- ````sc1```` (HDD) is for low frequency writes.

## Volumes Restored from EBS snapshot

- May need to be pre-warmed or use fast snapshot restore or ````fio/dd```` commmands to read entire volume.

## EBS versus instance store

## Encrypted AMI

Can be shared with other accounts via a custom key, not AWS default key.

- Encrypted AMI->Encrypted AMI to change encryption key
- Encrypted AMI->EC2 instance to change encryption key


## Instance Stores versus EBS

- Instance store volumes are high performance local disks, physically attached to the host on which the EC2 instance runs.
- Instance stores are ephemeral, data is lost when the instance is powered off
- Instance stores are ideal for temporary storage of information that changes frequently such as buffers, caches or scratch data.

