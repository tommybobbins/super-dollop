# Migration Services


- Use AWS Migration Hub to discover and track the status of the application migration across AWS and partner solution.
- Use the AWS Cloud Adoption Readiness Tool (CART) to generate a migration assessment report to identify gaps in organizational skills and processes.
- Use AWS Application Discovery Service to gather information about the running virtual machines and running applications inside the servers. Has an agentless (deployed through OVA in VMware) and agent-based discovery (deployed on individual servers).

## AWS Application Discovery Service 

Helps you plan your migration to the AWS cloud by collecting usage and configuration data about your on-premises servers. Application Discovery Service is integrated with AWS Migration Hub, which simplifies your migration tracking as it aggregates your migration status information into a single console. You can view the discovered servers, group them into applications, and then track the migration status of each application from the Migration Hub console in your home region.

- Hostnames.
- IP addresses.
- MAC addreses.
- Resource allocation / utilization details.
- CPU, Network, Memory and Disk.

Agentless discovery (Discovery Connector) is an OVA appliance in vCenter
Agent based discovery (Hyper_V & servers) also provides System configuration, System performance, Running processes, Network connections.

## AWS Migration Hub (Migration Hub) 

Provides a single place to discover your existing servers, plan migrations, and track the status of each application migration. The Migration Hub provides visibility into your application portfolio and streamlines planning and tracking. You can visualize the connections and the status of the servers and databases that make up each of the applications you are migrating, regardless of which migration tool you are using. Migration Hub gives you the choice to start migrating right away and group servers while migration is underway or to first discover servers and then group them into applications.

## Application Migration Service (MGN)

Highly automated lift-and-shift (rehost) solution for migrating applications to AWS.

- Agentless snapshot based replication with AWS MGN vCenter Client
- AWS recommend agent based replication when possible via continuous data protection (CDP)
- MGN utilizes continuous block-level replication and enables short cutover windows measured in minutes.
- Server migration service (fore-runner to MGN uses incremental snapshot based replication and enables cutover windows measured in hours).
- MGN integrates with the Cloud Migration Factory for orchestration.
- Can migrate virtual and physical services.

### Agent based replication

AWS Application Migration Service -> Automated, incremental and scheduled migrations -> Launch Template -> EC2 instances
Can also trigger Lambdas via Cloudwatch events.

## Database Migration Service (DMS)

Oracle -> DMS -> Redshift (use schema conversion tool for heterogenous migrations)
MySQL -> DMS -> Aurora (include Aurora, Redshift, DDB and DocumentDB).

- Cloud -> Cloud
- On-Premise -> Cloud
- Homogenous migrations via SCT
- Development and Test
- Database consolidation - consolidate multiple sources DBS to a single target DB.
- Continuous Data Replication - use for DR, dev/test, single source multi-target or multi-source single target.


# 7 Rs of migration

- Retire - Get rid.
- Retain - Leave for now.
- Relocate - Move without modification.
- Rehost - OS/App moved to another host system (lift and shift)
- Repurchase - Use a different solution (e.g. SaaS)
- Replatform - e.g. Move to RDS; server to Elastic Beanstalk
- Refactor - rebuild with cloud-native serverless architectures.


## Rehost

- AWS recommend the Application Migration Service (MGN) for lift and shift
- Can also use AWS SMS and VM Import/Extport

```` AWS Replication Agent installed on servers -> AWS MGN -> Test and Cutover EC2 ````

## Replatform

- DMS and/or Schema conversion tool (DMS+SCT)
- Migrate to EB using custom AMI or code level migration.
- Moderate development and migration effort.
- MySQL -> DMS -> Aurora
- Server Migration service

## Refactor

- Re-architect to a cloud-native serverless architecture
- Migrate servers to serverless functions or containers
- Migrate RDBMS to Managed DBS or NoSQL DBs
- Filestores to Object stores etc.