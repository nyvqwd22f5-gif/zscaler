# Deploying Machine Tunnels for Pre-Windows Login
Source: https://help.zscaler.com/unified/deploying-machine-tunnels-pre-windows-login
PDF: https://help.zscaler.com/pdf/com/en/1491406.pdf

A machine tunnel allows a user's Windows device to establish a connection to a private service before the user is logged in to the Zscaler Client Connector. To use a machine tunnel, you need to [configure Machine Groups and Machine Provisioning Keys](/unified/configuring-machine-provisioning-keys) in the Admin Portal and add keys to the Zscaler Client Connector profile [rules for Windows](/unified/configuring-zscaler-client-connector-app-profiles#windows). To learn more, see [About Machine Tunnels](/unified/about-machine-tunnels) and [About Machine Groups](/unified/about-machine-groups).
To deploy Machine Tunnels for Pre-Windows Login:
- Create the [Machine Provisioning Key and Machine Group](/unified/configuring-machine-provisioning-keys) within the Admin Portal.
- In the Admin Portal, add the Machine Provisioning Key (Machine Token) to the Zscaler Client Connector profile rule. To learn more, see [Configuring Zscaler Client Connector Profiles](/unified/configuring-zscaler-client-connector-app-profiles#windows).
- In the Zscaler Client Connector, click **More** > **Update Policy**. This allows the Zscaler Client Connector to enroll in the Machine Group via the Zscaler Client Connector profile rule created in the previous step.
[See image.](#See)
There are two methods to verify successful Machine Tunnel deployment:
- Client-side validation
After deploying the Machine Group, restart, logoff, or lock the computer to return to the Windows Login screen. If the Machine Tunnel deployment was successful, you will see a **Zscaler Diagnostics** tab.
[See image.](#See2)
From this tab, the user has access to several troubleshooting options. Click **Get Status** to verify the tunnel status.
- Cloud-side validation
- In the Admin Portal, click **Enrolled Devices**.
- Under the **Devices** left-navigation pane, select **Machine Tunnel**. Here you can view successfully enrolled Machine Tunnels. To learn more, see [About Enrolled Devices](/unified/about-enrolled-devices).
[]![Enrolling in the Machine Group via the Zscaler Client Connector](/downloads/zpa-machine-pwl-enrollment-clientConnector.png)
[]![Verifying Machine Tunnel Enrollment via Windows login](/downloads/zpa-machine-pwl-verification-client.png)