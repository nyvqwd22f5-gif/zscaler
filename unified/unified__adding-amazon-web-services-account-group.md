# Adding an Amazon Web Services Account Group
Source: https://help.zscaler.com/unified/adding-amazon-web-services-account-group
PDF: https://help.zscaler.com/pdf/com/en/1518646.pdf

This article provides information on how to add an Amazon Web Services (AWS) account group in the Admin Portal. To learn more, see [About Amazon Web Services Account Groups](/unified/about-amazon-web-services-account-groups).
Adding an AWS Account Group
To add an AWS account group:
- Go to **Infrastructure **> **Connectors **> **Cloud **> **Partner Integrations** > **AWS **> **Groups**.
-
Click **Add Group**.
[See image.](#AddAWSGroupButton)
The **Add AWS Group** window appears.
- In the **Add AWS Group** window:
- **Name**: Enter a name for the AWS account group.
- **Description**: Enter a description for the AWS account group.
- **Cloud Connector Group**: From the drop-down menu, select the Cloud Connector group(s) to associate with the account group.
-
From the table, select the AWS accounts to associate with the group. AWS accounts are sorted by the following criteria:
- **Account ID**: The ID of the AWS account where workloads are deployed.
- **Name**: The name of the AWS account.
- **Last Modified By**: The last admin to modify the account.
- **Last Modified On**: The date and time the account was last modified.
- **Permission**: The permission status of the account (i.e., **Pending**, **Allowed**, or **Denied**).
- **Latest Sync**: The last time the account synced. After refreshing, this column displays the time when the user clicked the Refresh button.
[See image.](#AddAWSGroup)
- Confirm the information entered is correct and click **Save**.
[]![The Add AWS Group window accessed from the Partner Integrations Groups page.](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/about-amazon-web-services-account-groups/AddAWSGroup.png)
[]![The Add Group button on the Partner Integrations Groups page of the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-amazon-web-services-account-group/Add%20AWS%20Group.png)