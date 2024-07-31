| Requirement | Solution |
| --- | --- |
| Global company needs to centrally manage creation of Infrastructure Service to Accounts in AWS Orgs|CloudFormation, Service Catalog, Products and Portfolios in a central account and share using Organizations.|
|Malicious attacks on RDP and SSH ports for remote access to EC2|Deploy Systems Manager Agent and use SSM|
|Development team want to deploy through CF, they use Javascript and Typescript|AWS CDK|
|Need to automate the process of updating an application when code is updated|CodePipeline (CodeCommit->CodeBuild->CodeDeploy)|
|Safely deploy updates to EC2 through Code Pipeline. Resources are defined in CF templates and Application code in S3|CodeBuild for automated testing, use CF change sets to evaluate changes and CodeDeploy to deploy using blue/green deployment.|
|Chef cookbooks->Moving to the Cloud|OpsWorks|