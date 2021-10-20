## Some points that I forget
- 1-128 nodes upto 160 GB per node and Not Multi-AZ
- Leader node aggregates results from computes nodes and sends it back to client
- DC2, DS2, RA3 (automatically offloads data to s3, when it goes beyond it's size)
- Spectrum is only used for querying s3
- Federated query across DWs, OLTP DBs(postgres) and S3
- Does not support indexes
- Supports automatic workload management and manual - requires reboot
- Also supports short query accelaration
- Concurrency scaling mode = auto / queue
- Cluster is unavailable during horizontal scaling (elastic resize) - I don't think this applies to spectrum
- Can configure redshift to automatically copy snapshots across region
- Performance debugging in redshift console
- Redshift advisor - cost optimization and perf tuning
- AQUA (Advanced query accelarator) similar to DAX for redshift

## Efficient table design
- Data distribution - ALL, EVEN, KEY, AUTO
- Sort strategies - Simple, compound, Interleaved 
- Compression - cannot be changed after table is created
- LZO (high compression), RAW (no compression)