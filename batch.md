# AWS Batch

- Batch job is a unit of work such as a shell script, executable or container.
- A job is submitted into a queue until scheduled onto a compute environment.
- Batch launches manages and terminates resources as required (EC2 and ECS/Fargate).
- Managed or unmanaged resources are used to run the job.
- You can use a managed compute environment to have AWS Batch manage the capacity and instance types of the compute resources within the environment.
- Managed compute environment: Launched into VPC you specify. Specify, Min, Desired, Maxc vCPU, Instance types.
- Managed compute environment: If you launch in private subnet, ensure it can reach ECS either using NAT GW or VPC Endpoint for ECS.
- Unmanaged compute environment: You control and manage instance config, provisioning and scaling.
- Job -> Job Definitiion -> Job queue-> Batch compute environment.


## AWS Batch - multi-node mode

- Used for HPC.
- Leverages mutliple EC2/ECS instances simultaneously.
- Good for tightly coupled workloads.
- Represents a single job and specified how many nodes to create for the job.
- 1 parent node, child nodes.
- Does not support spot instances.
- Works better if launch mode is placement group cluster (same rack, same AZ).

# Comparison of Batch and Lambda

| Lambda | Batch |
| --- | --- |
| Time Limited | No limit |
| Limited resources | Any runtime if container |
| Limited Disk | EBS/Instance size| 
| Serverless | Relies on EC2/Fargate |