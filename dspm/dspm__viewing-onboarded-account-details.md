# Viewing the Onboarded Account Details
Source: https://help.zscaler.com/dspm/viewing-onboarded-account-details
PDF: https://help.zscaler.com/pdf/com/en/1520536.pdf

After onboarding the accounts successfully, you can view the details of all the onboarded accounts on the Cloud Accounts page.
To view the onboarded account details:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
-
Click the required cloud account (AWS, Azure, or GCP).
[See image.](#img-select-account)
-
Select the **Accounts** tab for AWS, **Subscriptions** tab for Azure, and **Projects** tab for GCP.
[See image.](#img-select-subscription)
The tab name varies depending on the selected cloud account.
In this article, the **Subscriptions** tab is shown as an example. On the **Subscriptions** tab, you can do the following:
-
Select different actions from the **Manage** drop-down menu. To learn more, see [About Cloud Accounts](/dspm/about-cloud-accounts).
[See image.](#manage)
- [Add filters to view specific accounts.](/dspm/using-filters)
- Search for a specific account in the searchable columns.
- For each subscription, you can see:
- **Subscription Name:** The name of the subscription. Click the name to view additional details:
- [Details](#details-tab)
- [Issues](#issues-tab)
- **Subscription ID: **The unique identifier of the subscription.
- **Business Unit:** The business unit assigned to the account.
- **Status:** The status of the scan configuration (Successfully Configured, Pending Configuration, Needs Attention).
- **Last Validated**: The date and time when the account is validated to check all configurations.
- [Modify the table and its columns](/dspm/using-tables).
- Click the **Action** icon to [change the business unit](/dspm/changing-business-unit) or [delete](/dspm/deleting-onboarded-account) a subscription.
- Select multiple accounts and perform the same action on all of them at the same time, like [changing the business unit](/dspm/changing-business-unit) or [deleting the onboarded accounts](/dspm/deleting-onboarded-account).
[]
- **Status:** The [status of the scan configuration](/dspm/viewing-orchestrator-status) (Successfully Configured, Pending Configuration, Needs Attention) for the account.
- **Business Unit:** The [business unit](/dspm/changing-business-unit) assigned with the account.
- **Onboarding Date:** The date and time the account was onboarded
-
**CloudTrail**:
Cloud Trail details are displayed only for AWS accounts.
- **Bucket Name**: The name of the S3 bucket associated with CloudTrail.
- **Prefix**: The prefix specified in the CloudTrail bucket path.
- **Bucket Account ID**: The AWS account ID where the CloudTrail S3 bucket is present.
[See image.](#details)
[]
- View the configuration issues that occurred while onboarding the account along with the resolution steps. To learn more, see [Viewing Onboarding Issues](/dspm/viewing-onboarding-issues).
-
From the **Actions** drop-down menu, you can [change the business unit](/dspm/changing-business-unit) or [delete an onboarded account](/dspm/deleting-onboarded-account).
[See image.](#issues)
[]![DSPM cloud account details page with the Issues tab selected, showing issues and resolution steps. Within the Issues tab, the Action menu is annotated, showing available options.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-onboarded-accounts-or-subscriptions/issues.png)
[]![Account details page opened in the Details tab, showing the details of the cloud account.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-onboarded-accounts-or-subscriptions/details.png)
[]![Manage action menu, displaying available options.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-onboarded-accounts-or-subscriptions/manage.png)
[]![The Cloud Accounts page with the Subscriptions tab selected showing basic details about each subscription.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/viewing-onboarded-account-details/ds-account-details-n.png)
[]![The Cloud Accounts page, with an annotation around the Subscriptions tab, showing the basic details for each subscription. ](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-onboarded-accounts-or-subscriptions/ds-select-subscription.png)
[]![The list of onboarded cloud accounts with one account selected.](/downloads/tech-pubs-drafts/dspm-draft-articles/viewing-onboarded-accounts-or-subscriptions/ds-select-account.png)