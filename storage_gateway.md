## StorageGateway - File Gateway

- Filesystem is mounted using NFS or SMB.
- A local cache provides low latency access to recently used data.
- A virtual appliance runs on Hyper-V, VMWare or EC2.
- Backed by S3 (Standard, IA or One-Zone IA).
- Use with on-premise applications and EC2 applications that need filestorage.

## StorageGateway - Volume Gateway

- Block based volumes, iSCSI protocol


## Cached Volume Mode
```` Server-> iSCSI -> Cache -> AWS Storage Gateway -> Cached Volume Mode -> S3 ````
- Cache of the most recently used data kept on-premise.
- Entire data set is stored in S3.

## Stored Volume Mode
```` Server-> iSCSI -> AWS Storage Gateway -> Stored Volume mode-> Async Replication -> S3 ````
- Entire data set is stored on-premise.
- Data backed up as point in time snapshots.



## Storage Gateway - Tape Gateway

- Used for backup with popular backup software.
- Each gateway configured with a media changer and tape drive.
- Virtual tape: 100GB-> 2.5TB.
- Tape Gateway can have 1500 virtual tapes, up to 1PB.
- All data between gateway and AWS is encrypted using SSL.
- All data stored by the tape gateway in S3 is encrypted server-side with SSE-S3.
