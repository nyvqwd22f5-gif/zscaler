# About Administrators
Source: https://help.zscaler.com/zpc/about-administrators
PDF: https://help.zscaler.com/pdf/com/en/1392916.pdf

Role-based access control (RBAC) is an access management system that is essential for every organization to enforce the principle of least privilege and restrict user access to specific features and tasks depending on user roles and permissions.
ZPC enables you to create administrator accounts, add administrators to multiple groups with specific roles, and granularly control their level of access to various modules in the ZPC Admin Portal.
Configuring administrator accounts has the following benefits and enables you to:
- Create and manage groups, roles, and business units.
- Configure additional administrator accounts and add them to multiple groups.
- Control and manage user access to various modules in ZPC.
To facilitate role-based administration, the following entities are applicable:
- [Role](#a-role)
- [Group](#a-group)
- [Business Unit (Scope)](#a-bu)
About the Administrators and Groups Page
ZPC administrators can manage user accounts from the Administrators and Groups Page (Administration > Administrators and Groups) and do the following:
- View the list of administrators. For each administrator, you can see:
- **Administrator Name**: The name of the administrator. Click to view the administrator details along with the modules and global modules that are assigned. To learn more, see [ZPC Modules and Global Modules](/zpc/zpc-modules-and-global-modules).
[See image.](#admindetails)
If the administrator belongs to a group that is not associated with any business unit, the following message is displayed next to the administrator's name. [See image.](#invalid) This indicates that the group is invalid.
- **Email ID**: The administrator's email address.
- **Groups**: The groups assigned to the administrator. Click to view the list of administrators in each group.
[See image.](#adminlist)
- **Last Login**: The date and time when the administrator last logged in to the ZPC Admin Portal.
- [Add an administrator](/zpc/adding-administrators).
- [View the Group details](/zpc/adding-group).
- Sort the column data.
- [Edit an administrator account.](/zpc/editing-deleting-administrator-accounts)
- [Delete an administrator account.](/zpc/editing-deleting-administrator-accounts)
- [Modify the table and its columns](/zpc/using-tables).
- Search for specific data in the searchable columns (Administrator Name, Email ID, or Group).
- Export the data to a CSV file.
![View the Administrators and Groups page](/downloads/zpc/authentication-authorization/administrators-and-groups/about-administrators/zpc-admin-page.png)
[![View the admins in the group](/downloads/zpc/authentication-authorization/administrators-and-groups/about-administrators/zpc-admin-list.png)
]![Click and drag to move](data:image/gif;base64,R0lGODlhAQABAPABAP///wAAACH5BAEKAAAALAAAAAABAAEAAAICRAEAOw==)
​
[![View the admin details](/downloads/zpc/authentication-authorization/administrators-and-groups/about-administrators/zpc-admin-details.png)
]
[]Roles determine the level of access users have to the ZPC Admin Portal and tasks that they can perform. ZPC provides a default admin role that has full access to the ZPC Admin Portal, and this role is assigned to the default admin, but you can assign this role to other admins as necessary. You can assign users with predefined roles or [custom roles](/zpc/adding-custom-role).
[Predefined Roles in ZPC](#predefinedrolelist)
To view the permissions associated with each role, see [Predefined Roles and Permissions](/zpc/predefined-roles-and-permissions).
- []Administrator
- SecOps
- Compliance Auditor
- View Only Administrator
- IaC Administrator
- IaC Developer
- IT Administrator
- Vulnerability Administrator
- Vulnerability Viewer
- Kubernetes Onboarding
- LocalPlatformAgent
[]A logical entity that includes a group of users.
- Each group is assigned a single role.
- A group can be assigned to multiple business units.
- Users can be assigned to multiple groups, so they can perform various tasks based on the group's role and permissions.
- Users can [switch between groups](/zpc/about-groups#switchgroups) in the ZPC Admin Portal.
To learn more, see [About Groups](/zpc/about-groups).
[]A logical container for cloud accounts in the ZPC Admin Portal. Business units allow grouping of accounts. Groups of users (with their assigned roles) are assigned to different business units, allowing organizations to control what data can be viewed and what tasks can be performed by users on specific sets of cloud accounts. For example, if a group is assigned a compliance role, and this group is assigned to a business unit, then users in the group have all the compliance permissions to view data on cloud accounts in that business unit. To learn more, see [About Business Units](/zpc/about-business-units).
[![Invalid scope](/downloads/zpc/authentication-authorization/administrators-and-groups/about-administrators/zpc-scope-invalid.png)
]