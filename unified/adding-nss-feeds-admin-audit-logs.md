# Adding NSS Feeds for Admin Audit Logs
Source: https://help.zscaler.com/zia/adding-nss-feeds-admin-audit-logs
PDF: https://help.zscaler.com/pdf/com/en/1402711.pdf

It can take up to two hours for the audit logs to start streaming to the Nanolog Streaming Service (NSS) and your security information and event management (SIEM) system after the feed is configured.
You can configure up to 16 NSS feeds to specify the data from the Admin Audit logs that the NSS sends to the SIEM.
A large number of filters or complex filters, such as string searches, can impact the performance of the NSS. Before you start configuring a feed for Admin Audit logs, consider the [guidelines for configuring feeds](/zia/general-guidelines-nss-feeds-and-feed-formats).
If your organization has a policy to block unauthenticated traffic, ensure that Zscaler IP addresses are allowed in order to prevent streaming issues with Admin Audit logs. Zscaler IP addresses are included in the [Professional Services URL category](/zia/about-url-categories#Business). You can configure a policy that allows traffic in this category and then order the newly configured policy to take precedence over your existing policy that blocks unauthenticated traffic. Alternatively, you can:
- Configure a user-defined URL category that includes the following custom URL: [http://kproxy.hdeu1.zdataservices.net/](http://kproxy.hdeu1.zdataservices.net/)
- Configure a URL filtering policy that allows traffic in the user-defined URL category.
- Prioritize the new policy in the rule order. Rules are evaluated in ascending numerical order (i.e., Rule 1 before Rule 2, and so on).
To learn more, see [Configuring Custom URL Categories](/zia/adding-custom-url-categories) and [Configuring the URL Filtering Policy](/zia/configuring-url-filtering-policy).
To configure an NSS feed for Admin Audit logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
In the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name: **Enter the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/zia/adding-nss-servers) is required to add an NSS feed.
- **Status: **The NSS feed is **Enabled** by default. Choose **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as Unlimited, unless you need to throttle the output stream due to SIEM licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: Enter an appropriate rate limit for the events per second that you want to be streamed to your SIEM. A limit that is too low for the traffic volume can cause log loss. This field is available only if you have selected **Limited** in the **SIEM Rate **field.
- **Log Type**:** **Choose **Admin Audit**.
- **Feed Output Type**:** **The output is a comma-separated (**CSV**) list by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. You can edit the default list and if you choose **Custom **as the **Feed Output Type**, change the delimiter as well. See [NSS Feed Output Format: Admin Audit Logs](/zia/nss-feed-output-format-admin-audit-logs) for information about the available fields and their syntax.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/zia/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
- Define the filter:
- **Application**: Filter logs based on the specific application. You can specify multiple applications.
- **Branch Connector Portal Audit Log**: Allows real-time streaming of the Zscaler Cloud & Branch Connector Admin Portal audit logs to SIEM.
- **Client Connector Portal Audit Log**: Allows real-time streaming of the Zscaler Client Connector Portal audit logs to SIEM.
- **Risk360 Admin Portal Audit Log**: Allows real-time streaming of the Risk360 Admin Portal audit logs to SIEM.
- **ZDX Portal Audit Log**: Allows real-time streaming of the ZDX Admin Portal audit logs to SIEM.
- **ZIA Portal Audit Log**: Allows real-time streaming of the ZIA Admin Portal audit logs to SIEM.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).