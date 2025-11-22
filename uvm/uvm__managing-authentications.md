# Managing Authentications
Source: https://help.zscaler.com/uvm/managing-authentications
PDF: https://help.zscaler.com/pdf/com/en/1529503.pdf

After [creating an authentication](/uvm/configuring-authentications), you can manage and monitor it from the Authentications page. This page provides a centralized view of all configured authentications and their usage across data sources and outegrations. To learn more, see [Creating Data Sources](/uvm/creating-data-sources) and [Creating Outegrations](/uvm/creating-outegrations).
Authentication is critical to maintaining stable data connections and access control. Manage authentications cautiously to avoid service disruptions, failed data ingestion, or unintended access issues.
For each authentication, you can see:
- **Authentication Name**: The name of the authentication.
- **Vendor**: The name of the third-party vendor for which the authentication was created.
- **In Use**: The number of data **Sources** or **Outegrations** using the authentication. Hovering over the value displays additional details on the specific sources and outegrations that are using the authentication.
- **Created By**: The user who created the authentication.
- **Last Update**: The time and date when the authentication was last updated.
- **Updated By**: The user who last updated the authentication.
[See image.](#authentications-page)
[]![The authentications page displaying the table of authentications with their details.](/downloads/uvm/administration/connectors/authentications/managing-authentications/Authentications%20Page.png)
You can modify or remove authentications as needed directly from the Authentications page (Configure > Authentications).
For access to Authentications, your assigned role must include the Read, Create, Edit, and Delete permissions under the Platform - Authentications resource. To learn more, see [Creating Custom Roles](/uvm/creating-custom-roles) and [Assigning Roles to Users](/uvm/assigning-roles-users).
[See image.](#authentications-permissions)
- [Edit Authentications](#editing-authentications)
- [Delete Authentications](#deleting-authentications)
[]You can edit an authentication to update expired credentials, adjust access permissions for new integrations, or rename it for easier identification.
To edit an authentication:
- Hover over the authentication you want to modify, and click the **Edit **icon.
- Update the necessary details.
- Click **Save **to apply changes to the authentication.
If the authentication is currently in use by sources or outegrations, a confirmation message appears to ensure you're aware of the impact your changes might have.
- Click **Continue** to apply the changes to the existing authentication.
- Click **Save as New **to create a new authentication instance while preserving the original.
[See image.](#continue-save-as-new)
[]![184178c7-0871-475a-92ac-1393477a72cb.png](/downloads/uvm/configure/authentication/configuring-authentications/184178c7-0871-475a-92ac-1393477a72cb.png)
[]You can delete an authentication that is no longer in use. This might be the case if the source or outegration it was created for now uses a different authentication, or if your organization no longer works with the associated vendor.
Authentications currently in use by data sources or outegrations cannot be deleted. If your goal is to stop data ingestion from a third-party vendor, consider deactivating the relevant data source instead. To learn more, see [Managing Data Sources](/uvm/managing-data-sources).
To delete a specific authentication:
-
Hover over the authentication you want to delete, and click the **Delete **icon.
A warning message appears.
[See image.](#deleting-in-use-authentication)
- Click **Delete**.
To delete multiple authentications:
- Select the checkboxes for the authentications that you want to delete.
- Click the **Delete** button at the top of the page.
A warning message appears.
- Click **Delete**.
[]**![in-use%20authentications.png](/downloads/uvm/configure/authentication/managing-authentications/in-use%20authentications.png)
**
[]![c977a02a-7693-43b4-bb16-5b254df0715d.png](/downloads/uvm/configure/authentication/configuring-authentications/c977a02a-7693-43b4-bb16-5b254df0715d.png)