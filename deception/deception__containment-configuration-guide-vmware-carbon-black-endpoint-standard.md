# Containment Configuration Guide for VMware Carbon Black Endpoint Standard
Source: https://help.zscaler.com/deception/containment-configuration-guide-vmware-carbon-black-endpoint-standard
PDF: https://help.zscaler.com/pdf/com/en/1531423.pdf

This configuration guide provides information on prerequisites and how to integrate Zscaler Deception with VMware Carbon Black Endpoint Standard to contain and isolate detected attackers.
Deception integrates with VMware Carbon Black Endpoint Standard using its API.
Prerequisites
Before you configure the containment integration, ensure that:
- You have network connectivity from a Decoy Connector's management IP address to the VMware Carbon Black Endpoint Standard API.
- In the VMware Carbon Black Endpoint Standard console, you have:
- Obtained the Org key. To learn more about the Org key, refer to the [Carbon Black Cloud documentation](https://developer.carbonblack.com/reference/carbon-black-cloud/authentication/#construct-your-request).
- Created a Device API key with device-related permissions. To learn more about the Device API key, refer to the [Carbon Black Cloud documentation](https://developer.carbonblack.com/reference/carbon-black-cloud/platform/latest/devices-api/#authentication).
- If you are containing attackers using policies configured on VMware Carbon Black Endpoint Standard, you have:
- Created a policy API key with read permissions. To learn more about the Policy API key, refer to the [Carbon Black Cloud documentation](https://developer.carbonblack.com/reference/carbon-black-cloud/authentication/).
- Created a policy to isolate a device from the network, while retaining access to perform live response on the endpoint and collect further endpoint telemetry.
- Created a policy to restore the device network connectivity on the endpoint. To learn more about policies, refer to the [Carbon Black Cloud documentation](https://docs.vmware.com/en/VMware-Carbon-Black-Cloud/services/carbon-black-cloud-user-guide/GUID-814C8950-5560-49D6-8E74-466ECE460D4F.html).
Configuring Containment Integration with VMware Carbon Black Endpoint Standard
Follow these steps to configure containment integration with VMware Carbon Black Endpoint Standard:
- [Step 1: Configure the Containment Integration Between Deception and VMware Carbon Black Endpoint Standard](#carbon-black-defense-containment-configuration)
- [Step 2: Configure Orchestration Rule or Take Action to Contain Detected Attackers](#carbon-black-defense-containment-rule-action)
- []Go to **Orchestrate** > **Containment**.
-
In the table, locate **VMware Carbon Black Endpoint Standard **and click the **Edit** icon.
[See image.](#vmware-cb-ed-edit-option)
- In the **VMware Carbon Black Endpoint Standard** configuration window:
- **Enabled**: Select to enable containment.
- **URL**: Enter the URL to access VMware Carbon Black Endpoint Standard.
- **Org Key**: Enter the Org key.
- **Device API Key**: Enter the Device API key.
- **Decoy Connector**: Select a Decoy Connector from the drop-down menu from which a connection is established to VMware Carbon Black Endpoint Standard.
- **Action Type**: Select an option from the drop-down menu:
-
**Apply Policy**: Contain and block detected attackers based on the policies configured in VMware Carbon Black Endpoint Standard. Under **Policy**:
- **Policy API Key**: Enter the Policy API key.
- **Isolate Policy**: Enter the name of the policy you created to isolate a device from the network.
- **Unisolate Policy**: Enter the name of the policy you created to restore the device network connectivity.
[See image.](#vmware-cb-ed-containment-config)
-
**Quarantine**: Quarantine the device to block network connectivity with other devices in the organization. To learn more about what happens when a device is placed in quarantine, refer to the [Carbon Black Cloud documentation](https://community.carbonblack.com/t5/Knowledge-Base/Endpoint-Standard-What-happens-when-a-Device-is-placed-in/ta-p/71741).
The **Quarantine** option is not supported on Linux, so you cannot isolate attackers on this platform.
[See image.](#deception-containment-cb-ep-quarantine)
- Click **Save**.
- After the configuration is saved, click **Test** to verify network connectivity between the Zscaler Deception Admin Portal and VMware Carbon Black Endpoint Standard.
[]You can contain detected attackers automatically by creating an orchestration rule or manually by taking action from the Investigate page.
- [Create a rule.](#carbon-black-defense-containment-create-rule)
- [Take action from the Investigate page.](#carbon-black-defense-containment-take-action)
- []Go to **Orchestrate** > **Rule**.
-
Click **Add Rule**.
[See image.](#vmware-cb-ed-containment-add-rule-option)
- In the **Rule Details** window:
- Enter the name of the rule.
- Select **Enabled**.
-
Create a rule using queries and conditions.
[See image.](#vmware-cb-ed-containment-rule-details)
-
Under **Respond**, enable **VMware Carbon Black Endpoint Standard**.
[See image.](#deception-respond-endpoint-standard)
-
Click **Save**.
The attacker is contained by VMware Carbon Black Endpoint Standard in accordance with the conditions configured when the rule is triggered.
-
[]On the **Investigate** page, click an attack icon on the alert graph.
The attacker details pane opens.
[See image.](#vmware-cb-ed-containment-action-option)
-
Click **Actions**.
A list of actions that you can take to remediate the threat appears.
-
Click the **Carbon Black** drop-down menu, and select **Contain with VMware Carbon Black Endpoint Standard**.
[See image.](#vmware-cb-ed-containment-take-action)
- In the confirmation window, click **OK**.
After containing the detected attackers, you can [view the details of the attacker](/deception/viewing-contained-attacker-ip-address-details).
[]![VMware Carbon Black Endpoint Standard Containment Edit option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-vmcarbon-endpoint-standard-edit.png)
[]![Contain attacker using the policy configured on Carbon Black Endpoint Standard](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-cb-defense-action-type-apply-policy.png)
[]![Contain attacker using the Quarantine option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-cb-defense-action-type-quarantine.png?1669781046)
[]![Add Rule option](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-add-rule.jpg)
[]![Configure general block in a rule to contain attacker with VMware Carbon Black Endpoint Standard](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-vmware-endpoint-standard-general.jpg)
[]![Configure a containment rule with VMware Ednpoint Standard](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-vmware-endpoint-standard-respond-new.png)
[]![Action button on the Attacker Details pane](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-cb-ep-containment-action-option.png)
[]![Contain attacker with VMware Carbon Black Endpoint Standard](/downloads/deception/orchestrate/containment-integrations/zscaler-deception-and-vmware-carbon-black-endpoint-standard-deployment-guide/zscaler-deception-vmware-endpoint-standard-action.png)