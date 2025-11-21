# Viewing the Graph for AWS Data Stores
Source: https://help.zscaler.com/dspm/viewing-graph-aws-data-stores
PDF: https://help.zscaler.com/pdf/com/en/1519996.pdf

The Resource Inventory graph for AWS data stores is a visual representation of the scan result. The graph provides in-depth details of the [AWS resource](/dspm/supported-data-stores) that contains sensitive data, the DLP engines and dictionaries that match the sensitive data, whether it is publicly exposed to the internet, including the public exposure path, the list of entities that can access the resource, and the vulnerabilities and malware detected in the resource. These details are helpful to quickly evaluate and remediate the issues, protect the data, and maintain the security posture.
You can view graphs for the following AWS data stores:
- Simple Storage Service (S3)
- AWS EC2 instances
- RDS instance and clusters (MySQL, PostgreSQL, Aurora MySQL, Aurora PostgreSQL)
- AWS Dynamo DB tables
- NoSQL data stores (DynamoDB tables)
- Unmanaged PostgreSQL, MySQL server, Microsoft SQL servers and databases, Oracle Instance, and Oracle PDB
- AWS Bedrock Knowledge Base
- AWS Databricks
The following graph depicts the scan results for an AWS EC2 instance.
[]
![Graph that shows all the resources associated with an EC2 instance.](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-aws-graph.png)
The graph includes the following nodes:
- [1. Primary Resource](#ds_primary_resource)
- [2. Public Exposure Path](#ds-pepath)
- [3. Impacted Volume](#ds-volumewithdata)
- [4. Sensitive Records](#ds-nodes)
- [5. Volumes](#ds-allvolumes)
- [6. CVE](#ds-cves)
- [7. Malware](#aws_malware)
- [8. External](#ds-external)
- [9. Services](#ds-services)
- [10. Roles](#ds-roles)
- [11. Users](#ds-users)
- [12. Federated](#federated-identities)
[]View the following details of the primary resource:
- **Data Store Type**: The type of data store.
- **Resource Type**: The primary resource.
- **Account ID**: The unique identifier of the account in which the resource is located.
- **Account Name**: The name of the account in which the resource is located.
- **Organization ID**: The unique identifier of the organization to which the account belongs.
- **Region**: The region where the organization is located.
- **Latest Scan Status**: The status of the last scan.
- **Last Completed Scan**: The date and time when the last scan was completed.
- **Data Scanned**: The amount of data scanned.
- **Triggers**: The number of alerts raised for this resource.
- **Matched Files**: The number of files that matched the DLP engines.
- **DLP Engines**: The [DLP engines](/dspm/understanding-dlp-engines-and-dictionaries) that match the sensitive records.
- **DLP Dictionaries**: The dictionaries associated with the DLP engines.
- **Document Types**: The number of documents detected in the resource.
- **ARN**: Copy the Amazon Resource Name (ARN) to identify this resource in the AWS account.
- **Tags**: The tags associated with the resource.
- **Posture**: The [security posture](/dspm/understanding-security-posture-state) of the resource.
- **Metadata**: Click to view the metadata for the resource.
![AWS resource properties along with the scan details.](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-aws-datastores-accountname.png)
[]View the details of the EBS volume that contains sensitive data.
[![Details of the volume associated with the primary resource.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/AWS%20Impacted%20Volume_new.png)
](/dspm/understanding-security-posture-state)
[]View all the volumes, including those that do not contain any sensitive data and the ones that are not scanned. In this scenario, the EC2 instance has two volumes that contains sensitive data.
![The list of EBS volumes associated with the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-allvols.png)
[]View the services that can access the resource.
![The service that is associated with the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-services1.png)
[]View the list of users who can access the resource.
![Users who can access the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-users.png)
[]View the identity and access management (IAM) roles that has permissions to access the resource.
![Roles that have access to the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-roles.png)
[]View the publicly exposed resources. Click **Show Public Exposure Path** to view another graph that depicts how the resource is publicly exposed. To learn more, see [Viewing the Public Exposure Path](/dspm/viewing-public-exposure-path). [See image.](#ds-pegraph)
![The entity that has publicly exposed the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-pepath.png)
[]View the common vulnerabilities and exposure (CVE) details. Click **View All CVEs** to see the [vulnerability details](/dspm/viewing-vulnerability-details).
![View the vulnerabilities classified by severity](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-cvebalcony.png)
[]View the details of a sensitive record.
![The file that contains sensitive data.](/downloads/dspm/analytics/graphs/viewing-data-inventory-graph/AWS%20Sensitive%20Records_new.png)
[]![The public exposure graph with the entities that are misconfigured.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-gcp-graph-draft/AWS%20Public%20Exposure%20Path%202.png)
[]View the federated identities that can access the resource.
![The federated entities that can access the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-federatedentity.png)
[]View the external entities that can access the resource. These entities are part of a different cloud account that is not onboarded to the DSPM Admin Portal.
![External users that can access the primary resource](/downloads/dspm/analytics/graphs/viewing-graph-aws-data-stores/ds-di-aws-externalusers.png)
[]View the malware detected in the resource. Click **View All Malware **to see the [malware details](/dspm/viewing-malware-details).
[![Malware files detected in the primary resource.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-gcp-graph-draft/AWS%20Malware.png)
](/dspm/viewing-malware-details)