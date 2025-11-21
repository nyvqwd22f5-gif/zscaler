# Editing or Deleting an IdP Configuration
Source: https://help.zscaler.com/zpc/editing-or-deleting-idp-configuration
PDF: https://help.zscaler.com/pdf/com/en/1402951.pdf

You can edit or delete an IdP configuration you've configured.
Only the Default Super Administrator has the permission to edit or delete an IdP configuration. Deleting an IdP configuration may result in SSO login failure.
Editing an IdP Configuration
To edit an IdP configuration:
- Go to **Administration** > **Single Sign On**.
- On the **Single Sign On** page, click the **Edit** icon for the IdP that you wish to edit.
[See image.](#edit)
The **Edit IdP Configuration **window appears.
- In the **Edit IdP Configuration** window:
- **Name**, **Identity Provider Issuer**: Change the name or IP issuer.
- **Single sign-on URL**: Change the single-sing-on (SSO) URL.
- **Login Name Attribute**: Change the login name for the IdP.
- **Single Sign-On**: By default, SSO is enabled for all users in the tenant. Disable the SSO if required.
- **E****nable JIT**: Select to enable or disable just-in-time (JIT) provisioning.
- **Auto Update group based on IdP**: Select to allow the automatic update of user and user's group information from your IdP.
[See image.](#editwindow)
- Click **Save**.
Deleting an IdP Configuration
To delete an IdP configuration:
- Go to **Administration** > **Single Sign On**.
- On the **Single Sign On **page, click the **Delete** icon for the IdP that you wish to edit.
[See image.](#delete)
- A confirmation message appears. Click **Delete**.
[See image.](#deletewindow)
[![Click the Edit icon to edit the IdP configuration](/downloads/zpc/authentication/idp-configuration/editing-or-deleting-idp-configuration/zpc-sso-edit.png)
]
[![Edit the IdP configuration](/downloads/zpc/authentication/idp-configuration/editing-or-deleting-idp-configuration/zpc-edit-idp-window.png?1657865541)
]
[![Delete IdP](/downloads/zpc/authentication/idp-configuration/editing-or-deleting-idp-configuration/zpc-delete-idp-window.png)
]
[![Click the Delete icon to delete the IdP configuration](/downloads/zpc/authentication/idp-configuration/editing-or-deleting-idp-configuration/zpc-sso-delete.png)
]