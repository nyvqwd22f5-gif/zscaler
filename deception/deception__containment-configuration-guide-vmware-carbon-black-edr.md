# Containment Configuration Guide for VMware Carbon Black EDR
Source: https://help.zscaler.com/deception/containment-configuration-guide-vmware-carbon-black-edr
PDF: https://help.zscaler.com/pdf/com/en/1531424.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with VMware Carbon Black EDR to contain and isolate detected attackers.
Deception integrates with VMware Carbon Black EDR using its API. You can contain and block detected attackers based on the policies configured in the solution.
Prerequisites
Before you configure the containment integration, ensure that you have:
- Network connectivity from a Decoy Connector's management IP to VMware Carbon Black EDR on port 443.
- Obtained the API token. To learn more, refer to the [Carbon Black EDR documentation](https://docs.vmware.com/en/VMware-Carbon-Black-EDR/7.6/cb-edr-unified-view-user-guide/GUID-44ADED4B-36CE-40DE-9DB6-D900A10CA689.html).
- Created policies to isolate hosts from the network. To learn more, refer to the [Carbon Black EDR documentation](https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/carbon-black-cloud-user-guide/GUID-814C8950-5560-49D6-8E74-466ECE460D4F.html).
Configuring Containment Integeration with VMware Carbon Black EDR
Follow these steps to configure containment integration with VMware Carbon Black EDR:
- [Step 1: Configure the Containment Integration Between Deception and Carbon Black EDR](#vmware-cb-edr-containment-config)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#vmware-cb-edr-containment-rule-action)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **VMware Carbon Black EDR **and click the **Edit** icon.
[See image.](#vmware-cb-ed-edit-option)
-
In the **VMware Carbon Black EDR** configuration window:
- **Enable**: Select to enable containment.
- **URL**: Enter the URL to access the VMware Carbon Black EDR console.
- **API Key**: Enter the API token.
- **Decoy Connector**: Select a Decoy Connector from the drop-down menu from which a connection is established to VMware Carbon Black EDR.
[See image.](#vmware-cb-edr-edit-containment-details)
- Click **Save**.
- After the configuration is saved, click **Test** to verify network connectivity between the Zscaler Deception Admin Portal and VMware Carbon Black EDR.
[]You can contain detected attackers automatically by creating an orchestration rule or manually by taking action from the Investigate page.
- [Create a rule.](#vmware-cb-edr-containment-create-rule)
- [Take action from the Investigate page.](#vmware-cb-edr-containment-investigate)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#vmware-cb-edr-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#vmware-cb-edr-add-rule-details)
-
Under **Respond**, enable **VMware Carbon Black EDR**.
[See image.](#deception-vmware-edr-respond-block)
- Click **Save**.
The attacker is contained by VMware Carbon Black EDR in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#vmware-cb-edr-containment-action-option)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Carbon Black** drop-down menu, and select **Contain with VMware Carbon Black EDR**.
[See image.](#vmware-cb-edr-containment-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![VMware Carbon Black EDR Containment Edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-vmcarbon-edr-edit.png)
[]![Configure VMware Carbon Black EDR Containment details](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-carbon-black-edr-containment-config-details.png)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-add-rule.jpg)
[]![General block in a rule to contain attacker with VMware Carbon Black EDR](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-vmware-carbon-rule-general-block.jpg)
[]![Configure respond block in a rule to contain an attacker with VMWare EDR](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-vmcarbon-edr-respond.png)
[]![Attacker Details pane on the Investigate page](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-cb-edr-containment-action-option.png)
[]![Contain attacker with Carbon Black EDR](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-edr-deployment-guide/zscaler-deception-vmware-edr-action.png)