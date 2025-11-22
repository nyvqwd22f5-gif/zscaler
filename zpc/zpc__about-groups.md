# About Groups
Source: https://help.zscaler.com/zpc/about-groups
PDF: https://help.zscaler.com/pdf/com/en/1455961.pdf

A group is a logical entity that includes several users. Each group is assigned a single role and all users in the group are assigned the same role. Users can be assigned to multiple groups, so they can perform tasks based on the group's role and permissions. A group is also assigned to a single or multiple [business units (scope)](/zpc/about-business-units). Depending on the permissions, group users can access data on cloud accounts within specific business units.
You can add groups for single sign-on (SSO). This allows users in the group to log in to the ZPC Admin Portal directly from an Identity Provider's (IdP) portal. Any new users added to this group can also use SSO to log in to the ZPC Admin Portal. The IdP group overrides the local ZPC group.
While adding a group for SSO in the ZPC Admin Portal, make sure to use the same group name that exists on the IdP portal. To learn more, see [Adding an IdP Configuration](/zpc/adding-idp-configuration).
The following default groups are available in the ZPC Admin Portal:
- **Default Super Admin**: A group that has read, add, edit, and delete privileges in the ZPC Admin Portal.
- **Default Read Only**: A group that has only read privileges in the ZPC Admin Portal.
The group entity has the following benefits and enables you to:
- Create and manage groups.
- Assign users to single or multiple groups with specific roles.
- Assign groups to different business units.
- Control users' RBAC permissions through groups.
[]Accessing Groups
You can switch between groups to perform tasks based on the group's role and permissions.
- In the left-side navigation, click the **Profile** (![Profile icon](/downloads/zpc/authentication-authorization/administrators-and-groups/about-administrators/zpc-profileicon.png)
) icon.
- The groups (to which you are added) are displayed.
[See image.](#grouplist)
- Select the required group. The ZPC modules are displayed based on the group's role and permissions.
You can select the default group after logging into the ZPC Admin Portal. This setting ensures that you are part of the same group when you log back in later.
About the Administrators and Groups Page
On the** **Administrators and Groups page (Administration > Administrators and Groups), you can do the following:
- View the list of administrators. For each administrator, you can see the following:
- **Group Name**: The name of the group. Click to view the administrator name and email ID.
[See image.](#admindetails)
- **Role**: The role assigned to the group. Click to view the different [modules](/zpc/zpc-modules-and-global-modules) that this role can access.
[See image.](#modules)
- **Administrators**: The number of administrators in this group.
- **Group Scope**: The number of [business units](/zpc/about-business-units) that are assigned to the group.
- [Add a Group](/zpc/adding-group).
- [View the administrator details](/zpc/about-administrators).
If the administrator belongs to a group that is not associated with any business unit, the following message is displayed next to the administrator's name. [See image.](#scopeinvalid) This indicates that the group is invalid.
- Search for specific data in the searchable columns.
- Sort the column data.
- [Edit the group details.](/zpc/editing-deleting-group)
- [Delete a group.](/zpc/editing-deleting-group)
- [Modify the table and its columns](/zpc/using-tables).
- Export the data as a CSV file.
![View the Groups tab](/downloads/zpc/authentication-authorization/administrators-and-groups/about-groups/zpc-group-page.jpg)
[![View the administrator details](/downloads/zpc/authentication-authorization/administrators-and-groups/about-groups/zpc-admindetails.png)
]
[![View the assigned modules](/downloads/zpc/authentication-authorization/administrators-and-groups/about-groups/zpc-assignedroles.png)
]
[![Group List](/downloads/zpc/authentication-authorization/administrators-and-groups/about-groups/zpc-groupslist.jpg)
]
[![Invalid scope](/downloads/zpc/authentication-authorization/administrators-and-groups/about-groups/zpc-scope-invalid.png)
]