# Viewing the Top Vulnerable Active Directory Users and Computers
Source: https://help.zscaler.com/itdr/viewing-top-vulnerable-active-directory-users-and-computers
PDF: https://help.zscaler.com/pdf/com/en/1531772.pdf

You can view a list of the top 10 Active Directory (AD) users and computers that have the highest risks in the AD domain on the [Active Directory Posture](/itdr/about-active-directory-posture-dashboard) dashboard. Having visibility of these 10 riskiest identities in your AD domain helps you to prioritize what to focus on first. You can view issue details, such as risk type, severity level, critical group membership, etc. You can drill down to a specific user or computer to further investigate and swiftly remediate the issue.
To view the top vulnerable AD users and computers:
- Go to **ITDR** > **Dashboard** > **Active Directory Posture**.
-
On the **Active Directory Posture** dashboard:
- Select an AD domain from the **Result for** drop-down menu.
- Select a timestamp from the **scanned on** drop-down menu.
[See image.](#itdr-ad-top-10-users-computers-select-domain-timestamp)
The scan result for the AD domain appears.
-
Click **Top 10 Users & Computers**.
[See image.](#itdr-ad-top-10-users-computers-link)
The **Users and Computers** page appears. The issues are listed under the tabs (**All**, **Users**, and **Computers**)
-
Select a tab to view the following information:
- **Identity**: The AD object identity (user or computer). Click an AD [user](/itdr/viewing-affected-active-directory-user-account-details) or [computer](/itdr/viewing-affected-active-directory-computer-details) to view the details. You can use the search field to search for a specific identity.
- **Type**: The AD object type (**User** or **Computer**).
- **Type of Risk**: The type of vulnerability risk (e.g., **Vulnerable to AS-REP roasting**, **Privileged account delegation**, **Stale passwords**, etc.). Click the number to view all the risk types. You can filter the column to view issues for a specific risk type.
- **Critical Group Membership**: The group membership of the critical AD group. ADs are primarily categorized into security and distribution groups. These groups have 4 different scopes, including universal, global, domain local, and local. Scope helps determine the areas in the AD domain where a group's permissions can be enforced successfully. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups). You can use the search field to search for a specific group membership.
- **Identity Classification**: The AD user account type, such as privileged or service. A privileged AD user account has powerful permissions that allow the user to perform nearly any action in the AD. A service AD user account is created to run a particular service or application on the Microsoft Windows operating system and has the minimum permissions that are required to run the services. To learn more, refer to the Microsoft documentation for [Privileged](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/security-best-practices/appendix-b--privileged-accounts-and-groups-in-active-directory) and [Service accounts](https://learn.microsoft.com/en-us/entra/architecture/service-accounts-on-premises).
- **Severity**: The severity level of the vulnerability issue (e.g., **Critical**, **High**, **Medium**, or **Low**). You can filter the column to view issues for a specific severity level.
[See image.](#itdr-ad-view-comp-user-issue-details)
On each of these tabs, you can use the **Actions** menu to download the table in the Excel format and [copy specific columns from the table](/itdr/using-tables).
You can double-click an AD [user](/itdr/viewing-affected-active-directory-user-account-details) or [computer](/itdr/viewing-affected-active-directory-computer-details) to view additional details, such as posture risk score, failed posture checks, associated Okta user account details, Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) access snapshots, assigned roles, etc.
[]![Select an AD domain and scan timestamp](/downloads/itdr/dashboard/active-directory/viewing-issue-finding-recommendation-details/itdr-ad-post-scan-domain-date-without-options_0.png)
[]![Click Top 10 Users and Computers](/downloads/itdr/dashboard/active-directory/viewing-top-vulnerable-active-directory-users-and-computers/itdr-ad-dashboard-top-10-user-computer.png)
[]![View affected AD user details](/downloads/itdr/dashboard/active-directory/viewing-top-vulnerable-active-directory-users-and-computers/itdr-ad-view-top-10-issues.png)