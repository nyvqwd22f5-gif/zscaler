# About Cloud NSS Feeds
Source: https://help.zscaler.com/cloud-branch-connector/about-cloud-nss-feeds
PDF: https://help.zscaler.com/pdf/com/en/1452731.pdf

Cloud NSS allows you to instantly stream logs from the Zscaler Cloud & Branch Connector Admin Portal directly into a compatible cloud-based security information and event management (SIEM) system without the need to deploy an NSS VM. To learn more, see [Understanding Nanolog Streaming Service](/zia/understanding-nanolog-streaming-service).
A Cloud NSS feed specifies the data from the logs that Cloud NSS sends to your SIEM system. The feed is automatically assigned to Cloud NSS when you configure the feed. Also, you can use Cloud NSS feeds to configure SIEM connectivity across cloud-based SIEMs. Both Cloud Connector and Branch Connector can generate Session, DNS, Event, and Metrics logs.
Cloud NSS feeds provide the following benefits and enable you to:
- Support robust and extensive cloud-to-cloud logging by creating a feed for all log types.
- Define different filters and fields in each Cloud NSS feed for relevant data collection and select your preferred feed output format for actionable reports.
About the Cloud NSS Feeds Page
On the Cloud NSS Feeds page (Administration > Nanolog Streaming Service), you can do the following:
- [Add a Cloud NSS feed](/cloud-branch-connector/adding-cloud-nss-feeds).
- View a list of all configured Cloud NSS feeds. For each feed, you can see:
- **Feed Overview**:** **The general parts of the Cloud NSS feed (e.g., Feed Name, Status, etc.).
- **Log Filter**: The log type and its log type attributes.
- **Feed Output Format**: The strings pertaining to the log type. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/cloud-branch-connector/general-guidelines-nss-feeds-and-feed-formats).
- **Feed Attributes**: Other feed attributes (e.g., Time Zone, SIEM Rate, etc.).
- **Last Connectivity Test**: The time of the last completed connectivity test.
- [Edit a Cloud NSS feed](/cloud-branch-connector/editing-deleting-or-duplicating-items#edit).
- [Delete a Cloud NSS feed](/cloud-branch-connector/editing-deleting-or-duplicating-items#delete).
- Test the connectivity to the SIEM system.
A Cloud NSS feed behaves differently according to HTTP/S response status codes from the SIEM. The following responses are not specific to testing connectivity:
- HTTP code `200` or `204`: The feed considers the batch of logs successfully uploaded.
- HTTP code `400`: The feed considers the batch of logs to have a parsing error and drops the batch.
- Any other HTTP code (e.g., `401`, `403`, `501`, etc.): The feed repeatedly attempts to upload the same batch until it receives a `200`, `204`, or `400` response from the SIEM up to one hour. After one hour, the batch is dropped.
- Modify the table and its columns.
- View the [NSS Servers ](/cloud-branch-connector/about-nss-servers)page.
- View the[ NSS Feeds ](/cloud-branch-connector/about-nss-feeds)page.
![The Cloud NSS Feeds page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/NSSCloudFeeds.png)