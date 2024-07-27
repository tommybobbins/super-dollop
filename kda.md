# Kinesis Data Analytics

Real time analysis of streams using SQL queries/Flink.

- Use IAM to access Streaming Source and Destination
- Schema Discovery
- Integrates with Lambda for Pre-processing
- Autoscaling
- Serverless
- Pay for Resources consumed

# Kinesis Client Library (KCL)

- You can only use DynamoDB for checkpointing KCL
- Each KCL application must use it's own DDB table (Scan operations are used to obtain leases and shared IDs in streams are used as PK)



