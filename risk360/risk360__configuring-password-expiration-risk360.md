# Configuring Password Expiration in Risk360
Source: https://help.zscaler.com/risk360/configuring-password-expiration-risk360
PDF: https://help.zscaler.com/pdf/com/en/1456971.pdf

To provide additional security, you can enable password expiration for all admins logging in to the Risk360 Admin Portal.
If you don't enable this setting, the admins' passwords never expire.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#ZIdentity-administration)
To configure password expiration for admins:
- Go to** Administration** > **Administrator Management**.
- Click the** Administrator Management** tab.
- In the **Password Management** section:
- **Password Expiration**: Enable passwords to expire for all admins in the Risk360 Admin Portal. If enabled, you can see a column showing if an admin's password has expired on the [Administrators](/risk360/about-administrators-risk360) page. The following field appears when you enable this field:
- **Password Expires After**: Enter the number of days you want passwords to be valid for admins. The default is 180 days. The days can range from 15 to 365.
When there are 15 days left, the Zscaler service reminds admins to change their password and shows how many days it remains valid for when they log in. If admins change their password before it expires, their new password is valid for the specified time. However, if their password expires, admins must register a new password to access the Risk360 Admin Portal. The new password can't be the same as the previous one. Also, the password used must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character.
[See image.](#password-exp)
- Click **Save** and [activate the change](/risk360/saving-and-activating-changes-risk360-admin-portal).
[]![Screenshot of the Password Management section on the Administrator Management page.](/downloads/zia/authentication-administration/administrator-role-management/configuring-password-expiration/Risk360-Password-expiration.png)
[]![Link to the ZIdentity Admin Portal on the Administrator Management Page](/downloads/risk360/administration-authentication/administrator-role-management/understanding-administrator-management-settings-risk360/Risk360-ZIdentity-Administration.png)