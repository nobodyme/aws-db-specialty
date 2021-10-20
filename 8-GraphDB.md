## Some points that I forget

- Load data formats
    • csv (for gremlin), ntripples / nquads / rdfxml / turtle (for sparql)
- All files must be UTF-8 encoded
- Cloning - Only within region (can be in different VPC)
- neptune_enforce_ssl = 1 - Cluster parameter
- Audit log files can be enabled by enabling DB cluster parameter neptune_enable_audit_log
- Export to CW - Log exports for your cluster
- Max 8192 queries can be queued up per Neptune instance
- Use CloudWatch metric - MainRequestQueuePendingRequests to get number of queries queued (5 min granularity)
- SPARQL federated query
    • Query across multiple Neptune clusters or external data sources that
    support the protocol, and aggregate the results
    • Supports only read operations
- Streams use cases - Amazon ES Integration, Neptune-to-Neptune Replication