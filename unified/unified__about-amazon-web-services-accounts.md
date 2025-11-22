# About Amazon Web Services Accounts
Source: https://help.zscaler.com/unified/about-amazon-web-services-accounts
PDF: https://help.zscaler.com/pdf/com/en/1518626.pdf

Partner integrations enable you to add Amazon Web Services (AWS) accounts by allowing the Zscaler service to fetch metadata from the accounts. Adding an AWS account allows you to use user-defined tags in Zscaler security policies.
To enable this feature, contact Zscaler Support.
Partner integrations provide the following benefits and enable you to:
- Configure permissions for Zscaler to discover workloads and associated metadata from an AWS account.
- View discovered workloads and the associated metadata.
- Configure regions where Zscaler can discover workloads.
About the Partner Integrations Page
On the Partner Integrations page (**Infrastructure**> **Connectors **> **Cloud **> **Partner Integrations**), you can do the following:
- [Add an AWS account](/cloud-branch-connector/adding-amazon-web-services-account).
- View a list of all accounts. For each account, you can view:
- **Account ID**: The ID of the AWS account.
- **Name**: The name of the account.
- **Last Modified By**: The last admin to modify the account.
- **Last Modified On**: The date and time the account was last modified.
-
**Permission**: The permission status of the account (i.e., **Pending**, **Allowed**, or **Denied**).
After an account is onboarded, set the role in AWS and refresh the account in the Zscaler Admin Portal. The status updates from **Pending** to either **Allowed** or **Denied**.
- **Latest Sync**: The last time the account synced. After refreshing, this column displays the time when the user clicked the Refresh button.
- [Edit](/cloud-branch-connector/editing-deleting-or-duplicating-items) an account.
- Refresh an account.
- Configure additional settings for an account. For each account, you can configure:
- **Launch Cloudformation**: This allows you to launch CloudFormation in AWS.
- **Disable Data Collection**: Zscaler stops the tag discovery process.
- **Enable Data Collection**: Zscaler begins the tag discovery process.
- **Delete Accounts**: The account is permanently deleted.
- Modify the table and its columns.
- Search for an account.
- Download the CloudFormation template.
- Go to the [AWS Account Groups](/cloud-branch-connector/about-amazon-web-services-account-groups) page.