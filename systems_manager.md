# Systems Manager

- Automation (YAML or JSON). - Documents define actions to perform - Automation performs operations across AWS resources.
- Run Command. - Documents define command, automation, package etc.
- Inventory. Inventory of the resources you are managing. Instances need to have an agent installed so that they can communicate with systems manager.
- Patch Manager.
- Parameter stores.
- Scan managed instances for patch compliance and configuration inconsistencies.
- Collect and aggregate data from multiple AWS accounts and regions and then drill down into resources which are not compliant.
- AWS Systems Manager displays data about patching and associations.
- Can also customize the service and create your own compliances type based on the requirments (e.g must use the CLI). 

## Session Manager

- RDP/SSH for Windows/Linux but not exposed outside of AWS.
- Integrates with IAM for granular permissions.
- Integrates with Cloudtrail
- Store session logs in S3.
- Requires IAM permission for EC2 access to access SSM, S3 and Cloudwatch logs.
- No bastion hosts, no ports need opening within SG.

## Parameter Store

- Secure, hierarchical storage for configuration data and secret management.
- Highly durable, available and scalable.
- Store data such as passwords, database strings and licence keys.
- Store in plaintext or ciphertext
- Reference values by using the unique name that you specified when you created the parameter.
- *No native rotation of keys* - difference with AWS Secrets Manager which happens automatically.

## Fleet Manager

- Configure Default Host Management->Enable. All EC2s with supported OS created after this is enabled will automatically be registered as Managed Instances (default ssm-agent will register with IMDSv2).

## Run Command 

## Patch Manager