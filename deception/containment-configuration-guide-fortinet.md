# Containment Configuration Guide for Fortinet
Source: https://help.zscaler.com/deception/containment-configuration-guide-fortinet
PDF: https://help.zscaler.com/pdf/com/en/1531411.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Fortinet to contain and isolate detected attackers.
To learn more about how to integrate Zscaler Internet Access (ZIA)) and Zscaler Private Access (ZPA), see the [Zscaler and Fortinet Deployment Guide](/zscaler-technology-partners/zscaler-and-fortinet-deployment-guide).
Prerequisites
Ensure there is network connectivity from Fortinet to the Zscaler Deception Admin Portal on HTTP port 80.
Configuring Containment Integration with Fortinet
Follow these steps to configure the containment integration with Fortinet:
- [Step 1: Configure the Containment Integration Between Deception and Fortinet](#containment-integration-fortinet-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#contain-fortinet-rule-or-investigate)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **Fortinet (Threat Feeds - Attacker IPs)** or **Fortinet (Threat Feeds - Attacker Domains)** and click the **Edit **icon.
[See image.](#fortinet-containment-edit)
- In the Fortinet containment configuration window:
- **Enabled**: Select to enable containment.
-
**Default expiration (in hours)**: Enter the expiration time in hours. The IP addresses or hostnames are retained in the containment list for the specified number of hours.
You can select the **Infinite Expiration** checkbox if you want the IP addresses or hostnames to be retained in the containment list forever unless you manually [delete them from the list](/deception/viewing-contained-attacker-ip-address-details).
[See image.](#config-fortinet-containment-details)
-
Click **Save**.
After the configuration is saved, Deception generates a URL.
- On the **Containment **page, locate the Fortinet solution that you configured and click the **Edit** icon again.
-
In the Fortinet containment configuration window, copy the **URL**.
[See image.](#fortinet-containment-url)
- [Configure an external threat feed on Fortinet](https://docs.fortinet.com/document/fortigate/6.2.0/cookbook/9463/threat-feeds) and point the feed to the URL copied in the previous step to complete the containment integration.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#contain-fortinet-create-rule)
- [Take action from the Investigate page.](#containment-integration-fortinet-contain-investigate)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#containment-fortinet-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#containment-fortinet-create-a-rule-automation)
- Under **Respond **>** Fortinet**:
- Select **Enabled**.
-
Select **Fortinet (Threat Feeds - Attacker IPs)** or **Fortinet (Threat Feeds - Attacker Domains)** from the **Name** drop-down menu.
[See image.](#deception-fortinet-response)
-
Click **Save**.
The attacker is contained by Fortinet in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#fortinet-attacker-details-action)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Fortinet** drop-down menu, and select **Contain with Fortinet (Threat Feeds - Attacker IPs)** or **Contain with** **Fortinet (Threat Feeds - Attacker Domains)** depending on the integration.
[See image.](#fortinet-contain-investigate)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![Fortinet containment integration edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-edit.png)
[]![Configure Fortinet containment integration details](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-default.jpg)
[]![Copy Fortinet Containment URL](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-URL.jpg)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure general block in a rule to contain attackers with Fortinet](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-containment-general.jpg)
[]![Fortinet containment response configuration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-enable-rule-fortinet.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-containment-investigate-action.png?1665573337)
[]![Contain attacker with Fortinet](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-fortinet-deployment-guide/zscaler-deception-fortinet-actions.png)