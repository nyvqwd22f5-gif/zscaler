# Managing Entitlements
Source: https://help.zscaler.com/unified/managing-entitlements
PDF: https://help.zscaler.com/pdf/com/en/1505801.pdf

Entitlements refer to the type of access privileges and permissions that are assigned to ZIdentity users and user groups. ZIdentity supports [Administrative](/unified/about-administrative-entitlements) and [Service](/unified/about-service-entitlements) entitlements.
Administrative
The Administrative entitlements are used to assign and manage ZIdentity [users](/unified/about-users-0) and [user group's](/unified/about-user-groups) administrative access to a Zscaler service (e.g., Internet & SaaS, Private Applications, etc.) with a specific role that is created in the Admin Portal.
To provide users or user groups administrative access and assign a role:
-
Add [roles](/unified/adding-zidentity-admin-roles) in the Admin Portal.
The roles of the respective services are automatically synced into the ZIdentity database at regular intervals. To ensure that your ZIdentity database is up to date, you can perform a manual sync from the **View Roles** page. [See image.](#view-roles)
- Add [users](/unified/adding-users-0) and [user groups](/unified/adding-user-groups) in the ZIdentity.
- Go to **Administration **> **Admin Management **> **Role Based Access Control** > **Administrative Entitlements**.
-
On the [Administrative Entitlements](/unified/about-administrative-entitlements) page, select the service for which you want to assign users or user groups with admin roles.
[See image.](#zsl-admin-e)
-
[Assign users or user groups with admin roles to the service](/unified/assigning-entitlements-users#admin-entitlements).
[See image.](#zsl-assignroles)
- (Optional) [View the list of assigned users and user groups as service admins](/unified/about-administrative-entitlements).
If a user is assigned to multiple user groups with different levels of access, then the group created first takes precedence, and the user can perform tasks according to the role assigned to that group. However, if a user is assigned to a service admin role individually, and they are also a part of a user group with a different admin role, then the role assigned to the individual user takes precedence over the user group role.
Service
The Service entitlements are used for assigning ZIdentity [users](/unified/about-users-0) and [user groups](/unified/about-user-groups) to a Zscaler service (e.g., Internet & SaaS, Private Applications, etc.).
To assign users or user groups to a Zscaler service:
- Add [users](/unified/adding-users-0) and [user groups](/unified/adding-user-groups) in the ZIdentity.
-
Go to **Administration** > **Entitlements **> **End User Entitlements**.
[See image.](#zsl-service-e)
- On the [Service Entitlements](/unified/about-service-entitlements) page, select the service for which you want to assign users or user groups.
-
[Assign users or user groups to the service](/unified/assigning-entitlements-users#service-entitlements).
[See image.](#zsl-assignusers)
- (Optional) [View the list of users and user groups assigned to the service](/unified/about-service-entitlements).
[]![The Administrative Entitlements page](/downloads/zidentity/administration/entitlements/managing-entitlements/Administrative-ent.png)
[]![Assigning admin roles to user groups](/downloads/zidentity/administration/entitlements/managing-entitlements/Assign-groups.png)
[]![The Service Entitlements page](/downloads/zidentity/administration/entitlements/managing-entitlements/service%20ent.png)
[]
![Assigning users to the service](/downloads/zslogin/administration/entitlements/managing-entitlements/zid-service-assisgn-users.png)
[]
![View Roles](/downloads/zidentity/administration/entitlements/managing-entitlements/view-roles.png)