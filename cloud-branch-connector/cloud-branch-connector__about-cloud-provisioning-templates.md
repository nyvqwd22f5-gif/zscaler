# About Cloud Provisioning Templates
Source: https://help.zscaler.com/cloud-branch-connector/about-cloud-provisioning-templates
PDF: https://help.zscaler.com/pdf/com/en/1420426.pdf

[Watch a video about Cloud Provisioning Templates.](https://fast.wistia.net/embed/iframe/577qniv2zj)
The cloud provisioning URL is a prerequisite for deploying the Cloud Connector as a virtual machine (VM) in Amazon Web Services (AWS), Microsoft Azure, and Google Cloud Platform (GCP). To obtain a provisioning URL, you must configure the provisioning template.
Cloud Connector Provisioning Templates provide the following benefits and enable you to:
- Set up required preconfigurations for deployment.
- Use the same provisioning URL multiple times based on your requirements.
You must use the same provisioning URL for the Cloud Connector VMs deployed in a single Virtual Private Cloud (VPC).
About the Cloud Provisioning Template Page
On the Cloud Provisioning Templates page (Administration > Provisioning Templates > Cloud Provisioning), you can do the following:
- [Add a Cloud Connector Provisioning Template](/cloud-branch-connector/configuring-provisioning-templates).
- View a list of all cloud provisioning templates that are configured for your organization.
- **Template Name**: The name of the template.
- **Cloud Provider Type**: The Cloud Provider (AWS, Azure, or GCP).
- **Status**: The status of the template deployment.
- **VM Size**: The size of the virtual machine.
-
**Auto Scaling**: The status of auto scaling (i.e., **True** or **False**). Zscaler supports Auto Scaling in AWS and Azure, but does not support Auto Scaling for GCP.
In the AWS Marketplace, Auto Scaling is referred to as Auto Scaling. In the Azure Marketplace, Auto Scaling is referred to as Virtual Machine Scale Sets (VMSS). In the Zscaler Cloud & Branch Connector Admin Portal, references to Auto Scaling also refer to VMSS. To enable Auto Scaling or VMSS, contact Zscaler Support.
- **Last Modified By**: The last admin to modify the template.
- **Last Modified On**: The date and time the template was last modified.
- Click the arrow in the **Template Name **field to copy the cloud provisioning URL.
- [Edit ](/cloud-branch-connector/editing-deleting-or-duplicating-items#edit)the cloud provisioning template.
- [Delete](/cloud-branch-connector/editing-deleting-or-duplicating-items#delete) the cloud provisioning template.
- View the cloud provisioning template configurations.
- Modify the table and its columns.
- Search for a cloud provisioning template.
- Refresh the cloud provisioning template list.
- View the [Branch Provisioning Template](/cloud-branch-connector/about-branch-provisioning-template) page.
![Cloud Connector Provisioning Template Page](/downloads/cloud-branch-connector/administration/provisioning-configuration/about-cloud-provisioning-templates/About%20Cloud%20Connector%20Provisioning%20Templates1.png)