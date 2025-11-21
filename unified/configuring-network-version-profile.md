# Configuring a Network Version Profile
Source: https://help.zscaler.com/zpa/configuring-network-version-profile
PDF: https://help.zscaler.com/pdf/com/en/1529076.pdf

A Network version profile can be used to tie a [Network Connector group](/zpa/about-vpn-connector-groups) to a specific build. Configuring a Network version profile allows you to select a desired build for that profile. The Network version profile can only be assigned to one Network Connector group. This allows you to upgrade a Network Connector group to a specific build. For a complete list of ranges and limits, see [Ranges & Limitations](/zpa/ranges-limitations).
You can configure a Network version profile using one of the following methods:
- [Using the Network Version Profile Icon On the Network Connector Groups Page](#button)
- [Editing a Network Connector Group](#edit)
Zscaler recommends the following Network version profile best practices to balance stability and new features across your Network Connector groups:
- For critical Network Connector groups that are vital to the function and operations of an organization, use the **Previous Default** version profile.
- For Network Connector groups that require the latest software updates and features, use the **New Release** version profile.
- []Go to **VPN (for Legacy Apps)** > **Network Connectors** > **Network Connector Groups**.
- Click the **Version Profile **icon.
- In the **Customer Version Profile** window:
- Select the desired profile:
- **Default**: The stable and default cloud-wide build.
- **Previous Default**: The previous stable and default cloud-wide build. Provides a rollback ability.
- **New Release**: The latest cloud-wide build release.
- **Custom**: A specialized build released only to help resolve issues. Zscaler Support provides custom version profiles to address and debug issues. Custom version profiles might not be visible in the ZPA Admin Portal. If you select **Custom**, select a version profile from the drop-down menu.
- Choose whether you want to force update the Network Connector Group version profiles enabled at the Network Connector Group level.
[See image.](#buttonimage)
- Click **Save**.
[]![Selecting a version profile for the Network Connector](/downloads/zpa/configuring-vpn-version-profile/Customer%20Version%20Profile%20window_0.png)
- []Go to **VPN (for Legacy Apps)** > **Network Connectors** > **Network Connector Groups**.
- Click the **Edit** icon for the Network Connector group you want to configure the version profile for.
- In the **Edit Network Connector Group** window:
- Select **Enabled** under **Persist Local Profile**.
- Select the desired profile:
- **Default**: The stable and default cloud-wide build.
- **Previous Default**: The previous stable and default cloud-wide build. Provides a rollback ability.
- **New Release**: The latest cloud-wide build release.
- **Custom**: A specialized build released only to help resolve issues. Zscaler Support provides custom version profiles to address and debug issues. Custom version profiles might not be visible in the ZPA Admin Portal. If you select **Custom**, select a version profile from the drop-down menu.
[See image.](#editimage)
- Click **Save**.
[]![Edit window for a Network Connector Group](/downloads/zpa/configuring-vpn-version-profile/Config%20Version%20Prof%20edit%20image.png)