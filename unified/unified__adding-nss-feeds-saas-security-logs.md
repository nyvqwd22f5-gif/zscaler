# Adding NSS Feeds for SaaS Security Logs
Source: https://help.zscaler.com/unified/adding-nss-feeds-saas-security-logs
PDF: https://help.zscaler.com/pdf/com/en/1496811.pdf

You can configure up to 16 Nanolog Streaming Service (NSS) feeds that define the SaaS Security logs that the NSS sends to the security information and event management (SIEM) system. You can also configure multiple types of filters. For example, if an admin selects the location *HQ* and the department *Finance*, the NSS selects logs that belong to both the HQ location and Finance department. A large number of filters or complex filters, such as string searches, can impact the performance of the NSS.
Before you start configuring a feed for SaaS Security logs, consider the [guidelines for configuring feeds](/unified/general-guidelines-nss-feeds-and-feed-formats).
To configure an NSS feed for SaaS Security logs:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
In the **NSS Feeds** tab, click **Add NSS Feed**.
The **Add NSS Feed** window appears.
- In the** Add NSS Feed** window:
- **Feed Name: **Enter or edit the name of the feed. Each feed is a connection between the NSS and your SIEM.
- **NSS Type**: **NSS for Web** is selected by default.
- **NSS Server**:** **Select an NSS server from the list. A [configured NSS server](/unified/adding-nss-servers-internet-saas) is required to add an NSS feed.
- **Status: **The NSS feed is **Enabled** by default. Choose **Disabled** if you want to activate it at a later time.
- **SIEM Destination Type**: Select the type of destination:
- **SIEM IP Address**:** **Enter the IP address of the SIEM to which the logs are streamed.
- **SIEM FQDN**: Enter the destination for the TCP connection to which the logs are streamed. This allows failover from one IP to the other without manual intervention, but rather relying on updating the DNS entry. The NSS re-resolves the FQDN only when the existing connection goes down. This feature cannot be used for DNS-based load balancing.
- **SIEM TCP Port**: Enter the port number of the SIEM to which the logs are streamed. Ensure that the SIEM is configured to accept the feed from the NSS.
- **SIEM Rate**: Leave as **Unlimited**, unless you need to throttle the output stream due to licensing or other constraints.
- **SIEM Rate Limit (Events per Second)**: This is only applicable if you selected **Limited** under SIEM Rate. Enter an appropriate rate limit for the events per second that you want to be streamed to your SIEM. This number must be between 100 and 1,000,000. A limit that is too low for the traffic volume causes log loss.
- **Log Type**:** **Choose **SaaS Security**.
- **Application Category**: Choose an application category to limit the data to a specific category:
- **Collaboration**
- Microsoft Teams
- Slack
- Webex Teams
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
- Google Cloud Platform
- Microsoft Azure
- **Repository**
- Bitbucket
- GitHub
- GitLab
- **Feed Output Type**:** **The output is a comma-separated (**CSV**) list by default. Choose **Tab-separated **to create a tab-separated list. Choose **Custom **to use a different delimiter, such as a dash, and enter the delimiter when you specify the feed output format. This menu also lists feed output types for specific SIEMs.
- **Feed Escape Character**: The Zscaler service hex encodes all non-printable ASCII characters that are in URLs when it sends logs to the NSS. Any URL character that is less than 0x21, or above 0x7E, is encoded as `%HH`. This ensures that your SIEM can parse the URLs in case they contain non-printable characters. For example, a `\n` char in a URL is encoded as `%0A`, and a space is encoded as `%20`. In this field, you can specify additional characters that you want to encode. For example, type a comma (,) to encode it as `%2C`. This is useful if you are using this character as your delimiter and want to ensure it does not cause erroneous delimitation. Note that the service encodes characters in URLs, hostnames, and referrer URLs only. If custom encoding was done for a record, the `%s{eedone}` field is `YES` for that record.
- **Feed Output Format**:** **These are the fields that are displayed in the output. Edit the default list. If you choose **Custom **as the **Feed Output Type**, change the delimiter as well. To learn more about the available fields and their syntax, see [NSS Feed Output Format: SaaS Security Logs](/unified/nss-feed-output-format-saas-security-logs).
- **Time Zone**:** **By default, this is set to the organization's time zone. The time zone you set applies to the time field in the output file. The time zone automatically adjusts to changes in daylight savings in the specific time zone. The configured time zone can be output to the logs as a separate field. The list of time zones is derived from the IANA Time Zone database. Direct GMT offsets can also be specified.
- **Duplicate Logs**: To ensure that no logs are skipped during downtime, specify the number of minutes that the NSS sends duplicate logs. Zscaler recommends setting the number to 5 minutes, or more if required. This allows the NSS to send up to 60 minutes (one hour) of logs to the SIEM after the connection is restored. To learn more, see [General Guidelines for NSS Feeds and Feed Formats](/unified/general-guidelines-nss-feeds-and-feed-formats#duplicate-logs-example).
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
- **File Source**: Filter logs based on the file source location. You can search for a specific file location (e.g., /All Files/10.65.1.220_2/compressed/test). Multiple entries are allowed.
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
- **External Collaborators**: Filter logs associated with specific collaborators outside of your organization. Multiple selections are allowed.
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
- **File Source**: Filter logs based on the file source location. You can search for a specific file location (e.g., /All Files/10.65.1.220_2/compressed/test). Multiple entries are allowed.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Internal Collaborators**: Filter logs associated with specific collaborators within your organization. Multiple selections are allowed.
- **External Collaborators**: Filter logs associated with specific collaborators outside of your organization. Multiple selections are allowed.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g.,10KB-1MB, 200).
- **File Source**: Filter logs based on their source location.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **Internal Collaborators**: Filter logs associated with specific collaborators within your organization. Multiple selections are allowed.
- **External Collaborators**: Filter logs associated with specific collaborators outside of your organization. Multiple selections are allowed.
- **Object Type**: Choose **Any **to inspect all object types or choose an object type
- **Object Name**: Filter logs to specific object names. You can enter multiple object names separated by commas.
- []**File Name**: Filter logs to specific file names. You can enter multiple file names separated by commas.
- **File Size**: Filter logs based on their file size. Enter either a specific size or a range with a dash. You can enter multiple values separated by commas. By default, the service uses bytes, but you can also specify KB, MB, GB, or TB (e.g., 10KB-1MB, 200).
- **File Source**: Filter logs based on their source location.
-
**Non-Provisioned Owner**: Filter logs associated with file owners (inside or outside your organization) who are not provisioned to Internet & SaaS services. Multiple selections are allowed.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, you can filter logs associated with that file owner under the **User** field.
- **External Collaborators**: Filter logs associated with specific collaborators outside of your organization. Multiple selections are allowed.
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