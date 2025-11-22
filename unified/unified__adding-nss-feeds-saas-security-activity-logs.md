# Adding NSS Feeds for SaaS Security Activity Logs
Source: https://help.zscaler.com/unified/adding-nss-feeds-saas-security-activity-logs
PDF: https://help.zscaler.com/pdf/com/en/1496816.pdf

You can configure up to 16 NSS feeds that define the SaaS Security Activity logs that the Nanolog Streaming Service (NSS) sends to the security information and event management (SIEM) system. You can also configure multiple types of filters. For example, if an admin selects the location *HQ* and the department *Finance*, the NSS selects logs that belong to both the HQ location and the Finance department. A large number of filters or complex filters, such as string searches, can impact the performance of the NSS.
Before you start configuring a feed for SaaS Security Activity logs, consider the [guidelines for configuring feeds](/unified/general-guidelines-nss-feeds-and-feed-formats).
By configuring an NSS feed for SaaS Security Activity logs, you can track activities (e.g., Create, Delete, Share, etc.) that users performed in your organization’s sanctioned SaaS applications. To track and view more information about your SaaS applications (e.g., specific file names, sources, and collaborators, application categories, detected policy threats, etc.), you can configure an [NSS feed for SaaS Security logs](/unified/adding-nss-feeds-saas-security-logs).
To configure an NSS feed for SaaS Security Activity logs:
- Go to **Logs **> **Log Streaming **>** Nanolog Streaming Service**.
-
In the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name: **Enter or edit the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **NSS Server**:** **Choose an NSS from the list.
- **Status: **The NSS feed is **Enabled** by default. Choose **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **Log Type**:** **Choose **SaaS Security Activity**.
- **Feed Output Type**:** **The output is a comma-separated (CSV) list by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. Edit the default list. If you chose **Custom **as the **Feed Output Type**, change the delimiter as well.To learn more about the available fields and their syntax, see [NSS Feed Output Format: SaaS Security Activity Logs](/unified/nss-feed-output-format-saas-security-activity-logs).
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/unified/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Define the filters:
- **User**: Filter logs to specific users that generated transactions. You can search for users by username or email address. There's no limit to the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Tenant**: Filter logs based on the specific application tenant. You can specify multiple tenants.
- **Activity**: Filter logs based on specific activity. You can specify multiple types of activity.
- **Object 1 Type and Object 2 Type**: Filter logs based on the type of object (e.g., Organization). You can search for specific object types. If applicable, the activity can have a second object listed. The default option is **None**.
- Click **Save** and activate the change.