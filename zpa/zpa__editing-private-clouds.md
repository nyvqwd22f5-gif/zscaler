# Editing Private Clouds
Source: https://help.zscaler.com/zpa/editing-private-clouds
PDF: https://help.zscaler.com/pdf/com/en/1507161.pdf

To edit a Private Cloud:
- Go to **Configuration & Control** > **Business Continuity** > **Business Continuity Management **> **Private Clouds**.
-
In the table, locate the Private Cloud you want to modify and click the **Edit **icon.
Private Clouds that are managed by Zscaler are read only and cannot be edited. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
The **Edit Private Cloud** page appears.
- On the **Edit Private Cloud** page, you can modify any field.
- **Name**: Modify the name of the Private Cloud.
- **Status**: Enable or disable the Private Cloud. Disabling a Private Cloud causes all the associated Private Cloud Controllers to stop accepting connections from Zscaler Client Connector, App Connectors, and ZPA Private Service Edges.
- **Description**: Enter a description of the Private Cloud.
- **Certificate Renewal Threshold**: Specify the number of days before the certificate expires to automatically renew the enrollment certificate for Private Cloud Controllers, App Connectors, and ZPA Private Service Edges. The maximum supported value is 180 days.
- **Primary Control Channel Path**: Select **Private Cloud Controller **to allow App Connectors and ZPA Private Service Edges to use Private Cloud Controllers for control channels like configuration downloads, configuration updates, and logging during normal operations and when not in Business Continuity. Select **Public Cloud** to use App Connectors and ZPA Private Service Edges to establish a control channel to Zero Trust Exchange (ZTE) during normal operations.
-
**Force Business Continuity Mode**: Select **Enabled** to force Private Cloud Controllers, App Connectors, and ZPA Private Service Edges to use Business Continuity.
When enabled, you can configure a **Public Cloud Reconnect Interval** (default 15 mins, range is 15 mins to 24 hours). The App Connectors, ZPA Private Service Edges, and Private Cloud Controllers check back with the cloud based on the configured reconnect interval to see if **Force Business Continuity Mode** is disabled or enabled. If disabled, the App Connectors, ZPA Private Service Edges, and Private Cloud Controllers exit Business Continuity and connect back to the ZPA Cloud. If enabled, the App Connectors, ZPA Private Service Edges, and Private Cloud Controllers remain in Business Continuity.
- **Private Cloud Controller Groups**: Select the Private Cloud Controller groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available Private Cloud Controller groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **App Connector Groups**: Select the App Connector groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available App Connector groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Private Service Edge Groups**: Select the ZPA Private Service Edge groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available ZPA Private Service Edge groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Log Receivers**: Select the log receivers to associate with the Private Cloud. You can click **Select All Displayed **to select all available log receivers that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
![Editing a Private Cloud](/downloads/zpa/business-continuity-management/private-clouds/editing-private-clouds/zpa-edit-private-cloud_0.png)
- Click **Save**.