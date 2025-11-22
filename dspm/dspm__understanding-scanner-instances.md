# Understanding Scanner Instances
Source: https://help.zscaler.com/dspm/understanding-scanner-instances
PDF: https://help.zscaler.com/pdf/com/en/1488341.pdf

DSPM creates transitory scanner instances in the respective regions to perform data scanning on different data stores such as storage, compute, and databases. The orchestrator instance creates the scanner instances with a unique identity. Zscaler's applications are installed in these scanner instances to perform data scanning. For each data store, DSPM creates up to a maximum of 10 scanner instances each with configuration of 16 vCPU and 32 GiB memory, depending upon the number of data stores that must be scanned.
You need to ensure that sufficient vCPU quotas are enabled in the [orchestrator](/dspm/understanding-orchestrator) account. Such high configurations are required as DSPM scans huge amounts of data, and a high configuration of scanner instances ensures data scans are completed faster than the lower configuration instances that take a longer duration to perform a data scan. The scanner instance automatically pushes the data scan results to DSPM.
All scanner instances are created with tags and the tags should not be deleted or tampered with. The image required to launch the scanner instance is property of Zscaler and it is shared with the customer’s orchestrator account for data scanning purposes. Inbound access to scanner instances is restricted only from the orchestrator instance.
The following tags are added to the scanner instances. You can enable these tags in AWS to track the cost allocation for DSPM. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/awsaccountbilling/latest/aboutv2/cost-alloc-tags.html).
- z-dspm-resource = true
- z-dspm-scanner-resource= true
- z-dspm-tenant-id = <tenant_id>
- z-dspm-tenant-name = <tenant_name>
- z-dspm-scan-id = <scan_id>
Default Scanner Instances
The scanner instances for the following cloud types:
- [AWS](#aws)
- [Azure](#azure)
- [GCP](#gcp)
[]
| Data Store Type | Scan Type | Instance Type | Instance Configuration | Disk Configuration |
| --------------- | --------- | ------------- | ---------------------- | ------------------ |
| S3 | Full Scan | c5a.4xlarge | 16 core vCPUs and 32 GiB Memory | Root Disk: 20 GB GP3 |
| S3 | Incremental Scan | t3.2xlarge | 8 core vCPUs and 16 GiB Memory | Root Disk: 20 GB GP3 |
| EC2 | Full Scan | c6in.4xlarge | 16 core vCPUs and 32 GiB Memory | Root Disk: 20 GB GP3 |
| RDS | Full Scan | c5a.12xlargedb.r5.large | 48 core vCPUs and 96 GiB Memory2 core vCPUs and 16 GiB Memory | Root Disk: 20 GB GP3 |
[]
| Data Store Type | Scan Type | Instance Type | Instance Configuration | Disk Configuration |
| --------------- | --------- | ------------- | ---------------------- | ------------------ |
| Blob Container | Full | Standard_F16s_v2 | 16 core vCPUs and 32 GiB Memory | 30 GB Premium SSD LRS |
| Blob Container | Incremental | Standard_D8s_v3 | 8 core vCPUs and 16 GiB Memory | 30 GB Premium SSD LRS |
| Virtual Machine | Full | Standard_F16s_v2 | 16 core vCPUs and 32 GiB Memory | 30 GB Premium SSD LRS |
| SQL ServerPostgreSQL-Flexible Server | Full | Standard_F16s_v2 | 16 core vCPUs and 32 GiB Memory | 30 GB Premium SSD LRS |
[]
| Data Store Type | Scan Type | Instance Type | Instance Configuration | Disk Configuration |
| --------------- | --------- | ------------- | ---------------------- | ------------------ |
| Cloud Storage Bucket | Full | e2-standard-16 | 16 core vCPUs and 64 GiB Memory | 20 GB Standard persistent disk |
| Cloud Storage Bucket | Incremental | e2-standard-8 | 8 core vCPUs and 32 GiB Memory | 20 GB Standard persistent disk |