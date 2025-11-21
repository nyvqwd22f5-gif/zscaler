# Adding Cloud NSS Feeds for Web Logs
Source: https://help.zscaler.com/zia/adding-cloud-nss-feeds-web-logs
PDF: https://help.zscaler.com/pdf/com/en/1401861.pdf

To configure a Cloud NSS feed for web logs:
- Go to **Administration **>** Nanolog Streaming Service**.
-
On the **Cloud NSS Feeds** tab, click **Add Cloud NSS Feed**.
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
-
**API URL**: Enter the HTTP/S URL of the SIEM log collection API endpoint.
The HTTPS URL must be configured with a publicly trusted SSL certificate. Self-signed or internally issued certificates do not pass the SIEM connectivity test.
- **HTTP Headers**: Enter HTTP header information:
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **Web Log**.
-
**Feed Output Type**:** **The output is **JSON** by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
If you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- **JSON Array Notation**: When **JSON** is selected, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format: Individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. Edit the default list. If you chose **Custom **as the **Feed Output Type**, change the delimiter as well. See [NSS Feed Output Format: Web Logs](/zia/nss-feed-output-format-web-logs) for information about the available fields and their syntax.
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define the filters:
- [Action](#Action)
- [Who](#Who)
- [From Where](#Fwhere)
- [Transaction](#Transaction)
- [To Where](#Twhere)
- [Security](#Security)
- [File Type](#File)
- [DLP](#DLP)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
- []**Policy Action**: Use this filter to limit the logs to transactions that were either allowed or blocked. Transactions wherein the service displayed a Caution page are considered blocked transactions; if users proceeded with the transactions, they are considered allowed.
- **Policy Reason**: Use this filter to limit the logs based on the policy that the Zscaler service applied. These are the policy reason strings that are in transaction drilldown. They indicate which policy caused a block, or if allowed, the conditions under which they were allowed, such as **Allowed due to override **and** Internet Access cautioned**. Multiple selections are allowed.
- []**Users**: Use this filter to limit the logs to specific users who generated transactions. You can search for users by username or email address. There is no limit on the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Departments**: Use this filter to limit the logs to specific departments that generated transactions. You can search for departments. There is no limit on the number of departments that you can select. Departments that are deleted after they are selected appear with a strikethrough line.
- []**Locations**: Use this filter to limit the logs to specific [locations](/zia/about-locations) from which transactions were generated. You can search for locations. There is no limit on the number of locations that you can select. Locations that are deleted after they are selected appear with a strikethrough line.
- **Location Groups**: Use this filter to limit the logs to specific [location groups](/zia/about-location-groups) from which transactions were generated. You can search for location groups. Multiple selections are allowed.
-
**Client IP Addresses**: Use this filter to limit the logs based on a client’s private IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Public IP Addresses**: Use this filter to limit the logs based on a client’s public IP address. The internal IP address is available if traffic forwarding is forwarded to the service through a GRE or VPN tunnel or from the XFF header. If the internal IP address is not available, the value is the same as the client IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Traffic Forwarding**: Use this filter to limit the logs based on the traffic forwarding method used to send traffic to the Zscaler service. Choose one or more of the listed methods, or choose **Any**.
- []**Direction**: Use this filter to limit the logs to either inbound or outbound traffic.
- **User Agents**: Use this filter to limit the logs to transactions associated with the user-agent string that the browser included in its GET request. Choose from the list of predefined user-agent strings or enter custom user-agent strings. Multiple selections are allowed.
- **Custom User Agent Strings**: Use this filter to limit the logs to specific user-agent strings. A user-agent string contains browser and system information that the destination server can use to provide appropriate content.
- **Protocol Types**: Use this filter to limit the logs to specific protocols. Supported protocols are HTTP, HTTPS, and FTP. Multiple selections are allowed.
- **Request Methods**: Use this filter to limit the logs based on the HTTP request method obtained from the client request. Multiple selections are allowed.
- **Response Codes**: Use this filter to limit the logs based on the HTTP response code obtained from the server or generated by the ZIA Public Service Edge. Multiple selections are allowed.
- **Request Sizes**: Use this filter to limit the logs based on HTTP request size. Enter either a specific size or a range with a dash. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g.,**10KB-1MB, 200)**. You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Response Sizes**: Use this filter to limit the logs based on HTTP response size. Enter either a specific size or a range with a dash. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g., **10KB-1MB, 200)**.** **You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Transaction Sizes**: Use this filter to limit the logs based on transaction size, which is the header and body request or response size, or the request and response size. Enter either a specific size or a range with a dash. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g.,**10KB-1MB, 200**).** **You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
-
**Referer URLs**: Use this filter to limit the logs based on the Referer URL in the HTTP header. You can use wildcards based on the rules:
- *string -> Suffix matching match URLs ending with ‘string’
- String* -> Prefix matching match URLs beginning with ‘string’
- *string* -> Substring matching match URLs containing ‘string’
- String -> Exact matching match URLs that are exactly ‘string’
Multiple strings are allowed. Enter one string per line, then click **Add Items**. String search is not case-sensitive. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- []**URL Filter Type**: Use this filter to limit the logs based on URLs in HTTP Requests. You can specify either a **Hostname** or the **Full URL**. You can use wildcards based on the rules:
- String -> Exact matching match URLs that are exactly ‘string’
- *string* -> Substring matching match URLs containing ‘string’
- String* -> Prefix matching match URLs beginning with ‘string’
- *string -> Suffix matching match URLs ending with ‘string’
- **Hostnames**: This is only applicable if you select **Hostname **under **URL Filter Type**. Use this filter to limit the logs based on specific hostnames. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Full URLs**: This is only applicable if you select **Full URL** under **URL Filter Type**. Use this filter to limit the logs based on specific URLs. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **URL Classes**: Use this filter to limit the logs to specific [URL classes](/zia/about-url-categories). Select those that you want to include. Multiple selections are allowed.
- **URL Super Categories**: Use this filter to limit the logs to specific [URL super categories](/zia/about-url-categories). Select those that you want to include. Multiple selections are allowed.
-
**URL Categories**:** **Use this filter to limit the logs to specific [URL categories](/zia/about-url-categories). Select those that you want to include. Multiple selections are allowed.
The URL Categories filter falls under the same filter class as the Advanced Threats filter. This means if you select at least one advanced threat, then you must also select the specific URL categories that you want included in the logs. When you select at least one advanced threat, the default **Any** option in the URL Categories filter does not apply. In this case, you must select all the options in the URL Categories filter to include any possible URL categories in the logs.
-
**Server IP Addresses**: Use this filter to limit the logs based on the destination server’s IP address. You can enter:
- An IP address (e.g., 198.51.100.100)
- A range of IP addresses (e.g., 192.0.2.1-192.0.2.10)
- An IP address with a netmask (e.g., 203.0.113.0/24)
You can enter multiple entries. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Cloud Application Classes**: Use this filter to limit the logs to the selected [cloud application classes](/zia/cloud-app-categories). Multiple selections are allowed.
-
**Cloud Applications**: Use this filter to limit the logs to selected [cloud applications](/zia/cloud-app-categories). Multiple selections are allowed.
- **Include**: Use this filter to include selected cloud applications in the logs. This filter is enabled by default. The default value for this filter is **Any**.
- **Exclude**: Use this filter to exclude selected cloud applications from the logs. The default value for this filter is **None**.
The Miscellaneous <Cloud Application Category> Apps (e.g., Miscellaneous Finance Apps) option in this filter represents all the newly added lesser-known predefined applications for the category (e.g., Finance). Use the Search function to view and select the available Miscellaneous <Cloud Application Category> Apps options. To view the list of supported applications for each category, see [Viewing Supported Cloud Applications](/zia/understanding-cloud-app-categories).
- **Application Segment**: Use this filter to limit the logs to specific [application segments](/zpa/about-applications). The default option for this filter is **Any**.
- []**Malware Classes**: Use this filter to limit the logs based on malware class or name. Multiple selections are allowed.
- **Malware Names**: Use this filter to limit the logs based on specific malware or viruses that were detected. You can specify multiple malware or virus names. Use the Search function to search for either. Use the guidelines:
- *string -> Suffix matching match malware names ending with ‘string’
- String* -> Prefix matching match malware names beginning with ‘string’
- *string* -> Substring matching match malware names containing ‘string’
- String -> Exact matching match malware names that are exactly ‘string’
Multiple strings are allowed. Enter one string per line. String search is not case-sensitive.
-
**Advanced Threats**: Use this filter to limit the logs based on the types of advanced threats that were detected. Multiple selections are allowed.
The Advanced Threats filter falls under the same filter class as the URL Categories filter. This means if you select at least one URL category, then you must also select the specific advanced threats that you want included in the logs. When you select at least one URL category, the default **Any** option in the Advanced Threats filter does not apply. In this case, you must select all the options in the Advanced Threats filter to include any possible advanced threats in the logs.
-
**Threat Names**: Use this filter to limit the logs based on specific threats that were detected. You can specify multiple threat names. Use the Search function to search with the guidelines:
- *string -> Suffix matching match threat names ending with ‘string’
- String* -> Prefix matching match threat names beginning with ‘string’
- *string* -> Substring matching match threat names containing ‘string’
- String -> Exact matching match threat names that are exactly ‘string’
Multiple strings are allowed. Enter one string per line. String search is not case-sensitive. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- **Suspicious Content**: Use this filter to limit the logs based on the [Page Risk Index score](/zia/about-advanced-threats-protection) of a transaction. Enter either a single value or a range of values, between 0 and 100. Multiple values are allowed. Press `Enter` after each entry, then click **Add Items**. For item lists, you can view up to 500 items on a page; filter the list by searching for a word, phrase, or number contained in an item; and remove all items from the list (**Remove All**) or only items from a specific page (**Remove Page**). If you select **Remove All** or **Remove Page**, a confirmation window appears.
- []**Download File Type Category**: Use this filter to limit the logs based on the [category of the type of file downloaded](/zia/about-file-type-control) during the transaction. Multiple selections are allowed.
- **Download File Type**: Use this filter to limit the logs based on the [type of file downloaded](/zia/about-file-type-control) during the transaction. Multiple selections are allowed.
- **Upload File Type Category**: Use this filter to limit the logs based on the [category of the type of file uploaded](/zia/about-file-type-control) during the transaction. Multiple selections are allowed.
- **Upload File Type**: Use this filter to limit the logs based on the [type of file uploaded](/zia/about-file-type-control) during the transaction. Multiple selections are allowed.
- **Download User-Defined File Type**: Use this filter to limit the logs based on the [user-defined type of file](/zia/configuring-file-type-control-policy) downloaded during the transaction. Multiple selections are allowed. To learn more, see [Configuring Custom File Types](/zia/configuring-custom-file-types).
- **Upload User-Defined File Type**: Use this filter to limit the logs based on the [user-defined type of file](/zia/configuring-file-type-control-policy) uploaded during the transaction. Multiple selections are allowed. To learn more, see [Configuring Custom File Types](/zia/configuring-custom-file-types).
- **Unscannable Type**: Use this filter to limit the logs based on an unscannable file type. Multiple selections are allowed. The following options appear under this filter:
- **Encrypted File**: Encrypted or password-protected (e.g., GZIP, PDF)
- **Undetectable File**: Unable to determine the file type, based on multiple methods
- **Unscannable File**: Unscannable (e.g., corrupt archive)
- []**DLP Engines**: Use this filter to limit the logs to transactions in which data leakage was detected based on specific [DLP engines](/zia/about-dlp-engines). Multiple selections are allowed.
- **DLP Dictionaries**: Use this filter to limit the logs to transactions in which data leakage was detected based on specific [DLP dictionaries](/zia/about-dlp-dictionaries). Multiple selections are allowed.