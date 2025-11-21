# Managing Incident Groups
Source: https://help.zscaler.com/workflow-automation/managing-incident-groups
PDF: https://help.zscaler.com/pdf/com/en/1418041.pdf

Incident groups enable admins to group individual incidents together so that all of them can be managed together. Admins with Full or Restricted access to Workflow Automation can add incident groups, but only admins with Full access to Workflow Automation can map those incident groups. Incident groups are mapped to one or more of the incident attributes available in an incident transaction. After incident groups are configured, admins with Full access can then assign these incident groups to the various Restricted access admins that are going to be responsible for them on the Admins page in the Workflow Automation Admin Portal. To learn more, see [Managing Admin Assignments.](/zia/managing-admin-assignments)
Incident groups are also used to map the priority for incidents. To learn more, see [Managing Priorities.](/zia/managing-priorities)
On the Incident Group page in the Workflow Automation Admin Portal, admins can:
- [Add Incident Groups](#add-incident-group)
- [Add Incident Group Mappings](#add-incident-group-mapping)
- [Edit Incident Groups](#edit-incident-group)
- [View Incident Groups](#view-incident-groups)
- [View Mappings for Incident Groups](#view-mappings-incident-group)
- [View Incident Group Details](#view-incident-group-details)
[]To add an incident group:
- Go to **Incident Group** > **Incident Group**. The **Incident Group** page appears, listing all the incident groups for your organization.
- On the **Incident Group** page, click **Add More**.
- On the **Add Incident Group** page:
- **Type**: Select an existing type from the drop-down menu or to enter a new type for the incident group, perform these steps:
- Select the **Type** drop-down menu.
- Enter a new type at the bottom of the drop-down menu and click **Add Type**. The type is added to the drop-down menu and is available for selection.
[See image.](#add-incident-group-type)
- Select the new type in the drop-down menu.
- **Name**: Enter the name for the incident group.
- (Optional) **Description**: Enter a description for the incident group.
- (Optional) Select the **Save and create mapping** checkbox if you want to proceed to map the incident group on the **Incident Group Mapping** page after the incident group is added. To learn more, see [Managing Incident Group Mappings](/zia/managing-incident-group-mappings#add-incidentgroup-mapping).
[See image.](#Incident-Group-Page-Add)
- Click **Save**.
[]To add an incident group mapping:
- Go to **Incident Group** > **Incident Group**.** **The **Incident Group** page appears, listing all the incident groups for your organization.
- On the **Incident Group** page, click the **Add New Incident Group Mapping** icon for an incident group.
[See image.](#Add-New-Incident-Group-Mapping-Icon)
The **Incident Group Mapping** page appears, displaying an expanded row for the incident group.
[See image.](#incident-group-page-add-mapping)
- On the **Incident Group Mapping** page, add the incident group mapping for the incident group. To learn more, see [Managing Incident Group Mappings](/zia/managing-incident-group-mappings#add-incidentgroup-mapping).
Only admins with Full access to Workflow Automation can map an incident group.
[]To edit an incident group:
- Go to **Incident Group** > **Incident Group**. The **Incident Group** page appears, listing all the incident groups for your organization.
- (Optional) On the **Incident Group** page, use the **Search** field to locate the incident group you want to edit.
- Click the **Edit** icon for an incident group.
[See image.](#Incident-Group-Page-Edit)
- On the **Edit Incident Group** page, change any of the fields.
- Click **Save**.
To delete the incident group, click **Delete **on the **Edit Incident Group** page.
If the incident group is mapped, the incident group mappings must be deleted first before you can delete the incident group. To learn more, see [Managing Incident Group Mappings](/zia/managing-incident-group-mappings#delete-incidentgroup-mapping).
[]To view incident groups:
Go to **Incident Group** > **Incident Group**. The **Incident Group** page appears, listing all the incident groups for your organization. For incident groups, you can view the following information:
- **Incident Group Type**: The type of incident group.
- **Incident Group Name**: The name of the incident group.
[See image.](#Incident-Group-Page-Viewing-All)
[]To view the mapping for an incident group:
- Go to **Incident Group** > **Incident Group**.** **The **Incident Group** page appears, listing all the incident groups for your organization.
- On the **Incident Group** page, click the **Show Incident Group Mapping** icon for an incident group.
[See image.](#Incident-Group-Page-Showing-Mapping)
The **Incident Group Mapping** page appears, displaying the mapping for the incident group.
[]To view incident group details:
- Go to **Incident Group** > **Incident Group**.** **The **Incident Group** page appears, listing all the incident groups for your organization.
- On the **Incident Group** page, click anywhere in an incident group row. The **View Incident Group** page appears, displaying the details for the incident group.
[See image.](#Incident-Group-Page-View-Incident-Group-Details)
[]![Add Incident Group Page - Add a new type](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Add-Incident-Group-PG-Add-Type.png)
[]![Incident Group Page - Adding an Incident Group](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Add-Incident-Group-PG.png)
[]![Incident Group Page - Add New Incident Group Mapping Icon](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Incident-Group-PG-Add-Incident-Group-Mapping-Icons.png)
[]![Incident Group Page - Mapping an Incident Group](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Incident-Group-PG-Add-Mapping.png)
[]![Incident Group Page - Editing an Incident Group](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Incident-Group-PG-Edit.png)
[]![Incident Group Page - Viewing all Incident Groups](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Incident-Group-Page-View-All.png)
[]![Incident Group Page - Accessing Mapping](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-Incident-Group-PG-View-Mapping-Icon.png)
[]![View Incident Group Window](/downloads/workflow-automation/incident-group/managing-incident-groups/WA-View-Incident-Group-PG_0.png)