# Adding Cloud NSS Feeds for Email DLP Logs
Source: https://help.zscaler.com/zia/adding-cloud-nss-feeds-email-dlp-logs
PDF: https://help.zscaler.com/pdf/com/en/1483221.pdf

To configure a Cloud NSS feed for Email Data Loss Prevention (DLP) logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
In the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
The **Add Cloud NSS Feed** window appears.
- In the** Add Cloud NSS Feed** window:
- **Feed Name: **Enter the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **Status: **The Cloud NSS feed is **Enabled** by default. Select **Disabled** if you want to activate it at a later time.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to SIEM licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: Enter an appropriate rate limit for the events per second that you want to be streamed to your SIEM. A limit that is too low for the traffic volume causes log loss. This field is available only if you select **Limited** in the **SIEM Rate **field.
- **SIEM Type**: Select a SIEM type from the list.
- **OAuth 2.0 Authentication**: This setting is enabled by default if it is applicable to the SIEM type.
- **Max Batch Size**: Enter a size limit for an individual HTTP request payload to the SIEM's best practice.
-
**API URL**: Enter the HTTP/S URL of the SIEM log collection API endpoint.
The HTTPS URL must be configured with a publicly trusted SSL certificate. Self-signed or internally issued certificates do not pass the SIEM connectivity test.
- **HTTP Headers**: Enter HTTP header information:
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Select **Email DLP**.
-
**Feed Output Type**:** **The output is **JSON** by default. Select **Tab-separated **to create a tab-separated list. Select **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the **Feed Output Format**.
If you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- **JSON Array Notation**: When **JSON** is selected, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format: Individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, enter a comma (`,`) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding is done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that display in the output. You can edit the default list and if you select **Custom **as the **Feed Output Type**, change the delimiter as well. See [NSS Feed Output Format: Email DLP Logs](/zia/nss-feed-output-format-email-dlp-logs) for information about the available fields and their syntax.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight saving in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define the filters:
- [Who](#zia-cloud-nss-email-dlp-who-filter)
- [DLP](#zia-cloud-nss-email-dlp-dlp-filter)
- [Action](#zia-cloud-nss-email-dlp-action-filter)
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