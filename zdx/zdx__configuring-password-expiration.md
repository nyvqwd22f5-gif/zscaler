# Configuring Password Expiration
Source: https://help.zscaler.com/zdx/configuring-password-expiration
PDF: https://help.zscaler.com/pdf/com/en/1374821.pdf

[Watch a video about Configuring Password Expiration in ZDX.](https://fast.wistia.net/embed/iframe/5llwj5nox8)
To provide additional security, admins have the option to enable password expiration for all admins logging in to the ZIA and ZDX Admin Portals. The latest password expiration settings configured in either the ZDX Admin Portal or the ZIA Admin Portal apply to both.
If you do not enable this feature, passwords will never expire.
Configuring Password Expiration
If this feature is enabled, a column showing if an admin's password has expired can be seen on the Administrators tab in Administration > Administration Management. To learn more about the Administrators page, see [About Administrators](/zdx/about-administrators).
To enable this feature:
- Go to Administration > Administrator Management.
- Click the **Administrator Management** tab.
- In the **Password Management** section:
-
**Password Expiration**: Enable passwords to expire for all admins in the ZIA and ZDX Admin Portals. If enabled, you can see a column showing if an admin's password has expired on the Administrators page (Administration > Administration Management). To learn more, see [About Administrators](/zia/about-administrators) (ZIA) and [About Administrators](/zdx/about-administrators) (ZDX). The following field appears:
-
**Password Expires After**: Enter the number of days you want passwords to be valid for ZIA and ZDX admins. The default is 180 days. The days can range from 15 to 365.
When there are 15 days left, the Zscaler service reminds admins to change their password and shows how many days it will remain valid for when they log in. If admins change their password before it expires, their new password will be valid for the specified time. However, if their password expires, admins must register a new password to access any features in the ZIA and ZDX Admin Portals. The new password can't be the same as the previous one. Also, the password used must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character.
[See image.](#img_password)
- Click Save and [activate the change](/zdx/saving-and-activating-changes-admin-portal).
[]
![Setting Password Expiration in ZDX ](/downloads/zdx/administration/admin-configuration/configuring-administrator-management-settings/ZDX-AdministratorManagement-1.png)