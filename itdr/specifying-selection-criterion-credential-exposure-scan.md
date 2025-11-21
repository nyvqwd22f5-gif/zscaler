# Specifying Selection Criterion for Credential Exposure Scan
Source: https://help.zscaler.com/itdr/specifying-selection-criterion-credential-exposure-scan
PDF: https://help.zscaler.com/pdf/com/en/1531717.pdf

[Watch a video on Endpoint Credential Exposure.](https://fast.wistia.net/embed/iframe/rfq1kuvn5v)
After a [credential exposure scan](/itdr/configuring-endpoint-credential-exposure-scan) is added, you need to specify a selection criterion. The endpoint agent fetches the policy from the Zscaler ITDR Admin Portal and applies it to the endpoints based on the selection criterion.
By default, the Catch All criterion is selected for the newly created credential exposure scan to apply the policy to all the endpoint agents.
To specify a selection criterion:
- Go to **ITDR **> **Manage** > **Endpoint Credential Exposure**.
-
Locate the scan you want to specify a selection criterion for, and click the **Edit **icon.
[See image.](#edit-landmine-policy-specify-criterion)
-
In the configuration window, select **Endpoint Selection**.
[See image.](#select-criteria-option)
- In the **Endpoint Selection** window, choose a criterion from the drop-down menu:
-
**Catch All**: Apply the policy to all endpoint agents.
[See image.](#catch-all-criterion)
-
**User**: Apply the policy to all the endpoints where at least one of the users specified in the **User** field is logged in. You can enter the usernames in the **User** field, or click **Upload** to upload a text file with the usernames. You can also export the list of users as a text file.
[See image.](#user-criterion)
-
**Group**: Apply the policy to all the endpoints that are under the Active Directory (AD) groups specified in the **Group** field. You can enter the group names in the **Group** field, or click **Upload** to upload a text file with the group names. You can export the list of group names as a text file.
[See image.](#group-criterion)
-
**Hostname (Specific)**: Apply the policy to all the endpoints where the hostname of the system exactly matches one of the hostnames specified in the **Hostname** field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#hostname-specific-criterion)
-
**Hostname (RegEx)**: Apply the policy to all the endpoint agents where the hostname of the system matches the hostname pattern specified as a regular expression in the **RegEx** field.
[See image.](#hostname-regex-criterion)
-
**DNS Hostname (Specific)**: Apply the policy to all endpoints whose FQDN matches with one of the FQDN values specified in the **Hostname** field. You can enter the hostnames in the **Hostname** field, or click **Upload** to upload a text file with the hostnames. You can export the list of hostnames as a text file.
[See image.](#itdr-credex-dns-specific)
-
**DNS Hostname (RegEx)**: Apply the policy to all endpoints where the FQDN of the system matches the FQDN pattern specified as a regular expression in the **RegEx** field.
[See image.](#itdr-credex-dns-regex)
-
**User OU (RegEx)**: Apply the policy to all the users present in the organization unit (OU) that matches the OU regular expression pattern in the **RegEx** field.
[See image.](#ou-regex-criterion)
-
**Computer OU (RegEx)**: Apply the policy to all the systems present in the OU that match the OU regular expression pattern in the **RegEx** field.
[See image.](#computer-ou-regex-criterion)
-
Click **Save**.
A confirmation message appears indicating that the selection criterion is saved.
[]![Edit icon on the Endpoint Credential Exposure page](/downloads/itdr/itdr/endpoint-credential-exposure-scan/specifying-selection-criterion-credential-exposure-scan/itdr-ece-edit-icon.png)
[]![Select Criteria option ](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-exposure-selection-criteria.png)
[]![Catch All selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-catch-all.png)
[]![User selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-users.png)
[]![Group selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-group.png)
[]![Hostname Specific selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-hostname.png)
[]![Hostname RegEx selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-hostname-regex.png)
[]![DNS Hostname Specific selection criterion](/downloads/tech-pubs-drafts/itdr-draft-articles/specifying-selection-criterion-credential-exposure-scan-draft/itdr-credex-policy-criteria-dns-specific.png)
[]![DNS Hostname RegEx selection criterion](/downloads/tech-pubs-drafts/itdr-draft-articles/specifying-selection-criterion-credential-exposure-scan-draft/itdr-credex-policy-criteria-dns-regex.png)
[]![User OU (RegEx) selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-user-ou.png)
[]![Computer OU RegEx selection criterion](/downloads/itdr/specifying-selection-criterion-credential-exposure-scan/itdr-selection-criteria-computer-ou.png)