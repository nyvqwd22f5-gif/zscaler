# Understanding the Admin Scope
Source: https://help.zscaler.com/unified/understanding-admin-scope
PDF: https://help.zscaler.com/pdf/com/en/1488241.pdf

With role-based administration, an admin's scope specifies which areas of the organization an admin can manage and view in the Admin Portal. The default admin is assigned the Organization scope over the entire organization. For each additional admin you create, you must assign one of the following scopes:
- Organization
- Department
- Applications
- Location
You can assign a scope over the entire organization or either location or department. When selecting **Location** as a scope, you can assign a Zscaler **Location **to limit the area of impact. When selecting **Department**, you can assign a department to limit their area of impact.
The Effect of a Scope on an Admin
An admin’s scope affects the following areas:
- [Alert Rule Criteria](#rule-criteria)
- [Configuring Alert Rules or Accessing Information](#editing-rules-or-settings)
- [Assigning Scope for Admins](#assigning-scope)
- [Access to Organizational Resources](#access-to-organizational-resources)
- [Access to Digital Experience Monitoring Features](#access-to-admin-portal-features)
The Benefits of Admin Scope and Role
The process of creating an admin by assigning a role, ensures that alert rules and settings configured by that admin aren't impacted when the admin account is modified or deleted in the future. This is because an alert rule or setting is associated with an admin’s role and admin scope rather than a particular admin. If an admin account is deleted, you won't lose all the distinct permissions and functional scopes associated with that admin. You can simply reassign the admin scope and role, which includes the configured permissions and functional scope, to another admin.
For example, your organization has an admin account with access to all administration access and is assigned the Organization scope. If that admin leaves the organization and their account is deleted, the alert rules they created would not be affected and would remain. Furthermore, you can easily assign the next admin the same role and admin scope as the previous admin, without the need to redefine permissions and functional scopes from scratch.
[]Admins can define alert rules and settings for their assigned locations or departments.
- [Admin with Scope over Location](#scope-over-location)
- [Admin with Scope over Department](#scope-over-department)
[]For example, consider Admin A who is assigned a scope over two locations: Germany and France. When Admin A creates an alert rule:
- Admin A is required to make a selection for the Locations criteria. Because of her scope, only Germany and France are available for selection.
- Admin A can choose any or all users, departments, and groups. However, the alert rule only applies to users, department, or group members who are in Germany or France.
In the following scenario depicted, Admin A creates an alert rule and specifies Germany as a location. Admin A then chooses any user, group, or department. The alert rule applies only to users inside the orange box.
![Graphic depicting admin with scope over Germany and France and choosing only to apply rules to Germany](/downloads/zia/documentation-knowledgebase/managing-admins/about-admins/what-admin-scope/admin_applying_rule_to_germany.png)
[]For example, consider Admin B, assigned scope over two departments, HR and IT. When Admin B creates an alert rule:
- Admin B is required to make a selection for the Departments criteria. Only the HR and IT departments are available for selection.
- Admin B is required to make a selection for the Users criteria. Only users from the HR and IT departments are available for selection.
If Admin B selects a department under the Departments criteria, the alert rule applies to all users in that department, no matter which users Admin B selects under the Users criteria. Thus, specifying users from the Users criteria is useful only if Admin B is selecting users from a department different than the one Admin B selects in the Departments criteria (for example, if Admin B selects the IT department in the Departments criteria and then selects users from HR under the Users criteria).
- Admin B is required to select a User Group. The alert rule applies to all members of the specified group, regardless of their associated department. To limit the alert rule to members of the department specified in the Departments criteria, Zscaler recommends that admins choose a user group that includes only those department members. For example, if Admin B wants to ensure an alert rule applies to only members of Finance, the admin must select a User Group with only the Finance department members. Zscaler recommends that you avoid selecting All User Group for a User Group.
- Admin B can select any or all locations. The alert rule applies only to specified users and department or group members in the selected locations.
In the following scenario depicted, Admin B creates an alert rule and specifies the following for each criterion:
- **Users**: John Doe from IT
- **Departments**: HR
- **Groups**: HR-Group
- **Location**: Germany, France, and Belgium
This alert rule applies only to users inside the orange box.
![Graphic illustrating admin with Scope over Department](/downloads/zia/documentation-knowledgebase/managing-admins/about-admins/what-admin-scope/admin_applying_rule_to_specific_user.png)
[]Admins can configure an alert rule or access information (e.g., software inventory) depending on their scope.
For example, consider an alert rule that has a location criterion for Germany and France. Only an admin with scope over both Germany and France can configure this alert rule. An admin who has scope for Germany or only for France would not be able to configure this alert rule.
As another example, consider an admin with the scope assigned to HR with access to the Digital Experience Monitoring Dashboard. The admin can view the Dashboard and the impacted applications if the impacted application is assigned to HR employees. The admin only sees applications that are assigned to HR.
[]If admins have permission to manage admins, their scope limits the scope that they can assign other admins. For example, if Admin A, who has scope over Germany, creates an admin, and she wants to assign a scope by location, only Germany is available as an option. If she wants to assign the admin a scope in the department category, she can choose any (or all) departments.
[]Only admins who have scope over the entire organization can configure organization-wide alert rules, inventory settings, and information. For example, admins with Organization scope can access Inventory Settings, SaaS Integrations, and Authentication Settings.
[]The following table outlines how admin scope impacts the ability to access various Digital Experience Monitoring features within the Admin Portal.
-
-
-
-
-
| Features | Admin Scope Impact |
| -------- | ------------------ |
| **Dashboard** |
| Digital Experience Monitoring DashboardApplicationsUserInventoryAlerts | Admins can view traffic information for areas over which they have scope.For alerts, while configuring an alert rule and specifying users, departments, or locations, the admin can only configure alert rules for users in their assigned departments or for their assigned locations based on their area of scope.For example, if an admin is configuring an alert rule, the admin can only configure the filters for users in their assigned departments or for their assigned locations. For example, if Admin A who has scope over Germany creates an alert, and they want to have the filter applied by location, only Germany is available as an option. For Admin B who has scope over the HR and IT departments, only HR and IT are available as options for the department, and if specifying the users, only users from those departments are available as options.For the Digital Experience Monitoring Dashboard, Applications, User, and Inventory, an admin can only view impacted users and their devices based on their area of scope. |
-
-
-
-
[](/unified/adding-digital-experience-monitoring-roles)
| **Analytics** |
| ------------- |
| **Reporting**System-Generated ReportsQuarterly Business ReportsSnapshotsSelf Service | Admins can access reports based on the areas included in their assigned role and must have the appropriate permission settings. To learn more, see Adding Digital Experience Monitoring Roles. |
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
| **Administration** |
| ------------------ |
| **Administration**Deep TracingInventory SettingsProbes | For Deep Tracing, admins can configure Deep Tracing sessions for users based on their assigned scope.For Inventory Settings, admins require Organization scope to configure Inventory Settings.For probes, a user can configure probes for applications within their area of scope. |
| **Administration Controls**Administrator ManagementUser ManagementLocation ManagementAudit Logs | For Administrator Management > Administrators, admins can only manage Digital Experience Monitoring admins based on their scope.For Administration > API Configuration > Digital Experience API settings, admins require Organization scope to make changes.For User Management, if admins are assigned scope over specific departments, they can only view users from that department. If admins are assigned Organization scope or scope over locations, admins can view all users.For Location Management, if admins are assigned scope over specific locations, they can only view locations from their scope location. If admins are assigned Organization scope or scope over departments, admins can view all locations.Scope does not impact your account profile. |
| **API Configuration**Digital Experience API | For Digital Experience API, admins require Organization scope to make changes. |
| **Integration**Data CollectionSaaS App TenantsWebhooks | For Integration Settings, admins require Organization scope to make changes. |