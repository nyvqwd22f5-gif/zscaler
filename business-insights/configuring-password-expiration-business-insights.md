# Configuring Password Expiration in Business Insights
Source: https://help.zscaler.com/business-insights/configuring-password-expiration-business-insights
PDF: https://help.zscaler.com/pdf/com/en/1473141.pdf

To provide additional security, you can enable password expiration for all admins logging in to the Business Insights Admin Portal.
If you don't enable this setting, the admins' passwords never expire. The service doesn't enforce password expiration for SAML-based admins.
If you are subscribed to the ZIdentity service, the Administrator Management page shows a link to the ZIdentity Admin Portal. You can manage your admins from the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal). To learn more, see [What Is ZIdentity?](/zidentity/what-zidentity)
[See image.](#zidentity-administration)
To configure password expiration for admins:
- Go to** Administration** > **Administrator Management**.
- Click the** Administrator Management** tab.
- In the **Password Management** section, enable **Password Expiration** to allow passwords to expire for all admins in the Business Insights Admin Portal. If enabled, a column showing if an admin's password has expired appears on the [Administrators](/business-insights/about-administrators-business-insights) page.
The **Password Expires After** field appears when you enable the setting. Enter the number of days you want passwords to be valid for admins. The default is 180 days. The days can range from 15 to 365. When there are 15 days left, the Zscaler service reminds admins to change their password and shows how many days it remains valid for when they log in. If admins change their password before it expires, their new password is valid for the specified time. However, if their password expires, admins must register a new password to access the Business Insights Admin Portal. The new password can't be the same as the previous one. Also, the password used must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character.
[See image.](#password-exp)
- Click **Save**.
[]![Password Management section on the Administrator Management page](/downloads/business-insights/authentication-administration/configuring-password-expiration-business-insights/Business-Insights-Password-Expiration-Settings.png)
![Administrator Management page for ZSLogin-enabled tenants](/downloads/business-insights/authentication-administration/configuring-advanced-configuration-admins/Business-Insights-ZIdentity-Administration.png)
[]