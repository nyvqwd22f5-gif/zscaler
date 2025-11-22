# Email DLP Insights Logs: Filters
Source: https://help.zscaler.com/unified/email-dlp-insights-logs-filters
PDF: https://help.zscaler.com/pdf/com/en/1503456.pdf

Filters define the traffic information that you view in your Email Data Loss Prevention (DLP) Insights Logs. To learn more about logs, see [About Insights Logs](/unified/about-insights-logs).
Certain filters, like** **User, Department, and others, support the selection of multiple values. You can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Some filters support additional operators (i.e., Contains, Starts With, Ends With, Exact Match, Does Not Contain, Does Not End With, Does Not Start With, Not Null, or Is Null) for filters that perform string matches.
Following are the Email DLP Insights Logs filters that you can select:
- **Action Taken**: Use this filter to limit the data to activities associated with a specific action taken. The following actions appear under this filter:
- Allow
- Block
- Custom Header Insertion
- **Application**: Use this filter to limit the emails of a specific application.
- **Attachment Size**: Use this filter to limit emails based on a specific attachment size.
- All Sizes
- 0–1 KB
- 1 KB–100 KB
- 100 KB–1 MB
- 1 MB–5 MB
- 5 MB–10 MB
- 10 MB–50 MB
- 50 MB–100 MB
- Above 100 MB
- Custom
- **Department**: Use this filter to limit the emails of a specific [department](/unified/about-departments). Use the Search function to find a specific department.
- **Dictionary Count**: Use this filter to see the number of times a dictionary was triggered.
- **DLP Dictionaries**: Use this filter to see which email contains a particular dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view emails in which data leakage was detected. The default option for this filter is **None**. You can search for specific DLP engines.
- **DLP Identifier**: Use this filter to search for the emails using this DLP identifier. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors. Use it as a filter to locate the exact email. You can search for specific DLP identifiers.
- **Document Type**: Use this filter to limit email traffic associated with a specific uploaded or downloaded document type. The following document types appear under this filter:
- Corporate Finance
- Corporate Legal
- Court Form
- Immigration
- Insurance
- Invoice
- Legal
- Medical Information
- Real Estate
- Resume
- Tax
- Technical
- Transportation and Motor Department
- Unknown
- **External Users**: Use this filter to limit the email activities of a user who sent the email, but is not provisioned to Internet & SaaS.
- **File MD5**: Use this filter to enter the 32-character file MD5 in the text field.
- **File Name:** Use this filter to limit emails by specific file name. Enter all or part of the file name in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Does Not Start With**,** Not Null**, or **Is Null**.
- **File Types**: Use this filter to limit emails by specific file types.
- **Message ID:** Use this filter to limit emails by the unique email message identifier. Enter all or part of the message ID in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Does Not Start With**,** Not Null**, or **Is Null**.
- **Other Domains**: Use this filter to limit emails from domains that did not trigger an incident.
- **Other Recipients**: Use this filter to limit emails from recipients who did not trigger an incident.
- **Record Type**: Use this filter to limit the email activities associated with a specific record type. The following record types appear under this filter:
- DLP Incident
- Scan
- Sensitive Activity
- **Rule Name**: Use this filter to limit emails associated with specific rules in the Email DLP policy. Choose the rules from the list.
- **Scan Time**: Use this filter to limit emails associated within a specific range of time. The following scan time appears under this filter:
- All
- 0–10 Sec
- 10 Sec–30 Sec
- 30 Sec–1 Min
- 1 Min–5 Min
- 5 Min–10 Min
- 10 Min–30 Min
- 30 Min–1 Hour
- Above 1 Hour
- Custom
- **Severity**: Use this filter to limit emails associated with a specific rule severity. The following severities appear under this filter:
- High
- Information
- Low
- Medium
- **Subject**: Use this filter to limit emails by a specific subject. Enter all or part of the message ID in the text field, and choose **Contains**, **Starts With**, **Ends With**, **Exact Match**, **Does Not Contain**, **Does Not End With**, **Does Not Start With**,** Not Null**, or **Is Null**.
- **Tenant**: Use this filter to limit emails by a specific tenant.
- **Triggered Domains**: Use this filter to limit emails associated to a specific triggered domain.
- **Triggered Recipients**: Use this filter to limit emails associated to a specific triggered recipient.
-
**User**: Use this filter to view email activities of a specific user. The default option for this filter is **Any**. You can search or choose users from the list.