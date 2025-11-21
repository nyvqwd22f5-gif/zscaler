# Adding Cloud NSS Feeds for Cloud & Branch Connector DNS Logs
Source: https://help.zscaler.com/unified/adding-cloud-nss-feeds-cloud-branch-connector-dns-logs
PDF: https://help.zscaler.com/pdf/com/en/1519556.pdf

To configure a Cloud Nanolog Streaming Service (NSS) feed for DNS logs:
- Go to **Infrastructure **>** Connectors** > **Cloud** > **Nanolog Streaming Service**.
- In the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
- On the** Add Cloud NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between NSS and your security information and event management (SIEM) system.
- **NSS Type**: The NSS type is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **Status**: The status is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **SIEM Type**: Choose a SIEM type from the list.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload to the SIEM's best practice.
- **API URL**: Enter the HTTPS URL of the SIEM log collection API endpoint.
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **DNS**.
- **Feed Output Type**:** **The output is **JSON** by default. You can choose **Name Value Pairs** or **Tab Separated** if your SIEM accepts either of these formats.
- **JSON Array Notation**: When **JSON** is selected for the Feed Output Type, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format. That is, individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: (Optional) Type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**: These are the fields that are displayed in the output. See [NSS Feed Output Format: DNS Logs](/unified/nss-feed-output-format-dns-logs-1) for information about the available fields and their syntax.
- **Time Zone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define the filters:
- [Action](#Action)
- [Source](#Source)
- [Destination](#Destination)
- [Transaction](#Transaction)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**Policy Actions**
- **Allow**: Use this filter to limit the logs to allowed DNS requests and responses.
- **Block**: Use this filter to limit the logs to DNS requests and responses that the service dropped.
- **Redirect to ZPA**: Use this filter to limit the logs to transactions wherein the service redirected the DNS request or response to Zscaler Private Applications].
- **Rule Name**: Use this filter to limit the logs based on specific rules in the [DNS Filtering Rule](/unified/configuring-dns-filtering-rule). Choose the rules from the list.
- []**Locations**: Use this filter to limit the logs to specific locations and sublocations. To use the Search function, enter the location name in the Search box and click **Search**. There is no limit on the number of locations that you can select. Locations that you delete after selecting them appear with a strikethrough line.
- **Cloud or Branch Connector Groups**:** **Use this filter to limit the logs to specific [Cloud Connector Groups ](/unified/about-cloud-connector-groups-0)or Branch Connector Groups.
- **Cloud or Branch Connector**: Use this filter to limit the logs to specific Cloud Connectors or Branch Connectors.
- **Client IP Addresses**: Use this filter to limit the logs based on a client’s IP address. You can enter:
- An IP address (e.g., `198.51.100.100`)
- A range of IP addresses (e.g., `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (e.g., `203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- []**Server IP Addresses**: Use this filter to limit the logs to specific server IP addresses. You can enter:
- An IP address (e.g., `198.51.100.100`)
- A range of IP addresses (e.g., `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (e.g., `203.0.113.0/24`)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Server IP Ports**: Use this filter to limit the logs to specific server ports. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- []**Domains**: Use this filter to limit the logs to sessions associated with specific domains. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **DNS Request Types**: Use this filter to limit the logs to sessions associated with specific DNS request types.
- **DNS Response Types**: Use this filter to limit the logs to sessions associated with specific DNS response types.
- **DNS Responses**: Use this filter to limit the logs to sessions that contain specific data in the DNS responses. You can specify domain names, IPv4 and IPv6 addresses. For IPv4 addresses, you can enter:
- An IP address (e.g., `198.51.100.100`)
- A range of IP addresses (e.g., `192.0.2.1-192.0.2.10`)
- An IP address with a netmask (e.g., `203.0.113.0/24`)
You can enter multiple entries separated by commas. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Durations**: Use this filter to limit the logs based on the duration of the sessions, in seconds. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.