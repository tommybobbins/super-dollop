# Athena and AWS Glue

# Athena

- Serverless.
- SQL queries.
- Datasource in S3.
- .csv, .tsv, json, Parquet and ORC formats.

Can also query, Cloudwatch, DocumentDB, Redshift, MySQL, Redis, DDB, HBase, PostgreSQL, other data sources via lambda.

# AWS Glue

- Used as a metadata catalogue (can also use Apache Hive).
- Fully managed ETL service.
- Used for preparing data for analytics.
- Glue runs the ETL jobs on a fully managed scale-out Apache Spark environment.
- Discovers data and stores the associated metadata (table definition and schema) in the AWS Glue Data Catalogue.
- Works with data lakes (S3, Redshift, RDS or EC2 databases).
- You can use a crawler to populate the AWS Glue Data Catalogue with tables.
- A crawler can crawl multiple data stores in a single run.
- Upon completion, the crawler creates or updates one or more tables in your Data Catalogue.
- ETL jobs that you define in AWS Glue use the Data Catalogue tables as sources and targets.

## Optimize Athena for Performance

- Partition your data.
- Bucket your data within a single partition.
- Compression - Parquet or ORC.
- Optimize file sizes.
- Optimize columnar storage (Partquet or ORC).
- Optimize ORDER BY and GROUP BY queries.
- Use Approximate functions.
- Only include the columns that you need.