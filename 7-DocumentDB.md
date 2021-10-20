## Some points that I forget

- Default auth - SCRAM (Salted Challenge Response Authentication Mechanism)
- To enable TLS, set tls parameter in cluster parameter group
- Profiler and Audit Logs can be published to Cloudwatch 
- Profile Logs - identify slow queries, details of ops performed on cluster
- To enable profiler logs:
    • Set the parameters – profiler, profiler_threshold_ms, and profiler_sampling_rate
    • Enable Logs Exports for Audit logs by modifying the instance
    • Both the steps above are mandatory
- Audit Logs - records DDL statements, authentication, authorization, and user management events to CloudWatch Logs
- To enable auditing:
    • Set parameter audit_logs=enabled
    • Enable Logs Exports for Audit logs by modifying the instance
    • Both the steps above are mandatory
- explain command to identify slow queries ```db.runCommand({explain: {<query document>}})```
- db.adminCommand to find and terminate queries ```db.adminCommand({killOp: 1, op: <opid of the query>});```