# Configuring SAML for Single Sign-On
Source: https://help.zscaler.com/deception/configuring-saml-single-sign
PDF: https://help.zscaler.com/pdf/com/en/1531354.pdf

Zscaler recommends that you use the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal) to configure primary and secondary [external identity providers (IdPs)](/zidentity/about-external-identity-providers). ZIdentity supports both SAML and OpenID configurations. Contact Zscaler Support to subscribe to ZIdentity.
You can configure the Zscaler Deception Admin Portal as a service provider (SP) and use SAML single sign-on (SSO) for authenticating and provisioning users.
Before configuring SAML for SSO, make sure you download the SAML identity provider (IdP) metadata XML file.
Configuring SAML for SSO
To configure a SAML-based SSO:
- Go to **Settings** > **Users & Roles** > **IdP Providers**.
-
Click **Add Provider**, and select **SAML** from the drop-down menu.
[See image.](#add-provider-option)
-
In the **SAML Provider Details** window:
- **Name**: Enter a name for the SAML integration.
- **Enabled**: Select to enable the SAML provider.
- **Encryption**: Enable to allow the IdP to send the SAML assertion in an encrypted format. Enable only if the IdP supports encryption.
- **Sign GET Request**: Enable to allow the Deception Admin Portal to send a signed SAML request to the IdP. Enable only if the IdP supports signed requests.
- **Use Dedicated Certificate**: Enable to allow the Deception Admin Portal to create a long-lived self-signed certificate and use it for the SAML provider instead of the admin portal's certificate.
The Deception Admin Portal uses a Let's Encrypt certificate, which has a 90-day expiration period. Zscaler recommends that you enable **Use Dedicated Certificate** to generate a long-lived certificate that is dedicated to SAML authentication.
-
Click **Upload** to upload the IdP SAML 2.0 Metadata XML file.
[See image.](#saml-provider-details)
-
Click **Save**.
The SAML provider is added to the table.
[See image.](#saml-added)
To complete the IdP configuration, you need the SAML setup instructions and encryption certificate.
[]Obtaining SAML Setup Instructions
To view the SAML setup instruction details and download the encryption certificate:
- Go to **Settings** > **Users & Roles** > **IdP Providers.**
- Select a SAML provider, and click **Edit**.
-
In the **SAML Provider Details** window, scroll down to the **Setup Instructions** section to:
- View the **Service Provider Entity ID**.
- View the **Service Provider Assertion URL**.
- Download the encryption certificate.
- Download the XML file.
[See image.](#saml-set-up-instructions)
After the IdP is configured, you can sign in using the SAML authentication integration to test the configuration.
[See image.](#idp-login-page)
[]Configuring Group-Based SAML Login
Zscaler Deception allows you to create new users and assign them a role if their SAML responses contain one or more predefined group attributes. Group mapping is cumulative. If a user belongs to multiple groups, then the user is assigned roles that match each one of the groups.
While configuring group-based SAML login, if you are not a part of any group, then your roles are revoked, and you can lock yourself out during authentication. Make sure that you have a second account with super admin privileges via a username and password, and don't use SAML to log in to that account until you are done testing the integration.
To configure SAML group provisioning:
- Go to **Settings **> **User & Roles** > **IdP Providers**.
- Select the SAML configuration that you have configured for your IdP.
- In **SAML Provider Details**, under the **Group-Based SAML Login** section:
- **Auto Create User**: Enable to make sure the users in the specified groups are automatically created in the Deception Admin Portal.
- **SAML Response Group Attribute**: Enter the name of the attribute that is used for the group name in the SAML response (this value depends on your identity provider).
- **SAML Response Name Attribute**: Enter the name of the attribute used for the user name in the SAML response (this value depends on your identity provider).
-
Click **Add** to add a group and select the roles for each group.
- Enter the **Group Name** as seen in the SAML response.
- Select one or more **Roles** to assign to a user who has the corresponding group in the SAML response.
[See image.](#group-based-saml-login)
- Click **Save**.
If a user is created using the SAML group-based login feature, the ability to log in with a username and password is disabled by default.
If a user does not have a matching group, then the user does not have any roles and cannot log in.
Every time a user signs in using SAML, the role is updated regardless of if the user was created manually or automatically using the group-based SAML login.
[]![Add an IdP provider](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-add-provider-2.png)
[]![Configure SAML provider details](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-saml-details.png)
[]![IdP added](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-saml-added-1.png)
[]![Obtain SAML set up instructions](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-saml-set-up-instructions.png)
[]![Sign In Page](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-idp-button-sign-in-page.png)
[]![Configure Group Based SAML Login](/downloads/deception/authentication/saml-configuration/configuring-saml-single-sign/zscaler-deception-group-based-saml-admin-portal.png)