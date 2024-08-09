# CloudFormation

Infrastructure patterns are defined in a template file using code (json or yaml). Cloudformation builds infrastructure according to the template.

- Infrastructure provisioned consistently.
- Fewer mistakes, human error.
- Reusable templates (define once, keep re-using).
- Pay for the resources provisioned.
- Allows rollback once complete.
- Upload to CF directly or S3 and point CF to template in S3.
- Logical ID is used to reference resources within the template.
- Automatic rollback on error is enabled by default.
- Stacksets : *Multiple accounts and regions*
- Admin account for stacks and stacksets.
- Nested stacks, reference other templates (e.g. for load balancer).

|Component|Description|
|---|---|
|Templates|JSON or YAML text described by the template and created, updated and deleted as a single unit.|
|Stacks|The entire environment described by the template and created, updated and deleted as a single unit|
|StackSets|AWS CloudFormation Stacksets extends the functionality of stacks by enabling you to create, update and delete stacks across multiple accounts and regions within a single operation.|
|Change Sets|A summary of proposed changes. Preview mode.|

## Change Sets

- Direct update - submit changes and AWS immediately deploys.
- Change sets - preview the changes AWS will make and decide whether to apply or not.

## Service Catalog

AWS Service Catalog, create and manage approved catalogs of IT services. It enables users to quickly deploy only the approved IT services they need.

- Catalog Admin authors templates and creates product. Organise into portfolios.
- Product is added to a portfolio.
- Users/Groups are assigned permissions to a portfolio.
- Constraints are added to the product/portfolio.
- AWSServiceCatalogEndUserReadOnlyAccess to only allow users to provision from a Service Catalogue

### Constraints

- Controls the ways that AWS resources can be deployed.
- Apply limits to products for governance or cost control.
- *Launch constraints* - specify a role for a product in a portfolio. The role is used to provision resources at launch so you can restrict user permissions without impacting users ability to provision products from the catalog.
- *Notification constraints* - enable you to get notifications about stack events using an Amazon SNS topic.
- *Template constraints* - restrict the configuration parameters that are available for the user when launching the product.

### Service Catalog Permissions

- Users don't need permissions, only permissions to access Service Catalog.
- Underlying Service Catalog needs a Role and a Policy to allow it to launch resources.

# CloudFormation and Autoscaling groups

You can add an ````UpdatePolicy```` attribute to your stack to perform rolling updates (or replace the group) when a change has been made to the group. Alternatively, you can force a rolling update on your instances at any time after updating the stack by starting an instance refresh.

To specify how AWS CloudFormation handles rolling updates for an Auto Scaling group, use the ````AutoScalingRollingUpdate ```` policy. Rolling updates enable you to specify whether AWS CloudFormation updates instances that are in an Auto Scaling group in batches or all at once. For example, suppose you have updated the MaxBatchSize in your stack template’s UpdatePolicy from 1 to 10. This allows you to perform updates without causing downtime to your currently running application.
