# Analyzing Microsoft Azure Account Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-microsoft-azure-account-details
PDF: https://help.zscaler.com/pdf/com/en/1507806.pdf

The Microsoft Azure Account Details page provides general and management information for a selected Azure account. You can access the Azure Account Details page by clicking the **Regions**, **Subscriptions**, **Cloud Connectors**, or **Event Grid** number on the [Azure accounts](/cloud-branch-connector/about-microsoft-azure-accounts) page for a selected Azure account.
Workload discovery services for Azure are in Limited Availability (LA). To request this feature, contact Zscaler Support.
Analyzing the Azure Account Details Page
On the Azure account details page, you can view the following:
- [General](#general)
- [Regions Workload Inventory](#regionsworkloadinventory)
- [Permissions](#permissions)
- [Cloud Connectors](#cloudconnectors)
- [Event Grid](#eventgrid)
- [Storage Account](#storageaccount)
[]
- **Account Name**: The name used when creating the Azure account.
- **Directory ID**: The Directory (tenant) ID used in the service principal credential.
- **Application ID**: The client/application ID used in the service principal credential.
- **Last Modified By**: The last admin to modify the account.
- **Last Modified On**: The date and time the account was last modified.
[]
The Regions Workload Inventory section shows a list of selected regions for the Azure account.
[See image.](#regionsinfo)
Supported regions for Azure include:
- westeurope
- eastus
- eastus2
- uksouth
- northeurope
- centralindia
- southeastasia
- australiaeast
- germanywestcentral
- southcentralus
- westus2
- westus
- canadacentral
You can select a region to find the workload inventory. If you select a region, you can view the following:
- **Subscriptions**: The subscriptions associated with the region. You can select a subscription to view its details. If you select a subscription, you can view the following:
- **Private IP Address**: The private IP address of the workload. You can select a private IP address to view its details. If you select a private IP address, you can view the following:
- **Attributes**: The following attributes listed apply to the workload group. When you create a workload group, you do not see the virtual network (VNet), but you do see the virtual private cloud (VPC). You can only use certain attributes in policies. The following list indicates which attributes you can use:
- **Resource Group**: The name of the resource group assigned to the workload.
- **Image ID**: The virtual machine (VM) image SKU assigned to the workload. You can use this attribute in policies.
- **Platform**: The platform (i.e., **Linux/UNIX** or **Windows**) that the workload is operating on. You can use this attribute in policies.
- **VM ID**: The ID of the VM assigned to the workload.
- **Security Group ID**: The ID of the network security group assigned to the workload. You can use this attribute in policies.
- **VNET**: The VNet assigned to the workload. In policies, when creating workload groups, the drop-down field to configure this field is **VPC**. Although it is labeled VPC, you can enter VNet ID values. You can use this attribute in policies.
- **Subnet ID**: The ID of the subnet assigned to the workload.
- **Network Interface ID**: The ID of the network interface assigned to the workload.
- **Security Group Name**: The name of the security group assigned to the workload. You can use this attribute in policies.
-
**User Defined Tags**: The following user-defined tags apply to the workload group in Azure subscriptions:
- **Resource Type**: The type of resource is listed (i.e., **VM**, **VPC**, or **ENI**). VPCs can relay to VNets in Azure. Elastic network interfaces (ENIs) are specific to AWS.
- **Key**: The tag key string information for user-defined tags.
- **Value**: The tag value string information for user-defined tags.
[See image.](#privateIPaddress)
- **User Defined Tags**: The number of user-defined tags assigned to the workload.
- **Namespace**: The namespace assigned to the workload.
- **VNET**: The VNet assigned to the workload.
-
**Last Updated**: The last time the workload was updated.
[See image.](#subscriptions)
- **Duplicate IP Addresses**: The number of duplicate IP addresses discovered in the Azure subscription.
- **Private IP Addresses**: The number of private IP addresses discovered in the Azure subscription.
- **Receive Count**: The number of messages received over the partner destination.
- **Sent Count**: The number of messages sent over the partner topic.
-
**Discovery Service Status**: The status of the discovery service (i.e., **Starting**, **Success**, or **Error**).
[See image.](#regions)
[]
The Permissions list shows you a list of subscriptions that your credentials can access and that you have selected for this account.
- **Azure Subscription ID**: The subscription ID of the Azure account.
- **Permission**: The permission status of the Azure account (i.e., **Pending**, **Allowed**, or **Denied**). When you click **Refresh**, the state of the permission updates.
-
**Last Sync**: The last time the Azure account was refreshed. If you have never refreshed the account, it is **Pending**.
[See image.](#permissionsinfo)
[]
The Cloud Connectors list shows you the Cloud Connectors associated with the Azure account.
- **Cloud Connector Groups**: The Cloud Connector group(s) that receive the tag information.
-
**Namespace (Optional)**: The namespace that limits the IP addresses sent to the Cloud Connector and ensures that duplicate IP addresses map correctly.
[See image.](#cloudconnectorsinfo)
[]
The Event Grid list shows the event grids and their details that are associated with the Azure account. The workload discovery service communicates through API calls and a publish-subscribe mechanism based on the event grid and storage queue.
- **Regions**: The list of regions selected when the Event Grid was created.
- **Subscriptions**: The subscription associated with the event grid.
- **Resource Groups**: The resource group associated with the event grid.
- **Topic Status**: The topic status of the Azure account (i.e., **Activated**, **Created**, or **Unavailable**).
- **Destination Status**: The destination status of the Azure account (i.e., **Activated**, **Created**, or **Unavailable**).
- **Received Messages**: The number of messages that the partner destination has received since the creation of this destination.
- **Sent Messages**: The number of messages that the partner topic has sent since the creation of this topic.
-
**Last Sync**: The last time the Azure account was refreshed.
[See image.](#eventgridinfo)
[]
The Storage Account list shows you the storage account details associated with the Azure account.
- **Regions**: The list of regions selected when the Event Grid was created.
- **Resource Groups**: The resource group associated with the storage account used to create the partner topic and partner destination.
- **Storage Account**: The storage account associated with the storage account used to create the partner topic and partner destination.
-
**Prefix**: The name of the storage queue which is added to the name of the queue so you can organize the queues.
[See image.](#storageaccountinfo)
[]
![Regions Workload Inventory information from the Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-dashboard-details/regionsinfo.png)
[]
![Permissions information from the Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-dashboard-details/permissionsinfo.png)
[]
![Cloud Connectors information from the Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-details/CloudConnectors.png)
[]
![Event Grid information from the Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-dashboard-details/eventgridinfo.png)
[]
![Storage Account information from the Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-dashboard-details/storageaccountinfo.png)
[]
![Regions information from the Regions Workload Discovery Microsoft Azure Account Details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-details/regions.png)
[]
![Private IP address information from the Regions Workload Discovery Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-details/privateIPaddress.png)
[]
![Subscriptions information from the Regions Workload Discovery Microsoft Azure account details page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-microsoft-azure-account-details/subscriptions.png)