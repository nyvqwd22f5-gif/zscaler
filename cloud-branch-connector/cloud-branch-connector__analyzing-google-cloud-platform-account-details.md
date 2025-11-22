# Analyzing Google Cloud Platform Account Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-google-cloud-platform-account-details
PDF: https://help.zscaler.com/pdf/com/en/1528942.pdf

The Google Cloud Platform (GCP) account details page provides general and management information for a selected GCP account. You can access the GCP account details page by clicking the name of an account on the [GCP accounts](/cloud-branch-connector/about-google-cloud-platform-accounts) page.
Analyzing the GCP Account Details Page
On the GCP account details page, you can view the following:
- [Dashboard](#dashboard)
- [Regions](#regions)
- [Pub/Sub](#pubsub)
[]
On the **Dashboard** tab, you can configure or view the following:
- From the **Manage Account** drop-down menu, you can manage or delete your Google Cloud account by selecting one of the following options:
- **Edit**: Edit the account details. To learn more, see [Adding a Google Cloud Platform Account](/cloud-branch-connector/adding-google-cloud-platform-account).
- **Delete**: Delete the account, which causes the Zscaler service to remove access information for this account.
- In the **Account Details** section, view the following account details:
- **Name**: The name of the GCP account.
- **Zscaler Service Account Email**: The email address used to deploy the GCP account without Terraform.
- **Customer Service Account Email**: The email address, entered when adding a GCP account, that gives the Zscaler service permission to use the service account to discover workloads.
- In the **Projects and Regions** section, view the following:
- **Projects**: View the selected projects that are visible to the Zscaler service. You can select a region to view the Regions table.
- **Regions**: View the selected regions that the GCP account operates within.
- In the **Cloud Connector Groups - Pub/Sub** section, view the following Cloud Connector groups and publish/subscribe details:
- **Cloud Connector Groups**: View the Cloud Connector groups associated with this GCP account.
- **Pub/Sub**: GCP publish/subscribe is a messaging service that allows services to communicate asynchronously by sending messages to topics which are delivered to all subscribers.
- **Download Script**: Click **Download Script** to download the ZIP file containing **core_infra** and **centralized_grants**. It uses **core_infra** to create service accounts, IAM roles, and logging sinks. It uses **centralized_grants** to grant cross-project workload discovery permissions. This Terraform deployment package automates onboarding configuration for the workload discovery service. It creates or configures the service account with IAM roles, grants impersonation rights to the Zscaler SaaS service account, sets up logging sinks for VM start events, and configures Pub/Sub subscriptions for workload change events.
- Filter the GCP projects table by the following:
- **Projects**: The GCP project within the account.
- **Permissions**: The permission status of the GCP project within the account (i.e., **Allowed**, **Pending**, **Denied**, or **N/A**).
- **Status**: The status of the GCP project within the account (i.e., **Enabled** or **Disabled**).
- Search for a GCP project.
- Apply actions to a group of selected GCP projects:
- **Disable**: Disable the projects.
- **Enable**: Enable the projects.
- **Refresh**: Refresh the projects.
- View a list of Google Cloud accounts. For each account, you can view:
- **Projects**: The list of GCP projects you selected when creating the GCP account.
- **Permissions**: The permissions allowed for the GCP project (i.e., **Allowed**, **Pending**, **Denied**, or **N/A**).
- **Last Modified On**: The date and time when the GCP project was last modified.
- **Last Sync**: The date and time when the GCP project was last synced.
- **Last Modified By**: The last admin to modify the GCP project.
- Modify the table and its columns.
- Refresh the GCP project details.
![The dashboard details for a Google Cloud account accessed via the GCP Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-dashboard.png)
[]
On the **Regions** tab, select a region from the list to view the following:
-
**Projects**: If you select a project, you can view the following:
- **Private IP Address**: The private IP address of the workload. You can select a private IP address to view its details. If you select a private IP address, you can view the following:
-
**Attributes**: The following attributes listed apply to the workload group. When you create a workload group, you do not see the virtual network (VNet), but you do see the virtual private cloud (VPC). You can only use certain attributes in policies. The following list indicates which attributes you can use:
- **Resource Group**: The name of the resource group assigned to the workload.
- **Image ID**: The SKU for the virtual machine (VM) image assigned to the workload. You can use this attribute in policies.
- **Platform**: The platform (i.e., Linux/UNIX or Windows) that the workload is operating on. You can use this attribute in policies.
- **VM ID**: The ID of the VM assigned to the workload.
- **Security Group ID**: The ID of the network security group assigned to the workload. You can use this attribute in policies.
- **VPC**: The VPC assigned to the workload.
- **Subnet ID**: The ID of the subnet assigned to the workload.
- **Network Interface ID**: The ID of the network interface assigned to the workload.
- **Security Group Name**: The name of the security group assigned to the workload. You can use this attribute in policies.
[See image.](#attributes)
-
**User-Defined Tags**: The table lists the following information about user-defined tags, which apply to the workload group in GCP projects:
- **Resource Type**: The type of resource is listed (i.e., VM, VPC, or ENI). VPCs can relay to VNets in GCP. Elastic network interfaces (ENIs) are specific to AWS.
- **Key**: The tag key string information.
- **Value**: The tag value string information.
[See image.](#userdefinedtags)
- **User-Defined Tags**: The number of user-defined tags assigned to the workload.
- **VPC**: The VPC assigned to the workload.
- **Last Discovery**: The last discovery the GCP project made.
[See image.](#privateipaddress)
- **Private IP Addresses**: The number of private IP addresses discovered in the GCP project.
- **Discovery Service Status**: The status of the discovery service (i.e., **Starting**, **Success**, or **Error**).
-
**Last Sync**: The date and time when the GCP project was last synced.
[See image.](#projectsregions)
[]
On the **Pub/Sub** tab, you can view the following:
- **Region**: The region of the GCP project.
- **Topic Discovery**: This field displays the information that the topic discovery communicates, such as resource change notifications like VM creation, to the tag service. It is created by CloudFormation.
- **Topic Cloud Connector**: This field displays the information that the topic Cloud Connector communicates, such as any changes to tags associated with the Cloud Connector over this topic. It is created by CloudFormation.
-
**Last Sync**: The date and time when the Pub/Sub was last synced.
[See image.](#pubsubdetails)
[]
![The GCP project attributes section from the private IP address table of the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-attributes.png)
[]
![The GCP project user-defined tags section from the private IP address table of the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-userdefinedtags.png)
[]
![The GCP project private IP address table on the GCP details Partner Integrations page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-privateipaddress.png)
[]
![The GCP projects table accessed by selecting a region on the Partner Integrations page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-projects.png)
[]
![The Pub/Sub detail table, including the Region, Topic Discovery, Topic Cloud Connector, and Last Sync information in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-google-cloud-platform-account-details/gcptagging-pubsubdetails_0.png)