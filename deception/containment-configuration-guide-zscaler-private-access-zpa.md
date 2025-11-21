# Containment Configuration Guide for Zscaler Private Access (ZPA)
Source: https://help.zscaler.com/itdr/containment-configuration-guide-zscaler-private-access-zpa
PDF: https://help.zscaler.com/pdf/com/en/1531678.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with Zscaler Private Access (ZPA) to contain and isolate [detected attackers](/itdr/viewing-blocked-identities).
Prerequisites
Before you configure the containment integration, ensure that you have:
- Signed in to the ZPA Admin Portal and [configured an IdP for single sign-on (SSO) in ZPA](/zpa/configuring-idp-single-sign).
- Obtained the [ZPA tenant ID](/zpa/configuring-company-profile) (**Administration **> **Company**) from the ZPA Admin Portal.
Configuring Containment Integration with ZPA
Follow these steps to configure containment integration with ZPA:
- [Step 1: Configure the Containment Integration Between ITDR and ZPA](#zd-zpa-containment-configuration)
- [Step 2: Create an Orchestration Rule or Take Action to Contain Detected Attackers](#zd-zpa-contain-attack-rule-investigate)
- []In the Zscaler ITDR Admin Portal, go to **Orchestrate** > **Containment**.
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
- Under **ITDR Identity Metadata**, select **Enabled** to enable sync and fetch data from ZPA for traffic violations or bad activities.
[See image.](#zpa-zd-containment-configure)
- Click **Save**.
-
After the configuration is saved, click **Test** to verify network connectivity between the ITDR Admin Portal and ZPA.
- If ZIdentity is enabled for your organization, the ZIdentity IdP is displayed automatically in the **Zscaler Private Access** configuration window. This cannot be edited or deleted.
- If a user is contained with ZPA, real apps become inaccessible and only app decoys remain accessible.
[]You can contain detected attackers automatically by creating an orchestration rule or manually by taking action from the **Investigate** page.
- [Create an orchestration rule.](#zd-zpa-containment-rule)
- [Take action from the Investigate page.](#zd-zpa-containment-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#zpa-zd-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled **to enable the rule.
-
Create a rule using queries and conditions. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
[See image.](#zpa-zd-containment-rule-details)
-
Under **Respond**, enable **Zscaler Private Access**.
[See image.](#deception-zpa-containment-response)
- Click **Save**.
The attacker is contained by ZPA based on the conditions defined while configuring the rule.
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
[]![ZPA Containment edit option](/downloads/itdr/zscaler-itdr-and-zscaler-private-access-deployment-guide/itdr-containment-page.png)
[]![ZPA containment configuration details](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-zscaler-private-access-zpa/itdr-zpa-containment%20window-with-div_0.png)
[]![A screenshot highlighting the Add Rule button on the Rules page](/downloads/itdr/zscaler-itdr-and-zscaler-private-access-deployment-guide/itdr-rules-add-rule.png)
[]![Configure general block in a rule for containment with ZPA](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-zscaler-private-access-deployment-guide/zscaler-deception-zpa-containment-general.jpg)
[]![ZPA containment response configuration](/downloads/itdr/zscaler-itdr-and-zscaler-private-access-deployment-guide/itdr-contain-respond-zpa.png)
[]![Attacker Details pane on the Investigate page](/downloads/itdr/zscaler-itdr-and-zscaler-private-access-deployment-guide/itdr-investigate-actions.png)
[]![Contain attacker with ZPA](/downloads/itdr/zscaler-itdr-and-zscaler-private-access-deployment-guide/itdr-contain-with-zpa.png)