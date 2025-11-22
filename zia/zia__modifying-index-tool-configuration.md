# Modifying an Index Tool Configuration
Source: https://help.zscaler.com/zia/modifying-index-tool-configuration
PDF: https://help.zscaler.com/pdf/com/en/1400666.pdf

To edit or delete an Index Tool configuration:
- Go to **Administration **>** Index Tool**.
-
Locate the Index Tool configuration in the table and click **Edit**.
The **Edit Index Tool Configuration** window appears.
-
In the **Edit Index Tool Configuration **window, you cannot modify the **VM Name**. However, you can do the following:
- **Status**:** **Select **Enabled** or **Disabled**.
- **SSL Certificate**: **Download** the certificate or select **Regenerate SSL Certificate **to replace the old certificate. If you regenerate the certificate, make sure that you update the Index Tool virtual machine with the new file. To learn more, see [Configuring the Index Tool with VMWare](/zia/configuring-index-tool).
- **Enable Single Sign-On**:** **Select **Enabled **to configure single sign-on (SSO) for the Index Tool configuration. To learn more, see [Configuring Single Sign-On for the Index Tool](/zia/configuring-single-sign-index-tool).
- **Delete**: Removes the configuration.
[See image.](#edit-index-tool)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Editing an Index Tool Configuration within the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/modifying-index-tool-configuration/ZIA-edit-index-tool-config.png)