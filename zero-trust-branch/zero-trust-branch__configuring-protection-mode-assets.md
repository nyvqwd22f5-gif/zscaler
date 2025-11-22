# Configuring Airgap-Lite Mode for Assets
Source: https://help.zscaler.com/zero-trust-branch/configuring-protection-mode-assets
PDF: https://help.zscaler.com/pdf/com/en/1532714.pdf

Zero Trust Branch offers three protection solutions for your assets that are designed to meet different requirements for varying environments. These solutions, Airgap, Airgap-Lite, and Airgap+, address varying levels of network isolation and functionality needs. Airgap-Lite mode allows devices to use the same subnet mask provided by the DHCP server.
You can configure Airgap-Lite mode for assets in the following cases:
- Full isolation is not a strict requirement.
-
If the /32 subnet mask is not supported, you choose one of the following modes based on isolation requirements:
- Airgap-Lite mode (if full isolation is not a requirement)
- Airgap Plus mode
To learn more, [Understanding Protection Solutions](/zero-trust-branch/understanding-protection-solutions).
Configuring Airgap-Lite Mode for Assets
You can configure Airgap-Lite mode using one of the following methods:
- [Device Level](#device-level-stpes)
- [VLAN Level](#vlan-level-steps)
[]The device level configuration allows you to enable Airgap-Lite mode for each device independently. Use this method when you need to configure Airgap-Lite mode for specific devices that do not require full isolation.
To configure Airgap-Lite mode:
- Go to **Asset Intelligence **> **Assets**.
-
Locate and select the device for which you want to configure **Airgap-Lite** mode, and click **Edit**.
[See image.](#edit-asset)
- In the asset details drawer, go to the **Security **section on the **Properties **tab.
-
Locate the **Protection **field and select **Airgap-Lite **from the drop-down menu.
[See image.](#protection-field)
- Click **Apply**.
-
Confirm that the **Airgapped **column for the device does not show a check mark. The absence of a check mark indicates that the device is running in **Airgap-Lite** mode.
[See image.](#airgap-lite-confirmation)
- In the device terminal, run the following command for the DHCP lease release:
-
For Windows:
`ipconfig /release`
-
For Linux:
`dhclient -r`
-
In the device terminal, run the following command to request a new IP address from the DHCP server:
-
For Windows:
`ipconfig /renew`
-
For Linux:
`dhclient`
**Airgap-Lite **mode is applied at the device level.
- Repeat these steps for each device that you want to be part of the subnet.
[]The VLAN level configuration allows you to enable Airgap-Lite mode for multiple devices simultaneously. Use this method when you need to configure Airgap-Lite mode for all devices within a VLAN.
To configure Airgap-Lite mode:
- In the Zero Trust Branch Admin Portal, go to **Deployments **> **Sites**.
-
Select the name of the site whose VLAN must be configured.
[See image.](#site-name)
- Click **VLANS**.
-
On the **VLANS **tab, locate the VLAN whose devices must be configured with **Airgap-Lite** mode, click the **Gear **icon, and select **Edit**.
[See image.](#vlan-edit)
-
In the **Edit Airgap VLAN **drawer, go to the **Network **section, and select **ON (Airgap-Lite) **from the **DHCP Service **drop-down menu.
[See image.](#dhcp-service-field)
- Click **Save**.
- For each device in the VLAN, go to the device terminal and run the following command for the DHCP lease release:
-
For Windows:
`ipconfig /release`
-
For Linux:
`dhclient -r`
-
For each device in the VLAN, go to the device terminal and run the following command to request a new IP address from the DHCP server:
-
For Windows:
`ipconfig /renew`
-
For Linux:
`dhclient`
**Airgap-Lite** mode is applied to the devices in the VLAN.
[]![Assets page showing an asset selection with the option to edit the asset](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-edit-asset.jpg)
[]![Asset details drawer showing the Protection field](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-protection-field.jpg)
[]![ztb-not-airgapped-assets.jpg](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-not-airgapped-assets.jpg)
[]![Sites page showing a site](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-sites-page.jpg)
[]![Site details page showing option to edit a VLAN](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-edit-iconasset.jpg)
[]![Edit Airgap VLAN drawer showing the DHCP Service field](/downloads/zero-trust-branch/administration/asset-management/configuring-protection-mode-assets/ztb-dhcp-service-field.jpg)