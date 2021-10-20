## Some points that I forget
- Supports item sizes upto 400KB
- Throttling can occur if you exceed 2x the previous peak within 30 minutes in on-demand mode
- Can define upto 5 LSI, can only be created at the time of creating the table and cannot be deleted later.
- Can define upto 20 GSIs
- 3000 RCUs and 1000 WCUs - max supported throughput / partition
- Can scale down 4 times a day, then one scale down if no scale down in 4 hrs, total 9
- Copy table using, data pipeline (EMR) or through code or backup and restore.
- Backups are quick, RPO is 5 minutes but RTO takes long as it has to create a new table.
- Backups are preserved regardless of table deletion
- Restores can be in same region or cross region
- Restore table which is part of global table won't be a global table anymore
- Only one replica / region for global tables
- Contributor insights for performance debugging
- Throughput exceeded exception returns a 400 error code
- Prevent delete - dynamodb:DeleteTable - explicit deny - similar to deletion protection in RDS
- DynamoDB does not support automated backups
- For short bursts of traffic spikes, autoscaling is not the right option, switch to on-demand mode

## DAX
- Updates to item cache does not invalidate query cache 
- 10 nodes per cluster, minimum 3 recommended for prod

## Fancy use cases
- Indexing s3 objects metadata, while storing objects in s3, we can store it's location and metadata in dynamo to enable searching and filtering items, like search by date or total storage used by customer etc.