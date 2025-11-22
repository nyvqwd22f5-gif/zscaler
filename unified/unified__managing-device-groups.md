# Managing Device Groups
Source: https://help.zscaler.com/unified/managing-device-groups
PDF: https://help.zscaler.com/pdf/com/en/1505786.pdf

Users can access the Zscaler services through various devices. For example, one user can have two devices, one personal and one employer-provided. The personal device can be enrolled in Internet & SaaS, and the employer-provided device can be enrolled in Internet & SaaS and Private Applications. The ZIdentity admin can control or restrict the devices that are used to access the Zscaler services (Private Applications, Internet & SaaS, Digital Experience Monitoring, etc.) and ensure that only users on authorized devices can enroll in Zscaler services.
To manage device group restrictions:
- Go to **Administration** > **Entitlements **> **End User Entitlements**.
-
On the **Service Entitlements** page, click the required Zscaler service (e.g., Internet & SaaS).
[See image.](#zsl-se-page)
The **Internet & Saas - Service** page appears.
-
In the top-right corner, click** Manage** > **Device Group Restrictions**.
[See image.](#zsl-select-dgr)
-
In the **Manage Device Group Restrictions** window, select the toggle for **Enable** **Device Group Restrictions**.
[See image.](#zsl-enabledg)
The list of registered device IDs is displayed.
[See image.](#zsl-selectdevices)
An administrator who can access the ZIdentity service entitlements but does not have permissions to view the device groups can only see whether the **Enable Device Group Restrictions** option is enabled or not, but cannot change the setting.
- Select the devices that must be allowed to access the Zscaler service.
-
Click **Save**.
Users can access the Zscaler service from their registered device.
[]![The list of service entitlements](/downloads/zslogin/administration/managing-device-groups/Zid-service-entitlement1.png)
[]![Selecting the device group restrictions](/downloads/zslogin/administration/managing-device-groups/zid-manage-device-group2.png)
[]![Enabling device group restrictions](/downloads/zslogin/administration/managing-device-groups/zid-manage-device-group-window3.png)
[]![Selecting the devices](/downloads/zslogin/administration/managing-device-groups/zid-manage-device-enable.png)