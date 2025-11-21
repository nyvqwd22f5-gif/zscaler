# Creating a Landmine Policy
Source: https://help.zscaler.com/deception/creating-landmine-policy
PDF: https://help.zscaler.com/pdf/com/en/1531299.pdf

[Watch a video on Creating Landmine Policies and Decoys.](https://fast.wistia.net/embed/iframe/c3w5mose6l)
Landmine decoys are configured based on policies. Policies consist of various options, such as decoy files, processes, lures, etc. that can be applied to an endpoint. Each policy has a selection criterion, and the policy is applied to the endpoint only if the criterion matches.
Before creating landmine policies, obtain information about the list of users, hostnames, and selection criteria.
To create a landmine policy:
- [Step 1: Add a Landmine Policy](#adding-policy)
- [Step 2: Specify a Selection Criterion](#specifying-criteria)
- [Step 3: Configure the Lure Modules in the Landmine Policy](#lure-modules)
- []Go to **Deceive** > **Landmine** > **Policies**.
-
Click **Add Policy**.
[See image.](#add-lm-policy)
The **Policy Details** window appears.
-
In the **Policy Details** window:
- **Enabled**: Select to enable the policy.
- **Policy Name**: Enter a name for the policy. The name can be a user or system persona. For example, enter `IT Admins`.
- **OS**: Select an operating system of endpoints to which the policy should apply.
-
**Agentless**: Enable to deploy the policy in the agentless mode. By default, a policy is deployed in the agent mode.
The agentless policy applies only to the agentless version of Landmine, and the agent policy applies only to the agent version of Landmine.
[See image.](#policy-details)
-
Click **Save**.
The policy is added and listed in the **Policies** table.
[See image.](#policy-added-listed)
[]After the landmine policy is added, you need to specify a selection criterion. The landmine agent fetches the policy from the Zscaler Deception Admin Portal and applies it to the endpoints based on the selection criterion. If you are unsure about the criterion, specify the Catch All criterion to apply the policy to all of the landmine agents.
To specify a selection criterion:
-
In the **Policies** table, locate a landmine policy, and then click the **Edit** icon.
[See image.](#edit-landmine-policy-specify-criterion)
-
In the policy configuration window, click **Selection Criterion**.
[See image.](#select-criteria-option)
- In the **Selection Criterion** window, choose a criterion from the drop-down menu:
-
**Catch All**: Apply the policy to all landmine agents.
[See image.](#catch-all-criterion)
-
**Dynamic Rule**: Choose an option from the **Attribute** drop-down menu:
- **Process List**: Apply the policy to the endpoints that contain the processes specified in the **Contains** field. This is a substring of the process executable (e.g., `chrome`, `cmd`, and `winword.exe`).
- **Browser History**: Apply the policy to the endpoints whose browser history has the URL specified in the **Contains** field. This is a substring of URLs (e.g., `192.168.89.23`, `google.com`, and `https://www.zscaler.com`).
- **Installed Programs**: Apply the policy to the endpoints that contain the installed programs specified in the **Contains** field. This is a substring of the names of applications (e.g., `Google Chrome`, `Microsoft Office`, and `Firefox`).
- **Interesting Files**: Apply the policy to the endpoints that contain the files specified in the **Contains** field. This is a substring of the names of files (e.g., `passwords.txt`, `finance details`, and `ID Document`).
- **Recent Commands**: Apply the policy to the endpoints whose recent command list in the **Run** dialog box matches the commands specified in the **Contains** field (e.g., the list of comments that have been run from the Run prompt on Windows).
Click **Add** to add multiple dynamic rules to a single policy. If *any one* of the rules matches, the policy is applied at the endpoint.
[See image.](#dynamic-rule-criterion)
-
**User**: Apply the policy to all the endpoints where at least one of the users specified in the **User** field is logged in. You can enter the usernames in the **User** field, or click **Upload** to upload a text file with the usernames. To apply policies to Zscaler Client Connector users, specify their Zscaler Client Connector username. You can also export the list of users as a text file.
[See image.](#user-criterion)
-
**Group**: Apply the policy to all the endpoints that are under the Active Directory (AD) groups specified in the **Group** field. You can enter the group names in the **Group** field, or click **Upload** to upload a text file with the group names. You can export the list of group names as a text file.
Policies are applied to agents within a maximum of one day.
IdP groups are not supported.
[See image.](#group-criterion)
-
**Hostname (Specific)**: Apply the policy to all the endpoints where the hostname of the system exactly matches one of the hostnames specified in the **Hostname** field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#hostname-specific-criterion)
-
**Hostname (RegEx)**: Apply the policy to all landmine agents where the hostname of the system matches the hostname pattern specified as a regular expression in the **RegEx** field.
[See image.](#hostname-regex-criterion)
-
**DNS Hostname (Specific)**: Apply the policy to all endpoints whose FQDN matches with one of the FQDN values specified in the **Hostname **field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#dns-hostname-criterion)
-
**DNS Hostname (RegEx)**: Apply the policy to all landmine agents where the FQDN of the system matches the FQDN pattern specified as a regular expression in the **RegEx** field.
[See image.](#dns-hostname-regex)
-
**User OU (RegEx)**: Apply the policy to all the users present in the organization unit (OU) that matches the OU regular expression pattern in the **RegEx** field.
Policies are applied to agents within a maximum of one day.
[See image.](#ou-regex-criterion)
-
**Computer OU (RegEx)**: Apply the policy to all the systems present in the OU that match the OU regular expression pattern in the **RegEx** field.
Policies are applied to agents within a maximum of one day.
[See image.](#computer-ou-regex-criterion)
-
**Fallback**: Apply the policy to any system that has no other policy criteria specified. If you have specified the **Catch All **criterion, then the **Fallback** criterion is not applied.
[See image.](#fallback-criterion)
-
Click **Save**.
The specified selection criterion is listed in the **Policies** table.
[See image.](#selection-criterion-added)
[]After the selection criterion is specified, you can configure the required lure modules:
- [Password Settings](/deception/configuring-password-settings)
- [Defense Evasion](/deception/configuring-defense-evasion)
- [Privilege Escalation](/deception/configuring-privilege-escalation)
- [Cloud Lures](/deception/configuring-cloud-lures)
- [Browser Lures](/deception/configuring-browser-lures)
- [Session Lures](/deception/configuring-session-lures)
- [File Decoys](/deception/configuring-file-decoys)
- [Lure Settings](/deception/configuring-lure-settings)
- [Advanced Deception Capabilities](/deception/enable-advanced-deception-capabilities)
[]![Add Policy icon on the Policies page](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/deception-add-policy-button_0.png)
[]![Configure landmine policy details](/downloads/deception/product-documentation/deceive/endpoint-decoys/policies/creating-landmine-policy/zscaler-deception-policy-details-window-landmine.png)
[]![Landmine policy added](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/deception-added-new-policy.png)
[]![A screenshot capturing the option to edit a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/deception-edit-policy.png)
[]![ A screenshot highlighting the option to select criterion for a landmine policy](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/zscaler-deception-seelction-criterion.png)
[]![Catch all landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-catch-all.png)
[]![Dynamic rule landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-dynamic-rule.png)
[]![Users landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-user-new.png)
[]![Group landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-group.png)
[]![Hostname Specific landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-hostname-specific-new.png)
[]![Hostnames RegEx landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-hostname-regex.png)
[]![An FQDN configued as a DNS hostname selection criterion](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/zscaler-deception-specific-dns-hostnames.png)
[]![A regular expression for a FQDN configured as a DNS Hostname criterion](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/zscaler-deception-dns-regex.png)
[]![User OU (RegEx) landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-user-ou-regex.png)
[]![Computer OU RegEx landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-computer-ou-regex.png)
[]![Fallback landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/specifying-selection-criterion/zscaler-deception-fallback.png)
[]![Landmine policy selection criterion](/downloads/deception/deceive/landmine-decoys/policies/creating-landmine-policy/deception-policy-criterion_0.png)