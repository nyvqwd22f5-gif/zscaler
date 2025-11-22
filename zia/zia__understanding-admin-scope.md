# Understanding Admin Scope
Source: https://help.zscaler.com/zia/understanding-admin-scope
PDF: https://help.zscaler.com/pdf/com/en/1399731.pdf

With [role-based administration](/zia/about-administrators), an admin's scope specifies which areas of the organization an admin can manage in the ZIA Admin Portal. The default admin has scope over the entire organization. For each additional admin you create, you must select one of the following scopes:
- Organization
- Department
- Location
- Location Group
You can assign scope over the entire organization or either location, location group, or department (you can't combine location, location group, and department). To configure the admin scope, see [Adding ZIA Admins](/zia/adding-admins).
If your organization is using ZIdentity, admins are configured in the ZIdentity Admin Portal, but admin scope is configured in the ZIA Admin Portal.
The Effect of a Scope on an Admin
An admin’s scope affects the following areas:
- [Rule Criteria](#rule-criteria)
- [Editing Rules or Settings](#editing-rules-or-settings)
- [Assigning Scope for New Admins](#assigning-scope)
- [Access to Organizational Resources](#access-to-organizational-resources)
- [Access to ZIA Admin Portal Features](#access-to-admin-portal-features)
The Benefits of Admin Scope and Role
The process of creating an admin by assigning a [role](/zia/adding-admin-roles) ensures that rules and settings configured by that admin aren't impacted even if the admin account is modified or deleted at some point in the future. This is because a rule or setting is associated with an admin’s role (the role’s [admin rank](/zia/about-admin-rank), to be specific) and admin scope rather than a particular admin. Furthermore, if an admin account is deleted, you don't lose all the distinct permissions and functional scopes associated with that admin. You can simply reassign the admin scope and role, which includes configured permissions and functional scopes, to another admin.
For example, your organization’s CISO may have an admin account with access to all security-related policies and scope over the organization. If a CISO leaves the organization and their account is deleted, the policy rules they created would not be affected and would remain in place. Furthermore, you can easily assign the next CISO the same role and admin scope as the previous CISO, without redefining permissions and functional scopes from scratch.
[]Admins can only define rules and settings for their assigned locations, location groups, or departments.
- [Admin with Scope over Location](#scope-over-location)
- [Admin with Scope over Department](#scope-over-department)
![Graphic depicting admin with scope over Germany and France and choosing only to apply rules to Germany](/downloads/zia/documentation-knowledgebase/managing-admins/about-admins/what-admin-scope/admin_applying_rule_to_germany.png)
[]
For example, consider Admin A, assigned scope over two locations, Germany and France. When Admin A creates a policy rule:
- Admin A is required to make a selection for the Locations criteria. Because of her scope, only Germany and France are available for selection.
- Admin A can choose any or all users, departments, and groups. The rule applies, however, only to users, department, or group members who are in Germany or France.
In the scenario depicted below, Admin A creates a rule and specifies Germany as a location. Admin A then chooses any user, group, or department. The rule applies only to users inside the orange box.
![Graphic illustrating admin with Scope over Department](/downloads/zia/documentation-knowledgebase/managing-admins/about-admins/what-admin-scope/admin_applying_rule_to_specific_user.png)
[]
As another example, consider Admin B, assigned scope over two departments, HR and IT. When Admin B creates a policy rule:
- Admin B is required to make a selection for the Departments criteria. Only the HR and IT departments are available for selection.
- Admin B is required to make a selection for the Users criteria. Only users from the HR and IT departments are available for selection.
If Admin B selects a department in the Departments criteria, the rule applies to all users in that department, no matter which users Admin B selects in the Users criteria. Thus, specifying users in the Users criteria is useful only if Admin B is selecting users from a department different than the one Admin B selects in the Departments criteria (for example, if Admin B selects the IT department in the Departments criteria and then selects users from HR in the Users criteria).
- Admin B is required to select a group. The rule applies to all members of the specified group, regardless of their department. To limit the rule to just members of the department specified in the Departments criteria, Zscaler recommends that admins choose a group that contains just those department members. For example, if an admin wants to make sure a rule applies just to members of Finance, the admin must create a group with just the Finance department members and then select that group. Zscaler recommends that you avoid selecting “Any” for group.
- Admin B can select any (or all) locations. The rule applies only to specified users and department or group members in the selected locations.
In the scenario depicted below, Admin B creates a rule and specifies the following for each criteria:
- Users: John Doe from IT
- Departments: HR
- Groups: HR-Group
- Location: Germany, France, and Belgium
This rule applies only to users inside the orange box.
[]Admins can edit a rule or setting only if their scope is equal to or greater than the scope assigned the rule or setting. Along with scope, admin rank also impacts which rule or setting an admin can edit.** **For example, consider a URL filtering rule that has a location criterion of Germany and France. Only an admin with scope over both Germany and France can edit this rule. Admin A, who has scope only over Germany, would not be able to edit this rule.
[]If admins have permission to manage admins, their scope limits the scope that they can assign other admins. For example, if Admin A, who has scope over Germany, creates an admin, and she wants to assign a scope by location, only Germany is available as an option. However, if she wants to assign the admin a scope in the department category, she can choose any (or all) departments.
[]Only admins who have scope over the entire organization can create or edit organization-wide policies, settings, and resources. For example, only admins with organizational scope can edit security policies or create custom URL categories.
[]The following table outlines how admin scope impacts the ability to access the ZIA Admin Portal features.
-
-
-
-
-
-
-
-
| Dashboard |
| --------- |
| Features | Admin Scope Impact |
| Web OverviewSecurityWeb BrowsingCloud ApplicationsMobile ApplicationsEmail OverviewDNS OverviewFirewall Overview | Admins can only view traffic information for areas over which they have scope. |
|  |
-
-
-
-
-
-
-
| Analytics |
| --------- |
| Features | Admin Scope Impact |
| **Reporting**Interactive ReportsScheduled Reports | Admins can only access reports for areas over which they have scope. |
| **Insights**Web InsightsMobile InsightsEmail InsightsFirewall InsightsDNS Insights | Admins can only access insights for areas over which they have scope. |
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
| Policy |
| ------ |
| Features | Admin Scope Impact |
| **Web** > **Security**Malware ProtectionAdvanced Threat ProtectionSandboxBrowser Control | Admins require organizational scope to edit policies. |
| **Web** > **Access Control**URL & Cloud App ControlFile Type ControlBandwidth ControlSSL Inspection | Admins can only define rules for their assigned locations or departments. |
| **Web** > **Data Loss Prevention**Data Loss Prevention | Admins can only define rules for their assigned locations or departments. |
| **Mobile** > **Zscaler App Configuration**Zscaler Client Connector Portal | All admins can edit policies here. |
| **Mobile** > **Security**Mobile Malware Protection | Admins require organizational scope to edit policies. |
| **Mobile** > **Access Control**Mobile App Store Control | Admins can only define rules for their assigned locations or departments. |
| **Firewall** > **Access Control**Firewall ControlDNS ControlFTP Control | Admins can only define rules for their assigned locations or departments. |
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
| Administration |
| -------------- |
| Features | Admin Scope Impact |
| **Settings** > **Account Management**My ProfileCompany ProfileAlertsPrint All Policies | Scope does not impact My Profile and Print All Policies.For Company Profile, admins require organizational scope to make changes.For Alerts, if specifying users, departments, or locations, admins can only set alerts for users in their assigned departments or for their assigned locations. For example, if Admin A, who has scope over Germany, creates an alert, and she wants to have the alert apply by location, only Germany is available as an option. For Admin B who has scope over the HR and IT departments, only HR and IT are available as options for department, and if specifying users, only users from those departments are available as options. |
| **Settings** > **Cloud Configuration**Nanolog Streaming ServiceAdvanced SettingsVirtual Service Edges or Virtual ZENsICAP SettingsPartner Integrations | Admins require organizational scope to make changes. |
| **Authentication** > **Authentication Configuration**Authentication SettingsUser ManagementIdentity Proxy SettingsCloud Service API Key Management | For Authentication Settings, admins require organizational scope to make changes.For User Management, if admins are assigned scope over specific departments, they can only manage users from that department. If admins are assigned organizational scope or scope over locations, admins can manage all users. |
| **Authentication** > **Administration Controls**Administrator ManagementRole ManagementAudit LogsBackup & Restore | For Administrator Management, the admins’ scope limits the scope that they can assign other admins. To make changes to Auditors in Administrator Management, admins must have organizational scope.For Role Management, admin requires organizational scope to make changes.For Audit Logs, admins require organizational scope to make changes.For Backup & Restore, admins with limited scope may back up policies, but only admins with organizational scope can restore policies. |
| **Resources** > **Traffic Forwarding**LocationsVPN CredentialsHosted PAC FileseZ Agent ConfigurationZscaler Client Connector Devices | For Locations:Admins require organizational scope to add locations.If the admin’s scope is limited by location, the admin can make changes only for that location.If the admin has scope over organizations or departments, the admin can make changes to all locations.For all other features, admins require organizational scope to make changes. |
| **Resources **> **Access Control**URL CategoriesBandwidth ClassesTime IntervalsEnd User Notifications | For URL categories whose super category is User-Defined, admins require that their operational scope matches at least one of the scopes defined in the category to make changes.For all other features, admins require organizational scope to make changes. |
| **Resources **> **Firewall**Network ServicesNetwork ApplicationsIP Groups | For Network Services, admins with organizational scope can add and edit Services and Services Groups, while admins with limited scope can add Services and Service Groups, but not edit them.For Network Applications, admins with organizational scope can add and edit Applications Groups, while admins with limited scope can add Application Groups, but not edit them.For IP Groups, admins with organizational scope can add and edit Source and Destination IP groups, while admins with limited scope can add Source and Destinations IP Groups, but not edit them. |
| **Resources **>** Data Loss Prevention**DLP Dictionaries & EnginesDLP Notification TemplatesIndex TemplatesIndex Tool | Admins require organizational scope to make changes. |