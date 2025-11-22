# About Microsoft Information Protection Labels
Source: https://help.zscaler.com/unified/about-microsoft-information-protection-labels
PDF: https://help.zscaler.com/pdf/com/en/1492971.pdf

Microsoft Information Protection (MIP) provides sensitivity labels, which you can use to identify and protect files with sensitive content. These MIP labels are maintained by Microsoft and, through the addition of a MIP Account in the Admin Portal, these labels can be retrieved from Microsoft so that they can be used when defining a Data Loss Prevention (DLP) policy in the Admin Portal.
MIP labels provide the following benefits and enable you to:
- Prevent exfiltration of files tagged with MIP labels through inline web DLP policies. With the inline web DLP policy, the service can detect files tagged with these sensitivity labels when evaluating transactions.
- Auto-classify sensitive files using Zscaler SaaS Security API policies.
About the Microsoft Information Protection (MIP) Labels Page
On the Microsoft Information Protection (MIP) Labels page (Policies > Data Protection > Common Resources > MIP Labels), you can:
- [Add a MIP Account](/unified/adding-mip-account).
- View a list of all MIP accounts that were added for your organization. For MIP accounts, you can view the following:
- **Account Name**: The name of the account associated with the Microsoft account.
- **Labels**: The number of labels associated with the account. **No. of Labels **appears in this field for the account until you expand the **Account Name**.
- **Status**: The status of the account, including the last time the account information was last retrieved from Microsoft. The following states appear:
- **Active**: The account is active. MIP labels are retrieved from the Microsoft Portal.
- **Retrieval Pending:** The fetching of the MIP labels from the Microsoft Portal is in progress for the MIP account. Validation has been successful and the status of the MIP account is active.
- **Tenant Inactive**: The account is inactive. MIP labels are not retrieved from the Microsoft Portal.
- **Validation Failed**: The account failed to validate with the Microsoft Portal.
- **Validation Success**: The account is validated with the Microsoft Portal.
- **Validation Failed**: The account failed to validate with the Microsoft Portal.
To view the current state, you need to explicitly refresh the page. To refresh the page, complete one of the following steps:
- Click the **Reload this page** icon.
- Click the **Edit** icon for a MIP account.
- Navigate away from this page and then return to the page.
- Expand an **Account Name** to view the MIP labels associated with the account.
- Edit a MIP account.
- Download the list of labels associated with the MIP account to a comma-separated value Microsoft Excel spreadsheet.
- Delete a MIP account
- Search for a MIP account.
![MIP Labels page in the Admin Portal](/downloads/unified/policies/internet-saas/data-protection/data-loss-prevention/labels-and-tags/about-microsoft-information-protection-labels/Labels-and-Tags-Page-MIP-Page.png)