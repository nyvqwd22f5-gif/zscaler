# Configuring AppZones
Source: https://help.zscaler.com/zpa/configuring-appzones
PDF: https://help.zscaler.com/pdf/com/en/1531942.pdf

AppZones in Microsegmentation are applications grouped together into "zones" based on the applications' topology and their underlying network connectivity with each other. Admins can use AppZones to segment resources that use these applications to track usage. The AppZone page gives insight into your organization's complete list of AppZone data. It allows you to monitor and analyze the data for all configured AppZones in your organization.
The following factors impact AppZone definition:
- Network Address Translation (NAT) boundary: The Presence of NAT Gateways or internal load balancers between applications. All application workloads within an AppZone are assumed to be within a common NAT boundary.
- Policy Blast radius: Applications that interact with each other and inherit common policies must be in the same AppZone.
Admins can configure, [edit](/zpa/editing-appzones), and [delete](/zpa/deleting-appzones) AppZones as needed.
To configure an AppZone:
- Go to **Microsegmentation** > **Resource Management**.
- Click the **AppZone** tab.
- Click **Add AppZone**.
The **Add AppZone** window appears.
[See image.](#Resource-Management_AppZone_Add-AppZone)
-
In the **Add AppZone** window:
- **Name**: Enter a name for the new AppZone.
- **Description**: Enter a description.
- **Region**: Select at least one region from the drop-down menu to which the AppZone applies. All resources that belong to selected regions will be members of the AppZone.
-
(Optional) Select or deselect the **Include all VPCs for selected regions** checkbox. If selected, all virtual private clouds in the region will apply to this AppZone. It is selected by default.
If you deselect it, a new drop-down menu appears to select specific VPCs from the regions. The **Include existing and all new subnets added to selected VPCs** checkbox also appears. If selected, all resources that are deployed on selected subnets are members of the AppZone.
A given resource must belong to only one AppZone. If the AppZone definition has overlapping regions either for VPCs or subnets, this results in the mapping of resources to all related AppZones and all related data is highlighted on the Resources page.
[See image.](#Add_AppZone_window)
- Click **Save**.
Your new AppZone appears in the list of AppZones.
[]![A view of the AppZone page and its actions.](/downloads/zws/resource-management_AppZone_Add-AppZone.png)
[]![The view of a new AppZone configuration.](/downloads/zws/Add-AppZone-window.png)