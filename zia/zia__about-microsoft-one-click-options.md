# About Microsoft One Click Options
Source: https://help.zscaler.com/zia/about-microsoft-one-click-options
PDF: https://help.zscaler.com/pdf/com/en/1400881.pdf

If your organization uses any of the Microsoft 365 applications, you can send all Microsoft 365 traffic from all your locations, including remote user traffic, through the Zscaler service to the Microsoft cloud. Currently, Zscaler has two configuration options to choose from for Microsoft 365 traffic:
- Microsoft-Recommended One Click Microsoft 365 Configuration
- Microsoft 365 One Click Configuration
Microsoft recommends using their preferred configuration because it incorporates [their connectivity principals and recommendations](/zia/about-office-365).
Microsoft-Recommended One Click Microsoft 365 Configuration
Microsoft strongly recommends that any proxy should transparently forward end user Microsoft 365 traffic to their cloud. Zscaler does not identify all Microsoft 365 application traffic based on IP address and FQDN. It exempts a select list of FQDNs and IP ranges listed by Microsoft from TLS/SSL Inspection. To learn more, refer to the [Microsoft Technical documentation](https://docs.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide#new-office-365-endpoint-categories).
The Microsoft-Recommended Microsoft 365 One Click Configuration option allows Zscaler to map several but not all Microsoft IP address ranges and domains for most Microsoft 365 apps listed in [Microsoft 365 URLs and IP Address Ranges](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US&fromAR=1). Zscaler leverages the REST-based web service published by Microsoft to keep this mapping up to date.
Zscaler excludes specific Microsoft-listed FQDNs and IP ranges from TLS/SSL Inspection, as outlined in the following Microsoft 365 endpoints:
- [Microsoft 365 Worldwide (+GCC)](https://docs.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide)
- [Microsoft 365 operated by 21 Vianet](https://docs.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges-21vianet?view=o365-worldwide)
- [Microsoft 365 U.S. Government DoD](https://docs.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-u-s-government-dod-endpoints?view=o365-worldwide)
- [Microsoft 365 U.S. Government GCC High](https://docs.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-u-s-government-gcc-high-endpoints?view=o365-worldwide)
- [Enabling the Microsoft-Recommended Microsoft 365 One Click Configuration](#enablenew)
- [Effects of Enabling the Microsoft-Recommended Microsoft 365 One Click Configuration](#effectsnew)
To learn about enabling Microsoft Tenant Restrictions, see [Adding Tenant Profiles](/zia/adding-tenant-profiles#microsoft-login-services).
Zscaler does not publish the complete list of IP address ranges and FQDNs or wildcard domain names exempted from TLS/SSL Inspection. If further exemptions are required, you can define [TLS/SSL Inspection](/zia/configuring-ssl-inspection-policy) rules.
Microsoft 365 One Click Configuration
The following configuration was built prior to Microsoft's current [connectivity principals and recommendations](/zia/about-office-365). Microsoft advises using the **Microsoft-Recommended One Click Office 365 Configuration** detailed in the previous section.
With the **Office 365 One Click Configuration** feature, the Zscaler service automatically configures authentication exemption and decryption exemption rules required for the service to seamlessly support and secure your Microsoft 365 traffic. If this option is enabled, the Zscaler service exempts select Microsoft 365 applications from TLS/SSL Inspection. These exemptions are continuously evaluated based on Zscaler’s assessment of risk exposure and to ensure that anything exempted is as specific as possible to the delivery of Microsoft 365 for corporate users and no wider.
Zscaler does not publish the complete list of IP address ranges and FQDNs or wildcard domain names exempted from TLS/SSL Inspection. If further exemptions are required, you can define [TLS/SSL Inspection](/zia/configuring-ssl-inspection-policy) rules.
[]To enable this option, the **Office 365 One Click Configuration **option should be disabled.
- Go to **Policy** > **URL & Cloud App Control**.
- Go to the **Advanced Policy Settings** tab.
- Select **Enable Microsoft-Recommended One Click Office 365 Configuration**.
- Click **Save**, and then [activate the changes](/zia/saving-and-activating-changes-admin-portal).
If you get an error message after trying to enable this option, this relates to your admin rank. We compare your admin rank to that of two existing custom Firewall and DNS rules with top order. If your admin rank is less than those two ranks, you don’t have permission to enable the option.
[]To enable this option, the **Microsoft-Recommended Office 365 One Click Configuration** should be disabled.
- Go to** Administration **>** Advanced Settings**.
- Scroll down and select **Enable Office 365 One Click Exception Configuration**.
- Click **Save**, and then [activate the changes](/zia/saving-and-activating-changes-admin-portal).
- []The **Office 365 One Click Exception Configuration** option is grayed out.
- The Zscaler service automatically configures authentication exemption for Microsoft domains.
- A pre-defined **Office 365 One Click Rule** is enabled in the following policies:
- [][SSL Inspection Policy](#ssl-inspection)
- [Firewall Control Policy](#firewall-control)
- [DNS Control Policy](#dns-control)
- [Cloud App Control Policy](#cloud-app-control)
- When Microsoft 365 traffic is sent to the Firewall, the service fingerprints the application. All the fingerprinted information is logged and is viewable on the [Microsoft 365 dashboard](/zia/about-dashboards#o365).
- []Zscaler overrides the destination IP of Microsoft 365 traffic with the closest CDN destination for the Microsoft 365 application and leverages DNS servers at each of our data centers to provide a better user experience and improved application performance.
- DNS optimization is done automatically when the **Microsoft-Recommended Office 365 One Click Configuration **option is enabled.
- Microsoft's peering partnership with Zscaler allows for minimal hops into the Microsoft backbone for Microsoft 365 traffic, resulting in a better user experience.
- Zscaler exempts some IP, FQDN, or URLs from One Click if they are part of the Default category. Default category endpoints can be treated like regular destinations, which allows customers to apply the appropriate security controls. To learn more about Microsoft categories, refer to the [Microsoft Technical documentation](https://docs.microsoft.com/en-us/microsoft-365/enterprise/microsoft-365-network-connectivity-principles?view=o365-worldwide#new-office-365-endpoint-categories).
[]The rule isn't configurable and can't be deleted. It's automatically created to handle Microsoft 365 traffic through our Firewall module without inspecting the traffic. The rule allows Microsoft 365 traffic whose destination IP matches Microsoft 365 categories.
- If your admin rank is greater than or equal to that of the Firewall rule with top order, then the rule appears at rule order one with your rank. Going forward, only an admin with an equal or higher rank than yours can edit the rule order.
- If admin rank is disabled, then the rule appears at rule order one with rank 7.
[]The rule allows DNS traffic destined to Microsoft 365. The rule isn't configurable and can't be deleted, but its rule order can be changed, if necessary.
- If your admin rank is greater than or equal to that of the DNS rule with top order, then the rule appears at rule order one with your rank. Going forward, only an admin with an equal or higher rank than yours can edit the rule order.
[]A pre-defined rule is created, under each of the following cloud app categories, on the Cloud App Control Policy page (Policy > URL & Cloud App Control > Cloud App Control Policy):
- **Collaboration & Online Meetings**: The predefined rule in this category allows the Cloud App Control traffic destined to the following Microsoft 365 cloud applications.
- Yammer
- SharePoint Online
- Microsoft Teams
- Microsoft Sway
- **Productivity and CRM Tools**: The predefined rule in this category allows the Cloud App Control traffic destined to the following Microsoft 365 cloud applications.
- Common Microsoft 365 Applications
- Microsoft Dynamics 365
- Microsoft Delve
- Microsoft Power BI
- Microsoft Planner
- **File Sharing**: The predefined rule in this category allows the Cloud App Control traffic destined to the OneDrive cloud application.
- **Hosting Providers**: The predefined rule in this category allows the Cloud App Control traffic destined to the Microsoft Azure cloud application.
- **IT Services**: The predefined rule in this category allows the Cloud App Control traffic destined to the following Microsoft 365 cloud applications.
- Microsoft Azure AD
- Microsoft Intune
- **Webmail**: The predefined rule in this category allows the Cloud App Control traffic destined to the Outlook cloud application.
Cascading to URL filtering does not apply to the preceding predefined Cloud App Control policy rules when you enable the Allow Cascading to URL Filtering option (Administration > Advanced Settings). To perform URL cascading for Office 365 One Click, create a new rule with a higher rank than the existing predefined rule and use the cascading feature in that new rule.
The rules aren't configurable and can't be deleted, but their rule order can be changed, if necessary.
If your admin rank is greater than or equal to that of the Cloud App Control rule with top order, then the rules appear at rule order one with your rank. Going forward, only an admin with an equal or higher rank than yours can edit the rule order.
[]The rule isn't configurable and can't be deleted. If this rule is enabled, any Microsoft 365 traffic is exempted from SSL Inspection and other web policies, such as URL Filtering and Cloud App Control. For example, if you created a URL policy to block OneDrive, Sharepoint, etc., it's not applied.