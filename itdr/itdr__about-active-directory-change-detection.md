# About Active Directory Change Detection
Source: https://help.zscaler.com/itdr/about-active-directory-change-detection
PDF: https://help.zscaler.com/pdf/com/en/1531635.pdf

[Watch a video on Active Directory Change Detection.](https://fast.wistia.net/embed/iframe/37o4d4nbip)
Active Directory Change Detection monitors and detects active changes in an Active Directory (AD) domain, and classifies these changes as a good, bad, or info impact. It also provides additional issue and remediation details. Zscaler ITDR also allows you to customize the active changes you want to detect and monitor in the following AD properties for each identity type:
- **Users**: Access-control lists (ACLs), passwords, and group membership properties.
- **Groups**: ACLs, members, and group membership properties.
- **Computers**: ACLs and group membership properties.
The AD Change Detection monitors AD domains for the following issues:
- Kerberoastable accounts
- Vulnerable to AS-REP roasting
- Accounts with passwords set to never expire
- Accounts with password not required
- Accounts with exposed attributes
- Privileged account delegation
- Unconstrained delegation
- Constrained delegation
- Privileged account added or removed
- Vulnerable to DCSync attacks
- AdminSDHolder permissions
To view the change detection data, you need to [configure an AD domain for a scan](/itdr/scanning-active-directory) and enable the change detection feature or [configure a change detection policy](/itdr/creating-active-directory-custom-change-detection-policy) for custom change detection. AD Change Detection uses the AD scan results to collect data. The scan runs every 15 minutes. Two scans are required to detect changes. The first scan creates the base results. Any changes detected in the second scan are recorded and compared with the base results, and the data is categorized as Good, Bad, or Info.
AD Change Detection provides the following benefits and enables you to:
- Monitor and analyze changes to important AD properties.
- Obtain near real-time visibility into new misconfigurations and security risks introduced to your AD.
- Improve the security posture of your AD.
About the Active Directory Change Detection Page
On the Active Directory Change Detection page (ITDR > Dashboard > Active Directory Change Detection), you can see the following tabs:
- [Default](#ad-changedetection)
- [Custom](#custom-adchangedetection)
[]On the Default tab, you can do the following:
- Filter change detection results by an AD domain.
- [Copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
-
View all change detection data for the AD domain. For each change, you can view:
- **Change Date**: The date and time when a change is detected in the AD domain.
- **Issue**: The issues for which the change is detected (e.g., **Privileged account delegation**, **Unconstrained Delegation**, etc.). You can filter the column to view a specific issue.
- **Identity**: The name of the AD account for which the change is detected.
- **Change**: The description of active changes.
- **Impact**: Indicates the following change status. You can filter the column to view a specific change:
- **Good: **A good or safe change.
- **Bad: **A risky change. The system administrators can review and remediate the issue.
- **Info: **A significant change to the AD account that might be a good or bad impact based on the environment. The system administrators can review the impact and take necessary actions.
- **Classification**: The AD user account type (**Privileged** or **Service**). You can filter the column to view a specific user account type.
- **Type**: The type of AD object (**User** or **Computer**). You can filter the column to view a specific type.
You can double-click a change to [view issue and remediation details](/itdr/viewing-change-detection-issue-and-remediation-details).
- [View the change detection issue details and remediation](/itdr/viewing-change-detection-issue-and-remediation-details).
- [Add a change detection issue to the safelist](/itdr/adding-change-detection-issue-safelist).
- [Add a change detection object to the safelist](/itdr/adding-change-detection-ad-change-detection-object-safelist).
- [Select a remediation to run on the identity](/itdr/running-remediation-actions-change-detection). This option is available only for users with bad changes.
- [Create a ServiceNow ticket for a bad change](/itdr/creating-servicenow-ticket). This option is available only for bad changes.
-
Select the checkboxes for multiple AD changes and click **Remediations **to run remediations.
[See image.](#bulk-remediation)
![About the AD Change Detection dashboard](/downloads/tech-pubs-drafts/itdr-draft-articles/about-active-directory-change-detection-dashboard-draft/ad-change-detection-dashboard.png)
[]On the Custom tab, you can do the following:
- Filter change data by an AD domain.
- [Copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
- View change data for the AD properties. For each change, you can view:
- **Change Date**: The date and time when a change is detected in AD properties.
- **Identity**: The name of the AD user account, group, or computer. You can filter the column to view data for a specific identity.
- **Policy Name**: The name of the AD change detection policy. You can filter the column to view the details for a specific policy.
- **Identity Type**: The type of AD identity (**User**, **Computer**, or **Group**). You can filter the column to view data for a specific identity type.
- **Changed Properties**: The AD properties that are changed.
-
View the identity details with the history of changes. You can compare the previous and current properties change for further analysis. The history provides the following details:
- The AD identity details, such as the change date, identity name, change detection policy name, and identity type (**User**, **Computer**, or **Group**).
- The previous and current AD property change details.
[See image.](#changemonitoringdetails)
- Delete change details of AD identity properties.
![About the AD Custom Change Detection dashboard ](/downloads/itdr/dashboard/active-directory-change-detection/about-active-directory-custom-change-detection-dashboard/itdr-ad-custom-change-detection.png)
[]![The Active Directory Change Detection dashboard with multiple changes selected and annotation around Remediations drop-down menu.](/downloads/tech-pubs-drafts/itdr-draft-articles/about-active-directory-change-detection-dashboard-draft/itdr-ad-bulk-remediation.png)
[]![The Change Monitoring Details window displaying the identity details and history of changes.](/downloads/itdr/dashboard/active-directory-change-detection/about-active-directory-change-detection/itdr-change-monitoring-details.png)