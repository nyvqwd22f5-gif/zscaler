# Creating Blocklists
Source: https://help.zscaler.com/deception/creating-blocklist
PDF: https://help.zscaler.com/pdf/com/en/1531343.pdf

The Blocklist feature allows you to create a firewall rule that prevents ranges of or individual IP addresses from accessing one or more decoy IP addresses. Traffic from blocklisted IP addresses to the specified destination decoys and ports are dropped and not processed or stored in Zscaler Deception. For the blocklisted systems, it appears as if nothing is running at the destination port.
You can create a blocklist where the blocklist rule is applied to all decoy IP addresses on a selected Decoy Connector. You can also create blocklists in bulk where the blocklist rule is applied to all decoy IP addresses on multiple Decoy Connectors.
Creating a Blocklist
To create a blocklist:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Settings** > **Blocklist**.
-
Click **Actions** and select **Add Blocklist**.
[See image.](#zd-add-blocklist-option)
-
In the **Blocklist Details** window:
- **Comment**: Enter a relevant comment.
- **Source IPs**: Enter a list of source IP addresses or CIDR blocks to prevent accessing the decoys.
-
**Destination IP**: Enter a destination IP (decoy IP) address.
If the **Destination IP** field is blank, the blocklist rule is applied to all decoy IP addresses on the selected Decoy Connector.
If you are applying the blocklist rule to a Threat Intelligence (TI) decoy, enter `10.10.10.10` as the destination IP address.
- **Destination Ports**: Enter a single or multiple port numbers. You can separate the numbers with a comma.
- **Decoy Connector**: Select a Decoy Connector from the drop-down menu.
[See image.](#zd-blocklist--details)
-
Click **Save**.
The configured blocklist is added to the **Blocklist** table.
[See image.](#zd-blocklist-added)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys) for the configured blocklist to take effect.
Creating Blocklists in Bulk
To create blocklists across multiple Decoy Connectors:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Settings** > **Blocklist**.
-
Click **Actions** and select **Bulk Create Blocklist**.
[See image.](#zd-add-bulk-blocklist-option)
-
In the **Bulk Create Blocklist** window:
- **Comment**: Enter a relevant comment.
- **Source IPs**: Enter a list of source IP addresses or CIDR blocks to prevent accessing the decoys.
-
**Destination IP**: Enter a destination IP (decoy IP) address.
If the **Destination IP** field is blank, the blocklist rule is applied to all decoy IP addresses on the selected Decoy Connector.
If you are applying the blocklist rule to a TI decoy, enter `10.10.10.10` as the destination IP address.
- **Destination Ports**: Enter a single or multiple port numbers. You can separate the numbers with a comma.
- **Decoy Connector**: Select more than one Decoy Connector from the drop-down menu. The IP addresses are blocked across the selected Decoy Connectors.
[See image.](#zd-add-blocklist-bulk)
-
Click **Save**.
Blocklists for each Decoy Connector are added to the **Blocklist** table.
[See image.](#zd-blocklist-bulk-added)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys) for the configured blocklists to take effect.
[]![View the Add a Blocklist option](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-add-blocklist.png)
[]![Configure blocklist details](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-blocklist-details.png)
[]![Blocklist added for specific Decoy Connectors](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-blocklist-saved.png)
[]![Add a blocklist in bulk option](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-add-blocklist-bulk.png)
[]![Configure a blocklist in bulk](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-bulk-blocklist-details.png)
[]![Blocklists saved](/downloads/deception/deceive/deception-settings/creating-blocklist/zscaler-deception-action-blocklist-bulk-saved.png)