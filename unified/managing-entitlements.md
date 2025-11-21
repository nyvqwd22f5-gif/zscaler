# Managing Entitlements
Source: https://help.zscaler.com/zidentity/managing-entitlements
PDF: https://help.zscaler.com/pdf/com/en/1499226.pdf

Entitlements refer to the type of access privileges and permissions that are assigned to ZIdentity users and user groups. ZIdentity supports [Administrative](/zidentity/about-administrative-entitlements) and [Service](/zidentity/about-service-entitlements) entitlements.
Administrative
The Administrative entitlements are used to assign and manage ZIdentity [users](/zidentity/about-users) and [user group's](/zidentity/about-user-groups) administrative access to a Zscaler service (e.g., ZIA Admin Portal, ZPA Admin Portal) with the specific role that is created in the respective Zscaler service.
To provide users or user groups administrative access and assign a role:
-
Add roles on the respective Zscaler admin portal of that service (e.g., ZIA Admin Portal). To add roles for:
- ZIdentity Admin Portal, see [Adding ZIdentity Admin Roles](/zidentity/adding-zslogin-admin-roles).
- ZIA Admin Portal, see [Adding ZIA Admin Roles](/zia/adding-admin-roles).
- ZPA Admin Portal, see [Adding ZPA Admin Roles](/zpa/configuring-administrator-roles).
- ZDX Admin Portal, see [Adding ZDX Admin Roles](/zdx/adding-zdx-roles).
- Zscaler Client Connector Portal, see [Adding Client Connector Admin Roles](/client-connector/adding-roles).
- Zscaler Cloud & Branch Connector Admin Portal, see [Adding Cloud & Branch Admin Roles](/cloud-branch-connector/adding-admin-roles).
- Deception Admin Portal, see [About Users & Roles](/deception/about-users-roles#deception-add-new-user-admin-portal).
- Data Security Posture Management (DSPM), see [About Access Roles](/dspm/about-access-roles).
- Business Insights Admin Portal, see [About Administrators in Business Insights](/business-insights/about-administrators-business-insights)[.]
-
Risk360 Admin Portal, see [About Administrators in Risk360](/risk360/about-administrators-risk360).
ZIdentity supports login to Zscaler Breach Predictor and External Attack Surface Management (EASM) through Risk360, even if the Risk360, Breach Predictor, or EASM tenants have not been migrated to ZIdentity.
- Workflow Automation Admin Portal, see [Managing Admin Assignments](/workflow-automation/managing-admin-assignments).
- Breach Predictor, see [Using Breach Predictor](/breach-predictor/using-zscaler-breach-predictor).
- EASM Admin Portal, see [About Role Management](/easm/about-role-management).
- Zero Trust Branch, see [Understanding Zero Trust Branch Access Roles](/zero-trust-branch/understanding-zero-trust-branch-access-roles).
- Zscaler Cellular Admin Portal, the [Cellular Edge service](/zscaler-cellular/what-zscaler-cellular) must be enabled for your organization. To enable Cellular Edge, your organization must have ZIA, ZPA, and Branch Connector services enabled. Cellular Edge is not supported if your organization has more than one of either ZIA or ZPA tenants. To learn more, contact your Zscaler Account team.
The roles on the respective admin portals are automatically synced into the ZIdentity database at regular intervals. To ensure that your ZIdentity database is up to date, you can perform a manual sync from the **View Roles** page. [See image.](#view-roles)
- Add [users](/zidentity/adding-users) and [user groups](/zidentity/adding-user-groups) in the ZIdentity Admin Portal.
- Go to **Administration** > **Entitlements **> **Administrative**.
-
On the [Administrative Entitlements](/zidentity/about-administrative-entitlements) page, select the service for which you want to assign users or user groups with admin roles.
[See image.](#zsl-admin-e)
-
On the **Users **or **User Groups** tab, click **Assign Users** or **Assign Groups** to create a new administrative entitlement. You can also [edit or delete](/zidentity/editing-or-deleting-items) the entitlements, if required.
[See image.](#Assign-groups-delete)
-
[Assign users or user groups with admin roles to the service](/zidentity/assigning-entitlements-users-and-user-groups#admin-entitlements).
[See image.](#zsl-assignroles)
- (Optional) [View the list of assigned users and user groups as service admins](/zidentity/about-administrative-entitlements).
If a user is assigned to multiple user groups with different levels of access, then the group created first takes precedence, and the user can perform tasks according to the role assigned to that group. However, if a user is assigned to a service admin role individually, and they are also a part of a user group with a different admin role, then the role assigned to the individual user takes precedence over the user group role.
Service
The Service entitlements are used for assigning ZIdentity [users](/zidentity/about-users) and [user groups](/zidentity/about-user-groups) to a Zscaler service (e.g., ZIA, ZPA).
To assign users or user groups to a Zscaler service:
- Add [users](/zidentity/adding-users) and [user groups](/zidentity/adding-user-groups) in the ZIdentity Admin Portal.
-
Go to **Administration** > **Entitlements **> **Service**.
[See image.](#zsl-service-e)
- On the [Service Entitlements](/zidentity/about-service-entitlements) page, select the service for which you want to assign users or user groups.
-
[Assign users or user groups to the service](/zidentity/assigning-entitlements-users-and-user-groups#service-entitlements).
[See image.](#zsl-assignusers)
- (Optional) [View the list of users and user groups assigned to the service](/zidentity/about-service-entitlements).
[]![The Administrative Entitlements page](/downloads/zidentity/administration/entitlements/managing-entitlements/Administrative-ent.png)
[]
![User Groups tab of Zscaler Client Connector service in Administrative entitlement with Assign Groups button highlighted.](/downloads/tech-pubs-drafts/zidentity-draft-articles/draft-managing-entitlements-doc-60430/Assign-groups-delete.png)
[]![Assigning admin roles to user groups](/downloads/zidentity/administration/entitlements/managing-entitlements/Assign-groups.png)
[]![The Service Entitlements page](/downloads/zidentity/administration/entitlements/managing-entitlements/service%20ent.png)
[]
![Assigning users to the service](/downloads/zslogin/administration/entitlements/managing-entitlements/zid-service-assisgn-users.png)
[]
![View Roles](/downloads/zidentity/administration/entitlements/managing-entitlements/view-roles.png)