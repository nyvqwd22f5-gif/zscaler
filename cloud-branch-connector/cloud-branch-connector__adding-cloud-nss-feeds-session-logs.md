# Adding Cloud NSS Feeds for Session Logs
Source: https://help.zscaler.com/cloud-branch-connector/adding-cloud-nss-feeds-session-logs
PDF: https://help.zscaler.com/pdf/com/en/1452741.pdf

To configure a Cloud Nanolog Streaming Service (NSS) feed for Session logs:
- Go to **Administration **>** Nanolog Streaming Service**.
- In the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
- On the** Add Cloud NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between the NSS and your security information and event management (SIEM) system.
- **NSS Type**: **NSS for Firewall, Cloud and Branch Connector **is enabled by default.
- **Status**: It is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **SIEM Type**: Choose a SIEM type from the list.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload to the SIEM's best practice.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **API URL**: Enter the HTTPS URL of the SIEM log collection API endpoint.
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **Session**.
- Choose the **Session Log Type**:
- **Full Session Logs**: Logs all sessions of the rule individually, except HTTP/HTTPS.
- **Aggregate Logs**: Individual sessions are grouped together based on user, rule, network service, and network application recorded periodically, within a 15-minute time window.
- **Both Session and Aggregate Logs**
- **Feed Output Type**:** **The output is **JSON** by default. You can choose **Name-Value Pairs** or **Tab-separated** if your SIEM accepts either of these formats.
- **JSON Array Notation**: When **JSON** is selected for the Feed Output Type, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format. That is, individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: (Optional) Type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If a record was created using custom encoding, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**: These are the fields that are displayed in the output. See [NSS Feed Output Format: Session Logs](/cloud-branch-connector/nss-feed-output-format-session-logs) for information about the available fields and their syntax.
- **Time Zone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define filters:
- [Action](#Action)
- [Source](#Source)
- [Destination](#Destination)
- [Gateway](#gateway)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- []**Policy Action**:** **Use this filter to limit the logs based on the action the service took, in accordance with the [traffic forwarding rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).
- **Rule Name**: Use this filter to limit the logs based on[ traffic forwarding rules](/cloud-branch-connector/configuring-traffic-forwarding-rule).
- []**Locations**: Use this filter to limit the logs to specific locations. To use the Search function, enter the location name in the Search box and click **Search**. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Cloud or Branch Connector Groups**:** **Use this filter to limit the logs to specific [Cloud Connector Groups ](/cloud-branch-connector/about-cloud-connector-groups)or Branch Connector Groups.
- **Cloud or Branch Connector**: Use this filter to limit the logs to specific Cloud Connectors or Branch Connectors.
- **Client IP Addresses**:** **Use this filter to limit the logs to specific client destination IP addresses. For aggregated sessions, this is the client destination IP address of the last session in the aggregate. You can enter:
- An IP address (e.g., `198.51.100.100`)
- A range of IP addresses (e.g., `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (e.g.,` 203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
[]**Network Services**: Use this filter to limit the logs to specific [network services](/cloud-branch-connector/about-network-services) associated with the session or aggregated sessions.
[]**Gateway**: Use this filter to limit the log to specific gateways.