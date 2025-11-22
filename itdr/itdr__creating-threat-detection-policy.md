# Creating a Threat Detection Policy
Source: https://help.zscaler.com/itdr/creating-threat-detection-policy
PDF: https://help.zscaler.com/pdf/com/en/1531682.pdf

You can configure threat detection policies and specify a [selection criterion ](/itdr/specifying-selection-criterion)to apply to an endpoint. Each policy has a selection criterion, and the policy is applied to the endpoint only if the criterion matches.
Before creating threat detection policies, obtain information about the list of users, hostnames, and selection criteria.
To create a threat detection policy:
- Go to **ITDR** > **Manage** > **Threat Detection**.
-
Click **Add Policy**.
[See image.](#add-lm-policy)
-
In the **Policy Details** window:
- **Enabled**: Select to actively deploy the policy to the applicable endpoints.
- **Policy Name**: Enter a name for the policy.
[See image.](#policy-details)
-
Click **Save**.
The policy is added and listed on the **Threat Detection** page.
- After the threat detection policy is added, you need to [specify a selection criterion](/itdr/specifying-selection-criterion).
- After the selection criterion is specified, you can configure the [Active Directory](/itdr/configuring-itdr-active-directory) module.
[]![Add Policy on the Threat Detection page](/downloads/itdr/threat-detection-policies/creating-threat-detection-policy/itdr-threat-detection-add-policy.png)
[]![Configure threat detection details](/downloads/itdr/threat-detection-policies/creating-threat-detection-policy/itdr-policy-details_0.png)