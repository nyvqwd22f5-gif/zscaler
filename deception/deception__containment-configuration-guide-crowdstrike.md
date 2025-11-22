# Containment Configuration Guide for CrowdStrike
Source: https://help.zscaler.com/deception/containment-configuration-guide-crowdstrike
PDF: https://help.zscaler.com/pdf/com/en/1531436.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with CrowdStrike Falcon Insight to contain and isolate endpoints when an attack is detected. In addition, you can configure Deception to share intelligence along with suggested actions that CrowdStrike should perform for events with indicators of compromise (IOC) and indicators of attack (IOA). You can also configure Deception to share IPs or process hashes as indicators of compromise and process trees as indicators of attack.
To learn more about how to integrate Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) with CrowdStrike, see the [Zscaler and CrowdStrike Deployment Guide](/zscaler-technology-partners/zscaler-and-crowdstrike-deployment-guide).
Prerequisites
Ensure there is network connectivity from the Zscaler Deception Admin Portal to CrowdStrike Falcon Insight on HTTPS port 443.
Configuring Containment Integration with CrowdStrike Falcon Insight
Follow these steps to configure containment integration with CrowdStrike Falcon Insight:
- [Step 1: Create a Client and Secret Key in CrowdStrike Falcon Insight](#deception-containment-crowdstrike-client-secret-key)
- [Step 2: Configure the Containment Integration Between Deception and CrowdStrike Falcon Insight](#deception-containment-crowdstrike-config-integration)
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
- For **Custom IOA Rules**, select **Read **and **Write.**
-
For **IOCs (Indicators of Compromise)**, select **Read **and **Write**.
[See image.](#crowdstrike-add-api-client)
-
Click **Add**.
The **API client created** window appears.
[See image.](#crowdstrike-copy-client-id-secrey-key)
- Copy the client ID and secret key.
- Click **Done**.
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **CrowdStrike **and click the **Edit **icon.
[See image.](#crowdstrike-edit-containment)
- In the **CrowdStrike Falcon Insight **configuration window:
- **Enabled**: Select to enable the containment.
- **URL**: Enter the CrowdStrike API endpoint URL. For example, enter `https://api.crowdstrike.com`.
- **Client ID**: Enter the client ID that you copied in [Step 1](#deception-containment-crowdstrike-client-secret-key).
- **Client Secret**: Enter the client secret that you copied in [Step 1](#deception-containment-crowdstrike-client-secret-key).
- **Marking IOA Safe Processes: **(Optional) To avoid sharing legitimate process trees with CrowdStrike for IOA actions, follow these steps to designate legitimate processes as safe processes:
- Click** IOA Safe Processes**.
- In the **Safe Processes **window, click** Add Safe Process.**
-
In the **Create Safe Process** window, provide the following details:
- **Name**: Enter a name for the safe process.
- **Process Path**: Enter the path of the executable file from which the process originates.
[See image.](#deception-IOA-safe-process)
-
Click **Create Safe Process**.
Processes are marked as safe only if all elements of the process tree have an entry in the safe processes list.
- Click **Save**.
-
Click **Test** to verify the reachability of the CrowdStrike Falcon Insight platform.
[See image.](#crowdstrike-containment-configure)
[]You can contain detected attackers automatically by creating an orchestrated rule or manually by taking action from the Investigate page.
- [Create a rule.](#crowdstrike-containment-create-a-rule)
- [Take action from the Investigate page.](#crowdstrike-containment-take-actions-investigate)
- []Go to **Orchestrate** > **Rule**.
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
When the same IP address is encountered for more than one CrowdStrike-managed device, none of these devices are isolated and the event is recorded as a containment failure in the logs as a system message. To learn more about system messages, see [Viewing and Managing System Messages](/deception/viewing-and-managing-system-messages).
- **IOC Hash**: Enable to share file hashes that are considered indicators of compromise with CrowdStrike and select an appropriate **IOC Hash Action **and **IOC Hash Severity**.
- **IOC Hash Action**: Choose the action that CrowdStrike should perform when IOC hashes are shared:
- **Detect Only**: Show the indicator as a detection and take no other action.
- **Block**: Add the indicator to the denylist and show it as a detection.
- **Block, Hide Detection**: Add the indicator to the denylist and do not detect it.
- **Allow**: Add the indicator to the allowlist and do not detect it.
- **No Action**: Save the indicator for future use and take no action.
- **IOC Hash Severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike for IOC hashes. The available levels are **Informational**,** Low**, **Medium**,** High**,** **and **Critical**.
- **IOC IP: **Enable to share IPs that are considered indicators of compromise with CrowdStrike and select an appropriate **IOC IP Action **and **IOC IP Severity**.
- **IOC IP Action**: Choose the action that CrowdStrike should perform when IPs are shared:
- **Detect Only**: Show the indicator as a detection and take no other action.
- **No Action**: Save the indicator for future use and take no action.
- **IOC IP Severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike for IOC IPs. The available levels are **Informational**,** Low**, **Medium**,** High**,** **and **Critical**.
- **IOA Process Tree**: Enable to share process trees that are considered indicators of attack with CrowdStrike and select an appropriate **IOA Action **and **IOA Severity**.
- **IOA Action**: Choose the action that CrowdStrike should perform when IOA process trees are shared:
- **Detect**: Show the indicator as a detection and take no other action.
- **Monitor**: Use the indicator for informational use only and take no action nor show it as a detection.
-
**Block Execution**: Kill the process and show the indicator as detection.
Exercise caution when choosing the Block Execution action as CrowdStrike kills all processes that match with the process tree across all endpoints in your network. To avoid killing legitimate processes, make sure that you have configured IOA safe processes as described in [Step 2](#deception-containment-crowdstrike-config-integration).
-
**IOA severity**: Designate an appropriate severity level for indicators that should be shared with CrowdStrike for IOC hashes and IPs. The available levels are **Informational**,** Low**,** Medium**,** High**,** **and **Critical**.
[See image.](#deception-crowdstrike-response)
- Click **Save**.
- []On the **Investigate** page, click an attack icon on the alert graph.
-
The attacker details pane opens.
[See image.](#crowdstrike-action-option-attacker-details)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **CrowdStrike Falcon** drop-down menu, and select **Contain with CrowdStrike Falcon Insight **or **Create IoC IP Indicator in CrowdStrike**.
[See image.](#crowdstrike-contain-attacker-take-action)
-
In the confirmation window, click **OK**.
When the same IP address is encountered for more than one CrowdStrike-managed device, the containment action with Falcon Insight fails and an error is displayed.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-details).
[]![Select API Scopes in CrowdStrike](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-cs-api.png?1677502280)
[]![Copy the client ID and secret key from CrowdStrike Falcon Insight](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-containment-crowdstrike-copy-api-client.png?1667533820)
[]![CrowdStrike containment integration Edit icon](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-edit_0.png)
[]![Creating an IOA Safe Process](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-IOA-safe-process.jpg)
[]![Configure CrowdStrike Falcon Insight containment integration](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-configuration.jpg)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure a rule to contain attackers with CrowdStrike](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-rule-general_1.jpg)
[]![Configure response rule for CrowdStrike ](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-config.jpg)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-containment-investigate-action.png?1665575345)
[]![Contain attacker with CrowdStrike](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-crowdstrike-deployment-guide/zscaler-deception-crowdstrike-actions.png)