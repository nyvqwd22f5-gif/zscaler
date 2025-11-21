# Configuring Entity Drawers in UVM
Source: https://help.zscaler.com/uvm/configuring-entity-drawers-uvm
PDF: https://help.zscaler.com/pdf/com/en/1527911.pdf

Zscaler Unified Vulnerability Management (UVM) provides a default UI configuration for displaying the main entity drawers (e.g., tickets, assets, findings, exceptions). You can customize the UI fields and organize the information layout within the entity drawer to meet your organization's specific needs.
To configure the drawer:
- In the **Vulnerabilities** app, go to **Settings** > **UI Config**.
[See image.](#vulns-settings-ui-config)
-
From the **Entity **drop-down menu, select the entity drawer you want to configure (e.g., **Ticket**, **Asset**, **Finding**, **Exception**).
The available fields vary depending on the selected entity.
If you select **Ticket **or **Finding**: from the **Type **drop-down menu, select the type of entity (e.g., **CVE**, **DEFAULT**, **MISCONFIG**).
- (Optional) Select the **Severity** checkbox to display the severity level in the top panel of the entity drawer.
-
(Optional) Select the **Status Timeline** checkbox to display the status timeline in the top panel of the entity drawer.
[See image.](#severity-status-timeline-ticket-drawer)
- Save the settings in one of the following ways:
- Click **Save **to update the current configuration.
- Click **Save as New Type** to save the settings as a new type.
Creating Types
You can create a new type for the different entities.
To create a new type:
- From the **Entity **drop-down menu, select the entity you want to configure (e.g., **Ticket**).
- From the **Type **drop-down menu, select the type of entity (e.g., **CVE**, **MISCONFIG**), and use it as a template to create a new type. The original types are not affected.
- Configure the fields and settings as needed.
- Click **Save as New Type**.
- Enter a name for the new type.
-
Click **Apply**.
The new type is added to the **Type** drop-down menu.
Creating and Managing Tabs
For each entity drawer, you can manage system tabs, and also create and configure custom tabs. Each tab corresponds to a configurable element in the entity drawer. You can perform the following actions when customizing an entity drawer:
- [Rearrange Tabs](#rearrange-tabs)
- [Add Tabs](#add-tabs)
- [Delete Tabs](#delete-tabs)
- [Restore System Tabs](#restore-system-tabs)
[]![vulns settings ui config](/downloads/uvm/vulnerability-management/settings-uvm/configuring-ticket-ui-vulnerabilities-app/vulns%20settings%20ui%20config.png)
[]![severity and status timeline in ticket drawer](/downloads/uvm/vulnerability-management/settings-uvm/configuring-ticket-ui-vulnerabilities-app/severity%20and%20status%20timeline%20in%20ticket%20drawer.png)
[]To rearrange the order of tabs:
-
Hover over the grid icon to drag the tab to the desired position.
[See image.](#hover-rearrange)
- Save the settings in one of the following ways:
- Click **Save **to update the current configuration.
- Click **Save as new Type** to save the settings as a new type.
[]![hover and rearrange](/downloads/uvm/vulnerability-management/settings-uvm/configuring-ticket-ui-vulnerabilities-app/hover%20and%20rearrange.png)
[]To add tabs to an entity drawer:
- Click **Add Tab**.
-
Click **Add Custom Tab**.
A dialog window appears.
- In the dialog window:
- **Tab Name**: Enter a name for the tab.
- **Tab Main Projection**: Select the entity from the drop-down menu that the tab should display data from.
- **Should show the tab by field**: Select a field to set the tab visibility. The tab appears only when the selected field is populated.
- **Type**: Select the tab type.
- **Fields**: Data is displayed as a list of fields.
- **2 Columns**: Data is displayed in two columns.
- **Table**: Data is displayed in a table.
- **Text**: Data is displayed as plain text.
- Click **Apply**.
- For table tabs, select how the data should be displayed.
- **Visible**: Select to display all data by default.
- **On Expand**: Select to display data when expanding the table.
- Save the settings in one of the following ways:
- Click **Save **to update the current configuration.
- Click **Save as new Type** to save the settings as a new type.
[]To delete a tab, hover over the tab and click the **Delete **icon.
[See image.](#hover-delete)
[]You can restore system tabs that were deleted.
-
Click **Add Tab**.
A list of deleted system tabs appears.
- Select the deleted tab from the list.
[See image.](#deleted-system-tabs)
- Save the settings in one of the following ways:
- Click **Save **to update the current configuration.
- Click **Save as new Type** to save the settings as a new type.
[]![hover and delete](/downloads/uvm/vulnerability-management/settings-uvm/configuring-ticket-ui-vulnerabilities-app/hover%20and%20delete.png)
[]![abaa7a1f-15b3-455c-9973-aec1940d2d8f.png](/downloads/uvm/vulnerability-management/settings/configuring-ticket-ui-vulnerabilities-app/abaa7a1f-15b3-455c-9973-aec1940d2d8f.png)
Customizing Fields in Tabs
You can customize the presentation of information within each tab and add new fields to a tab.
The following table lists the differences between configuring system tabs and custom tabs.
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
| **Tab Type** | **Available Configurations** |
| ------------ | ---------------------------- |
| System Tabs | Rearrange by dragging to a new position.Add new fields.Delete tabs.Restore deleted tabs.For the Details tab, you can specify whether fields appear on the left or right columns.Configure data as fully visible or revealed only when expanding the respective table row (Visible/On Expand). |
| Custom Tabs | Edit tabs, sections, and fields.Rearrange by dragging to a new position.Add new fields.Delete tabs (cannot be restored later).Configure data as fully visible or revealed only when expanding the respective table row (Visible/On Expand). |
When customizing fields, you can do the following:
- [Rearrange Fields](#rearrange-fields)
- [Delete Fields](#delete-fields)
- [Add Custom Fields](#add-fields)
- [Edit Custom Fields](#edit-fields)
After completing the configuration of the UI settings, click **Save**.
[]To rearrange the order of fields on the tab or section, hover over the grid icon to drag the field to the desired position.
[]To delete a field, click the **Delete **icon.
[]You can add a new field to a system tab or to a custom tab.
To add a new custom field:
-
Click **Add Field**.
A dialog window appears.
- In the dialog window:
- **Display Name**: Enter a name for the field.
- **Field Name**: Select a field from the drop-down menu.
- (Optional) **Link Field**: Select a field from the drop-down menu. If a field contains a valid URL, the hyperlink is populated within the field on the ticket or asset. The **Field Name **text is displayed as a clickable hyperlink.
- Click **Apply**.
[]To edit a custom field:
- Hover over the tile of the field you want to edit.
- Click the **Edit **icon.
- Make the necessary changes, and click **Apply**.
You cannot edit a system tab, including the name, type, and default fields. These can only be rearranged or deleted.