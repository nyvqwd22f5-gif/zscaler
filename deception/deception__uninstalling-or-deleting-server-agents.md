# Uninstalling or Deleting Server Agents
Source: https://help.zscaler.com/deception/uninstalling-or-deleting-server-agents
PDF: https://help.zscaler.com/pdf/com/en/1531605.pdf

This article provides instructions for uninstalling or deleting server agents.
Uninstalling Server Agents
You can uninstall a single agent, multiple agents, or all server agents from the Deception Admin Portal.
To uninstall server agents:
- Go to **Settings **> **Server Agent Settings **> **Agents**.
- In the **Agents** table, choose one of the following options:
-
Select the server agents that you want to uninstall, and then click **Actions** > **Uninstall Selected** to uninstall them.
[See image.](#zd-landmine-selected-uninstall)
-
Click **Actions** > **Uninstall All Agents** to uninstall all server agents.
[See image.](#zd-landmine-all-uninstall)
-
Click the **Uninstall **icon under the **Actions **column to uninstall server agents individually.
[See image.](#zd-uninstall-standalone-agent-individual)
-
In the **Uninstall Agent** window, click **Uninstall**. The server agent tries to remove the policies from the servers for three days, and then it uninstalls itself.
[See image.](#zd-landmine-agent-delete-dialog)
A confirmation message appears indicating that the uninstallation request is successful. After the server agents are uninstalled on the requested system, the agent's entry is deleted from the **Agents** table.
Deleting Server Agents
To delete a server agent:
- Go to **Settings **> **Server Agent Settings **> **Agents**.
- In the **Agents** table, choose one of the following options:
-
Select the server agents that you want to delete, and then click **Actions** > **Delete Selected** to delete them.
[See image.](#zd-delete-landmine-agents)
-
Click the **Delete **icon under the **Actions **column to delete server agents individually.
[See image.](#zd-delete-standalone-agent-individual)
-
In the confirmation window, click **OK**.
[See image.](#zd-delete-landmine-agents-dialog)
- When you delete a server agent, its entry is removed from the Deception Admin Portal only. The agent is not uninstalled from the server.
- Server agents cannot be deleted if their Last Seen value is under 7 days.
[]![Uninstall multiple server agents](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-uninstall-selected.png)
[]![Uninstall all server agents ](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-uninstall-all-agents.png)
[]![Uninstall a server agent](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-uninstall-agent-window.png)
[]![Delete server agents](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-delete-selected.png)
[]![View server agents deleting confirmation window](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-delete-server-agent-pop-up.png)
[]![View standalone server agent deletion ](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-delete-individual-agents.png)
[]![Uninstall standalone server agent](/downloads/deception/settings/server-agents-settings/agents/agent-management/uninstalling-or-deleting-server-agents/zscaler-deception-server-agent-uninstall-individual-agents.png)