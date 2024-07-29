# Elastic container service

## Overview

- ECS cluster is a logical grouping of tasks or services.
- An ECS task is a running docker container. 
- Container instance - EC2 instance running the ECS agent.
- Task definition is json blueprint (c.f. docker-compose file) which dictates how a task is started.
- Registry is an Image (can be stored in ECR).
- ECS services are long running tasks used to maintain a desired count of tasks. Can control task count wih auto-scaling and attach an ELB.
- ECS Clusters can span multiple AZ.
- ECS Container instances are inside an ASG
- Can run serverless with Fargate. Fully scalable.
- Fully managed container orchestration. 
- Windows container.
- Elastic Load balancers (ALB and NLB supported).
- ECS Anywhere - extend the control plane to manage on-premise implementations.

## ECS Launch types

|EC2 Launch Type| Fargate Launch Type |
| --- | --- |
|EC2 instances with ECS Agent installed.| Fargate automatically provisions resources. |
|You are responsible for managing the EC2 instances (patch management, security) | Fargate provisions and manages compute. |
|Charged per running EC2 instance.| Charged for running tasks |
|ECS Agent supports Docker volumes, EFS and FSx for Windows File Server.| EFS integration |
|You handle cluster optimization| Fargate handles cluster optimization.|
|More granular control over infrastructure.| Limited control, infrastructure is automated.|

