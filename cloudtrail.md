# CloudTrail


## Securing CloudTrail Logs

Enable CloudTrail log file integrity validation
Use Amazon S3 MFA delete on the S3 bucket that holds cloudtrail logs and digest files.

Enable CloudTrail log file integrity validation - Validated log files for security/forensic investigations.

When you enable log file integrity validation, CloudTrail creates a hash for every log file that it delivers. Every hour, CloudTrail also creates and delivers a file that references the log files for the last hour and contains a hash of each. This file is called a digest file. CloudTrail signs each digest file using the private key of a public and private key pair. After delivery, you can use the public key to validate the digest file. CloudTrail uses different key pairs for each AWS region.

Use Amazon S3 MFA Delete on the S3 bucket that holds CloudTrail logs and digest files - The digest files are delivered to the same Amazon S3 bucket associated with your trail as your CloudTrail log files. If your log files are delivered from all regions or from multiple accounts into a single Amazon S3 bucket, CloudTrail will deliver the digest files from those regions and accounts into the same bucket.

Configuring multi-factor authentication (MFA) ensures that any attempt to change the versioning state of your bucket or permanently delete an object version requires additional authentication. This helps prevent any operation that could compromise the integrity of your log files, even if a user acquires the password of an IAM user that has permission to permanently delete Amazon S3 objects.
