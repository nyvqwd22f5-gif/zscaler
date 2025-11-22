# Adding NSS Feeds for Firewall Logs
Source: https://help.zscaler.com/unified/adding-nss-feeds-firewall-logs
PDF: https://help.zscaler.com/pdf/com/en/1496716.pdf

You can configure up to 8 Nanolog Streaming Service (NSS) feeds to specify the data from the Firewall logs that the NSS sends to the security information and event management (SIEM) system. For each feed, you can configure multiple types of filters. For example, you can configure separate feeds for each location or for different policy rules. A large number of filters or complex filters, such as string searches, can impact the performance of the NSS.
Before you start configuring a feed for Firewall logs, consider the [guidelines for configuring feeds](/unified/general-guidelines-nss-feeds-and-feed-formats).
To configure an NSS feed for Firewall logs:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
On the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between NSS and your SIEM.
-
**NSS Type**: Select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/unified/adding-nss-servers) is required to add an NSS feed.
- **Status**: It is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **Log Domain**:
- If you want to configure NSS for Internet & SaaS Firewall logs, choose **Firewall** and follow the successive steps.
- If you want to configure NSS for Cloud & Branch Connector logs, choose **Cloud & Branch Connector **and see [Adding NSS Feeds](/unified/adding-nss-feeds-cloud-branch-connector) for applicable log types.
- **Log Type**:** **Choose **Firewall Logs**.
- Choose the **Firewall Log Type**:
- **Full Session Logs**: Logs all sessions of the rule individually, except HTTP(S).
- **Aggregate Logs**: Individual sessions are grouped together based on { user, rule, network service, network application } and recorded periodically, within a 15-minute time window.
- **Both Session and Aggregate Logs**
- **Feed Output Type**:** **The output is a comma-separated (**CSV**) list by default. You can choose **Name-Value Pairs** or **Tab-separated** if your SIEM accepts any of these formats.
- **Feed Escape Character**: Optionally, type a character that you want to hex encode when it appears in a URL, hostname, or referrer URL. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**: These are the fields that are displayed in the output. See [NSS Feed Output Format: Firewall Logs](/unified/nss-feed-output-format-firewall-logs) for information about the available fields and their syntax.
- **Time Zone**: By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/unified/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Define the filters:
- [Action](#Action)
- [Who](#Who)
- [Source](#Source)
- [Server Traffic](#Server)
- [Session](#Session)
- [Protocol Classification](#Protocol)
- [Security](#IPS)
- Click **Save** and [activate the change](/unified/saving-and-activating-changes-admin-portal).
- []**DNAT Policy Action**:** **Use this filter to limit the logs to traffic on which the service performed [destination NAT](/unified/about-nat-control) and redirected traffic to specific IP addresses and optionally, ports.
- **DNAT Destination Names**: Use this filter to limit the logs to traffic that was redirected to specific FQDNs after the service performed destination NAT. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Firewall & IPS Policy Actions**: Use this filter to limit the logs based on the action the service took, in accordance with the Firewall Filtering and IPS policies. You can choose multiple actions:
- **Allow**: Packets that were allowed through the Firewall or IPS due to policy.
- **Block/Drop**: Packets that were silently dropped due to Firewall policy.
- **Block/ICMP**: Packets that were dropped because they matched a Firewall rule and sent the client an ICMP error message of Type 3 (Destination Unreachable) and code 9 or 10 (network/host administratively prohibited).
- **Block/Reset**: For TCP traffic, the Zscaler service drops all packets that match the Firewall rule and sends the client a TCP reset. (A TCP packet with the reset (RST) flag is set to 1 in the TCP header, indicating that the TCP connection must be instantly stopped.) For non-TCP traffic, it's the same as Block/Drop.
- **IPS Drop**: Packets that were silently dropped due to IPS policy.
- **IPS Reset**: Packets that were reset due to IPS policy.
- **Firewall Filtering Rule Name**: Use this filter to limit the logs based on specific rules in your Firewall policies. Choose the rules from the list.
- **IPS Rule Name**: Use this filter to limit the logs based on specific rules in your IPS policies. Choose the rules from the list.
- []**Users**: Use this filter to limit the logs to specific users who generated transactions. To use the Search function, enter either the username or email address in the Search box and click **Search**. There is no limit on the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Departments**: Use this filter to limit the logs to specific departments that generated transactions. To use the Search function, enter the department name in the Search box and click **Search**. There is no limit on the number of departments that you can select. Departments that are deleted after they are selected appear with a strikethrough line.
- []**Locations**: Use this filter to limit the logs to specific locations and sub-locations. To use the Search function, enter the location name in the Search box and click **Search**. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Location Groups**: Use this filter to limit the logs to specific [location groups](/unified/about-location-groups) from which transactions were generated. You can search for location groups. Multiple selections are allowed.
-
**Client Source IP Addresses**: Use this filter to limit the logs based on a client’s private IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Client Source Ports**:** **Use this filter to limit the logs to specific client source ports. For aggregated sessions, this is the client source port of the last session in the aggregate. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Client Destination Names**: For Advanced Firewall, use this filter to limit the logs to traffic associated with a specific destination FQDN.
-
**Client Destination IP Addresses**:** **Use this filter to limit the logs to specific client destination IP addresses. For aggregated sessions, this is the client destination IP address of the last session in the aggregate. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Client Destination Ports**: Use this filter to limit the logs to specific client destination ports. For aggregated sessions, this is the client destination port of the last session in the aggregate. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Client Public IP Addresses**: Use this filter to limit the logs based on a client’s public IP address. The internal IP address is available if traffic forwarding is forwarded to the service through a GRE tunnel or from the XFF header. If the internal IP address is not available, the value is the same as the client IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Traffic Forwarding**: Use this filter to limit the logs based on the traffic forwarding method used to send traffic to the Zscaler Firewall. Choose one or more of the listed methods or choose **Any**.
-
[]**Server Source IP Addresses**: Use this filter to limit the logs to specific server source IP addresses. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Server Source Ports**: Use this filter to limit the logs to specific server source ports. For aggregated sessions, this is the server source port of the last session in the aggregate. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Server Destination IP Addresses**: Use this filter to limit the logs to specific server destination IP addresses. For aggregated sessions, this is the server destination IP address of the last session in the aggregate. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Server Destination Port**: Use this filter to limit the logs to specific server destination ports. For aggregated sessions, this is the server destination port of the last session in the aggregate. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Tunnel IP Addresses**: Tunnel IP address of the server. For aggregated sessions, this is the server's tunnel IP address corresponding to the last session in the aggregate. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Server IP Classes**: The [URL class](/unified/about-url-categories) that corresponds to the server IP address.
- **Server IP Super Categories**: The [URL super category](/unified/about-url-categories) that corresponds to the server IP address.
- **Server IP Categories**: The [URL category](/unified/about-url-categories) that corresponds to the server IP address.
- **Countries**: The country code that corresponds to the server IP address.
- []**Inbound Bytes**: Use this filter to limit the logs based on the number of bytes sent from the server to the client. For aggregated sessions, this is the total bytes sent from the server across all sessions in the aggregate. You can specify numbers or ranges. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Outbound Bytes**: Use this filter to limit the logs based on the number of bytes received by the server. For aggregated sessions, this is the total bytes received by the server across all sessions in the aggregate. You can specify numbers or ranges. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Durations**: Use this filter to limit the logs based on the duration of the sessions, in seconds. For aggregated sessions, this indicates the average session duration. You can specify numbers or ranges. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Number of Sessions**: For aggregated logs, you can filter by the number of sessions. You can specify numbers or ranges. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- []**Network Applications**: Use this filter to limit the logs to specific [network applications](/unified/about-network-applications) associated with the session or aggregated sessions.
- **Include**: Use this filter to include selected network applications in the logs. This filter is enabled by default. The default value for this filter is **Any**.
- **Exclude**: Use this filter to exclude selected network applications from the logs. The default value for this filter is **None**.
- **Network Services**: Use this filter to limit the logs to specific [network services](/unified/about-network-services) associated with the session or aggregated sessions.
- []**Threat Names**: Use this filter to limit the logs to specific threat names. You can specify the threats.
-
Use the guidelines:
- *string -> Suffix matching match threat names ending with ‘string’
- String* -> Prefix matching match threat names beginning with ‘string’
- *string* -> Substring matching match threat names containing ‘string’
- String -> Exact matching match threat names that are exactly ‘string’
Multiple strings are allowed. Enter one string per line. String search is not case-sensitive. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Advanced Threat Category**: Use this filter to limit the logs to specific threat categories. Choose the categories from the list.