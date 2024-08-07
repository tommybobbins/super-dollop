# AWS Backup

AWS Backup is a fully-managed service that makes it easy to centralize and automate data protection across AWS services, in the cloud, and on premises. Using this service, you can configure backup policies and monitor activity for your AWS resources in one place. It allows you to automate and consolidate backup tasks that were previously performed service-by-service, and removes the need to create custom scripts and manual processes. With a few clicks in the AWS Backup console, you can automate your data protection policies and schedules.

- EC2/EBS
- S3
- DDB
- RDS
- EFS
- FSx
- DocumentDB
- Neptune
- Redshift
- etc.

## Backup Vaults
In AWS Backup, a backup vault is a container that stores and organizes your backups. Associated with a KMS key.

## Backup Policies can be created at the Organization Level.

https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_backup_create.html

- After you enable backup policies for your organization, you can create a policy.
- When your backup requirements change, you can update an existing policy.
- When you no longer need a policy and after you detach it from all organizational units (OUs) and accounts, you can delete it.