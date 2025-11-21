# Adding a Partner Tenant to Zscaler Client Connector
Source: https://help.zscaler.com/zscaler-client-connector/adding-partner-tenant-zscaler-client-connector
PDF: https://help.zscaler.com/pdf/com/en/1472836.pdf

You can add a partner tenant to the app so that you can access the partner’s internal resources without needing to log out of and back in to Zscaler Client Connector.
Before you can add a partner tenant, your organization and the partner organization must [enable Zscaler Private Access (ZPA) partner logins](/zscaler-client-connector/enabling-zpa-partner-logins). If you use Zscaler Client Connector version 4.6 and later for Windows, your organization can [enable partner logins by app profile](/zscaler-client-connector/configuring-zscaler-client-connector-app-profiles) and for specific domains. You can enable ZPA partner logins even if you do not use ZPA and use only Zscaler Internet Access (ZIA).
This article provides instructions on adding a partner tenant to Zscaler Client Connector based on the OS.
- [Windows](#windows-add-partner-tenant)
- [macOS](#macOS-add-partner-tenant)
[]To add a partner tenant using the Windows version of Zscaler Client Connector:
-
Open Zscaler Client Connector and click **Private Access**.
[See image.](#windows_partner_1)
If your organization does not use ZPA, the **Private Access** window displays only the **Add Partner Tenant** link and information about the partner tenant.
-
Click **Add Partner Tenant**.
The **Add Tenant** window appears.
- Based on your organization’s partner tenant settings, you are prompted to complete one of the following steps:
-
In the **Add Tenant** window, enter your username for the partner tenant and click **Submit**.
[See image.](#windows_partner_2)
- In the **Add Tenant** window:
-
Select the partner tenant to access and click **Connect**.
[See image.](#windows_partner_2b)
- Enter your username for the partner tenant, and click **Submit**.
-
The identity provider page for the partner organization appears. In this example, the partner identity provider is Okta.
[See image.](#windows_partner_3)
-
Enter your credentials for the partner tenant and log in.
The **Private Access** window reappears and displays both your organization's tenant and the partner tenant.
[See image.](#windows_partner_4)
After logging in to the partner organization, Zscaler Client Connector automatically turns off ZPA access to your organization. You can click **Turn On** for the main tenant to enable it and automatically turn off access to the partner organization.
After you have added the partner tenant, the partner tenant remains on this window, and you can click **Turn On** for the partner tenant to enable ZPA access to the partner organization.
[]![The Private Access window of Zscaler for WindowsClient Connector](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/windows_partner_1.png)
[]![The Add Tenant window of Zscaler Client Connector for Windows](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/windows_partner_2.png)
[]![zscaler-client-connector-add-tenant-partner-domain.png](/downloads/zscaler-client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/zscaler-client-connector-add-tenant-partner-domain.png)
[]![The authentication window of Zscaler Client Connector for Windows](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/windows_partner_3.png)
[]![The Private Access window of Zscaler Client Connector for Windows](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/windows_partner_4.png)
[]To add a partner tenant using the macOS version of Zscaler Client Connector:
-
Open Zscaler Client Connector and click **Private Access**.
[See image.](#mac_partner_1)
If your organization does not use ZPA, the **Private Access** window displays only the **Add Partner Tenant** link and information about the partner tenant.
-
Click **Add Partner Tenant**.
The **Add Tenant** window appears.
[See image.](#mac_partner_2)
-
In the **Add Tenant** window, enter your username for the partner tenant and click **Submit**.
The identity provider page for the partner organization appears. In this example, the partner identity provider is Okta.
[See image.](#mac_partner_3)
-
Enter your credentials for the partner tenant and log in.
The **Private Access** window reappears and displays both your organization's tenant and the partner tenant.
[See image.](#mac_partner_4)
After logging in to the partner organization, Zscaler Client Connector automatically turns off ZPA access to your organization. You can click **Turn On** for the main tenant to enable it and automatically turn off access to the partner organization.
After you have added the partner tenant, the partner tenant remains on this window, and you can click **Turn On** for the partner tenant to enable ZPA access to the partner organization.
[]![The Private Access window of Zscaler Client Connector for mac](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/mac_partner_1.png)
[]![The Add Tenant window of Zscaler Client Connector for mac](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/mac_partner_2.png)
[]![The authentication window of Zscaler Client Connector for mac](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/mac_partner_3.png)
[]![The Private Access window of Zscaler Client Connector for mac](/downloads/client-connector/end-user-guide/adding-partner-tenant-zscaler-client-connector/mac_partner_4.png)