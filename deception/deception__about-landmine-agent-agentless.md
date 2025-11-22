# About Landmine Agent and Agentless
Source: https://help.zscaler.com/deception/about-landmine-agent-agentless
PDF: https://help.zscaler.com/pdf/com/en/1531324.pdf

A landmine is an endpoint component that deploys decoy credentials, files, browser cookies, processes, etc. on real endpoints in your network. You can download a landmine either as an agent installer or agentless installer from the Zscaler Deception Admin Portal.
Landmine provides the following benefits and enables you to:
- Deploy full-featured active deception via a persistent agent (in agent mode) running on endpoints in your network.
- Deploy decoys with a limited set of deception lures via a permanent service (in agentless mode) running on endpoints.
[Zscaler ITDR](/itdr/what-zscaler-itdr) components such as CredentialExposure.Console.exe, CredEx.exe, or CredExInstaller.exe are also installed on endpoints as part of Zscaler Client Connector. The processes associated with these components are legitimate processes and will not activate (run) unless the respective functionality is enabled in ITDR.
To learn more, see [Supported Deception Features for Landmine Agent and Agentless Installers](/deception/supported-deception-features-landmine-agent-and-agentless).
You can install landmine agents and agentless installers on the following supported platforms:
- Landmine Agent:
- [Windows](/deception/installing-landmine-agent-windows)
- [macOS](/deception/installing-landmine-agent-macos)
- [Linux](/deception/installing-landmine-agent-linux)
- [Windows Using MECM or SCCM](/deception/installing-landmine-agents-windows-using-mecm-or-sccm)
- Landmine Agentless:
- [Windows](/deception/running-landmine-agentless-installer-windows)
- [macOS](/deception/running-landmine-agentless-installer-macos)
- [Linux](/deception/running-landmine-agentless-installer-linux)
About the Landmine Agents Page
On the Agents page (Settings > Endpoint Settings > Agents), you can do the following:
- [Obtain the landmine registration token](/deception/obtaining-agent-registration-token).
- [Download landmine agent ](/deception/downloading-landmine-agents)and [agentless](/deception/downloading-landmine-agentless).
- [Export landmine agent configuration details to a file](/deception/exporting-landmine-agents-configuration).
-
Perform an action on agents or a group of agents by selecting an option from the **Actions **drop-down menu:
- **Show all agents**: Shows or hides inactive agents.
- If enabled, inactive agents are shown along with active agents.
-
If disabled, only active agents are shown. By default, the **Show all agents **toggle is disabled.
Landmine agents (ZCC Integrated and Standalone) with last check-in time older than 7 days are considered inactive and are hidden. The landmine agentless is always active.
- **Uninstall All Agents**: [Uninstalls all landmine agents.](/deception/uninstalling-or-deleting-landmine-agents)
- **Uninstall Selected**: [Uninstalls only selected landmine agents.](/deception/uninstalling-or-deleting-landmine-agents)
- **Delete Selected**:** **[Deletes selected landmine agents.](/deception/uninstalling-or-deleting-landmine-agents)
- **Trigger Logs**: Fetches log data from landmine agents and makes it available for [download from the Deception Admin Portal](/deception/downloading-landmine-agent-logs-endpoint).
[See image.](#agents-action-menu)
- View a list of systems on which the landmine agent or agentless installers are installed. For each system, you can view:
- **System Name**: The name of the system.
- **System User Name**: The usernames of the system.
- **Client Connector User: **The usernames in Zscaler Client Connector.
- **Client Connector Version**: The version number of Zscaler Client Connector installed on the endpoint.
- **Matched Policies**: The policies that can be applied on the endpoint.
- **First Seen**: The date and time when the agent was installed on the system.
- **Last Seen**: The date and time when the agent was last connected to the Deception Admin Portal
- **OS Version**: The operating system (OS) name and version.
- **Version**: The landmine agent version number. You can filter the agents table by choosing a specific version number from the **Version **drop-down menu. The values listed in the drop-down menu shows only the version number of active agents if the **Show all agents** option is disabled. All possible values are listed in the drop-down only if the **Show all agents** option is enabled from the **Actions **menu.
- **Type**: The type of agent (ZCC Integrated, Standalone, or Agentless). You can filter the agents table by choosing a specific agent type from the **Type **drop-down menu.
- **IP**: The IP address of the system.
- View error logs, [view policy details](/deception/viewing-policy-details), [uninstall or delete an agent](/deception/uninstalling-or-deleting-landmine-agents), and [download agent logs](/deception/downloading-landmine-agent-logs-endpoint).
![The Landmine Agents page](/downloads/deception/settings/endpoint-settings/agents/about-landmine-agent-agentless/zscaler-deception-about-agents.jpg)
When a critical event occurs on the agent, error logs are generated. Click the **View Error Logs** icon to open the **Error Logs **window and view the latest log entry.
[See image.](#Error_logs_window)
[]![Error Logs](/downloads/deception/settings/endpoint-settings/agents/about-landmine-agent-agentless/endpoint_errorlog.png)
[]
![The Actions menu on the Agents page](/downloads/deception/settings/endpoint-settings/agents/about-landmine-agent-agentless/zscaler-deception-agents-page-options.jpg)