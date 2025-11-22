# Integrating with Microsoft Defender for Endpoint
Source: https://help.zscaler.com/unified/integrating-microsoft-defender-endpoint
PDF: https://help.zscaler.com/pdf/com/en/1494641.pdf

Zscaler's integration leverages Microsoft Defender for Endpoint APIs to provide endpoint detection and response (EDR) visibility for [Sandbox](/unified/about-sandbox)-detected malware. When the integration is configured, the Zscaler service calls the Microsoft Defender for Endpoint API and requests information for endpoints that have been exposed to the malicious file. Microsoft Defender for Endpoint uses the new file signature to detect compromised points throughout your organization's network.
You can view information about the affected endpoints in the [Sandbox logs and reports](/unified/viewing-sandbox-reports-and-data) of the Admin Portal. You can also isolate endpoints, start automated investigation and remediation (AIR), and stop malicious file executions from the Admin Portal. For further investigation and remediation, you can go to the Microsoft Defender portal. These automated workflows reduce the threat dwell time and remediation time.
Prerequisites
Before you begin the Microsoft Defender for Endpoint integration, ensure you have:
- A Microsoft Defender for Endpoint admin account
- Zscaler Advanced Sandbox
The Microsoft Defender for Endpoint admin account must be able to grant the required permissions to integrate with Zscaler. You can use either a global admin account, or any admin account with the ability to grant the necessary permissions.
To learn more, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/microsoft-365/security/defender-endpoint/?view=o365-worldwide).
Integrating with Microsoft Defender for Endpoint
To integrate the Zscaler service with Microsoft Defender for Endpoint:
- Go to **Infrastructure **> **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations**.
- Click the **Microsoft Defender for Endpoint** tab.
-
Under **Authorize Microsoft Defender for Endpoint**, click **Provide Admin Credentials**.
[See image.](#seeimage-3)
The Microsoft Defender portal appears.
- Log in to Microsoft Defender for Endpoint.
-
Review the required permissions for the Zscaler service to access Microsoft Defender for Endpoint, and click **Accept**.
After the authorization is complete, the **Zscaler SaaS Connector** and **Directory (Tenant) ID** appear.
[See image.](#seeimage-5)
- Click **Save**.
If your Microsoft Defender for Endpoint credentials are valid, the Zscaler service calls the Microsoft Defender for Endpoint APIs and syncs your endpoint hits to the Zscaler service. You then can view file and endpoint information in the [Microsoft Defender Endpoint Hits report](/unified/viewing-microsoft-defender-endpoint-hits-report).
[]![The Provide Admin Credentials button in the Authorize Microsoft Defender for Endpoint section.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/integrating-microsoft-defender-endpoint/ZIA-Authorize-Microsoft-Defender-Endpoint-Provide-Admin-Credentials.png)
[]![The Zscaler SaaS Connector and Directory (Tenant) ID fields in the Authorization Complete section.](/downloads/zscaler-tech-pubs-style-guide/draft-articles/integrating-microsoft-defender-endpoint/ZIA-Microsoft-Defender-for-Endpoint-Authorization-Complete.png)