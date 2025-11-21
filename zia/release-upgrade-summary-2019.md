# Release Upgrade Summary (2019)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2019

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 06, 2019
### Feature Available
#### Updates to Cloud Service API
The following updates were made to the cloud service API:
- The following SSL Inspection Settings resources are now available:
- `GET /sslSettings/exemptedUrls`
- `POST /sslSettings/exemptedUrls`
- The following URL Filtering Policies resources are now available:
- `GET /urlFilteringRules`
- `POST /urlFilteringRules`
- `GET /urlFilteringRules/{ruleId}`
- `PUT /urlFilteringRules/{ruleId}`
- `DELETE /urlFilteringRules/{ruleId}`
- The following User Authentication Settings resources are now available:
- `GET /authSettings/exemptedUrls`
- `POST /authSettings/exemptedUrls`
- The `GET /urlFilteringRules/lite` resource was deprecated and removed.
To learn more about each endpoint, see the [API Reference](/zia/about-api) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection was also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

## November 22, 2019
### Feature Available
#### End of Support for TLS 1.0 & 1.1 for Admin Portal/Cloud Service API
Zscaler no longer supports TLS 1.0 and 1.1 for accessing the ZIA Admin Portal or Cloud Service API. If you are using a browser that does not support TLS 1.2, you must upgrade the browser or use an alternative browser.

