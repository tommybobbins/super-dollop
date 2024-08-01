# Data Pipeline

- Managed ETL Service.
- Process and move data between different AWS compute and storage services.
- Data sources can also be on-prem.
- Data can be processed and transformed.
- Results can be loaded to S3, RDS, DDB and EMR.

## ClickStream Data Example

````
Clickstream data -> S3 bucket -> Hive Activity (converts log files to CSV with EMR) -> S3 -> Redshift.
````

# Data Lake

Data Lake is structured and unstructured repository for storing data at any scale. You can store your data as-is without having to first structure the data.



|Characteristics| Data Warehouse | Data Lake |
| --- | --- | --- |
| Data | Relational from transaction systems, operational databases and line of business applications| Non-relational and relational from websites, mobile apps, social media and corporate applications |
| Schema | Designed prior to the DW implementation (schema-on-write)| Written at the time of analysis (schema-on-read) |
|Price/Performance|Fastest query results using higher cost storage| Query results getting faster using low-cost storage|
|Data Quality|Highly curated data that servers as a central version of the truth|Any data that may or may not be curated (i.e. raw data)|
|Users|Business analysts|Data scientists, Data Developers (and analysts using curated data)|
|Analytics|Batch reporting, BI and visualizations|ML, Predictive analytics, discovery and profiling|

# AWS Lake Formation

- Lake formation enables you to setup secure data lakes in days
- Data can be collected from databases and object storage
- It is saved to the S3 data lake
- ML can be applied
- Security at Column, Row and Cell levels.
- Datasets can then be used by Redshift, Athena, EMR, Spark and Quicksight.
- Lake formation builds on the capabilities in AWS Glue.