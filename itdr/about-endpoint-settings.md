# About Endpoint Settings
Source: https://help.zscaler.com/itdr/about-endpoint-settings
PDF: https://help.zscaler.com/pdf/com/en/1531652.pdf

Endpoint Settings allow you to manage agents' details and safe processes, customize agent configuration, and configure phased updates for agents.
Endpoint Settings provide the following benefits and enable you to:
- Continuously monitor endpoints and the Active Directory (AD) domain to detect identity-based attacks.
- Trigger an LDAP-based [AD scan](/itdr/scanning-active-directory) to communicate with the AD domain and identify vulnerabilities.
- Trigger a [credential exposure scan](/itdr/about-endpoint-credential-exposure-scan) on endpoints to detect exposed credentials and other identity-related data that can be easily exfiltrated.
About the Endpoint Settings Page
On the Endpoint Settings page (Settings > Endpoint Settings), you can see the following tabs:
- [Endpoint Agents](#endpoint_settings)
- [Agent Configuration](#agent-config)
- [Agent Update Groups](#agent-update-groups)
- [Safe Processes](#safe-processes)
[]
On the Agents tab, you can do the following:
- View a list of systems on which the endpoint agents are installed. For each system, you can view:
- **System Name**: The name of the system.
- **System User Name**: The usernames of the system.
- **Client Connector User: **The usernames in Zscaler Client Connector.
- **Matched Policies**: The [threat detection policies](/itdr/about-threat-detection) that are applied on the endpoint.
- **First Seen**: The date and time when the agent was installed on the system.
- **Last Seen**: The date and time when the agent was last connected to the Zscaler ITDR Admin Portal.
- **OS Version**: The operating system (OS) name and version.
- **Version**: The endpoint agent version number.
- **Endpoint Credential Exposure Policy Name: **The name of the [endpoint credential exposure](/itdr/about-endpoint-credential-exposure-scan) policy on the endpoint agent.
- **Endpoint Credential Exposure Policy Status: **The status of the endpoint credential exposure policy (e.g., **Completed Successfully**, **Completed Partially**, **Failed**, **Processing**, **Not Started**). When an endpoint credential exposure policy for an agent fails or is partially completed, you can view the logs of the error by clicking the **Failed** or **Completed Partially** status. The endpoint credential exposure error logs provide the following information:
- **Timestamp**: The date and timestamp for when the error was generated.
- **Type**: The type of endpoint credential exposure policy.
- **Message**: The message of the error.
- **Detail**: The detailed description of the error.
- **IP**: The IP address of the system.
-
[Install endpoint agents](/itdr/deploying-itdr-zscaler-client-connector-windows).
The endpoint agent's CPU consumption is capped at 25%.
- Download **Troubleshooter** to manage the endpoint agents using CLI commands.
- [Export endpoint agent configuration details to a file](/itdr/managing-endpoint-agents).
- Select any of the following options from the **Actions** drop-down menu:
- **Show all agents**: Shows or hides inactive agents. Inactive agents are the endpoint agents with last check-in time older than 7 days. By default, this setting is disabled.
- If enabled, all agents (active and inactive) are displayed.
- If disabled, only active agents are displayed.
- **Trigger Logs:** Trigger the [downloading of endpoint agent logs](/itdr/downloading-endpoint-agent-logs-endpoint) from an endpoint.
- View error logs, [view policy details](/itdr/viewing-policy-details), [uninstall or delete an agent](/itdr/uninstalling-or-deleting-endpoint-agents), and [download agent logs](/itdr/downloading-endpoint-agent-logs-endpoint).
![The Agents tab on the Endpoint Settings page with all agent details](/downloads/itdr/endpoint-settings/agents/about-endpoint-settings/Endpoint%20Settings.png)
When a critical event occurs on the agent, error logs are generated. Click the **View Error Logs** icon to open the **Error Logs** window and view the latest log entry.
[See image.](#Error_logs)
[]![Error Logs](/downloads/itdr/endpoint-settings/agents/about-endpoint-settings/endpoint_errorlog.png)
[]
On the Agent Configuration tab, you can do the following:
- [Customize the landmine agent installer properties.](/itdr/customizing-agent-configuration)
- [Enable auto-cleanup of duplicate agents.](/itdr/customizing-agent-configuration)
![The Agent Configuration page with Installer Customizations and Auto-Cleanup Duplicate Agents options](/downloads/itdr/endpoint-settings/agent-configuration/about-agent-configuration/itdr-about-agent-configuration-new.png)
[]
On the Agent Update Groups tab, you can do the following:
- View a list of agent update groups that you created. For each agent update group, you can view:
- **Name**: The name of the agent update group.
- **Selection Criterion**: The selection criterion specified for the agent update group.
- **Update Progress**: The total number of agents updated in the group.
- **Update Enabled**: The status of phased updates. The **X** icon indicates that the updates are disabled for the group, and the **Checkmark **icon indicates that the updates are enabled for the group.
- [Add an agent update group](/itdr/adding-endpoint-agent-group).
- [Enable the phased updates](/itdr/enabling-phased-updates-using-agent-update-groups) for the agent update groups.
- [Manage agent update groups.](/itdr/managing-agent-update-groups)
![The Agent Update Groups page with Add Group and Enable Phased Updates options](/downloads/itdr/endpoint-settings/phased-updates-agent-groups/about-agent-update-groups/itdr-agent-update-group-page_0.png)
[]
On the Safe Processes tab, you can do the following:
- View a list of safe processes. For each configured safe process, you can see:
- **Name**: A unique identifier to categorize the safe processes.
- **Enabled**: Shows whether a safe process is enabled or disabled. The **X** icon indicates that the process is disabled and the **Checkmark **icon indicates that the process is enabled.
- **Executable File Path**: The executable file path expressed in absolute values.
- **Executable File Regex**: The executable file path expressed in regular expressions.
- **Executable File Hash**: The executable file hash (e.g., md5, sha1, and sha256).
- **Certificate Issuer**: A unique certificate issuer name that identifies the issuer of the digital certificate.
- **Certificate Serial**: A unique certificate serial number issued by a certificate authority.
- **Certificate Thumbprint**: A unique certificate thumbprint that is a hash of a certificate.
- **Type**: Shows whether a safe process is internal or not. The internal safe processes are identified using the Internal label.
- Show or hide internal safe processes. These are a set of predesignated safe processes that are provided by Zscaler ITDR.
- [Configure a safe process](/itdr/configuring-safe-process) to prevent generating false positives. You can designate known and trusted processes in your environment as safe processes.
- [Edit or delete a safe process](/itdr/editing-or-deleting-safe-process)[.](/deception/editing-or-deleting-safe-process)
![The Safe Processes page with Add Safe Process option](/downloads/itdr/endpoint-settings/safe-processes/about-safe-processes/itdr-safe-processes-page.png)