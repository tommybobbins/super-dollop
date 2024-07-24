# Kinesis

It is a managed data streaming service suitable for

- Application logs
- Metrics
- IoT
- Clickstreams
- Real-time big data
- Spark/NiFi

Sources->Kinesis Streams->Kinesis Analytics->Kinesis Firehose->S3, Redshift, ES/OS.

# Kinesis Data Streams

Low latency streaming ingest at scale.

Producers -> Shard1, Shard2, .. Shard_n_ -> Consumers

- Data retention is by default 24 hours, but can be configured to be 365d.
- Data auto-replicated to 3 AZ.
- Has the ability to reprocess/replay data.
- Multiple applications can consume the same stream.
- Real-time processing with scale of throughput.
- Once data is in Kinesis it cannot be deleted.
- Batching or per message requests.
- Number of shards can evolve over time, (resharding/merging).
- Records are ordered within a shard but not between shards.

## Capacity Modes

| On-demand | Provisioned |
| --- | --- |
| Shards are scaled automatically | Shards are managed up-front/over time |


## Kinesis Agent
Java software application provides a way to collect and send data to Kinesis Data Strreams.
https://docs.aws.amazon.com/streams/latest/dev/writing-with-agents.html