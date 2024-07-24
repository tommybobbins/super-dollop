# Kinesis Data Streams vs Kinesis Data Firehose use cases.

When to use KDS and KDF:

| Kinesis Data Streams | Kinesis Data Firehose
| --- | --- |
| Streaming service for Ingest at Scale | Ingesion service for Storage |
| Write Custom Code (producer/consumer) | Fully Managed |
| Real Time (200ms) | Near Real Time (Up to 1s)|
| Manage scaling (shard splitting/merging) | Automated Scaling |
| Data Storage 1-365 Days | No native storage, stores in other services |
| Supports Replay | No Replay |