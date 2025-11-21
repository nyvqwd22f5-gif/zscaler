# Exempting URLs and Cloud Apps from Authentication
Source: https://help.zscaler.com/unified/exempting-urls-and-cloud-apps-authentication
PDF: https://help.zscaler.com/pdf/com/en/1491631.pdf

Some client applications and websites don't support [cookie-based authentication](/unified/about-zscaler-cookies) or don't respond when the Zscaler service sends an HTTP 307 code that redirects the browser to authenticate to the Zscaler service. For example, the AIM client application and some Office 365 applications don't respond to the HTTP 307 redirect sent by the service. To enable users to access these applications and websites, you can add these URLs to an Authentication Exemptions list in the Admin Portal or add the URLs to your [PAC file](/unified/understanding-pac-files). Use tools like Fiddler or Wireshark to find the URL that the application or website is trying to access.
This URL exemption configuration only applies to traffic originating from known locations configured in the Admin Portal, excluding locations created with the Dedicated proxy port. For increased security and to prevent unauthorized use of subscribed dedicated proxy ports and authentication exemptions to work with DPP locations, unauthenticated users must authenticate, and authenticated users must first visit a website that does not bypass authentication or SSL inspection.
Configuring the Authentication Exemptions List
To exempt URLs and cloud apps from authentication:
- Go to **Policies **> **Common Configuration** > **Advanced** >** Advanced Settings**.
- In the **Authentication Exemptions **section:
- **Exempted** **URL Categories**: Select the [URL categories](/unified/about-url-categories) that you want to exempt from cookie authentication.
- **Exempted URLs**: Enter the URLs that you want to exempt from cookie authentication. See [URL format guidelines](/unified/url-format-guidelines).
-
**Exempted Applications**: Select the cloud applications or [cloud application categories](/unified/understanding-cloud-app-categories) that you want to exempt from cookie authentication.
By default, this field displays the first 100 cloud applications. The next 100 cloud applications are displayed when you click the **Click to see more **link at the bottom of the list. You can repeat this process to view the remaining cloud applications.
[See image.](#cloud-app-field-with-click-see-more)
- Click **Save **and activate the change.
Bypassing Authentication in a PAC File
If adding URLs to the authentication exemptions list in the Admin Portal isn't feasible, then you can [edit the PAC file](/unified/best-practices-writing-pac-files) and add an exception. For example:
if (dnsDomainIs (host, ".zscaler.com") || dnsDomainIs (host, ".aol.com)) return "PROXY ${GATEWAY}:9480; PROXY ${SECONDARY_GATEWAY}:9480; DIRECT";
The exception is applicable only for the traffic generated from a known location.
[]![Screenshot of ZIA Advanced Settings with Click to See More in the Cloud Applications Field](/downloads/zia/authentication-administration/user-management-authentication-settings/exempting-urls-cloud-apps-authentication/ZIA-Advanced-Settings-Click-to-See-More.png)