# Active Directory with LDAP to SCIM Provisioning Migration Guide
Source: https://help.zscaler.com/zia/active-directory-scim-provisioning-migration-guide
PDF: https://help.zscaler.com/pdf/com/en/1486446.pdf

This guide contains information on how to migrate from Active Directory (AD) with [LDAP user synchronization](/zia/about-ldap-user-synchronization) to SCIM provisioning in the ZIA Admin Portal.
Prerequisites
Make sure the following prerequisites are met:
- Set the repository type to [Active Directory](/zia/synchronizing-user-data-active-directory-openldap) in the ZIA Admin Portal.
- Use [SAML](/zia/configuring-saml) for authentication and AD for provisioning.
- Ensure that the AD is syncing the database to Zscaler and the IdP.
When migrating from AD to SCIM, do not change the database type in the ZIA Admin Portal from Active Directory to Hosted DB. Doing so can cause all existing user and group mappings to be deleted and creates duplicate users with SCIM provisioning.
Migrating to SCIM
To migrate from AD to SCIM provisioning:
- Go to **Administration **>** Authentication Settings.**
-
Click **Sync Now **to perform a manual sync with the AD; this ensures that the Zscaler service has the latest database from the AD.
[See image.](#sync-now)
- (Optional) Ensure that you have the latest user data from the AD in your IdP application by performing a manual sync in the IdP application.
-
In the ZIA Admin Portal, go to **Administration **> **Authentication Settings** and enable **Disable Directory Sync & Enable SCIM Provisioning**.
[See image.](#disable-directory-sync)
- Go to the **Identity Providers **tab and click the **Edit **icon of the IdP you plan to use.
-
In the **Provisioning Options **section, click **Enable SCIM Provisioning** and copy the **Base URL **and **Bearer Token **as you need them when configuring SCIM in your IdP application.
[See image](#enable-scim)
Zscaler recommends that you disable **Enable Saml Auto-Provisioning **when using SCIM provisioning**.**
-
Using the information you copied in step 5, [configure SCIM provisioning in your selected IdP application](/zia/authentication-administration/provisioning-authenticating-users/saml-scim).
After the IdP is configured, ensure that users syncing from the IdP match those on the [Users page](/zia/about-users) in the ZIA Admin Portal.
User Management in the ZIA Admin Portal remains read-only because the **User Repository Type** is set to **Active Directory**.
Make sure that you do not disable the **Disable Directory Sync & Enable SCIM Provisioning **option or change the repository types. If you are using Zscaler Authentication Bridge (ZAB), it is safe to disable the ZAB VM if there are no provisioning issues observed after a few days.
If you need to revert from SCIM to AD provisioning:
- Go to **Administration **> **Authentication Settings **> **Identity Providers** and click the **Edit **icon for the IdP you used.
- Disable the **Enable SCIM Provisioning **option.
- On the **Default Settings **page, disable the **Disable Directory Sync & Enable SCIM Provisioning **option.
- In the IdP application that you previously configured SCIM for, disable the SCIM configuration.
- In the ZIA Admin Portal, go to **Administration **>** Authentication Settings **> **Default Settings**, and click **Sync Now.**
[]![Image of the Sync Now button ](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/active-directory-scim-provisioning-migration-guide/ZIA-ad-scim-sync-now.png)
[]
![Image of the Disable Directory Sync... Option](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/active-directory-scim-provisioning-migration-guide/ZIA-ad-scim-disable-directory-sync.png)
[]![Image of the Enable SCIM Provisioning Option](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/active-directory-scim-provisioning-migration-guide/ZIA-enable-scim.png)