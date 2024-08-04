# Resource Access Manager

AWS Resource Access Manager (AWS RAM) is a service that enables you to securely share your AWS resources across AWS accounts or within your organization. It simplifies the resource and policy management required for sharing resources, ensuring that only intended accounts have access to shared items. It’s important to note that only certain types of resources can be shared using AWS RAM, and a list of these resources is available on the AWS documentation.

- Shared resources across accounts.
- Participants can create, modify, and delete their own resources.
- Participants cannot view or modify resources of other participants or the VPC owner.
- Extend subnets across accounts.

RAM can be used to share:
- Transit Gateways.
- Subnets.
- AWS Licence manager configuration.
- Amazon R53 Resolver Rules.
- Share Aurora MySQL DB, EC2 instances.

# Add Jon Bonso stuff here.
