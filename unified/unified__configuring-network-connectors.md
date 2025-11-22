# Configuring Network Connectors
Source: https://help.zscaler.com/unified/configuring-network-connectors
PDF: https://help.zscaler.com/pdf/com/en/1532371.pdf

Within the Admin Portal, you can create [Network Connectors](/unified/about-vpn-connectors), [Network Connector groups](/unified/about-vpn-connector-groups), and [Network Connector provisioning keys](/unified/about-vpn-connector-provisioning-keys). For a complete list of ranges and limits, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To add a new Network Connector:
- Go to **Infrastructure **>** Private Access **>** Component **>** VPN (For Legacy Apps) **>** Network Connectors**.
- Click **Add**.
The **Add Network Connector** page appears.
- Complete the following steps:
- [Signing Certificate](#sign)
- [Network Connector Group](#VPNCG)
- [Create Provisioning Key](#Key)
- [Review](#Review)
- [Review Documentation](#Reviewdoc)
- []For the **Signing Certificate** step, from the drop-down menu, select the certificate that is used to sign certificates it issues to the Network Connector. If you need to generate a new enrollment certificate, see [Generating Zscaler-Issued Enrollment (CA) Certificates](/unified/generating-zscaler-issued-enrollment-ca-certificates).
[See image.](#signimage)
- Click **Next**.
To learn more about certificates, see [Understanding Certificates](/unified/understanding-certificates).
[]![Add Network Connector Window within Admin Portal](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%201.png)
[]For the **Network Connector Group** step, choose one of the following options:
[See image.](#selectadd)
- [Select Network Connector Group](#select)
- [Add Network Connector Group](#add)
[]![Add Network Connector window with Network Connector Group tab selected](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%202.png)
- []Select an existing Network Connector group from the drop-down menu. You can search for a specific group, or click **Clear Selection** to remove any selections. Network Connector groups can be associated with multiple provisioning keys, so you can assign this Network Connector to an existing group that's already associated to a provisioning key.
- Click **Next**.
- []Click **Add Network Connector Group**:
- **Name**: Enter a name for the group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Make sure **Enabled** is selected.
- **Description**: (Optional) Enter a description for the group.
- **Persist Local Version Profile**: Enable if the Network Connector Group should persist the local version profile. By default, **Disabled** is selected.
- **Version Profile**: Displays the current version profile. The default value is set to Default. To learn more, see [Configuring a Network Version Profile](/unified/configuring-network-version-profile).
- **Network Connector Software Update Schedule**: Schedule the periodic Network Connector software update for the group by selecting the day of the week and start time. You can search for a specific day of the week and start time, or click **Clear Selection** to remove any selections.
- **Network Connector Location**: Enter the location where the Network Connectors in the group are set up. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, and **Location Address** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
[See image.](#addvpg)
- Click **Next**.
[]![Add Network Connector window in Add Network Connector Group tab](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%203.png)
[]For the **Create Provisioning Key** step:
- **View or Export Provisioning Key After Creation**: Select this option if you want to view, copy, or download the provisioning key after creation. This option is enabled by default. If disabled, you cannot enable this option at a later time.
- **Name**: Enter a name for the provisioning key. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
[See image.](#pkey)
- Click **Next**.
[]![Add Network Connector Window with Create a Provisioning Key step](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%204.png)
- []For the** Review** step, review your configuration settings.
[See image.](#review)
- Click **Save**.
[]![Add Network Connector window in Review tab](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%205.png)
- []For the **Review Documentation** step:
- **Copy Provisioning Key**: Copy the Network Connector provisioning key. You need to enter this key when you deploy the Network Connector to a platform. You can click the **Copy** icon to copy the key to your clipboard.
- **Review Documentation**: Choose the platform you want to deploy your Network Connector on, and follow the instructions that appear.
[See image.](#reviewdoc)
- Click **Done**.
[]![Add Network Connector window in Review Documentation tab](/downloads/zpa/configuring-vpn-connectors/Config%20Net%20Conn%206.png)