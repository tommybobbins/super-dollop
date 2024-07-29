# Architecture Patterns - Containers and PaaS

| Requirement | Solution |
| --- | --- |
| Deploy containers at the lowest costs | ECS with a cluster or Spot instances and enable spot instance draining OR Use App Runner. |
| Company plans to migrate containers but does not want to manage OS. | ECS Fargate |
| Fargate task is launched in a private subnet and fails with ````CannotPullContainer````| NAT Gateway |
| Application will be deployed on ECS and must scale based on memory| *Use service auto-scaling and use memory utilisation!* (You'd think this would require Cloudwatch agent installed on ECS instances) |
| Application runs on ECS tasks across multiple hosts and needs access to an S3 bucket| Add a Task Execution IAM Role to provide permissions. Never to the container host. |
|Docker container automation and management service | EKS|
|Company needs to move many simple Web apps running on PHP/Java and Ruby to AWS. Utilization is low.| Single instance Elastic Beanstalk.|
|Business critical application running on EB must be updated. Require zero downtime and quick and complete rollback.| Immutable deployment with a new ASG and swap traffic.|
| Dev app on beanstalk needs a cost effective and quick update.| All at once.|
|Managed environment for running a simple web app. App can process data for several minutes.|Elastic beanstalk with a webserver, SQS and a worker tier.|