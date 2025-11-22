# Editing Private Clouds
Source: https://help.zscaler.com/unified/editing-private-clouds
PDF: https://help.zscaler.com/pdf/com/en/1528626.pdf

To edit a Private Cloud:
- Go to **Infrastructure** > **Private Access **> **Business Continuity **> **Private Clouds**.
-
In the table, locate the Private Cloud you want to modify and click the **Edit **icon.
Private Clouds that are managed by Zscaler are read only and cannot be edited. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/unified/understanding-zscaler-managed-business-continuity-cloud).
The **Edit Private Cloud** page appears.
- On the **Edit Private Cloud** page, you can modify any field.
- **Name**: Enter the name of the Private Cloud.
- **Status**: Enable or disable the Private Cloud. Disabling a Private Cloud causes all the associated Private Cloud Controllers to stop accepting connections from Zscaler Client Connector, App Connectors, and Private Service Edges for Private Applications.
- **Description**: Enter a description of the Private Cloud.
- **Certificate Renewal Threshold**: Specify the number of days before the certificate expires to automatically renew the enrollment certificate for Private Cloud Controllers, App Connectors, and Private Service Edges for Private Applications. The maximum supported value is 180 days.
- **Primary Control Channel Path**: Select **Private Cloud Controller** to allow App Connectors and Private Service Edges for Private Applications to use Private Cloud Controllers for control channels like configuration downloads, configuration updates, and logging during normal operations and when not in Business Continuity. Select **Public Cloud** to use App Connectors and Private Service Edges for Private Applications to establish a control channel to Zero Trust Exchange (ZTE) during normal operations.
- **Force Business Continuity Mode**: Forces Private Cloud Controllers, App Connectors, and Private Service Edges to use Business Continuity. This option is only available when editing a Private Cloud.
- **Private Cloud Controller Groups**: Select the Private Cloud Controller groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available Private Cloud Controller groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **App Connector Groups**: Select the App Connector groups to associate with the Private Cloud. You can click **Select All Displayed **to select all available App Connector groups that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Private Service Edge Groups**: Select the Private Service Edge groups for Private Applications to associate with the Private Cloud. You can click **Select All Displayed **to select all available Private Service Edge groups for Private Applications that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
- **Log Receivers**: Select the log receivers to associate with the Private Cloud. You can click **Select All Displayed **to select all available log receivers that are displayed in the drop-down menu, or click **Clear All **to clear all selections.
![Editing a Private Cloud](/downloads/zpa/business-continuity-management/private-clouds/editing-private-clouds/zpa-edit-private-cloud_0.png)
- Click **Save**.