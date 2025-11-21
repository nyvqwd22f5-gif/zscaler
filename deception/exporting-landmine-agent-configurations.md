# Exporting Landmine Agent Configurations
Source: https://help.zscaler.com/deception/exporting-landmine-agent-configurations
PDF: https://help.zscaler.com/pdf/com/en/1531313.pdf

You can export landmine agent configuration details as a CSV or JSON file. You can export the configuration details of all the installed agents, or filter the agents based on the system name, user, policy, operating system, Zscaler Deception Admin Portal version, and IP address.
Use the search field in the table columns to filter the agents per your requirements. For example, you can enter the system user name in the search field of the **System User Name **column to filter agents for a particular user.
[See image.](#zd-agent-filter)
To export landmine agents' configuration details:
- Go to **Settings **> **Endpoint Settings **> **Agents**.
-
Click **Export** and select an option from the drop-down menu:
- **All agents as CSV**: Exports the configuration details of all agents as a CSV file.
-
**All agents as JSON**: Exports the configuration details of all agents as a JSON file.
The **All agents as CSV** and **All agents as JSON** options export only the agents that are shown in the agents table. The agents table can include or exclude inactive agents, depending on whether the **Show all agents** option under the **Actions **drop-down menu is enabled or disabled. If you want to export all agents including the inactive agents, make sure the **Show all agents** option is selected.
[See image.](#show-all-option-selection)
- **Filtered agents as CSV**: Exports the configuration details of all the filtered agents as a CSV file.
- **Filtered agents as JSON**: Exports the configuration details of all the filtered agents as a JSON file.
[See image.](#zd-export-options-agents)
A CSV or JSON file with the landmine agent configuration details is downloaded to your local system.
[]![Filter landmine agents by users](/downloads/deception/deceive/landmine-decoys/agents/agent-management/exporting-landmine-agent-configurations/zscaler-deception-search-filter-new.jpg)
[]![Export landmine agents configuration as a CSV or JSON file.](/downloads/deception/deceive/landmine-decoys/agents/agent-management/exporting-landmine-agent-configurations/zscaler-deception-export-options-agents-new.jpg)
[]![A screenshot highlighting the Show all agents option](/downloads/deception/deceive/landmine-decoys/agents/agent-management/exporting-landmine-agent-configurations/zscaler-deception-endpoint-settings-show-all.jpg)