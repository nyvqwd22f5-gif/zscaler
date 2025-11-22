# About NSS Feeds
Source: https://help.zscaler.com/cloud-branch-connector/about-nss-feeds
PDF: https://help.zscaler.com/pdf/com/en/1420626.pdf

A Nanolog Streaming Service (NSS) feed specifies the data from the logs that the NSS sends to the security information and event management (SIEM) system. Both Cloud Connector and Branch Connector can generate Session, DNS, Event, and Metrics logs.
You can add up to 16 NSS feeds for each NSS. ([Session Logs](/cloud-branch-connector/adding-nss-feeds-session-logs) are limited to 8 feeds per NSS to ensure optimal performance.)
NSS Feeds provide the following benefits and enable you to:
- Apply different fields, formats, and filters for each feed.
- Filter the data, to send only the data you need to the SIEM.
About the NSS Feeds Page
On the NSS page (Administration > Nanolog Streaming Service > NSS Feeds), you can do the following:
- [Add an NSS feed](/cloud-branch-connector/adding-nss-feeds).
- View a list of all configured NSS feeds:
- **Feed Overview: **The general parts of the NSS feed (e.g., Feed Name, NSS Server, Status, etc.).
- **Log Filter: **The log type and its log type attributes.
- **Feed Output Format: **The strings related to the log type.
- **Feed Attributes: **Other feed attributes (e.g., Duplicate Logs, Time Zone, SIEM Rate, etc.).
- [Edit an NSS Feed](/cloud-branch-connector/editing-deleting-or-duplicating-items#edit).
- [Delete an NSS Feed](/cloud-branch-connector/editing-deleting-or-duplicating-items#delete).
- Modify the table and its columns.
- View the** **[NSS Servers](/cloud-branch-connector/about-nss-servers) page.
To learn more about adding NSS servers per platform, see the [NSS Deployment Guides](/cloud-branch-connector/deploying-nss-virtual-appliances).
- View the [Cloud NSS Feeds](/cloud-branch-connector/about-cloud-nss-feeds) page.
![NSS Feeds page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/NSSFeeds.png)