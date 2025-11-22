# Configuring VDI Groups
Source: https://help.zscaler.com/cloud-branch-connector/configuring-vdi-groups
PDF: https://help.zscaler.com/pdf/com/en/1471701.pdf

This article provides information on how to configure a dynamic Virtual Desktop Infrastructure (VDI) group. To learn more, see [About VDI Groups](/cloud-branch-connector/about-vdi-groups).
To add a VDI group:
- Go to **Administration** > **VDI Device Management** > **VDI Groups**.
- Click **Add Dynamic VDI Group**.
- On the **Add Dynamic VDI Group** page:
- On the **General** tab:
- **Name**: Enter a name for the VDI group.
- **MTU**: Enter the Maximum Transmission Unit (MTU) value for the devices in the VDI group. The default value is 1,400 bytes.
-
**Description**: (Optional) Enter a description for the VDI group.
[See image.](#VDIGroupsGeneral)
- On the **Devices Criteria** tab, from the **Add Criteria** drop-down menu, select one or more options:
- **Locations**: Select one or more locations to be associated with the VDI group.
- **OS Type**: Select an operating system (OS) type for the VDI group. Only **WINDOWS_OS** is currently supported.
-
**Hostname Prefix**: Enter the hostname prefix that Zscaler Client Connector for VDI detects.
[See image.](#VDIGroupsDevicesCriteria)
-
On the **VDI Forwarding Profile** tab, from the drop-down menu, select a VDI forwarding profile that is applied to the group.
[See image.](#VDIGroupsVDIForwardingProfile)
-
On the **Review** tab, confirm that the information is correct, then click **Save**.
[See image.](#VDIGroupsReview)
[]![The General tab of the Add Dynamic VDI Group page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-vdi-groups-draft-doc-50724/ZscalerClientConnforVDIGeneral.png)
[]![The Devices Criteria tab of the Add Dynamic VDI Group page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-vdi-groups-draft-doc-50724/ZCCVDIGroupsConfigure.png)
[]![The VDI Forwarding Profile tab of the Add Dynamic VDI Group page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/configuring-vdi-groups-draft-doc-50724/ZscalerClientConnforVDIForwardingProfile.png)
[]![The Review tab of the Add Dynamic VDI Group page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/zscaler-vdi-agent-management/configuring-vdi-groups/Configuring%20VDI%20Groups%20-%20Review%20tab.png)