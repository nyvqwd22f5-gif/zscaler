# Configuring Agent Groups
Source: https://help.zscaler.com/zpa/configuring-agent-groups
PDF: https://help.zscaler.com/pdf/com/en/1531956.pdf

Agents in Microsegmentation are installed on servers' workloads, such as virtual machines or bare metal servers. You can install agents using most configuration management tools that accommodate Windows .msi files or Linux .deb and .rpm files.
Agents must be placed in the same group based on the upgrade plan and location. For the upgrade plan, agents in the same agent group inherit the same upgrade plan, including version profile, upgrade schedule, upgrade order (serial or parallel), and upgrade failure behavior (halt or skip). For agents deployed in on-premises data center environments, customers must enable Advanced Settings and provide the admin-supplied region, virtual private cloud (VPC), and Subnet IDs. These attributes are inherited by all agents in the group.
Agent groups allow admins to group together different agents to organize them depending on different local machines they are deployed to. Admins can configure, [edit](/zpa/editing-agent-groups), and [delete](/zpa/deleting-agent-groups) agent groups as needed.
To configure an agent group:
- Go to **Microsegmentation** > **Agent Management**.
- Click the** Agent Groups** tab.
- Click **Add Agent Group**.
The **Add Agent Group** window appears.
[See image.](#Agent-Management_Add-Agent-Group)
- In the **Add Agent Group** window:
- **Name**: Enter a name for the new agent group.
- **Admin Status**: Enable or disable the admin status.
- **Description**: (Optional) Enter a description. The limit is 2,500 characters.
- **Cloud**: Select the cloud for the agent group (**AWS**, **Azure**, **GCP**, or **On Premises**).
[See image.](#Agent-Group_Name-AdminStatus-Description)
- Expand the **Version Profile & Configurations** menu:
- **Auto Update**: Select **Enabled **or **Disabled**. If you select **Enabled**, set the parameters for the following options:
- **Version Profile**: Select **Latest** or **Custom**.
- If you select **Latest**, the most recently available profile is selected.
- If you select **Custom**, choose from the **Custom Version Profile** drop-down menu.
- **Agent Version**: The version number of the agent.
- **Schedule Agent Upgrade On**: Choose the day of the week, time, and time zone upgrades should happen.
- **Update Sequence**: Select **Serial** or **Parallel**.
- If you select **Serial**, agents are upgraded one at a time.
- If you select **Parallel**, the system automatically upgrades agents in one or more batches. The batch size is automatically calculated depending on the total agent count in the group. For smaller agent groups, the first batch might include all agents so users might notice all agents are being upgraded.
- **In case of upgrade failure**: Choose one of the following options:
- If **Halt next agent upgrade** is selected, two potential behaviors can happen:
- If selected with the **Serial** upgrade sequence, then the upgrade process is immediately paused and the agent group is marked as Failed.
- If selected with the **Parallel** upgrade sequence, the current batch of agents continues upgrading until they return to their respective status. However, the next agent batch is not started, and the agent groups are marked as Failed.
- If **Skip to next agent** is selected, the system continues to upgrade the next agent, and the agent group's status is marked as Incomplete.
[See image.](#Agent-Group_Version-Profile-and-Configurations)
- **Advanced Settings**: Enable different options for on-premises agents.
- **Enable on-premises**: Select this checkbox to enable the agent group when a workload is on-premises. By enabling this setting, the admin can override the Region, VPC ID, and Subnet ID settings reported by the agent. This setting is intended to be used when the agent is deployed in on-premises data centers where Instance Meta-Data Service (IMDS) is unavailable. If agents are deployed in cloud-based virtual machines, then the agents override the values discovered via IMDS with the admin-supplied values.
If enabled, enter the following information:
- VPC ID
- Subnet ID
- Region
[See image.](#Agent-Group_Advanced-Settings)
- Click **Next**.
- **Provisioning Key**: Enter details for provisioning key data.
- **Name**: Enter the provisioning key name.
- **Maximum Reuse of Key**: Enter a number from 1 to 1,000 for how many times the provisioning key can be reused.
- **Signing Certificate**: Select a signing certificate from the drop-down menu.
[See image.](#Agent-Group_Provisioning-Key)
- **Review**: Check that the entered information for **Agent Group** and **Provisioning Key** are correct.
[See image.](#Agent-Group_Review)
- Click **Next**.
- **Review Documentation**: Review the selected information and the installation file options for your system. Select the operating system (**Linux** or **Windows**).
- For Linux systems:
- Download the Agent Manager to your local machine: RPM, Ubuntu, or GPG Key (optional):
- Copy the **Provisioning Key** into a file named `provision_key` in the /opt/zscaler/zms/var directory. If the directory does not exit, you must create it to continue with the installation.
- Install the downloaded Agent Manager.
[See image.](#Agent-Group_Review-Documentation)
- For Windows systems:
- Download the Agent Manager MSI for Windows to your local machine.
- Copy the **Provisioning Key** into a file named `provision_key` in the directory of your choice.
- Install the downloaded ZMS Manager MSI.
[See image.](#Windows-instructions)
- Click **Done**.
Your new agent group appears in the list of Agent Groups.
[]![A view of the Agents Groups page and all its actions.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups/Agent-Management_Agent-Groups_Add-Agent-Group.png)
[]![Image]()
![The first page of the agent group configuration window shows the fields for the Name and Description, the toggle for the Admin Status, and the options to select for Cloud, such as AWS, Azure, GCP, and On Premises.](/downloads/zpa/microsegmentation/agent-management/agent-groups/configuring-agent-groups/Add-Agent-Group_Name-AdminStatus-PolicyStatus-Description-Cloud1.png)
[]![A view of the Version Profile & Configurations for an Agent Group.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups/Agent-Group_Version-Profile-and-Configurations.png)
[]![A view of the Advanced Settings fields.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups/Agent-Group_Advanced-Settings.png)
[]![A view of the Provisioning Key fields.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups/Agent-Group_Provisioning-Key.png)
[]![A view of the Review fields.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups/Agent-Group_Review.png)
[]![A view of the Review Documentation fields.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups-draft-doc-56043/Add-Agent-window_Review-Documentation_Linux-steps-FULL_RPM-Ubuntu-GPG.png)
[]![Review the Windows instructions.](/downloads/tech-pubs-drafts/zws-draft-articles/configuring-agent-groups-draft-doc-56043/Add-Agent-window_Review-Documentation_Windows-steps.png)