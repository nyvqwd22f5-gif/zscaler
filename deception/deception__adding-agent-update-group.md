# Adding an Agent Update Group
Source: https://help.zscaler.com/deception/adding-agent-update-group
PDF: https://help.zscaler.com/pdf/com/en/1531322.pdf

You can add an agent update group with a selection criterion based on hostnames to selectively roll out the updates for landmine agents.
To add an agent update group:
- Go to **Settings **> **Endpoint Settings **> **Agent Update Groups**.
-
Click **Add Group**.
[See image.](#add-agent-update-group)
- In the **Agent Update Group Details** window:
- Enter a name for the agent update group.
- Select **Enable Updates** to enable phased updates for the agent update group.
- Select a criterion from the drop-down menu:
-
**Hostname List**: Applies updates to all the agents where the hostname of the system exactly matches the hostnames specified in the **Hostname List** text box.
[See image.](#agent-update-group-hostname)
-
**Hostname RegEx**: Applies updates to all the agents where the hostname of the system matches the hostname pattern specified as a regular expression in the **Hostname RegEx **text box.
[See image.](#agent-update-group-regex)
Zscaler recommends that you add a group named "All systems" with a catch-all regular expression ( .* ), and enable this group after you complete the testing to make sure all endpoints are upgraded.
-
Click **Save**.
The agent update group is created and appears in the **Agent Update Groups** table.
[]![A screenshot capturing the Agent Update Groups page with the Add Group option highligted](/downloads/deception/deceive/landmine-decoys/phased-updates-agent-groups/adding-landmine-agent-group/zscaler-deception-enabled-phased-updates-add-group.jpg)
[]
![A screenshot capturing the Agent Update Group Details Window](/downloads/deception/settings/endpoint-settings/agent-update-groups/adding-agent-update-group/zscaler-deception-agent-update-groups-hostname.jpg)
[]
![A screenshot capturing the Agent Update Groups window](/downloads/deception/settings/endpoint-settings/agent-update-groups/adding-agent-update-group/zscaler-deception-agent-update-groups-regex.jpg)