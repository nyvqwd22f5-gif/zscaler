# Assigning Entitlements to Users and User Groups
Source: https://help.zscaler.com/zidentity/assigning-entitlements-users-and-user-groups
PDF: https://help.zscaler.com/pdf/com/en/1517711.pdf

You can assign an individual ZIdentity user or user group to a Zscaler service. You must [add users](/zidentity/adding-users) or [user groups](/zidentity/adding-user-groups) before assigning them to a service. You can assign users to perform administrative tasks via [administrative entitlements](/zidentity/about-administrative-entitlements) or assign them as end users via [service entitlements](/zidentity/about-service-entitlements). To view the list of entitlements for a specific user, see [Viewing Entitlements to Assigned to Users](/zidentity/viewing-entitlements-assigned-users).
[]Administrative Entitlements
To assign users to a Zscaler service for performing administrative tasks:
-
Go to **Administration **> **Entitlements **> **Administrative **> service's name.
[See image.](#adminsitrative-entitilement-options)
- Assign users via one of these methods:
- [Assign users via user groups](#user-groups-administrative)
- [Assign users individually](#users-individual-administrative)
[]Service Entitlements
To assign users to a Zscaler service as end users:
-
Go to **Administration **> **Entitlements **> **Service **> service's name.
[See image.](#select-service-entitlement-service)
- Assign users via one of these methods:
- [Assign users individually](#users-individual-service)
- [Assign users via user groups](#user-groups-service)
[]If a user is assigned to a service admin role individually, but they are also a part of a user group with a different admin role, then the role assigned to the individual user takes precedence over the user group role.
-
On the **User Groups **tab, click **Assign Groups**.
[See image.](#assign-groups-option-admin-entitlements)
The **Assign Groups** wizard appears.
-
In the **Assign Groups** wizard:
- On the **Select Groups & Roles** tab, select the user groups that must be assigned to the Zscaler service.
-
In the **Role **column, the drop-down menu includes a list of roles configured on the respective services' admin portal (e.g., the [Role Management](/zia/about-role-management) page in the ZIA Admin Portal). Select the role that must be assigned to each user group.
[See image.](#select-groups-and-roles-admin)
If you want to apply the same role for all groups, enable **Set same role for all selected groups**, and select the preferred role from the drop-down menu.
[See image.](#select-groups-roles-common-admin)
-
The **Microtenant **column is visible only for the Zscaler Private Access (ZPA) service. Select the Microtenant for the admins within the ZPA Admin Portal. To learn more, see [About Microtenants](/zpa/about-microtenants).
[See image.](#Assign-groups-page)
If no Microtenant is configured in the ZPA Admin Portal, you must select **Default** in the **Microtenant **column.
- Click **Next**.
-
On the **Summary **tab, review the assignment details and click **Assign**.
[See image.](#review-group-assigment-admin)
The selected user groups are assigned to the Zscaler service with administrative privileges for all users in the groups.
-
[]On the **Users **tab, click **Assign Users**.
[See image.](#assign-users-button-admin)
The **Assign Users **wizard appears.
-
In the **Assign Users **wizard:
- On the **Select Users & Roles** tab, select the users that must be assigned to the Zscaler service.
-
In the **Role **column, the drop-down menu includes a list of roles configured on the respective services' admin portal (e.g., the [Role Management](/zia/about-role-management) page in the ZIA Admin Portal). Select the role that must be assigned to each user.
[See image](#users-and-roles-admin)
If you want to apply the same role for all groups, enable **Set same role for all selected users**, and select the preferred role from the drop-down menu.
[See image](#users-and-roles-admin-common)
-
The **Microtenant **column is visible only for the Zscaler Private Access (ZPA) service. This is the [Microtenant](/zpa/configuring-microtenants) that you can assign to other admins:
- If you have Full permission to manage administrative entitlements in ZIdentity, you can assign any Microtenant to other admins. You can also edit or delete any Microtenant.
- If you have Restricted Full permission to manage administrative entitlements in ZIdentity and are assigned a **Default** Microtenant in ZPA, you can assign any Microtenant to other admins. You can also edit or delete any Microtenant.
-
If you have Restricted Full permission to manage administrative entitlements in ZIdentity and are assigned a Microtenant other than the **Default** Microtenant, you can only assign that Microtenant to other admins. You can edit or delete only the assigned Microtenant.
[See image.](#Assign-users-page)
If no Microtenant is configured in the ZPA Admin Portal, you must select **Default** in the **Microtenant **column.
- Click **Next**.
-
On the **Summary **tab, review the assignment details and click **Assign**.
[See image.](#summary-users-assigment-admin)
The selected users are assigned to the Zscaler service with administrative privileges.
-
[]On the **User Groups **tab, click **Assign Groups**.
[See image.](#assign-groups-button-service)
The **Assign Groups** wizard appears.
-
In the **Assign Groups** wizard:
-
On the **Select Groups **tab, select the user groups that must be assigned to the Zscaler service.
[See image.](#assign-groups-service)
- Click **Next**.
-
On the **Summary **tab, review the assignment details and click **Assign**.
[See image.](#assign-groups-summary-service)
The selected user groups are assigned to the Zscaler service with all users in the groups as end users.
-
[]On the **Users **tab, click **Assign Users**.
[See image.](#assign-users-button-service)
The **Assign Users **wizard appears.
-
In the **Assign Users **wizard:
-
On the **Select Users **tab, select the users that must be assigned to the Zscaler service.
[See image.](#assign-users-select-service)
- Click **Next**.
-
On the **Summary **tab, review the assignment details and click **Assign**.
[See image.](#assign-users-summary-service)
The selected users are assigned to the Zscaler service as end users.
[]
![A screenshot highlighting a Zscaler service in the Administrative Entitlements page](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidnetity-administrative-entitilement-select-service.png)
[]
![A screenshot highlighting the Assign Groups button in Adminstrative Entitlements](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-administrative-entitlement0assign-groups-button.png)
[]
![A screenshot showing the groups selected to be assigned to a Zscaler service](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-assign-groups-roles.png)
[]
![A screenshot highlighting the option to apply roles to all groups](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-roles-groups.png)
[]
![A screenshot showing the group assigment summary](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-review-admingroups.png)
[]
![A screenshot highlghting the option to assign users to administrative entitlements](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-assign-users-button.png)
[]
![A screenshot highlighting the users selected to be assigned to a Zscaler service](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-users-roles-select-admin.png)
[]
![A screenshot highlighting the option to assign roles to all users](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-select-option.png)
[]
![A screenshot of user assigment summary](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-review-users-roles.png)
[]
![A screenshot highlighting a Zscaler service in Service Entitlements](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-service-entitlements-option.png)
[]
![A screenshot highlighting the option to assign groups to a Zscaler service](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-assign-groups-button-service.png)
[]
![A screenshot highlighting the groups in Select Groups step](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-select-groups-service.png)
[]
![A screenshot of thegroup assignment summary](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-review-groups-service.png)
[]
![A screenshot highlighting thr Assign Users button](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-assign-users-button-service.png)
[]
![A screenshot showing selecting users for a Zscaler service](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-users-service.png)
[]
![A screenshot showing the Assign Users page](/downloads/zidentity/administration/users/assigning-users-zscaler-service/zidentity-users-review-service.png)
[]![A screenshot showing admins assigned to the Zscaler service individually](/downloads/zidentity/administration/entitlements/assigning-entitlements-users-and-user-groups/Assign-users-page.png)
[]
![A screenshot showing admins assigned to the Zscaler service.](/downloads/zidentity/administration/entitlements/assigning-entitlements-users-and-user-groups/Assign-groups-page.png)