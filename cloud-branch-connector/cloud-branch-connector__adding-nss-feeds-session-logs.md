# Adding NSS Feeds for Session Logs
Source: https://help.zscaler.com/cloud-branch-connector/adding-nss-feeds-session-logs
PDF: https://help.zscaler.com/pdf/com/en/1420721.pdf

You can configure up to 8 NSS feeds to specify the data from the Session logs that the NSS sends to the SIEM. For each feed, you can configure multiple types of filters. A large number of filters or complex filters, such as string searches, can impact the performance of the NSS.
To configure a feed for session logs:
- Go to **Administration **>** Nanolog Streaming Service**.
- On the **NSS Feeds** tab, select **Add NSS Feed**.
[See image.](#AddNSSFeed)
[![Adding a NSS Feed in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/nss/nss-feeds/adding-nss-feeds/adding-nss-feeds-session-logs/Add%20NSS%20Feed.jpg)
]
- In the** Add NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between NSS and your SIEM.
- **NSS Type**: The NSS type is set to **NSS for Firewall, Cloud and Branch Connector **by default.
- **NSS Server**:** **Select an **NSS Server** from the list.
- **Status**: The status is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: The type of destination. Select from **IP Address** or **FQDN**.
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **SIEM FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but without relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: The SIEM rate is** **set to **Unlimited** by default. Select **Limited **if** **you need to control the output stream due to SIEM licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: Enter a rate limit for the events that you streamed to your SIEM.
- **Log Type**: Select **Session**.
- Select the **Session Log Type**:
- **Full Session Logs**: Logs all sessions of the rule individually, except HTTP and HTTPS.
- **Aggregate Logs**: Individual sessions are grouped together based on {user, rule, network service, network application} and recorded periodically.
- **Both Session and Aggregate Logs**
- **Feed Output Type**:** **The output is a comma-separated value (**CSV**) list by default. You can select from **Name Value Pairs**, **Tab Separated**, **JSON**, or **Custom **if your SIEM accepts any of these formats.
- **Feed Escape Character**: (Optional) Type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If custom encoding was done for a record, the `%s{eedone} `field displays **YES** for that record.
- **Feed Output Format**: These are the fields that are displayed in the output.
- **Timezone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone Database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during any downtime, specify the number of minutes that the NSS sends duplicate logs.
[See image.](#AddNSSFeedwindow)
[![Add NSS Feed window in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-connector/analytics-monitoring/nss/nss-feeds/adding-nss-feeds/adding-nss-feeds-session-logs/Add%20NSS%20Feed%20window.jpg)
]
- Define the following filters.
- [Action](#Action)
- [Source](#Source)
- [Destination](#Destination)
- [Gateway](#Gateway)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
- **[]Policy Actions**: Use this filter to limit the logs based on the action the service took, in accordance with the[ traffic forwarding](/cloud-branch-connector/about-traffic-forwarding) rules.
- **Rule Name**: Use this filter to limit the logs based on the [configured traffic forwarding rule](/cloud-branch-connector/configuring-traffic-forwarding-rule). Select the rule name(s) from the list.
- **[]Locations**: Use this filter to limit the logs to specific [locations](/cloud-branch-connector/about-locations). To use the search function, enter the location name in the search box and click **Search**. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Branch Connector Groups**: Use this filter to limit the logs to specific Branch Connector groups.
- **Branch Connector**: Use this filter to limit the logs to specific Branch Connectors.
- **Client IP Addresses**: Use this filter to limit the logs based on a client’s IP address. You can enter:
- An IP address (e.g., 198.51.100.100).
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10).
- An IP address with a netmask (e.g., 203.0.113.0/24).
You can enter multiple entries. Press **Enter** after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
**[]Network Services**: Select Any to apply the NSS feed to all [network services](/cloud-branch-connector/about-network-services), or use the drop-down menu to select specific network services.
[]**Gateway**: Use this filter to limit the logs to specific gateways.