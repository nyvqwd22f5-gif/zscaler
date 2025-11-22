# Editing Cloud Connectors
Source: https://help.zscaler.com/cloud-branch-connector/editing-cloud-connectors
PDF: https://help.zscaler.com/pdf/com/en/1420856.pdf

Modifying Zscaler Cloud Connectors is one of the tasks you can complete after deployment.
To edit a Cloud Connector:
- Go to **Administration **>** Cloud Connector Groups**.
-
On the [Cloud Connector Groups](/cloud-branch-connector/about-cloud-connector-groups) page, locate the group or the individual connector you want to modify and click the **Edit** icon.
[See image.](#seeimage1)
- [Cloud Connector group](#cloudconnectorgroup)
- [Individual Cloud Connector](#individualcloudconnector)
[]
- In the **Edit Cloud Connector Group** window, view or configure the following:
- In the **Upgrade Schedule** section, under **Software Upgrade Schedule**, designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
- In the **Tunnel Information** section, configure the following:
- **ZIA Tunnel Mode**: Select **Unencrypted UDP**, **DTLS**, or **TLS** for the encryption type to be used when forwarding traffic to Zscaler Internet Access (ZIA). By default, **Unencrypted UDP** is selected.
- **Fallback to TLS**: You can only enable this feature if **Unencrypted UDP** or **DTLS** is selected as the **ZIA Tunnel Mode**. Select **Enable** to have the tunnel type automatically switch to **TLS** if the tunnel becomes unhealthy. Select **Disable** to deactivate this feature. This feature is enabled by default.
- In the **Group Information** section, view the following:
- **Name**: The name of the Cloud Connector group.
- **Location Name**: The [location](/cloud-branch-connector/about-locations) from where your Cloud Connector was deployed.
- **No. of Connectors**: The number of Cloud Connectors belonging to the Cloud Connector group.
-
**Connector Names**: The names of the Cloud Connectors.
[See image.](#seeimage2)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
- In the **Edit Cloud Connector** window:
- In the **Operational Status** section, configure or view the following:
- **Status**: Select **Enable** or **Disable** to activate or disable the Cloud Connector.
-
**Last Heartbeat Received On**: View the date and time when the Zscaler service last received a heartbeat, or keepalive communication, from the Cloud Connector.
[See image.](#operationalstatus)
- In the **Upgrade Schedule** section, configure or view the following:
- **Software Upgrade Schedule**: Designate a day and time for periodic software updates. To learn more, see [Managing Cloud & Branch Connector Upgrades](/cloud-branch-connector/managing-cloud-branch-connector-upgrades).
- **Last Upgrade On**: The date and time when the software was last upgraded.
- **Current Version**: The current version of the software.
-
**Scheduled Version**: The version of the software to update to.
[See image.](#upgradeschedule)
-
In the **Tunnel Information** section, view the following:
- **ZIA Tunnel Mode**: View the encryption type to be used when forwarding traffic to ZIA. By default, **Unencrypted UDP** is selected.
- **Fallback to TLS**: View the status of TLS fallback as **Enable** or **Disable**. If enabled, the tunnel type automatically switches to TLS if the tunnel becomes unhealthy. If disabled, this feature is deactivated. By default, TLS fallback is enabled.
[See image.](#tunnelinfo)
- In the **Location Information** section, view the following:
- **Name**: The name of the Cloud Connector.
- **Location Name**: The [location](/cloud-branch-connector/about-locations) where your Cloud Connector was deployed from.
- **Configuration Template Name**: The name of the Cloud Connector provisioning template.
-
**Connector VM Size**: The size of the Cloud Connector virtual machine (VM).
[See image.](#locationinfo)
- In the **Connector Information** section, view the following:
- **Management Outgoing Gateway IP Address**: The default gateway IP address.
- **Management IP Address**: The IP address of the Cloud Connector.
-
**Management DNS Server 1**: The IP address of the primary DNS server.
[See image.](#connectorinfo)
- In the **Forwarding Information** section, view the following:
- **Internal Gateway IP Address**: The gateway IP address.
-
**DNS Server 1**: The IP address of the primary DNS server.
[See image.](#forwardinginfo)
- In the **Service Information** section, view the following:
- **Service IP**: The service IP address.
-
**Virtual IP Address**: The virtual IP address.
[See image.](#serviceinfo)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![The Edit icon demonstrated on the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/editingcloudconnectors.png)
[]
![The Edit Cloud Connector Group window when editing Cloud Connector group settings on the Cloud Connector Groups page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/EditCloudConnectorGroup-TLS.png)
[]
![The Operational Status section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/operationalstatus.png)
[]
![The Upgrade Schedule section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/upgradeschedule.png)
[]
![The Tunnel Information section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/EditCloudConnector-TLS.png)
[]
![The Location Information section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/locationinformation.png)
[]
![The Connector Information section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/connectorinformation.png)
[]
![The Forwarding Information section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/forwardinginformation.png)
[]
![The Service Information section in the Edit Cloud Connectors window of the Cloud Connector Groups page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-group-management/serviceinformation.png)