## November 01, 2019
### Feature Available
#### CIPA Compliance
The new CIPA Compliance feature helps your organization be in compliance with [CIPA requirements](http://www.fcc.gov/sites/default/files/childrens_internet_protection_act_cipa.pdf). This feature provides a predefined URL filtering rule (**CIPA Compliance Rule**) and a control (**Enable CIPA Compliance**) to enable the predefined rule. It also provides a [CIPA Compliance Report](/zia/cipa-compliance-report) which gives insights into the traffic and users that are blocked from accessing the prohibited content based on the CIPA Compliance Rule. To learn more, see [About CIPA Compliance](/zia/about-cipa-compliance).

## October 30, 2019
### Feature Available
#### New File Type Supported for File Type Control
File Type Control now supports Microsoft Visual Studio (.vsix). You can select this file type when adding a File Type Control rule.
To learn more, see [Configuring the File Type Control Policy](/zia/configuring-file-type-control-policy).

## October 18, 2019
### Feature Available
#### Virtual Service Edge Support
ZIA Virtual Service Edge is designed for locations that need the full feature set of a ZIA Public Service Edge (ZEN) in a virtual form factor that is horizontally scalable and requires minimal deployment logistics.
[See image.](#vse)
To learn more, see [About Virtual Service Edge](/zia/about-virtual-service-edge) and [About Virtual Service Edge Clusters](/zia/about-virtual-service-edge-clusters).
[]![Screenshot of the new Virtual Service Edges page (formerly known as Virtual ZENs)](/downloads/zia/documentation-knowledgebase/release-notes/57-release/october-2019-service-update-release-notes/ZIA-Virtual-Service-Edges.png)

## October 11, 2019
### Feature Available
#### OneDrive & OneDrive (Personal)
The OneDrive cloud application is now split into **OneDrive** and **OneDrive (Personal)**. You can control access to your enterprise and personal OneDrive tenants through the Cloud App Control Policy page, under **File Sharing**.
[See image.](#onedrive)
To learn more, see [Adding a File Sharing Rule for Cloud App Control](/zia/adding-file-sharing-rule-cloud-app-control) and [About Microsoft One Click Options](/zia/about-microsoft-one-click-options).
[] ![Screenshot of OneDrive and OneDrive (Personal) options in the File Sharing Rule window](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/cloud-apps/configuring-office-365-support/about-microsoft-one-click-options/ZIA-5.7-OneDrive-File-Sharing.png)

## September 20, 2019
### Feature Available
#### Enable IPS Control at a Location or Sub-Location
If **Enforce Firewall Control** is enabled for a location or sub-location, you can also **Enable IPS Control** to use signature-based detection to control and protect your traffic inline.
[See image.](#location-ips)
To learn more, see [Configuring Locations](/zia/configuring-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and [About IPS Control](/zia/about-ips-control).
[]![Add Location with Gateway Options within ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-addlocation-ipscontrol.png)

### Feature Available
#### Executive Insights App Access
When configuring admins and admin roles, you can now allow admins access to the Executive Insights App. You can give them access to only the Executive Insights App or both the Admin Portal and the Executive Insights App. The admin's authorized mobile devices also can be viewed in the Admin Portal.
[See image.](#exec-insights)
To learn more, see [Adding an Executive Insights App Admin](/zia/adding-executive-insights-app-admin) and [Editing the Default Executive Insights App Role](/zia/editing-default-executive-insights-app-role).
[]![Screenshot of the Add Executive Insights App Administrator window.](/downloads/zia/authentication-administration/administrator-role-management/administrators/adding-executive-insights-app-admin/ZIA-Add_Executive-Insights-App-Administrator-Window.png)

### Feature Available
#### IPS Control
With IPS Control, you can use signature-based detection to control and protect your traffic inline. To learn more, see [About IPS Control](/zia/about-ips-control).
There are multiple ways to visualize and analyze your IPS data. You can use the new **IPS Overview** dashboard. You can also use the new **Threat Category**, **Threat Name**, and **IPS Rule Name** filters in the Firewall Logs and the **IPS Location**, **IPS Rule**, **IPS Threat Category**, and **IPS User** data types available with Firewall Insights. To learn more, see [About Dashboards](/zia/about-dashboards), [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters), and [Firewall Data Types and Filters](/zia/firewall-data-types-and-filters).
You can also configure your NSS feeds to include data about **IPS Rule Names**, **IPS Actions**, **Threat Names**, and** Threat Categories**. To learn more, see [Adding NSS Feeds for Firewall Logs](/zia/adding-nss-feeds-firewall-logs).

### Feature Available
#### New Firewall Log Fields for NSS Feed Output
The following Firewall log fields were added to NSS Feeds:
- IPS
- `%s{threatcategory} `
- `%s{threatname} `
- `%s{ipsrulelabel} `
To learn more, see [NSS Feed Output Format: Firewall Logs](/zia/nss-feed-output-format-firewall-logs).

## September 14, 2019
### Feature Available
#### EDNS0 Support
Zscaler authoritative DNS servers support EDNS0 client subnet options of EDNS0 protocol. To learn more, see [RFC 7871: Client Subnet in DNS Queries](https://tools.ietf.org/html/rfc7871) and [RFC 2671: Extension Mechanisms for DNS (EDNS0)](https://tools.ietf.org/html/rfc2671). These authoritative DNS servers can now accurately identify the origin of the DNS requests by looking into the client subnet options and return more accurate DNS responses based on the user's location.
To learn more, see [About Zscaler Authoritative DNS Servers](/zia/about-zscaler-authoritative-dns-servers).

## August 10, 2019
### Feature Available
#### Increased Allowed Tenants for Microsoft 365
The number of allowed tenant domains for Microsoft 365 has increased from 100 to 250, with 64 being the maximum characters per domain. For more information, see [Support for Microsoft Tenant Restrictions](/zia/support-microsoft-tenant-restrictions).

### Feature Available
#### Sandbox Augmented with Machine Learning
The Sandbox static analysis is now enhanced with machine learning capabilities. Machine learning improves malware detection and increases the accuracy of Sandbox verdicts. You can view the machine learning results in the [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report).
[See image.](#sandbox)
[]![Screenshot of the Machine Learning Widget in the Sandbox Detail Report.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/august-2019-service-update-release-notes/ZIA-Sandbox-Detail-Report-Machine-Learning-Analysis.png)

### Feature Available
#### TLD Categories
You can now use top-level domains (TLD) as criteria in URL filtering policies. Using our new TLD categories, URL filtering policies can match traffic to specific TLDs and act accordingly.
[See image.](#tld-categories-image)
To learn more, see [About TLD Categories](/zia/about-tld-categories) and [Configuring TLD Categories](/zia/configuring-tld-categories).
[]![TLD Categories](/downloads/TLD-Categories-Image.png)

## July 26, 2019
### Feature Available
#### Enforce Zscaler Client Connector SSL Setting
For **Locations**, you can now use the **Enforce Zscaler Client Connector SSL Setting** option to enforce the [SSL Inspection setting for Zscaler Client Connector (Z App)](/z-app/configuring-ssl-inspection-zscaler-app#configure-SSL-Zscaler-App) and ignore the location's SSL policy for all Zscaler Client Connector traffic.
[See image.](#enforce-zscaler-app-ssl)
To learn more, see [Configuring Locations](/zia/configuring-locations#EnableSSLScanning) and [Configuring Sub-Locations](/zia/configuring-sub-locations#EnableSSLScanning).
[]![The Enforce Zscaler Client Connector SSL Setting option for Locations](/downloads/zia/Locations-Enforce-Zscaler-App-SSL-Setting.png)

## May 31, 2019
### Feature Available
#### Additional DLP Dictionaries
We have added four new predefined DLP dictionaries. These are:
- **ABA Bank Routing Numbers**: This dictionary detects ABA routing transit numbers from the United States.
- **Individual Taxpayer Registry ID (Brazil)**: This dictionary detects Individual Taxpayer Registry ID numbers (CPF) from Brazil.
- **National Health Service Number (UK)**:  This dictionary detects National Health Service (NHS) numbers from the United Kingdom.
- **Standardized Bank Code (Mexico)**: This dictionary detects Standardized Bank Code (CLABE) numbers from Mexico.
To learn more, see [About DLP Dictionaries](/zia/about-dlp-dictionaries) and [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).

### Feature Available
#### Additional EDM Data Types
When creating your EDM templates, you can now select** ABA Bank Routing Numbers**, **Individual Taxpayer Registry ID (Brazil)**, **National Health Service Number (UK)**, and **Standardized Bank Code (Mexico)** as Data Types. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### AES-GCM Support for IPSec VPN Tunnels
Zscaler now supports the following IPSec encryption algorithms for IKE Phase 2:
- AES-128-GCM with 128-bit ICV
- AES-192-GCM with 128-bit ICV
- AES-256-GCM with 128-bit ICV
To learn more, see [Supported IPSec VPN Parameters](/zia/about-ipsec-vpns#supported-ipsec-vpn-parameters).

### Feature Available
#### DLP Dictionary Enhancements
The **Medical Information** DLP dictionary has been enhanced with additional phrases for diseases, treatments, and drugs. In addition, you can now select a **Confidence Score Threshold** for the **National Insurance Numbers (UK)** dictionary.

### Feature Available
#### ECDHE_ECDSA Cipher Suite Support
Zscaler now supports ephemeral ECDH with ECDSA signatures for SSL inspection to ensure Perfect Forward Secrecy (PFS). To learn more, see [Zscaler SSL/TLS Support](/zia/zscaler-ssl-tls-support).

### Feature Available
#### End User Notification (EUN) for Unauthenticated Traffic
You can now display a caution notification to unauthenticated users sending traffic through a location or sub-location.
[See image.](#location-caution)
To learn more, see [Configuring Locations](/zia/configuring-locations), [Configuring Sub-Locations](/zia/configuring-sub-locations), and [About Acceptable Use Policy and End User Notifications](/zia/about-acceptable-use-policy-and-end-user-notifications#configuringcaution).
[]![Add Location with Gateway Options within ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-addlocation-enablecaution.png)

### Feature Available
#### Enhancement to Advanced Threat Protection
Advanced Threat Protection now supports file format vulnerability protection for PDF documents. To learn more, see [Configuring the Advanced Threat Protection Policy](/zia/about-advanced-threat-protection#malicious).

### Feature Available
#### Enhancement to File Type Control
There is a new **Online Gaming** category for use in [File Type Control](/zia/about-file-type-control). This category is composed of:
- Sega Master System Files (sms)
- Game Boy Advance Files (gba)
- Nintendo DS Files (3ds, nds)
- Playstation Files (psx)
- Sega 32X Files (32x)
- XBox Files (xipo, xtfo, xbeh)
You can also select **Executable Scripts (py, sh, bat)** under the **Executable category**.

### Feature Available
#### Enhancement to FTP Control
FTP Control is now available to any organization that has the Standard Firewall subscription. This gives you the ability to control FTP over HTTP and native FTP traffic. To learn more, see [About FTP Control](/zia/about-ftp-control).

### Feature Available
#### Enhancement to HTTP Tunnel Control
You can now allow or block non-RFC compliant HTTP traffic on HTTP/HTTPS ports. This option is enabled by default for new organizations, but disabled for existing ones. To learn more, see [About Advanced Settings](/zia/about-advanced-settings#http-tunnel-control).
[See image.](#http-tunnel-control)
[]![Screenshot highlighting the Block non-RFC compliant HTTP requests on HTTP/HTTPS ports option on the Advanced Settings page.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-advanced-settings-block-non-rfc-compliant-http-requests.png)

### Feature Available
#### Enhancement to Malware Protection Policy
You can now allow or block ransomware when configuring the Malware Protection policy. To learn more, see [Configuring the Malware Protection Policy](/zia/about-malware-protection#configure-malware-protection-policy).
[See image.](#ransomware)
[]![Screenshot highlighting the Ransomware option on the Malware Protection page.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-malware-protection-ransomware.png)

### Feature Available
#### Enhancement to Sandbox Policy
Sandbox now supports the following file types when adding a Sandbox Policy rule:
- 7-Zip (.7z)
- Bzip2 (.bz, .bz2)
- Tar (.tgz, .gtar, .tar)
- Excel Add-In (.xlam)
- Excel Binary Workbook (.xlsb)
- Symbolic Link (.slk)
- PowerPoint Show (.ppsx)
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
Additional Sandbox enhancements were applied to improve reliability and stability.

### Feature Available
#### Explicit Proxy Mode Configuration Available for Index Tool VM
You can now choose to configure your Index Tool VM in explicit proxy mode. To learn more, see [Configuring the Index Tool](/zia/configuring-index-tool).

### Feature Available
#### Increase to Maximum Number of Dictionaries & Engines
You can now create a maximum of 79 custom DLP dictionaries and 47 custom DLP engines.

### Feature Available
#### Insights Logs Improvements & Enhancements
The Insights Logs pages have been enhanced to give you a better workflow as you view and define traffic information. These pages contain the following enhancements:
- Insights Logs is now its own page, so you can smoothly switch between Insights and Insights Logs.
- You can now select the number of records you'd like displayed on the page.
- You can now sort through certain columns by ascending or descending order.
- You can now search within columns that have the magnifying glass icon next to their name.
- At the top of the logs table, you can now see the number of records found between the timeframe you select.
[See image.](#insights)
To learn more, see [About Insights](/zia/about-insights) and [About Insights Logs](/zia/about-insights-logs).
[]![Screenshot of the Web Insights Logs page with the 5.7 enhancements highlighted](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-5.7-insights-enhancements.png)

### Feature Available
#### Interactive Report: SSL Traffic Overview
The new interactive report SSL Traffic Overview allows you view aggregated statistics for metrics logged for SSL transactions. To view the report, go to **Analytics** > **Interactive Reports**, and look under **Web Activity**. To learn more, see [About Interactive Reports](/zia/about-interactive-reports).
[See image.](#cipher-report)
[]![Screenshot of the SSL Traffic Overview interactive report](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-5.7-cipher-report.png)

### Feature Available
#### Item List Improvements
Items lists now have the following customization options:
- Filter the list by searching for a word, phrase, or number contained in an item.
- Remove all  items from the list or only items from a specific page.
- View up to 500 items on a page.
[See image.](#item-list)
[]![Screenshot of the item list with the improved features.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/ZIA-Item-List.png)

### Feature Available
#### New Action in Firewall Insights Logs
Zscaler has introduced a new Action in Firewall Insights Logs; **Allow due to insufficient app data**. This is used when the service's deep packet inspection (DPI) evaluates a Firewall Filtering policy rule containing a Network Application and the session terminates before the DPI can determine the type of traffic or Network Application. To learn more, see [Firewall Insights Logs: Filters](/zia/firewall-insights-logs-filters).

### Feature Available
#### New Cloud Apps
Added four new cloud apps for use in Cloud App Control:
- **Google Classroom**, a **Productivity & CRM Tools** cloud app
- **MailBigFile**, a **File Sharing** cloud app
- **Meetup**, a **Social Networking** cloud app
- **Zoom**, a **Collaboration & Online Meetings** cloud app
To learn more, see [About Cloud App Categories](/zia/cloud-app-categories).

### Feature Available
#### New Controls for RTSP and PPTP Traffic
You can now select RTSP and PPTP as options for** Auto Proxy Forwarding for Non-defined Ports**. You can use this to send your RTSP and PPTP traffic to the web engine for inspection if it's destined for a non-standard port and doesn't match the predefined network services. To learn more, see [About Advanced Settings](/zia/about-advanced-settings).
[See image.](#auto-prox)
In addition, if your organization uses a port other than 554 for RTSP traffic or 1723 for PPTP traffic, you can configure the Zscaler service to accept traffic from your custom RTSP and PPTP ports by using the **Services Forwarded to RTSP** and **Services Forwarded to PPTP** options. To learn more, see [Configuring Custom Ports](/zia/configuring-custom-ports).
[See image.](#services-forwarded)
[]![Screenshot of Auto Proxy Forwarding ](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-auto-proxy-forwarding.png)
[]![Screenshot of Services Forwarded options](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-services-forwarded.png)

### Feature Available
#### New File Types Available for DLP Policies
When creating DLP policy with both Zscaler and external DLP engines you can now select **Microsoft Outlook Message (msg)** as a **File Type**. In addition, for policies created with an external DLP engine, you can select **Password Protected / Encrypted** for use on password protected files. To learn more, see [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection).

### Feature Available
#### New Shorthand Character Classes Supported
When creating patterns for your DLP Dictionaries, the \d, \D, \s, \S, \w, and \W character classes are now supported. To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries).

### Feature Available
#### New Ways to Monitor DLP Transactions
We have added two new fields to help you monitor your DLP transactions: **DLP MD5** and **DLP Identifier**. You can find these fields in your DLP Notification Templates, NSS, and Web Insights Logs.
For your DLP Notification Templates, there are two new macros. These are:
- ${DLPMD5}: This macro provides the MD5 hash of the file that triggered the DLP rule.
- ${TRANSACTION_ID}: This macro provides the DLP identifier of the transaction that triggered a DLP rule.
To learn more, see [Configuring DLP Notifications](/zia/configuring-dlp-notification-templates).
For your NSS web log feeds, you can add:
- %s{dlpmd5}: This field provides the MD5 hash of the file that triggered the DLP rule.
- %d{dlpidentifier}: This field provides the DLP identifier of the transaction that triggered the DLP rule.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).
You can use these numbers with the new** DLP MD5** and **DLP Identifier** filters in your Web Insights Logs to help you locate your DLP transactions. To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters).
Enhancements to the Dictionary Field
The **DLP Dictionaries** filter in Web Insights Logs now includes a match count that displays how many times the dictionary was hit.
[See image.](#match-count)
For NSS, there is a new %s{dlpdictcount} field which shows the number of times a dictionary was hit. This can be used together with %s{dlpdict} to see how many times a particular dictionary was hit.
There are no changes to the ${DICTIONARIES} macro from DLP Notification Templates as it already displays a match count.
[]![Screenshot of the DLP Dictionary Match Count features](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-dlp-dictcount.png)

### Feature Available
#### New Web Log Fields for NSS Feed Output
The following web log fields were added to NSS Feeds:
- DLP
- `%d{dlpidentifier}`
- `%s{dlpmd5} `
- `%s{dlpdicthitcount} `
- Zscaler Client Connector Device Information
- `%s{devicename}`
- `%s{deviceostype}`
- `%s{deviceosversion}`
- `%s{devicemodel}`
- `%s{deviceappversion}`
- HTTP Transaction
- `%s{ua} `
- `%s{ua_token} `
The existing field `%s{ua}` will now include the full user agent string. If you'd like the tokenized version, you can add the new field `%s{ua_token}` to your NSS Feed.
To learn more, see [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs).

### Feature Available
#### Outlook & Outlook (Personal)
The Outlook cloud application is now split into **Outlook** and **Outlook (Personal)**. You can control access to your enterprise and personal Outlook applications through the Cloud App Control Policy page, under **Webmail**. To learn how to add a Webmail rule, see [Adding a Webmail Rule for Cloud App Control](/zia/adding-webmail-rule-cloud-app-control).
[See image.](#outlook)
With the Microsoft-Recommended Microsoft 365 One Click Configuration option turned on, Outlook and Outlook (Personal) won’t be SSL bypassed. This allows you to perform SSL inspection to identify phishing attacks and data exfiltration, DLP, Sandbox, and all other security policies Zscaler provides. To learn more, see [About Microsoft One Click Options](/zia/about-microsoft-one-click-options).
[]![Screenshot of Outlook & Outlook (Personal) in the Webmail Rule window](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/ZIA-5.7-Outlook-Webmail.png)

### Feature Available
#### Response Signing SSL Certificate for Identity Proxy
When configuring Identity Proxy settings for cloud apps (**Administration** > **Identity Proxy Settings**), You now can choose the signing SSL certificate you want the Identity Proxy to use for signing SAML responses. To learn more,  see [Configuring the Zscaler Identity Proxy for Cloud Apps](/zia/configuring-zscaler-identity-proxy-cloud-apps#configure-identity-proxy-settings).
[See image.](#identity-proxy-cert)
[]![Screenshot highlighting the Response Signing SSL Certificate option in the Edit Identity Proxy Settings window.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-identity-proxy-response-signing-certificate.png)

### Feature Available
#### Scheduled Updates for EDM Templates
We have introduced the ability to schedule regular updates for your Index Template. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### SSL Cipher Filters Extended to Encrypted SSL Traffic
The following SSL Cipher Web Insights filters now apply to encrypted SSL traffic (**Analytics** >** Web Insights** > **Logs**):
- Certificate Expiry
- Cipher Certificate Validations
- Client Connection Ciphers
- Client Connection TLS Version
- OCSP Result
- Server Connection Ciphers
- Server Connection TLS Version
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters).

### Feature Available
#### Terminology Changes on SSL Inspection Page
To enhance clarity, the following field names have changed on the SSL Inspection page (**Policy** > **SSL Inspection**):
- **Do Not Inspect Sessions to these URL Categories** is now** Exempt These URL Categories from Inspection & Other Policies**
- **Do Not Inspect Sessions to these Hosts** is now **Exempt These Hosts from Inspection & Other Policies**
- **Do Not Inspect these Applications** is now **Exempt These Applications from Inspection & Other Policies**
On the **Advanced Settings** page (**Administration** > **Advanced Settings**), **Enable policies for SSL global exempted domains** is now **Override Zscaler Global SSL Exemptions List**.

### Feature Available
#### Tunnel Insights
With the new Tunnel Insights (**Analytics** > **Tunnel Insights**), you can now view IPSec and GRE tunnel data as well as monitor the health and status of your configured tunnels. To learn more, see [About Insights](/zia/about-insights) and [About Insights Logs](/zia/about-insights-logs).
[See image.](#tunnel-insights)
[]![Screenshot of the Tunnel Insights page.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-tunnel-insights.png)

### Feature Available
#### Updates to Cloud Service API
The following updates were made to the cloud service API:
- A `/vips` endpoint was added that allows you to get a flat list of all virtual IP addresses (VIPs) for your Zscaler cloud. To learn more, see [Determining Your Zscaler Data Center VIPs for SD-WAN Integrations](/zia/sd-wan-api-integration#VIP) and the [API Reference](/zia/about-api).
- The rate limit was updated for the following resources:
- `POST /auditlogEntryReport`
- `POST /users`
- `PUT /users/{userId}`
To learn more, see the [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection was also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### Updates to Ranges & Limitations
The following ranges and limitations changes were made to the Admin Portal:
- For Locations:
- Location Groups: You can add a combined total of 256 location groups per organization.
- For URL Filtering & Cloud App Control:
- Custom URLs: You can add a combined total of 25,000 custom URLs across all policies.
- Google App Domains per Request: You can add a combined total of 100 domains, and each domain can have up to 160 characters.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations).

### Feature Available
#### URL Count Display
When adding URLs that count towards the [25,000 custom URL limit](/zia/ranges-limitations#URLFiltering_CloudAppControl), you can now see how many your organization is using and how many are still available to add.
[See image.](#url-count)
You can see this information in the following areas within the Admin Portal:
- **Custom URLs** in all **URL Categories**
- **Authentication Exempted URLs** in **Advanced Settings**
- **Optimize the FQDN** and **Do Not Optimize These FQDN** in **Advanced Settings**
- **Blocked URLs** in **SSL Inspection**
- **Exempt These Hosts from Inspection & Other Policies** in **SSL Inspection**
- **Do Not Scan Content from these URLs **in **Malware Protection** and **Advanced Threat Protection**
- **Allowed URLs** in **FTP Control **
- **Domains** in **Bandwidth Classes**
[]![Screenshot of URL Count Display](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-url-count.png)

### Feature Available
#### Z-Tunnel 2.0
The Z-Tunnel is a lightweight, HTTP tunnel that the Zscaler service uses to forward traffic to the ZIA Public Service Edges. Z-Tunnel 2.0 has a tunneling architecture that uses DTLS or TLS to send packets to the Zscaler service. Because of this, Z-Tunnel 2.0 is capable of sending all TCP, UDP and ICMP traffic.
To learn more, see [About Z-Tunnel 1.0 & Z-Tunnel 2.0](/z-app/about-z-tunnel-1.0-z-tunnel-2.0).

### Feature Available
#### Zscaler Client Connector Portal as IdP
Zscaler Client Connector Portal as IdP (**Administration** > **Authentication Settings**) simplifies the configuration process when configuring the Zscaler Client Connector Portal as your IdP. It now automatically performs the necessary configurations with the Zscaler Client Connector IdP URL and certificate. To learn more, see [Using the Zscaler Client Connector Portal as an Identity Provider](/z-app/using-zscaler-app-portal-identity-provider-idp).
[See image.](#zscaler-app-IdP)
[]![Screenshot highlighting the Zscaler Client Connector Portal as IdP option in the Authentication Profile page.](/downloads/z-app/configuring-policy-and-administration-settings/using-zscaler-app-portal-identity-provider-idp/ZIA-Authentication-Profile-Zscaler-App-Portal-IdP.png)

## May 13, 2019
### Feature Available
#### Perform SSL Inspection for Specific URL Categories
When configuring the SSL Inspection policy, you can now select URL categories you want the service to inspect. To learn more, see [Configure the SSL Inspection Policy](/zia/about-ssl-inspection#configure-ssl-inspection-policy).
[See image.](#ssl-inspection-url-categories)
[]![Screenshot highlighting the Inspect Sessions to These URL Categories option on the SSL Inspection page.](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-ssl-inspect-sessions-url-categories.png)
