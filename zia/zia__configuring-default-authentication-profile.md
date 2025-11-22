# Configuring the Default Authentication Profile
Source: https://help.zscaler.com/zia/configuring-default-authentication-profile
PDF: https://help.zscaler.com/pdf/com/en/1458901.pdf

In the Authentication Profile section on the Default Settings page (Administration > Authentication Settings > Default Settings), you can:
- [Configure a User Repository](#directory)
- [Disable Directory Sync & Enable SCIM Provisioning](#disable-directory-enable-scim)
- [Configure the Authentication Frequency](#authentication-frequency)
- [Configure an Authentication Type](#saml)
- [Synchronize the Directory](#sync)
- [Configure a One-Time Token or One-Time Link](/zia/configuring-one-time-token-or-one-time-link)
![Authentication Profile section on the Default Settings page](/downloads/zia/authentication-administration/user-management-authentication-settings/configuring-default-authentication-profile/ZIA-configuring-default-authentication-profile.png)
[]**User Repository Type**: Choose one of the following repositories and configure accordingly.
- [Hosted User Database (Hosted DB)](/zia/how-do-i-configure-hosted-user-database)
- [Active Directory](/zia/synchronizing-user-data-active-directory-openldap)
- [OpenLDAP](/zia/synchronizing-user-data-active-directory-openldap)
Active Directory (AD) and OpenLDAP user repositories are only available when SCIM provisioning is disabled and SAML auto-provisioning is enabled for only one [identity provider (IdP)](/zia/about-identity-providers).
If you are configuring a Zscaler Authentication Bridge (ZAB), see [Deploying a Zscaler Authentication Bridge](/zia/how-do-i-deploy-zscaler-authentication-bridge) to learn more about configuring the directory and deploying the ZAB.
[]**Disable Directory Sync & Enable SCIM Provisioning**: This setting only appears if you choose **Active Directory** or **OpenLDAP** for the **User Repository Type** and **SAML** for the **Authentication Type**. Enable this setting to disable directory synchronization for the user repository type so that you can enable SCIM provisioning or SAML auto-provisioning (if you have multiple [IdPs](/zia/about-identity-providers)). Use this setting to migrate from directory synchronization to SCIM provisioning.
If you enable this setting:
- The Zscaler service disables directory synchronization. Therefore, the **Authentication Wizard** and **Advanced Configuration** options for AD and OpenLDAP disappear, as well as the **Directory Synchronization **section.
- You can enable SCIM provisioning or SAML auto-provisioning for your IdPs.
- The** Formed-Based** option for **Authentication Type** becomes unavailable.
[]**Authentication Frequency**: Choose how often users are required to authenticate to the Zscaler service. These options don't apply to users with Zscaler Client Connector.
- **Daily**:** **Authentication expires between 12 to 24 hours from the login time, depending on the time the user authenticated the day before.
-
**Only Once**: This is the default authentication interval. After users have logged in, they do not need to authenticate again as long as the [cookie](/zia/about-zscaler-cookies) is saved in the browser or as an Adobe Flash object. (Typically, the cookie expires in about two years.) However, to log out of Zscaler, users must log out of the service explicitly or delete the cookie from their browser.
Zscaler recommends choosing **Only Once **as your authentication frequency. To learn more, see [About User Authentication Frequency](/zia/why-does-zscaler-recommend-configuring-authentication-frequency-be-only-once).
- **Once Per Session**:** **Authentication expires after the user closes the browser.** **In this case, no cookie is saved.
- **Custom**:** **Customize your authentication interval.
- **Custom Authentication Frequency (days)**:** **Enter the number of days, between 1 and 180 inclusive. Authentication is requested when the user's cookie expires.
[]**Authentication Type**: Choose how users authenticate into the Zscaler service. Zscaler recommends using SAML Single Sign-On (SSO).
-
**Form-Based**: Users log in to the Zscaler service with their credentials. See [Configuring the Hosted User Database](/zia/how-do-i-configure-hosted-user-database).
- **Password Strength**: Choose the required password strength.
- **None**: Choose to place no restriction on the strength or complexity of the passwords. Not recommended. Weak passwords can be easily compromised.
- **Medium**: Choose to require users to set passwords that are at least eight characters long and that contain at least one non-alphabetic character. This is the default.
-
**Strong**: Choose to require users to set passwords that are at least eight characters long and that contain at least one digit, one capital letter, and one special character.
Only ASCII characters are allowed for the password.
- **Password Expiration**: Choose the duration after which users must change their passwords. The default is **Never**, but Zscaler strongly recommends setting the duration higher. Old passwords allow access to your system by people no longer in your organization.
If you're using AD or OpenLDAP user repositories, you must disable **Disable Directory Sync & Enable SCIM Provisioning** to choose **Form-Based** authentication.
-
**SAML**:** **Users authenticate with SAML SSO. You must configure at least one IdP to enable SAML. To learn more, see [Configuring SAML](/zia/configuring-saml). Also, if the Zscaler service provider (SP) signing SSL certificate is about to expire or expired, the following field appears:
- **SP SSL Certificate Expiration Date**: Displays the expiration date for the SAML signing certificate of the SP. A **Caution** icon appears if the certificate expires within 30 days.
[See image.](#SAML-Certificate-Caution)
If you're using AD or OpenLDAP user repositories, you must disable SCIM provisioning and enable SAML auto-provisioning for only one [IdP](/zia/about-identity-providers) to choose **SAML** authentication.
[]![Screenshot of the Caution icon and message for the SAML Certificate Expiration Date field](/downloads/zia/authentication-administration/user-management-authentication-settings/managing-default-authentication-profile/zia-saml-certificate-expiration_date-caution-message.png)
[]If you are using Active Directory (AD) or OpenLDAP, you can click **Sync Now** to synchronize the Zscaler service with the AD or OpenLDAP server.
![Screenshot of the Sync Now button](/downloads/zia/authentication-administration/user-management-authentication-settings/managing-default-authentication-profile/Directory%20Synchronization.png)
Depending on the [Synchronization Frequency](/zia/configuring-zscaler-service-synchronize-data) you configured for your AD or OpenLDAP server, under **Last Synchronization Time**, you can view the time when the Zscaler service last synchronized with the AD or OpenLDAP server.