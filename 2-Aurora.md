## Some points that I forget
- Disable binlog replication to improve crash recovery time, binlog_format = OFF
- Changing the parameter group associated with the cluster does not require reboot
- Aurora serverless only has cluster param group no instance, since there are no permanent instances
- Enable logs with server_audit_logging
- server_audit_logs_upload = 1, to upload logs to cloudwatch
- We can directly export logs to s3 from aurora, unlike RDS, where we need to export from cloudwatch console. Use, SELECT INTO OUTFILE S3, e.g. SELECT * FROM db.table INTO OUTFILE S3 s3_file_path FIELDS TERMINATED BY ‘,’ LINES TERMINATED BY ‘\n’;
- We cannot disable automatic backups in aurora
- Cross region replication must be disabled to use backtrack
- apg_ccm_enabled=1, for postgres to improve perf of a promoted instance post failover
- Cannot promote aurora read replica to a standalone db instance, can promote cross region read replicas though. Should enable bin logging for cross region read replicas
- Can stop cluster and not the individual instances
- Aurora MySQL engine uses InnoDB


## Other flavours of aurora
- Aurora parallel query is available only for aurora mysql engine
- Performance Insights, Backtrack (PITR) and IAM Authentication is not supported when parallel query is enabled
- Aurora Serverless compute layer is placed in a single AZ (not multi-AZ). Failover time is longer than a provisioned cluster.
- Enabling data API on serverless cluster, allows ine to access the cluster over secure HTTP endpoint.
- 15 minutes cooldown after a scale up operation and 310 second cooldown for subsequent cooldown, no cooldown for scaleup
- Aurora Global tables, RTO < 1 minute, RPO < 1 second, 5 secondary read-only regions and 16 read replicas in each
- Cannot stop aurora serverless, multi-master or global db or one that uses parallel query