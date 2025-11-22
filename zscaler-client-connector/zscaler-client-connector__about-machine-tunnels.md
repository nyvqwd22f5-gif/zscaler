# About Machine Tunnels
Source: https://help.zscaler.com/zscaler-client-connector/about-machine-tunnels
PDF: https://help.zscaler.com/pdf/com/en/1370131.pdf

A machine tunnel allows a user's Windows or macOS device to establish a connection to a service before the user is logged in to Zscaler Client Connector. Zscaler Client Connector doesn't support machine tunnels for iOS, Linux, Android, and Android on ChromeOS.
- Admins can enable **ZPA Machine Authentication** in [App Profiles](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles) to require users to authenticate against their IdP before the machine tunnel starts.
- WebView2 authentication is not supported for Machine Tunnels.
- Contact Zscaler Support to enable this feature for Zscaler Client Connector for macOS.
To use a machine tunnel, you must [configure Machines groups and Machine Provisioning keys](/zpa/configuring-machine-provisioning-keys) in the Zscaler Private Access (ZPA) Admin Portal, add keys to Zscaler Client Connector app profile [rules for Windows](/zscaler-client-connector/configuring-zscaler-app-profiles#windows) or [macOS](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles#mac-auth), and [enable the ZPA machine tunnel for all](/zscaler-client-connector/selective-entitlement-configuring-zpa-machine-tunnel-all).
The Machine Tunnel page provides the following benefits and enables you to:
- View a list of machines and details for your organization.
- Search for a machine tunnel by hostname, filter by operating system and status, and export machine tunnel details as a CSV file.
- View details for a machine tunnel and copy the token for each machine.
- Remove machine tunnels from the Zscaler Client Connector Portal.
About the Machine Tunnel Page
On the Machine Tunnel page (Enrolled Devices > Machine Tunnel), you can do the following:
- Filter the list of enrolled devices with the following options:
- View machines for a specific operating system.
- View machines by status:
- **Active**:** **The default status. The machine tunnel is connected to ZPA before user login.
- **Inactive**: The machine tunnel is not connected to ZPA for various reasons, including the following:
- The machine tunnel was turned off by the admin and cannot establish a connection.
- The device was turned off or disconnected from the network.
- The machine tunnel failed to establish a connection because of connection issues or failed authentication.
- The machine tunnel was not enabled for the device in [Zscaler Service Entitlement](/zscaler-client-connector/about-zscaler-service-entitlement).
- **Removed: **The machine tunnel configuration was deleted or deactivated from the Zscaler Client Connector Portal.
- **Unregistered: **The machine tunnel is no longer connected to Zscaler services or policies.
- Remove selected machine tunnels from the Zscaler Client Connector Portal.
- View a list of machines for your organization. For each machine tunnel, you can see:
- **Hostname**: The name of the machine.
- **OS Type**: The operating system of the machine.
- **Device Model**: The model of the machine.
- **Zscaler Client Connector Version**: The Zscaler Client Connector version installed on the machine.
- **Status**: The status of the machine tunnel.
- Select machine tunnels for removal from the Zscaler Client Connector Portal.
- Search for a machine tunnel by **Hostname**, **Machine Tunnel Token**, **Hardware Fingerprint**, or **Zscaler Client Connector Version**.
- View the details for a machine tunnel. You can view and copy the token for each machine.
- Export the machine tunnel details as a CSV file for all items listed in the table, as determined by the filters.
![About Machine Tunnels](/downloads/client-connector/monitoring-usage/about-machine-tunnels/zscaler-client-connector-machine-tunnels.png)