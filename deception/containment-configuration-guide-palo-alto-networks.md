# Containment Configuration Guide for Palo Alto Networks
Source: https://help.zscaler.com/deception/containment-configuration-guide-palo-alto-networks
PDF: https://help.zscaler.com/pdf/com/en/1531422.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Palo Alto Networks to contain and isolate detected attackers.
Prerequisites
Ensure there is network connectivity from the Palo Alto Networks platform to the Zscaler Deception Admin Portal on HTTPS on port 443.
Configuring Containment Integration with Palo Alto Networks
Follow these steps to configure containment integration with Palo Alto Networks:
- [Step 1: Configure the Containment Integration Between Deception and Palo Alto Networks](#palo-alto-nw-containment-integration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#palo-alto-nw-contain-rule-investigate)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **Palo Alto Networks (External Dynamic List - Attacker IPs)** or **Palo Alto Networks (External Dynamic List - Attacker Hostnames)** and** **click the **Edit **icon.
[See image.](#palo-alto-network-edit-option)
-
In the **Palo Alto Networks** configuration window:
- **Enabled**: Select to enable containment.
-
**Default expiration (in hours)**: Enter the expiration time in hours. The IP addresses or hostnames are retained in the containment list for the specified number of hours.
You can select the **Infinite Expiration** checkbox if you want the IP addresses or hostnames to be retained in the containment list forever unless you manually [delete them from the list](/deception/viewing-contained-attacker-ip-address-details).
[See image.](#palo-alto-network-containment-config)
-
Click **Save**.
After the configuration is saved, Deception generates a URL.
- On the **Containment **page, locate the Palo Alto Networks solution that you configured and click the **Edit** icon again.
-
In the **Palo Alto Networks** configuration window, copy the **URL**.
[See image.](#palo-alto-networks-containment-copy-url)
- [Configure an external threat feed in Palo Alto Networks](https://docs.paloaltonetworks.com/pan-os/10-2/pan-os-web-interface-help/objects/objects-external-dynamic-lists) and point the feed to the URL copied in the previous step to complete the containment integration. When configuring the threat feed in Palo Alto Networks, select **IP List** if you are using the attacker IPs or **Domain List** if you are using the attacker hostname version of the integration.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#palo-alto-nw-create-rule)
- [Take action from the Investigate page.](#palo-alto-nw-containment-investigate-take-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#palo-alto-containment-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions to automate the containment of attackers.
[See image.](#palo-alto-network-containment-config-rule)
-
Under **Respond **>** Palo Alto Networks - NGFW**:
- Select **Enabled**.
- Select **Palo Alto Networks NGFW External Dynamic List - Attacker IPs** or **Palo Alto Networks NGFW External Dynamic List - Attacker Hostnames **from the **Name** drop-down menu.
[See image.](#deception-palo-alto-response)
-
Click **Save**.
The attacker is contained by Palo Alto Networks in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#palo-alto-network-action-menu-option-investigate)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Palo Alto Networks** drop-down menu, and select **Contain with** **Palo Alto Networks - NGFW (IP) **or **Contain with** **Palo Alto Networks - NGFW (Hostname)** depending on the integration.
[See image.](#palo-alto-networks-attacker-containment)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![Palo Alto Networks Containment Edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-edit.png)
[]![Configure Palo Alto Networks Containment integration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-default.jpg)
[]![Copy Palo Alto Networks Containment URL](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-URL.jpg)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure general block in a rule to contain attacker with Palo Alto Networks](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-rule-general_0.jpg)
[]![Palo Alto Networks Containment Response Configuration ](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-enable-rule-palo-alto.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-nw-containment-action-menu-investigate.png?1665571501)
[]![Contain attacker with Palo Alto Networks ](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-palo-alto-networks-deployment-guide/zscaler-deception-palo-alto-action.png)