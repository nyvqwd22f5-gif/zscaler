# Configuring Password Expiration
Source: https://help.zscaler.com/cloud-branch-connector/configuring-password-expiration
PDF: https://help.zscaler.com/pdf/com/en/1420776.pdf

To provide additional security, you can enable password expiration for all admins logging in to the Zscaler Cloud & Branch Connector Admin Portal.  Zscaler strongly recommends implementing routine password rotation as a fundamental best practice to safeguard your organization.
If you don't enable this setting, passwords will never expire.
To configure password expiration for admins:
- Go to** Administration** > **Administrator Management**.
- Click the** Administrators Management** tab.
- In the **Password Management** section:
- **Password Expiration**: Enable passwords to expire for admins in the portal. If enabled, a column shows if an admin's password has expired on the Administrators page (Administration** **> Administrator Management > Administrators). To learn more, see [About Administrators](/cloud-branch-connector/about-administrators). The **Password Expires After** field appears when this setting is enabled.
- **Password Expires After**: Enter the number of days you want passwords to be valid for Cloud & Branch Connector admins. The default is 180 days. The days can range from 15 to 365.
The Zscaler service reminds admins to change their password 15 days before its expiration. Also, when an admin logs into the portal, they are alerted to how many days their password will remain valid. If admins change their password before it expires, their new password will be valid for the specified time. However, if their password expires, admins must register a new password to access any features in the portal.
A new password must be at least 8 characters in length, and include at least one uppercase letter, one number, and one special character. Also, the new password cannot be the same as the previous one.
[See image.](#password-exp)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]![Password Management section on the Administrators Management page in the Zscaler Cloud & Branch Connector Admin Portal.](/downloads/cloud-branch-connector/administration/administrator-role-management/configuring-password-expiration/Configuring%20Password%20Expiration%20up.jpg)