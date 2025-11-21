# Uninstalling or Deleting Landmine Agents
Source: https://help.zscaler.com/deception/uninstalling-or-deleting-landmine-agents
PDF: https://help.zscaler.com/pdf/com/en/1531312.pdf

This article provides instructions for uninstalling or deleting landmine agents.
Uninstalling Landmine Agents from the Zscaler Deception Admin Portal
You can uninstall a single agent, multiple agents, or all agents from the Deception Admin Portal.
To uninstall agents:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
- In the **Agents** table, choose one of the following options:
-
Select the agents that you want to uninstall, and then click **Actions** > **Uninstall Selected** to uninstall them.
[See image.](#zd-landmine-selected-uninstall)
-
Click **Actions** > **Uninstall All Agents** to uninstall all agents.
[See image.](#zd-landmine-all-uninstall)
-
Click the **Uninstall **icon under the **Actions **column to uninstall standalone landmine agents individually.
[See image.](#zd-uninstall-standalone-agent-individual)
- In the **Uninstall Agent** window, choose an option:
- **Uninstall**: The agent removes the policies from the endpoint, and then it uninstalls itself. The agent tries to remove the policies for three days before uninstalling itself.
-
**Force Uninstall**: The agent uninstalls the policies from the endpoint on a best-effort basis, and then it uninstalls itself.
[See image.](#zd-landmine-agent-delete-dialog)
A confirmation message appears indicating that the uninstallation request is successful. After the agents are uninstalled on the requested system, the agent's entry is deleted from the **Agents** table.
Uninstalling Agents on Windows
Occasionally, uninstallation of agents from the Deception Admin Portal can fail when you try to remotely uninstall agents. It can also fail due to network connectivity issues. In such scenarios, you can uninstall the agents using CLI.
To uninstall agents on Windows:
- Click **Start**.
- In the Start Search box, enter `cmd`, and then press `CTRL+SHIFT+ENTER`.
- When the **User Account Control (UAC)** dialog box appears, click **Yes**.
-
In the command prompt, enter the following command to uninstall the agent:
msiexec /qn /x {94e4ac3b-2519-46eb-97bd-d6be9b6c8f55}
The landmine agent is uninstalled. All the services and program files related to the agent are removed from the system. You can verify if the files have been removed from the `C:\ProgramData` folder. The uninstaller attempts to remove the system entry from the Deception Admin Portal. If the agent fails to remove the system entry for 5 consecutive times, it continues with the uninstallation. If this is unsuccessful, the entry must be deleted manually.
Deleting Landmine Agents
To delete a landmine agent:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
- In the **Agents** table, choose one of the following options:
-
Select the agents that you want to delete, and then click **Actions** > **Delete Selected** to delete them.
[See image.](#zd-delete-landmine-agents)
-
Click the **Delete **icon under the **Actions **column to delete standalone landmine agents individually.
[See image.](#zd-delete-standalone-agent-individual)
-
In the confirmation window, click **OK**.
[See image.](#zd-delete-landmine-agents-dialog)
- When you delete an agent, its entry is removed from the Deception Admin Portal only. The agent is not uninstalled from the system.
- Landmine agents cannot be deleted if their **Last Seen** value is under 7 days.
[]![Uninstall multiple landmine agents](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-uninstall-selected-agents-new.jpg)
[]![Uninstall all landmine agents ](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-uninstall-all-agents-new.jpg)
[]![Uninstall or force uninstall a landmine agent](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/uninstalling-or-deleting-landmine-agents/zscaler-deception-uninstall-agents.png)
[]![Delete landmine agents](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-delete-selected-agents-new.jpg)
[]![Delete landmine agents](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-delete-landmine-agent.png)
[]![A screenshot capturing the option to delete each standalone landmine agent ](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-uninstall-standalone-individual-new.jpg)
[]![A screenshot capturing the option to uninstall standalone landmine agents](/downloads/deception/deceive/landmine-decoys/agents/agent-management/uninstalling-or-deleting-landmine-agents/zscaler-deception-delete-standalone-individual-new.jpg)