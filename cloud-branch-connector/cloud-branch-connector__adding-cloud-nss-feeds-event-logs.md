# Adding Cloud NSS Feeds for Event Logs
Source: https://help.zscaler.com/cloud-branch-connector/adding-cloud-nss-feeds-event-logs
PDF: https://help.zscaler.com/pdf/com/en/1458976.pdf

To configure a Cloud Nanolog Streaming Service (NSS) feed for Event logs:
- Go to **Administration **>** Nanolog Streaming Service**.
- On the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
[See image.](#AddCloudNSSFeed)
[][![Adding a Cloud NSS Feed in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/nss-feeds/adding-cloud-nss-feeds/adding-cloud-nss-feeds-event-logs/Add%20Cloud%20NSS%20Feed.png)
]
- In the** Add Cloud NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between NSS and your security information and event management (SIEM) system.
- **NSS Type**: The NSS type is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **Status**: The status is** Enabled** by default. If you want to activate it at a later time, click **Disabled**.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** for SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **SIEM Type**: Select a SIEM type from the list.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload according to the SIEM's best practice.
- **API URL**: Enter the HTTPS URL of the SIEM log collection API endpoint.
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **Event**.
- **Feed Output Type**:** **The output is **JSON** by default. You can choose **Name Value Pairs** or **Tab Separated** if your SIEM accepts either of these formats.
- **JSON Array Notation**: When **JSON** is selected for the Feed Output Type, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format. That is, individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: (Optional) Type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If a record was created using custom encoding, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**: These are the fields that are displayed in the output. See [NSS Feed Output Format: Event Logs](/cloud-branch-connector/nss-feed-output-format-event-logs) for information about the available fields and their syntax.
- **Timezone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. You can also specify direct GMT offsets.
- **Locations**: Use this filter to limit the logs to specific locations and sublocations. To use the Search function, enter the location name in the Search box and click **Search**. There is no limit on the number of locations that you can select. Locations that you delete after selecting them appear with a strikethrough line.
- **Cloud/Branch Connector Groups**:** **Use this filter to limit the logs to specific [Cloud Connector Groups ](/cloud-branch-connector/about-cloud-connector-groups)or Branch Connector Groups.
- **Cloud/Branch Connector VM**: Use this filter to limit the logs to specific Cloud or Branch Connector virtual machines (VMs).
[See image.](#AddEventCloudNSSFeed)
[][![Add Cloud NSS Feed window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/nanolog-streaming-service/nss-feeds/adding-cloud-nss-feeds/adding-cloud-nss-feeds-event-logs/Add%20Event%20Cloud%20NSS%20Feed.png)
]
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).