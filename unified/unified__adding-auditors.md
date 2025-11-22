# Adding Auditors
Source: https://help.zscaler.com/unified/adding-auditors
PDF: https://help.zscaler.com/pdf/com/en/1490796.pdf

You must have a super admin [role](/unified/adding-admin-roles) and organizational [scope](/unified/about-admin-scope) to add [auditors](/unified/about-auditors).
To add an auditor:
- Go to **Administration **>** Admin Management **> **Administrator Management **>** Internet Access Administrators**.
- Click the **Auditors **tab.
-
Click **Add Auditor**.
The **Add Auditor** window appears.
- In the **Add Auditor** window:
- **Login ID**: Enter the login ID the auditor uses to log in from your SSO provider portal, and select the appropriate domain name. The domain names you provided to Zscaler appear in the drop-down menu.
- **Name**: Enter a name for the auditor.
- **Status**: Enable or disable the auditor. If you disable the auditor, the password is automatically cleared. So, when you re-enable the status of the disabled auditor, you must set a new password. If SAML is enabled, then setting a password is optional. You can save your changes only after the authentication is complete.
- **Comments**: (Optional) Enter additional notes or information. The comments cannot exceed 10,240 characters.
- **New Password**: Enter a password for the auditor. It can be 8 to 100 characters and must contain at least one number, one special character, and one upper-case letter. This is the password the auditor must enter to give an admin permission to view user names. To learn more, see [About Auditors](/unified/about-auditors).
- **Confirm Password**: Re-enter the password to confirm.
- Click **Save **and [activate the change](/unified/saving-and-activating-changes-admin-portal).