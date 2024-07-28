# Elasticache

- In memory datastores
- Elasticache OR
- Redis.
- Can put in front of databases such as RDS and DynamoDB.
- Memcached has multi-az but no failover or replication
- Redis has multi-az with failover.
- Redis non-cluster mode, add nodes (read replicas), cluster mode add shards.

## Elasticache for Redis Security

You can use both in-transit as well as at-rest encryption to guard against unauthorized access of your data on the server. In-transit encryption encrypts your data whenever it is moving from one place to another, such as between nodes in your cluster or between your cluster and your application. At-rest encryption encrypts your on-disk data during sync and backup operations.

Redis authentication tokens enable Redis to require a token (password) before allowing clients to run commands, thereby improving data security. You can require that users enter a token on a token-protected Redis server. You also need to include it in all subsequent commands to the replication group or cluster.

Configure the security group for the ElastiCache cluster with the required rules to allow inbound traffic from the cluster itself as well as from the cluster's clients on port 6379

## Elasticache scalability

- Memcached add nodes to cluster.
- Scale vertically (node type) - must create a new cluster manually.

## Redis 
Cluster mode disabled:
- Add replica or change mode type - creates a new cluster and migrates data

Cluster mode enabled (3*shards and then replicas):
- Online resharding to add or remove shards, vertical scaling to change node type.
- Offline resharding to add or remove shards, change node type or upgrade engine (more flexible than online).
