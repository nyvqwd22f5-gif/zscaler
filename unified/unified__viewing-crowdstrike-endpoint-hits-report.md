# Viewing the CrowdStrike Endpoint Hits Report
Source: https://help.zscaler.com/unified/viewing-crowdstrike-endpoint-hits-report
PDF: https://help.zscaler.com/pdf/com/en/1494636.pdf

If you [integrated with CrowdStrike](/unified/integrating-crowdstrike), you can view information on endpoints that have been exposed to a potentially malicious file. After the Sandbox analyzes a file, you can click the **MD5** hash and choose **View CrowdStrike Endpoint Hits**. The CrowdStrike Endpoint Hits report provides visibility into all the endpoints installed and detected with CrowdStrike Falcon. The CrowdStrike integration leverages the CrowdStrike Falcon endpoint detection and response (EDR) capabilities and allows you to quarantine endpoints detected with the indicator of compromise (IOC). This IOC enrichment is important for:
- Tracing [patient 0 events](/unified/configuring-patient-0-alert) if the Zscaler service is configured to allow unknown files while sandboxing.
- Threat hunting to prevent attackers from spreading malware and moving laterally across your network.
- Incident responses from an infection caused by lateral movement or an out-of-band channel (e.g., USB).
After the integration is configured, admins can switch to the CrowdStrike portal to get more contextual information about the detection of the IOC or indicator of attack (IOA) before deciding to quarantine the endpoint or take remedial action with CrowdStrike's Real Time Response (RTR) capabilities.
Viewing the CrowdStrike Endpoint Hits Report
To view the CrowdStrike Endpoint Hits report, click the **MD5** hash for any file analyzed by Sandbox and choose **View CrowdStrike Endpoint Hits**.
[See image.](#cs-endpoint-hits)
About the CrowdStrike Endpoint Hits Report
In the CrowdStrike Endpoint Hits report, you can view file and endpoint information from the Zscaler service and CrowdStrike.
Sandbox File Properties (Zscaler)
In this section, you can view general information about the file from the [Zscaler Sandbox](/unified/about-sandbox) analysis. The following information appears:
- **Sandbox Category**: The type of file. The following categories appear:
- **Sandbox Adware**: Files that automatically render advertisements/install adware.
- **Sandbox Malware/Botnet**: Files that behave like APTs, exploits, botnets, trojans, keyloggers, spyware, and other malware.
- **Sandbox P2P/Anonymizer**: Files that contain anonymizers and P2P clients.
- **Sandbox Score**: The threat score determined from the Sandbox analysis.
- **Threat Name**: The threat name of the file. Click to go to the [Zscaler Threat Library](https://threatlibrary.zscaler.com/) to learn more about the file.
- **File Type**: The type of file (e.g., Windows Executable).
- **File Size**: The total bytes of the file.
- **MD5**: The MD5 hash of the file. Click to view the [Sandbox Detail Report](/unified/viewing-sandbox-reports-and-data#about-sandbox-detail-report).
- **SHA-1**: The SHA-1 hash of the file. You can use it to find identical files.
- **SHA-256**: The SHA-256 hash of the file. You can use it to find identical files.
- **SSDEEP**: The ssdeep hash of the file. You can use it to find partial matches with other suspicious files.
[See image.](#zscaler)
File Detected on Endpoints (CrowdStrike)
A list of endpoints on which the file was detected via CrowdStrike.
- **CrowdStrike Agent ID**: The Agent ID (aid) on CrowdStrike. Click to view more information about the endpoint and host in the CrowdStrike portal.
- **Hostname**: The name of the host.
- **Internal IP**: The internal IP address of the host.
- **External IP**: The external IP address of the host.
- **OS Version**: The operating system and version of the host.
- **First Seen**: The first time the file was detected on the endpoint.
- **Last Seen**: The last time the file was detected on the endpoint. You can sort this column.
- **File Status**: The status of the file.
- **Seen**: The CrowdStrike Falcon agent saw the file on the host.
- **Detected**: The CrowdStrike Falcon agent triggered a detection based on a process or an operation associated with the file.
- **Prevented**: The CrowdStrike Falcon agent blocked a process or an operation associated with the file.
- **Endpoint Status**: The status of the endpoint. The following states appear:
- **Normal**: The endpoint is active and not quarantined. Click **Contain** to call the CrowdStrike API to quarantine the endpoint. This action only appears if the endpoint status is **Normal**.
- **Contained**: The endpoint is quarantined.
- **Containment Pending**: The endpoint is being quarantined.
- **Lift Containment Pending**: The endpoint is being removed from quarantine.
[See image.](#crowdstrike)
[]![Screenshot of the View CrowdStrike Endpoint Hits option for the MD5 in Insights Logs.](/downloads/zia/partner-integrations/viewing-crowdstrike-endpoint-hits-report/ZIA-Insights-Logs-MD5-View-CrowdStrike-Endpoint-Hits.png)
[]![Screenshot of the Sandbox File Properties (Zscaler) section in the CrowdStrike Endpoint Hits report.](/downloads/zia/partner-integrations/viewing-crowdstrike-endpoint-hits-report/zia-sandbox-file-properties-zscaler.png)
[]![Screenshot of the File Detected on Endpoints (CrowdStrike) section in the CrowdStrike Endpoint Hits report.](/downloads/zia/partner-integrations/viewing-crowdstrike-endpoint-hits-report/ZIA-file-detected-on-endpoints-crowdstrike.png)