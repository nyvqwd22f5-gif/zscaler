# Deleting an Onboarded Account
Source: https://help.zscaler.com/dspm/deleting-onboarded-account
PDF: https://help.zscaler.com/pdf/com/en/1478036.pdf

You can choose to delete or offboard AWS, Microsoft Entra, and Google Cloud Platform (GCP) accounts when the resources are removed from the accounts or when you no longer want DSPM to scan the resources in these accounts.
When you delete an account:
- All the resources within the account are deleted.
- The delete action cannot be reverted. You must onboard the cloud account again if it must be scanned.
- Deleting the account does not delete resources created while [deploying templates](/dspm/about-cloud-accounts). You must manually delete these resources. To delete the resources, run the `terraform destroy` command.
Deleting or offboarding cloud accounts impacts the following modules:
[](/dspm/about-cloud-accounts)[](/zpc/about-alerts)[](/dspm/about-alert-notifications)[](/dspm/about-ignore-alert-filters)[](/dspm/about-scan-settings)[](/dspm/creating-custom-policies)
| Modules | Impact |
| ------- | ------ |
| Cloud Accounts | The account is removed from the Accounts tab. |
| Alerts | All alerts generated for the deleted account are closed. You cannot filter the alerts for the deleted account. |
| Alert Notifications, Ignore Alert Filter | If the deleted account was the only account defined for the filter scope, then the alert rule or ignore alert filter is disabled with an exclamation mark indicating that it is invalid. |
| Scan Settings | If the deleted account was the only account selected for scanning, then the scan configuration is disabled. |
| Policies | The deleted account is not shown while creating custom policies. Any existing custom policy created for the deleted account is marked as invalid. |
Prerequisites
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Delete Account permissions.
Deleting an Organization or Tenant
To delete an organization or tenant:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
-
Select the cloud account you want to delete.
[See image.](#select_org_tenant)
-
From the **Manage** drop-down menu, select **Delete Organization** or **Delete Tenant** depending on the cloud type.
[See image.](#i-manage-delete)
-
Read the message in the confirmation window, type `DELETE`, and then click **DELETE**.
[See image.](#i-delete-org)
The organization or tenant and all associated accounts are deleted from the DSPM Admin Portal.
Deleting Single or Multiple Accounts
When you delete either a single account or multiple accounts, it is only deleted from the DSPM Admin Portal and there is no impact on these accounts on the cloud service provider.
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account.
-
In the parent cloud account, select **Accounts** for AWS, **Subscriptions** for Microsoft Entra, and **Projects** for GCP.
[See image.](#i-project_sub_account)
- Choose any of these options:
- [For a single account, subscription, or project](#single)
- [For multiple accounts, subscriptions, or projects](#multiple)
-
Read the message in the confirmation window, type `DELETE`, and then click **DELETE**.
[See image.](#i-delete-projects)
The account is deleted from the DSPM Admin Portal.
- []Click the **Actions** icon for the account, subscription, or project you want to delete.
-
Select **Delete Account**, **Delete Subscription**, or **Delete Project**.
[See image.](#i-singleaction_delete)
- []Select the checkboxes for the required accounts, subscriptions, or projects.
-
From the **Actions** drop-down menu that appears, select **Delete Accounts**, **Delete Subscriptions**, or **Delete Projects**.
[See image.](#i-multipleaction-delete)
[]![Delete confirmation window with a warning about deleting the projects and annotation around Delete button.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/deleteprjtsconf.png)
[]![In the Projects tab, for a project, the action icon clicked with an annotation around the  Delete Project option.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/bulkdelproj.png)
[]![In the Projects tab, for a project, the action icon clicked with an annotation around the Delete Project option.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/single_action-delete.png)
[]![Cloud Accounts page with an account selected, and the Project tab displays the projects for the account.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/select_projects.png)
[]![Cloud accounts page, showing the onboarded accounts with an annotation around a cloud account to select.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/select_organization_tenant.png)
[]![Manage action button is clicked to see the available options and an annotation around the Delete option.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/i_manage-delete.png)
[]![Delete confirmation window with a warning about deleting the tenant and annotation around Delete button.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/deleting-onboarded-account/i-delete-org.png)