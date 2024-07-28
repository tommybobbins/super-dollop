# Amazon AppFlow

- Integration between SaaS services and Amazon (DataSources like Slack, Salesforce, SAP).
- Destination is Redshift, S3, Snowflake etc.
- Flow is created connecting data source with a destination.
- Flow can run on-demand, on a schedule or based on an event.
- Fields can be mapped manually or via a csv.
- 100GB of data per flow.
- Can run mapping, merging, masking, filtering and validation as part of the flow.
- Leverages AWS PrivateLink for secure transfer of data using private endpoints.
- Encryption through AWS KMS and fine-grained permissions can be applied using IAM policies.
