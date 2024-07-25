# IAM Principals

IAM Principals must be authenticated to send requests (there are a few exceptions). A Principal is a person or an application that can make a request for an action or operation on an AWS Resource.

- User
- Role
- Federated User
- Application

# Users (long term credentials)

# Groups (of users)

# Roles
Short term credentials, uses STS
- EC Instance Roles: Uses the EC2 metadata service. One role at a time per instance.
- Service Roles: API Gateway, CodeDeploy, etc.
- Cross Account Roles.

# Policies

Identity based policy versus Resource based policy

- AWS Managed.
- Customer Managed.
- Inline Policies - embedded inside a role.

## Trust Policy

Who can assume the role? This is an example of an Resource based policy (What resources can assume this role?)

## Permissions Policy

What can they do when they have access? This is an example of an Identity based policy.

## Resource based policies

- e.g S3 bucket, SQS queue. Can be useful for providing cross account access without assuming roles.

# IAM Policies

- json doc with Effect, Action, Resource, Conditions and Policy Variables.
- Explicit DENY has precedence over ALLOW.
- Best practice is to use least privilege for maximum security.
- Access Adviser - See permissions granted and when last accessed.
- Access Analyzer - Analyze resources shared with an external entity.


# IAM AWS Managed Policies

- e.g. AdminstratorAccess E,A,R: Allow,*,*
- e.g. PowerUserAccess  E,A,R: Allow, NotAction [ iam:*, organization:*, account:* ], *

# IAM Condition Operator
````
"Condition": {"StringEquals": {"aws:PrincipalTag/job-category": "iamuser-admin"}}
"Condition": {"StringLike": {"s3:prefix": [ "", "home/", "home/${aws:username}/" ]}}
"Condition": {"Bool": {"aws:SecureTransport": "true"}}
"Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
"Condition": {"IpAddress": {"aws:SourceIp": "1.2.3.0/24"}}
"Condition":{"Null":{"aws:TokenIssueTime":"true"}}
````

# IAM Policy Variables and Tags

Example: ````${aws:username}````
    "Resource": ["arn:aws:s3:::mybucket/${aws:username}/*"]
AWS Specific:
    aws:CurrentTime, aws:TokenIssueTime, aws:principaltype, aws:SecureTransport,
    aws:SourceIp, aws:userid, ec2:SourceInstanceARN
Service Specific:
    s3:prefix, s3:max-keys, s3:x-amz-acl, sns:Endpoint, sns:Protocol
Tag Based:
    iam:ResourceTag/key-name, aws:PrincipalTag/key-name

# IAM Roles and Resource Based Policies

Attach a policy to a resource (e.g. bucket policy) versus attaching using a role as a proxy:

User in Account A---->Role Account B---->Amazon S3 Account B
User in Account A---->[Bucket Policy]--->Amazon S3 Account B

- When you assume a role, original permissions are given up and the permissions are that of the assumed role.
- When using a resource based policy, the principal doesn't have to give up any permissions.
- e.g. User in Account A needs to scan a DynamoDB table in Account A and dump it into an S3 bucket in Account B. 

## Supported by 
- S3
- SNS
- SQS
- Lambda
- ECR
- Backup
- EFS
- Cloud9
- AWS Artifact
- Secrets Manager
- ACM
- KMS
- CW Logs
- API GW
- EventBridge
- ...

# IAM Permission Boundaries

IAM Permission Boundaries are supported for users and roles, but not groups. They are an advanced feature to set the maximum permissions and entity can get.

e.g. If a permission boundary is E,A,R: Allow, [s3:*,cloudwatch:*,ec2:*], *, then a policy is applied E, A, R: Allow, [iam:CreateUser], *, the permissions will not be allowed.

Permission Boundaries can be used in combinations of AWS Organizations Service Control Policies. Use Cases:
- Delegate responsibilities to non-administrators within their permission boundaries, for example to create new IAM users
- Allow developers to self-assign policies and manage their own permissions without allowing them to escalate.
- Useful to restrict one specific user instead of whole account using Organizations and SCP

Organizations SCP + Permissions Boundaries + Identity Based Pollicy = Effective Permissions.


# Users (long term credentials)

# Groups (of users)

# Roles
Short term credentials, uses STS
- EC Instance Profile -> IAM Roles: Uses the EC2 metadata service. One role at a time per instance.
- Service Roles: API Gateway, CodeDeploy, etc.
- Cross Account Roles.

An EC2 application uses the Instance Profile to assume the Role, temporary credentials are returned via sts.

# Policies

- AWS Managed.
- Customer Managed.
- Inline Policies - embedded inside a role.

## Resource based policies

- e.g S3 bucket, SQS queue. Can be useful for providing cross account access without assuming roles.

# IAM Policies

- json doc with Effect, Action, Resource, Conditions and Policy Variables.
- Explicit DENY has precedence over ALLOW.
- Best practice is to use least privilege for maximum security.
- Access Adviser - See permissions granted and when last accessed.
- Access Analyzer - Analyze resources shared with an external entity.


# IAM AWS Managed Policies

