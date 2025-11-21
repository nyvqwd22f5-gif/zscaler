# Release Upgrade Summary (2020)
Source: https://help.zscaler.com/zia/release-upgrade-summary-2020

This article provides a summary of all new features and enhancements per Zscaler cloud for Zscaler Internet Access (ZIA). Zscaler will email a notification to your organization's registered support contacts approximately one week before your cloud is upgraded. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** zscaler.net, zscalerone.net, zscalertwo.net, zscalerthree.net, zscloud.net, zscalerbeta.net
The following service updates were deployed to zscaler.net on

## December 16, 2020
### Feature Available
#### Custom Root Certificates for Cloud Browser Isolation
Custom root certificates allow admins to have more control over isolation profile authentication. Admins in the Cloud Browser Isolation Admin Portal can manage custom root certificates for their organization, and associate them with specific isolation profiles.
To learn more, see [About Custom Root Certificates in Cloud Browser Isolation](https://help.zscaler.com/zia/about-custom-root-certificates-cloud-browser-isolation).

## December 14, 2020
### Feature Available
#### Customizable End User Notification in Isolation
Cloud Browser Isolation admins can customize the end user notification that displays in the browser at the beginning of a new isolated session.
Admins can edit the notification for individual isolation profiles, or for all isolation profiles in their organization, and can personalize themes that align with their organization's brand. Theme features that can be customized include the text and background color, welcome title and notification message, and image logo. There is also the ability to disable the end user notification altogether.
To learn more, see [Selecting a Banner Theme for the End User Notification in Cloud Browser Isolation](https://help.zscaler.com/zia/selecting-banner-theme-end-user-notification-cloud-browser-isolation).

### Feature Available
#### Override PAC Files to Avoid Incorrect Webpage Translation in Isolation
Some users in Cloud Browser Isolation may experience traffic redirects resulting in inaccurate language translation of the isolated webpage. This is due to the chance that the ZIA Public Service Edge (formerly Zscaler Enforcement Node or ZEN) geographically closest to the user's isolation session may be in a different region or country than the ZIA Public Service Edge geographically closest to the physical user.
To avoid this, users can make the change in new or existing isolation profiles to override the associated PAC file and return traffic to the originated ZIA Public Service Edge.
To learn more, see [Creating an Isolation Profile for Cloud Browser Isolation](https://help.zscaler.com/zia/creating-isolation-profile-cloud-browser-isolation).

## December 11, 2020
### Feature Available
#### DLP & EDM Support for PESEL Numbers
We have added a new predefined DLP dictionary: Identity Card Number (Poland). This dictionary detects PESEL numbers from Poland.
When creating your EDM templates, you can also select Identity Card Number (Poland) as a Data Type.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries) and [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### Increase to Maximum Number of Custom DLP Dictionaries
You can now create a maximum of 160 custom DLP dictionaries. Prior to this release, a maximum of 79 custom DLP dictionaries was allowed.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations#DLP).

### Feature Available
#### Migrating from Directory Synchronization to SCIM Provisioning
If you use Active Directory or OpenLDAP user repositories, you can now disable directory synchronization and enable SCIM Provisioning or SAML auto-provisioning (if you have multiple identity providers). Zscaler recommends using this option to migrate from directory sync to SCIM provisioning.
[See image.](#disable-sync-enable-scim)
As part of this enhancement, the Directory Type field was renamed to User Repository Type on the Authentication Profile page.
[See image.](#user-repository-type)
To learn more, see [About Authentication Profile](/zia/about-authentication-profile).
[]![Screenshot highlighting the Disable Directory Sync & Enable SCIM Provisioning setting on the Authentication Profile page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Authentication-Profile-Disable-Directory-Sync-Enable-SCIM-Provisioning.png)
[]![Screenshot highlighting the User Repository Type field on the Authentication Profile page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Authentication-Profile-User-Repository-Type.png)

### Feature Available
#### New Actions for Patterns & Phrases Type DLP Dictionaries
Zscaler now supports two new actions that allow you to configure how Patterns & Phrases type DLP dictionaries evaluate matching patterns and phrases:
- Count All: The dictionary counts all matches of the pattern or phrase, including identical patterns or phrases, toward the match count.
- Count Unique: The dictionary counts each unique match of the pattern or phrase toward the match count only once, regardless of how many times the pattern or phrase appears.
[See image.](#dlp-dictionary-action-image)
To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries) and [Defining Phrases for Custom DLP Dictionaries](/zia/defining-phrases-custom-dictionaries).
[]![The Count All and Count Unique Actions for custom DLP dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/DLP-Dictionaries-Count-All-Unique.png)

## November 20, 2020
### Feature Available
#### Enhancements to PAC File Verification
You can now save a custom PAC file version only after verifying it in the Add PAC File window from the Administration > Hosted PAC Files page. If you try to save a PAC file with verified errors, you will be prompted with a warning message. You can still save the file by entering `I accept the risk` into the warning window that appears.
[See image.](#deploy-pac-file)
To learn more, see [Using Custom PAC Files to Forward Traffic to ZIA](/zia/using-custom-pac-file-forward-traffic-zia).
[]![Screenshot of Save and Deploy PAC file version Window](/sites/default/files/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/pac-files/using-pac-files/using-custom-pac-file-forward-traffic-zia/zia-save-deploy-pac-file.png)

### Feature Available
#### New Field Supported in Web Insights
There is a new field for **Domain Fronting Hostname **in the Web Insights. The field is available in filters and columns.
To learn more, see [Web Insights Logs: Filters](/zia/web-insights-logs-filters) and [Web Insights Logs: Columns](/zia/web-insights-logs-columns).

### Feature Available
#### SaaS Assets Report
The new SaaS Assets Report shows you the current state of your files and email messages.
[See image.](#saas-assets-report)
When you click to further analyze an application or tenant, you are redirected to the Assets with Incidents page, which provides a comprehensive view for each selected application and tenant.
[See image.](#assets-with-incidents)
Also, the current SaaS Security Report has been renamed to the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Report](/zia/saas-assets-report) and [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
[]![Screenshot of the SaaS Assets Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-SaaS-Assets-Report-1.png)
[] ![Screenshot of the Assets with Incidents page in the SaaS Assets Report](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-Assets-with-Incidents-Page.png)

### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for Salesforce.
[See image.](#salesforce-tenant)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies & Scan Configuration
You can now configure the SaaS Security API policies and scan schedules for CRM applications. Prior to this release, the policies and scan schedules were configurable for email and file sharing applications only.
[See image.](#policies-schedules-crm-apps)
To learn more, see [Configuring SaaS Security API Policies](/zia/configuring-saas-security-api-policies).
For Scan Configuration, you can now use the New Data Only option to configure a scan to ignore all historical data.
[See image.](#new-data-only-option)
To learn more, see [Configuring SaaS Security API Scan Schedules](/zia/configuring-saas-security-api-scan-schedules).
Updates to the SaaS Assets Summary Report
You can now view the CRM application category in the SaaS Assets Summary Report.
To learn more, see [SaaS Assets Summary Report](/zia/saas-assets-summary-report).
Updates to SaaS Security Insights & Insights Logs
You can now view the CRM application category in SaaS Security Insights and Insights Logs.
To learn more, see [SaaS Security Insights](/zia/saas-security-insights) and [SaaS Security Insights Logs](/zia/saas-security-insights-logs).
[]![Screenshot highlighting the new Salesforce application in the Choose the SaaS Application Provider section on the Add SaaS Application Tenant page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Choose-SaaS-Application-Provider-Release.png)
[]![Configure SaaS Security API policies and scan schedules for CRM applications](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/6.0r-SaaS-Policies-CRM.png)
[]![The New Data Only option for SaaS Security API Scan Configuration](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/6.0r-SaaS-New-Data-Only.png)

## November 06, 2020
### Feature Available
#### DLP & EDM Support for Malaysian Identity Card Numbers & Indonesian Tax Identification Numbers
We have added two new predefined DLP dictionaries:
- Identity Card Number (Malaysia): This dictionary detects national identity card (MyKad) numbers from Malaysia.
- Tax Identification Number (Indonesia): This dictionary detects tax identification numbers (NPWP) from Indonesia.
When creating your EDM templates, you can also select Identity Card Number (Malaysia) and Tax Identification Number (Indonesia) as Data Types.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries) and [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### Enhancements to Cloud App Categories
Updated the following predefined cloud app categories in the Cloud App Control Policy page:
- [Collaboration & Online Meetings](#collaboration-onlinemeetings)
- [Consumer](#consumer)
- [Hosting Providers](#hosting-providers)
- [Human Resources](#human-resources)
- [IT Services](#it-services)
- [Productivity & CRM Tools](#productivity-crmtools)
- [Sales & Marketing](#sales-marketing)
- [System & Development](#system-development)
To learn more, see [About Cloud App Categories](/zia/about-cloud-app-categories).
[]Added the following new cloud apps to this category:
- ConceptBoard
- Livestorm
[]Added the following new cloud apps to this category:
- Book4time
- Fortuna
- Getsquire
- Mileiq
- Motorlot
- Pantheon
- Preply
- ResumeCompanion
- SurveyAnyplace
- Teachable
- Vionic
- Xologic
[]Added the new cloud app Efty to this category.
[]Added the following new cloud apps to this category:
- Breezy
- Bullhorn
- Recruiter
[]Added the following new cloud apps to this category:
- Centrify
- Emailage
- ParticularAudience
- Rulai
[]Added the following new cloud apps to this category:
- Accelo
- Betteryou
- BrandFolder
- Chartio
- Close
- Envoy
- Genially
- Granular
- Lighthouse
- PriorityMatrix
- Talech
- Zoovu
[]Added the following new cloud apps to this category:
- AgilityPR
- Automizy
- Comscore
- Constant.Co
- Evidence
- Notifia
- RapidFunnel
- Tooltip
- Unless
- Zeeto
- Zurple
[]Added the following new cloud apps to this category:
- Glitch
- Instabug
- Rapidapi
- Saucelabs
- Talkjs

### Feature Available
#### Increase to Maximum Number of Phrases for Custom DLP Dictionaries
The maximum number of phrases allowed in a custom DLP dictionary has increased from 120 to 256.
To learn more, see [Defining Phrases for Custom DLP Dictionaries](/zia/defining-phrases-custom-dictionaries).

### Feature Available
#### New File Types Supported for File Type Control & DLP
When configuring File Type Control and DLP policies, you can now select new file types in the following categories:
- Archive
- Database
- Executable
- Other Documents
- Other Microsoft Files
- Source Code
- Web Content
Database, Other Microsoft Files, and Source Code are new categories.
To see the new file types added for each category, go to the [File Type Control](/zia/about-file-type-control) and [Data Loss Prevention](/zia/about-data-loss-prevention) pages in the ZIA Admin Portal.

## October 23, 2020
### Feature Available
#### Bytes Supported by Data Type Traffic Direction
The data type **Traffic Direction** now supports only the unit **Bytes**. You will see this change when selecting **Traffic Direction** in Web Insights and when creating or adding a new widget for dashboards or custom reports.
[See image.](#traffic-direction)
To learn more, see [Web Data Types and Filters](/zia/web-data-types-and-filters).
[]![Screenshot of the data type Traffic Direction in Web Insights. The unit Bytes is the only unit supported by the Traffic Direction.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-Traffic-Direction-Insights.png)
![Screenshot of the data type Traffic Direction in the New Widget window. The unit Bytes is the only unit supported by the Traffic Direction.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-Traffic-Direction-Widget.png)

## October 09, 2020
### Feature Available
#### Enhancements to Cloud App Categories
Updated the following predefined cloud app categories in the Cloud App Control Policy page:
- [Collaboration & Online Meetings](#collaboration-onlinemeetings)
- [Consumer](#consumer)
- [IT Services](#it-services)
- [Productivity & CRM Tools](#productivity-crmtools)
- [Sales & Marketing](#sales-marketing)
- [Streaming Media](#streaming-media)
- [System & Development](#system-development)
To learn more, see [About Cloud App Categories](/zia/about-cloud-app-categories).
[]The new cloud app WeChat Work was added to this category.
[]The following new cloud apps were added to this category:
- Grammarly
- Realtor
- TradingView
[]The following new cloud apps were added to this category:
- Chocolatey
- New Relic
[]The following new cloud apps were added to this category:
- Glia
- StreamRail
- WalkMe
- ZenDesk
[]The following new cloud apps were added to this category:
- AdRoll
- Celtra
- Connatrix
- Conviva
- Criteo
- Dianomi
- FullStory
- Medallia
- Outbrain
- Permutive
- RevJet
- SundaySky
- Taboola
- Yotpo
[]The new cloud app iHeartRadio was added to this category.
[]The following new cloud apps were added to this category:
- Bugsnag
- Split

### Feature Available
#### FQDN Evaluation for Standard and Advanced Cloud Firewall
Zscaler now allows FQDN evaluation for both Standard and Advanced Cloud Firewall policies. Depending on your type of Firewall, IP addresses and FQDNs will have separate maximum limits.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations).

### Feature Available
#### QBR Report: Include/Exclude Road Warrior Traffic
You now have the ability to include or exclude remote user (i.e., road warrior) traffic in the QBR Report.
To learn more, see [Quarterly Business Review Report](/zia/quarterly-business-review-report).

### Feature Available
#### Rate Limit for Exporting Logs to a CSV File
There is now a limit to the number of times (20 requests/hour) you can export Web, Mobile, Firewall, DNS, and Tunnel Insights Logs.
To learn more, see [Ranges & Limitations](/zia/ranges-limitations#Reporting) and [About Insights Logs](/zia/about-insights-logs).

## September 25, 2020
### Feature Available
#### Enhancement to Tenancy Restriction
Zscaler's tenancy restriction now allows you to create tenant profiles for cloud applications and associate them with cloud app control rules. This feature provides granular tenant restrictions for cloud applications, such as allowing multiple tenants for users, locations, or groups, etc.
You can create tenant profiles in the Administration > Tenant Profiles page.
Also, the tenancy restriction feature support is now extended to the following applications:
- [YouTube](#YouTube)
- [Slack](#slack)
- [Dropbox](#dropbox)
As part of this enhancement, the tenancy restriction of the following applications were moved to Administration > Tenant Profiles page from Policy > URL & Cloud App Control > Advanced Policy Settings page:
- [Google Apps (formerly Allowed Domains for Google Apps)](#Google)
- [Microsoft Login Services (formerly Enable Microsoft 365 Tenant Restriction)](#microsoft-login-service)
Any existing tenancy restriction rules related to Microsoft 365, Google Apps, or YouTube for Schools Filter for your organization were automatically migrated, by creating and associating the tenant profiles for the respective apps.
[]This feature allows you to provide access to specific content on YouTube.
You can use the following YouTube configurations to provide access to your organization-specific content:
- [Channels](#channels)
- [Categories](#categories)
- [School ID](#school-id)
To learn more, see [Adding a Tenant Profile](/zia/adding-tenant-profiles) and [Adding a Streaming Media Rule for Cloud App Control](/zia/adding-streaming-media-rule-cloud-app-control).
[]This feature allows you to provide access only to your organizations' Slack channels. You can achieve this by providing your workspace ID (team ID) and the allowed workspace IDs (e.g., T2DQ3J9AA).
To learn more, see [Adding a Tenant Profile](/zia/adding-tenant-profiles) and [Adding a Collaboration & Online Meetings Rule for Cloud App Control](/zia/adding-collaboration-online-meetings-rule-for-cloud-app-control).
[]This feature allows you to provide access either to your work Dropbox account, personal Dropbox account, or both. You can achieve this by providing the allowed Dropbox team IDs (e.g., 4875936).
To learn more, see [Adding a Tenant Profile](/zia/adding-tenant-profiles) and [Adding a File Sharing Rule for Cloud App Control](/zia/adding-file-sharing-rule-cloud-app-control).
[]This feature allows you to provide access to Google applications for the added domains (e.g., zscaler.com).
To learn more, see [Adding a Tenant Profile](/zia/adding-tenant-profiles).
[]This feature allows you to provide access to Microsoft applications. You can achieve this by providing the tenant directory and the allowed Microsoft 365 tenants (corp1.safemarch.com).
To learn more, see [Adding a Tenant Profile](/zia/adding-tenant-profiles) and [Adding an IT Services Rule for Cloud App Control](/zia/adding-it-services-rule-cloud-app-control).
[]This allows you to restrict access only to the contents of certain YouTube channels by using the respective YouTube channel IDs (e.g., UCSylwuqCXM_W13ARfzASm3Q).
[]This allows you to restrict access only to the contents of the following YouTube categories based on your selection:
- Action/Adventure
- Anime/Animation
- Autos & Vehicles
- Classics
- Comedy
- Documentary
- Drama
- Education
- Entertainment
- Family
- Film & Animation
- Foreign
- Gaming
- Horror
- Howto & Style
- Movies
- Music
- News & Politics
- Nonprofits & Activism
- People & blogs
- Pets & Animals
- Science & Technology
- Sci-fi/Fantasy
- Shorts
- Short Movies
- Shows
- Sports
- Thriller
- Trailers
- Travel & Events
- Videoblogging
[]This allows you to restrict access only to educational videos selected by your school by using the school ID.

### Feature Available
#### Enhancement to URL Filtering and Cloud App Control Rules
The new Rule Expiration feature allows you to specify the validity period for a URL Filtering policy rule or Cloud App Control policy rule. This feature provides a control, Enable Rule Expiration, that allows you to set the start date and time, end date and time, and time zone in which the rule is valid.
[See image.](#rule-expiraation)
To learn more, see [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Adding Rules to the Cloud App Control Policy](/zia/adding-rules-cloud-app-control-policy).
This functionality is also available via our cloud service API. To learn more, see the [API Reference](/zia/about-api).
[]![Screenshot of the Add URL Filtering Rule page.](/sites/default/files/downloads/zia/documentation-knowledgebase/policies/url-filtering/configuring-url-filtering-policy/ZIA-Rule-Expiration.png)

### Feature Available
#### Enhancements to TLD Categories Page
The Top Level Domains column in the TLD Categories page was renamed to No. of Top Level Domains. It displays the total number of Top Level Domains under the respective TLD categories.
You can view up to 20 TLDs when you click the number under this column.
To learn more, see [About TLD Categories](/zia/about-tld-categories).

## September 18, 2020
### Feature Available
#### Enhancement to AI/ML-Based Content Categorization
The AI/ML-based content categorization feature support is now extended to cover other URL categories so that the URL filtering rules are applied to most of your organizations' traffic.
As part of this enhancement, the AI/ML-based content categorization support is extended for the following additional URL categories:
- Alcohol/Tobacco
- Anonymizer
- Art/Culture
- Blogs
- Classifieds
- Continuing Education/College
- Dining/Restaurant
- FileHost
- Finance
- Government
- Job/Employment Search
- K-12
- Online Auctions
- Online Shopping
- Radio Stations
- Real Estate
- Social Networking
- Special Interests/Social Organizations
- Travel
- Vehicles
To learn more, see  [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings#Dynamic).

## September 11, 2020
### Feature Available
#### DLP & EDM Support for Thai National Identity Card Numbers
A new predefined dictionary, Identity Card Number (Thailand), was added. This dictionary detects national identity card numbers from Thailand.
When creating your EDM templates, you can also select Identity Card Number (Thailand) as a Data Type.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries) and [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### Enhancements to Cloud App Categories
The following predefined cloud app categories were updated in the Cloud App Control Policy page:
- Collaboration & Online Meetings: The new cloud app Amazon Chime was added to this category.
- File Sharing: The new cloud app TagMyDoc was added to this category.
- Productivity & CRM Tools: The new cloud app ServiceNow was added to this category.
- Streaming Media: The new cloud app Sohu TV was added to this category.
- Webmail: The new cloud app QQMail was added to this category.
- Hosting Providers: The new cloud apps Tencent Cloud and OVHcloud were added to this category.
To learn more, see [About Cloud App Categories](/zia/about-cloud-app-categories).

### Feature Available
#### Sandbox Machine Learning Prescanning
Zscaler now supports machine learning-based intelligence to enhance Sandbox quarantining. If you have Sandbox rules configured to quarantine unknown files for the first-time action, you now can enable machine learning prescanning to detect and predict the likelihood of malware for unknown files while they undergo Sandbox analysis. Suspicious  files will be held in quarantine until there is a verdict from the Sandbox analysis. Benign files will be released from quarantine and allowed to download while the Zscaler service continues to perform Sandbox analysis.
[See image.](#sandbox-ml)
To learn more, see [Configuring the Sandbox Policy](/zia/configuring-sandbox-policy).
[]![Screenshot highlighting the Machine Learning Prescanning setting in the Add Sandbox Rule window.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/zia-add-sandbox-rule-machine-learning-prescanning-field.png)

## August 28, 2020
### Feature Available
#### Firewall Threat Logging with IPS
Detected Firewall threats are now logged in Firewall Insights > Logs. You can use the filters to find the logged results of the chosen threat categories configured in your IPS Control Policy.
To learn more, see [About IPS Control](/zia/about-ips-control) and [Configuring IPS Control Policy](/zia/configuring-ips-control-policy).

### Feature Available
#### Support for Source IP Anchoring
Some cloud applications or web services restrict access to them based on the source IP from which the traffic originates. The Source IP Anchoring feature caters to such needs where access to applications requires your traffic to egress with a pre-registered unique IP address, which mostly belongs to your organization.
This feature allows you to steer the traffic processed by ZIA back to your network and egress using an IP address of your choice. To achieve this, you can configure granular policies on the ZIA Admin Portal to selectively forward certain application traffic to the appropriate destination servers via the ZPA App Connectors of your choice. Zscaler ensures that the traffic is processed and secured before forwarding the traffic.
To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring).
This feature can be enabled upon request after specific criteria are met. For more information, contact your Zscaler Account team.

## August 14, 2020
### Feature Available
#### Configuring DLP Policy Rules to Match Only Specified Engines
The DLP policy was enhanced to support the ability to configure a rule that only triggers when transactions match the DLP engines specified in the rule, and doesn’t match any other engines from different rules. This ability allows you to influence how the DLP policy evaluates all of its rules and prevent a user from leaking sensitive data when sending out non-sensitive data. You can do this by selecting the Match Only option when configuring a DLP rule that allows transactions that match its criteria.
[See image.](#match-only-image)
To learn more, see [DLP Policy Configuration Example: Match Only](/zia/dlp-policy-configuration-example-match-only) and [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection).
[]![The Match Only option for DLP Policy Rules](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-DLP-Engines-Match-Only_0.png)

### Feature Available
#### Enhancement for Custom DLP Dictionaries
Zscaler now allows you to configure Patterns & Phrases type DLP dictionaries with the Boolean operators All and Any (i.e., AND and OR). Prior to this release, Patterns & Phrases type dictionaries triggered based on OR operator logic only.
The Any operator is the default setting for Patterns & Phrases type dictionaries. When you create a dictionary with this operator, the dictionary triggers when a transaction matches any one of the dictionary’s patterns or phrases.
When you create a dictionary with the All operator, the dictionary only triggers when a transaction matches all of the dictionary’s patterns and phrases. This allows you to create a dictionary that detects specific patterns and phrases, and decreases the number of custom dictionaries you must create.
[See image.](#image)
To learn more, see [Adding Custom DLP Dictionaries](/zia/adding-custom-dlp-dictionary).
[]![The Match Type option for Pattern & Phrases type DLP dictionaries](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-DLP-dictionary-Match-Type.png)

### Feature Available
#### New DLP Dictionary
We have added one new predefined DLP dictionary: Aadhaar Card Number (India). This dictionary detects Aadhaar unique identification (UID) numbers from India.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).

### Feature Available
#### New EDM Data Type
When creating your EDM templates, you can now select Aadhaar Card Number (India) as a Data Type.
To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template).

### Feature Available
#### Zscaler Identity Proxy Support for Microsoft 365
Zscaler now supports configuring Identity Proxy for Microsoft 365 cloud apps from the **Administration **>** Identity Proxy Settings** page of the ZIA Admin Portal. You can also now create multiple instances of the supported cloud apps.
[See image.](#add-cloud-app)
To learn more, see [About Identity Proxy Settings](/zia/about-identity-proxy-settings).
[]![Screenshot of Add Cloud Application for Office 365](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Add-Cloud-Application-Office-365-IdP.png)

### Feature Available
#### Zscaler Incident Receiver
The Zscaler Incident Receiver is an on-premises tool that allows you to securely receive information about DLP policy violations. The Zscaler service sends information about policy violations via ICAP to the incident receiver. This tool sends the policy-violating content and a JSON file containing the DLP policy scan metadata (e.g., the URL, DLP dictionaries, DLP engines, etc.). The incident receiver is only available for organizations that do not already own an ICAP server.
[See image.](#zscaler-incident-receiver-image)
To learn more, see [About Zscaler Incident Reciever](/zia/about-zscaler-incident-receiver).
[]![Zscaler Incident Receiver](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Zscaler-Incident-Receiver.png)

## July 31, 2020
### Feature Available
#### Converting Admins to Users
When deleting admins, you now can decide to keep them as users or delete them entirely from your organization.
[See image.](#rns)
To learn more, see [Deleting Admins](/zia/deleting-admins).
[]![Screenshot of the Confirm Changes window in Edit Administrators.](/downloads/zia/release-notes/release-upgrade-summary-2020/zia-edit-administrators-confirm-changes-window.png)

### Feature Available
#### Enhancement to the URL Categories Page
The following updates were made to the URL Categories page:
- The page header displays the number of Predefined and Custom URL categories that are available.
- The following columns display the number of values under the respective fields of the URL categories:
- No. of Custom URLs
- No. of URLs retaining parent category
- No. of Custom Keywords
- No. of Keywords retaining parent category
You can view up to 20 values when you click the number under respective column.
- The following filters are now introduced for the URL categories search:
- URL
- Keyword
- URL Category Name
- All
The search result displays the URL categories with the number of matching terms under the respective fields.
To learn more, see [About URL Categories](/zia/about-url-categories).

## July 24, 2020
### Feature Available
#### SaaS Security API
The following enhancements are now available for SaaS Security API.
New SaaS Application Support
You can now configure tenants for the following SaaS applications:
- Dropbox
- Gmail
- Google Drive
- Microsoft Exchange
[See image.](#newapps)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to the SaaS Application Tenants
You can now optionally add external trusted domains and users for email application tenants (e.g, Exchange and Gmail).
[See image.](#external)
To learn more, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants).
Updates to SaaS Security API Policies & Scan Configuration
You can now configure the SaaS Security API policies and scan schedules for email applications. Prior to this release, the policies and scan schedules were configurable for file sharing applications only.
You can also configure Data Loss Prevention (DLP) policy exceptions for both file sharing and email applications.
[See image.](#policy-image)
To learn more, see [Configuring SaaS Security API Policies](/zia/configuring-saas-security-api-policies).
Updates to the SaaS Security Report
There are new layout and widget updates to the SaaS Security Report for a better summary of SaaS Security API-based discovery and remediation activities.
[See image.](#casb-report)
To learn more, see [SaaS Security Report](https://help.zscaler.com/zia/saas-security-report).
Updates to SaaS Security Insights & Insights Logs
The SaaS Security Insights and Insights Logs have new filters, and a new section called Application Category to help you filter logs and scans by application category (File or Email).
[See image for Insights.](#casb-insights)
[See image for Insights Logs.](#casb-insights-logs)
To learn more, see [SaaS Security Insights](https://help.zscaler.com/zia/saas-security-insights) and [SaaS Security Insights Logs](https://help.zscaler.com/zia/saas-security-insights-logs).
[]![Screenshot highlighting all the supported SaaS applications, including the new ones.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Choose-SaaS-Application-Provider-release-notes.png)
[]![Screenshot highlighting the (Optional) Configure External Trusted Domains & Users for the Tenant step when adding SaaS application tenants.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/zia-optional-configure-external-trusted-domains-users-tenant-exchange-release-notes.png)
[]![DLP-Policy-Email-Applications.png](/sites/default/files/downloads/DLP-Policy-Email-Applications.png)
[]![Screenshot of the SaaS Security Report and its widgets in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-SaaS-Security-Report-v2.png)
[]![Screenshot of the SaaS Security Insights page with each part labeled](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-SaaS-Security-Insights-v2.png)
[]![Screenshot of the SaaS Security Insights Logs page with labeled parts in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-SaaS-Security-Logs-v2.png)

## July 17, 2020
### Feature Available
#### Cloud Application Trend Widget: Support for 1000 Applications
The Cloud Application Trend widget in the Cloud Applications dashboard now supports a listing of 1,000 applications. Also, the **Name **column on the widget is now searchable.
[See image.](#cloud-app-widget)
To learn more, see [About Dashboards](/zia/about-dashboards).
[]![Screenshot of the Cloud Application Trend widget in the Cloud Applications dashboard](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-Cloud-App-Trend-Widget.png)

### Feature Available
#### Flexible Regular Expression Support for DLP Patterns
Zscaler DLP patterns were enhanced to support more flexible regular expressions. This flexibility enables an admin to write more accurate regular expressions, thereby reducing the number of false positives. These enhancements include flexibility in the base token (or first character) of a regular expression. The base token enhancements provide support for:
- Special Characters - The base token can be any special character such as, at sign (@), number sign (#), dollar sign ($), and others, for example, `%abc`, `[%@#]abc`
- Shorthand Characters - The base token can be a shorthand character like a word boundary (`\b`) or space (`\s`), for example, `\sabc`, `\babc`
- Shorthand Character Followed by a Special Character - The base token can be a shorthand character followed by a special character, for example, `\b%abc`, `\s[%@]abc`
- Nested Shorthand Characters  - The base token can have up to 2 nested shorthand characters, for example, `\b\sabc`, `\b[\s\W]abc`
In custom DLP dictionaries, the implicit references for a word boundary (`\b`) at the beginning of every pattern was removed. So, in order to maintain functionality for existing DLP patterns configured in the ZIA Admin Portal, all patterns were modified to explicitly include `\b` at the beginning. For example, a previously configured DLP pattern for a phone number using digits would appear as follows:
[2-9]\d{2}\)?[-. ][2-9]\d{2}[-. ]\d{4}
This pattern was modified to:
\b([2-9]\d{2}\)?[-. ][2-9]\d{2}[-. ]\d{4}
To learn more, see [Defining Patterns for Custom DLP Dictionaries](/zia/defining-patterns-custom-dictionaries).

### Feature Available
#### Simplifying Support for Multiple IPSec Tunnels to Zscaler Cloud with NAT-Traversal
This capability simplifies the deployment of multiple IPSec tunnels for branches/data centers that need more than 1Gig throughput. Enabling NAT-Traversal (NAT-T) takes away the need to create a unique public IPv4 for each IPSec tunnel. With this capability, you can deliver multiple IPSec tunnels using a single public IPv4 address.

## July 03, 2020
### Feature Available
#### Azure Virtual WAN (VWAN) Partner Integration
Zscaler's integration leverages Microsoft's Azure VWAN APIs to discover and configure Azure hubs. The integration provides a one-click configuration to create outbound IPSec tunnels from Azure hubs to Zscaler data centers.
[See image.](#vwan-config)
To learn more, see [Configuring a Microsoft Azure Virtual WAN Integration](/zia/configuring-microsoft-azure-virtual-wan-integration) and [Configuring Azure Virtual WAN Locations](/zia/configuring-azure-vwan-locations).
[]![Azure Virtual WAN page within the ZIA Admin Portal ](/downloads/zia/documentation-knowledgebase/release-notes/57-release/57-release-upgrade-summary/zia-azurevwan-relnotes.png)

### Feature Available
#### Carbon Black Partner Integration
VMware Carbon Black integration using the Carbon Black endpoint protection platform allows immediate visibility, and containment for advanced persistent threats detected in the Cloud Sandbox. Through API integration between Zscaler and Carbon Black, malware detected by the Zscaler cloud sandbox is correlated with Carbon Black endpoint data to identify all endpoints with this file present. Malware can spread laterally across endpoints via malware propagation vectors such as USB or Bluetooth file transfer.
The integration presents Zscaler's patient 0 alerting and reporting alongside a list of identified Carbon Black endpoint devices, enabling admins to quickly assess the impact to the endpoint environment and take action. In addition, an admin can enact an endpoint containment request from the ZIA Admin Portal to the Carbon Black platform for further investigation and remediation. These automated workflows reduce the threat dwell time and the time to remediation for advanced threats including zero-day threats.
[See image.](#carbon-black)
To learn more, see [Zscaler and VMware Carbon Black Deployment Guide](/zscaler-technology-partners/zscaler-and-vmware-carbon-black-deployment-guide).
[]![Screenshot of the Carbon Black tab on the Partner Integrations page.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Partner-Integrations-Carbon-Black-tab.png)

### Feature Available
#### New Data Types in Web, DNS, and Firewall Insights
The following are new data types in Web, DNS, and Firewall Insights:
- Web Insights
- Client External IP
- Client IP
- File Name
- File Type
- Server IP
- Threat Name
- DNS Insights
- Server IP
- Firewall Insights
- Threat Name
- Client Server IP
- Server Destination IP
For these data types, you can choose to view the top 5, 10, 25, 50 or 100 items.
To learn more, see [About Insights](/zia/about-insights).

### Feature Available
#### New Interactive Report: Top Threat Names
The Top Threat Names report shows you the top threat names for Web and Firewall (if you are not subscribed to either service, the widgets will show you as unsubscribed). These widgets cannot be used to create a custom report.
[See image.](#topthreatnames)
To learn more, see [About Interactive Reports](/zia/about-interactive-reports).
[]![Screenshot of the Top Threat Names report in the Interactive Reports page](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-Top-Threat-Names.png)

## June 26, 2020
### Feature Available
#### UCaaS One Click Configuration
Unified Communications as a Service (UCaaS) is a cloud delivery model that offers communications and audio/video-based collaboration services. Zscaler now enables direct-to-cloud access for the UCaaS applications Zoom, LogMeIn, and RingCentral by enabling organizations to send traffic directly to application servers over the internet, instead of backhauling traffic over costly MPLS circuits.
[See image.](#ucaas)
To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings).
[]![Screenshot of the UCaaS section in the Advanced Policy Settings section of the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-UCaaS.png)

## June 12, 2020
### Feature Available
#### Support for Third-Party Proxy Chaining
Zscaler can now successfully integrate with third-party services, which some organizations may want to use for additional layers of security or compliance purposes, by acting as a child proxy or a down-stream proxy. This feature uses forwarding policies to define the traffic that needs to be forwarded to a third-party proxy service of your choice.
To learn more, see [About Third-Party Proxy Chaining](/zia/about-third-party-proxy-chaining).

## May 01, 2020
### Feature Available
#### Enhancements to Virtual ZENs and Virtual Service Edges
ZIA Virtual ZEN and Virtual Service Edge now support Microsoft Azure Hypervisor. You can now create Virtual ZEN or Virtual Service Edge virtual machines (VMs) in the Azure cloud and associate them to an Azure load balancer.
To learn more, see [Configuring VZEN](/zia/configuring-vzen-microsoft-azure) and [Configuring Virtual Service Edge](/zia/configuring-virtual-service-edge-microsoft-azure) for Microsoft Azure.

## April 10, 2020
### Feature Available
#### SaaS Security API
SaaS Security API provides visibility and security for sanctioned SaaS applications. To get started, you can configure SaaS application tenants, and configure SaaS Security API policies to inspect content from the tenants. You can then view the results through the SaaS Security Report and Insights pages.
SaaS Application Tenants
You can now integrate sanctioned SaaS applications with the Zscaler service by adding them as tenants. On the SaaS Application Tenants page, you can see general information about each integrated tenant.
[See image.](#saas-app-tenants)
To learn more, see [About SaaS Application Tenants](https://help.zscaler.com/zia/about-saas-application-tenants).
SaaS Security API Policies & Scan Configuration
You can configure two types of policies and configure scan schedules to protect data at rest for your organization’s SaaS applications tenants:
- Data Loss Prevention (DLP): This policy uses Zscaler’s DLP engines to discover and protect sensitive data at rest.
[See image.](#dlp)
- Malware Detection: This policy discovers and prevents threats to data at rest. You can also configure exceptions for this policy.
[See image.](#malware)
- Scan Configuration: Configure scan schedules for the DLP and Malware Detection policies to inspect data at rest.
[See image.](#scan)
To learn more, see [Configuring SaaS Security API Policies](/zia/configuring-saas-security-api-policies).
SaaS Security Report
The SaaS Security Report provides a summary of SaaS Security API-based discovery and remediation activities. This serves as the starting point when investigating what data is affected and identifying risky users.
[See image.](#report)
To learn more, see [SaaS Security Report](https://help.zscaler.com/zia/saas-security-report).
SaaS Security Insights & Insights Logs
The SaaS Security Insights and Insights Logs pages are where you can further research the API discovery and remediation results from the SaaS Security Report. You can analyze the logs and summary charts to further understand how data at rest in SaaS applications is being protected.
[See image for Insights.](#insights)
[See image for Insights Logs.](#logs)
To learn more, see [SaaS Security Insights](https://help.zscaler.com/zia/saas-security-insights) and [SaaS Security Insights Logs](https://help.zscaler.com/zia/saas-security-insights-logs).
NSS Feeds for SaaS Security Logs
You can now add NSS feeds for SaaS Security Logs.
[See image.](#nss-feed-saas)
To learn more, see [Adding NSS Feeds for SaaS Security Logs](https://help.zscaler.com/zia/adding-nss-feeds-saas-security-logs).
NSS Feed Output Format for SaaS Security Logs
You can now add SaaS Security log fields to the field output format in NSS Feeds.
To learn more, see [NSS Feed Output Format: SaaS Security Logs](https://help.zscaler.com/zia/nss-feed-output-format-saas-security-logs).
[]![Screenshot of the SaaS Application Tenants page in the ZIA Admin Portal.](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-SaaS-Application-Tenants-page.png)
[]![SaaS-dlp-release-notes.png](/sites/default/files/downloads/SaaS-dlp-release-notes.png)
[]![SaaS-malware-release%20notes.png](/sites/default/files/downloads/SaaS-malware-release%20notes.png)
[]![SaaS-scan-release-notes.png](/sites/default/files/downloads/SaaS-scan-release-notes.png)
[]![Screenshot of the SaaS Security Report and its widgets in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/6.0-SaaS-Security-Report.png)
[]![Screenshot of the SaaS Security Insights page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-SaaS-Security-Insights.png)
[]![Screenshot of the SaaS Security Insights Logs page in the ZIA Admin Portal](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-SaaS-Security-Insights-Logs.png)
[]![Screenshot of the Add NSS Feed window with the Log Type as SaaS Security API](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-NSS-Feed-SaaS-Security.png)

## March 20, 2020
### Feature Available
#### Cloud App Categories Enhancements
The following new predefined cloud app categories were added to the Cloud App Control Policy page:
- [DNS Over HTTPS Services](#DOH)
- [Human Resources](#human-resources)
The following predefined cloud app categories were updated in the Cloud App Control Policy page:
- [Collaboration and Online Meetings](#collaboration-online-meetings)
- [Consumer](#Consumer)
- [File Sharing](#File-share)
- [Hosting Providers](#hosting-provider)
- [Instant Messaging](#instant-messaging)
- [Productivity & CRM Tools](#productivity-CRM-tools)
- [Sales & Marketing](#sales-marketing)
- [Social Networking](#social-networking)
- [Streaming Media](#streaming-media)
- [System & Development](#system-development)
To learn more, see [About Cloud App Categories](/zia/about-cloud-app-categories).
[]It includes the DNS server applications that support DNS resolution using the HTTPS protocol.
[]It includes applications that support the management of employee-related resources.
[]The following new cloud apps were added to this category:
- Best Buy
- Ikea
- Te Connectivity
- Wayfair
[]The following new cloud apps were added to this category:
- Asana
- Google Calendar
- Google Jamboard
- Google Keep
- Google Meet
- Google Sites
- Monday
- Smartsheet
- Trello
- Wrike
[]The following new cloud apps were added to this category:
- 500px
- CasImages
- Files Anywhere
- ImageShack
- Mimedia
- MyAirBridge
- Photoshelter
- PicDrop
- SmugMug
[]The new cloud app Linode was added to this category.
[]The cloud app Google Talk in this category was renamed to Google Hangouts.
[]The following new cloud apps were added to this category:
- Adobe Creative Cloud
- Adobe Document Cloud
- Agile CRM
- Camcard Business
- Freshdesk
- Freshsales CRM
- Greyhound
- GumGum
- Hotjar
- Kustomer
- LiveAgent
- Looyu
- Pega
- Pipedrive
- SAP Concur
- Sentry
- SurveyMonkey
- Totango
- Vision Critical
- Xero
[] The following new cloud apps were added to this category:
- Bouncex
- ZoomInfo
[]The following new cloud apps were added to this category:
- Badoo
- Glassdoor
- Taringa
- Tinder
[]The following new cloud apps were added to this category:
- Disney Plus
- Plex TV
[] The following new cloud apps were added to this category:
- Adobe Business Catalyst
- Apple Developer
- Azure DevOps
- Canva
- Firebase
- Google App Maker
- Google Developer
- Jimdo
- Microsoft Powerapps
- Mit app inventor
- Source forge
- Square space
- Voog
- Wix

### Feature Available
#### Cloud Application Dashboard Enhancement
Zscaler has extended our partnership with Bitglass, so you can now view the Bitglass cloud application risk score information per cloud application under the Dashboard > Cloud Application page.
[See image.](#Bitglass-cloud-app-risk-score)
To learn more, see [About Dashboards](/zia/about-dashboards).
[]![Screenshot of Bitglass cloud application risk score information](/sites/default/files/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/ZIA-Bitglass-cloud-application-risk-score-information.png)

### Feature Available
#### CrowdStrike Partner Integration
Zscaler's integration leverages CrowdStrike APIs to provide endpoint detection and response visibility for Sandbox detected malware. Once the integration is configured, the Zscaler service calls the CrowdStrike Falcon API and requests information for endpoints that have been exposed to the malicious file.
[See image.](#crowdstrike)
To learn more, see [Integrating with CrowdStrike](/zia/integrating-crowdstrike).
[]![Screenshot of the new CrowdStrike tab on the Partner Integrations page.](/sites/default/files/downloads/zia/partner-integrations/configuring-crowdstrike-integration/ZIA-Partner-Integrations-CrowdStrike-Tab-Release.png)

### Feature Available
#### Enhancement to Location Groups
[Watch a feature video about Location Groups](https://fast.wistia.net/embed/iframe/rxlkzf3gpy)
You can now create two types of location groups: manual location groups or dynamic location groups.
When creating a manual location group, you can manually assign any number of locations or sub-locations to it.
When creating a dynamic location group, you select the location attributes that locations or sub-locations must match to be assigned to the group. A dynamic group automatically updates to include any matching locations or sub-locations.
[See image.](#location-groups-image)
To learn more, see [About Location Groups](/zia/about-location-groups).
[]![release-note-image.png](/sites/default/files/downloads/release-note-image.png)

### Feature Available
#### Firewall Network Applications Enhancements
The following network applications were added under their respective firewall network applications' categories in the Network Applications page:
- Files Anywhere under the Streaming Media category.
- Glassdoor under the Social Networking category.
- Google Keep under the Enterprise category.
- Mimedia under the Streaming Media category.
- RingCentral under the Streaming Media category.
- Sharefile under the Streaming Media category.
- Tinder under the Social Networking category.
- Zoominfo under the Business category.
The following network applications were renamed in the Network Applications page:
- Acrobat to Adobe Creative Cloud under the Business category.
- 2CH to CH under the Social Networking category.
- about.com to Dotdash under the Web category.
To learn more, see [About Network Applications](/zia/about-network-applications).
After the cloud upgrade, the newly added network applications will be displayed under their respective firewall network applications' category. These categories are in preview at this time and are not yet available for use. These categories will become available after all Zscaler clouds have been upgraded. A follow-up notification will be sent at that time.

### Feature Available
#### FQDN Support in NSS Feeds
NSS feeds now support an FQDN as the destination (for the TCP connection), in addition to the existing destination IP address. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry.
[See image.](#FQDN)
To learn more, see [Adding NSS Feeds](/zia/adding-nss-feeds).
[]![Screenshot of the Add NSS Feed window in the ZIA Admin Portal with the FQDN fields highlighted](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-6.0-NSS-Feed-FQDN.png)

### Feature Available
#### Identity-based Block Override
You can allow authorized users to provide temporary access to blocked pages by using their company provided login credentials such as the single sign-on (SSO) credentials. You can do this by enabling the Enable Identity-based Block Override option under the Policy > URL & Cloud App Control > Advanced Policy Settings tab.
[See image.](#enable-identity-based-block-override)
To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings).
[]![Screenshot of the Enable Identity-based Block Override option in the Advanced Policy Settings page.](/sites/default/files/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/how-do-i-configure-advanced-url-policy-settings/Advanced-policy-settings-enable%20identity-based%20block%20override-option-v6.0.png)

### Feature Available
#### Increase to Total Cell Usage for EDM Templates
EDM templates now support a maximum of 5 billion cells.
To learn more, see [About Index Templates](/zia/about-index-templates).

### Feature Available
#### Independent Firewall Evaluation for HTTP Tunnel Connections
Zscaler now allows Firewall policies to evaluate inner and outer 5-tuples of HTTP tunnel connections independently. Zscaler removes the HTTP CONNECT request from the outer tunnel and then applies the firewall policies to the request inside the HTTP connect tunnel. This means that any 5-tuple that results in a blocking policy will block the corresponding session.
The new predefined firewall filtering rule, [Zscaler Proxy Traffic](/zia/about-predefined-firewall-filtering-rules#zscaler-proxy-traffic), ensures that the HTTP Tunnel connections with independent firewall evaluation do not impact your firewall filtering rules.
If your organization is provisioning Firewall for the first time, then Zscaler Proxy Traffic takes one of the following admin rank values based on the scenario:
- 0 - when there is at least one admin with rank 0 in your organization.
- 7 - when there is no admin with rank 0 in your organization.
If your organization has provisioned Firewall previously and if no admin had ever logged into the Admin Portal, then Zscaler Proxy Traffic takes the admin rank of the admin who first logs into the Admin Portal.
To learn more, see [Firewall HTTP TUNNEL Connectivity](/zia/firewall-http-tunnel-connectivity).

### Feature Available
#### Multiple Identity Provider Support for SAML
[Watch a feature video about Multiple IdP Support for SAML](https://fast.wistia.net/embed/iframe/kp6mmq2k3l)
You can now configure multiple identity providers when configuring SAML single sign-on for users.
[See image.](#multiple-idp)
To learn more, see [About Identity Providers](/zia/about-identity-providers).
[]![Screenshot of the new Identity Providers page in the ZIA Admin Portal.](/sites/default/files/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/about-identity-providers/ZIA-Identity-Providers-Tab.png)

### Feature Available
#### New Default Admin Naming Convention
There is a new naming convention for default admins. The previously used default admin account will be deprecated in the future.
[See image.](#default-admin)
To learn more, see [About Administrators](/zia/about-administrators).
[]![Screenshot highlighting the DEFAULT ADMIN and DEFAULT ADMIN (Deprecated).](/sites/default/files/downloads/zia/authentication-administration/administrator-role-management/administrators/about-administrators/ZIA-Default-Admin-Release.png)

### Feature Available
#### New DLP Dictionaries
We have added five new predefined DLP dictionaries:
- Identity Card Number (China): This dictionary detects Resident Identity Card numbers from China.
- National Identification Card Number (Taiwan): This dictionary detects national identification card numbers from Taiwan.
- National Identification Number (France): This dictionary detects INSEE numbers from France.
- National Identification Number (Spain): This dictionary detects national identity card numbers (DNI) from Spain.
- Resident Registration Number (Korea): This dictionary detects resident registration numbers (RRN) from South Korea.
To learn more, see [Editing Predefined DLP Dictionaries](/zia/editing-predefined-dlp-dictionaries).

### Feature Available
#### New EDM Data Types
When creating your EDM templates, you can now select Identity Card Number (China), National Identification Card Number (Taiwan), National Identification Number (France), National Identification Number (Spain), and Resident Registration Number (Korea) as Data Types.
To learn more, see [Creating an Exact Data Match Template.](/zia/creating-exact-data-match-template)

### Feature Available
#### SSL Policy Evaluation and Logging Improvements
SSL policy evaluation and logging have been enhanced to give you a consistent and clear behavior under different traffic forwarding methods, SSL inspection scenarios (i.e., enabled, disabled, disable and show end user notification), and policy actions.
[See image.](#SSLPolicyEvalimage)
Following is a summary of the policy evaluation and logging improvements:
- CONNECT requests to a ZIA Public Service Edge (formerly Zscaler Enforcement Node or ZEN) gets evaluated and the protocol is recorded as HTTP-PROXY, which was earlier evaluated and recorded either as HTTPS or SSL.
- Another round of policy evaluation is done on the Client Hello SNI in addition to the evaluation on the CONNECT request.
- When the SSL connection is not inspected, a single web log is recorded with the protocol SSL to represent the aggregate traffic transferred within that connection. Because the weblog record represents an SSL connection, the URL policy ignores the request method criteria and it is recorded as N/A.
- When the SSL connection is inspected, a web log record is not recorded to represent the full connection. The protocol is recorded as HTTPS for the individual HTTPS transaction records only.
- In transparent proxy mode, when an SSL connection is not inspected, the request method is evaluated as Any and recorded as N/A, which was recorded as CONNECT earlier.
- URL filtering policy support for the common HTTP request methods, such as PUT, POST, GET, etc. was added. This, in combination with the HTTP-PROXY special protocol, allows you to define a policy that blocks CONNECT requests to third-party proxies without interfering with the CONNECT requests to Zscaler.
- The protocol negotiated under the ALPN (Application-Layer Protocol Negotiation) TLS extension is now recorded in a dedicated web log field for non-SSL inspected traffic.
- The protocol for binary data (an undecodable protocol by Zscaler) inside an inspected SSL connection is now evaluated and recorded as TUNNEL-SSL to distinguish it from the binary data after a CONNECT request.
- The ZIA Public Service Edge now evaluates policies on CONNECT requests generated by Zscaler Client Connector (Z-Tunnel 1.0) destined to an IP address, <IP>:443, which were previously exempted from SSL inspection and policy enforcement. As a result, if you have a default block policy for Miscellaneous URL category, you may notice some additional traffic getting blocked because most IP addresses typically fall under the Miscellaneous URL category.
To learn more, see [About Policy Enforcement](/zia/about-policy-enforcement#ssl).
[]![SSL Policy Evaluation Workflow](/downloads/zia/policies/about-policy-enforcement/ZIA-SSL-Policy-Evaluation.png)

### Feature Available
#### Support for AI/ML-Based Content Categorization
The Dynamic Content Categorization service can now analyze the content of uncategorized websites using AI/ML tools and categorize them under one of the super categories that support content categorization.
As part of this support, the following enhancements are included under the Policy > URL & Cloud App Control > Advanced Policy Settings page:
- The Enable Dynamic Content Categorization option is renamed to Enable AI/ML-based Content Categorization.
[See image.](#DCCimage)
- The content categorization support is extended for the following additional super categories:
- Games
- Health
- Religion
- Shopping and Auctions
- Sports
To learn more, see [Configuring Advanced URL Policy Settings](/zia/configuring-advanced-url-policy-settings#Dynamic).
[]![Screenshot of Advanced Policy Settings page showing Enable AI/ML based Content Categorization option](/sites/default/files/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/url-filtering/configuring-url-filtering/how-do-i-configure-advanced-url-policy-settings/zia-advanced-policy-settingsAI-ML_v6.0.png)

### Feature Available
#### Support for Multi-Selection with Exclusion Capability
[Watch a feature video about Multi-Selection with Exclusion Capability](https://fast.wistia.net/embed/iframe/dm14k68yew)
Zscaler now supports the selection of multiple values for reporting (i.e., Insights Logs, Interactive Reports, Dashboard) with certain filters. You can also choose to include or exclude the selected values.
[See image.](#multi-select-include-exclude)
Insights Logs also supports additional operators (i.e., Does Not Contain, Does Not Start With, Does Not End With, Is Null, Is Not Null) for filters that perform a string match, like Domain search.
[See image.](#operators)
To learn more, see [About Widgets](/zia/about-widgets) and [About Insights Logs](/zia/about-insights-logs).
[]![Screenshot of the New Widget window with multi-selected options within a filter](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-New-Widget-Multi-Select.png)
![Screenshot of an Insights page with the Include/Exclude option within the User filter](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Insights-Include-Exclude.png)
[]![Screenshot of an Insights Logs page with operators within a filter](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-Insights-Logs-Operators.png)

### Feature Available
#### Update to DLP Dictionaries and DLP Engines
[Watch a feature video about Reusable DLP Dictionaries](https://fast.wistia.net/embed/iframe/dbxa1p60p0)
You can now configure the match count when adding a DLP dictionary to a DLP engine, and specify a different value for this setting each time you add a dictionary to an engine. For example, you can create a DLP policy rule that blocks documents that have more than 5 credit card numbers, and another rule for alerts when a document has between one and 4 credit card numbers.
When configuring an engine, you can now combine dictionaries with Boolean operators to create a logical expression. This enhancement allows for more flexibility and clarity when combining dictionaries in an engine, and decrease the number of engines and DLP policy rules you must create.
[See image.](#dlp-engine-expression)
To learn more, see [Understanding DLP Engines](/zia/understanding-dlp-engines).
[]![ZIA-DLP-Engine-6.0.png](/sites/default/files/downloads/zia/release-notes/release-upgrade-summary-2020/ZIA-DLP-Engine-6.0.png)

### Feature Available
#### Updates to Cloud Service API
The following updates were made to the cloud service API:
- The following Location Management resources are now available:
- The following resources were updated and can now be used for location and sub-location management:
- `POST /locations`
- `POST /locations/bulkdelete`
- `PUT /locations/{locationsId}`
- `DELETE /locations/{locationId}`
- The following new resource allows you to get sub-location information based on the parent location's ID:
- `GET /locations/{locationId}/sublocations`
- The following Admin & Role Management resources are now available:
- `GET /adminRoles/lite`
- `GET /adminUsers`
- `POST /adminUsers`
- `PUT /adminUsers/{userId}`
- `DELETE /adminUsers/{userId}`
To learn more about each endpoint, see the [API Reference](/zia/api/) and [API Rate Limit Summary](/zia/api-rate-limit-summary).
The Postman collection was also updated to include new and updated resources. To learn more, see [Configuring the Postman REST API Client](/zia/configuring-postman-rest-api-client).

### Feature Available
#### URL Categories Enhancements
[Watch a feature video about URL Categories Enhancements](https://fast.wistia.net/embed/iframe/p22wn3vjxk)
The following updates were made to the URL Categories page:
- Added the following new predefined URL categories:
- DNS Over HTTPS Services: It includes the DNS server URLs that support DNS resolution using the HTTPS protocol.
- End-to-End encrypted Content: It includes sites that are encrypted end-to-end.
- Malicious TLDs: It includes the Top Level Domains (TLDs) that are known to serve malicious content.
- Marijuana: It includes sites that have anything to do with Marijuana.
- Online Trading, Brokerage, Insurance: It includes the sites that provide trading of securities and management of investment assets, insurance, financial investment strategies, quotes or investment news.
- Operating System and Software Updates: It includes the sites and links that are used for downloading operating systems such as Windows, iOS, etc. and software updates.
- Web Conferencing: It includes the URLs that assist in conducting video conferencing or provide software to enable virtual meetings.
- Renamed the following URL categories:
- Alternate Lifestyle to Lifestyle.
- Drugs to Other Drugs.
- Music to Music and Audio Streaming.
- Other Games to Online and Other Games.
- Streaming Media to Video Streaming.
To learn more, see [About URL Categories](/zia/about-url-categories).
After the cloud upgrade, these URL categories will be displayed within the ZIA Admin Portal. These categories are in preview at this time and are not yet available for use in implementing your policies. These categories will become available for setting and enforcing policies after all Zscaler clouds have been upgraded. A follow-up notification will be sent at that time.

### Feature in Limited Availability
#### Zscaler Remote Browser Isolation
Zscaler Remote Browser Isolation enables organizations using ZIA to enhance their security posture by creating an air-gap between their users and the web pages accessed on the internet, reducing the attack surface to virtually null.
To learn more, see [About the Zscaler Remote Browser Isolation Platform](/zia/about-browser-isolation).
To access this feature, contact your Zscaler Account Team.

## January 29, 2020
### Feature Available
#### New Zscaler Support Portal
Zscaler Customer Services is excited to announce our new Support Portal launching on February 8, 2020. This new portal will allow you to seamlessly submit tickets and monitor support cases with the Zscaler Support team. It offers improved system functionality and provides more channels through which you can interact with Support.
What are the key features?
- Personalization and engagement with your preferred channel of communication.
- Simplified case submission form.
- Intelligent ticket routing to a Zscaler subject matter expert.
- Omni-channel experience via phone, email, web, and in the future, chat.
- Single console to track all support tickets.
- Ability to add collaborators from your teams.
How does this affect you?
- We will switch to this portal on February 8, 2020, between 18:00 – 19:00 UTC; during this time you can [use phone support](https://help.zscaler.com/phone-support) to report any issue.
- Your personal and organization’s tickets can only be viewed by logging in to the ZIA Admin Portal.
- We will be migrating the last 12 months of cases from our current case system; closed tickets more than 12 months old will no longer be available.
Additional information can be found in the [Zscaler Subprocessor Notice](https://trust.zscaler.com/posts/4566) that was posted to the Zscaler Trust Portal on December 5, 2019.
- The way tickets are submitted will not change and you can still log and access tickets by:
- Logging in to your ZIA Admin Portal.
- Reporting an issue without logging in to the Admin Portal at: [https://help.zscaler.com/submit-ticket](https://help.zscaler.com/submit-ticket).
- Calling in for phone support. We have added new phone numbers for certain locations. These numbers can be found on our Zscaler Help Portal at: [https://help.zscaler.com/phone-support](https://help.zscaler.com/phone-support).
We look forward to launching this new portal on February 8, 2020, helping to resolve tickets at lightning speed, and ensuring you have a world-class Zscaler Support experience.

## January 24, 2020
### Feature Available
#### New Tunnel Logs Field for NSS Feed Output
The field `%d{recordid}` is now available when adding an NSS feed for tunnel logs.
To learn more, see [NSS Feed Output Format: Tunnel Logs](/zia/nss-feed-output-format-tunnel-logs).

### Feature Available
#### Obfuscating User Names in Remote Assistance
You can now choose to obfuscate user names or leave them visible when enabling Remote Assistance. Users with view-only or full access can edit this feature. For all SSO users, user names will be obfuscated automatically, and this default cannot be disabled.
[Show image.](#RemoteAssistanceImage)
To learn more, see [Enabling Remote Assistance](/zia/enabling-remote-assistance).
[![Remote Assistance Enabling Options](/sites/default/files/downloads/zia/troubleshooting/enabling-remote-assistance/RemoteAssistance_UserNameObfuscation_Mockup_callout.png)
]

## January 10, 2020
### Feature Available
#### CIPA Compliance Enhancement
Two new predefined URL categories, Alcohol/Tobacco, and Newly Registered Domains are added to the CIPA Compliance Rule. You can also now add custom URLs to any of the predefined categories under the URL super category, Legal Liabilities. All these predefined categories are included by default in the CIPA Compliance Rule when it's activated for the first time.
The custom categories under Legal Liabilities are not included in the CIPA Compliance Rule.
To learn more, see [About CIPA Compliance](/zia/about-cipa-compliance#view-CIPA-comp-rule).

### Feature Available
#### Virtual ZENs or Virtual Service Edges
The Admin Portal now displays either Virtual ZENs or Virtual Service Edges under the Administration > Cloud Configuration page based on your subscription. For example, if you purchased a subscription for Virtual Service Edge, you will only see Virtual Service Edge-related fields in the Admin Portal.
To learn more, see [About Virtual ZENs](/zia/about-virtual-zens) and [About Virtual Service Edges](/zia/about-virtual-service-edges).
