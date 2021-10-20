## Some points that I forget

- Uses query language named PartiQL (SQL-like, Open standard)
- Uses Amazon ION format
- QLDB offers three views of your data
- User view
    • latest version of your data
    • default view
- Committed view
    • user view + system generated metadata
- History view
    • contains all historical document revisions
    • i.e. all change history with metadata
- Can only export your QLDB journal to S3
    • For analytics / auditing / data retention / verification / exporting to other systems
    • limit of two concurrent journal export jobs
- Doesn't support Backups, CRR, and PITR
- QLDB Streams