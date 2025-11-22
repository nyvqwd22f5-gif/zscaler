# Adding Cloud NSS Feeds for SaaS Security Logs
Source: https://help.zscaler.com/unified/adding-cloud-nss-feeds-saas-security-logs
PDF: https://help.zscaler.com/pdf/com/en/1496871.pdf

To configure a Cloud NSS feed for SaaS Security logs:
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
-
**API URL**: Enter the HTTP/S URL of the SIEM log collection API endpoint.
The HTTPS URL must be configured with a publicly trusted SSL certificate. Self-signed or internally issued certificates do not pass the SIEM connectivity test.
- **HTTP Headers**: Enter HTTP header information:
- **Key 1**: Enter the key for the HTTP header.
- **Value 1**: Enter the token value for the HTTP header.
- **Add HTTP Header**: Click to add more HTTP headers (keys and values).
- **Log Type**:** **Choose **SaaS Security**.
- **Application Category**: Choose an application category to limit the data to a specific category:
- **Collaboration**
- Microsoft Teams
- Slack
- Zoom
- **CRM**
- Salesforce
- Microsoft Dynamics 365
- **Email**
- Gmail
- Microsoft Exchange
- **File**
- Box
- Citrix ShareFile
- Confluence
- Dropbox
- Google Drive
- Microsoft OneDrive
- Microsoft SharePoint
- Smartsheet
- **Gen AI**
- ChatGPT
- **ITSM**
- Jira Software
- ServiceNow
- **Public Cloud Storage**
- Amazon S3
- **Repository**
- Bitbucket
- GitHub
- GitLab
-
**Feed Output Type**:** **The output is **JSON** by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
If you select **JSON** as the **Feed Output Type**, special characters such as `\` present in string fields may cause a parsing issue for your SIEM. To prevent the issue, enter `,\"` as the **Feed Escape Character** and use hex encoded fields (e.g., `%s{elogin}`instead of `%s{login}`) in the **Feed Output Format**`.`
- **JSON Array Notation**: When **JSON** is selected, the **JSON Array Notation** setting is enabled by default. This setting allows the NSS to stream a batch of logs in a JSON Array format: Individual logs are ordered in a list, separated by commas, and surrounded by square brackets (e.g., [\{JSON1},\{JSON2}]). You can disable this setting.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM is able to parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. Edit the default list. If you chose **Custom **as the **Feed Output Type**, change the delimiter as well. To learn more about the available fields and their syntax, see [NSS Feed Output Format: SaaS Security Logs](/unified/nss-feed-output-format-saas-security-logs).
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- Define the filters:
- [Action](#action)
- [Who](#who)
- [Collaboration](#collaboration)
- [CRM](#CRM)
- [Email](#Email)
- [File](#file)
- [ITSM](#ITSM)
- [Public Cloud Storage](#pcs)
- [Repository](#Repository)
- [DLP](#dlp)
- [Malware](#malware)
- [Application](#application)
- Click **Save** and activate the change.
-
[]**Policy Type**: Filter logs based on the specific policy type. You can specify multiple policies.
By default, the DLP and Malware policy types are not selected. Therefore, all incidents and violations with or without a rule name are exported through the NSS. You must explicitly select DLP and Malware policy types from the list to export only the incidents with valid rule names through the NSS.
- **Policy Action**: Filter logs based on the specific policy action taken. You can specify multiple policy actions.
- **Scan Time**: Filter logs based on the time the Data at Rest Scanning policy took to scan content within the tenant. Enter either a specific value or a range with a dash. The default unit of measure is milliseconds, but you can specify this unit using either MS or SEC (e.g., 10MS-100MS).
- **Download Time**: Filter logs based on the file download time. Enter either a specific value or a range with a dash. The default unit of measure is milliseconds, but you can specify this unit using either MS or SEC (e.g., 10MS-100MS).
-
**Event**: Select one of the following event types:
- **Any**: Any type of event in the scan.
- **Incident**: A violation was detected in the scan and a configured DLP or malware rule was also triggered.
- **Scan**: No violation was detected in the scan. The scan is considered normal.
- **Violation**: A violation was detected in the scan (i.e., either a DLP engine was matched or malware was detected.)
A previous version of the **Event** filter, available for Internet & SaaS 6.2 and earlier, does not include **Violation** as an option. Any NSS feed that you previously configured using the earlier version of the filter remains supported until you make any edits or changes to the feed. The **Event** filter is then replaced by the latest version, which includes the **Violation** option. All newly configured NSS feeds support the latest version of the filter by default.
- []**Users**: Filter logs to specific users that generated transactions. You can search for users by username or email address. There's no limit to the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- **Departments**: Filter logs to specific departments that generated transactions. You can search for users by username or email address. There's no limit to the number of users that you can select. Users that are deleted after they are selected appear with a strikethrough line.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g., 10KB-1MB, 200).
- **File Source**: Filter logs based on the file source location. You can search for a specific file location (e.g., `/All Files/10.65.1.220_2/compressed/test`). Multiple entries are allowed.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Bucket Name**: Filter logs to specific bucket names. You can enter multiple bucket names separated by commas.
- []**External Recipients**: Filter logs to specific recipients outside your organization. Multiple selections are allowed.
- **Internal Recipients**: Filter logs to specific recipients within your organization. Multiple selections are allowed.
- **Channel Name**: Filter logs to specific channel names. You can enter multiple channel names separated by commas.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g.,10KB - 1MB, 200).
- **File Source**: Filter logs based on their source location.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Internal Collaborators**: Filter logs associated with specific collaborators within your organization. Multiple selections are allowed.
- **External Collaborators**: Filter logs associated with specific collaborators outside your organization. Multiple selections are allowed.
- **Object Type**: Choose **Any **to inspect all object types or choose an object type
- **Object Name**: Filter logs to specific object names. You can enter multiple object names separated by commas.
- []**Message Size**: Filter logs by the size of the email message.
-
**Non-Provisioned Owner Name**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **External Recipients**: Filter logs to specific recipients outside your organization. Multiple selections are allowed.
- **Internal Recipients**: Filter logs to specific channel names. You can enter multiple channel names separated by commas.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g., 10KB-1MB, 200).
- **File Source**: Filter logs based on the file source location. You can search for a specific file location (e.g., `/All Files/10.65.1.220_2/compressed/test`). Multiple entries are allowed.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Internal Collaborators**: Filter logs associated with specific collaborators within your organization. Multiple selections are allowed.
- **External Collaborators**: Filter logs associated with specific collaborators outside your organization. Multiple selections are allowed.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g.,10KB-1MB, 200).
- **File Source**: Filter logs based on their source location.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Internal Collaborators**: Filter logs associated with specific collaborators within your organization. Multiple selections are allowed.
- **External Collaborators**: Filter logs associated with specific collaborators outside your organization. Multiple selections are allowed.
- **Object Type**: Choose **Any **to inspect all object types or choose an object type
- **Object Name**: Filter logs to specific object names. You can enter multiple object names separated by commas.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g., 10KB-1MB, 200).
- **File Source**: Filter logs based on their source location.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **External Collaborators**: Filter logs associated with specific collaborators outside your organization. Multiple selections are allowed.
- **Project Name**: Filter logs to specific project names. You can enter multiple project names separated by commas.
- **Repository Name**: Filter logs to specific repository names. You can enter multiple repository names separated by commas.
- []**DLP Engines**: Filter logs to transactions in which data leakage was detected based on specific [DLP engines](/unified/about-dlp-engines). Multiple selections are allowed.
- **DLP Dictionaries**: Filter logs to transactions in which data leakage was detected based on specific [DLP dictionaries](/unified/about-dlp-dictionaries). Multiple selections are allowed.
- **Severity**: Choose the severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- []**Malware Classes**: Filter logs based on the specific malware class. You can specify multiple malware classes.
- **Malware Names**: Filter logs based on the specific malware names. You can specify multiple malware names.
- **Threat Name**: Filter logs based on specific threats that were detected. You can specify multiple threat names separated by commas.
- []**SaaS Application**: Filter logs based on the specific sanctioned SaaS application. You can specify multiple applications.
- **SaaS Application Tenant**: Filter logs based on the specific SaaS application tenant. You can specify multiple tenants.