## Some points that I forget

Supports reserved instances

### Redis
- Cluster mode disabled - single shard - upto 5 read-replicas (good for ready heavy workload) cannot change mode once created
- MultiAZ-Replicas can failover like aurora
- Cluster mode enabled - 90 nodes, min 3 shards for HA (good for write heavy - more data)
- Can backup from original or replica, looks like we can specify where to backup from, hence choose replica.
- If Multi-AZ with automatic failover is enabled, you cannot remove the last replica
- To promote a read replica to primary node, disable Multi-AZ with automatic failover if Cluster mode disabled.
- **Redis Global Datastore** can replicate upto 2 regions and available only for non-single node clusters


### Memcache
- 20 nodes / cluster, 100 / region (soft limit) and no replica support