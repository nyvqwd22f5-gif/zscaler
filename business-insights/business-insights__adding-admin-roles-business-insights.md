# Adding Admin Roles in Business Insights
Source: https://help.zscaler.com/business-insights/adding-admin-roles-business-insights
PDF: https://help.zscaler.com/pdf/com/en/1473166.pdf

Roles dictate the level of access admins have to a feature or module in the Business Insights Admin Portal. Configuring the Business Insights admin role is one of the tasks you must complete when configuring role-based administration. To learn more, see [Configuring Role-Based Administration](/business-insights/configuring-role-based-administration-business-insights).
Prerequisites
Before you can configure roles, ensure the following prerequisites are met:
- You must have the proper permissions to configure a role.
- You must have organizational scope.
Adding Admin Roles
To configure admin roles:
- Go to **Administration **>** Role Management**.
- Click **Add Role**.
The **Add Role** drawer appears.
- In the **Add Role** drawer:
- **Name**: Enter a name** **for the admin role.
-
**Permissions**: Permissions allow you to control an admin's access to the major features in the Business Insights Admin Portal. Depending on the feature, you must select one of the following permissions:
- **Full**: Allows admins to view, add, edit, and delete items.
- **View Only**: Allows admin view-only access to the feature.
- **None**: Doesn’t allow admins access to the feature.
- **Visible**: Allows admin to view specific data in the Business Insights Admin Portal.
- **Obfuscated**: Specific data is obfuscated in the Business Insights Admin Portal for the admin.
For each role you configure, you must assign permissions in the following categories:
- [General Permissions](#general)
- [Module Permissions](#module)
- [Feature Permissions](#feature)
- [Data Visibility](#data)
[See image.](#add-role-wind-img)
-
Click **Save**
You can [edit or delete](/business-insights/editing-or-deleting-items-business-insights) admin roles at any time.
[]For **General Permissions**, admins can manage other admins, view Zscaler Internet Access (ZIA) users and locations, or enable remote assistance in:
- Administrator Management (Administration > Administration Management)
- Remote Assistance Management (Help > Remote Assistance)
- ZIA User Management (Administration > ZIA Users)
- ZIA Location Management (Administration > ZIA Locations)
[]For **Module Permissions**, admins can view and manage the following Business Insights modules:
- Application Insights (Applications > Application Insights)
- All Applications (Applications > All Applications)
- Application Settings (Applications > Application Settings)
- Workplaces (all the modules inside the Workplaces section)
- All Contracts (Applications > All Contracts)
[]For **Feature Permissions**, admins can configure scheduled reports and set up Workflow Automation, or view system-generated reports under the Reports section.
[]The **Data Visibility **permission allows you to view or obfuscate the usernames throughout the Business Insights Admin Portal for the role.
[]![Create Role Drawer](/downloads/tech-pubs-drafts/business-insights-draft-articles/viewing-application-details-0/Business-Insights-Add-role-drawer.png)