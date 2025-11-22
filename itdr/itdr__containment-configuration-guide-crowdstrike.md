# Containment Configuration Guide for CrowdStrike
Source: https://help.zscaler.com/itdr/containment-configuration-guide-crowdstrike
PDF: https://help.zscaler.com/pdf/com/en/1531808.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler ITDR with CrowdStrike Falcon Insight to contain and isolate endpoints when an attack is detected. In addition, you can configure ITDR to share intelligence along with suggested actions that CrowdStrike should perform for events with indicators of compromise (IOC).
To learn more about how to integrate Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) with CrowdStrike, see the [Zscaler and CrowdStrike Deployment Guide](/zscaler-technology-partners/zscaler-and-crowdstrike-deployment-guide).
Prerequisites
Ensure there is network connectivity from the Zscaler ITDR Admin Portal to CrowdStrike Falcon Insight on HTTPS port 443.
Configuring Containment Integration with CrowdStrike Falcon Insight
Follow these steps to configure containment integration with CrowdStrike Falcon Insight:
- [Step 1: Create a Client and Secret Key in CrowdStrike Falcon Insight](#deception-containment-crowdstrike-client-secret-key)
- [Step 2: Configure the Containment Integration Between ITDR and CrowdStrike Falcon Insight](#deception-containment-crowdstrike-config-integration)
- [Step 3: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#crowdstrike-containment-contain-attacker)
- []Log in to the CrowdStrike Falcon Insight platform.
- Go to **Support** > **API Clients and Keys**.
- Click **Add new API** client.
- In the **Add new API client** window:
- Enter the **Client Name** of the new API.
- Enter the **Description**.
- Under **API Scopes**:
- For **Detections**,** **select **Read**.
- For **Hosts**, select** Read **and** Write**.
-
For **IOCs (Indicators of Compromise)**, select **Read **and **Write**.
[See image.](#crowdstrike-add-api-client)
-
Click **Add**.
The **API client created** window appears.
[See image.](#crowdstrike-copy-client-id-secrey-key)
- Copy the client ID and secret key.
- Click **Done**.
- []In the ITDR Admin Portal, go to **Orchestrate** > **Containment**.
-
In the table, locate **CrowdStrike **and click the **Edit **icon.
[See image.](#crowdstrike-edit-containment)
- In the **CrowdStrike Falcon Insight **configuration window:
- **Enabled**: Select to enable the containment.
- **URL**: Enter the CrowdStrike API endpoint URL. For example, enter `https://api.crowdstrike.com`.
- **Client ID**: Enter the client ID that you copied in the [previous step](#deception-containment-crowdstrike-client-secret-key).
- **Client Secret**: Enter the client secret that you copied in the [previous step](#deception-containment-crowdstrike-client-secret-key).
- Click **Save**.
-
Click **Test** to verify the reachability of the CrowdStrike Falcon Insight platform.
[See image.](#crowdstrike-containment-configure)
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#crowdstrike-containment-create-a-rule)
- [Take action from the Investigate page.](#crowdstrike-containment-take-actions-investigate)
- []In the ITDR Admin Portal, go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#crowdstrike-add-rule)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#crowdstrike-config-rule)
- Under **Respond**, locate the **CrowdStrike **section, and configure the following options:
-
**Falcon Insight**: Enable to contain an endpoint using CrowdStrike when an event matching the configured rule occurs.
When the same IP address is encountered for more than one CrowdStrike-managed device, none of these devices are isolated and the event is recorded as a containment failure in the logs as a system message. To learn more about system messages, see [Viewing and Managing System Messages](/itdr/viewing-and-managing-system-messages).
-
**IOC Hash**: Enable to share file hashes that are considered indicators of compromise with CrowdStrike, and select an appropriate **IOC Hash Action **and **IOC Hash Severity**.
[See image.](#deception-crowdstrike-response)
- Click **Save**.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
- Click the **CrowdStrike Falcon** drop-down menu, and select **Contain with CrowdStrike Falcon Insight**.
-
In the confirmation window, click **OK**.
When the same IP address is encountered for more than one CrowdStrike-managed device, the containment action with Falcon Insight fails and an error is displayed.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-details).
[]![Selecting API Scopes in CrowdStrike](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-crowdstrike/zscaler-itdr-cs-api_0.png)
[]![Copy the client ID and secret key from CrowdStrike Falcon Insight](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-containment-crowdstrike-copy-api-client.png?1667533820)
[]![CrowdStrike containment integration Edit icon](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-crowdstrike/zscaler-itdr-crowstrike-option.png)
[]![Configure CrowdStrike Falcon Insight containment integration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-configuration.jpg)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure a rule to contain attackers with CrowdStrike](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-rule-general_1.jpg)
[]![Configure response rule for CrowdStrike ](/downloads/itdr/orchestrate/containment-integrations/containment-configuration-guide-crowdstrike/itdr-crowstrike-rule.png)