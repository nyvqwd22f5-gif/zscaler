# SaaS Security Insights
Source: https://help.zscaler.com/zia/saas-security-insights
PDF: https://help.zscaler.com/pdf/com/en/1401386.pdf

The SaaS Security Insights page is where you can view and define information that you want to view when analyzing files scanned through charts. To learn more about how to analyze your traffic on the Insights pages, see [Analyzing Traffic Using Insights](/zia/analyzing-traffic-using-insights).
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account Team.
About the SaaS Security Insights Page
To view Insights, go to **Analytics** > **SaaS Security Insights**.
- View the [Logs](/zia/saas-security-insights-logs) tab.
- Clear all filters.
- Click to show or hide the left pane.
- Choose a predefined time frame or select **Custom** to use the calendar and time menus to define your own time frame.
- Select a chart type.
- View the data as **Units**. Depending on the application category you select, the unit is the number of scans, message scans, or file scans.
- Filter the data by application category. You can filter by **All**, **Collaboration**, **CRM**, **Email**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Depending on the application category you select, certain filters change accordingly. For example, if you select the application category **Email**, the **Application** filter only show you email apps.
- Define filters. Certain filters, like** Users**, **Departments**, **Locations**, and others, support the selection of multiple values. For these, you can select up to 200 values in a single filter. You can also choose to include or exclude the selected values. Following are the SaaS Security data types and their associated filters:
- [Advanced Threat Category](#advthreatcat)
- [Application](#app)
- [Application Category](#appcat)
- [Department](#dept)
- [DLP Dictionary](#dlpdictionary)
- [DLP Engine](#dlpengine)
- [Incident Type](#incidenttype)
- [Owner Name](#ownername)
- [Severity](#severity)
- [Tenant](#tenant)
- [Threat Super Category](#threatsupercat)
- [User](#user)
- Always click **Apply Filters** to activate your changes.
- Define data types. See the list in Step 8.
- For certain data types, you can choose to view the top 5, 10, 25, 50 or 100 items. For example, you can view the top 5 or 100 domains that were visited by your users. This option is available in bar charts and tables only.
- In trend and pie charts, you'll only see the top 5 items. The "Other" category refers to the rest of the data types not in the top 5.
- Print the entire sequence of charts in the history bar.
- View the chart and interactively drill down for more information.
- Narrow down the data scope by applying filters. Each data type has its own set of filters. See the data types and filters listed in Step 8.
- To get more information about a specific item in a chart, hover and click it, and then choose a data type.
- View logs for a specific item in the chart. Hover and click it, and then choose **View Logs**.
- View your workflow in the history bar.
As you work with your data, the History bar records the workflow. Each time you make a change to the chart (e.g., add a filter or change the chart type), the portal adds the previous version to the history bar. You can then click any chart in the history bar to see it again. If you view an earlier version and change it, all subsequent versions are automatically deleted. This enables an administrator to review the various stages of the investigation and change direction for the analysis upon review, if necessary. The history bar can retain up to 50 versions of the chart. If there are more than 50 versions, the portal deletes the oldest versions as new ones are added. The chart icons are numbered, so you can track how many versions you have. You can delete charts from your workflow.
- View the weblog time, which appears at the bottom of every window. The Nanolog servers collect the logs of all users worldwide, and then consolidates and correlates them. The weblog time displays the date and time of the logs that are being processed by the Nanolog servers.
![This image shows the SaaS Security Insights](/downloads/zia/dashboard-analytics/insights/saas-security-insights/SaaS_Security_Insights2.png)
[]Displays data about the detected viruses or spyware. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about SaaS applications. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about the application category (CRM, file, email, Gen AI, ITSM, or repository). You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about the web traffic of each department in your organization. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Threat Category**: Use this filter to view scans associated with a specific threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about scans in which data leakage was detected. The data is grouped according to the DLP (Data Loss Prevention) dictionaries that were used to detect data loss. You can apply the following filters:
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about scans in which data leakage was detected. The data is grouped according to the DLP (Data Loss Prevention) engines that were used to detect data loss. You can apply the following filters:
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about the incident type (DLP or Malware). You can apply the following filters:
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]When you select this data type, the **Application Category** section automatically changes to **Email**. Displays data about the owner of the mailbox where the questionable email is located. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
- **Application**: Use this filter to view scans associated with specific SaaS applications. The following apps appear under this filter:
- Exchange
- Gmail
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
[]Displays data about scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. You can apply the following filters:
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about tenants. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]Displays data about the detected viruses and spyware for each virus and spyware super category. You can apply the following filters:
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **Owner Name**: This filter only appears when the **Application Category** section is set to **Email**. Use this filter to view scans associated with the owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware). You can search for specific owners. You can choose to include or exclude certain owners.
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.
[]When you select this data type, the **Application Category** section automatically defaults to **File**, but the data type also works with **Collaboration**, **CRM**, **Gen AI**, **ITSM**, **Public Cloud Storage**, and **Repository**. Displays data about the owner of the questionable data. The trend chart does not support this data type. You can apply the following filters:
- **Advanced Threat Category**: Use this filter to view scans associated with a specific advanced threat category. These threats are detected by **Malware Protection**. The default option for this filter is **Any**. You can search for specific categories. The following categories appear under this filter:
- Advanced Browser Exploit
- Adware
- Adware/Spyware Sites
- Archive Bomb
- Backdoor
- Benign
- Boot Virus
- Botnet Callback
- Browser Exploit
- Cross-site Scripting
- Cryptomining
- Denial of Service Attack
- Dialer
- Downloader
- Macro Virus
- Malicious Content
- Malware Exploit
- MalwareTool
- Misdisinfection
- Other Malware
- Other Spyware
- Other Threat
- Other Virus
- Password Stealer
- Peer-to-Peer
- Phishing
- Privacy Risk
- Proxy
- Ransomware
- Sandbox Adware
- Sandbox Anonymizer
- Sandbox Malware
- Sent for Analysis
- Spyware Callback
- Suspicious Content
- Suspicious Destination
- Trojan
- Unauthorized Communication
- Unrecognized Virus
- Unwanted Application
- Web Spam
- Worm
-
**Application**: Use this filter to view scans associated with specific SaaS applications.
The following app appears when the **Application Category** section is set to **All** or **Collaboration**:
- Microsoft Teams
- Slack
- Webex Teams
- Zoom
The following app appears when the **Application Category** section is set to **All** or **CRM**:
- Salesforce
- Dynamic 365
The following apps appear when the **Application Category** section is set to **All** or **Email**:
- Exchange
- Gmail
The following apps appear when the **Application Category** section is set to **All** or **File**:
- Box
- Confluence
- Dropbox
- Google Drive
- OneDrive
- ShareFile
- SharePoint
- Smartsheet
The following app appears when the **Application Category** section is set to **None **or **Gen AI**:
- ChatGPT
The following apps appear when the **Application Category** section is set to **All** or **ITSM**:
- Jira Software
- ServiceNow
The following app appears when the **Application Category** section is set to **All** or **Public Cloud Storage**:
- Amazon S3
- Google Cloud Platform
- Microsoft Azure
The following app appears when the **Application Category** section is set to **All** or **Repository**:
- Bitbucket
- GitHub
- GitLab
- **Department**: Use this filter to view scans associated with a specific department. The default option for this filter is **Any**. You can search for specific departments. You can choose to include or exclude certain departments.
- **DLP Dictionary**: Use this filter to see which scans contain this dictionary as a trigger. If a dictionary was triggered, the name of the dictionary is displayed along with a match count indicating the search score or match count for this dictionary. The default option for this filter is **None**. You can search for specific DLP dictionaries.
- **DLP Engine**: Use this filter to view scans associated with specific DLP engine. The default option for this filter is **Any**. You can search for specific DLP engines.
- **Incident Type**: Use this filter to view scans associated with a specific incident type. The following policy types appear under this filter:
- DLP
- Malware Detection
- **Severity**: Use this filter to view scans associated with the severity level of the incidents detected by the SaaS Security API DLP policy. The following severity levels appear under this filter:
- High
- Information
- Low
- Medium
- **Tenant**: Use this filter to view scans associated with a specific tenant. The default option for this filter is **All**. You can search for specific tenants.
- **Threat Super Category**: Use this filter to view scans associated with a specific threat super category. The default option for this filter is **None**. The following categories appear under this filter:
- Advanced Threat
- Malware Detection
- Sandbox
- Spyware
- Virus
- **User**: This filter only appears when the **Application Category** section is set to **Collaboration**, **CRM**, **File**, **Gen AI**, **ITSM**, **Public Cloud Storage**, or **Repository**. Use this filter to view scans associated with the owner of the questionable data. The default option for this filter is **Any**. You can search for specific file owners. You can choose to include or exclude certain file owners.