# Viewing Sandbox Reports and Data
Source: https://help.zscaler.com/unified/viewing-sandbox-reports-and-data
PDF: https://help.zscaler.com/pdf/com/en/1494356.pdf

You can view a variety of [Sandbox](/unified/about-sandbox) data and reports under Dashboard and Analytics:
- [Security Dashboard](#security-dashboard)
- [Web Insights](#web-insights)
- [Sandbox Detail Report](#about-sandbox-detail-report)
- [Sandbox Activity Report](/unified/about-sandbox-activity-report)
- [Sandbox Files Found Malicious Report](/unified/about-sandbox-files-found-malicious-report)
- [CrowdStrike Endpoint Hits Report](/unified/viewing-crowdstrike-endpoint-hits-report)
- [Microsoft Defender Endpoint Hits Report](/unified/viewing-microsoft-defender-endpoint-hits-report)
[]You can monitor malware detected by the Sandbox on the [Security dashboard](/unified/about-dashboards#security) (Analytics > Internet & SaaS > Dashboard > Security). You can edit the dashboard and add widgets that display transaction information for the Sandbox, Sandbox Action, and Top Users/Locations for Sandbox.
[See image.](#zia-security-dashboard)
If you have Advanced Sandbox, you can also see the Sandbox Patient 0 Events widget. It displays patient 0 events that occurred in your organization within the chosen time frame. To learn more about patient 0 events and the widget, see [Configuring the Patient 0 Alert](/unified/configuring-patient-0-alert).
[See image.](#zia-sandbox-patient-0-events-widget)
[]![Screenshot of the sandbox related widgets on the Security Dashboard.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/viewing-sandbox-reports-data/zia-security-dashboard.png)
[]![Screenshot of the Sandbox Patient 0 Events widget.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/configuring-sandbox/configuring-patient-0-alert/zia-sandbox-patient-0-events-widget.png)
[]In [Web Insights Logs](/unified/about-insights-logs) (Logs > Insights > Internet & SaaS > Web Insights), the Sandbox logs provide additional information about malicious transactions.
[See image.](#ZIA-Web-Insights-Logs-Sandbox)
Following are some popular columns used for troubleshooting Sandbox transactions:
- **Threat Name**: Indicates the exact malware name (e.g., Trojan.Zbot, Backdoor.Caphaw) or the malware category, based on the behavior recognized by the Zscaler service. You can click the threat to view more information about it in the Zscaler Threat Library. If you have Standard Sandbox and a malicious file is allowed because it doesn't match criteria of the default Sandbox rule, the service displays Not Subscribed in the Threat Name column.
[See image.](#not-subscribed)
- **Policy Action**: Displays what the Sandbox engine has done with suspicious files. The Sandbox engine takes the following actions with suspicious files:
- **Sent to Analysis**:** **The file was sent to the Sandbox for behavioral analysis, and the user can download the file.
- **Quarantined**:** **The file was sent to the Sandbox for behavioral analysis, and the user cannot download the file until the analysis is completed.
- **Blocked**:** **The file was blocked immediately based on previous Sandbox analysis with a known MD5 hash.
- **MD5**: Displays the hash of suspicious files. If you have Advanced Sandbox, you can click the value to view the [Sandbox Detail Report](/unified/viewing-sandbox-reports-and-data#about-sandbox-detail-report).
- **Threat Category**: Displays the threat type of the file. The following categories appear under this column:
- **Benign**: A known non-malicious file.
- **Sandbox Adware**:** **A known malicious file that automatically renders advertisements and installs adware.
- **Sandbox Anonymizer**: A known malicious file that contains anonymizers and P2P clients.
- **Sandbox Malware**: A known malicious file that behaves like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware.
- **Sent for Analysis**: An unknown file that is sent to the Sandbox for behavioral analysis. After analysis, if the Sandbox classifies the file as malicious, the new malicious threat category is appended to Sent for Analysis (e.g., Sent for Analysis - Sandbox Malware/Anonymizer/Adware).
[See image.](#threat-category)
- **Suspicious Content**: Displays the raw Page Risk Index score of the file. If the file is blocked for other security reasons, the score is set to 100.
[]![Screenshot of the Sandbox logs on the Web Insights Logs page](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Web-Insights-Logs-Sandbox.png)
[]![Screenshot of a Sandbox malware transaction with the Not Subscribed appended in the Threat Name column.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Web-Insights-Logs-Not-Subscribed.png)
[]![Screenshot highlighting Sent for Analysis - Sandbox Malware in the Threat Category column.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Web-Insights-Logs-Threat-Category-Column.png)
[]If your organization has Advanced Sandbox, you can click the MD5 hash of the file in the logs and view the Sandbox Detail Report. It provides different types of information about a file and its behavior, including forensic details such as which registry keys were changed, which network connections were initiated, and which files were read.
For each category, you can view additional details by clicking the **Expand** icon at the top right-hand corner of each widget.
[See image.](#ZIA-Sandbox-Detail-Report-Expand-Icon)
You can print the report by clicking the **Print** icon and a printer-friendly version of the report appears.
[See image.](#ZIA-Sandbox-Detail-Report-Print-Icon)
You can also download the original file sample, dropped files, and network packet capture from the Download Summary widget.
[See image.](#ZIA-Sandbox-Detail-Report-Download-Summary-Widget)
The Sandbox is augmented with machine learning capabilities. Machine learning improves malware detection and increases the accuracy of Sandbox verdicts. You can view the machine learning results in the Machine Learning Analysis widget.
[See image.](#ZIA-Sandbox-Detail-Report-Machine-Learning-Analysis-Widget)
For Advanced Sandbox users, all malicious samples are analyzed twice automatically, first through an unpatched vulnerable VM (Zero Day Report or Fully Patched VM Report) and then a second time through the fully patched secured VM (Regular Report). This allows you to compare the report outputs to identify mitigation effectiveness and potential risk.
[See image.](#sandbox_zero)
When configuring the Sandbox policy, you also can enable AI Quarantine to analyze an unknown file in quarantine and determine the likelihood of it being benign or suspicious while the file is undergoing Sandbox analysis. To learn more, see [Configuring the Sandbox Policy](/unified/configuring-sandbox-policy).
[]![Screenshot of the Expand icon in the Sandbox Detail Report](/downloads/zia/policies/sandbox/viewing-sandbox-reports-data/ZIA-Sandbox%20Detail%20Report-Expand-Icon_2.png)
[]![Screenshot of the Print icon in the Sanbox Detail Report](/downloads/zia/policies/sandbox/viewing-sandbox-reports-data/ZIA-Sandbox-Detail-Report-Print-Icon_2.png)
![Screenshot of the printer-friendly version of the Sandbox Detail Report.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Sandbox-Detail-Report-Print-View.png)
[]
[]![Screenshot of the Download Summary widget in the Sandbox Detail Report](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Sandbox-Detail-Report-Download-Summary-Widget.png)
[]![An unpatched, vulnerable report with the Threat Score, Zero Day Report, and Virus and Malware highlighted.](/downloads/zia/policies/sandbox/viewing-sandbox-reports-data/Zero%20Day%20Report%2000_2.png)
![A patched, secure analysis with Threat Score, Regular Report, and Virus and Malware highlighted.](/downloads/zia/policies/sandbox/viewing-sandbox-reports-data/Zero%20Day%20Report%2001_2.png)
[]![Screenshot of the Machine Learning Analysis widget in the Sandbox Detail Report.](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/sandbox/viewing-sandbox-reports-data/ZIA-Sandbox-Detail-Report-Machine-Learning-Analysis-Widget.png)