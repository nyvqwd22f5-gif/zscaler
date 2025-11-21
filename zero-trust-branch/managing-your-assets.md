# Managing Your Assets
Source: https://help.zscaler.com/zero-trust-branch/managing-your-assets
PDF: https://help.zscaler.com/pdf/com/en/1509846.pdf

The Assets section provides admins with visibility into all endpoints connected to the network along with their health status.
Zero Trust Branch leverages multiple techniques (e.g., DHCP options, HTTP User-Agent, SSL fingerprint, mDNS) to help automatically identify assets. In addition, the application integrates with third-party vendors such as Armis to further enhance the accuracy of the device discovery.
After an asset has been discovered, Zero Trust Branch tags the asset automatically. If you have integrated Zero Trust Branch with third-party vendors (e.g., Armis), then additional tags are created. You can also assign custom tags to assets. To learn more, see [Working with Tags](/zero-trust-branch/working-with-tags).
View Assets
To view assets:
- Go to **Asset Intelligence > Assets**.
- In the upper right, select how you want to view the assets.
- [View Assets by Type](#assets-type)
- [View Assets by Category](#assets-category)
- [View Assets in a List](#assets-list)
-
To view more detail on an asset, click the link for that asset in any list (either all assets or for a specific type or category).
[See image.](#asset-detail)
Edit a Device
To edit a device:
- View the assets in a list view (either all assets or for a specific type or category).
-
Select the checkbox next to one or more devices and click **Edit**.
[See image.](#edit-button-image)
-
In the edit device drawer, make the desired changes and click **Apply**. If you are editing multiple devices, your changes affect all devices.
[See image.](#edit-device-image)
The **Protection **drop-down menu allows you to select among three different solutions: **Airgap**, **Airgap-Lite**, and **Airgap+**. To learn more, see [Understanding Protection Solutions](/zero-trust-branch/understanding-protection-solutions).
Quarantine a Device
If an unfamiliar device appears on the Assets page, you can put that device into quarantine while you perform additional investigation. A device placed into quarantine can access the internet but not the private networks. Inbound connectivity is also allowed so that an admin could remotely connect to the quarantined device.
To place a device into quarantine, edit the device as described previously, and then select **Yes **from the **Quarantined** drop-down menu, and click **Apply**.
[]Select **Type **to view assets grouped by device type. Click any type to open a list of assets of that type.
[See image.](#assets-type-image)
[]Select **Category **to view assets grouped by device category. Click any category to open a list of assets of that category.
[See image.](#assets-category-image)
[]Select **List **to view assets in a detailed list.
[See image.](#assets-list-image)
[]![Viewing asset details from the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-open-asset-details.jpg)
[]![Viewing assets by type on the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-assets-by-type.jpg)
[]![Viewing assets by category on the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-asset-by-category.jpg)
[]![Viewing a list of assets on the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-assets-by-list.jpg)
[]![Editing an asset on the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-edit-an-asset.jpg)
[]![Edit device drawer on the Assets page.](/downloads/zero-trust-branch/administration/asset-management/managing-your-assets/ztb-edit-window-proprties-and-discovery-window_0.jpg)