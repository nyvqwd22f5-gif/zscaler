# Adding NSS Feeds for Email DLP Logs
Source: https://help.zscaler.com/zia/adding-nss-feeds-email-dlp-logs
PDF: https://help.zscaler.com/pdf/com/en/1483216.pdf

You can configure up to 16 Nanolog Streaming Service (NSS) feeds to specify the data from the Email Data Loss Prevention (DLP) logs that the NSS sends to the security information and event management (SIEM) system.
A large number of filters or complex filters, such as string searches, can impact the performance of the NSS. Before you start configuring a feed for Email DLP logs, consider the [guidelines for configuring feeds](/zia/general-guidelines-nss-feeds-and-feed-formats).
To configure an NSS feed for Email DLP logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
In the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name: **Enter the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/zia/adding-nss-servers) is required to add an NSS feed.
- **Status: **The NSS feed is **Enabled** by default. Select **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination.
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **SIEM FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to SIEM licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: Enter an appropriate rate limit for the events per second that you want to be streamed to your SIEM. A limit that is too low for the traffic volume causes log loss. This field is available only if you select **Limited** in the **SIEM Rate **field.
- **Log Type**:** **Select **Email DLP**.
- **Feed Output Type**:** **The output is a comma-separated (**CSV**) list by default. Select **Tab-separated **to create a tab-separated list. Select **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the **Feed Output Format**.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, enter a comma (`,`) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding is done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that display in the output. You can edit the default list and if you select **Custom **as the **Feed Output Type**, change the delimiter as well. See [NSS Feed Output Format: Email DLP Logs](/zia/nss-feed-output-format-email-dlp-logs) for information about the available fields and their syntax.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight saving in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Define the filters:
- [Who](#zia-nss-email-dlp-who-filter)
- [DLP](#zia-nss-email-dlp-dlp-filter)
- [Action](#zia-nss-email-dlp-action-filter)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []**Users**: Use this filter to limit the logs to specific users (i.e., senders) who generated transactions. You can search for users by username or email address. There is no limit on the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Departments**: Use this filter to limit the logs to specific departments that generated transactions. You can search for departments. There is no limit on the number of departments that you can select. Departments that are deleted after they are selected appear with a strikethrough line.
- []**DLP Engines**: Use this filter to limit the logs to transactions in which data leakage was detected based on specific DLP engines. Multiple selections are allowed.
- **DLP Dictionaries**: Use this filter to limit the logs to transactions in which data leakage was detected based on specific DLP dictionaries. Multiple selections are allowed.
- **Record Type**: Use this filter to limit the logs based on record type. Multiple selections are allowed:
- **DLP Incident**: A violation of a DLP rule was detected.
- **Scan**: The scan is normal (i.e., no DLP rule violation or movement of sensitive data was detected.)
- **Sensitive Activity**: Movement of sensitive data was detected.
- []**Policy Action**: Use this filter to limit the logs to transactions that were either allowed or blocked by the Zscaler service. Select **Custom Header Insertion** to limit the logs to transactions that resulted in a different action (e.g., quarantine) taken by the email application (e.g., Microsoft Exchange) as defined by a custom header (e.g., X-Zscaler-Scan:Quarantine).
- **Severity**: Use this filter to limit the logs transactions associated with a specific DLP rule severity as configured in the Outbound Email Policy. Multiple selections are allowed.