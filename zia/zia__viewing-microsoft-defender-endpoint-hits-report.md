# Viewing the Microsoft Defender Endpoint Hits Report
Source: https://help.zscaler.com/zia/viewing-microsoft-defender-endpoint-hits-report
PDF: https://help.zscaler.com/pdf/com/en/1402161.pdf

If you [integrated with Microsoft Defender for Endpoint](/zia/integrating-microsoft-defender-endpoint), you can view information on endpoints that have been exposed to a potentially malicious file. After the Sandbox analyzes a file, you can click the **MD5** hash and choose **View Microsoft Defender Endpoint Hits**. The Microsoft Defender Endpoint Hits report provides visibility into all the endpoints installed and detected with Microsoft Defender for Endpoint. The Microsoft Defender for Endpoint integration leverages the Microsoft advanced threat hunting, incident response, and EDR capabilities and allows you to quarantine endpoints detected with the indicator of compromise (IOC). This IOC enrichment is important for:
- Tracing [patient 0 events](/zia/configuring-patient-0-alert) if the Zscaler service is configured to allow unknown files while sandboxing.
- Threat hunting to prevent attackers from spreading malware and moving laterally across your network.
- Incident responses from an infection caused by lateral movement or an out-of-band channel (e.g., USB).
After the integration is configured, admins can go to the Microsoft Defender for Endpoint portal to get more contextual information about the detection of the IOC or indicator of attack (IOA) before deciding to quarantine the endpoint or take remedial action.
Zscaler and Microsoft are technology partners. To learn more about the Zscaler and Microsoft Defender Integration, see the [Zscaler and Microsoft Defender Deployment Guide](/zscaler-technology-partners/zscaler-and-microsoft-defender-deployment-guide).
Viewing the Microsoft Defender Endpoint Hits Report
To view the Microsoft Defender Endpoint Hits report, click the **MD5** hash for any file analyzed by Sandbox and choose **View Microsoft Defender Endpoint Hits**.
[See image.](#cs-endpoint-hits)
About the Microsoft Defender Endpoint Hits Report
In the Microsoft Defender Endpoint Hits report, you can view file and endpoint information from the Zscaler service and Microsoft Defender for Endpoint.
Sandbox File Properties (Zscaler)
In this section, you can view general information about the file from the Zscaler [Sandbox](/zia/about-sandbox) analysis. The following information appears:
- **Sandbox Category**: The type of file. The following categories appear:
- **Sandbox Adware**: Files that automatically render advertisements/install adware.
- **Sandbox Malware/Botnet**: Files that behave like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware.
- **Sandbox P2P/Anonymizer**: Files that contain anonymizers and P2P clients.
- **Sandbox Score**: The threat score determined from the Sandbox analysis.
- **Threat Name**: The threat name of the file. Click to go to the [Zscaler Threat Library](https://threatlibrary.zscaler.com/) to learn more about the file.
- **File Type**: The type of file (e.g., Windows Executable).
- **File Size**: The total bytes of the file.
- **MD5**: The MD5 hash of the file. Click to view the [Sandbox Detail Report](/zia/viewing-sandbox-reports-data#about-sandbox-detail-report).
- **SHA-1**: The SHA-1 hash of the file. You can use it to find identical files.
- **SHA-256**: The SHA-256 hash of the file. You can use it to find identical files.
- **SSDEEP**: The ssdeep hash of the file. You can use it to find partial matches with other suspicious files.
[See image.](#zscaler)
File Detected on Endpoints (Microsoft Defender for Endpoint)
A list of endpoints on which the file was detected via Microsoft Defender for Endpoint.
- **Microsoft Defender Agent ID**: The ID of Microsoft Defender agent installed on the host.
- **Hostname**: The name of the host.
- **Internal IP**: The internal IP address of the host.
- **External IP**: The external IP address of the host.
- **OS Version**: The operating system and version of the host.
- **First Seen**: The first time the file was detected on the endpoint.
- **Last Seen**: The last time the file was detected on the endpoint. You can sort this column.
- **File Status**: The status of the file.
- **Seen**: The Microsoft Defender agent saw the file on the host.
- **Detected**: The Microsoft Defender agent triggered a detection based on a process or an operation associated with the file.
- **Quarantined**: The Microsoft Defender agent stopped the ongoing processes of the file and removed it from the host.
- **Remediated**: The Microsoft Defender agent used [automated investigation and remediation (AIR) capabilities](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/automation-levels?view=o365-worldwide#levels-of-automation) to remediate the file.
- **Endpoint Status**: The status of the endpoint. The following states appear:
- **Active**: The endpoint is not quarantined.
- **Isolated**: The endpoint is quarantined.
- **Actions**: Call the Microsoft Defender for Endpoint API to perform one of the following actions.
- **Isolate**: Click to quarantine the endpoint. This option only appears if the endpoint status is **Active**.
- **Stop Current Executions**: Click to stop any ongoing processes associated with the file on the endpoint.
- **Trigger Alert & Start AIR**: Click to trigger an alert and start AIR on the endpoint. To learn more about configuring AIR, see the [Microsoft Defender for Endpoint documentation](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/configure-automated-investigations-remediation?view=o365-worldwide).
- **Prevent Future Executions**: Click to stop any future processes of the file on all endpoints.
[See image.](#crowdstrike)
[]![Screenshot of the View Microsoft Defender Endpoint Hits option for the MD5 in Insights Logs.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/viewing-microsoft-defender-endpoint-hits-report/ZIA-Insights-Logs-MD5-View-Microsoft-Defender-Enpoint-Hits.png)
[]![Screenshot of the Sandbox File Properties (Zscaler) section in the Microsoft Defender Endpoint Hits report.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/viewing-microsoft-defender-endpoint-hits-report/ZIA-Microsoft-Defender-Endpoint-Hits-Sandbox-File-Properties-Zscaler.png)
[]![Screenshot of the File Detected on Endpoints (Carbon Black) section in the Carbon Black Endpoint Hits report.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/viewing-microsoft-defender-endpoint-hits-report/ZIA-File-Detected-On-Endpoint-Microsoft-Defender-for-Endpoint.png?1619551892)