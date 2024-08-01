# Data Exchange 

- Data Marketplace with 3000 products from 250 providers.
- Data Files, Data Tables and Data APIs for sale.
- Consume directly into data lakes, applications , analytics and machine learning models.
- Automatically export new or updated data sets to S3.
- Query data tables with AWS Data Exchange for Amazon Redshift.


## Why use it

- Lots of datasets.
- One place to exchange data publicly or privately.
- Native integration into AWS.
- Self-service, secure and compliant.


| Requirement | Solution |
| --- | --- |
|Athena is being used to analyze a large volume of data based on data ranges. Performance must be optimized.|Apache Hive partitioning, key based on data. Use Apache Parquet/ORC formatting.|
|Lambda is processing streaming data from API Gateway and is generating TooManyRequestsException|Stream into KDS from API GW and process in batches.|
|Lambda function is processing streaming data that must be analyzed with SQL|kds->kda|
|WAF logs must be sent to a third party|KDF->Auditing Application as an HTTP endpoint.|
|Real time streaming data must be stored for future analysis|kds->kdf->store for later analysis.|
|Company runs several prodcution databases and wants complex queries against them|Data Lake->Redshift.|