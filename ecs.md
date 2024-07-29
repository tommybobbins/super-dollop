# Elastic container service

## Overview

- ECS cluster is a logical grouping of tasks or services.
- An ECS task is a running docker container. 
- Container instance - EC2 instance running the ECS agent.
- Task definition is json blueprint (c.f. docker-compose file) which dictates how a task is started. Can also configure through console.
- Registry is an Image (can be stored in ECR).
- ECS services are long running tasks used to maintain a desired count of tasks. Can control task count wih auto-scaling and attach an ELB.
- ECS Clusters can span multiple AZ.
- ECS Container instances are inside an ASG
- Can run serverless with Fargate. Fully scalable.
- Fully managed container orchestration. 
- Windows container.
- Elastic Load balancers (ALB and NLB supported).
- ECS Anywhere - extend the control plane to manage on-premise implementations. (cf. EKS anywhere)
- ECS Console creates a cluster using Cloud Formation!

## ECS Launch types

|EC2 Launch Type| Fargate Launch Type |
| --- | --- |
|EC2 instances with ECS Agent installed.| Fargate automatically provisions resources. |
|You are responsible for managing the EC2 instances (patch management, security) | Fargate provisions and manages compute. |
|Charged per running EC2 instance.| Charged for running tasks |
|ECS Agent supports Docker volumes, EFS and FSx for Windows File Server.| EFS integration |
|You handle cluster optimization| Fargate handles cluster optimization.|
|More granular control over infrastructure.| Limited control, infrastructure is automated.|

## ECS and IAM Roles

- The container instance IAM roles provides permissions to the host.
- The ECS task IAM role provides permissions to the container.
- Container instances have access to *all the permissions* that are suppled to the *container instance role* through instance metadata.
- With the fargate launch type, only IAM task roles can be applied. - Different tasks, different privileges. Least privilege.

## Scaling Amazon ECS

### Service Auto Scaling
- Automatically change the desired task count up or down using the Application Auto Scaling service.
- Supports target tracking, step and scheduled scaling policies.
- Metrics are reported into CloudWatch. 
- Application Autoscaling service increments the number of tasks.

### Cluster autoscaling 
- Increase number of container instances.
- A Capacity provider reservation metric measures the total % of cluster resources needed by all ECS workloads in the cluster.
- ASG is linked to ECS using a Capacity provider. ASG launches a new ECS instance.
- Managed scaling, Managed instance termination protection.

## ECS and ALB

ALB has Container awareness.

- Each task is running a web service on port 80.
- A dynamic port is allocated on the host (32600) (HostPort).
- ALB can forward to the dynamic ports.
- NAT gateway is required for tasks in private subnets to access the internet.