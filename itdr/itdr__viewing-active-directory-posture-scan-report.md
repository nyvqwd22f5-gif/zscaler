# Viewing the Active Directory Posture Scan Report
Source: https://help.zscaler.com/itdr/viewing-active-directory-posture-scan-report
PDF: https://help.zscaler.com/pdf/com/en/1531625.pdf

You can view the posture scan report for a [scanned Active Directory (AD)](/itdr/scanning-active-directory) domain. On the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard, you can select an AD domain to view the latest scan report. You can select a timestamp to view a specific report based on the scan date and time.
The AD posture scan report shows vulnerability issues, affected user accounts, and affected computers. The report enables you to analyze and remediate issues to maintain the security posture of your AD infrastructure.
The scan reports are permanently deleted when the retention policy period expires. To learn more, see [Configuring a Retention Policy](/itdr/about-advanced-settings#itdr-adv-settings-retention-page-section).
To view the AD posture scan report:
- Go to **ITDR** > **Dashboard > Active Directory Posture**.
- On the **Active Directory Posture **dashboard:
- Select an AD domain from the **Result for** drop-down menu.
-
Select a timestamp from the **scanned on** drop-down menu.
The scan result for the AD domain appears.
-
Click **View Report**.
[See image.](#itdr-view-vul-report-option)
The posture scan report for the AD domain appears.
- In the report, you can view the following information on each tab:
- [Issues](#itdr-issue-identity-vulnerability-report)
- [Users](#itdr-users-identity-vulnerability-report)
- [Computers](#itdr-computers-identity-vulnerability-report)
[]Lists the vulnerability issues. For each issue, you can:
- View the following details:
- **Issue**: The vulnerability issue. You can use the search field to search for a specific issue.
- **Description**: The description of user accounts and groups that are affected by vulnerability issues. You can use the search field to search for a specific description.
- **Type of Risk**: The type of vulnerability risk (e.g., **Kerberos Abuse**, **Credential Exposure**, **Weak Permissions**, etc.). You can use the search field to search for a specific type of risk.
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Medium**, or **Low**). You can filter the column to view issues by severity.
- **Remediation**: The remediation assessment (e.g., **Difficult**, **Moderate**, or **Easy**). You can filter the column to view issues by remediation.
- Click the **Create ServiceNow ticket** icon to [create a ServiceNow ticket](/itdr/creating-servicenow-ticket) to track and assess the issue.
[See image.](#deception-issue-report)
Click **Download Excel Report t**o download the report to your local system as an Excel file. You can [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
[]Lists the user accounts affected by issues. For each user account, you can view:
- **Identity**: The AD user account name. Double-click the AD user to view [affected AD user details](/itdr/viewing-affected-active-directory-user-account-details). You can use the search field to search for a specific user.
- **Type of Risk**: The type of vulnerability risk (e.g., **Kerberoastable accounts**, **GPO control rights**, **Account control rights**, etc.). You can filter the column to view issues for a specific type of risk.
- **Critical Group Membership**: The group membership of the critical AD group. ADs are primarily categorized into security and distribution groups. These groups have 4 different scopes, including universal, global, domain local, and local. Scope helps determine the areas in the AD domain where a group's permissions can be enforced successfully. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups). You can use the search field to search for a specific group membership.
- **Identity Classification**: The AD user account type, such as privileged or service. A privileged AD user account has powerful permissions that allow the user to perform nearly any action in the AD. A service AD user account is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Medium**, or **Low**). You can filter the column to view issues by severity.
[See image.](#deception-identity-user-report)
Select **Download User **from the **Actions** drop-down menu to download the report to your local system as a CSV file. You can [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
[]Lists the computers affected by issues. For each computer, you can view:
- **Identity**: The computer name. Double-click the computer to view the [affected AD computer details](/itdr/viewing-affected-active-directory-computer-details). You can use the search field to search for a specific computer.
- **Type of Risk**: The type of vulnerability risk (e.g., **GPO control rights**, **Constrained Delegation**, **Obsolete Operating System**, etc.). You can filter the column to view issues for a specific type of risk.
- **Critical Group Membership**: The group membership of the critical AD group. ADs are primarily categorized into security and distribution groups. These groups have 4 different scopes, including universal, global, domain local, and local. Scope helps determine the areas in the AD domain where a group's permissions can be enforced successfully. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups). You can use the search field to search for a specific group membership.
- **Identity Classification**: The AD user account type, such as privileged or service. A privileged AD user account has powerful permissions that allow the user to perform nearly any action in the AD. A service AD user account is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises) accounts.
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Medium**, or **Low**). You can filter the column to view issues by severity.
[See image.](#deception-identity-computer-report)
Select **Download Computer **from the **Actions** drop-down menu to download the report to your local system as a CSV file. You can [copy specific columns](/itdr/using-tables#itdr-copy-columns-table-section) from the table.
[]![The View Report option](/downloads/itdr/dashboard/viewing-vulnerability-report/itdr-view-report-option.png)
[]![View a AD issues](/downloads/itdr/dashboard/viewing-vulnerability-report/itdr-vulnerability-report-issues-tab.png)
[]![View affected AD user details in the scan report](/downloads/itdr/dashboard/viewing-vulnerability-report/itdr-vulnerability-report-users-tab.png)
[]![View affected AD computer details in the scan report.](/downloads/itdr/dashboard/viewing-vulnerability-report/itdr-vulnerability-report-computers-tab.png)