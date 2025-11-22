# About Business Units
Source: https://help.zscaler.com/zpc/about-business-units
PDF: https://help.zscaler.com/pdf/com/en/1403176.pdf

Business units are logical containers for cloud accounts in the ZPC Admin Portal. Business units govern ZPC from a role-based access control (RBAC) perspective. Organizations can control and manage user access to data in their cloud accounts. This controlled access helps alleviate security risks and thereby maintain the security posture of your cloud resources.
You can onboard your [cloud accounts](/zpc/about-cloud-accounts) and map them to business units. You can restrict user access to specific business units. For example, you may want to restrict the developer team to view the alerts only for Amazon Web Services (AWS) accounts or restrict partners to view cloud assets only for a certain set of Google Cloud Platform (GCP) accounts. To manage cloud accounts within business units, see [Managing Cloud Accounts](/zpc/managing-cloud-accounts).
Business units are mapped to [groups](/zpc/about-groups) that are assigned with specific [roles and permissions](/zpc/about-roles).
Configuring business units has the following benefits and enable you to:
- Manage cloud accounts within the business unit.
- Assign multiple business units to groups.
- Control what data can be viewed and what tasks can be performed by users on specific sets of cloud accounts.
About the Business Unit Management Page
On the Business Unit Management page (Administration > Business Unit Management), you can:
- View the list of business units. For each business unit, you can see:
- **Business Unit Name**: The name of the business unit. Click to view the groups and cloud accounts that are assigned to this business unit.
[See image.](#bu-drawer)
By default, the "Default Super Admin" and "Default Read Only" groups are assigned to all business units. [See image.](#predefinedgroups)
- **Groups**: The names of groups assigned to the business unit. To learn more, see [About Groups](/zpc/about-groups).
- **Account Count**: The number of cloud accounts in the business unit.
- **Created On**: The date and time when the business unit was created.
- [Add a Business Unit](/zpc/adding-business-unit).
- Search for specific data. Click the Information icon (![Information icon](/downloads/zpc/administration/business-units/about-business-units/zpc-info-icon.png)
) to see the columns that can be searched. [See image.](#searchable)
- Sort the column data.
- [Edit a business unit](/zpc/editing-deleting-business-unit).
- [Delete a business unit](/zpc/editing-deleting-business-unit).
- [Modify the table and its columns](/zpc/using-tables).
![View the Business Unit Management page](/downloads/zpc/administration/business-unit-management/about-business-units/zpc-bu-page.png)
[![Searchable columns](/downloads/zpc/administration/business-unit-management/about-business-units/zpc-bu-searchcolumns.png)
]
[![View the groups and cloud accounts assigned to the business unit](/downloads/zpc/administration/business-unit-management/about-business-units/zpc-bu-drawer.png)
]
[![Predefined groups assigned to business unit](/downloads/zpc/administration/business-unit-management/about-business-units/zpc-bu-predefinedgroups.png)
]