# EMR 

Managed Clustered platform that simplifies running big data frameworks including Apache Hadoop and Apache Spark.

- Used for processing data for analytics and business intelligence.
- Can also be used for transforming and moving large amounts of data.
- ETL.
- EMR runs in a single AZ.
- Optionally attach EBS volumes.
- Each cluster has 1 master and no core nodes.

EC2 Nodes in the cluster run EMR.
VPC is used to configure the EMR network.
S3 is used to store input and output data.
CloudWatch is used to monitor cluster performance and configure alarms.
IAM to configure permissions.
Cloudtrail - audit requests made to the service.
Data Pipeline - schedule and start your clusters.
Lake Formation - discover, catalog and secure data in an Amazon S3 data lake.

## OUTPUTS

- S3
- S3 Glacier
- Redshift
- DDB
- RDS
- Hadoop HDFS

## Use Cases

```` Data Source->S3->EMR->Redshift->BI reporting ````
```` Data Source->S3->EMR doing ETL->S3 Cleansed data->Redshift->QuickSight ````