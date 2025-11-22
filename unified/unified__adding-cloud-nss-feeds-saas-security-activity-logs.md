# Adding Cloud NSS Feeds for SaaS Security Activity Logs
Source: https://help.zscaler.com/unified/adding-cloud-nss-feeds-saas-security-activity-logs
PDF: https://help.zscaler.com/pdf/com/en/1496881.pdf

Before you start configuring a feed for SaaS Security Activity logs, consider the [guidelines for configuring feeds](/unified/general-guidelines-nss-feeds-and-feed-formats).
By configuring a Cloud NSS feed for SaaS Security Activity logs, you can track activities (e.g., Create, Delete, Share, etc.) that users performed in your organization’s sanctioned SaaS applications. To track and view more information about your SaaS applications (e.g., specific file names, sources, and collaborators, application categories, detected policy threats, etc.), you can configure a [Cloud NSS feed for SaaS Security logs](/unified/adding-cloud-nss-feeds-saas-security-logs).
To configure a Cloud NSS feed for SaaS Security Activity logs:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
In the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
- In the** Add Cloud NSS Feed** window:
- **Feed Name: **Enter or edit the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **Status: **The NSS feed is **Enabled** by default. Choose **Disabled** if you want to activate it at a later time.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **SIEM Type**: Choose a SIEM type from the list.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload to the SIEM's best practice.
- **API URL**: Enter the HTTPS URL of the SIEM log collection API endpoint.
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **SaaS Security Activity**.
-
**Feed Output Type**:** **The output is **JSON** by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
If you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- **JSON Array Notation**: When **JSON** is selected, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format: Individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. Edit the default list. If you chose **Custom **as the **Feed Output Type**, change the delimiter as well. To learn more about the available fields and their syntax, see [NSS Feed Output Format: SaaS Security Activity Logs](/unified/nss-feed-output-format-saas-security-activity-logs).
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define the filters:
- **User**: Filter logs based on specific users that generated transactions. You can search for users by username or email address. There's no limit to the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Tenant**: Filter logs based on a specific application tenant. You can specify multiple tenants.
- **Activity**: Filter logs based on a specific activity. You can specify multiple types of activity.
- **Object 1 Type and Object 2 Type**: Filter logs based on the type of object (e.g., Organization). You can search for specific object types. If applicable, the activity can have a second object listed. The default option is **None**.
- Click **Save** and activate the change.