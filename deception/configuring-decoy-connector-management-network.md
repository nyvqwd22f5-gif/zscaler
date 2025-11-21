# Configuring a Decoy Connector Management Network
Source: https://help.zscaler.com/deception/configuring-decoy-connector-management-network
PDF: https://help.zscaler.com/pdf/com/en/1531259.pdf

After you configure a Decoy Connector on any supported hypervisor, you need to configure its management network.
To configure the management network:
- Start the Decoy Connector on your hypervisor.
- Open the VM console.
-
After you are redirected to the Zscaler Deception Recovery Console, enter the username and password. The default username and password is `recovery`.
After you connect a Decoy Connector to the Zscaler Deception Admin Portal, its recovery password is randomized. You can [obtain the new recovery password credentials](/deception/obtaining-decoy-connector-recovery-and-diagnostics-credentials) from the Deception Admin Portal. The username is always `recovery`.
-
In the recovery console main menu, enter `2` to configure the management network for the Decoy Connector.
[See image.](#config-network)
- Enter the IP address.
- Enter the subnet mask.
- Enter the default router address.
-
Enter the DNS IP address.
Only one DNS server is allowed.
-
Select a management interface from the list. For example, enter `em0` for VMware platforms.
[See image.](#config-app-management-interface)
- After the configuration is saved, press `Enter` to return to the recovery console's main menu.
[]![Configure Decoy Connector management network option](/downloads/deception/product-documentation/settings/topology/appliances/how-setup-appliance/zscaler-deception-config-network-opt-2.png)
[][![Configure Decoy Connector management interface](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/configuring-decoy-connector-management-network/zscaler-deception-config-app-network-ip_360.png)
]