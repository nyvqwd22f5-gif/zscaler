# Adding NSS Feeds for DNS Logs
Source: https://help.zscaler.com/zia/adding-nss-feeds-dns-logs
PDF: https://help.zscaler.com/pdf/com/en/1399086.pdf

You can configure up to 16 Nanolog Streaming Service (NSS) feeds to specify the data from the DNS logs that the NSS sends to the security information and event management (SIEM) system. For each feed, you can configure multiple types of filters. For example, you can configure separate feeds for each location or for different policy rules. A large number of filters or complex filters, such as string searches, can impact the performance of the NSS.
Before you start configuring a feed for DNS logs, consider the [guidelines for configuring feeds](/zia/general-guidelines-nss-feeds-and-feed-formats).
To configure an NSS feed for DNS logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
On the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name**:** **Enter or edit the name of the feed. Each feed is a connection between the NSS and your SIEM.
-
**NSS Type**: Select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/zia/adding-nss-servers) is required to add an NSS feed.
- **Status**: It is** Enabled** by default. Click **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **Log Domain**:
- If you want to configure NSS for ZIA DNS logs, choose **Firewall** and follow the successive steps.
- If you want to configure NSS for Cloud & Branch Connector logs, choose **Cloud & Branch Connector **and see [Adding NSS Feeds](/cloud-branch-connector/adding-nss-feeds) for applicable log types.
- **Log Type**: Choose **DNS Logs.**
- **Feed Output Type**:** **The output is a comma-separated (**CSV**) list by default. You can choose **Name-Value Pairs** or **Tab-separated**, if your SIEM accepts any of these formats.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**: These are the fields that are displayed in the output. See [NSS Feed Output Format: DNS Logs](/zia/nss-feed-output-format-dns-logs) for information about the available fields and their syntax.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Define the filters:
- [Action](#Action)
- [Who](#Who)
- [Source](#Source)
- [Destination](#Destination)
- [Session](#Session)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []**Policy Actions**
- **Allow**: Use this filter to limit the logs to allowed DNS requests and responses.
- **Block**: Use this filter to limit the logs to DNS requests and responses that the service dropped.
- **Redirect**: Use this filter to limit the logs to transactions wherein the service redirected the DNS request or response.
- **Request Allow**: Use this filter to limit the logs to allowed DNS requests only.
- **Request Block**: Use this filter to limit the logs to DNS requests that the service dropped.
- **Request Redirect**: Use this filter to limit the logs to DNS requests that the service redirected.
- **Response Allow**: Use this filter to limit the logs to allowed DNS responses only.
- **Response Block**: Use this filter to limit the logs to DNS responses that the service dropped.
- **Response Redirect**: Use this filter to limit the logs to DNS responses that the service redirected.
- **Rule Names**: Use this filter to limit the logs based on specific rules in the [DNS Control policy](/zia/configuring-dns-control-policy). Choose the rules from the list.
- []**Users**: Use this filter to limit the logs to specific users who generated transactions. To use the Search function, enter either the username or email address in the Search box and click **Search**. There is no limit on the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Departments**: Use this filter to limit the logs to specific departments that generated transactions. To use the Search function, enter the department name in the Search box and click **Search**. There is no limit on the number of departments that you can select. Departments that are deleted after they are selected appear with a strikethrough line.
- []**Locations**: Use this filter to limit the logs to specific [locations](/zia/about-locations) and [sublocations](/zia/understanding-sublocations). To use the Search function, enter the location name in the Search box and click **Search**. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Location Groups**: Use this filter to limit the logs to specific [location groups](/zia/about-location-groups) from which transactions were generated. You can search for location groups. Multiple selections are allowed.
-
**Client IP Addresses**: Use this filter to limit the logs based on a client’s IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
[]**Server IP Addresses**: Use this filter to limit the logs to specific server IP addresses. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Server Ports**: Use this filter to limit the logs to specific server ports. You can specify individual ports and a range of ports. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **IP Domain Classes**: Use this filter to limit the logs to specific [URL classes](/zia/about-url-categories) with the domain in the request.
- **IP Domain Super Categories**: Use this filter to limit the logs to specific [URL super categories](/zia/about-url-categories) with the domain in the request.
- **IP Domain Categories**: Use this filter to limit the logs to specific [URL categories](/zia/about-url-categories) associated with the domain in the request.
- []**Domains**: Use this filter to limit the logs to sessions associated with specific domains. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **DNS Request Types**: Use this filter to limit the logs to sessions associated with specific DNS request types.
- **DNS Response Codes**: Use this filter to limit the logs to sessions associated with specific DNS response codes.
-
**DNS Responses**: Use this filter to limit the logs to sessions that contained specific data in the DNS responses. You can specify domain names, IPv4 and IPv6 addresses. For IPv4 addresses, you can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries separated by commas. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Durations**: Use this filter to limit the logs based on the duration of the sessions, in seconds. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.