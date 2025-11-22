# Managing Data Events
Source: https://help.zscaler.com/dspm/managing-data-events
PDF: https://help.zscaler.com/pdf/com/en/1530669.pdf

Data events provide information on the activities performed on or within AWS data stores, such as reading or writing to an S3 bucket, GetObject API operations, etc. DSPM supports ingestion of data events to analyze the activity logs.
Managing Data Events Configuration for an Organization
To manage data events configuration for an organization:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the onboarded account.
-
Click **Manage**, and then select **Manage Data Events**.
[See image.](#manage-dataevents)
-
On the **Configure Data Events** page, click the toggle to enable or disable data events.
- [Enable](#enabledataevents)
- [Disable](#disabledataevents)
When disabled, DSPM stops collecting data events from the S3 bucket.
[See image.](#configuredataevents-disabled)
Managing Data Events Configuration for Single or Multiple Accounts
To manage data events configuration for single or multiple accounts:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
-
Select the AWS account and then select the **Accounts** tab.
[See image.](#accounts-tab)
- Choose one of the following options:
-
To manage data events for a single account:
Click the **Actions** icon for the account you want to update data events on, then select **Manage Data Events**.
[See image.](#single-dataevents)
- To manage data events for multiple accounts:
- Select the checkboxes for the required accounts.
-
From the **Actions **drop-down menu, select **Manage Data Events.**
[See image.](#bulk-select-managedataevents)
-
In the **Configure Data Events** window, click the toggle to enable or disable data events.
- [Enable](#singleaccount-enable)
- [Disable](#singleaccount-disable)
[See image.](#configuredataeventstoggle)
-
[]Provide the following details:
- **CloudTrail Type**: Select the **OrgCloudTrail **checkbox, if it is an organization CloudTrail.
- **CloudTrail Bucket Name**: Enter the S3 bucket name where the CloudTrail events are logged.
- **Prefix **(Optional): Enter the prefix specified in the CloudTrail bucket path, if any.
- **Bucket Account ID**: Enter the AWS account ID where the CloudTrail S3 bucket is present.
[See image.](#configuredata-events-enabled)
-
On the **Apply Changes** page:
- Select the template type (**CloudFormation **or **Terraform**).
- Download the **Data Events** template and run it on the account where the specified CloudTrail S3 bucket is present.
[See image.](#applychangespage)
- []Click **Next**.
- On the **Apply Changes** page, click **Done**.
-
[]Provide the following details:
- **CloudTrail Type**: Select the **OrgCloudTrail **checkbox, if it is an organization CloudTrail.
- **CloudTrail Bucket Name**: Enter the S3 bucket name where the CloudTrail events are logged.
- **Prefix **(Optional): Enter the prefix specified in the CloudTrail bucket path, if any.
- **Bucket Account ID**: Enter the AWS account ID where the CloudTrail S3 bucket is present.
[See image.](#configuredataevents)
- On the **Apply Changes** page:
- Select the template type (**CloudFormation **or **Terraform**).
- Download the **Data Events** template and run it on the account where the specified CloudTrail S3 bucket is present.
- []Click **Next**.
- On the **Apply Changes** page, click **Done**.
[]![The Manage action drop-down menu listing the available actions for the selected cloud account and annotation around Manage Data Events.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-manage-data-events.jpg)
[]![The Configure Data Events page with toggle to enable or disable data events storage option.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-configure-data-events.jpg)
[]![The Configure Data Events page with the CloudTrail details provided.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-configure-data-events-enabled.jpg)
[]![The Apply Changes page displaying the Data Events template that must be run on the AWS account.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-apply-changes-page.jpg)
[]![The Actions drop-down menu listing the actions available for the selected accounts.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-data-events/dspm-bulk-dataevents.png)
[]![The Accounts tab displaying the onboarded accounts.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-data-events/dspm-select-accounts-tab.png)
[]![The Actions drop-down menu listing the actions available for the selected account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-data-events/dspm-singleaccount-dataevents.png)
[]![The Configure Data Events page with annotation around the toggle button.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-data-events/dspm-enable-dataevents.png)
[]![The Configure Data Events page with the CloudTrail details blurred.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/managing-data-events/dspm-configure-data-events-page.png)