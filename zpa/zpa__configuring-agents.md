# Configuring Agents
Source: https://help.zscaler.com/zpa/configuring-agents
PDF: https://help.zscaler.com/pdf/com/en/1531952.pdf

Agents in Microsegmentation are installed on users' server workloads to collect endpoint data. You can install agents using most configuration management tools that accommodate Windows .msi files or Linux .rpm files. After configuring agents, you can configure [agent groups](/zpa/configuring-agent-groups) and [agent provisioning keys](/zpa/about-agent-provisioning-keys-page).
To configure an agent:
- Go to **Microsegmentation** > **Agent Management**.
- Click the** Agents** tab.
- Click **Add Agent**.
The **Add Agent** window appears.
[See image.](#Agent-Management_Add-Agent)
- In the **Add Agent** window:
- **Agent Group**: Select an agent group from the drop-down menu. If there are no agent groups available, select **Create New Agent Group** and follow the onscreen instructions. You must place agents in groups based on the upgrade plan and location. For the upgrade plan, agents in the same agent group inherit the same upgrade plan including version profile, upgrade schedule, upgrade order (serial or parallel), and upgrade failure behavior (halt or skip). For agents deployed in on-premises data center environments, you must enable Advanced Settings and provide the admin-supplied region, VPCs, and Subnet IDs. These attributes are inherited by all agents in the group. To learn more, see [Configuring Agent Groups](/zpa/configuring-agent-groups).
- Click **Next**.
[See image.](#Add-Agent-window_Agent-Group)
- **Provisioning Key**: Select an agent provisioning key from the drop-down menu. If there are no agent provisioning keys available, select **Create New Provisioning Key** and follow the onscreen instructions. To learn more, see [About Agent Provisioning Keys](/zpa/about-agent-provisioning-keys-page)*.*
- Click **Next**.
[See image.](#Add-Agent-window_Provisioning-Key)
- **Review**: Review the entered information to ensure it is correct:
- **Agent Group**:
- **Name**
- **Status **(this is enabled by default)
- **Description**
- **Auto Update **(this is disabled by default)
- **Provisioning Key**:
- **Name**
- **Maximum Reuse**
- Click **Next**.
[See image.](#Add-Agent-window_Review)
- **Review Documentation**: Review the entered information and the agent provisioning key file.
- Select the operating system for the agent (**Linux** or **Windows**).
- Download the installation binary to your server workload.
- Copy the provisioning key provided into a file called provision_key in the same directory as the installation script.
- Run the downloaded binary on your server workload.
[See image.](#Add-Agent-window_Review-Documentation)
- Click **Done**.
After your new agent first deploys onto a workload and is registered with the agent provisioning key, it appears in the list of Agents.
[]![A view of the agents page and all its actions.](/downloads/zpa/microsegmentation/agent-management/agents/configuring-agents/Agent-Management_Agents_Add-Agent2.png)
[]![A view of the Agent Group section when configuring a new agent. ](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agents/Add-Agent-window_Agent-Group1.png)
[]![A view of the Provisioning Key section when configuring a new agent. ](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agents/Add-Agent-window_Provisioning-Key.png)
[]![A view of the Review section when configuring a new agent. ](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agents/Add-Agent-window_Review.png)
[]![A view of the Review Documentation section when configuring a new agent. ](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agents/Add-Agent-window_Review-Documentation.png)