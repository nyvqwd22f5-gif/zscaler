# Changing a Business Unit
Source: https://help.zscaler.com/dspm/changing-business-unit
PDF: https://help.zscaler.com/pdf/com/en/1474926.pdf

You can change the business units for each [organization unit](/dspm/onboarding-aws-organization) (OU), [management group](/dspm/onboarding-microsoft-azure-tenant), single account, or multiple accounts.
When a business unit is assigned to an OU or a management group, all the accounts within that OU or management group are assigned to the same business unit. For example, if an OU has 5 accounts and BU1 is assigned to the OU, all 5 accounts within that OU are assigned to BU1.
Changing business unit overrides the currently assigned business unit.
Prerequisite
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or any role with Business Unit Mapping permission.
Changing a Business Unit for an OU or Management Group
To change a business unit for an OU or management group:
- Go to **Administration** > **Configuration** >** Cloud Accounts**.
- Select the cloud account (AWS organization, Microsoft Entra tenant or GCP organization).
-
Click **Manage**, and then select **Business Units Mapping** from the drop-down menu.
[See image.](#bu-map-option)
-
On the **Business Units Mapping** page, assign a business unit to the OU. All the accounts in the OU are mapped to the selected business unit.
[See image.](#assign-bu)
-
Click **Done**.
A message appears indicating that the business unit was changed successfully.
Changing a Business Unit for Single or Multiple Accounts
To change a business unit for single or multiple accounts:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account:
- [AWS](#aws-single-multiple-bu-change)
- [Azure](#azure-single-multiple-subscription)
- [GCP](#gcp-single-multiple-project)
-
In the **Change Business Unit for Selected** window, select the business unit from the drop-down menu.
[See image.](#bu-change-window)
-
Click **Apply**.
A message appears indicating that the business unit was changed successfully.
-
[]Select the organization and then select the **Accounts** tab.
[See image.](#selectaccountstab)
- Choose any of the following options:
-
To change a business unit for a single account:
Click the **Actions** icon for the account you want to change the business unit, then select **Change Business Unit**.
[See image.](#singleaccount)
- To change a business unit for multiple accounts:
-
Select the checkboxes for the required accounts.
The **Actions** menu appears on the page.
[See image.](#actionsmenuaws)
-
From the **Actions** drop-down menu, select **Change Business Unit**.
[See image.](#bulkaccounts)
-
[]Select the tenant and then select the **Subscriptions** tab.
[See image.](#selectsubscriptions)
- Choose any of the following options:
-
To change a business unit for a single subscription:
Click the **Actions** icon for the subscription you want to change the business unit, then select **Change Business Unit**.
[See image.](#singlesubscription)
- To change a business unit for multiple subscriptions:
-
Select the checkboxes for the required subscriptions.
The **Actions** menu appears on the page.
[See image.](#actionsmenusub)
-
From the **Actions** drop-down menu, select **Change Business Unit**.
[See image.](#bulksub-bu)
-
[]Select the organization and then select the **Projects** tab.
[See image.](#selectprojectstab)
- Choose any of the following options:
-
To change a business unit for a single project:
Click the **Actions** icon for the project you want to change the business unit, then select **Change Business Unit**.
[See image.](#singleproject)
- To change a business unit for multiple projects:
-
Select the checkboxes for the required projects.
The **Actions** menu appears on the page.
[See image.](#actionsmenupro)
-
From the **Actions** drop-down menu, select **Change Business Unit**.
[See image.](#bulkprojects-bu)
[]![Business units mapping](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-manage-bu-mapping.png)
[]![Assign business units for OU](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-select-bu.png)
[]![Change Business Unit window](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-singleaccount-buchange-window.png)
[]![Select the Projects tab](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-select-or-projects.png)
[]![Select the Accounts tab](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-select-accounts-tab.png)
[]![Select the Subscriptions tab](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-selecttenant-subscriptions.png)
[]![Change business unit for a single project](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-change-bu-singleproject.png)
[]![Change business unit for a single account](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-single-account-buchange_0.png)
[]![Change business unit for a single subscription](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-azure-singlebuchange.png)
[]![Change business unit for bulk accounts](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-bulkaccounts-changebu.png)
[]![Actions menu](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-actions-menu.png)
[]![dspm-actions-menu.png](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-actions-menu.png)
[]![dspm-actions-menu.png](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-actions-menu.png)
[]![Change Business Unit for multiple subscriptions](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-bulk-sub-change-bu.png)
[]![Change Business Unit for multiple projects](/downloads/dspm/administration/cloud-account-management/changing-business-unit/dspm-bulk-projects-buchange.png)