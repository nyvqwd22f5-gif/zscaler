# Managing a Zero Trust SD-WAN Device
Source: https://help.zscaler.com/unified/managing-branch-connector-device
PDF: https://help.zscaler.com/pdf/com/en/1519246.pdf

You can view and manage the following items using the tabs on the details page for a Zero Trust SD-WAN device. To open the details page, click the device name on the Appliances page (Infrastructure > Connectors > Edge > Appliances).
In Experience Center, Zero Trust SD-WAN Devices might be called Branch Connectors, appliances, or Edge Connectors.
- [Appliance Details](#applianceDetails)
- [Network](#Network)
- [Interfaces](#Interfaces)
- [App Connector](#appConnector)
- [Upgrade Schedule](#upgradeSchedule)
- [Troubleshooting](#Troubleshooting)
[]On the **Appliance Details** tab:
- View the device details:
- **Name**: The device name.
- **Model**: The physical device model or virtual appliance hypervisor host.
- **Serial Number**: The serial number of the physical device.
- **Status**: The status of the device.
- **Appliance Group**: The group the device belongs to.
- **Next Upgrade**: The date and time of the next device upgrade.
- **Current Version**: The current version.
- **Next Version**: The next version.
- Edit the device:
- In the **Appliance Details** tab, click the edit icon.
- Modify the name as needed.
- (Optional) Add or modify the description.
- Click **Save**.
- Click **Delete **to delete the appliance.
[]On the **Network **tab:
- **Auto-Populate DNS Cache**: Select **Enabled **or **Disabled**.
- **ZIA Tunnel Mode**: Select **Encrypted (DTLS)** or **Unencrypted (UDP)** as the tunnel encryption mode to be used when forwarding the device's traffic to Internet & SaaS.
- **WAN Traffic Distribution Mode** (for physical devices deployed in gateway mode): Select **Balanced **to distribute traffic evenly or **Best-link** to always forward the traffic via the best-performing WAN link.
[]Interfaces are initially configured on the Branch Connector Configuration Template page. For information about the settings you can view and edit on the **Interfaces **tab, see Configuring a Branch Configuration Template.
On the **Interfaces **tab:
- View information about the interfaces:
- **Interface**: The interface name.
- **Type**: The interface type, such as MGT for the management interface.
- **IP Address**: The IP address of the interface.
- **DHCP**: Whether the interface receives its IP address via the DHCP client.
- **Details**: Details about the interface, such as whether HA is enabled and the WAN traffic distribution mode.
- **Admin Status**: The status of the interface, which is reported as **Up **or **Down**.
- **Link Status**: Whether the link is up or down.
- Search for an interface.
- Modify the table and its contents:
- Sort by interface and type.
- Filter by type.
- Show or hide sub-interfaces.
- Click the name in the **Interface **column and view interface details.
- Edit interface settings, and then click **Save**.
The fields and settings depend on the interface type (MGT, LAN, WAN), whether it is a sub-interface, and whether the device is a hypervisor host or hardware device. If it is a hardware device, the fields and settings depend on whether the device is deployed in gateway or one-arm mode. For more information, see Configuring a Branch Configuration Template.
- Delete an unused interface or a sub-interface:
- Click the icon on the right side of the row.
- Click **Delete**.
[]App Connectors are initially configured and enabled on the Branch Connector Configuration Template page.
On the **App Connector** tab you can view and edit the following properties:
- **App Connector Group**: The name of your App Connector group.
- **Deployment Status**; Your App Connector deployment status, such as **Active-Active.**
- **Provisioning Key**: Your App Connector provisioning key name.
[]By default, the upgrade window for Zero Trust SD-WAN Devices starts every Sunday at midnight, local time of the device.
On the **Upgrade Schedule** tab, you can view the following information:
- **Upgrade Schedule**: The day and local time on which the upgrade window starts.
- **Current Version**: The current version and when the device was last upgraded.
- **Next Version**: The next version and the scheduled upgrade window.
To change the upgrade window:
- Select the day and time for the upgrade window.
- Click **Save** to save the upgrade window or **Reset** to cancel your changes.
[]You can request remote assistance and allow Zscaler Support to log into your device without opening a firewall connection for inbound traffic.
On the **Troubleshooting **tab,
- View the support tunnel configuration.
- Change support tunnel settings:
- Select one of the following:
- **Enable support tunnel**: Enables the support tunnel.
- **Allow Zscaler Support to start and stop the support tunnel**. Enables the support tunnel and allows Zscaler Support to start and stop it.
- Click **Save**. To cancel your changes, click **Reset**.