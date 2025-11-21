# About Cloud NSS Feeds
Source: https://help.zscaler.com/zia/about-cloud-nss-feeds
PDF: https://help.zscaler.com/pdf/com/en/1401836.pdf

[Watch a video about Cloud NSS feeds.](https://fast.wistia.net/embed/iframe/pu3xumhpuf)
Cloud NSS allows you to instantly stream logs from Zscaler Internet Access (ZIA) directly into a compatible cloud-based security information and event management (SIEM) system without the need to deploy an NSS virtual machine (VM) for Web or Firewall. To learn more, see [Understanding Nanolog Streaming Service (NSS)](/zia/understanding-nanolog-streaming-service).
A Cloud NSS feed specifies the data from the logs that Cloud NSS sends to your SIEM. You can configure one Cloud NSS feed per [ZIA log type](/zia/adding-cloud-nss-feeds) (e.g., SaaS Security) per Cloud NSS instance. The feed is automatically assigned to Cloud NSS when you configure the feed. Also, you can use Cloud NSS feeds to configure SIEM connectivity across cloud-based SIEMs.
Cloud NSS feeds provide the following benefits and enable you to:
- Support robust and extensive cloud-to-cloud logging by creating a feed for all [ZIA log types](/zia/adding-cloud-nss-feeds) (e.g., Web, Tunnel, etc.).
- Define different filters and fields in each Cloud NSS feed for relevant data collection and select your preferred feed output format (e.g., JSON) for actionable reports.
About the Cloud NSS Feeds Page
On the Cloud NSS Feeds page (Administration > Nanolog Streaming Service), you can do the following:
- [Add a Cloud NSS feed](/zia/adding-cloud-nss-feeds).
- Search for a Cloud NSS feed.
- View a list of all configured Cloud NSS feeds. For each feed, you can see:
- **Feed Overview**:** **The general parts of the Cloud NSS feed (e.g., Feed Name, Status, etc.).
- **Log Filter**: The log type and its log type attributes.
- **Feed Output Format**: The strings pertaining to the log type. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats).
- **Feed Attributes**: Other feed attributes (e.g., Time Zone, Max Batch Size, etc.).
- **Last Connectivity Test**: The time of the last completed connectivity test.
- [Modify the table and its columns](/zia/using-tables).
- Test the connectivity to the SIEM.
A Cloud NSS feed behaves differently according to HTTP/S response status codes from the SIEM. The following responses are not specific to testing connectivity:
- HTTP code `200` or `204`: The feed considers the batch of logs successfully uploaded.
- HTTP code `400`: The feed considers the batch of logs to have a parsing error and drops the batch.
- Any other HTTP code (e.g., `401`, `403`, `501`, etc.): The feed repeatedly attempts to upload the same batch until it receives a `200`, `204`, or `400` response from the SIEM up to one hour. After one hour, the batch is dropped.
- [Edit a Cloud NSS feed](/zia/editing-deleting-duplicating-items).
- [Add an NSS server](/zia/about-nss-servers).
- [Add an NSS feed.](/zia/adding-nss-feeds)
- [Add an NSS Collector server](/zia/adding-nss-collector-servers).
![Screenshot of the Cloud NSS Feeds page in the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-feeds/about-cloud-nss-feeds/zia-nss-add-cloud-nss-feed-page.png)