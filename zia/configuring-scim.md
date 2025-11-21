# Configuring SCIM
Source: https://help.zscaler.com/zia/configuring-scim
PDF: https://help.zscaler.com/pdf/com/en/1400831.pdf

This article covers how to enable [SCIM](/zia/about-scim) [provisioning](/zia/choosing-provisioning-and-authentication-methods) in the ZIA Admin Portal. If you wish to use SCIM for provisioning, you must also use [SAML](/zia/understanding-saml) for authentication and obtain and implement a SCIM client.
Prerequisites
Before configuring SCIM, ensure you have [added an IdP](/zia/adding-identity-providers) in the ZIA Admin Portal to establish a unique identifier. The identifier is included in the SCIM base URL.
Configuring SCIM
To configure SCIM in the ZIA Admin Portal:
- Go to **Administration **** **>** Authentication Settings**.
- Click the **Identity Providers** tab.
- Click the **Edit** icon for the identity provider (IdP) you want to enable SCIM provisioning for.
The **Edit IdP** window appears.
- In the **Edit IdP** window:
- **Enable SAML Auto-Provisioning**: Disable this option when enabling SCIM-based provisioning.
- **Enable SCIM Provisioning**: Enable to activate SCIM-based provisioning for users on the Zscaler service. To learn more, see [About SCIM](/zia/about-scim). SCIM provisioning isn't supported with Active Directory or OpenLDAP user repositories. If you want to migrate from directory synchronization to SCIM provisioning, enable **Disable Directory Sync & Enable SCIM Provisioning** on the [Authentication Profile page](/zia/about-authentication-profile). After enabling SCIM provisioning, the following fields appear:
- **Base URL**: Copy the Base URL for the SCIM server. You need this URL when configuring your IdP for SCIM provisioning. If you see multiple URLs, use the one with the new format:
https://scim.<Zscaler Cloud>/<Organization ID>/<IdP ID>/scim
If you are configuring Okta as the IdP for SCIM provisioning, Okta only requires the `/<Organization ID>/<IdP ID>/` parts of the base URL for the SCIM server.
The old SCIM Base URL marked as **(Deprecated)** will be removed in the future.
- **Bearer Token**: Copy the bearer token. It's a unique alphanumeric string that is used by the SCIM client to make authenticated API calls to the Zscaler SCIM server. You need this token when configuring your IdP for SCIM provisioning.
- **Generate Token**: Click to generate a new bearer token for security reasons. If you're generating a new bearer token for an existing SCIM configuration, ensure you update the token for your IdP.
[See image.](#seeimage-4)
- Click **Save** to exit the window.
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[]![Screenshot of the AUTO-PROVISIONING OPTIONS section in the Edit Identity Provider window.](/downloads/zia/authentication-administration/provisioning-authenticating-users/saml-scim/configuring-scim/ZIA-Provisioning-Options-Section.png)