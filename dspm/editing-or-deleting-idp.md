# Editing or Deleting an IdP
Source: https://help.zscaler.com/dspm/editing-or-deleting-idp
PDF: https://help.zscaler.com/pdf/com/en/1479186.pdf

You can edit or delete an [IdP configuration](/dspm/adding-identity-providers) you've configured.
Deleting an IdP configuration might result in SSO login failure.
Editing an IdP Configuration
To edit an IdP configuration:
- Go to **Administration** > **Single Sign-On**.
-
On the **Single Sign-On** page, click the **Edit** icon for the IdP that you want to edit.
[See image.](#editicon)
-
In the **Edit IdP Configuration** window, change the following fields as required.
- **Name**, **Identity Provider Issuer**: Change the name or IP issuer.
- **Single Sign-On**: By default, SSO is enabled for all users in the tenant. Disable SSO if required.
- **Single Sign-On URL**: Change the SSO URL.
- **Enable JIT**: Select to enable or disable just-in-time (JIT) provisioning.
- **Auto Update group based on IdP**: Select to allow the automatic update of user and user's group information from your IdP.
[See image.](#editwindow)
- Click **Save**.
Deleting an IdP Configuration
To delete an IdP configuration:
- Go to **Administration** > **Single Sign-On**.
-
On the **Single Sign-On **page, click the **Delete** icon for the IdP that you want to edit.
[See image.](#deleteicon)
-
A confirmation message appears. Click **Delete.**
[See image.](#deletewindow)
[]![Edit the IdP configuration](/downloads/dspm/authentication/idp-configuration/editing-or-deleting-idp/dspm-sso-edit.png)
[]![Edit IdP configuration window](/downloads/dspm/authentication/idp-configuration/editing-or-deleting-idp/dspm-edit-idp-window.png)
[]![Delete the configured IdP](/downloads/dspm/authentication/idp-configuration/editing-or-deleting-idp/dspm-sso-delete.png)
[]![Delete the configured IdP](/downloads/dspm/authentication/idp-configuration/editing-or-deleting-idp/dspm-delete-idp-window.png)