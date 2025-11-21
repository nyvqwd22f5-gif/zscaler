# About Entra ID Change Detection
Source: https://help.zscaler.com/itdr/about-entra-id-change-detection
PDF: https://help.zscaler.com/pdf/com/en/1531759.pdf

[Watch a video on Entra ID Change Detection.](https://fast.wistia.net/embed/iframe/y1qs9e29jz)
Entra ID Change Detection monitors and detects active changes in an Entra ID tenant and classifies these changes as a good, bad, or info impact. It also provides additional issues and remediation details. Zscaler ITDR also allows you to customize the active changes you want to detect and monitor in the following Entra ID properties for each identity type:
- **Users**: Role assignment changes, password changes, multi-factor authentication (MFA) changes, users flagged as risky, delegated permission grants to applications, administrative units, and group memberships.
- **Service Principals**: Secret or Certificate changes, added or revoked admin permissions, added or removed API permissions, added or removed app roles, ownership changes, and group membership changes.
- **Entra Roles**: Additions and removals of roles.
- **RBAC and Custom Roles**: Additions and removals of roles.
Some of the changes or issues that Entra ID Change Detection detects in an Entra ID tenant as as follows:
- **Users without multi-factor authentication (MFA)**: MFA acts as an additional layer of security to prevent unauthorized users from accessing Entra ID tenants. If any user is exempted from MFA to sign in, the change is detected and marked as a bad impact.
- **Privileged guest accounts**: Whenever a guest user is assigned a privileged role, this action is detected and marked as a bad impact. It is recommended to assign the least required permissions to the guest users.
- **Revoked roles on a service principal**: When permissions to access private data are revoked from a service principal, the overall attack surface reduces and stops the application's ability to read private data. This is marked as a good impact.
To view the change detection data, you need to [configure an Entra ID tenant](/itdr/connecting-entra-id-tenant-zscaler-itdr-admin-portal) for a scan or [configure a change detection policy](/itdr/adding-change-detection-entra-id-change-detection-object-safelist) for custom change detection. Entra ID Change Detection uses the Entra ID scan results to collect data. ITDR makes API calls to Entra ID every 15 minutes to detect any changes in Entra identity properties. The detected changes are analyzed and displayed on the Entra ID Change Detection page for further analysis.
Entra ID Change Detection provides the following benefits and enables you to:
- Obtain near real-time visibility into new misconfigurations and security risks introduced to your Entra ID tenant.
- Monitor and analyze critical changes in the Entra ID identity properties.
- Improve the security posture of your Entra ID.
About the Entra ID Change Detection Page
On the Entra ID Change Detection page (ITDR > Dashboard > Entra ID Change Detection > Default), you can see the following tabs:
- [Default](#defautentraID)
- [Custom](#customentraID)
[]On the Default tab, you can do the following:
- Filter change detection results by an Entra ID tenant.
- [Copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
- View change detection data for the Entra ID tenant. For each change, you can view:
- **Change Date**: The date and time when a change is detected in the Entra ID tenant.
- **Issue**: The issues for which the change is detected (e.g., **Insecure permissions on application**, **Privileged guest accounts**, etc.). You can filter the column to view a specific issue. Double-click to view [issue and remediation details](/itdr/viewing-change-detection-issue-and-remediation-details).
- **Identity**: The name of the Entra ID user or service principal (identity) for which the change is detected. You can use the search option to search for a specific identity.
- **Initiated By**: The details of identity who initiated this change. You can use the search option to search for a specific identity who initiated the change.
- **Reason**: The reason for the change.
- **Impact**: Indicates the following change status. You can filter the column to view a specific change.
- **Good**: A good or safe change.
- **Bad**: A risky change. The system administrators can review and remediate the issue.
- **Info**: A significant change to the Entra ID tenant that might be a good or bad impact based on the environment. The system administrators can review the impact and take necessary actions.
- **Type**: The type of Entra ID identity (**User** or **Service Principal**). You can filter the changes by identity type.
- [View the Entra ID change detection issue details and remediation](/itdr/viewing-entra-id-change-detection-issue-and-remediation-details).
- [Add an Entra ID change detection issue to the safelist](/itdr/adding-change-detection-issue-entra-id-change-detection-safelist).
- [Add an Entra ID change detection object to the safelist](/itdr/adding-change-detection-entra-id-change-detection-object-safelist).
- [Create a ServiceNow ticket for a bad change](/itdr/creating-servicenow-ticket).
![About the Entra ID Change Detection Dashboard](/downloads/tech-pubs-drafts/itdr-draft-articles/about-entra-id-change-detection-dashboard-draft/entraid-change-detection.png)
[]On the Custom tab, you can do the following:
- Filter change data by an Entra ID tenant.
- [Copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
- View change data for the Entra ID properties. For each change, you can view:
- **Change Date**: The date and time when a change is detected in the Entra ID tenant.
- **Identity**: The name of the Entra ID identity, such as users, service principals, and Entra and RBAC roles. You can use the search option to search for a specific identity.
- **Policy Name**: The name of the Entra ID change detection policy. You can use the search option to search for a specific policy.
- **Identity Type**: The type of Entra ID identity (**User**, **Service Principal**, or **Role**). You can filter the column to view data for a specific identity type.
- **Change Type**: The type of active changes detected in the Entra ID properties. You can filter the column to view data for a specific change type.
-
View the history of changes of Entra ID properties to compare the previous and current changes for further analysis. The history provides the following details:
- The Entra ID identity details, such as the change date, identity name, change detection policy name, and identity type (**User**, **Service Principal**, or **Role**).
- The previous and current Entra ID property change details.
[See image.](#details-window)
- Delete change details of Entra ID properties.
![The Entra ID Change Detection Custom dashboard with the list of changes detected in the Entra ID tenant.](/downloads/itdr/dashboard/entra-id-change-detection/about-entra-id-custom-change-detection-dashboard/itdr-custom-entraID-change-detection.png)
[]
![View Entra ID identity property change details ](/downloads/itdr/dashboard/entra-id-change-detection/viewing-history-entra-id-properties-change-details/itdr-about-entra-id-custom-cd-view-details-1.png)