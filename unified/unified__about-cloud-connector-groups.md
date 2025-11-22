# About Cloud Connector Groups
Source: https://help.zscaler.com/unified/about-cloud-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1518881.pdf

Cloud Connector Groups are automatically created when a Zscaler Cloud Connector is deployed in Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).
Cloud Connector Groups provide the following benefits and enable you to:
- Apply policies to a group of deployed Cloud Connectors.
- Upgrade Cloud Connectors belonging to a group to maintain redundancy while upgrades are being executed.
About the Cloud Connector Groups Page
On the Cloud Connector Groups page (Infrastructure > Connectors > Cloud > Cloud Connector Groups), you can do the following:
- View the following details of the Cloud Connector Group.
- **Name**: The name of the Cloud Connector Group.
- **Cloud Provider Type**: The cloud provider, which can be AWS, Azure, or GCP.
- **Location**: The location where the Cloud Connector Group is deployed.
- **Availability Zone**: The availability zone where the Cloud Connector is deployed.
-
**Auto Scaling**: The status of auto scaling (i.e., **True** or **False**). Zscaler supports Auto Scaling in AWS and Azure, but does not support Auto Scaling for GCP.
In the AWS Marketplace, Auto Scaling is referred to as Auto Scaling. In the Azure Marketplace, Auto Scaling is referred to as Virtual Machine Scale Sets (VMSS). In the Zscaler Cloud & Branch Connector Admin Portal, references to Auto Scaling also refer to VMSS. To enable Auto Scaling or VMSS, contact Zscaler Support.
- **Upgrade Window**: The window of time scheduled for performing the Cloud Connector upgrades.
- **Operational Status**: The operational status (**Active**, **Inactive**, or** Disabled)** of the Cloud Connector.
- **Upgrade Status**: The status of the scheduled upgrade. To learn more, see [Managing Cloud & Branch Connector Upgrades](/unified/managing-cloud-branch-connector-upgrades).
- View more details about a Cloud Connector group. When a GCP instance deployed in an instance group is deleted, it is replaced by a new one. The new instance appears in this section.
- Edit the Cloud Connector Group or Cloud Connector. To learn more, see [Editing Cloud Connectors](/unified/editing-cloud-connectors).
- Delete the Cloud Connector. This action cannot be undone.
- Modify the table and its columns.
- Search for a Cloud Connector or Cloud Connector Group.
![Cloud Connector Groups page](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/about-cloud-connector-groups/About%20Cloud%20Connector%20Groups3.png)