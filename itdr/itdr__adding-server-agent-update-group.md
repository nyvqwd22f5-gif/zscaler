# Adding a Server Agent Update Group
Source: https://help.zscaler.com/itdr/adding-server-agent-update-group
PDF: https://help.zscaler.com/pdf/com/en/1531862.pdf

You can add an agent update group with a selection criterion based on hostnames to selectively roll out the updates for server agents.
To add an agent update group:
- Go to **Settings **> **Server Agent Settings **> **Agent Update Groups**.
-
Click **Add Group**.
[See image.](#add-agent-update-group)
- In the **Agent Update Group Details** window:
- **Name**: Enter a name for the agent update group.
- **Enable Updates**: Select to enable phased updates for the agent update group.
- **Selection Criterion**: Select a criterion from the drop-down menu:
-
**Hostname List**: Applies updates to all the agents where the hostname of the system exactly matches the hostnames specified in the **Hostname List** field.
[See image.](#agent-update-group-hostname)
-
**Hostname RegEx**: Applies updates to all the agents where the hostname of the system matches the hostname pattern specified as a regular expression in the **Hostname RegEx **field.
[See image.](#agent-update-group-regex)
Zscaler recommends that you add a group named "All systems" with a catch-all regular expression ( .* ), and enable this group after you complete the testing to make sure all servers are upgraded.
-
Click **Save**.
The agent update group is created and appears in the **Agent Update Groups** table.
[]![View add group option ](/downloads/deception/settings/server-agents-settings/agent-update-groups/adding-server-agent-update-group/zscaler-deception-server-agent-adding-agent-update-group.png)
[]
![View agent update group details window](/downloads/deception/settings/server-agents-settings/agent-update-groups/adding-server-agent-update-group/zscaler-deception-server-agent-agent-update-group-details-window.png)
[]
![View agent update group details window](/downloads/deception/settings/server-agents-settings/agent-update-groups/adding-server-agent-update-group/zscaler-deception-server-agent-update-group-details-window.png)