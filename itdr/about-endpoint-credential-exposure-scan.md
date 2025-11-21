# About Endpoint Credential Exposure Scan
Source: https://help.zscaler.com/itdr/about-endpoint-credential-exposure-scan
PDF: https://help.zscaler.com/pdf/com/en/1531685.pdf

The Endpoint Credential Exposure Scan feature checks for risky identity material, such as usernames, passwords, API keys, SSH keys, certificate files, and other credentials stored locally on endpoints. In post-compromise scenarios, the presence of such credentials on the endpoint is a critical source of risk and enables adversaries to escalate privileges and access sensitive data and applications. The exploitation of these local credentials has been observed in several publicly reported breaches. Visibility into these credentials presents an opportunity to clean them up and enforce policies for securely storing them, thereby reducing the post-compromise attack surface available to an adversary.
Endpoint Credential Exposure Scan provides the following benefits and enables you to:
- Monitor endpoints for credentials and other identity material stored locally.
- Find configuration issues that open up privilege escalation points from an endpoint.
About the Endpoint Credential Exposure Page
On the Endpoint Credential Exposure page (ITDR > Manage > Endpoint Credential Exposure), you can do the following:
- View a list of configured endpoints. For each endpoint, you can view:
- **Name: **The name of the configuration.
- **Scan Frequency: **The scheduled scan frequency (**Daily**, **Weekly**, **Monthly**, and **Quarterly**).
-
**Info: **The status of the scan:
- **Completed**: The endpoint agent completed the scan across the modules and sent the data to the ITDR Admin Portal.
- **Partially Completed**: The endpoint agent completed the scan across only a few modules due to errors in other modules, and sent the partial data to the ITDR Admin Portal.
- **Failed**: The endpoint agent failed to scan the modules.
- **Not Started**: The endpoint agent has not started the scan that is queued in the ITDR Admin Portal.
- **Processing**: The endpoint agent is currently running the scan across the modules and will send the data to the ITDR Admin Portal after completion.
Click the status to find the associated [endpoint agent](/itdr/about-endpoint-settings) on the Agents page.
- **Password Analysis**: Allows you to find credentials that have been leaked in publicly disclosed breaches, are part of online password dictionaries, or are being reused.
- If enabled, passwords are hashed using a custom salt locally on the endpoint and are collected on your tenant for analysis. Zscaler cannot access your credentials in plain text.
- If disabled, passwords are neither processed nor collected.
- [Configure an endpoint.](/itdr/configuring-endpoint-credential-exposure-scan)
- [Stop an ongoing scan](/itdr/stopping-ongoing-credential-exposure-scan).
- [Trigger an on-demand scan](/itdr/triggering-demand-credential-exposure-scan).
-
[Edit or delete a scan](/itdr/managing-credential-exposure-scan).
![Endpoint Credential Exposure page](/downloads/itdr/itdr/endpoint-credential-exposure-scan/about-endpoint-credential-exposure-scan/itdr-ece-page.png)