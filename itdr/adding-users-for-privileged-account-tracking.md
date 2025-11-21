# Adding Users for Privileged Account Tracking
Source: https://help.zscaler.com/itdr/adding-users-for-privileged-account-tracking
PDF: https://help.zscaler.com/pdf/com/en/1531889.pdf

You can add users or groups to track in an Active Directory (AD) domain apart from the default privileged users. Each login activity of these users is monitored, and any suspicious activities are listed in the [Active Directory Privileged Account Tracking report](/itdr/about-ad-privileged-account-tracking-report). You can add a maximum of 200 user accounts to track in each AD domain.
Prerequisites
Before you add users to track, ensure that the following prerequisites are met:
- The [Session Tracking setting](/itdr/enabling-session-tracking-and-password-analysis-server-agent) for a server agent must be enabled.
- Users or groups that are added for tracking must be found in the AD domain.
Adding an Individual User for Tracking
To add an individual user for tracking:
- Go to **ITDR **> **Manage **> **AD Privileged Account Tracking**.
-
Click **Add User**.
[See image.](#add-user1)
-
In the **Add Users to Track** window:
- **Type**: Select **User **from the drop-down menu.
- **UPN**: Enter the User Principal Name (UPN) of the user as it appears in the AD domain. The user cannot be tracked if the UPN is not found.
- **Reason**: Enter a reason for tracking this user.
[See image.](#add-individual-user)
-
Click **Save**.
The user is added for tracking on the [AD Privileged Account Tracking](/itdr/about-ad-privileged-account-tracking) page.
Adding a Group for Tracking
To add a group for tracking:
- Go to **ITDR **> **Manage **> **AD Privileged Account Tracking**.
-
Click **Add User**.
[See image.](#add-user2)
-
In the **Add Users to Track** window:
- **Type**: Select **Group** from the drop-down menu.
- **Distinguished Name**: Enter the full Distinguished Name (DN) of the group as it appears in the AD domain. The group cannot be tracked if the name is not found.
- **Reason**: Enter a reason for tracking this group.
[See image.](#add-group)
-
Click **Save**.
The group is added for tracking on the [AD Privileged Account Tracking](/itdr/about-ad-privileged-account-tracking) page.
When all users are fetched from a group, the group name is replaced by the users in the group on the AD Privileged Account Tracking page.
[]![AD Privileged Account Tracking page with highlighted Add User button.](/downloads/itdr/scan-configuration/active-directory-privileged-account-tracking/adding-users-for-privileged-account-tracking/ITDR-PAT-1.png)
[]![Add users to track window for privileged account monitoring.](/downloads/itdr/itdr/ITDR-add-individual-user1.png)
[]![AD Privileged Account Tracking page with highlighted Add User button.](/downloads/itdr/scan-configuration/active-directory-privileged-account-tracking/adding-users-for-privileged-account-tracking/ITDR-PAT-2.png)
[]![Add users to track window for privileged account monitoring.](/downloads/itdr/scan-configuration/active-directory-privileged-account-tracking/adding-users-for-privileged-account-tracking/ITDR-add-group1.png)