# Kinesis

It is a managed data streaming service suitable for

- Application logs
- Metrics
- IoT
- Clickstreams
- Real-time big data
- Spark/NiFi
- 2MB/s/shard

Sources->Kinesis Streams->Kinesis Analytics->Kinesis Firehose->S3, Redshift, ES/OS.

# Kinesis Data Streams

Low latency streaming ingest at scale.

Producers -> Shard1, Shard2, .. Shard_n_ -> Consumers

- Data retention is by default 24 hours, but can be configured to be 365d.
- Each shard has a limit of 1MB/s. Throughput exception above this.
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

### Enhanced fanout if there is lag between producers and consumers

Amazon Kinesis Data Streams (KDS) is a massively scalable and durable real-time data streaming service. KDS can continuously capture gigabytes of data per second from hundreds of thousands of sources such as website clickstreams, database event streams, financial transactions, social media feeds, IT logs, and location-tracking events. By default, the 2MB/second/shard output is shared between all of the applications consuming data from the stream.

You should use enhanced fan-out if you have multiple consumers retrieving data from a stream in parallel. With enhanced fan-out developers can register stream consumers to use enhanced fan-out and receive their own 2MB/second pipe of read throughput per shard, and this throughput automatically scales with the number of shards in a stream.

## Kinesis Consumer Library

One of the methods of developing custom consumer applications that can process data from KDS data streams is to use the Kinesis Client Library (KCL).


## Kinesis Producer Library

An Amazon Kinesis Data Streams producer is an application that puts user data records into a Kinesis data stream (also called data ingestion). The Kinesis Producer Library (KPL) simplifies producer application development, allowing developers to achieve high write throughput to a Kinesis data stream.
