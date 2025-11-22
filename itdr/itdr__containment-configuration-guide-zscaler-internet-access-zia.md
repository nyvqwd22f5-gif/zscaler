# Containment Configuration Guide for Zscaler Internet Access (ZIA)
Source: https://help.zscaler.com/itdr/containment-configuration-guide-zscaler-internet-access-zia
PDF: https://help.zscaler.com/pdf/com/en/1531679.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with Zscaler Internet Access (ZIA). With this integration, you can contain and isolate Zscaler Client Connector attackers within your organization. When ITDR threat detection is triggered, the activity is logged as an attack and the user information is shared with ZIA. Based on the user information, ZIA blocks internet access to those users across devices by moving them to a restricted group.
Prerequisites
Before you configure the containment integration, ensure that you have:
- Signed in to the ZIA Admin Portal, [configured an IdP](/zia/adding-identity-providers), and [enabled SCIM provisioning](/zia/configuring-scim).
- Obtained the Base URL and Bearer Token of the configured IdP (**Administration **> **Authentication Settings **> **Identity Providers**) from the ZIA Admin Portal.
- Created a [user group](/zia/adding-groups) and configured a [firewall filtering policy for the group](/zia/configuring-firewall-filtering-policy) with Block/Drop as action.
- Installed Zscaler Client Connector version 4.1 or later across all endpoints.
Configuring Containment Integration with ZIA
Follow these steps to configure the containment integration with ZIA:
- [Step 1: Configure the Containment Integration Between ITDR and ZIA](#zd-zia-containment-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#zd-zia-contain-attack-rule-investigate)
- []In the Zscaler ITDR Admin Portal, go to **Orchestrate** > **Containment**.
-
In the table, locate **Zscaler Internet Access** and click the **Edit **icon.
[See image.](#zia-zd-containment-edit-option)
- In the **Zscaler Internet Access** configuration window:
- **Enabled**: Select to enable containment.
- **SCIM Base URL**: Enter the Base URL copied from the ZIA Admin Portal.
- **SCIM Bearer Token**: Enter the Bearer Token copied from the ZIA Admin Portal.
- **Keep existing value**: Select to keep the existing bearer token from the ZIA Admin Portal.
- **SCIM User Group**:** **Enter the name of the user group that was created in ZIA with the policy to block network traffic.
-
Under **ITDR Identity Metadata:**
- **Enabled: **Select to enable sync with ZIA to fetch the data for traffic violations or bad activities from ZIA.
- **Base URL: **Enter the Base URL used for ZIA Admin Portal.
- **Username: **Enter your username used for signing in to the ZIA Admin Portal.
- **Password: **Enter your password used for signing in to the ZIA Admin Portal.
-
**Keep existing value**: Select to keep the existing password or deselect to use a new password.
By default, the **Keep existing value** checkbox is selected if you don't enter any new password. When you enter a new password, the check box is disabled.
[See image.](#zia-zd-containment-configure)
-
Click **Save**.
A confirmation message appears indicating that the settings are saved.
[]You can create an orchestration rule to automatically contain the detected attackers, or you can manually take action from the Investigate page.
- [Create an orchestration rule.](#zd-zia-containment-rule)
- [Take action from the Investigate page.](#zd-zia-containment-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#zia-zd-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled **to enable the rule.
-
Create a rule using queries and conditions. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
[See image.](#zia-zd-containment-rule-details)
-
Under **Respond**, enable **Zscaler Internet Access**.
[See image.](#deception-zia-containment-response)
- Click **Save**.
The attacker is contained by ZIA based on the conditions defined while configuring the orchestration rule.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
[See image.](#zia-zd-containment-action-menu-investigate)
-
Click the **Zscaler **drop-down menu** **and select **Contain with Zscaler Internet Access**.
[See image.](#zia-zd-containment-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![ZIA Containment edit option](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-containment-page.png)
[]![ZIA containment configuration details](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-identity-metadat.png)
[]![Add Rule option](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-rules-add-rule.png)
[]![Configure general block in a rule for containment with ZIA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-internet-access-deployment-guide/zscaler-deception-rule-general.png)
[]![ZIA containment response configuration](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-respond-zia.png)
[]![Attacker Details pane on the Investigate page](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-investigate-actions.png)
[]![Contain attacker with ZIA](/downloads/itdr/zscaler-itdr-and-zscaler-internet-access-deployment-guide/itdr-contain-with-zia.png)