# Specifying Selection Criterion for Threat Detection Policies
Source: https://help.zscaler.com/itdr/specifying-selection-criterion-threat-detection-policies
PDF: https://help.zscaler.com/pdf/com/en/1531683.pdf

After a [threat detection policy is added](/itdr/creating-endpoint-policy), you need to specify a selection criterion. The endpoint agent fetches the policy from the Zscaler ITDR Admin Portal and applies it to the endpoints based on the selection criterion.
By default, the Catch All criterion is selected for the newly created threat detection policy to apply the policy to all of the endpoint agents.
To specify a selection criterion:
- Go to **ITDR **> **Manage **> **Threat Detection**.
-
Locate the threat detection policy you want to specify a selection criterion for, and click the **Edit **icon.
[See image.](#edit-landmine-policy-specify-criterion)
-
In the policy configuration window, select **Endpoint Selection**.
[See image.](#select-criteria-option)
- In the **Endpoint Selection** window, choose a criterion from the drop-down menu:
-
**Catch All**: Apply the threat detection policy to all endpoint agents.
[See image.](#catch-all-criterion)
-
[]**Dynamic Rule**: Apply the threat detection policy to all the endpoints that matches the rule specified in the following fields. Choose an option from the **Attribute** drop-down menu:
- **Process List**: Apply the threat detection policy to the endpoints that contain the processes specified in the **Contains** field.
- **Browser History**: Apply the threat detection policy to the endpoints whose browser history has the URL specified in the **Contains** field.
- **Installed Programs**: Apply the threat detection policy to the endpoints that contain the installed programs specified in the **Contains** field.
- **Interesting Files**: Apply the threat detection policy to the endpoints that contain the files specified in the **Contains** field.
- **Recent Commands**: Apply the threat detection policy to the endpoints whose recent command list in the **Run** dialog box matches the commands specified in the **Contains** field.
Click **Add** to add multiple dynamic rules to a single policy. If *any one* of the rules matches, the policy is applied at the endpoint.
[See image.](#dynamic-rule-criterion)
-
**User**: Apply the threat detection policy to all the endpoints where at least one of the users specified in the **User** field is logged in. You can enter the usernames in the **User** field, or click **Upload** to upload a text file with the usernames. You can also export the list of users as a text file.
[See image.](#user-criterion)
-
**Group**: Apply the threat detection policy to all the endpoints that are under the Active Directory (AD) groups specified in the **Group** field. You can enter the group names in the **Group** field, or click **Upload** to upload a text file with the group names. You can export the list of group names as a text file.
[See image.](#group-criterion)
-
**Hostname (Specific)**: Apply the threat detection policy to all the endpoints where the hostname of the system exactly matches one of the hostnames specified in the **Hostname** field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#hostname-specific-criterion)
-
**Hostname (RegEx)**: Apply the threat detection policy to all the endpoint agents where the hostname of the system matches the hostname pattern specified as a regular expression in the **RegEx** field.
[See image.](#hostname-regex-criterion)
-
**DNS Hostname (Specific)**: Apply the policy to all endpoints whose FQDN matches with one of the FQDN values specified in the **Hostname** field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#itdr-tp-dns-specific)
-
**DNS Hostname (RegEx)**: Apply the policy to all endpoints where the FQDN of the system matches the FQDN pattern specified as a regular expression in the **RegEx** field.
[See image.](#itdr-tp-dns-regex)
-
**User OU (RegEx)**: Apply the threat detection policy to all the users present in the organization unit (OU) that matches the OU regular expression pattern in the **RegEx** field.
[See image.](#ou-regex-criterion)
-
**Computer OU (RegEx)**: Apply the threat detection policy to all the systems present in the OU that match the OU regular expression pattern in the **RegEx** field.
[See image.](#computer-ou-regex-criterion)
-
**Fallback**: Apply the threat detection policy to any system that has no other policy criteria specified. If you have specified the **Catch All **criterion, then the **Fallback** criterion is not applied.
[See image.](#fallback-criterion)
-
Click **Save**.
The specified selection criterion is listed in the [threat detection table](/itdr/about-threat-detection).
[]![Edit icon on the Threat Detection page](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-threat-detection-edit-icon.png)
[]![Select Criteria option ](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-endpoint-selection.png)
[]![Catch all threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-select-all.png)
[]![Dynamic rule threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-dynamic-rule.png)
[]![Users threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-user.png)
[]![Group threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-group.png)
[]![Hostname Specific threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-hostname.png)
[]![Hostnames RegEx threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-hostanme-regex.png)
[]![Configuring endpoint selection criteria using DNS hostname value](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-credex-policy-criteria-dns-specific.png)
[]![Configuring endpoint selection criteria using DNS hostname value in regex format](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-credex-policy-criteria-dns-regex.png)
[]![User OU (RegEx) threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es--user-ou.png)
[]![Computer OU RegEx threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-computer-ou-regex.png)
[]![Fallback threat detection policy selection criterion](/downloads/itdr/threat-detection-policies/specifying-selection-criterion/itdr-es-fallback.png)