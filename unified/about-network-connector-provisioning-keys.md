# About Network Connector Provisioning Keys
Source: https://help.zscaler.com/zpa/about-network-connector-provisioning-keys
PDF: https://help.zscaler.com/pdf/com/en/1529077.pdf

A provisioning key is a text string that is generated when you add a new [Network Connector](/zpa/about-network-connectors). When deploying a Network Connector, you are prompted to enter this key. The provisioning key functions like an ID for the Network Connector, enabling the ZPA cloud to verify the Network Connector's authenticity and complete the deployment process. Furthermore, each key is associated with a specific [Network Connector group](/zpa/about-network-connector-groups). The key allows the ZPA cloud to identify the Network Connector group that a Network Connector is associated with.
Provisioning keys should be treated as secrets and properly protected because they can create a resource for a tenant. The provisioning key must also be secured and not transmitted or stored in clear text.
Network Connector provisioning keys provide the following benefits and enable you to:
- Identify Network Connectors to a VPN Service Edge.
- Select the signing certificate used to enroll Network Connector certificates.
The following is a Network Connector provisioning key example:
1|api.mytest.com|68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2 A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0 AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdb orq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpS ztJ/68F0AOEgpcG8McLmwdborq2m6v2A5oNEpSztJ==
About the Network Connector Provisioning Keys Page
On the Network Connector Provisioning Keys page (VPN (for Legacy Apps) > Network Connectors > Network Connector Provisioning Keys), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Network Connector Provisioning Keys page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Expand the rows in the table to see more information about each Network Connector provisioning key.
- View a list of all Network Connector provisioning keys that are configured for your organization. For each Network Connector provisioning key, you can see:
- **Name**: The name of the key. When expanded, you can see the Signing Certificate (enrollment certificate) for the provisioning key. Click **Root** to edit the certificate.
- **Network Connector Group**: The Network Connector group associated with the key.
-
**Provisioning Key**: The key needed to deploy a Network Connector.
This entry is blank if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Network Connectors](/zpa/configuring-network-connectors).
-
Copy the provisioning key to your clipboard.
This icon isn't available if you disabled the **View or Export Provisioning Key After Creation** option when [configuring Network Connectors](/zpa/configuring-network-connectors). If the provisioning key doesn't appear, and a backup of the provisioning key isn't securely stored in an external credential vault, a new key must be generated. A new provisioning key can be created and attached to the same Network Connector.
- [Edit a configured Network Connector provisioning key](/zpa/editing-network-connector-provisioning-keys).
- Delete a Network Connector provisioning key.
- Display more rows or a different page of the table.
- Go to the [Network Connectors](/zpa/about-vpn-connectors) page to add Network Connectors or manage existing Network Connectors.
- Go to the [Network Connector Groups](/zpa/about-vpn-connector-groups) page to add Network Connector groups or manage existing Network Connector groups.
![Network Connector Provisioning Keys page in the ZPA Admin Portal](/downloads/zpa/vpn-legacy-apps/network-connector-management/network-connector-provisioning-keys/about-network-connector-provisioning-keys/network-connector-prov-keys-page-w-steps_0.png)