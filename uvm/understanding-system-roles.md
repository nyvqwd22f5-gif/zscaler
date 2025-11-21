# Understanding System Roles
Source: https://help.zscaler.com/uvm/understanding-system-roles
PDF: https://help.zscaler.com/pdf/com/en/1530653.pdf

System roles are predefined, built-in roles that grant users specific permissions through established access levels. These roles simplify user management by providing a consistent way to assign the necessary privileges for users to perform their tasks while maintaining the platform's security and operational integrity.
The set of available system roles depends on the applications installed within the platform (e.g., UVM, AEM), with each application offering roles specific to its features and workflows. To assign and manage roles, see [Assigning Roles to Users](/uvm/assigning-roles-users) and [Managing System and Custom Roles](/uvm/managing-system-and-custom-roles).
System roles are ideal for standard use cases where common permission sets suffice. When your access requirements extend beyond the system roles, you can create custom roles and configure the access granted to users assigned to those roles. To learn more, see [Creating Custom Roles](/uvm/creating-managing-custom-roles).
The following system roles apply per application:
- [Unified Vulnerability Management (UVM)](#UVM-system-roles)
- [Asset Exposure Management (AEM)](#AEM-system-roles)
To view the specific permissions assigned to a role, click the role name on the Roles page. This opens the role's matrix, where you can view the detailed actions the role can perform. To learn more, see [Managing System and Custom Roles](/uvm/managing-system-and-custom-roles).
[]The following table details the different system roles for the UVM app and the actions each role allows users to perform.
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
| **Role** | **Permissions** |
| -------- | --------------- |
| Admin | Manage data model entities and their fieldsView and manage data source mappingView, create, and manage data sourcesView, create, and manage user-saved views across the platformView and manage outegrationsView and search logsView and manage custom dashboards and reportsView and manage built-in vulnerability dashboard and analyticsView and manage ticketsView and manage ticket scoring, grouping rules, and life-cycle customizationView and manage findingsView and manage assetsTrigger third-party outegration from tickets |
| Vulnerabilities Admin | View all built-in dashboardsManage and view custom dashboards and reportsCreate and configure integrationsRun search queriesView, create, and edit tickets (split and merge)Edit and view ticket settingsView assets and findings |
| Vulnerabilities Editor | View all built-in dashboardsManage and view custom dashboards and reportsRun search queriesView, create, and edit tickets (split and merge)View ticket settingsView assets and findings |
| Vulnerabilities Reader | View all built-in dashboardsView custom reports and dashboardsView tickets and ticket settingsView findingsView tickets |
[]The following table details the different system roles for the AEM app and the actions each role allows users to perform.
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
| **Role** | **Permissions** |
| -------- | --------------- |
| Admin | Manage data model entities and their fieldsView and manage data source mappingView, create, and manage data sourcesView, create, and manage user-saved views across the platformView and manage outegrationsView and search logsView and manage custom dashboards and reportsView and manage built-in dashboards and analyticsView and manage violation ticketsView and manage violation ticket scoring, grouping rules, and life-cycle customizationView and manage policy violationsView and manage assetsTrigger third-party outegration from violation tickets |
| Assets Admin | View all built-in dashboardsManage and view custom dashboards and reportsCreate and configure outegrationsRun search queriesView, create, and edit violation tickets (split and merge)Edit and view violation ticket settingsView assets and policy violations |
| Assets Editor | View all built-in dashboardsManage and view custom dashboards and reportsRun search queriesView, create, and edit violation tickets (split and merge)View violation ticket settingsView assets and policy violations |
| Assets Reader | View all built-in dashboardsView custom reports and dashboardsView violation tickets and violation ticket settingsView policy violationsView violation tickets |