- e.g. AdminstratorAccess E,A,R: Allow,*,*
- e.g. PowerUserAccess  E,A,R: Allow, NotAction [ iam:*, organization:*, account:* ], *

# IAM Condition Operator
````
"Condition": {"StringEquals": {"aws:PrincipalTag/job-category": "iamuser-admin"}}
"Condition": {"StringLike": {"s3:prefix": [ "", "home/", "home/${aws:username}/" ]}}
"Condition": {"Bool": {"aws:SecureTransport": "true"}}
"Condition": {"Bool": {"aws:MultiFactorAuthPresent": "true"}}
"Condition": {"IpAddress": {"aws:SourceIp": "1.2.3.0/24"}}
"Condition":{"Null":{"aws:TokenIssueTime":"true"}}
````

# IAM Policy Variables and Tags

Example: ````${aws:username}````
    "Resource": ["arn:aws:s3:::mybucket/${aws:username}/*"]
AWS Specific:
    aws:CurrentTime, aws:TokenIssueTime, aws:principaltype, aws:SecureTransport,
    aws:SourceIp, aws:userid, ec2:SourceInstanceARN
Service Specific:
    s3:prefix, s3:max-keys, s3:x-amz-acl, sns:Endpoint, sns:Protocol
Tag Based:
    iam:ResourceTag/key-name, aws:PrincipalTag/key-name

# IAM Roles and Resource Based Policies

Attach a policy to a resource (e.g. bucket policy) versus attaching using a role as a proxy:

User in Account A---->Role Account B---->Amazon S3 Account B
User in Account A---->[Bucket Policy]--->Amazon S3 Account B

- When you assume a role, original permissions are given up and the permissions are that of the assumed role.
- When using a resource based policy, the principal doesn't have to give up any permissions.
- e.g. User in Account A needs to scan a DynamoDB table in Account A and dump it into an S3 bucket in Account B. 

## Supported by 
- S3
- SNS
- SQS
- Lambda
- ECR
- Backup
- EFS
- Cloud9
- AWS Artifact
- Secrets Manager
- ACM
- KMS
- CW Logs
- API GW
- EventBridge
- ...

# IAM Permission Boundaries

IAM Permission Boundaries are supported for *users and roles, but not groups*. They are an advanced feature to set the maximum permissions and entity can get.

e.g. If a permission boundary is E,A,R: Allow, [s3:*,cloudwatch:*,ec2:*], *, then a policy is applied E, A, R: Allow, [iam:CreateUser], *, the permissions will not be allowed.

Permission Boundaries can be used in combinations of AWS Organizations Service Control Policies. Use Cases:
- Delegate responsibilities to non-administrators within their permission boundaries, for example to create new IAM users
- Allow developers to self-assign policies and manage their own permissions without allowing them to escalate.
- Useful to restrict one specific user instead of whole account using Organizations and SCP

Organizations SCP + Permissions Boundaries + Identity Based Pollicy = Effective Permissions.

## IAM Access Analyzer

Find out which resources are shared externally:
- S3 Buckets
- IAM Roles
- KMS Keys
- Lambda Functions and Layers
- SQS queues
- Secrets Manager Secrets

Define a Zone of Trust == AWS Account / AWS Organization.
Access outside zone of trust provides findings.

### Access Analyzer Policy Validation

- Validates your policy against IAM policy grammar and best practices.
- General warnings, security warnings, errors, suggestions.
- Provides actionable recommendations.

### IAM Access Analyzer Policy Generation

- Generates an IAM Policy based on access activity.
- CloudTrail logs are reviewed to generate a policy with the fine-grained permissions and appropriate Actions and Services.
- Reviews CloudTrail Logs of *up to 90 days*.

## RBAC and ABAC

### RBAC

- Multiple groups (Admins, Developers, Operations).
- Users are placed into those Groups.
- Permissions are assigned to those Groups.
- Minimum permissions required to perform the job.

### ABAC

- Attribute based access control (e.g. tags)
- DBAdmins Group-> Dave is in the group-> Tag assigned to Dave (Department = DBAdmins)
- *IF:* Permissions policy rds:RebootDBInstance assigned to Group if StringEquals-> ```` [ aws:PrincipalTag/Department: DBAdmins ] ````
- *AND:* Resource Tag ```` [rds:db-tag/Environment: Production ] ````


## Combinations of policies

- Identity-based policy + Resource Based policy is a logical OR (concat).
- Identity-based policy + Permissions Boundary is a logical AND (intersection).
- Identity-based policy + Organizations SCP is a logical AND (intersection).
- An explicity Deny in any policy overrides (Trumps).

## Permissions Boundary

Used when creating user, prevents Privilege escalation.

## Best Practices

- Lock away root user access keys.
- Create individual IAM users.
- Use groups to assign permissions to IAM users.
- Grant least privilege.
- Get started using permissions with AWS managed policies.
- Use customer managed policies instead of inline policies.
- Use access levels to review IAM permissions.
- Configure a strong password policy for your users.
- Use MFA for all users.
- Use roles for applications on EC2.
- Use roles to delegate permissions.
- Do not share access keys.
- Rotate credentials regularly.
- Remove unnecessary credentials.
- Use policy conditions for extra security.
- Monitor activity in your account.

