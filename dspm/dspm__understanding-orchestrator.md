# Understanding Orchestrator
Source: https://help.zscaler.com/dspm/understanding-orchestrator
PDF: https://help.zscaler.com/pdf/com/en/1478006.pdf

As organizations transition to the public cloud to maintain their cloud infrastructure, ensuring data security becomes a critical concern due to several factors like shared infrastructure, risk of data breaches, compliance requirements such as GDPR and HIPAA, potential data loss, etc. It is essential for organizations to prioritize robust security measures, including encryption, regular audits, and data loss prevention scans to protect against unauthorized access and safeguard sensitive information.
To achieve maximum protection for sensitive data in the public cloud, it is essential to perform posture assessments and data scans regularly. Traditionally, these scans were performed on the data after moving them out of the organization's cloud environment. This approach leads to multiple challenges such as data privacy concerns, cost associated with data transfer, preferences to keep the data within the organization, etc.
To overcome these challenges, Zscaler provides a local scanner platform called orchestrator, a cloud security solution deployed in your organization that performs data scanning within the organization's public cloud environment. The local scanner platform architecture consists of an orchestrator instance and scanner instances. An orchestrator instance is an EC2 instance, virtual machine, or a cloud storage that organizes the data scanning across the selected regions of AWS, Azure, and GCP. The [scanner instances](/dspm/understanding-scanner-instances) are created by the orchestrator instance and are launched in the respective regions where DSPM performs data scanning of the resources.
The orchestrator instance includes tags that should not be deleted or tampered with. The image required to set up the orchestrator instance is a property of Zscaler and is shared with the customer's orchestrator account.
You need to choose an account in your environment and the primary region in which Zscaler's DSPM orchestrator template is deployed. This account is referred to as the orchestrator account. DSPM leverages the template deployed in the orchestrator account to scan the data stores (S3 bucket, EC2 workloads, etc.) of the target accounts. The orchestrator instance is moved to the selected primary region where it organizes the data scan. The orchestrator instance is backed by an autoscaler that ensures atleast one orchestrator is running. The target account might have data stores across multiple regions. The scanner instances are launched with a unique identity in the corresponding regions of the orchestrator account where the target data stores are available. The data from the target account's data stores is moved to the scanner instances in the corresponding regions of the orchestrator account. After the scan is complete, the scanner instances are terminated. For example, if the target account has data stores in 5 regions, then scanner instances are launched in those same 5 regions of the orchestrator account. The data is then moved to these 5 scanner instances to be scanned for sensitive data. This ensures data scanning within your public cloud environment and avoids interregional data transfer costs.
- The orchestator instance requires only outbound internet access to communicate with DSPM. Outbound connections from the orchestrator instance to download scanner images and upload results and logs to DSPM cloud are limited to the following specific service IPs:
- [DSPM IPs for US Cluster](#IPs-for-US)
- [DSPM IPs for Europe Cluster](#IPs-for-EU)
- DSPM supports scanning of data stores present in all global regions of AWS, Azure, and GCP.
The supported orchestrator instance types and configurations are as follows:
-
-
-
-
-
-
| Cloud Service Provider | Instance Type | Instance Configuration | Disk Configuration |
| ---------------------- | ------------- | ---------------------- | ------------------ |
| AWS | t3.large | 2 core vCPUs and 8 GiB Memory | Root Disk: 20 GB GP3Data Disk: 16 GB GP3 |
| Azure | Standard_D2s_V3 | 2 core vCPUs and 8 GiB Memory | Root Disk: 30 GB Standard HDD LRSData Disk: 10 GB Standard HDD LRS |
| GCP | e2-standard-2 | 2 core vCPUs and 8 GiB Memory | Root Disk: 20 GB Standard persistent diskData Disk: 10 GB Standard persistent disk |
- []54.188.198.110
- 52.38.65.228
- 35.162.237.153
- 54.203.244.84
- 100.20.13.195
- 44.232.83.106
- []3.78.36.199
- 18.153.255.114
- 18.193.231.22
- 35.157.194.12
- 35.159.181.237
- 3.78.50.170