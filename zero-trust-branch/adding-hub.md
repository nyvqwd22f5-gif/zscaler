# Adding a Hub
Source: https://help.zscaler.com/zero-trust-branch/adding-hub
PDF: https://help.zscaler.com/pdf/com/en/1525471.pdf

In Zero Trust Branch, a hub enables site-to-site communication. To learn more, see [Configuring a Site-to-Site VPN](/zero-trust-branch/configuring-site-vpn).
Add a Hub
To add a hub:
- Go to **Deployments > Hubs**.
-
Click **Add On-Prem Hub **in the upper-right corner.
[See image.](#hubs)
- In the **Add On-Prem Hub **panel:
- To add another gateway to an existing hub:
- **Location**: Select an existing hub from the drop-down menu.
- **Gateway Name**: Enter a name for the gateway.
- **WAN Virtual IP**: Enter the floating IP address to be used.
- **WAN VRRP Group ID (1 - 255)**: Enter a number between 1 and 255 to uniquely identify the WAN router.
- **Provision using ZTP**: Disable if you do not want to provision this site using Zero Touch Provisioning (ZTP). ZTP is not supported in Zero Trust Branch version 7.7 and earlier.
- **WAN IP Address**: Enter the WAN IP address.
- **WAN Subnet Mask**: Enter the WAN subnet mask.
-
**Default Gateway IP Address**: Enter the gateway IP address.
[See image.](#add-existing-hub)
- To add a new hub location:
- **Location**: Select **Add New Location**.
- **Name**: Enter a name for the location.
- **Gateway Name**: Enter a name for the gateway.
- **User Reachable IP**: Enter the IP address for the gateway.
- **Provision Using ZTP**: Disable if you do not want to provision this site using ZTP. ZTP is not supported in Zero Trust Branch version 7.7 and earlier.
- **WAN IP Address**: Enter the WAN IP address.
- **WAN Subnet Mask**: Enter the WAN subnet mask.
-
**Default Gateway IP Address**: Enter the gateway IP address.
[See image.](#add-new-hub)
- Click **Add **to save the hub.
[]
![Hubs page](/downloads/device-segmentation/administration/deployment-configuration/adding-hub/hubs.png)
[]
![Add On-Prem Hub panel for an existing hub](/downloads/device-segmentation/administration/deployment-configuration/adding-hub/add-hub-existing.png)
[]
![Add On-Prem Hub panel for a new hub](/downloads/device-segmentation/administration/deployment-configuration/adding-hub/add-hub-new.png)