## Some points that I forget

- For multi-AZ, create at least one replica for each index in the cluster.
- Without replicas, cross-AZ replication doesn’t happen which largely defeats the purpose of Multi-AZ.
- Amazon ES provides three types of Elasticsearch logs
    • error logs
    • search slow logs
    • index slow logs
- UltraWarm instance – On-Demand or Managed storage (new tier type, cost-effective way to store large amounts of read-only data)