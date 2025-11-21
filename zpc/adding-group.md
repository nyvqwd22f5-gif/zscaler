# Adding a Group
Source: https://help.zscaler.com/zpc/adding-group
PDF: https://help.zscaler.com/pdf/com/en/1394136.pdf

A[ group](/zpc/about-groups) is a logical entity that includes several users. Each group is assigned a single role and all users in the group are assigned the same role. You can add a new group and assign a specific [predefined role](/zpc/predefined-roles-and-permissions) or custom role, but you can assign multiple [business units](/zpc/about-business-units) (scopes) to the group. All users belonging to that group are assigned the same role and permissions.
Adding a Group
To add a group:
- Go to **Administration **>** Administrators and Groups**.
- On the **Administrators and Groups** page, select the **Groups** tab.
- Click **Add Group**.
[See image.](#groupbutton)
- In the **Add Group** window:
- **Group Name**: Enter the name of the group.
- **Role**: Select the role from the drop-down menu. You can select either a [predefined role](/zpc/predefined-roles-and-permissions) or a custom role.
- **Scope**: Select one or multiple scopes (business units) that must be assigned to the group. [Business units](/zpc/about-business-units) are logical containers for cloud accounts in the ZPC Admin Portal. Users can view data and perform specific tasks on cloud accounts within those business units.
- **Single Sign-On**: Select to enable SSO. This allows users in the group to log in to the ZPC Admin Portal directly from their Identity Provider's (IdP) portal. To learn more, see [About SAML](/zpc/about-saml).
- **Comments**: Enter any description for the group.
[See image.](#groupdetails)
- Click **Save**.
The newly added group is displayed on the **Group** tab of the **Administrators and Groups** page.
[![Click the Add Group button](/downloads/zpc/authentication-authorization/administrators-and-groups/adding-group/zpc-addgroupbutton.png)
]
[![Add the group details](/downloads/zpc/authentication-authorization/administrators-and-groups/adding-group/zpc-add-groupwindow.png)
]