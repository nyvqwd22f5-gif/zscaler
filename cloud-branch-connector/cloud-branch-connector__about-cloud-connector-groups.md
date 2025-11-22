# About Cloud Connector Groups
Source: https://help.zscaler.com/cloud-branch-connector/about-cloud-connector-groups
PDF: https://help.zscaler.us/pdf/com/en/1420476.pdf

Cloud Connector groups are automatically created when you deploy a Zscaler Cloud Connector in Amazon Web Services (AWS), Microsoft Azure, or Google Cloud Platform (GCP).
Cloud Connector groups provide the following benefits and enable you to:
- Apply policies to a group of deployed Cloud Connectors.
- Upgrade Cloud Connectors belonging to a group to maintain redundancy while upgrades are being executed.
About the Cloud Connector Groups Page
On the Cloud Connector Groups page (Administration > Cloud Connector Groups), you can do the following:
- Search for a Cloud Connector group or an individual Cloud Connector.
- View the following Cloud Connector group details:
- **Name**: The name of the Cloud Connector group.
- **Cloud Provider Type**: The cloud provider type (i.e., **AWS**, **Azure**, or **GCP**).
- **Group Type**: The Cloud Connector group type (i.e., **Cloud Connector** or **Zero Trust Gateway**).
- **Location**: The location where the Cloud Connector group is deployed.
- **Availability Zone**: The availability zone where the Cloud Connector is deployed.
-
**Auto Scaling**: The status of Auto Scaling (i.e., **True** or **False**). Zscaler supports Auto Scaling in AWS and Azure, but does not support Auto Scaling for GCP.
In the AWS Marketplace, Auto Scaling is referred to as Auto Scaling. In the Azure Marketplace, Auto Scaling is referred to as Virtual Machine Scale Sets (VMSS). In the Zscaler Cloud & Branch Connector Admin Portal, references to Auto Scaling also refer to VMSS. To enable Auto Scaling or VMSS, contact Zscaler Support.
- **Upgrade Window**: The window of time scheduled for performing the Cloud Connector upgrades.
- **Operational Status**: The operational status (i.e., **Active**, **Inactive**, or** Disabled**) of the Cloud Connector.
- **Upgrade Status**: The status of the scheduled upgrade. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
- Modify the table and its columns.
- Select a Cloud Connector group or multiple individual Cloud Connector checkboxes to apply actions to the selected Cloud Connectors:
- **Schedule Upgrade**: Designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
- **Enable**: Enable an individual Cloud Connector or group of Cloud Connectors.
- **Disable**: Disable an individual Cloud Connector or group of Cloud Connectors, which stops traffic from processing. Disabling a Cloud Connector does not delete it.
- View more details about a Cloud Connector group. When a GCP instance deployed in an instance group is deleted, it is replaced by a new one. The new instance appears in this section of the table.
- Edit a Cloud Connector group or an individual Cloud Connector. To learn more, see [Editing Cloud Connectors](/cloud-branch-connector/editing-cloud-connectors).
- Delete a Cloud Connector. This action cannot be undone.
![The Cloud Connector Groups accessed from the Administration tab of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/about-cloud-connector-groups/AboutCloudConnectorGroups.png)