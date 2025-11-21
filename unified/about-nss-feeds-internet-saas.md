# About NSS Feeds for Internet & SaaS
Source: https://help.zscaler.com/unified/about-nss-feeds-internet-saas
PDF: https://help.zscaler.com/pdf/com/en/1496626.pdf

An NSS feed specifies the data from the logs that the NSS sends to your security information and event management (SIEM) system. You can add as many as 16 feeds per NSS server. ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per server to ensure optimal performance.)
NSS feeds provide the following benefits and enable you to:
- Define different filters and fields in each NSS feed for relevant data collection and select your preferred feed output format (e.g., CSV) for actionable reports.
- Add a separate feed for real-time alerts to monitor essential NSS connections to the Zscaler Nanolog and to your SIEM.
About the NSS Feeds Page
On the NSS Feeds page (Logs > Log Streaming > Nanolog Streaming Service > NSS Feeds), you can do the following:
- [Add an NSS feed](/unified/adding-nss-feeds).
- [Add an MCAS NSS feed](/unified/adding-mcas-nss-feeds).
- Search for an NSS feed.
- View a list of all configured NSS feeds. For each feed, you can see:
- **Feed Overview**:** **The general parts of the NSS feed (e.g., Feed Name, NSS Server, Status, etc.).
- **Log Filter**: The log type and its log type attributes.
- **Feed Output Format**: The strings pertaining to the log type. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/unified/general-guidelines-nss-feeds-and-feed-formats).
- **Feed Attributes**: Other feed attributes (e.g., Duplicate Logs, Time Zone, etc.).
- [Modify the table and its columns](/unified/using-tables).
- Edit an NSS feed.
-
[Add an NSS server](/unified/about-nss-servers).
To learn more about adding NSS servers per platform, see the [NSS Deployment Guides](/unified/logs/internet-saas/log-streaming/nss-deployment-guides).
- [Add a Cloud NSS feed](/unified/about-cloud-nss-feeds).
- [Add an NSS Collector server](/unified/about-nss-collector-servers).
![Screenshot of the NSS Feeds page in the ZIA Admin Portal](/downloads/unified/logs/internet-saas/log-streaming/nss-feeds/about-nss-feeds/zia-add-nss-feed-page.png)