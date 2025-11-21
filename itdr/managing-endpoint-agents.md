# Managing Endpoint Agents
Source: https://help.zscaler.com/itdr/managing-endpoint-agents
PDF: https://help.zscaler.com/pdf/com/en/1531662.pdf

You can manage endpoint agents using the following options:
- [Exporting Endpoint Agent Configurations](#Exporting_Endpoint_Agent_Configurations)
- [Viewing Threat Detection Policy Details](#Viewing_Threat_Detection_Policy_Details)
- [Downloading Endpoint Agent Logs](#Downloading_Endpoint_Agent_Logs)
- [Uninstalling Endpoint Agents](#uninstalling_endpoint_agents)
- [Deleting Endpoint Agents](#deleting_endpoint_agents)
[]
You can export endpoint agent configuration details as a CSV or JSON file. You can export the configuration details of all the endpoint agents, or filter the agents based on the system name, user, policy, operating system version, Zscaler ITDR Admin Portal version, and IP address.
Use the search field in the table columns to filter the endpoint agents per your requirements. For example, you can enter the system user name in the search field of the **System User Name **column to filter agents for a particular user.
[See image.](#itdr-agent-filter)
To export endpoint agents' configuration details:
- Go to **Settings** > **Endpoint Settings** > **Agents**.
-
Click **Export** and select an option from the drop-down menu:
- **All agents as CSV**: Exports the configuration details of all agents as a CSV file.
-
**All agents as JSON**: Exports the configuration details of all agents as a JSON file.
The **All agents as CSV** and **All agents as JSON** options export only the agents that are shown in the agents table. The agents table can include or exclude inactive agents, depending on whether the **Show all agents** option under the **Actions **drop-down menu is enabled or disabled. If you want to export all agents including the inactive agents, make sure the **Show all agents** option is selected.
[See image.](#show-all-option)
- **Filtered agents as CSV**: Exports the configuration details of all the filtered agents as a CSV file.
- **Filtered agents as JSON**: Exports the configuration details of all the filtered agents as a JSON file.
[See image.](#itdr-export-options-agents)
A CSV or JSON file with the endpoint agent configuration details is downloaded to your system.
[]
You can view details of the threat detection policy and the [Active Directory threat detection modules](/itdr/configuring-active-directory-threat-detection-module) that are configured for the policy.
To view details of the threat detection policies:
- Go to **Settings** > **Endpoint Settings** > **Agents**.
- Select a system on which the policy is deployed, and under the **Actions **column, click the **View **icon.
-
[See image.](#view-policy-details-icon)
The policy details page appears. You can view:
- **Details**: The system name, username, domain name, matched threat detection policy, operating system name and version, date and time when the endpoint agent was last connected to the ITDR Admin Portal, and type of agent on the system.
- **Threat Detection: **The policy name and the status (True if enabled, False if disabled) of the following [AD threat detection](/itdr/configuring-active-directory-threat-detection-module) modules:
- DCSync
- DCShadow
- Zerologon
- Session Enumeration
- Monitored Privileged Accounts
- Kerberoast Detection
- LDAP Detection
[See image.](#policy-details)
[]
You can download the endpoint agent logs from an endpoint that is connected to the ITDR Admin Portal. The endpoint agent logs contain records of endpoint agent activities (agent installation, threat detection policy applied to the endpoint agent, endpoint agent connection details, etc.) in the ITDR Admin Portal. You can send these logs to Zscaler Support to troubleshoot issues.
To download endpoint agent logs from an endpoint:
- Go to **Settings** > **Endpoint Settings** > **Agents**.
- In the **Agents** table, select an agent for which you want to download the logs.
-
Click **Actions** > **Trigger Logs**.
[See image.](#trigger-logs-action-menu)
After a few minutes, a **Download** icon appears under the **Actions** column of the selected agent.
[See image.](#download-agent-logs-icon)
To check when the agent logs were uploaded to the ITDR Admin Portal, hover over the **Download **icon.
[See image.](#itdr-agent-log-tooltip)
-
Click the **Download **icon.
The endpoint agent logs from the endpoint are downloaded to your system in a compressed (.zip) file.
[]
To uninstall endpoint agents:
- Go to **Settings** > **Endpoint Settings** > **Agents**.
-
Locate the endpoint agent you want to uninstall, and under the **Actions** column, click the **Uninstall **icon.
[See image.](#itdr-uninstall-agent)
- In the **Uninstall Agent** window, choose an option:
- **Uninstall**: The agent removes the policies from the endpoint, and then it uninstalls itself. The agent tries to remove the policies for up to three days before uninstalling itself.
-
**Force Uninstall**: The agent uninstalls the policies from the endpoint on a best-effort basis, and then it uninstalls itself.
[See image.](#zd-landmine-agent-delete-dialog)
A confirmation message appears indicating that the endpoint agent is uninstalled on the specific system, and the agent's entry is deleted from the **Agents** table.
[]
To delete an endpoint agent:
- Go to **Settings** > **Endpoint Settings** > **Agents**.
-
Locate the endpoint agent that you want to delete, and under the **Actions **column, click the **Delete **icon.
[See image.](#itdr-delete-agent)
-
In the confirmation window, click **OK**.
A confirmation message appears indicating that the endpoint agent is deleted successfully.
Endpoint agents cannot be deleted if their **Last Seen** value is less than 7 days.
[]![Uninstall or force uninstall a landmine agent](/downloads/deception/product-documentation/deceive/endpoint-decoys/agents/uninstalling-or-deleting-landmine-agents/zscaler-deception-uninstall-agents.png)
[]![itdr-endpoint-agents-delete-icon.png](/downloads/itdr/endpoint-settings/agents/uninstalling-or-deleting-endpoint-agents/itdr-endpoint-agents-delete-icon.png)
[]![itdr-endpoint-agent-delete-icon.png](/downloads/itdr/endpoint-settings/agents/uninstalling-or-deleting-endpoint-agents/itdr-endpoint-agent-delete-icon.png)
[]![Trigger downloading of landmine agent logs from an endpoint](/downloads/itdr/endpoint-settings/agents/downloading-endpoint-agent-logs-endpoint/itdr-agent-trigger-logs_0.png)
[]![Download landmine agent logs icon](/downloads/itdr/endpoint-settings/agents/downloading-endpoint-agent-logs-endpoint/itdr-endpoint-agents-download-logs-icon.png)
[]![A sceenshot capturing the mouseover tooltip that displays upload date of an agent log](/downloads/itdr/endpoint-settings/agents/downloading-endpoint-agent-logs-endpoint/itdr-logs-download-date.png)
[]![View policy details icon](/downloads/itdr/endpoint-settings/agents/viewing-policy-details/itdr-endpoint-agents-view-policy-details.png)
[]![View policy details](/downloads/itdr/endpoint-settings/agents/viewing-policy-details/itdr-agents-view-policy-details.png)
[]![Filter landmine agents by users](/downloads/itdr/endpoint-settings/agents/exporting-endpoint-agent-configurations/itdr-search-endpoint-agent.png)
[]![Export landmine agents configuration as a CSV or JSON file.](/downloads/itdr/endpoint-settings/agents/exporting-endpoint-agent-configurations/itdr-export-endpoint-agent.png)
[]![A screenshot highlighting the Show all agents option](/downloads/deception/deceive/landmine-decoys/agents/agent-management/exporting-landmine-agent-configurations/zscaler-deception-endpoint-settings-show-all_0.jpg)