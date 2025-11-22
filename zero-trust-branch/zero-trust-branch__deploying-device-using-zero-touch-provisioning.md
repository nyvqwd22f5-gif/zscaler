# Deploying a Device Using Zero Touch Provisioning
Source: https://help.zscaler.com/zero-trust-branch/deploying-device-using-zero-touch-provisioning
PDF: https://help.zscaler.com/pdf/com/en/1529033.pdf

You can quickly deploy a device to Zero Trust Branch by adding a site with Zero Touch Provisioning (ZTP):
-
Follow all the steps in [Adding a Site](/zero-trust-branch/adding-site).
Refer to the following table to determine which template to use for your device:
| Device | Template (High Availability) | Template (Standalone) |
| ------ | ---------------------------- | --------------------- |
| ZT800 | `zt800-ha-default` | `zt800-standalone-default` |
| ZT600 | `zt600-ha-default` | `zt600-standalone-default` |
| ZT400 | `zt400-ha-default` | `zt400-standalone-default` |
You can clone and edit the template to meet your deployment configuration. To learn more, see [Managing Templates](/zero-trust-branch/managing-templates).
- Ensure that **Provision Using ZTP** is enabled.
- In the **DHCP Service** field, if not set by the template, select **DHCP S****erver** for a DHCP server; for a relay to a server, select **r****elay**.
- Verify that all other site parameters are set correctly for the device you are deploying.