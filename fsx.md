# FSX

Implement 3rd party high performance filesystems in AWS. It is a fully managed service.

- FSx for Lustre
- FSx for Windows File Server
- FSx for Netapp Ontap
- FSx for OpenZFS

# FSx for Windows File Server

- Fully managedwindows filesystem shared service.
- SMB + NTFS.
- AD Integration, ACLs, User Quotas.
- Can be mounted on Linux via SMB.
- Supports Microsoft's distributed filesystem (DFS) namespaces. Allows files to be grouped across multiple filesystems.
- Scale up to 10s of GB, millions of IOPS, 100S of PB.
- SSD/HDD.
- Can be accessed ia VPN/DX.
- Can be configured to be Multi-AZ.
- Data is backed up daily to S3.

# FSx for Windows Lustre

High performance computing. Lustre = Linux + Cluster

- ML, HPC, Video Processing, Design Automation.
- SSD/HDD.
- Seamless integration with S3 (can read/write S3)
- SSD/HDD.
- Can be accessed ia VPN/DX.

# FSx for Netapp Ontap

NTFS/SMB/iSCSI

- Move workloads running ontap or NAS to AWS.
- Linux, Windows, OSX, vmware on AWS, Amazon Workspaces, Appstream 2.0, EC2, ECS, EKS.
- Storage shrinks or grows automatically.
- Snapshots/Replication/Compression/Dedupe.
- Point in time Cloning.

# FSx for OpenZFS

NFS/ZFS->AWS

- Move workloads running ontap or NAS to AWS.
- Linux, Windows, OSX, vmware on AWS, Amazon Workspaces, Appstream 2.0, EC2, ECS, EKS.
- Snapshots/Replication/Compression. * NO DEDUPE *.
- Point in time Cloning.
- Low cost, helpful for testing new workloads.

# FSx File System Deployment Options

## Scratch File System

- Temporary Storage.
- Data is not replicated (fails if the fileserver fails).
- 6x faster, 200MBps/TB.
- Usage: short-term processing, optimise costs.
- Writes to S3.

## Persistent File System

- Long term Storage.
- Data is replicated within AZ.
- Replace failed files in minutes.
- Usage: long-term processing, sensitive data.
- Writes to S3.

## Migration from Single AZ to Multi-AZ

Two options:

FSx For WFS (single AZ)------> AWS Data Sync -------> FSx for WFS (multi AZ)
FSx For WFS (single AZ)------> Backup->Restore -----> FSx for WFS (multi AZ)

Backup can only restore to the same size. It can only increase capacity, not decrease. To reduce the capacity allocated to FSx, perform migration and point App to the new endpoint.