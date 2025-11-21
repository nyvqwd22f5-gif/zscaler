# Remediating Active Directory Changes
Source: https://help.zscaler.com/itdr/remediating-active-directory-changes
PDF: https://help.zscaler.com/pdf/com/en/1531876.pdf

You can take remediation actions on the Active Directory (AD) user identities in which changes are detected. Remediation is available only for users with bad changes in the AD domain. You can take the following remediation actions and apply them to single or multiple users:
- Enable User
- Disable User
- Reset Password
- Revoke Group Membership
To run remediations for users with bad changes:
- Go to **ITDR** > **Active Directory Change Detection **> **Default **or **Custom**.
- Select an AD domain from the **Result for** drop-down menu.
- Do one of the following:
-
Click the **Remediation **icon for the AD change you want to remediate, and then select an appropriate remediation action.
[See image.](#single-adchange)
-
Select multiple AD user changes, click **Remediations**, and then select a remediation action.
[See image.](#bulk-changes)
**Revoke Group Membership** is not available for bulk remediation action.
-
In the confirmation window, click **OK**.
The remediation is applied successfully.
You can [view the remediation logs or history](/itdr/viewing-ad-remediation-history) for further analysis.
[]![The Remediations icon and list of remediations available for a single Active Directory change.](/downloads/itdr/dashboard/active-directory-change-detection/running-remediations-active-directory-change-detection-dashboard/itdr-ad-cd-remediation.jpg)
[]![The Remediations menu and list of remediations available for multiple Active Directory changes.](/downloads/itdr/dashboard/active-directory-change-detection/running-remediations-active-directory-change-detection-dashboard/ad-bulk-cd-remediations.jpg)