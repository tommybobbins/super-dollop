# Elasticache

## Elasticache for Redis Security

You can use both in-transit as well as at-rest encryption to guard against unauthorized access of your data on the server. In-transit encryption encrypts your data whenever it is moving from one place to another, such as between nodes in your cluster or between your cluster and your application. At-rest encryption encrypts your on-disk data during sync and backup operations.

Redis authentication tokens enable Redis to require a token (password) before allowing clients to run commands, thereby improving data security. You can require that users enter a token on a token-protected Redis server. You also need to include it in all subsequent commands to the replication group or cluster.

Configure the security group for the ElastiCache cluster with the required rules to allow inbound traffic from the cluster itself as well as from the cluster's clients on port 6379