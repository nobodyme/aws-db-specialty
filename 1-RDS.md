## Some points that I forget
- RDS also supports TDE (Transparent Data Encryption) for SQL Server (Enterprise Edition only) and Oracle DB instances. Might slightly affect DB performance if you use TDE and **encryption at rest** simultaneously
- RDS offers only upto 5 read replicas, and 5 cross region read replicas
- You cannot promote a replica to a standalone instance when backup is running
- PITR is 5 minutes but RTO is longer incase of DR.
- You can export log data from CloudWatch Logs to S3 by creating an export task in CloudWatch (create export-task CLI command)
- Set log retention with parameter rds.log_retention_period for postgresql
- For MySQL/MariaDB set log retention with stored procedures. e.g. call mysql.rds_set_configuration('binlog retention hours', 24);
- Does not support cloning, backtracking
- [Stopping RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_StopInstance.html)
- For a Multi-AZ deployment, a large amount of time might be required to stop a DB instance. If you have at least one backup after a previous failover, then you can speed up the stop DB instance operation by performing a reboot with failover operation before stopping the DB instance.
- You can't stop a DB instance that has a read replica, or that is a read replica.
- You can't stop an Amazon RDS for SQL Server DB instance in a Multi-AZ configuration.
- [Backups](https://aws.amazon.com/rds/faqs/) Automated backups are deleted when the DB instance is deleted. Only manually created DB Snapshots are retained after the DB Instance is deleted.
- Migration of DB Instances from inside to outside VPC is not supported. For security reasons, a DB Snapshot of a DB Instance inside VPC cannot be restored to outside VPC. The same is true with “Restore to Point in Time” functionality.
- MyISAM storage engine for RDS MySQL does not support automated backups, InnoDB and Aria engine support it.
- 100 manual snapshots per Region
- Can not copy RDS Snapshot to S3. Use **Export to S3** option

## Windows authentication
- Create AWS Managed Microsoft AD directory and setup trust relationship between your corporate AD and AWS Managed AD (called forest trust)
- AWS Managed AD is best choice if you have > 5000 users and need a trust relationship with your on-premise directory
- Alternatively, you can also use an AD connector (for an existing on-premise directory) or a Simple AD (if you have under 5000 users)
- Set up users and groups in the AD
- Enable SQL Server Windows Authentication in the RDS instance to map the directory to the DB instance (appropriate IAM role is created automatically)
- Login to DB with master user credentials and create SQL Server Windows logins for AD users
- Amazon Directory service provides this microsoft AD stuff

## Exams
- When using IAM database authentication with MySQL, you are limited to a maximum of 200 new connections per second. If you are using a db.t2.micro DB instance class, the limit is 10 connections per second.
- Go through table in this link, [details about Multi-AZ and read replicas differences in aurora and mysql](https://aws.amazon.com/rds/features/read-replicas/)
- [Read replica deletion](https://aws.amazon.com/rds/faqs/) An Amazon RDS for MySQL or MariaDB read replica will stay active and continue accepting read traffic even after its corresponding source DB instance has been deleted. If you desire to delete the Read Replica in addition to the source DB instance, you must explicitly do so using the DeleteDBInstance API or AWS Management Console.
- If you delete an Amazon RDS for PostgreSQL DB Instance that has read replicas, all Read Replicas will be promoted to standalone DB Instances and will be able to accept both read and write traffic. The newly promoted DB Instances will operate independently of one another. If you desire to delete these DB Instances in addition to the original source DB Instance, you must explicitly do so using the DeleteDBInstance API or AWS Management Console.
- [Cross region read replica deletion](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_DeleteInstance.html) For MariaDB, MySQL, and Oracle DB instances, when the source DB instance for a **cross-Region read replica** is deleted, the read replica is promoted.
- For PostgreSQL DB instances, when the source DB instance for a cross-Region read replica is deleted, the replication status of the read replica is set to `terminated`. The read replica isn't promoted. You have to promote the read replica manually or delete it.
- Create a new Option Group and configure SQLSERVER_BACKUP_RESTORE option.  Associate the option group with the DB instance. - to take native backup
- gp2 - 16k iops, io1 - 64k, sc1 - 500, st1 - 250

## Delete an instance in the cluster

Run the following command:

```plainText
aws rds delete-db-instance --db-instance-identifier sample-instance
```

You might receive one of the following error messages when trying to delete an instance in the cluster.

-   "InvalidParameterCombination: An error occurred (InvalidParameterCombination) when calling the DeleteDBInstance operation: FinalDBSnapshotIdentifier cannot be specified when deleting a cluster instance"
    
    You receive this error when you use the **--final-db-snapshot-identifier** option when you run the command to delete the instance in the cluster. This error warns you that you can't take a final snapshot when deleting an instance in the cluster. Either remove the **--final-db-snapshot-identifier** option or use the **--skip-final-snapshot** option, and then run the command again.
