# Configuring Private Clouds
Source: https://help.zscaler.com/zpa/configuring-private-clouds
PDF: https://help.zscaler.com/pdf/com/en/1507146.pdf

To configure Private Clouds:
- Go to **Configuration & Control **> **Business Continuity **> **Business Continuity Management** > **Private Clouds**.
-
Click **Add**.
Private Clouds that are managed by Zscaler are read only and cannot be configured, edited, or deleted. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
The **Add Private Cloud** page appears.
- On the **Add** **Private Cloud** page:
- **Name**: Enter the name of the Private Cloud.
- **Status**: Enable or disable the Private Cloud. Disabling a Private Cloud causes all the associated Private Cloud Controllers to stop accepting connections from Zscaler Client Connector, App Connectors, and ZPA Private Service Edges.
- **Description**: Enter a description of the Private Cloud.
- **Certificate Renewal Threshold**: Specify the number of days before the certificate expires to automatically renew the enrollment certificate for Private Cloud Controllers, App Connectors, and ZPA Private Service Edges. The maximum supported value is 180 days.
- **Primary Control Channel Path**: Select **Private Cloud Controller **to allow App Connectors and ZPA Private Service Edges to use Private Cloud Controllers for control channels like configuration downloads, configuration updates, and logging during normal operations and when not in Business Continuity. Select **Public Cloud** to use App Connectors and ZPA Private Service Edges to establish a control channel to Zero Trust Exchange (ZTE) during normal operations.
- **Force Business Continuity Mode**: Forces Private Cloud Controllers, App Connectors, and ZPA Private Service Edges to use Business Continuity. This option is only available when [editing a Private Cloud](/zpa/editing-private-clouds).
- **Private Cloud Controller Groups**: Select the Private Cloud Controller groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available Private Cloud Controller groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **App Connector Groups**: Select the App Connector groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available App Connector groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Private Service Edge Groups**: Select the ZPA Private Service Edge groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available ZPA Private Service Edge groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Log Receivers**: Select the log receivers to associate with the Private Cloud. You can click **Select All Displayed **to select all available log receivers that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
[See image.](#addprivatecloudpage)
- Click **Save**.
[]![Configuring a Private Cloud within the Add Private Cloud Page](/downloads/zpa/business-continuity-management/private-clouds/configuring-private-clouds/zpa-add-private-cloud_0.png)