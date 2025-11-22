# Containment Configuration Guide for Zscaler Internet Access (ZIA)
Source: https://help.zscaler.com/deception/containment-configuration-guide-zscaler-internet-access-zia
PDF: https://help.zscaler.com/pdf/com/en/1531476.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Zscaler Internet Access (ZIA).
With this integration, you can contain and isolate Zscaler Client Connector users within your organization who interact with landmine decoys deployed in the assets managed by your organization. When Zscaler Client Connector users interact with the landmine decoys, the activity is logged as an attack and the user information is shared with ZIA. Based on the user information, ZIA blocks internet access to those users across devices by moving them to a restricted group.
Prerequisites
Before you configure the containment integration, ensure that you have:
- Signed in to the ZIA Admin Portal, [configured an IdP](/zia/adding-identity-providers), and [enabled SCIM provisioning](/zia/configuring-scim).
- Obtained the Base URL and Bearer Token of the configured IdP (**Administration **> **Authentication Settings **> **Identity Providers**) from the ZIA Admin Portal.
- Created a [user group](/zia/adding-groups) and configured a [firewall filtering policy for the group](/zia/configuring-firewall-filtering-policy) with Block/Drop as action.
- Installed Zscaler Client Connector version 4.1 or later across all endpoints.
Configuring Containment Integration with ZIA
Follow these steps to configure containment integration with ZIA:
- [Step 1: Configure the Containment Integration Between Deception and ZIA](#zd-zia-containment-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#zd-zia-contain-attack-rule-investigate)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **Zscaler Internet Access** and click the **Edit **icon.
[See image.](#zia-zd-containment-edit-option)
-
In the **Zscaler Internet Access** configuration window:
- **Enabled**: Select to enable containment.
- **SCIM Base URL**: Enter the Base URL copied from the ZIA Admin Portal.
- **SCIM Bearer Token**: Enter the Bearer Token copied from the ZIA Admin Portal.
- **SCIM User Group**:** **Enter the name of the user group that was created in ZIA with the policy to block network traffic.
[See image.](#zia-zd-containment-configure)
- Click **Save**.
- After the configuration is saved, click **Test** to verify network connectivity between the Zscaler Deception Admin Portal and ZIA.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#zd-zia-containment-rule)
- [Take action from the Investigate page.](#zd-zia-containment-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#zia-zd-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#zia-zd-containment-rule-details)
-
Under **Respond**, enable **Zscaler Internet Access**.
[See image.](#deception-zia-containment-response)
-
Click **Save**.
The attacker is contained by ZIA in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#zia-zd-containment-action-menu-investigate)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Zscaler **drop-down menu,** **and then select **Contain with Zscaler Internet Access**.
[See image.](#zia-zd-containment-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![ZIA Containment edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-zia-edit.png)
[]![ZIA containment configuration details](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-ZIA-contianment-configuration.png)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure general block in a rule for containment with ZIA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-rule-general.png)
[]![ZIA containment response configuration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-zia-respond.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-zpa-zd-containment-action-menu.png)
[]![Contain attacker with ZIA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-zia-take-action_2.png)