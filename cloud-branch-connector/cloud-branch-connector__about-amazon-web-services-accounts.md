# About Amazon Web Services Accounts
Source: https://help.zscaler.com/cloud-branch-connector/about-amazon-web-services-accounts
PDF: https://help.zscaler.com/pdf/com/en/1463456.pdf

Amazon Web Services (AWS) partner integrations enable you to add AWS accounts by allowing the Zscaler service to fetch metadata from those accounts. An AWS account has credentials that provide access to a single AWS account. Adding an AWS account allows you to use user-defined tags in Zscaler security policies.
To enable this feature, contact Zscaler Support.
Partner integrations provide the following benefits and enable you to:
- Configure permissions for Zscaler to discover workloads and associated metadata from an AWS account.
- View discovered workloads and the associated metadata.
- Configure regions where Zscaler can discover workloads.
About the Accounts Page
On the Accounts page (Administration > Partner Integrations > AWS > Accounts), you can do the following:
- [Add an AWS account](/cloud-branch-connector/adding-amazon-web-services-account).
- Download the CloudFormation template.
- Search for an account.
- View a list of all accounts. For each account, you can view:
- **Account ID**: The ID of the AWS account. Select an account ID to view the dashboard details.
- **Name**: The name of the account.
- **Last Modified By**: The last admin to modify the account.
- **Last Modified On**: The date and time the account was last modified.
-
**Permission**: The permission status of the account (i.e., **Pending**, **Allowed**, or **Denied**).
After an account is onboarded, set the trusted role in AWS and refresh the account in the Zscaler Cloud & Branch Connector Admin Portal. The status updates from **Pending** to either **Allowed** or **Denied**.
- **Latest Sync**: The last time the account synced. After refreshing, this column displays the time when the user clicked the Refresh button.
- Modify the table and its columns.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items) an account.
- Refresh an account.
- Configure additional settings for an account. For each account, you can configure:
- **Launch Cloudformation**: This allows you to launch CloudFormation in AWS.
- **Disable Data Collection**: Zscaler stops the tag discovery process.
- **Enable Data Collection**: Zscaler begins the tag discovery process.
- **Delete Accounts**: The account is permanently deleted.
- Go to the [Microsoft Azure Accounts](/cloud-branch-connector/about-microsoft-azure-accounts) page.
- Go to the [Google Cloud Platform (GCP) Accounts](/cloud-branch-connector/about-google-cloud-platform-accounts) page.
- Go to the [AWS Account Groups](/cloud-branch-connector/about-amazon-web-services-account-groups) page.
![The AWS Accounts Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-accounts/AboutAWSAccounts-GCP02.png)