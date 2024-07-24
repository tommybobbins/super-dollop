# AWS Organizations

All features – This feature set is the preferred way to work with AWS Organizations, and it includes Consolidating Billing features. When you create an organization, enabling all features is the default. With all features enabled, you can use the advanced account management features available in AWS Organizations such as integration with supported AWS services and organization management policies. Policies in AWS Organizations enable you to apply additional types of management to the AWS accounts in your organization. You can use policies when all features are enabled in your organization. Service control policies (SCPs) offer central control over the maximum available permissions for all of the accounts in your organization.

Consolidated Billing features – All organizations support this subset of features, which provides basic management tools that you can use to centrally manage the accounts in your organization. You cannot leverage SCPs in this feature mode.


## SCP

* Not available in an organization which only has consolidated billing enabled.*

Service Control policies don't replace associating IAM policies. SCPs allow or deny access to AWS Services for individual AWS Accounts within the Organization (members accounts or groups of accounts within an OU). The specified actions from an attached SCP affect all IAM identities including the root user.

AWS Services that aren't explicity allowed by the SCP associated with an AWS Account or Parent OU are denied access to the AWS Accounts. SCP's associated to an OU are inherited by all AWS accounts inside that OU.
