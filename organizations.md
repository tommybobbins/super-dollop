# AWS Organizations

Organizations with only consolidated billing enabled 


## SCP

* Not available in an organization which only has consolidated billing enabled.*

Service Control policies don't replace associating IAM policies. SCPs allow or deny access to AWS Services for individual AWS Accounts within the Organization (members accounts or groups of accounts within an OU). The specified actions from an attached SCP affect all IAM identities including the root user.

AWS Services that aren't explicity allowed by the SCP associated with an AWS Account or Parent OU are denied access to the AWS Accounts. SCP's associated to an OU are inherited by all AWS accounts inside that OU.
