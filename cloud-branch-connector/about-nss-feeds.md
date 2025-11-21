# About NSS Feeds
Source: https://help.zscaler.com/zia/about-nss-feeds
PDF: https://help.zscaler.com/pdf/com/en/1400216.pdf

An NSS feed specifies the data from the logs that the NSS sends to your security information and event management (SIEM) system. You can add as many as 16 feeds per NSS server. ([Web](/zia/adding-nss-feeds-web-logs) and [Firewall](/zia/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per server to ensure optimal performance.)
NSS feeds provide the following benefits and enable you to:
- Define different filters and fields in each NSS feed for relevant data collection and select your preferred feed output format (e.g., CSV) for actionable reports.
- Add a separate feed for real-time alerts to monitor essential NSS connections to the Zscaler Nanolog and to your SIEM.
About the NSS Feeds Page
On the NSS Feeds page (Administration > Nanolog Streaming Service), you can do the following:
- [Add an NSS feed](/zia/adding-nss-feeds).
- [Add an MCAS NSS feed](/zia/adding-mcas-nss-feeds).
- Search for an NSS feed.
- View a list of all configured NSS feeds. For each feed, you can see:
- **Feed Overview**:** **The general parts of the NSS feed (e.g., Feed Name, NSS Server, Status, etc.).
- **Log Filter**: The log type and its log type attributes.
- **Feed Output Format**: The strings pertaining to the log type. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats).
- **Feed Attributes**: Other feed attributes (e.g., Duplicate Logs, Time Zone, etc.).
- [Modify the table and its columns](/zia/using-tables).
- [Edit an NSS feed](/zia/editing-deleting-duplicating-items).
-
[Add an NSS server](/zia/about-nss-servers).
To learn more about adding NSS servers per platform, see the [NSS Deployment Guides](/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides).
- [Add a Cloud NSS feed](/zia/about-cloud-nss-feeds).
- [Add an NSS Collector server](/zia/adding-nss-collector-servers).
![Screenshot of the NSS Feeds page in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-feeds/about-nss-feeds/nss-feed-page.png)