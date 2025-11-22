# About Server Agents
Source: https://help.zscaler.com/deception/about-server-agents
PDF: https://help.zscaler.com/pdf/com/en/1531600.pdf

As cyber threats evolve, attackers are increasingly targeting server infrastructure to gain unauthorized access, exfiltrate data, or disrupt operations. A server agent is used to [deploy and manage Active Directory (AD) decoys](/deception/about-active-directory-decoys) (users and computer objects). The server agent improves the effectiveness of AD decoys by simulating activities on AD decoy objects by performing password resets, login actions, etc.
Server agents provide the following benefits and enable you to:
- Automate the AD decoy deployment, eliminating manual script downloads from the Zscaler Deception Admin Portal.
- Monitor events and forward logs to the Deception Admin Portal or SIEM solutions.
- Refresh AD decoys by simulating activities (e.g., password resets, login actions), ensuring decoys appear active and legitimate.
About the Agents Page
On the Agents page (Settings > Server Agent Settings > Agents), you can do the following:
- [View and obtain the server agent registration token](/deception/obtaining-agent-registration-token-0).
- [Download a server agent](/deception/downloading-server-agent).
- [Export the configuration details of the server agent.](/deception/exporting-server-agent-configurations)
-
Select any of the following actions:
- **Show all agents**: Shows or hides inactive server agents.
- If enabled, inactive server agents are shown along with active agents.
- If disabled, only active server agents are shown. By default, the **Show all agents **toggle is disabled.
- **Uninstall All Agents**: [Uninstalls all server agents.](/deception/uninstalling-or-deleting-server-agents)
- **Uninstall Selected**: [Uninstalls only the selected server agents.](/deception/uninstalling-or-deleting-server-agents)
- **Delete Selected**:** **[Deletes the selected server agents.](/deception/uninstalling-or-deleting-server-agents)
- **Trigger Logs**: Fetches the log data from server agents and makes it available for [downloading](/deception/downloading-server-agent-logs). These are the server agent's activity logs that are used for troubleshooting.
[See image.](#server_agents_actions_menu_options)
- View the list of systems on which the server agent is installed. For each system, you can see:
- **System Name**: The name of the system on which a server agent is installed.
- **Domain Name**: The name of the domain.
- **First Seen**: The date and time when the server agent was installed.
- **Last Seen**: The date and time when the server agent was last connected to the Deception Admin Portal.
- **OS Version**: The operating system's (OS) name and version.
- **Version**: The server agent's version number. You can filter the versions. If the **Show all agents **option is enabled, you can view all the versions. If disabled, you can view only the versions of active server agents.
- **Server Type**: The type of AD server. You can filter the required server types.
- **DC Type**: The type of domain controller.
- **IP**: The IP address of the system.
- View audit status, [uninstall](/deception/uninstalling-or-deleting-server-agents), and [delete a server agent.](/deception/uninstalling-or-deleting-server-agents)
![View server agents page](/downloads/deception/settings/server-agents-settings/agents/about-server-agent/zscaler-deception-server-agent.png)
[]
![View server agents actions menu options](/downloads/deception/settings/server-agents-settings/agents/about-server-agent/zscaler-deception-server-agent-action-menu.png)