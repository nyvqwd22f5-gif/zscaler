# Adding an Amazon Web Services Account
Source: https://help.zscaler.com/cloud-branch-connector/adding-amazon-web-services-account
PDF: https://help.zscaler.com/pdf/com/en/1464091.pdf

This article provides information on how to onboard an Amazon Web Services (AWS) account to enable tag discovery services within the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [About Amazon Web Services Accounts](/cloud-branch-connector/about-partner-integrations).
To enable this feature, contact Zscaler Support.
Adding an AWS Account
To add an AWS account:
- Go to **Administration **> **Partner Integrations** > **AWS** > **Accounts**.
-
Click **Add AWS Account**.
[See image.](#AddAWSAccount)
The **Add AWS Account **window appears.
- In the **Add AWS Account** window:
-
In the **Configuration** section:
- **Name**: Enter a name for your AWS account.
- **AWS Account ID**: Enter the ID of the account where workloads are deployed.
- **AWS Role Name**: Enter the name of the AWS trusting role in your account.
- **Account Group**: (Optional) Select an AWS account group to add the account to.
- **External ID**: Enter a unique external ID for each account. This is the external ID in the trust relationship of the IAM role that calls AWS while fetching the tag information. You must add the unique external ID to the AWS IAM role configuration. If this ID is regenerated, update it in your AWS account.
- **Event Bus Name**: The name of the event bus in the Zscaler account. This event bus is the target of events in your account.
- **Trusted Account ID**: The ID of the Zscaler AWS account.
- **Trusted Role**: The name of the trusted role in the Zscaler AWS account.
[See image.](#AddAWSAccountConfiguration)
-
In the **Region** section, select one or more regions where your workloads are deployed.
If you do not select one or more regions where you have workloads deployed, the Zscaler discovery service does not discover the workloads, and tag-based security policies are not applied to the workloads.
[See image.](#AddAWSAccountRegion)
-
In the **Review** section, confirm that the information is correct and click **Save and Next**.
[See image.](#AddAWSAccountReview)
-
After entering the necessary information into the Cloud & Branch Connector Admin Portal, you must provide the Zscaler service with permissions to fetch metadata from your AWS account. To grant these permissions, in the **CloudFormation** section, launch or download the CloudFormation template:
- **Launch Cloudformation template in AWS console**: After launching the CloudFormation template, you are prompted to log in to your AWS account. The CloudFormation template is displayed in your AWS account with custom values based on the information you entered in the Cloud & Branch Connector Admin Portal. To proceed, you must confirm the information and execute the template.
- **Download CloudFormation Template for Later Execution**: If the Zscaler admin user does not have permission to execute the CloudFormation template in their AWS account, download the CloudFormation template to deploy at a later date.
[See image.](#AddAWSAccountCloudFormation)
![Adding an AWS Account on the Partner Integrations page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/AddAWSAccount-GCP.png)
[]
![The Configuration section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/AWSaccgroupconfigtab.png)
[]
![The Region section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/AddAWSAccountRegion.png)
[]
![The Review section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/awsaccreviewtab.png)
[]
![The CloudFormation section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/AddAWSAccountCloudFormation.png)
[]
After the CloudFormation template is executed, your account is onboarded into the Cloud & Branch Connector Admin Portal.