# About Server Agents
Source: https://help.zscaler.com/itdr/about-server-agents
PDF: https://help.zscaler.com/pdf/com/en/1531856.pdf

As cyber threats evolve, attackers are increasingly targeting server infrastructure to gain unauthorized access, exfiltrate data, or disrupt operations. The Zscaler ITDR server agent monitors Active Directory (AD) users and computer activities, providing insights to help you quickly address identity-based threats. You can enable session tracking in the server agent policy to monitor logon activities. You can also enable password analysis to identify compromised or weak passwords by checking hashes against leaked databases, common patterns, and custom dictionaries while also monitoring for password reuse or rotation.
Server agents provide the following benefits and enable you to:
- Continuously monitor AD activity for identity threat detection.
- Monitor logon activities and identify any anomalous user activity.
- Reducing account compromise risk by analyzing weak passwords
About the Agents Page
On the Agents page (Settings > Server Agent Settings > Agents), you can do the following:
- [View and obtain the server agent registration token](/itdr/obtaining-server-agent-registration-token).
- [Download a server agent](/itdr/downloading-server-agent).
- [Export the configuration details of the server agent](/itdr/exporting-server-agent-configurations).
-
Select any of the following options from the **Actions **drop-down menu:
- **Show all agents**: Shows or hides inactive server agents.
- If enabled, inactive server agents are shown along with active agents.
- If disabled, only active server agents are shown. By default, the **Show all agents **toggle is disabled.
- **Uninstall All Agents**: [Uninstalls all server agents.](/itdr/uninstalling-or-deleting-server-agents)
- **Uninstall Selected**: [Uninstalls only the selected server agents.](/itdr/uninstalling-or-deleting-server-agents)
- **Delete Selected**:** **[Deletes the selected server agents.](/itdr/uninstalling-or-deleting-server-agents)
- **Trigger Logs**: Fetches the log data from server agents and makes it available for [downloading](/itdr/downloading-server-agent-logs). These are the server agent's activity logs that are used for troubleshooting.
[See image.](#server_agents_actions_menu_options)
- View a list of systems on which the server agent is installed. For each system, you can see:
- **System Name**: The name of the system on which a server agent is installed.
- **Domain Name**: The name of the domain.
- **First Seen**: The date and time when the server agent was installed.
- **Last Seen**: The date and time when the server agent was last connected to the ITDR Admin Portal.
- **OS Version**: The operating system's (OS) name and version.
- **Version**: The server agent's version number. You can filter the versions. If the **Show all agents **option is enabled, you can view all the versions. If disabled, you can view only the versions of active server agents.
- **Server Type**: The type of AD server. You can filter the required server types.
- **DC Type**: The type of domain controller.
- **IP**: The IP address of the system.
- View error logs, view audit policy status, [uninstall a server agent](https://help.zscaler.com/itdr/v4_30/uninstalling-or-deleting-server-agents), and [delete a server agent.](/itdr/uninstalling-or-deleting-server-agents)
![Viewing the Server Agents Page](/downloads/itdr/settings/server-agents-settings/agents/about-server-agents/Server%20agent_0.png)
When a critical event occurs on the agent, error logs are generated. Click the **View Error Logs** icon to open the **Error Logs **window and view the latest log entry.
[See image.](#Error_log)
[]![Error Logs](/downloads/itdr/settings/server-agents-settings/agents/about-server-agents/Serveragent_errorlog.png)
[]
![View Server Agents Actions menu options](/downloads/deception/settings/server-agents-settings/agents/about-server-agent/zscaler-deception-server-agent-action-menu.png)