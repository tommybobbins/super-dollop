# Datasync

Migrate data to/from:

- On-premise.
- Other cloud.
- AWS.

Can sync to:

- S3
- EFS
- NFS
- SMB
- HDFS
- Snowcone
- Self managed object storage (CEPH)
- FSx Windows
- FSx Netapp
- FSx Lustre
- FSx OpenZFS

Replication tasks can be scheduled hourly, daily, weekly. File permissions and metadata are preserved (POSIX). Up to 10Gbps, bandwidth limits can be setup if required. Snowcone agent is pre-installed with the datasync agent.

````
[on prem datasync agent]----> Direct Connect ----> Private VIF -----> [VPC  PrivateLink -> Interface VPC Endpoint->AWS Data Sync 
````