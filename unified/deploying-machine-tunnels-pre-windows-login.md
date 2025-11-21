# Deploying Machine Tunnels for Pre-Windows Login
Source: https://help.zscaler.com/zpa/deploying-machine-tunnels-pre-windows-login
PDF: https://help.zscaler.com/pdf/com/en/1484906.pdf

A machine tunnel allows a user's Windows device to establish a connection to a private service before the user is logged in to the Zscaler Client Connector. To use a machine tunnel, you need to [configure Machine Groups and Machine Provisioning Keys](/zpa/configuring-machine-provisioning-keys) in the ZPA Admin Portal and add keys to the Zscaler Client Connector profile [rules for Windows](/z-app/configuring-zscaler-app-profiles#windows). To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels) and [About Machine Groups](/zpa/about-machine-groups).
To deploy Machine Tunnels for Pre-Windows Login:
- Create the [Machine Provisioning Key and Machine Group](/zpa/configuring-machine-provisioning-keys) within the ZPA Admin Portal.
- In the Zscaler Client Connector Portal, add the Machine Provisioning Key (Machine Token) to the Zscaler Client Connector profile rule. To learn more, see [Configuring Zscaler Client Connector Profiles](/z-app/configuring-zscaler-app-profiles#windows).
- In the Zscaler Client Connector, click **More** > **Update Policy**. This allows the Zscaler Client Connector to enroll in the Machine Group via the Zscaler Client Connector profile rule created in the previous step.
[See image.](#See)
There are two methods to verify successful Machine Tunnel deployment:
- Client-side validation
After deploying the Machine Group, restart, logoff, or lock the computer to return to the Windows Login screen. If the Machine Tunnel deployment was successful, you will see a **Zscaler Diagnostics** tab.
[See image.](#See2)
From this tab, the user has access to several troubleshooting options. Click **Get Status** to verify the tunnel status.
- Cloud-side validation
- In the Zscaler Client Connector Portal, click **Enrolled Devices**.
- Under the **Devices** left-navigation pane, select **Machine Tunnel**. Here you can view successfully enrolled Machine Tunnels. To learn more, see [About Enrolled Devices](/z-app/about-enrolled-devices).
[See image.](#See3)
- In the ZPA Admin Portal, go to **Dashboard **> **Users**. Active Machine Tunnel devices are shown on the Current Connected Users dashboard.
[See image.](#See4)
[]![Enrolling in the Machine Group via the Zscaler Client Connector](/downloads/zpa-machine-pwl-enrollment-clientConnector.png)
[]![Verifying Machine Tunnel Enrollment via Windows login](/downloads/zpa-machine-pwl-verification-client.png)
[]![View your enrolled devices in the Zscaler Client Connector Portal](/downloads/zpa-machine-pwl-verification-cloud2.png)
[]![View the current connected users in the Users Dashboard](/downloads/zpa/authentication/machine-authentication/deploying-machine-tunnels-pre-windows-login/Updated%20last%20screenshot_0.png)