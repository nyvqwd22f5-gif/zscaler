# About Business Units
Source: https://help.zscaler.com/dspm/about-business-units
PDF: https://help.zscaler.com/pdf/com/en/1474931.pdf

Business units are logical containers for cloud accounts in the DSPM Admin Portal. Business units govern DSPM from a role-based access control (RBAC) perspective. Organizations can control and manage user access to data in their cloud accounts. This controlled access helps alleviate security risks and thereby maintain the security posture of your cloud resources.
You must assign users or user groups to the business units in the ZIdentity Admin Portal. To learn more, see [About Users](/zidentity/about-users).
You can onboard your [cloud accounts](/dspm/about-cloud-accounts) and map them to business units. You can also restrict user access to specific business units. For example, you might want to restrict a specific team to view the alerts only for Google Cloud Platform (GCP) Cloud Storage buckets, Amazon Web Services (AWS) accounts, or restrict partners to view resources only for a certain set of Microsoft Azure subscriptions.
The Business Unit Management page provides the following benefits and enables you to:
- Manage cloud accounts within the business unit.
- Control what data can be viewed and what tasks can be performed by users on specific sets of cloud accounts.
About the Business Unit Management Page
On the Business Unit Management page (Administration > Configuration > Business Unit Management), you can do the following:
- View the list of business units. For each business unit, you can see:
-
**Business Unit Name**: The name of the business unit. Click to view the cloud accounts that are assigned to this business unit. Click **Manage **to add or delete a cloud account from the [Cloud Accounts](/dspm/about-cloud-accounts) page.
[See image.](#groupscloudaccounts)
- **Account Count**: The number of [cloud accounts](/dspm/about-cloud-accounts) assigned to the business unit.
- **Created On**: The date and time the business unit was created.
-
Add a business unit.
- Click **Add Business Unit**.
- In the **Add Business Unit** window, enter a unique name for the business unit.
- Click **Create**.
[See image.](#addbu)
- Search for specific data in the searchable columns.
- Sort the column data.
- [Modify the table and its columns](/dspm/using-tables).
-
Click the **Actions **icon to edit or delete a business unit.
You cannot edit or delete the default business unit.
![The Business Unit Management page displaying the list of default and custom business units.](/downloads/dspm/administration/business-units/about-business-units/dspm-bu-page.png)
[]![The business unit details page listing the cloud accounts that are assigned.](/downloads/dspm/administration/business-units/about-business-units/dspm-businessunit-window.png)
[]![The Add Business Unit window with the name field and Create button.](/downloads/dspm/administration/business-units/about-business-units/dspm-add-bu.png)