# About Cybersecurity Insights
Source: https://help.zscaler.com/unified/about-cybersecurity-insights
PDF: https://help.zscaler.com/pdf/com/en/1497456.pdf

The Zscaler service protects your organization's traffic against multiple different security threats on a daily basis. The policies that you configure to strengthen your organization's traffic from malicious attacks take effect in fending off and blocking persistent cyberattacks. Zscaler keeps updating the protection perimeter to protect your organization from ever-evolving threats by using Zscaler's progressive security features to stay ahead of the attacker while providing a safe, secure, and seamless experience for your users.
Cybersecurity Insights provides a unified real-time visibility into critical security incidents and policy actions to understand the security efficacy of layered defense across [Malware Protection](/unified/configuring-malware-protection-policy), [Advanced Threat Protection](/unified/configuring-advanced-threat-protection-policy) (ATP), [Sandbox](/unified/about-sandbox), [Firewall](/unified/configuring-firewall-policies), and Isolation for your organization. You can view the metrics for different types of threat incidents that Zscaler blocked, such as the threat category, number of threats, and attack trends, among many other things.
Additionally, the page displays information about new threat protection that Zscaler has equipped your organization with. You can read the complete blog or article on the threat by our ThreatLabZ team across various media outlets referenced from this page.
Cybersecurity Insights provides the following benefits and enables you to:
- Gain real-time visibility into the security incidents that the Internet & SaaS service protects you from.
- View the incidents from user, location, URL categories, cloud apps, and department perspectives.
- Identify the location, users, and category of threats that are targeted at your organization so that you can appropriately configure stronger policies against them.
- View new evolving threats that Zscaler shields you against with detailed information on each threat by Zscaler's ThreatLabZ.
About the Cybersecurity Insights Page
On the Cybersecurity Insights page (Analytics > Internet & SaaS > Analytics > Cybersecurity Insights), you can do the following:
- Filter to view data for the last 1 hour, 4 hours, 1 day, 7 days, or 14 days. The default time is the last 1 hour.
- **Incoming Real-Time Threats**: View the graph for the number of incidents recorded for the selected time period. Hover over a date in the graph to see the total number of incidents for that date and the split between the following threat categories:
- [Threat Categories](#threat-category)
- **Top Locations by Security Incidents**: View the top 10 locations with incidents and the number of incidents for each location.
- **Top Users by Security Incidents**: View the top 10 users with incidents and the number of incidents for each user.
- **Top Departments by Security Incidents**: View the top 10 departments with incidents and the number of incidents recorded by them.
- **Cloud Apps by Security Incidents**: View the pie chart for cloud apps with incidents. The total number of incidents in all the cloud apps is at the center of the pie chart. Hover over the pie chart to view the number of incidents for each cloud app.
- **URL Categories by Security Incidents**: View the pie chart for URL categories with incidents. The total number of incidents in all the URL categories is at the center of the pie chart. Hover over the pie chart to view the number of incidents for each URL category.
-
**Threat Incidents**: View the number of incidents recorded for each threat category. Click on a threat category to view a list of all incidents that occurred in the threat category. For each incident, you can view the following information:
- **Incident Name**: The name of the incident. Click on the incident to view the details of the incident on the Details tab.
- [Details Tab](#details-tab)
- **Category**: The category of the incident (e.g., Botnet Callback, Phishing, etc.).
- **Impacted Systems**: The user transactions impacted by the incident. Click on the number to further analyze the systems in the Impacted Systems tab.
- [Impacted Systems Tab](#impacted-systems)
- **Status**: The action taken on the transactions related to the incident.
- **Last Known Attempt**: The date and time of the last known attempt by the threat.
- **First Known Attempt**: The date and time of the first known attempt by the threat.
You can choose to view the table for 25, 50, or 100 rows at a time and use the arrows to navigate back and forth between the table pages from the bottom of the table.
- **Recent Protections**: View the cards detailing recent protections Zscaler introduced into the service. Click the **View Details** link for a card; you're redirected to the media outlets where you can read the complete article or blog on that threat.
![The Cybersecurity Insights Page in the ZIA Admin Portal](/downloads/zia/dashboard-analytics/reports/about-cybersecurity-insights/ZIA-6.2r-Cybersecurity-Insightss.png)
[]On the Details tab, you can view the following information:
- **Policy Action**: The policy action enforced on transactions related to the incident.
- **Event Type**: The type of threat event.
- **Last Known Attempt**: The date and time of the last known attempt by the threat.
- **First Known Attempt**: The date and time of the first known attempt by the threat.
- **Duration**: The duration between the first and last known attempt by the threat.
- **Total Transactions**: The total number of transactions related to the threat.
- **Total Bytes**: The total bytes of data for all the transactions related to the threat.
- **File Name**: The name of the file related to the incident.
- **Sandbox Category**: The name of the sandbox category, if the file is sent for sandbox analysis.
- **File Type**: The type of file involved in the incident.
- **File Size**: The file size involved in the incident.
- **MD5**: The MD5 hash for the file that triggered the rule.
- **SHA-2 (256-bit)**: The hash of identical files.
- **Destination IP**: The destination IP.
- **Hostname**: The hostname involved in the incident.
- **Application Category**: The application category related to the incident, if applicable.
- **Application**: The name of the application involved in the incident, if applicable.
- **URL Category**: The [URL category](/unified/about-url-categories) of the incident.
[See image.](#details-tab-img)
[]On the Impacted Systems tab, you can view the following information:
- **Top Departments by Security Incidents**: The top 5 departments impacted by the incident.
- **Top Locations by Security Incidents**: The top 5 locations impacted by the incident.
-
**Total Impacted Systems**: The table shows all the users impacted by this incident. For each incident, you can view the following information:
- **User Name**: The name of the user.
- **Client IP**: The IP address from which the transaction originated. This is the IP address of the client device.
- **Client External IP**: The internet gateway location IP address of the client.
- **Last Known Attempt**: The date and time of the last known attempt by the threat for the user.
- **First Known Attempt**: The date and time of the first known attempt by the threat for the user.
- **Duration**: The duration of the transactions related to the incident.
- **Department**: The [department](/unified/about-departments) the user belongs to.
- **Locations**: The [location](/unified/about-locations) of the user.
- **Allowed Transactions**: The number of user transactions that were allowed related to the incident.
- **Total Transactions**: The total number of user transactions related to the incident.
You can choose to view the table for 25, 50, or 100 rows at a time and use the arrows to navigate back and forth between the table pages from the bottom of the table.
[See image.](#impacted-systems-tab-img)
- []Malware
- Spyware
- Virus
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sandbox Offensive Security Tools
- Sandbox Ransomware
- Suspected Spyware or Adware
- Adware/Spyware Sites
- Advanced Security
- Botnet Callback
- Browser Exploit
- Crypto Mining
- Domain Generated Algorithm Domains
- Malicious Content
- Suspicious Content
- Peer-to-Peer
- Phishing
- Suspicious Destinations
- Unauthorized Communication
- Webspam
- Cross-site Scripting
- Unknown (this represents all the incidents that the Zscaler service was unable to classify under a threat category or were not classifiable under any of the preceding categories)
[]![Details tab in the Cybersecurity Inisghts](/downloads/zia/dashboard-analytics/reports/about-cybersecurity-insights/ZIA-6.2r-Cybersecurity-Insights-Details-tab.png)
[]![Impacted Systems tab in Cysbersecurity Insights](/downloads/zia/dashboard-analytics/reports/about-cybersecurity-insights/ZIA-6.2r-Cybersecurity-Insights-impacted-systems-tab_0.png)