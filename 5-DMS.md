## Some things I forget
- SCT tools require db drivers to be installed to perform assesment or schema change
- Converts DB/DW schema from source to target (including procedures / views / secondary indexes / FK and constraints)
- Mainly for heterogeneous DB migrations and DW migrations
- For homogeneous migrations, can use it for migration assessment
- Can be installed on EC2 or locally on your computer (closer to source DB)
- Application conversion – can convert SQL statements embedded in the application code
- Script conversion – can convert ETL scripts (Oracle / Microsoft / Teradata scripts àAurora / Redshift scripts)
- Can optimize schemas in Redshift (recommends distribution and sort keys, different from native Redshift advisor)
- Can monitor task progress by:
    • checking the task status
    • using the task’s control table
    • or with CloudWatch
- Certain DMS issues / warnings / error messages appear only in the task log
    • e.g. data truncation issues or row rejections due to FK violations are only written to the task log
- SCT extractors do not support validation. Only DMS does.
- **describe-table-statistics** to receive the data validation report in JSON format
- Validation errors and diagnostic info is written to a table named **awsdms_validation_failures_v1** at the target endpoint

## PostgreSQL Migration

- From PostgreSQL (on-premises / EC2)
    • One time – use pg_dump / pg_restore (some downtime)
- From CSV data stored on S3
    • Use aws_s3 PostgreSQL extension and import data using the aws_s3.table_import_from_s3 function (some downtime)
- From PostgreSQL on RDS (large DBs)
    • Use pg_transport extension (streams data, is extremely fast, minimal downtime)

## SQL Server Migration

- From SQL Server (on RDS)
    • Restore from a snapshot
    • Or use native backup and restore feature
    • Or use SQL Server Management Studio
- From SQL Server (on-premises / EC2)
    • Use native backup and restore (.bak backup files stored on S3)
    • Supports encryption and compression
    • Or use SQL Server Management Studio

## Redis Online Migration

- Source cluster
    • must have Redis AUTH disabled
    • must have “protected-mode”
    disabled
    • “bind” config if present should allow
    requests from ElastiCache
- Target cluster
    • must have Cluster-mode disabled
    • must have Multi-AZ enabled
    • must have Encryption disabled
    • must have sufficient memory