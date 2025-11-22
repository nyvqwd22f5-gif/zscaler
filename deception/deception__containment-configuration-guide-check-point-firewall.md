# Containment Configuration Guide for Check Point Firewall
Source: https://help.zscaler.com/deception/containment-configuration-guide-check-point-firewall
PDF: https://help.zscaler.com/pdf/com/en/1531421.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Check Point Firewall to contain and isolate detected attackers.
Deception integrates with Check Point Firewall using its API. You can contain and block detected attackers based on the policies configured in Check Point Firewall.
Prerequisites
Before you configure the containment integration, ensure that you have:
- Network connectivity from a Decoy Connector's management IP to the API server port on Check Point Firewall on port 443.
- Obtained credentials with web API permission to access Check Point Firewall.
- Configured policies on Check Point Firewall. To learn more, refer to the [Check Point Firewall documentation](https://sc1.checkpoint.com/documents/R80.30/WebAdminGuides/EN/CP_R80.30_SecurityManagement_AdminGuide/html_frameset.htm?topic=documents/R80.30/WebAdminGuides/EN/CP_R80.30_SecurityManagement_AdminGuide/159917).
Configuring Containment Integration with Check Point Firewall
Follow these steps to configure containment integration with Check Point Firewall:
- [Step 1: Configure the Containment Integration Between Deception and Check Point Firewall](#checkpoint-containment-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#checkpoint-containment-contain-rules-investigate)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **Check Point Firewall **and click** **the **Edit **icon.
[See image.](#check-point-firewall-containment-edit-option)
-
In the **Check Point Firewall** window:
- **Hostname/IP**: Enter the IP address or the hostname of Check Point Firewall.
- **Port**: Enter the port number used to connect to the API server.
- **Rule Name**: Enter a rule name to add the IP address to Check Point Firewall. If the rule name you enter does not exist on Check Point Firewall, a new rule with that name is automatically created.
- **Decoy Connector**: Select a Decoy Connector from the drop-down menu from which a connection is established to Check Point Firewall.
- **Username**: Enter the username of Check Point Firewall.
- **Password**: Enter the password of Check Point Firewall.
[See image.](#check-point-containment-config)
- Click **Save**.
- After the configuration is saved, click **Test** to verify network connectivity between the Zscaler Deception Admin Portal and Check Point Firewall.
- Click **Set Policy**.
-
In the **Set Policy** window:
- Enable **Set Policy**.
- Select a **Policy** from the drop-down menu.
- Select a **Layer** from the drop-down menu.
The policy and layer details are retrieved from Check Point Firewall using the APIs.
- Click **Save**.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#checkpoint-containment-firewall-create-rule)
- [Take action from the Investigate page.](#checkpoint-containment-take-actions-investigate)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#checkpoint-containment-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#check-point-config-rule)
-
Under **Respond**, enable **Check Point Firewall**.
[See image.](#deception-check-point-respond-configuration)
-
Click **Save**.
The attacker is contained by Check Point Firewall in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#check-point-containment-action-option)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Select **Contain with Check Point Firewall**.
[See image.](#check-point-contain-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![Check Point Firewall Edit Configuration option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-checkpoint-edit.png)
[]![Configure Check Point Firewall containment integration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-configure-checkpoint-containment.png?1665564344)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure a rule to contain attacker with Check Point Firewall](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-checkpoint-containment-rule-general_0.jpg)
[]![A containment response rule with Check Point Firewall configuration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-ception-rules-checkpoint-respond.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-checkpoint-containment-action-option.png)
[]![Contain attacker with Check Point Firewall](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-checkpoint-firewall-deployment-guide/zscaler-deception-checkpoint-take-action.png)