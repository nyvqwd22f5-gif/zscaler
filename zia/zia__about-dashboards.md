# About Dashboards
Source: https://help.zscaler.com/zia/about-dashboards
PDF: https://help.zscaler.com/pdf/com/en/1399451.pdf

[Watch a video about Insights & Dashboards.](https://fast.wistia.net/embed/iframe/hn1697gbbr)
Predefined dashboards are available in the ZIA Admin Portal. These dashboards contain widgets according to your organization's subscriptions. For example, if your organization has a subscription to the web security service only, you can see dashboards and widgets that report on web traffic, but not those that report on mobile traffic. Each dashboard contains [widgets](/zia/what-widget) that present data in interactive charts, so you can instantly jump from a chart to individual transactions. A dashboard or widget displays the message "View Restricted"** **when you do not have the appropriate permissions to view its content.
Depending on your [role permission](/zia/how-do-i-add-admin-roles) and [scope](/zia/what-admin-scope), you can customize, view and edit the predefined dashboards. When you customize a dashboard, the changes are visible only to you. To view any newly-released widgets, the customized dashboards must be reset.
Zscaler dashboards provide the following benefits and enable you to:
- View real-time visibility into your organization's internet traffic.
- View multiple dashboard views, so you can track internet usage and take action when you see anomalous trends or security threat
- Log out, and when you log back in, the service remembers and displays the last dashboard you viewed.
By default, user-related widgets include locations and users. You can exclude locations by creating new or editing existing widgets and using the Exclude Location filter. This filter applies to all user-related widgets except for widgets in the default Security dashboard. To learn more, see [Excluding Locations in User-Related Reports](/zia/how-do-i-exclude-locations-user-related-reports).
Zscaler recommends that you set your dashboards to automatically reset every 15 minutes. This prevents your session from timing out and also keeps the information in your window up to date. Go to Administration > My Profile to enable this. To learn more, see [Customizing Your Admin Account Settings](/zia/how-do-i-customize-my-admin-account-settings).
Predefined Dashboards
All bandwidth widgets show the data rate, so units are shown in bps, Kbps, Mbps, and Gbps. Any other widgets, including the Top Throttled Locations** **widget, show the data amount itself, so units are shown in bytes, KBs, MBs, and GBs.
The following sections describe the predefined dashboards:
- [Web Overview](#web-overview)
- [Security](#security)
- [Web Browsing](#web-browsing)
- [Cloud Applications](#cloud-applications)
- [Mobile Applications](#mobile-applications)
- [Email Overview](#email-overview)
- [DNS Overview](#DNS-overview)
- [Firewall Overview](#firewall-overview)
- [Bandwidth Control](#bandwidth-control)
- [Office 365](#o365)
- [IPS Overview](#ips)
- [Endpoint DLP](#edlp)
- [Zscaler DSPM Portal](#DSPM-portal)
- [Email DLP Overview](#emaildlp)
[]This dashboard provides a high-level view of your organization's web traffic.
- The **Cloud Application Classes** widget displays the volume of traffic for each cloud application class.
- The **Top URL Categories** widget displays the number of transactions for the top [URL categories](/zia/about-url-categories).
- The **Top Users** widget lists users by bandwidth usage.
- The **Social Networking Applications** widget displays the number of transactions for the top applications in the Social Networking application class.
- The **Streaming Media Applications** widget displays the bandwidth usage for the top streaming media and file share sites that were accessed by your users.
- The **Top Advanced Threats** widget lists the number of transactions that were blocked due to threats in the Advanced Threats category.
- The **Top Application Segments **widget displays the number of transactions for the top application segments.
[See image.](#seeimage10)
[]The service classifies threats into two classes: Viruses and Spyware, and Advanced Threats. This dashboard provides data about the various threats that were blocked by the service in each class.
- The **Viruses & Spyware **widget, the **Advanced Threats** widget, and the **Sandbox** widget provide an overview of the types of threats that were blocked over the selected time period.
- The **Top Users/Locations for Viruses & Spyware** widget, the **Top Users/Locations for Advanced Threats**, and the **Top Users/Locations for Sandbox** flags users and locations whose transactions were blocked due to each type of threat.
- The **Sandbox Patient 0 Events** widget lists patient 0 events that occurred in your organization. This widget is available only if you have Advanced Sandbox. To learn more, see [About the Sandbox Patient 0 Event Widget](/zia/configuring-patient-0-alert#about-sandbox-patient-0-events-widget).
If you have Advanced Sandbox and don't see the **Sandbox Patient 0 Events** widget, [reset](/zia/about-dashboards#what-to-do) the Security dashboard.
- The **Top Application Segments **widget displays the transactions that were blocked for application segments.
[See image.](#seeimage11)
[]This dashboard provides visibility into the browsing activity of your organization.
- The **Web Browsing Trend** widget provides the browsing activity trend of your users for each [URL class](/zia/about-url-categories) in the selected time period.
- The **Web Browsing Summary** widget displays the number of transactions in the selected time period for each URL class.
- The **Top URL Categories** widget displays the number of transactions for each URL category.
- The **Top Users** widget lists the users with the most browsing activity, from the user with the most number of transactions to the least.
- The **Top Blocked URL Categories** widget displays the number of attempts to access URL categories that were blocked due to the configured [URL policies](/zia/about-url-filtering).
- The **Top Blocked Users** widget lists the users with the most blocked transactions.
- The **Top Application Segments **widget displays the transactions for each application segment.
[See image.](#webbrowsing)
[]This dashboard provides visibility into the cloud applications used by your organization.
- The **Cloud Application Trend** widget gives you information on the cloud applications that were used over the selected time period. Zscaler has partnered with Microsoft Cloud App Security (MCAS) to provide a risk profile for each application. To see the risk scores provided by MCAS, as well as the aggregated score provided by Zscaler, point to a cloud app in the widget. Hover over **Microsoft Cloud App Security** to expand and view the data. You can also download the data as a CSV file for further analysis. This information is available on the dashboard and as a CSV file only. It is not available in logs. If a cell is blank, the Zscaler service has been unable to retrieve data for it.
- [Description of Cloud App Trend CSV Fields](#CSV-desc)
The widget supports visibility into 1,000 applications. Also, the Name** **column is searchable, so you can easily find the application you're looking for.
The Miscellaneous <Cloud Application Category> Apps (e.g., Miscellaneous Finance Apps) represents the newly added, lesser-known predefined applications for a category (e.g., Finance). For the Miscellaneous <Cloud Application Category> Apps, the Net Usage (GB) column displays the cumulative data for all the applications grouped inside it, and the columns specific to the individual applications (i.e., Category, Threat Index, and Risk Level) grouped inside it display "No Data."
- The **Social Networking Applications** widget displays the number of transactions for the top applications in the Social Networking application class.
- The **Social Networking Users** widget lists the top users of these applications by the number of transactions.
- The **Streaming Applications** widget displays the bandwidth used by the top applications in this class.
- The **Streaming Users** widget lists the top users of these applications by bandwidth usage.
[See image.](#cloud-apps-pic)
[]This dashboard provides visibility into the traffic from your organization's mobile devices.
- The **Mobile Device Platform Traffic Trend** widget displays the traffic trend for each mobile device type.
- The **Mobile App Category Traffic Pattern** widget displays the activity in each mobile application category.
- The **Mobile App Traffic Pattern** widget displays the activity for each mobile app.
- The **Mobile App Category Summary** widget displays the number of transactions for each mobile application category.
- The **Top Mobile Users** widget displays the top users of mobile devices.
- The **Top Blocked Mobile Users** lists the users who may have violated policies.
[See image.](#seeimage12)
[]This dashboard provides information about the email traffic of your organization.
This dashboard is only visible to users who are admins.
- The **Inbound Email Trends** widget displays a trend line recording how many inbound emails the policies are being applied to.
- The **Outbound Email Trends** widget displays a trend line recording how many outbound emails the policies are being applied to.
- The **Top Senders** widget displays a list of the users who send the most email and how many emails they sent.
- The **Inbound Email Type** displays the number of inbound emails that fall into a policy type.
- The **Outbound Email Type** displays the number of outbound emails that fall into a policy type.
- The **Top Recipients** widget displays a list of the users who receive the most email and how many emails they received.
[See image.](#emailoverview)
[]This dashboard provides data about the DNS traffic of your organization.
- The **Top DNS Tunnels & Network Apps** widget displays what type of tunnels and network applications were most commonly detected.
- The **DNS Tunnel & Network App Categories** widget displays what tunneling and network application categories transactions fell into.
- The **Top Request Categories** widget displays the number of transactions for each requested domain.
- The **Top Blocked Request Categories** widget displays the number of attempts to access the requested domain that were blocked due to the configured DNS Control policies.
- The **Top Users** widget lists the users with the most browsing activity, from the user with the most number of transactions to the least.
- The **Top Blocked Rules Hit** widget lists the [DNS policy](/zia/about-dns-control) rules that were enforced when traffic was blocked.
- The **Top Blocked Users** widget lists the users with the most blocked transactions due to the DNS policy.
- The **DNS Protocol Distribution** widget shows what protocols are in use and which rules they are associated with.
- The **Top Response Categories **widget displays the number of transactions for each DNS response category.
- The **Top Blocked Response Categories **widget displays the number of attempts to access a blocked DNS response category that were blocked due to the configured DNS Control policies.
[See image.](#dns-dashboard-pic)
[]This dashboard provides data about the [firewall](/zia/about-firewall-control) traffic of your organization.
- The **Top Applications** widget displays the network applications that were used.
- By default, the widget does not display internal apps and apps that have not been identified by the Zscaler firewall.
- To add the excluded apps, edit the widget. Then edit the **Network Application **filter and select the apps from the list.
- The **Top Network Services** widget displays the network services that were used.
- The **Top Users** widget lists the users with the most browsing activity, from the user with the most number of transactions to the least.
- The **Top Blocked Rules Hit** widget lists the [firewall policy rules](/zia/understanding-firewall-capabilities) that were enforced when traffic was blocked.
- The **Top Blocked Users** widget lists the users with the most blocked transactions due to the firewall policy.
- The **Top Application Segments **widget displays the application segments with the highest number of sessions to the least.
[See image.](#firewalloverview)
[]This dashboard provides real-time visibility into your organization's bandwidth usage.
- The **Total Bandwidth Consumption** widget displays your organization's bandwidth usage (in bits per second) in a line chart. By default, the dashboard displays bandwidth usage for the past 24 hours. You can choose a different time frame from the menu. When you choose 30 days as the time frame, the widget displays the 95th percentile trend line, which is based on the 95th percentile of inbound or outbound traffic; whichever is highest. From the 30-day view, you can drill down to a 5-minute view right on the chart. The Total Bandwidth Consumption widget displays the 95th percentile line only 30 days after the [Bandwidth Control policy ](/zia/about-bandwidth-control)has been enabled.
- The **Top Throttled Locations** widget displays locations with the most throttled transactions and their corresponding throttled bandwidth.
- The **Top Bandwidth Classes** widget displays the top five bandwidth classes by bandwidth usage.
- The **Top Bandwidth Locations** widget displays the top locations with the highest bandwidth.
- The **Bandwidth Control Rules** widget displays the rules that used the maximum bandwidth.
[See image.](#bandwidthcontrol)
[]This dashboard provides real-time visibility into your organizations' Office 365 traffic.
- The **Total Office 365 Traffic Volume **widget displays the total volume of traffic for each Office 365 application.
- The **Office 365 App Traffic Volume **widget displays the bandwidth usage for the top Office 365 applications that were accessed by your users.
- The **Top Office 365 Locations **widget displays the top locations with the highest bandwidth.
- The **Top Office 365 Users **widget lists the top users of these applications by bandwidth usage.
- The **Total Traffic Volume **widget displays the overall bandwidth usage for all applications.
[See image.](#office365)
[]This dashboard provides real-time visibility into your organization's [IPS](/zia/about-ips-control) traffic.
- The **Top Blocked Locations** widget displays the top locations blocked by IPS policy.
- The **Top Blocked Rules Hit** widget lists the top IPS policy rules that were enforced when traffic was blocked.
- The **Top Threats Categories** widget lists the top types of threats blocked by IPS Control rules.
- The **Top Blocked Users** widget lists the users with the most blocked transactions due to the IPS policy.
- The **Top Rules Hit** widget lists the top IPS policy rules that were enforced.
- The **Top Application Segments **widget displays the number of sessions for each application segment.
[See image.](#ips-img)
[]This dashboard provides real-time visibility into your organization's Endpoint Data Loss Prevention (DLP) traffic.
- The **Top Users** widget lists the top users generating the incidents and the number of incidents per user.
- The **Incidents by Action** widget displays the incidents based on the actions. Hover over the actions at the bottom of the graph to view the trend for a specific action.
- The **Incidents by Severity** widget displays the number of incidents by severity.
- The **Top DLP Engines** widget lists the top DLP engines with incidents and the number of incidents for each DLP engine.
- The **Top Machine Learning Categories **widget displays the top ML categories with incidents and the number of incidents for each category.
- The **Top Rules** widget lists the top Endpoint DLP policy rules that were triggered.
- The **Justification Options **widget displays the top justifications provided by the users to complete their activities.
[See image.](#edlp-img)
[]
Data Security Posture Management (DSPM) helps protect an organization’s data stored in your cloud resources against data theft, misuse, or loss by continuously scanning the data and numerous potential misconfigurations, vulnerabilities, and permissions that might contribute to attack vectors. DSPM provides detailed insights into where this sensitive data resides in your cloud environment, sensitive data types, and misconfigurations in data stores that contain sensitive data. To learn more, see[ DSPM Help](/dspm).
You can access the DSPM Admin Portal from the ZIA Admin Portal using SSO, if you have subscribed to the DSPM service and if a DSPM Admin or DSPM Super Admin role is assigned to you. To learn more about predefined roles and permissions in DSPM, see [About Roles](/dspm/about-roles). To check if you are subscribed to the DSPM service, you can view your company subscriptions to confirm if a DSPM license is present. To learn more, see [Viewing Subscriptions](/zia/viewing-subscriptions).
To access the DSPM Admin Portal, in the ZIA Admin Portal, go to **Dashboard** > **Zscaler DSPM Portal**, or **Policy** >** Zscaler DSPM Portal**.
The Admin with view permission can access the DSPM Admin Portal only from the** Dashboard**.
[See image.](#DSPM-SSO-Links)
[]![Screenshot of DSPM SSO Links](/downloads/tech-pubs-drafts/zia-draft-articles/accessing-zscaler-dspm-admin-portal-using-sso/DSPM_SSO_Links.png)
[]This dashboard provides real-time visibility into your organization's Email DLP traffic.
- The **Incidents by Severity** widget displays the number of incidents by severity.
- The **Incidents by Action** widget displays the incidents based on the actions. Hover over the actions at the bottom of the graph to view the trend for a specific action.
- The **Top Rules** widget lists the top Email DLP policy rules that were triggered.
- The **Top DLP Engines** widget lists the top DLP engines with incidents and the number of incidents for each DLP engine.
- The **Top Machine Learning Categories **widget displays the top ML categories with incidents and the number of incidents for each category.
- The **Top Users** widget lists the top users generating the incidents and the number of incidents per user.
[See image.](#email_dlp)
About the Dashboard Pages
On any Dashboard page, you can do the following:
- View another dashboard. Hover over the Dashboard tab to list the dashboards, then click the dashboard you want to view.
- Change the title of the dashboard. A dashboard title can contain up to 50 characters. Click the title of the dashboard and enter a new name. Click anywhere outside of the title field to save the change.
- Choose a different time frame from the menu. By default, dashboards display data for the last 24 hours. The time frame is retained when you navigate to other dashboards. The Bandwidth Control and Office 365 dashboards are the only dashboards that offer a 30-day time frame. Selecting multiple days results in seeing the sum of bytes/transactions per day in charts.
- View, edit, delete, resize, and move the widgets that the dashboard contains. To learn more, see [About Widgets](/zia/6.1/what-widget).
- Edit or delete a note to the dashboard. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/6.1/how-do-i-add-notes-dashboard-and-interactive-reports).
-
Roll over a chart to obtain more information about an item, click it, and select one of the following options:
- **View Logs** to see its associated logs. This option is not available for charts that display secure browsing class, data or status, because they only use samples as their data units. To learn more, see [About Insights Logs](/zia/about-insights-logs).
If you select this option** **for the following widgets on the Office 365 dashboard, then some predefined filters are automatically set on the [Insights Logs](/zia/about-insights-logs) page:
- [Total Office 365 Traffic Volume](#total-office-365-traffic-volume-logs)
- [Office 365 App Traffic Volume](#office-365-traffic-volume-logs)
- [Top Office 365 Locations](#top-o365-locations-logs)
- [Total Traffic Volume](#total-traffic-volume-logs)
- [Top Office 365 Users](#top-o365-users-logs)
- **Analyze Chart** to view the chart in the **Analytics **tab where you can interactively drill down to the logs. To learn more, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
If you select this option** **for the following widgets on the Office 365 dashboard, then some predefined data types and filters are automatically set on the [Web Insights](/zia/about-insights) page:
- [Total Office 365 Traffic Volume](#total-office-365-traffic-volume-charts)
- [Office 365 App Traffic Volume](#office-365-traffic-volume-charts)
- [Top Office 365 Locations](#top-o365-locations-charts)
- [Total Traffic Volume](#total-traffic-volume-charts)
- [Top Office 365 Users](#top-o365-users-charts)
[]For this widget, on the **Insights Logs** page, the [filters](/zia/web-insights-logs-filters) are set as follows:
- **Cloud Application**: This filter includes the cloud application for which you want to view the logs as the value.
- **Show Delayed Logs**: This filter is disabled by default.
[]For this widget, on the **Web Insights** page, the [data type and filters](/zia/web-data-types-and-filters) are set as follows:
- The data type is set to **Cloud Application**.
- The filter is set to **Cloud Application**, which includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
[]For this widget, on the **Insights Logs** page, the [filters](/zia/web-insights-logs-filters) are set as follows:
- **Cloud Application**: This filter includes the cloud application for which you want to view the logs as the value.
- **Show Delayed Logs**: This filter is disabled by default.
[]For this widget, on the **Web Insights** page, the [data type and filters](/zia/web-data-types-and-filters) are set as follows:
- The data type is set to **Cloud Application**.
- The filter is set to **Cloud Application**, which includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
[]For this widget, on the **Insights Logs** page, the [filters](/zia/web-insights-logs-filters) are set as follows:
- **User**: This filter includes the user for which you want to view the logs as the value.
- **Cloud Application**: This filter includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
- **Show Delayed Logs**: This filter is disabled by default.
[]For this widget, on the **Web Insights** page, the [data type and filters](/zia/web-data-types-and-filters) are set as follows:
- The data type is set to **User** with the view option to **Top 100**.
- The following filters are selected:
- **User**: This filter includes its default value **Any**.
- **Cloud Application**: This filter includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
[]For this widget, on the **Insights Logs** page, the [filters](/zia/web-insights-logs-filters) are set as follows:
- **Location**: This filter includes the location for which you want to view the logs as the value.
- **Cloud Application**: This filter includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
- **Show Delayed Logs**: This filter is disabled by default.
[]For this widget, on the **Web Insights** page, the [data type and filters](/zia/web-data-types-and-filters) are set as follows:
- The data type is set to **Location** with the view option to **Top 100**.
- The following filters are selected:
- **Location**: This filter includes its default value **Any**.
- **Cloud Application**: This filter includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
[]For this widget, on the **Insights Logs** page, the [filters](/zia/web-insights-logs-filters) are set as follows:
- **Cloud Application**: This filter includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
- **Show Delayed Logs**: This filter is disabled by default.
[]For this widget, on the **Web Insights** page, the [data type and filters](/zia/web-data-types-and-filters) are set as follows:
- The data type is set to **Overall Traffic **with the view option to **Top 100**.
- The filter is set to **Cloud Application**, which includes the following applications:
- Common Office 365 Applications
- Microsoft Azure
- Microsoft Azure AD
- Microsoft Delve
- Microsoft Dynamics 365
- Microsoft Intune
- Microsoft Planner
- Microsoft Power BI
- Microsoft Sway
- Microsoft Teams
- OneDrive
- OneDrive (Old Category)
- Outlook
- SharePoint Online
- Skype
- Yammer
A widget displays the top five items and groups everything else under **Other**. Click **Show Details** to see the items that were grouped under **Other**.
[See image.](#other)
- Hide or show all notes. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/how-do-i-add-notes-dashboard-and-interactive-reports).
- Reset the dashboard to its original settings and view any newly-released widgets. You lose any changes you made, including new widgets that you created.
- Add a note to the dashboard. To learn more, see [Adding Notes to Dashboards and Interactive Reports](/zia/how-do-i-add-notes-dashboard-and-interactive-reports).
- Create a new widget. A dashboard can contain up to 12 widgets. To learn more, see [About Widgets](/zia/what-widget).
- View the Weblog time, which appears at the bottom of every window. The Nanolog servers collect the logs of all users worldwide, and then consolidates and correlates them. The Weblog time displays the date and time of the logs that are being processed by the Nanolog servers.
![Screenshot of the Mobile Applications dashboard and the different widgets and parts](/downloads/zia/documentation-knowledgebase/analytics/about-dashboards/ZIA-6.2-About-Dashboards.png)
[]A description of the fields available in the Cloud Application Trend CSV file.
Zscaler
- **Cloud App Name**: The name of the cloud app that was visited.
- **Cloud App Category**: The cloud app category to which the app belongs.
- **Threat Index**: The threat level assigned by Zscaler and it's based on the history and analysis of the app. Scores range from 0–100 and the lower the score, the safer Zscaler considers the app.
- **Alexa Ranking**: A popularity rating retrieved from partner site alexa.com/siteinfo. A site with an Alexa Rank of 1 has the highest number of combined page views and visitors over the last three months.
- **Risk Level**: The risk level assigned by Zscaler (Low, Medium, or High).
- **Risk Score**: The risk score assigned by Zscaler. Scores range from 1–100 and the higher the score, the riskier Zscaler considers the app.
- **SSL Pinned**: A Boolean representing whether the app provides SSL pinning.
- **Admin Audit Logs**: A Boolean representing whether the app provides admin audit logs.
- **Password Strength**: A Boolean representing whether the app provides a secure password.
- **Data Breach In Last 3 Years**: A Boolean representing whether the app had a data breach in the last 3 years.
- **Vendor Activities Supported**: A list of the vendor activities supported by the app (e.g., View, Upload, Download, etc).
- **Number of Employees**: Number of employees the application's company has (<100, 100–1000, 1000–10000, or 10000+).
- **Year Incorporated**: The year when the application's company was incorporated.
- **DNS CAA Policy**: A Boolean representing whether the app provides DNS CAA policy.
- **DomainKeys Identified Mail**: A Boolean representing whether the app provides DomainKeys Identified Mail.
- **HTTP Security Header Support**: A Boolean representing whether the app provides HTTP security header support.
- **Domain-Based Message Authentication**: A Boolean representing whether the app provides Domain-Based Message Authentication.
- **Weak Cipher Support**: A Boolean representing whether the app provides weak cipher support.
- **Vulnerable to Heartbleed**: A Boolean representing whether the app is vulnerable to Heartbleed.
- **MFA Support**: A Boolean representing whether the app provides MFA support.
- **Support for WAF**: A Boolean representing whether the app provides support for web application firewall (WAF).
- **Poor Terms of Service**: A Boolean representing whether the app provides poor terms of service (e.g., the application can use data shared for other purposes).
- **Published CVE Vulnerabilities**: A Boolean representing whether the app is vulnerable to published CVE.
- **Evasive**: A Boolean representing whether the app provides support for accessing data anonymously without expecting the user to create an account and log in.
- **Data Encryption in Transit**: A Boolean representing whether the app provides data encryption in transit. The encryption the app uses for data in transit (e.g., SSLv2, SSLv3, TLSv1.3, etc).
- **Source IP Restriction**: A Boolean representing whether the app provides source IP restriction.
- **Vulnerability Disclosure Policy**: A Boolean representing whether the app provides the vulnerability disclosure policy.
- **File Sharing**: A Boolean representing whether the app provides file sharing.
- **Remote Access Screen Sharing**: A Boolean representing whether the app provides remote access screen sharing.
- **Vulnerable to Logjam**: A Boolean representing whether the app is vulnerable to Logjam.
- **Sender Policy Framework**: A Boolean representing whether the app provides the Sender Policy Framework.
- **Malware Scanning Content**: A Boolean representing whether the app provides malware scanning content.
- **Vulnerable to Poodle**: A Boolean representing whether the app is vulnerable to Poodle.
- **Valid SSL Certificate**: A Boolean representing whether the app has a valid SSL certificate.
- **Compliance Certifications**: A list of the compliance certifications used by the app (e.g., GDPR, etc.).
- **Vendor Services**: A list of the Zscaler services provided for the app (e.g., API, DLP, Sandbox, etc).
- **Usage**: The total traffic proxied through Zscaler for this app. It's measured in bytes.
To learn more, see [Hosting and Security Characteristics](/zia/shadow-it-report#hosting-security).
MCAS
- **Vendor Name**: Microsoft, the name of the vendor who provided the information.
- **Risk Level**: The risk level assigned by MCAS (Low, Medium, or High).
- **Compliance Certifications**: A list of the compliance certifications used by the app. For example, ["Privacy Shield", "ISO 27001"].
- **Data at Rest Encryption**: Lists the type of encryption given to data at rest. For example, AES.
- **Admin Audit Trail**: A Boolean representing whether the app provides an admin audit trail.
- **User Audit Trail**: A Boolean representing whether the app provides a user audit trail.
- **Data Audit Trail**: A Boolean representing whether the app provides a data audit trail. A data audit trail records transactions every time a data record is altered within the application.
- **HTTP security headers**: A list of the HTTP security headers that the app uses.
- **Multi-factor authentication**: A Boolean representing whether the app supports multi-factor authentication. For example, ["x_frame_options"].
- **Business HQ**: The country where the app maker's headquarters are located.
- **Risk Score**: The risk score assigned by MCAS. Scores range from 0–10 and the higher the score, the safer MCAS considers the app.
Bitglass
- **Vendor Name**: Bitglass, the name of the vendor who provided the information.
- **Risk Score**: The risk score assigned by Bitglass. Scores range from 0–10 and the higher the score, the safer Bitglass considers the app.
- **Risk Level**: The risk level assigned by Bitglass (Low, Medium, or High).
- **Compliance Certifications**: A list of the compliance certifications used by the app. For example, ["FedRAMP", "Privacy Shield"].
- **Multi-factor authentication**: A Boolean representing whether the app supports multi-factor authentication. For example, ["x_frame_options"].
- **Admin Audit Trail**: A Boolean representing whether the app provides an admin audit trail.
- **Data Encryption**: A Boolean representing whether the app provides encryption to data at rest.
- **Transit Encryption**: The encryption the app uses for data in transit. For example, ["TLS 1.3"].
[]![Screenshot of Other slice from Zscaler widget pie chart](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-dashboard-widget-other.png)
[]![Screenshot of the Cloud Applications dashboard ](/downloads/zia/analytics/about-dashboards/ZIA-6.0-Cloud-Applications-Dashboard.png)
[]![Screenshot of the DNS Overview dashboard](/downloads/zia/analytics/about-dashboards/zia-dns-dashboard_6.1r.png)
[]![Screenshot of the Bandwidth Control dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-bandwidth-control-dashboard.jpg)
[]![Screenshot of the Email Overview dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-email-overview-dashboard.jpg)
[]![Screenshot of the Firewall Overview dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-firewall-overview-dashboard.jpg)
[]![Screenshot of the Office 365 dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-office-365-dashboard.jpg)
[]![Screenshot of the Web Browsing dashboard](/downloads/zia/analytics/about-dashboards/ZIA-6.0-Web-Browsing-Dashboard.png)
[]![Screenshot of the Web Overview dashboard](/downloads/zia/analytics/about-dashboards/ZIA-6.0-Web-Overview-Dashboard.png)
[]![Screenshot of the Security dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-security-dashboard.png)
[]![Screenshot of the Mobile dashboard ](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/ZIA-6.0-Mobile-Apps-Dashboard.png)
[]![Screenshot of the IPS Overview Dashboard](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/dashboards/about-dashboards/zia-dashboard-ips.png)
![Endpoint DLP Dashboard in ZIA Admin Portal](/downloads/tech-pubs-drafts/zia-draft-articles/about-dashboards-doc-45874/ZIA-6.2r-endpoint-dlp-dashboard.png)
[]
![Email DLP Dashboard](/downloads/zia/Email_DLP_Overview.png)
[]