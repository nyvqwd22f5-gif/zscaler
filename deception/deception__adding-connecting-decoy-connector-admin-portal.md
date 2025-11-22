# Adding and Connecting a Decoy Connector to the Zscaler Deception Admin Portal
Source: https://help.zscaler.com/deception/adding-connecting-decoy-connector-admin-portal
PDF: https://help.zscaler.com/pdf/com/en/1531269.pdf

[Watch a video on Adding and Connecting Decoy Connectors to the Zscaler Deception Admin Portal.](https://fast.wistia.net/embed/iframe/u6tiabaqnr)
You can configure and add a Decoy Connector for Network Decoys and connect it to the Zscaler Deception Admin Portal.
Zscaler Deception uses Zscaler Private Access (ZPA) App Connectors and Threat Intelligence (TI) Decoy Connectors to deploy Zero Trust Network Decoys and TI Decoys respectively in a dedicated Deception cloud. You cannot add or connect the App Connectors or TI Decoy Connectors to the Deception Admin Portal yourself. Contact Zscaler Support to manage them.
To add and connect a Decoy Connector to the Deception Admin Portal:
- [Step 1: Add a Decoy Connector](#add-decoy-connector)
- [Step 2: Obtain the Connection Code](#connection-code)
- [Step 3: Connect the Decoy Connector to the Deception Admin Portal](#connect-dc-admin-portal)
- []Go to **Settings** > **Topology** > **Decoy Connectors**.
-
Click **Add Decoy Connector**.
[See image.](#add-connector-admin-portal)
- In the** Decoy Connector Details** window, enter the **Name** of the Decoy Connector.
-
Select an **Aggregator** from the drop-down menu.
[See image.](#add-decoy-connector-details)
-
Click **Save**.
The Decoy Connector is added and displayed on the **Decoy Connectors** page. However, it appears with a red connection status icon (![Red connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-red-status-icon.png)
) indicating that the Decoy Connector is not yet connected to the Deception Admin Portal.
[See image.](#not-connected-status)
-
[]Select the Decoy Connector that you want to connect to the Deception Admin Portal, and then click **Actions **> **Connection Code**.
[See image.](#connection-code-image)
-
Copy the 8-digit connection code. You need this code when connecting the Decoy Connector to the Deception Admin Portal from the Zscaler Deception Recovery Console.
[See image.](#copy-connection-code)
The connection code is valid for up to 12 hours.
- Click **Done**.
-
[]Log in to the Zscaler Deception Recovery Console via the VM console.
The default password for the recovery user is `recovery`. After you connect a Decoy Connector to the Deception Admin Portal, its recovery password is randomized. You can obtain the new recovery password from the Deception Admin Portal. To learn more, see [Obtaining Decoy Connector Recovery and Diagnostics Credentials](/deception/obtaining-decoy-connector-recovery-and-diagnostics-credentials).
-
On the recovery console main menu, enter `4` to connect the Decoy Connector to the Deception Admin Portal.
[See image.](#connect-admin-portal-option-4)
- Enter the Deception Admin Portal's hostname (FQDN/DNS name). For example, enter `<hostname>``.illusionblack.com`.
-
Enter the 8-digit connection code that you copied in Step 2, and then press `Enter`.
[See image.](#host-name-connection-code)
- After the Decoy Connector is successfully connected, log in to the Deception Admin Portal.
- Go to **Settings** > **Topology** > **Decoy Connector**.
-
Verify the Decoy Connector connection status. If it is successful, the connection status icon turns green (![Green connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-green-status-icon.png)
).
If you make any changes to the Decoy Connector after a connection is established, perform Step 2 and Step 3 again to establish a new connection.
[See image.](#decoy-connector-connected)
[]![Add a Decoy Connector](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-add-appliance_1.png)
[]![Configure Decoy Connector details](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-add-appliance-details-1.png)
[]![Decoy Connector not connected to the Admin Portal](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-appliance-not-connected-1.png)
[]![Decoy Connector Connection Code option](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-action-connection-code-1.png)
[]![Copy Decoy Connector Connection Code](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-connection-code.png)
[]![Enter 4 to connect the Decoy Connector to the Admin Portal](/downloads/deception/product-documentation/settings/topology/appliances/connecting-appliance-zscaler-deception-admin-portal/zscaler-deception-connect-appliance-admin-portal-opt-4.png)
[]![Enter 8-digit connection code](/downloads/deception/product-documentation/settings/topology/appliances/connecting-appliance-zscaler-deception-admin-portal/zscaler-deception-connection-code-recovery-console.png)
[]![Decoy Connector connected](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/adding-connecting-decoy-connector-admin-portal/zscaler-deception-appliance-connected-1.png)