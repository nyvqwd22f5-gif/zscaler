# Adding an Amazon Web Services Account
Source: https://help.zscaler.com/unified/adding-amazon-web-services-account
PDF: https://help.zscaler.com/pdf/com/en/1520696.pdf

This article provides information on how to onboard an Amazon Web Services (AWS) account to enable tag discovery services within the App Portal. To learn more, see [About Amazon Web Services Accounts](/unified/about-amazon-web-services-accounts).
To enable this feature, contact Zscaler Support.
Adding an AWS Account
To add an AWS account:
- Go to **Infrastructure **> **Partner Integrations** > **AWS**> **Accounts**.
-
Click **Add AWS Account**.
[See image.](#AddAWSAccount)
The **Add AWS Account **window appears.
- In the **Add AWS Account** window:
- On the **Configuration** tab:
- **Name**: Enter a name for your AWS account.
- **AWS Account ID**: Enter the account ID where workloads are deployed.
- **AWS Role Name**: Enter the name of the AWS trusting role in your account.
- **Account Group**: (Optional) Select an AWS account group to add the account to.
- **External ID**: Enter a unique external ID for each account. This is the external ID in the trust relationship of the IAM role that calls AWS while fetching the tag information. You must add the unique external ID to the AWS IAM role configuration. If this ID is regenerated, update it in your AWS account.
- **Event Bus Name**: The name of the event bus in the Zscaler account. This event bus is the target of events in your account.
- **Trusted Account ID**: The ID of the Zscaler AWS account.
-
**Trusted Role**: The name of the trusted role in the Zscaler AWS account.
[See image.](#AddAWSAccountConfiguration)
-
On the **Region** tab, select one or more regions where your workloads are deployed.
If you do not select one or more regions where you have workloads deployed, the Zscaler discovery service does not discover the workloads, and tag-based security policies are not applied to the workloads.
[See image.](#AddAWSAccountRegion)
-
On the **Review** tab, confirm that the information entered is correct and click **Save and Next**.
[See image.](#AddAWSAccountReview)
-
After entering the necessary information into the Admin Portal, you must provide Zscaler with permissions to fetch metadata from your AWS account. To grant these permissions, on the **CloudFormation** tab, launch or download the CloudFormation template, then click **Finish**:
- **Launch Cloudformation template in AWS console**: After launching the CloudFormation template, you are prompted to log in to your AWS account. The CloudFormation template is displayed in your AWS account with custom values based on the information entered in the Cloud & Branch Connector Admin Portal. To proceed, you must confirm the information and execute the template.
- **Download CloudFormation Template for Later Execution**: If the Zscaler admin user does not have permission to execute the CloudFormation template in their AWS account, download the CloudFormation template to deploy at a later date.
[See image.](#AddAWSAccountCloudFormation)
![Adding an AWS Account on the Partner Integrations page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account/Add%20AWS%20Account.png)
[]
![The Configuration section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account/AddAWSAccountConfiguration.png)
[]
![The Region section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account/AddAWSAccountRegion.png)
[]
![The Review section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account/Adding%20an%20AWS%20Account%20review.png)
[]
![The CloudFormation section of the Add AWS Account page](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account/AddAWSAccountCloudFormation.png)
[]
After the CloudFormation template is executed, your account is onboarded into the Admin Portal.