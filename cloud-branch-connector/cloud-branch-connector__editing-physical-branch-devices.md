# Editing Physical Branch Devices
Source: https://help.zscaler.com/cloud-branch-connector/editing-physical-branch-devices
PDF: https://help.zscaler.com/pdf/com/en/1467031.pdf

After deployment, you can modify physical branch devices.
To edit a physical branch device:
- Go to **Administration **>** Branch Devices** > **Physical**.
- From the [Physical Branch Devices](/cloud-branch-connector/about-physical-branch-devices) page, locate the group or the individual device you want to modify and click the **Edit** icon.
- [Group](#group)
- [Individual device](#individualdevice)
[]
- In the **Edit Physical Branch Device** window:
- **Software Upgrade Schedule**: Designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
- **Auto Populate DNS Cache**: Click **Enable** to activate advance DNS resolution of the application service fully qualified domain names (FQDNs) or click **Disable** to disable this feature. By processing the response of the DNS queries, Branch Connector builds an IP cache that helps policy match even when the DNS queries do not pass through the device.
- **ZIA Tunnel Mode**: Select either **Unencrypted** or **DTLS** for the encryption type to be used when forwarding traffic to Zscaler Internet Access (ZIA).
-
**Location Information**: View the following:
- **Name**: The name of the Branch Connector group.
- **Location Name**: The [location](/cloud-branch-connector/about-locations) where your Branch Connector was deployed from.
- **No. of Connectors**: The number of Branch Connectors belonging to the Branch Connector Group.
- **Connector Names**: The names of the Branch Connectors.
[See image.](#groupwindow)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
- In the **Edit Physical Branch Device** window:
- **Status**: Select **Enable** or **Disable** to activate or disable the device.
- **Last Heartbeat Received On**: View the date and time the device last received a heartbeat.
- **Software Upgrade Schedule**: Designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades). You can view the following information:
- **Last Upgrade On**: The date and time when the software was last upgraded.
- **Current Version**: The current version of the software.
- **Scheduled Version**: The version of the software to update to.
- **Auto Populate DNS Cache**: Click **Enable** to activate advance DNS resolution of the application service FQDNs or click **Disable** to disable this feature. By processing the response of the DNS queries, Branch Connector builds an IP cache that helps policy match even when the DNS queries do not pass through the device.
- **Automatic Failover**: Select **Enable** to allow all local and internet-destined traffic to flow without policy validation or content inspection if the policy enforcement engine fails or is stopped for upgrades. When this feature is enabled, you cannot access applications protected by Zscaler Private Access (ZPA). Select **Disable** to disable this feature. This feature is disabled by default.
- **ZIA Tunnel Mode**: View the encryption type to be used when forwarding traffic to ZIA.
- **Location Information**: View the following:
- **Name**: The name of the Branch Connector group.
- **Location Name**: The [location](/cloud-branch-connector/about-locations) where your Branch Connector was deployed from.
- **Connector VM Size**: The size of the the Branch Connector VM.
- **Configuration Template Name**: The name of the branch configuration template.
- **Connector Information**: View the following:
- **Management Outgoing Gateway IP Address**: The default gateway IP address.
- **Management IP Address**: The IP address of the Branch Connector.
- **Management DNS Server 1**: The IP address of the primary DNS server.
- **Forwarding Information**: View the following:
- **Internal Gateway IP Address**: The gateway IP address.
- **DNS Server 1**: The IP address of the primary DNS server.
- **DNS Server 2**: The IP address of the secondary DNS server.
-
**Service Information**: View the following:
- **Service IP**: The service IP address.
- **Virtual IP Address**: The virtual IP address.
- **Load Balancer**: The load balancer IP address.
[See image.](#individualdevicewindow)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
![The Edit Physical Branch Device window for a group of devices in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/branch-connector-device-management/editing-physical-branch-devices/editingphysicalbranchdevice-group.png)
[]
![The Edit Physical Branch Device window for an individual device in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/branch-connector-device-management/editing-physical-branch-devices/editingphysicalbranchdevice-individualdevice.png)