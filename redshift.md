# Redshift

## Database use cases

| Operational | Analytical |
| --- | --- |
| OLTP| OLAP |
|Production DBS that process transactions (e.g. adding custom records, checking stock, INSERT, UPDATE, DELETE).| Data warehouse - never customer facing. Data is extracted for decision making.| 
|Short transactions and simple queries .| Long transaction and complex queries. |
|RDS, DynamoDB|Redshift, EMR| 

## Redshift backups:

Create a snapshot copy grant in the destination Region for a KMS key in the destination Region. Configure Redshift cross-Region snapshots in the source Region
To copy snapshots for AWS KMS–encrypted clusters to another AWS Region, you need to create a grant for Redshift to use a KMS customer master key (CMK) in the destination AWS Region. Then choose that grant when you enable copying of snapshots in the source AWS Region. You cannot use a KMS key from the source Region as AWS KMS keys are specific to an AWS Region.

## QuickSight integrations

Data can be analysed with BI Tools such as QuickSight using SQL. The queries against redshift go via JDBC/ODBC.

## Redshift inputs

- AWS Data Pipeline.
- S3.
- Redshift Spectrum via S3.
- EMR.
- DDB.
- RDS.
- AWS Glue.
- EC2 (via SSH).
- On Premise servers (via SSH).