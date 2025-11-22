# Managing Shared Configurations for ZDX Alerts
Source: https://help.zscaler.com/workflow-automation/managing-shared-configuration-zdx-alerts
PDF: https://help.zscaler.com/pdf/com/en/1464316.pdf

The Shared Configurations page helps you govern location and location group-based alerts by configuring multiple locations into a single resource for your organization. Maintaining multiple workflows to create tickets for every location impacted by a single event is challenging. Therefore, this page enables you to create a shared configuration resource that hosts multiple location groups with a dedicated ticketing system and an assignee for each location.
The shared configuration is predominantly used when creating workflows for location and location group-based alerts. It acts as a centralized configuration that can be shared across various workflows. These configurations are managed by defining the associated JSON schema to support workflows.
On the Shared Configurations page, you can do the following:
- [Add Shared Configuration Resources](#add-shared-config)
- [Edit Shared Configuration Resources](#edit-shared-config)
- [View Shared Configuration Resources](#view-shared-config)
- [Delete Shared Configuration Resources](#delete-shared-config)
[]To add a shared configuration resource:
- Go to **Workflows** > **Shared Configurations**. The **Shared Configurations** page appears.
-
Click **Add More**. The **Add New Resource** page appears.
[See image.](#add-shared-config-window)
- On the **Add New Resource** page:
- **Name**: Enter a name for the resource.
- **Schema**: From the drop-down menu, select a schema. You can select a location- or location group-based schema.
- [Location-based schema](#location-schema)
- [Location group-based schema](#location-group-schema)
- **Description**: Enter additional information or notes for the resource.
-
(Optional) Click the **Add** icon and repeat the preceding step to add more ticketing configurations to the resource.
[See image.](#add-icon-location-groups-add-window)
- Click **Save**. The shared configuration resource is added.
[]In the** Location Group Ticketing Configurations** section:
- **Location Group Name**: Enter the location group name. Align the location group name with the location groups configured in the ZDX Admin Portal—for example, US-City-Group.
- **Ticketing Type**: From the drop-down menu, select the type of ticket. The ticketing type is **ServiceNow**.
- **Ticketing System**: From the drop-down menu, select a ticketing system with the appropriate tenant for the alert containing the corresponding location group.
- **Assignee**: From the drop-down menu, select the email address of the admin to whom you want to assign the ticket. The assignee details must be configured on the [Integration Users](/workflow-automation/draft-managing-integration-users-zdx) page.
[]In the** Location Ticketing Configurations** section:
- **Location Name**: Enter the location name. Align the location name with the locations configured in the ZDX Admin Portal—for example, US-southern-location.
- **Ticketing Type**: From the drop-down menu, select the type of ticket. The ticketing type is **ServiceNow**.
- **Ticketing System**: From the drop-down menu, select a ticketing system with the appropriate tenant for the alert containing the corresponding location.
- **Assignee**: From the drop-down menu, select the email address of the admin to whom you want to assign the ticket. The assignee details must be configured on the [Integration Users](/workflow-automation/draft-managing-integration-users-zdx) page.
[]When managing shared configurations, you can view shared configurations and the details for a shared configuration.
- [Viewing Shared Configurations](#view-shared-configurations)
- [Viewing Shared Configuration Details](#view-shared-configuration-details)
[]To view shared configurations, go to **Workflows **> **Shared Configurations**. The **Shared Configurations** page appears, listing all the shared configurations configured for your organization. For each shared configuration, you can view the following information:
- **Name**: The name of the shared configuration.
- **Description**: The description of the shared configuration.
[See image.](#view-all-shared-configurations)
[]To view shared configuration details:
- Go to **Workflows **> **Shared Configurations**. The **Shared Configurations** page appears.
-
Click the **View** icon next to the shared configuration resource. The **View Shared Configuration** window appears.
[See image.](#view-icon)
-
In the **View Shared Configuration** window, view all the details about the resources, such as the name, schema, and ticketing configurations. You cannot modify the resource details from this window.
[See image.](#view-shared-config-window)
- Click **Cancel** to exit the window.
[]To delete a shared configuration resource:
- Go to **Workflows **> **Shared Configurations**. The **Shared Configurations** page appears.
-
Click the **Delete** icon next to the shared configuration resource. A message appears asking whether you want to delete the resource.
[See image.](#delete-icon)
- Click **Yes**. The shared configuration is deleted.
[]To edit a shared configuration resource:
- Go to **Workflows** > **Shared Configurations**. The **Shared Configurations** page appears.
-
Click the **Edit** icon next to the shared configuration resource you want to edit. The **Edit Shared Configuration** page appears.
[See image.](#edit-icon)
-
On the **Edit Shared Configuration** page, modify the name and description of the resource.
You cannot change the schema for the resource. If you want to change the schema, create a new shared configuration resource for the same location or location groups.
[See image.](#edit-shared-config-window)
- In the** Location Group Ticketing Configurations **section** **or the **Location Ticketing Configurations **section, modify the ticketing system and assignee name of the existing configurations.
-
(Optional) Click the **Add** icon to add more ticketing configurations to the shared configuration resource. To learn more, see [Add Shared Configuration Resources](#add-shared-config).
[See image.](#add-icon-edit-window)
-
(Optional) Use the **Up** and** Down** arrows to change the order of the configurations and the **Delete** icon to delete a configuration.
[See image.](#up-down-delete-icon)
- Click **Update**. The shared configuration resource is updated with new changes.
![Viewing the Add New Resource page in the Shared Configurations page for ZDX. The Add New Resource page has fields for Name, Schema, and Description and Save and Cancel buttons.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Add-New-Resource-PG.png)
[]
![Viewing the Add New Resource page with the Add icon highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Add-New-Resource-PG-Add-Icons.png)
[]
[]![Viewing shared configurations on the Shared Configurations page. The shared configurations are listed in a table with columns for Name, Description, and Action.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Shared-Configurations-PG-View-All.png)
![Viewing the Shared Configurations page with View icons highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Shared-Configurations-PG-View-Icons.png)
[]
![Viewing the View Shared Configuration window](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-View-Shared-Configuration-PG.png)
[]
![Viewing the Shared Configurations page with the Delete icon and confirmation message highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Shared-Configurations-PG-Delete-Icon.png)
[]
![Viewing the Edit Shared Configuration page in the Shared Configurations page. The Edit Shared Configuration page has fields for Name, Schema, and Description. In addition, it contains a Location Ticketing Configurations section.](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Edit-Shared-Configuration-PG.png)
[]
![Viewing the Edit Shared Configuration page with the Add icon highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Edit-Shared-Configuration-PG-Add-Icon.png)
[]
![Viewing the Edit Shared Configurations page with the Upward arrow, Downward arrow, and Delete icon highlighted](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Edit-Shared-Configuration-PG-Delete-Up-Down-Icons.png)
[]
![Viewing the Shared Configurations page with the Edit icons highlighted in the Action column](/downloads/workflow-automation/zscaler-digital-experience/workflows/managing-shared-configuration-zdx-alerts/WA-ZDX-Shared-Configurations-PG-Edit-Icons.png)
[]