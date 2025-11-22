# Containment Configuration Guide for Zscaler Private Access (ZPA)
Source: https://help.zscaler.com/deception/containment-configuration-guide-zscaler-private-access-zpa
PDF: https://help.zscaler.com/pdf/com/en/1531425.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with Zscaler Private Access (ZPA) to contain and isolate [detected attackers](/deception/viewing-blocked-identities).
Prerequisites
Before you configure the containment integration, ensure that you have:
- Signed in to the ZPA Admin Portal and [configured an IdP for single sign-on (SSO) in ZPA](/zpa/configuring-idp-single-sign).
- Obtained the ZPA tenant ID (**Administration **> **Company**) from the ZPA Admin Portal.
Configuring Containment Integration with ZPA
Follow these steps to configure containment integration with ZPA:
- [Step 1: Configure the Containment Integration Between Deception and ZPA](#zd-zpa-containment-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#zd-zpa-contain-attack-rule-investigate)
- []In Zscaler Deception Admin Portal, go to **Orchestrate** > **Containment**.
-
In the table, locate **Zscaler Private Access** and click the **Edit **icon.
[See image.](#zpa-zd-containment-edit-option)
-
In the **Zscaler Private Access** configuration window:
- **Enabled**: Select to enable containment.
- **Customer ID**: Verify if the customer ID matches the ZPA tenant ID that you obtained from the ZPA Admin Portal.
-
**IdP**: Select all IdPs that you want to integrate.
If SCIM Sync or SCIM Attributes for Policy are disabled in the IdP, enter the SAML attribute name.
[See image.](#zpa-zd-containment-configure)
- Click **Save**.
-
After the configuration is saved, click **Test** to verify network connectivity between the Deception Admin Portal and ZPA.
- If ZIdentity is enabled for your organization, the ZIdentity IdP is displayed automatically in the **Zscaler Private Access** configuration window. This cannot be edited or deleted.
- If a user is contained with ZPA, real apps become inaccessible and only app decoys remain accessible.
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#zd-zpa-containment-rule)
- [Take action from the Investigate page.](#zd-zpa-containment-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#zpa-zd-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#zpa-zd-containment-rule-details)
-
Under **Respond**, enable **Zscaler Private Access**.
[See image.](#deception-zpa-containment-response)
-
Click **Save**.
The attacker is contained by ZPA based on the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#zpa-zd-containment-action-menu-investigate)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Zscaler** drop-down menu, and then select **Contain with Zscaler Private Access**.
[See image.](#zpa-zd-containment-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![ZPA Containment edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-edit.png)
[]![ZPA containment configuration details](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-zd-containment-configuration.png)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure general block in a rule for containment with ZPA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-containment-general.jpg)
[]![ZPA containment response configuration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-respond.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-zd-containment-action-menu.png)
[]![Contain attacker with ZPA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-take-action_0.png)