# About ZPA App Connectors in Deception
Source: https://help.zscaler.com/deception/about-zpa-app-connector-deception
PDF: https://help.zscaler.com/pdf/com/en/1531569.pdf

ZPA App Connectors are hosted by Zscaler and are used to connect to your Zero Trust Exchange (ZTE) environment. In the Zscaler Deception Admin Portal, App Connectors are configured when creating [Zero Trust Network decoys](/deception/creating-zero-trust-network-decoy). To learn more, see [About App Connectors](/zpa/about-connectors).
App Connectors provide the following benefits and enable you to:
- Create a secure interface between the Decoy Connector and the Zero Trust Exchange (ZTE) via Zscaler Private Access (ZPA).
- Deploy Zero Trust Network decoys in the Zero Trust Exchange (ZTE) environment.
You can view the details of the App Connector on the ZPA App Connectors page (Settings > Topology > ZPA App Connectors). On this page, you can do the following:
- View a list of all deployed App Connectors. For each deployed App Connector, you can see:
- **Name**: The name of the App Connector. The following icons indicate the connection status of the App Connector with the Deception Admin Portal:
- ![zscaler-deception-zpa-app-con-green-status-icon.png](/downloads/deception/settings/topology/zpa-app-connectors/viewing-zpa-app-connector-dashboard-deception/zscaler-deception-zpa-app-con-green-status-icon.png)
: Active or connected to the Deception Admin Portal.
- ![zscaler-deception-red-zp-app-con-status-icon.png](/downloads/deception/settings/topology/zpa-app-connectors/viewing-zpa-app-connector-dashboard-deception/zscaler-deception-red-zp-app-con-status-icon.png)
: Inactive or not connected to the Deception Admin Portal.
- ![zscaler-deception-zpa-app-con-orange-status-icon.png](/downloads/deception/settings/topology/zpa-app-connectors/viewing-zpa-app-connector-dashboard-deception/zscaler-deception-zpa-app-con-orange-status-icon.png)
: Not connected to an aggregator.
- ![zscaler-deception-zpa-app-con-yellow-status-icon.png](/downloads/deception/settings/topology/zpa-app-connectors/viewing-zpa-app-connector-dashboard-deception/zscaler-deception-zpa-app-con-yellow-status-icon.png)
: Update in progress or update failed.
- **Version**: The version of the Decoy Connector.
- **ZPA Manager Version**: The version of the current App Connector Manager software. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software).
- **Last Connected Time**: The time when the Decoy Connector was last connected to the Deception Admin Portal.
- **ZPA App Connector Last Connected Time**: The time when the App Connector was last connected to the ZPA cloud.
- [Reboot](/deception/rebooting-zpa-app-connector) an App Connector.
- [View update logs](/deception/viewing-zpa-app-connector-update-logs) and [download the debug logs](/deception/downloading-zpa-app-connector-debug-logs) for an App Connector.
[]![About ZPA App Connector in Deception](/downloads/deception/settings/topology/zpa-app-connectors/about-zpa-app-connector-deception/zscaler-deception-about-zpa-app-con-1.png)