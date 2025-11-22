# Editing Cloud Connectors
Source: https://help.zscaler.com/unified/editing-cloud-connectors
PDF: https://help.zscaler.com/pdf/com/en/1518891.pdf

Modifying Cloud Connectors is one of the tasks you can complete after deployment.
To edit a Cloud Connector:
- Go to **Infrastructure **>** Connectors** > **Cloud** > **Cloud Connector Groups**.
- From the [Cloud Connector Groups](/unified/about-cloud-connector-groups-0) page, locate the group or the individual connector you want to modify and select the **Edit** icon.
[See image.](#seeimage1)
- In the **Edit Connectors** window:
- **Operational Status**: Select to **Enable** or **Disable** the operational status of the individual Cloud Connector or all Cloud Connectors belonging to a Cloud Connector Group. If enabled, the operational status of the Cloud Connector changes to **Active**. If disabled, the operational status of the Cloud Connector changes to **Disabled**.
- **Software Upgrade Schedule**: Designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/unified/managing-cloud-branch-connector-upgrades).
- **ZIA Tunnel Mode**: Select from **DTLS **or **Unencrypted** for the encryption type to be used when forwarding traffic to Internet & SaaS.
- **Group Information**: View the following location information:
- **Name**: The name of the Cloud Connector group.
- **Location Name**: The location where your Cloud Connector was deployed.
- **No. of Connectors**: The number of Cloud Connectors belonging to the Cloud Connector Group.
- **Connector Names**: The names of the Cloud Connectors.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).