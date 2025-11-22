# Understanding the Assets Report: Assets with Incidents
Source: https://help.zscaler.com/unified/understanding-assets-report-assets-with-incidents
PDF: https://help.zscaler.com/pdf/com/en/1533575.pdf

When you click to further analyze an application or tenant on the main [SaaS Assets Report](/unified/about-assets-report) page, you are redirected to the Assets with Incidents page, which provides a comprehensive view of each selected application and tenant. The filters are preset to the application or tenant, and time frame you choose to further analyze, but you can click **Reset** at any time. You can also go back to the main SaaS Assets Report page by clicking the **Back** icon next to the page's title.
To view your assets with incidents:
- Select the individual **Application** you’d like to analyze.
- Select which **Tenant** you’d like to analyze. You can choose **All Tenants** or specific ones. You can also search for tenants.
- Select to view a **Current Scan**, a **Previous Scan**, or **All Scans**.
- Select to view the scans for a particular time frame. You can choose to view scans for the current day, the current week, the last 24 hours, the last 7 days, or choose a custom time frame.
- Once you select your **Application**, **Tenant**, **Scan**, and scan time, click **Apply** to update the page with your selections. You can click **Reset** at any time.
- You can export the data.
![The Export button in the Assets with Incidents page, which is part of the SaaS Assets Report](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Assets-with-Incidents-Export.png)
Collaboration Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Messages](#messages-collab)
- [Senders](#senders-collab)
- [Show Advanced Filters](#collabadvancedfilters)
CRM Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Objects](#objects-crm)
- [Owners](#owners-crm)
- [Collaborators](#collaborators-crm)
- [Show Advanced Filters](#crm-advancedfilters)
Email Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Email Messages](#emailmessages)
- [Senders](#senders)
- [Recipients](#recipients)
- [Show Advanced Filters](#emailadvancedfilters)
File Sharing Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Files](#files)
- [Owners](#owners)
- [Collaborators](#collaborators)
- [Show Advanced Filters](#fileadvancedfilters)
Gen AI Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Messages](#messages-genai)
- [Senders](#senders-genai)
- [Show Advanced Filters](#genaiadvancedfilters)
ITSM Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Objects](#objects-itsm)
- [Owners](#owners-itsm)
- [Collaborators](#collaborators-itsm)
- [Show Advanced Filters](#itsmadvfilters)
Source Code Repository Applications and Tenants
The following tabs and advanced filters appear on your generated page:
- [Objects](#objects-github)
- [Owners](#owners-github)
- [Collaborators](#collaborators-github)
- [Show Advanced Filters](#repoadvancedfilters)
Public Cloud Storage Applications and Tenants
To enable Amazon S3, Google Cloud Platform, and Microsoft Azure for your organization, contact your Zscaler Account team.
The following tabs and advanced filters appear on your generated page:
- [Objects](#objects-publiccloud)
- [Owners](#owners-publiccloud)
- [Collaborators](#collaborators-publiccloud)
- [Show Advanced Filters](#public-cloudadvfilters)
[]You can select to view one of the following tiles:
- Messages with Incidents Matching a Rule
- Messages with DLP Violation
- Messages with Malware
- Messages with External Collaborators
- Externally Sent Messages with DLP Violation
- Quarantined Messages
[See image.](#collabmessages-tab)
Each tile has the following columns:
- **File Name**: The name of the file.
- **Message ID**: The message ID of the file.
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Workspace Name**: The workspace name for the collaboration application.
- **Internal Recipients**: The recipients within your organization.
- **External Recipients**: The** **recipients outside your organization.
- **Run ID**: The ID of the run. A run is when a scan is stopped and started. Every run is identified and tracked with a run ID.
- **Remediation Action**: You can take the following remediation actions when you click on the ellipsis:
- **View Scan History**: You can view the scan history. You'll be redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
- **Quarantine**: You can quarantine a message or file that is malware-reported, with incidents, or DLP violations.
-
**Remove**: You can permanently remove a message or file that is quarantined, malware-reported, with incidents, or DLP violations.
When you select **Quarantine** or **Remove** as a remediation action, it appears as a separate incident entry. The new entry has the most current Last Scan Time value, and the Action category is updated to reflect the remediation action you selected.
- **Restore**: You can restore a quarantined message or file that is malware-reported, with incidents, or DLP violations (for Slack only).
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Shared Channel Hostname**: The hostname of the Slack, Webex Teams, Microsoft Teams, or Zoom shared channel.
- **Channel Name**: The name of the Slack, Webex Teams, Microsoft Teams, or Zoom channel.
- **SHA**: The secure hash algorithm (SHA).
- **Sender**: The sender of the file.
- **Scan ID**: The ID of a scan. Every scan that is defined in the Historic Scan Configuration has a unique identifier associated with it.
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **Owner**: The owner of the file.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Action**: The Data at Rest Scanning DLP policy rule action.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Messages tab in the Collaboration app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report/ZIA-6.1-Collaborators-Tab-Column-2.png)
For each email message, you can click **See Scan History**; you're redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
[]![The Messages tab in the Collaboration app category](/downloads/zia/dashboard-analytics/reports/saas-assets-report-assets-incidents/ZIA-6.2r-Collaboration-Messages-Tab.png)
[]You can select to view one of the following tiles:
- Senders Affected with Incidents Matching a Rule
- Senders of Messages with DLP Violations
- Senders of Messages with Malware
[See image.](#collabsenders-tab)
Each tile has the following columns:
- **Sender**: The sender of the message.
- **Number of Messages with Incidents**: The number of messages that contain incidents.
You can click on a number, and the **Messages with Incidents - Senders** window appears for that particular owner. In the **Messages with Incidents - Owners window**, the columns shown are the same ones in the **Senders** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Recipients**: The number of recipients outside your organization.
- **Number of Internal Recipients**: The number of recipients within your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Senders tab in the Collaboration app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Collaboration-Senders-Tab-Column.png?1613684824)
[]![The Senders tab in the Collaboration app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Collaboration-Senders-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific file name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-collab-img)
The following are the advanced filters you can use:
- **Number of Internal Recipients**: The recipients within your organization.
- **Number of External Recipients**: The number of recipients outside your organization.
- **Internal Recipients**: The recipients within your organization.
- **File Name**: The name of the file.
- **External Recipients**: The recipients outside your organization.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Channel Name**: The name of the Slack, Webex Teams, Microsoft Teams, or Zoom channel.
- **Collaboration Message**: The message that was collaborated on.
- **Shared Channel Hostname**: The hostname of the Slack, Webex Teams, Microsoft Teams, or Zoom shared channel.
- **SHA**: The secure hash algorithm (SHA).
- **Sender Name**: The sender of the file.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the account where the questionable message is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Messages with Incidents Matching a Rule
- Messages with DLP Violation
- Messages with Malware
[See image.](#messagesgenai)
Each tile has the following columns:
- **Bot Name**: The name of the bot that triggered a DLP response.
- **Component**: The name of the component (i.e., file or message).
- **File Name**: The name of the file.
- **Message ID**: The message ID of the file.
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Sender Type**: The type of sender (i.e., bot, system, or user).
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Run ID**: The ID of the run. A run is when a scan is stopped and started. Every run is identified and tracked with a run ID.
- **Remediation Action**: You can take the following remediation action when you click on the ellipsis:
- **View Scan History**: You can view the scan history. You'll be redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
- **Scan ID**: The ID of a scan. Every scan that is defined in the Historic Scan Configuration has a unique identifier associated with it.
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **Owner**: The owner of the file.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Action**: The Data at Rest Scanning DLP policy rule action.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for column names.
![This image shows the Gen AI Messages Tab Column menu](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report-assets-incidents/genai_messages_tab_column_menu.png)
[]![This image shows the Gen AI Messages tab.filters](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report-assets-incidents/Genai_messages_tab.png)
[]You can select to view one of the following tiles:
- Senders Affected with Incidents Matching a Rule
- Senders of Messages with DLP Violations
- Senders of Messages with Malware
[See image.](#genaisenders-tab-img)
Each tile has the following columns:
- **Sender**: The sender of the message.
- **Number of Messages with Incidents**: The number of messages that contain incidents.
You can click on a number, and the **Messages with Incidents - Senders** window appears for that particular sender.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can search for columns.
[]![This image shows the Gen AI Senders tab](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report-assets-incidents/Genai_senders_tab.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific file name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image](#advfilters-genai-img).
The following are the advanced filters you can use:
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Bot Name**: The name of the bot that triggered the DLP response.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **File Name**: The name of the file.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Message ID**: The message ID of the file.
- **Owner Name**: The owner of the account where the questionable message is located. It can be a sender (DLP) or a recipient (Malware).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Sender Type**: The name of the sender (i.e., bot, system, or user).
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Tenant**: The name of the SaaS application tenant.
- **Threat Name**: The name of the threat.
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
[]![This image shows the advanced filters](/downloads/zia/dashboard-analytics/reports/saas-security/saas-assets-report-assets-incidents/Advanced_Filters.png)
[]You can select to view one of the following tiles:
- Objects with Incidents Matching a Rule
- Objects with DLP Violation
- Objects with Malware
- Objects with External Collaborators
[See image.](#crmobjects-tab)
Each tile has the following columns:
- **Object ID**: The ID of the object.
- **Object Name**: The name of the object.
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Owner**: The owner of the file.
- **External Collaborators**: The collaborators outside your organization.
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Threat Name**: The name of the threat.
- **Public URL**: The public URL used to access a shared file.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **DLP Dictionary**:The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **File Modification Time**: The last time, by time and date, a file was modified. You can sort this column.
- **Internal Collaborators**: The internal collaborators within your organization.
- **File Size**: The size of the file.
- **File Path**: The path of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **Download Time**: The download time, in milliseconds, of the file.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Objects tab in the CRM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Objects-Tab-Column.png)
[]![The Objects tab in the CRM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Objects-Tab_0.png)
[]You can select to view one of the following tiles:
- Owners of Files with Incidents Matching a Rule
- Owners of Files with DLP Violation
- Owners of Files with Malware
- Owners of Files with External Collaborators
[See image.](#crmowners-tab)
Each tile has the following columns:
- **Owner**: The owner of the file.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Owners** window appears for that particular owner. In the **Objects with Incidents - Owners** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the CRM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Owners-Tab-Column.png)
[]![The Owners tab in the CRM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Owners-Tab_0.png)
[]You can view the External Collaborators of Files with Incidents Matching a Rule tile.
[See image.](#crmcollaborators-tab)
The tile has the following columns:
- **External Collaborator**: The collaborator outside your organization.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Collaborators** window appears for that particular external collaborator. In the **Objects with Incidents - Collaborators** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Owners**: The owners of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Collaborators tab in the CRM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Collaborators-Tab-Column.png)
[]![The Collaborators tab in the CRM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-CRM-Collaborators-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific thread name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-crm-img)
The following are the advanced filters you can use:
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **External Collaborators**: The collaborators outside your organization.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Internal Collaborators**: The internal collaborators within your organization.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., External Collaborators - Edit).
- **Object Name**: The name of the object.
- **Object ID**: The ID of the object.
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Email Messages with Incidents Matching a Rule
- Email Messages with DLP Violation
- Email Messages with Malware
- Externally Sent Email Messages with DLP Violation
[See image.](#emailmessages-tab)
Each tile has the following columns:
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Message ID**: The email message identifier. Every email message has a unique ID. An Exchange or Gmail administrator can log in to their admin portals and search and pull a specific message with this ID if needed.
- **Thread Name**: The name of the email thread.
- **Attachments**: The attachments within the email message.
You can click on the attachment, click **View Details**, and the **Attachments for Message **window appears.
In the **Attachments for Message** window, you can view the following columns:
- **File Name**: The name of the email attachment.
- **File Size**: The size of the email attachment.
- **File MD5**: The MD5 hash of the email attachment.
- **File Type**: The type of email attachment (e.g., CSV, TXT, etc.).
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns.
- **Mail Sent Time**: The time and date the email was sent.
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **Sender**: The email sender.
- **Internal Recipients**: The email recipients within your organization.
- **External Recipients**: The email recipients outside your organization.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Message Size**: The size of the email message.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **Advanced Threat Category**: The detected viruses or spyware.
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Non-Provisioned Owner**: The mailbox owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **DLP Dictionary**:** **The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Threat Name**: The name of the threat.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Email Messages tab in the Email app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Email-Messages-Tab-Column.png)
For each email message, you can click **See Scan History**; you're redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
[]![The Email Messages tab in the Email app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Email-Messages-Tab_0.png)
[]You can select to view one of the following tiles:
- Senders Affected with Incidents Matching a Rule
- Senders of Messages with DLP Violations
- Senders of Messages with Malware
[See image.](#emailsenders-tab)
Each tile has the following columns:
- **Sender**: The email sender.
- **Number of Email Messages with Incidents**: The number of email messages that contain incidents.
You can click on a number, and the **Email Messages with Incidents - Senders **window appears for that particular sender. In the **Email Messages with Incidents - Senders** window, the columns shown are the same ones in the **Email Messages** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by selecting and deselecting the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Recipients**: The number of email recipients outside your organization.
- **Number of Internal Recipients**: The number of email recipients within your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Senders tab in the Email app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Senders-Tab-Column.png)
[]![The Senders tab in the Email app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Email-Senders-Tab_0.png)
[]You can select to view one of the following tiles: External Recipients on Messages with DLP Violations or Users Who Received Messages with Malware.
[See image.](#emailrecipients-tab)
Each tile has the following columns:
- **External Recipients**: The email recipients outside your organization.
- **Number of Email Messages with Incidents**: The number of email messages that contain incidents.
You can click on a number, and the **Email Messages with Incidents - Recipients **window appears for that particular external recipient. In the **Email Messages with Incidents - Recipients** window, the columns shown are the same ones in the **Email Messages** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns. You can export the list.
- **Senders**: The email senders that sent the email messages with incidents.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Recipients tab in the Email app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Recipients-Tab-Column.png)
[]![The Recipients tab in the Email app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Email-Recipients-Tab.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific thread name; in that case, you can add the advanced filter **Thread Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-email-img)
The following are the advanced filters you can use:
- **Threat Name**: The name of the threat.
- **Attachment File Name**: The name of the attached file in the email message.
- **Attachment File MD5**: The MD5 hash of the attached file.
- **Message ID**: The email message identifier. Every email message has a unique ID. An Exchange or Gmail administrator can log in to their admin portals and search and pull a specific message with this ID if needed.
- **Thread Name**: The name of the email thread.
- **Number of Internal Recipients**: The email recipients within your organization.
- **Number of External Recipients**: The number of email recipients outside your organization.
- **Attachment File Size**: The size of the email attachment.
- **Sender Name**: The email sender.
- **Internal Recipients**: The email recipients within your organization.
- **External Recipients**: The email recipients outside your organization.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses or spyware.
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**:** **The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Files with Incidents Matching a Rule
- Files with DLP Violation
- Files with Malware
- Files with External Collaborators
- Publicly Shared Files with DLP Violations
- Quarantined Files
[See image.](#files-tab)
Each tile has the following columns:
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **File ID**: The ID of the file. For example, if a file is scanned multiple times, an admin can use the file ID to view the scan trail.
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **File Path**: The path of the file.
- **Severity of Last Incident**: The severity level of the file's last incidents detected by the Data at Rest Scanning DLP policy.
- **Owner**: The owner of the file.
- **External Collaborators**: The collaborators outside your organization.
- **External Collaborator Group**: The group of collaborators outside your organization with whom the user shares assets.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **File Modification Time**: The last time, by time and date, a file was modified. You can sort this column.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Remediation Action**: You can take the following remediation actions when you click on the ellipsis:
- **View Scan History**: You can view the scan history. You're redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
- **Go to File**: You're redirected to the file in question.
- **Remove Public Link**: You can remove the file's public link. This option will be grayed out after selecting it.
-
**Remove Collaborators**: You can remove the file's collaborators. When you select this option, the **Remove Collaborators** window appears, where you can choose from the following options:
- **Remove All Collaborators**: Removes all external and internal collaborators of the file.
- **Remove All External Collaborators**: Removes all external collaborators of the file.
- **Remove Specific External Collaborators**: Remove specific external collaborators from the file. From the **Collaborators** field, select the collaborators you want to remove and click **Done**, then **Remove**.
[See image.](#remove-file-collab)
- **Remove Public Link and External Collaborators**: You can remove both the file's public link and the external collaborators.
- **Remove**: You can permanently remove a quarantined malware file or a malware reported file.
- **Remove Watermark**: You can remove a watermark that was applied to a file via a [watermark profile](/unified/adding-editing-watermark-profiles). This option is not available for image files.
- **Restore**: You can restore a quarantined file to its original location. The subsequent policy scans bypass the restored file until the file is modified. This action is available only for quarantined files.
- **Quarantine to User Root Folder**: You can quarantine an incident-reported file to the user's root folder by selecting a Tombstone Template that is used to create a tombstone file that replaces the quarantined file in its original location.
- **Restore Most Recent Redacted Version**: You can restore the most recent file to which redaction characters were applied via a redaction profile. Zscaler stores both the original file version and the redacted file version for possible recovery by administrators in the event of any inadvertent file deletions. To learn more, see [About Redaction](/unified/about-redaction) and [Adding and Editing Redaction Profiles](/unified/adding-editing-redaction-profiles).
-
**Admin Quarantine**: An admin can quarantine sensitive files to a specific file location. Users must refer to the Tombstone template for admin contact details to request access to the file.
This option is currently available only for Google Drive, Microsoft OneDrive, and Microsoft SharePoint.
- **Restore Admin Quarantine**: You can restore a file that was previously quarantined to the admin-specified location.
- **Advanced Threat Category**: The detected viruses or spyware.
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **File MD5**: The MD5 hash of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **DLP Dictionary**:** **The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Public URL**: The public URL used to access a shared file.
- **Download Time**: The download time, in milliseconds, of the file.
- **Internal Collaborators**: The internal collaborators within your organization.
- **Internal Collaborator Group**: The group of collaborators within your organization with whom the user shares assets.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **File Size**: The size of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Threat Name**: The name of the threat.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Files tab in the File Sharing app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Files-Tab-Column.png)
[]![The Files tab in the File Sharing app category](/downloads/zia/dashboard-analytics/reports/saas-assets-report-assets-incidents/ZIA-6.2r-Assets-with-incidents-file-tab_0.png)
[]You can select to view one of the following tiles:
- Owners of Files with Incidents Matching a Rule
- Owners of Files with DLP Violation
- Owners of Files with Malware
- Owners of Files with External Collaborators
- Owners of Publicly Shared Files
[See image.](#fileowners-tab)
Each tile has the following columns:
- **Owner**: The owner of the file.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Files with Incidents - Owners **window appears for that particular owner. In the **Files with Incidents - Owners** window, the columns shown are the same ones in the **Files** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the File app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Owners-Tab-Column.png)
[]![The Owners tab in the File Sharing app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-File-Owners-Tab_0.png)
[]You can view the External Collaborators of Files with Incidents Matching a Rule** **tile.
[See image.](#filecollaborators-tab)
The tile has the following columns:
- **External Collaborator**: The collaborator outside your organization.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Files with Incidents - Collaborators** window appears for that particular external collaborator. In the **Files with Incidents - Collaborators** window, the columns shown are the same ones in the **Files** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Owners**: The owners of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Collaborators tab in the File Sharing app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Collaborators-Tab-Column.png)
[]![The Collaborators tab in the File Sharing app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-File-Collaborators-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific file name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-file-img)
The following are the advanced filters you can use:
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **File ID**: The ID of the file. For example, if a file was scanned multiple times, an admin can use the file ID to view the scan trail.
- **File Path**: The path of the file.
- **File MD5**: The MD5 hash of the file.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **File Size**: The size of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., External Collaborators - Edit).
- **Internal Collaborators**: The interna collaborators within your organization.
- **External Collaborators**: The collaborators outside your organization.
- **External Collaborator Group**: The group of collaborators outside your organization with whom the user shares assets.
- **Internal Collaborator Group**: The group of collaborators within your organization with whom the user shares assets.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses or spyware.
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**:** **The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Objects with Incidents Matching a Rule
- Objects with DLP Violation
- Objects with Malware
- Objects with External Collaborators
[See image.](#itsmobjects-tab)
Each tile has the following columns:
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Object ID**: The ID of the object.
- **Object Name**: The name of the object.
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Owner**: The owner of the file.
- **External Collaborators**: The collaborators outside your organization.
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Threat Name**: The name of the threat.
- **Public URL**: The public URL used to access a shared file.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **File Modification Time**: The last time, by time and date, a file was modified. You can sort this column.
- **Internal Collaborators**: The internal collaborators within your organization.
- **File Size**: The size of the file.
- **File Path**: The path of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **Download Time**: The download time, in milliseconds, of the file.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Objects tab in the ITSM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Objects-Tab-Column.png)
[]![The Objects tab in the ITSM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Objects-Tab_0.png)
[]You can select to view one of the following tiles:
- Owners of Files with Incidents Matching a Rule
- Owners of Files with DLP Violation
- Owners of Files with Malware
- Owners of Files with External Collaborators
[See image.](#itsmowners-tab)
Each tile has the following columns:
- **Owner**: The owner of the file.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Owners** window appears for that particular owner. In the **Objects with Incidents - Owners** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the ITSM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Owners-Tab-Column.png)
[]![The Owners tab in the ITSM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Owners-Tab_0.png)
[]You can view the External Collaborators of Files with Incidents Matching a Rule tile.
[See image.](#itsmcollaborators-tab)
The tile has the following columns:
- **External Collaborator**: The collaborator outside your organization.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Collaborators** window appears for that particular external collaborator. In the **Objects with Incidents - Collaborators** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Owners**: The owners of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Collaborators tab in the ITSM app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Collaborators-Tab-Column.png)
[]![The Collaborators tab in the ITSM app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-ITSM-Collaborators-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific thread name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-itsm-img)
The following are the advanced filters you can use:
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **External Collaborators**: The collaborators outside your organization.
- **Number of Internal Collaborators**: The number of collaborators within your organization.
- **Internal Collaborators**: The internal collaborators within your organization.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., External Collaborators - Edit).
- **Object Name**: The name of the object.
- **Object ID**: The ID of the object.
- **Object Type**: The type of object (e.g., report, campaign, dashboard).
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Objects with Incidents Matching a Rule
- Objects with DLP Violation
- Objects with Malware
- Objects with External Collaborators
[See image.](#repoobjects-tab)
Each tile has the following columns:
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **File ID**: The ID of the file. For example, if a file was scanned multiple times, an admin can use the file ID to view the scan trail.
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Repository**: The name of the repository.
- **Project**: The name of the project.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Owner**: The owner of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **File MD5**: The MD5 hash of the file.
- **File Path**: The path of the file.
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **Threat Name**: The name of the threat.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **File Size**: The size of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
- **External Collaborators**: The collaborators outside your organization.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **File Modification Time**: The last time, by time and date, a file was modified. You can sort this column.
- **Download Time**: The download time, in milliseconds, of the file.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Objects tab in the Source Code Repository app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Objects-Tab-Column.png)
For each file, you can click **See Scan History**; you're redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
[]![The Objects tab in the Source Code Repository app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Repository-Objects-Tab_0.png)
[]You can select to view one of the following tiles:
- Owners of Files with Incidents Matching a Rule
- Owners of Files with DLP Violation
- Owners of Files with Malware
- Owners of Files with External Collaborators
[See image.](#repoowners-tab)
Each tile has the following columns:
- **Owner**: The owner of the file.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Owners** window appears for that particular owner. In the **Objects with Incidents - Owners** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Number of External Collaborators**: The number of collaborators outside your organization.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the Source Code Repository app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Repo-Owners-Tab-Column.png)
[]![The Owners tab in the Source Code Repository app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Repository-Owners-Tab_0.png)
[]You can view the External Collaborators of Files with Incidents Matching a Rule tile.
[See image.](#repocollaborators-tab)
The tile has the following columns:
- **External Collaborator**: The collaborator outside your organization.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Collaborators** window appears for that particular external collaborator. In the **Objects with Incidents - Collaborators** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Owners**: The owners of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Collaborators tab in the Source Code Repository app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Repo-Collaborators-Tab-Column.png)
[]![The Collaborators tab in the Source Code Repository app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Repository-Collaborators-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific thread name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-repo-img)
The following are the advanced filters you can use:
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **Number of External Collaborators**: The number of collaborators outside your organization.
- **External Collaborators**: The collaborators outside your organization.
- **File MD5**: The MD5 hash of the file.
- **File Size**: The size of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., External Collaborators - Edit).
- **File Path**: The path of the file.
- **Project Name**: The name of the project.
- **Repository Name**: The name of the repository.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the mailbox where the questionable email is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Identifier**: The ID number used to search for records. Whenever a DLP rule is hit, and the appropriate alert is configured, an email containing this ID is sent to your auditors.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
[]You can select to view one of the following tiles:
- Objects with Incidents Matching a Rule
- Objects with DLP Violation
- Objects with Malware
Each tile has the following columns:
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **File ID**: The ID of the file. For example, if a file was scanned multiple times, an admin can use the file ID to view the scan trail.
- **File Name**: The name of the suspicious file detected by the Data at Rest Scanning policy.
- **File Path**: The path of the file.
- **Last Scan Time**: The last time, by time and date, a file was scanned. You can sort this column.
- **Severity of Last Incident**: The severity level of the file's last incidents detected by the Data at Rest Scanning DLP policy.
- **Bucket Owner**: The name of the owner of the bucket.
- **Bucket Name**: The name of the bucket.
- **Owner**: The owner of the files.
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **File Modification Time**: The last time, by time and date, a file was modified. You can sort this column.
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **File MD5**: The MD5 hash of the file.
- **Collaboration Scope**: The collaboration scope and permissions for SaaS application tenant files (e.g., Edit).
- **Public URL**: The public URL used to access a shared file.
- **File Size**: The size of the file.
- **File Type**: The type of file (e.g., CSV, TXT, etc.).
- **SHA**: The secure hash algorithm (SHA).
- **Number of Collaborators**: The number of file collaborators.
- **Collaborators**: All the file collaborators.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **Rule Name**: The name of the rule that triggered the session or aggregated sessions.
- **Advanced Threat Category**: The detected viruses or spyware.
- **Policy Type**: The type of policy that took action (e.g., DLP).
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Action**: The Data at Rest Scanning DLP policy rule action.
[See image.](#publiccloud-objects-tab)
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the Public Cloud Storage app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Objects-Tab-Column.png)
For each file, you can click **See Scan History**; you're redirected to the [SaaS Security Insights Logs](/unified/about-saas-security-insights-logs) page.
[]![The Objects tab in the Public Cloud Storage app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Objects-Tab_0.png)
[]You can select to view one of the following tiles:
- Owners of Files with Incidents Matching a Rule
- Owners of Files with DLP Violation
- Owners of Files with Malware
- Owners of Files with External Collaborators
[See image.](#Publiccloud-owners-tab)
Each tile has the following columns:
- **Owner**: The owner of the files.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents** window appears for that particular external collaborator. In the **Objects with Incidents** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Collaborators**: The collaborators of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Owners tab in the Public Cloud Storage app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Owners-Tab-Column.png)
[]![The Owners tab in the Public Cloud Storage app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Owners-Tab_0.png)
[]You can view the External Collaborators of Files with Incidents Matching a Rule tile.
[See image.](#publiccloud-collaborators-tab)
The tile has the following columns:
- **Collaborator**: The collaborator of the files.
- **Number of Files with Incidents**: The number of files that contain incidents.
You can click on a number, and the **Objects with Incidents - Collaborators** window appears for that particular external collaborator. In the **Objects with Incidents - Collaborators** window, the columns shown are the same ones in the **Objects** tab.
Hover over the **Column Menu** icon on the top right of the table to customize these columns by checking and unchecking the ones you want to view or hide on the page and arranging them in the order you want to view them. You can also search for columns. You can export the list.
- **Owners**: The owners of the files.
Hover over the **Column Menu** icon on the top right of the table to customize these columns. You can select and deselect the ones you want to view or hide on the page. You can also arrange them in the order you want to view them. You can search for columns.
![The Column Menu for the Collaborators tab in the Public Cloud Storage app category in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Collaborators-Tab-Column.png)
[]![The Collaborators tab in the Public Cloud Storage app category](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Public-Cloud-Storage-Collaborators-Tab_0.png)
[]You can add advanced filters to tailor certain fields with your specific searches. For example, you might want to filter your page to include a specific thread name; in that case, you can add the advanced filter **File Name** and include the operator **Equals**. You can also select or add other operators to your fields:
- Equals
- Ends with
- Starts with
- Contains
- Does not equal
- Does not start with
- Does not end with
- Does not contain
You can add or remove multiple advanced filters, and you can select, add, or remove operators to best tailor your filtering. Click **Apply** to update the page to reflect your filters or **Reset** to start over.
[See image.](#advfilters-publiccloud-img)
The following are the advanced filters you can use:
- **File Name**: The name of the file.
- **File ID**: The ID of the file. For example, if a file was scanned multiple times, an admin can use the file ID to view the scan trail.
- **File Path**: The path of the file.
- **SHA**: The secure hash algorithm (SHA).
- **Bucket Name**: The name of the bucket.
- **Non-Provisioned Owner**: The file owners (inside or outside your organization) that are not provisioned to the Internet & SaaS services.
When a non-provisioned file owner within your organization is later provisioned to the Internet & SaaS services, the service begins to log the file owner under the **User **column.
- **File MD5**: The MD5 hash of the file.
- Number of Collaborators
- **File Size**: The size of the file.
- **Action**: The Data at Rest Scanning DLP policy rule action.
- **Severity**: The severity level of the incidents detected by the Data at Rest Scanning DLP policy.
- **Advanced Threat Category**: The detected viruses and spyware for a specific advanced threat category (e.g., Trojan).
- **Threat Super Category**: The detected viruses and spyware for a specific super threat category (i.e., Malware, Sandbox, Spyware, and Virus).
- **Scan Time**: The amount of time, in milliseconds, the Data at Rest Scanning policy took to scan content within the tenant.
- **Document Type**: The type of document uploaded or downloaded during the transaction.
- **Download Time**: The download time, in milliseconds, of the file.
- **Threat Name**: The name of the threat.
- **Owner Name**: The owner of the account where the questionable message is located. It can be a sender (DLP) or a recipient (Malware).
- **DLP Engine**: The [DLP engine](/unified/about-dlp-engines) that was detected.
- **DLP Dictionary**: The [DLP dictionary](/unified/about-dlp-dictionaries) that was triggered.
[]![The Advanced Filters section in the Assets with Incidents page](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/reports/saas-assets-report-assets-incidents/ZIA-6.1-Advanced-Filters.png)
![Remove Collaborators window](/downloads/zia/dashboard-analytics/reports/saas-assets-report-assets-incidents/ZIA6.2r-remove-collaborators%20(1).png)
[]