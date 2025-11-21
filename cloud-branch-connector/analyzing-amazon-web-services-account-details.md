# Analyzing Amazon Web Services Account Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-amazon-web-services-account-details
PDF: https://help.zscaler.com/pdf/com/en/1529425.pdf

The Amazon Web Services (AWS) account details page provides general and management information for a selected AWS account. You can access the AWS account details page by going to the Partner Integrations page and clicking the name of an account on the [AWS Accounts](/cloud-branch-connector/about-amazon-web-services-accounts) page.
Analyzing the AWS Account Details Page
On the AWS account details page, you can view the following:
- **Account Name**: The name of the AWS account.
- **External ID**: The ID in the trust relationship of the IAM role that calls AWS while fetching the tag information.
- **Last Modified On**: The date and time when the AWS account was last modified.
- **Last Modified By**: The admin who last modified the AWS account.
- **Role Name**: The name of the role in your account that Zscaler uses to fetch data.
- **Trusted Account ID**: The ID of the Zscaler account that is required in the AWS trust policy.
- **Event Bus Name**: The name of the event bus that sends notifications to the Zscaler service using EventBridge. This event bus is the target of the EventBridge. To learn more, see [Configuring Workload Discovery for Workloads in Amazon Web Services](/cloud-branch-connector/configuring-workload-discovery-workloads-amazon-web-services).
-
**Trusted Role**: The Zscaler role that assumes the role name provided, which is required for the AWS trust policy.
[See image.](#awsaccountdetails)
In the **Regions** section, you can view a table of regional information:
- **Name**: The name of the region. Select the name of a region to view the Workloads table and its details:
-
**Private IP Address**: The private IP address of the workload. Select a private IP address to view the following:
- [Attributes](#attributes)
- [User-Defined Tags](#userdefinedtags)
- **VPC ID**: The ID of the VPC assigned to the workload. You can use this attribute in policies.
- **Namespace**: A set of VPC endpoints. To learn more, see [Understanding Namespaces for Amazon Web Services and Microsoft Azure Accounts](/cloud-branch-connector/understanding-namespaces-amazon-web-services-and-microsoft-azure-accounts).
- **User-Defined Tags**: The number of user-defined tags in the workload.
-
**Last Updates**: The date and time when the workload was last modified.
[See image.](#workloaddetails)
- **Discovery Service Status**: The status of the discovery service. The following statuses are the most commonly displayed:
- **Success**: The service is running as expected.
- **Disabled**: The service is disabled. To re-enable data collection, go to the [AWS Accounts](/cloud-branch-connector/about-amazon-web-services-accounts) page.
- **Error**: The service has discovered an issue.
- **Starting Discovery**: Data collection has not been started.
- **No of Duplicates IP**: The number of duplicate IP addresses in the region. If you have any duplicate IP addresses in a region, use namespaces to resolve them.
-
**No of Private IP Addresses**: The number of workloads that the tag discovery service has discovered. Each IP address represents a workload. If a workload has multiple IP addresses within it, it is shown as multiple workloads.
[See image.](#regiondetails)
Supported regions for AWS include:
| **Region Code** | **Region Name** |
| --------------- | --------------- |
| us-east-1 | N. Virginia |
| us-east-2 | Ohio |
| us-west-1 | N. California |
| us-west-2 | Oregon |
| eu-central-1 | Frankfurt |
| eu-west-1 | Ireland |
| eu-west-2 | London |
| ap-southeast-1 | Singapore |
| ap-south-1 | Mumbai |
| ap-southeast-2 | Sydney |
[]
- **Instance Role**: The role of the EC2 instance when it is launched.
- **AMI ID**: The ID of the Amazon Machine Image (AMI).
- **Platform**: The platform (i.e., **Linux/UNIX** or **Windows**) that the workload is operating on.
- **VM ID**: The ID of the virtual machine (VM) assigned to the workload.
- **Security Group ID**: The ID of the network security group assigned to the workload.
- **VPC ID**: The ID of the virtual private cloud (VPC) assigned to the workload. You can use this attribute in policies.
- **Subnet ID**: The ID of the subnet assigned to the workload.
- **Network Interface ID**: The ID of the network interface assigned to the workload.
-
**Security Group Name**: The name of the security group assigned to the workload.
[See image.](#attributedetails)
[]
- **Resource Type**: The type of resource is listed (i.e., VM, VPC, ENI, or Subnet).
- **Key**: The tag key string information for user-defined tags.
-
**Value**: The tag value string information for user-defined tags.
[See image.](#userdefinedtagdetails)
[]
![The AWS details accessed from the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-details/awsaccountdetails.png)
[]
![The Workloads table accessed from the Regions table in the Zscaler Cloud & Branch Connector Admin Portal. You can filter the table by VPC ID, Namespace, and IP Address. ](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-details/workloaddetails.png)
[]
![The Regions table accessed from the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-details/regiondetails.png)
[]
![The Attributes section accessed from the workloads table of the AWS Partner Integrations details page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-details/attributedetails.png)
[]
![The User-Defined Tags section accessed from the workloads table of the AWS Partner Integrations details page in the Zscaler Cloud & Branch Connector Admin Portal. It contains table with columns for Resource Type, Key, and Value, and sorting icon.](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/analyzing-amazon-web-services-account-details/userdefinedtagdetails.png)