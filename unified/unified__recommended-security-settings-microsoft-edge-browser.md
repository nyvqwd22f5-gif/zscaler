# Recommended Security Settings for Microsoft Edge Browser
Source: https://help.zscaler.com/unified/recommended-security-settings-microsoft-edge-browser
PDF: https://help.zscaler.com/pdf/com/en/1491636.pdf

When you use Microsoft Edge, the browser automatically assigns all the websites you visit to one of the four security zones. You can adjust the default settings by accessing the **Security** tab in the** Internet Options** window.
To access and configure Microsoft Edge security zones, go to **Control Panel **> **Network and Internet** > **Internet Options** > **Security.**
[See image.](#four-security-zones)
If you are using an Explicit Proxy configuration (i.e., a PAC file or Proxy configuration with bypasses), any website that bypasses the proxy server is put into the **Local Intranet** zone. The bypasses are generally websites on your organization's network or the SAML server for authentication (ADFS/PingFederate/OKTA). Because the websites are in the **Local Intranet** zone, the browser automatically performs **Integrated Windows Authentication - logon** with a current username and password (NTLM/Kerberos), and you are authenticated to the server.
Websites that do not bypass the proxy server are considered to be internet traffic and are put into the **Internet** zone. In this case, you are prompted to re-authenticate with a username and password to access those websites.
However, when the Zscaler Client Connector feature is enabled in Tunnel Mode (Z-Tunnel 1.0 or Z-Tunnel 2.0), the explicit proxy configuration is removed, and all traffic is considered as internet traffic. Therefore, no traffic is bypassed. You must add the internal domains (i.e., websites on your organization's network) into the **Local Intranet** zone for the browser to perform automatic **Integrated Windows Authentication - logon** with a current username and password.
Zscaler recommends the following Microsoft Edge browser security settings:
- [Protected Mode Settings](#Protected-Mode-and-Trusted-Zone-Section)
- [Local Intranet Settings](#Local-Intranet-Option)
- [Trusted Sites Settings](#trusted-sites-settings)
- [Restricted Sites Settings](#restricted-sites-settings)
[]Zscaler recommends that you either **Enable** or **Disable** the Protected Mode across all four security zones. When Protected Mode is enabled, the browser distrusts all internet traffic.
To configure protected mode, go to **Internet Options **>** Security **>** Enable Protected Mode (requires restarting Internet Explorer)**.
[See image.](#Enable-Disable-Protected-Mode)
[]Websites that are on your organization's network are assigned to the **Local Intranet** zone. Zscaler recommends the following settings:
- Go to **Internet Options** > **Security** > **Local Intranet**.
-
In the **Local Intranet** page, click **Sites**.
[See image.](#local-intranet-sites)
- Enable the following options:
- Include all local (intranet) sites not listed in other zones.
- Include all network paths (UNCs)
-
Click **Advanced**.
[See image.](#Local-Intranet)
-
In the next window that appears, add your organization’s internal domains or websites.
[See image.](#adding-local-domains)
[]Websites that you trust are assigned to the **Trusted Sites** zone. Zscaler recommends that you do not add any sites specific to your Zscaler cloud in this zone.
To view and configure the trusted site settings:
- Go to **Internet Options** > **Security** > **Trusted Sites**.
-
On **the Trusted Sites** page, click **Sites**.
[See image.](#Trusted-Sites-Menu)
-
Remove any Zscaler specific sites from the **Trusted Sites** window and then enable **Require server verification (https:) for all sites in this zone**.
[See image.](#Trusted-Sites)
[]Websites in the **Restricted Sites** zone are not blocked but are unable to use scripting or any active content. Zscaler recommends that you do not add any sites specific to your Zscaler cloud in this zone.
To view and configure the restricted site settings:
- Go to **Internet Options** > **Security** >** Restricted Sites**.
-
On **the Restricted Sites** page, click **Sites**.
[See image.](#Restricted-Sites-Menu)
-
Remove any Zscaler specific sites from the **Restricted Sites** window.
[See image.](#Restricted-Sites)
[]![Screenshot of Microsoft Edge four security zones](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-settings-four-zones.png)
[]![Screenshot of Microsoft Edge security settings to enable or disable Protected Mode](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-enable-disable-protected-mode.png)
[]![Screenshot of Microsoft Edge Local Intranet Sites ](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-local-intranet-sites.png)
[]![Screenshot of Microsoft Edge Local Intranet advanced security settings ](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-local-intranet-advanced-settings.png)
[]![Screenshot of Microsoft Edge security settings to add Local Intranet domains](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-adding-local-intranet-domains.png)
[]![Screenshot of Microsoft Edge Trusted Sites](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-trusted-sites.png)
[]![Screenshot of Microsoft Edge security settings to add Trusted Sites](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-adding-trusted-sites.png)
[]![Screenshot of Microsoft Edge Restricted Sites](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-restricted-sites.png)
[]![Screenshot of Microsoft Edge security settings to add Restricted Sites](/downloads/zia/authentication-administration/user-management-authentication-settings/recommended-security-settings-microsoft-edge-browser/ZIA-microsoft-edge-security-adding-restricted-sites.png)