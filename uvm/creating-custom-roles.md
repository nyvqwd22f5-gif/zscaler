# Creating Custom Roles
Source: https://help.zscaler.com/uvm/creating-custom-roles
PDF: https://help.zscaler.com/pdf/com/en/1527841.pdf

User roles control access to features and actions within the platform. After [creating users](/uvm/creating-managing-users) in your account, you can [assign roles](/uvm/assigning-roles-users) to define their access and permissions. You can choose from [predefined system roles](/uvm/understanding-system-roles), or the account admin can create and assign custom roles. Custom roles are configured to reflect your internal policies or workflows.
When new platform features are released, related permissions must be manually added to your custom roles.
To create a custom role:
- Click the **Profile** menu on the top right of the page.
- Go to **Account Settings **> **Permissions **> **Roles**.
- On the **Roles **page, you can create a custom role in the following ways:
- Click **Create**.
-
Duplicate an existing role by hovering over the role in the list and clicking the **Duplicate** icon (![777a3f3e-c9b5-4c06-a036-5b473c4cf9ab.png](/downloads/uvm/account-management/user-management/role-permissions/777a3f3e-c9b5-4c06-a036-5b473c4cf9ab.png)
), or selecting the role and clicking **Duplicate**. The duplicated role is added to the list of roles.
You can't duplicate the system Admin role.
- On the **New Role** page:
- **Role Name**: Enter a unique name for the role.
-
**Resource**: Select the relevant permissions (e.g., **Read**, **Create**, **Edit**, **Delete**, **Audit**) for each resource.
To apply the same permission to all items in a category, select the checkbox at the top of the category. Selecting a higher-level permission (e.g., **Edit**) automatically enables required lower-level permissions (e.g., **Read**).
[See image.](#select-all-checkbox)
-
Click **Next**.
The **Add Users** window appears.
- Select the users you want to assign to the role.
- Click **Add**.
- You can continue to manage users after clicking **Add**:
- To add more users, click **Add Users**.
- To remove users, select them and click **Remove From Role**.
- Click **Finish**.
After changes are saved, the selected users' roles are updated immediately.
Resources
Role permissions are organized into distinct categories, each representing a group of related system resources. Within each category, you can select permissions (i.e., Read, Create, Edit, Delete, and Audit) for custom roles to control access and operations on those resources. These assignments form a permissions matrix for the custom roles that are subsequently assigned to users.
Platform
The following table outlines key platform resources and the specific types of access that can be granted to users through custom roles.
| **Resource** | **Access Granted** |
| ------------ | ------------------ |
| Model Management | Manage data model entities and their fields |
| Data Source Mapping | View and manage data source mapping |
| Data Source | View, create, and manage data sources |
| User Saved Views | View, create, and manage user-saved views across the platform |
| Outegrations | View and manage outegrations |
| Authentications | View and manage authentications |
Explore
The following table outlines key analytics resources and the specific types of access that can be granted to users through custom roles.
| **Resource** | **Access Granted** |
| ------------ | ------------------ |
| Search | View and search logs |
| Reports & Dashboards | View and manage custom dashboards and reports |
Vulnerabilities App (UVM)
The following table outlines key resources of the UVM application and the specific types of access that can be granted to users through custom roles.
| **Resource** | **Access Granted** |
| ------------ | ------------------ |
| Dashboards & Analytics | Built-in vulnerability dashboard and analytics |
| Tickets Page | View and manage tickets |
| Tickets Settings | Ticket scoring, grouping rules, and life-cycle customization |
| Findings Page | View and manage findings |
| Assets Page | View and manage assets |
| Exceptions Page | View and manage exceptions |
| Exceptions Settings | Exceptions form, assignment rules, and notification customization |
Assets App (AEM)
The following table outlines key resources of the AEM application and the specific types of access that can be granted to users through custom roles.
| **Resource** | **Access Granted** |
| ------------ | ------------------ |
| Violations Tickets | View and manage policy violations |
| Policy Violations | Violation ticket grouping rules and life-cycle customization |
| Policy Violations Outegrations | Trigger third-party outegrations from policy violations |
| Policy Rule | View and manage policy rules |
| Analytics & Insights | Built-in vulnerability dashboard and analytics |
| Assets Page | View and manage assets |
| Asset Outegrations | Trigger third-party outegrations from assets |
[]![new role page](/downloads/uvm/administration/account-management/user-management/creating-custom-roles/new%20role%20resrources.png)