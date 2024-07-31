| Requirement | Solution |
| --- | --- |
| Company is migrating Linux and Windows VMs in VMware to the cloud. Needs to determine performance requirements. | Application Discovery Service discovery connector|
|Company is migrating vmware and physical servers to the cloud. Needs to identify dependencies for grouping applications for migration.  | Application Discovery Service connector and or agent|
|Oracle data warehouse to AWS | Migrate using DMS and SCT to Redshift |
|Snowball Edge transfer is slow|Batch files, run each command from a different terminal in it's own snowball client instance.| 
|Minimize downtime for servers that must be migrated to AWS|Use AWS SMS and perform a final sync. before cutting over in a small outage window.|
|Need to migrate 50TB of data|Snowball|