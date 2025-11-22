# Enabling SCIM for Identity Management
Source: https://help.zscaler.com/unified/enabling-scim-identity-management
PDF: https://help.zscaler.com/pdf/com/en/1491496.pdf

Within the Admin Portal, you can set up [SCIM](/unified/about-scim) for identity management. Using SCIM allows you to quickly remove users from Private Applications when you delete them in your user directory.
Prior to enabling SCIM, you should configure an IdP for SAML authentication to use for single sign-on. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
Zscaler only supports SCIM version 2.0.
To enable SCIM:
- Go to **Administration **>** Identity **> **Private Access** > **IDP Configuration**.
- In the table, locate the IdP you want to modify and click the **Edit icon**.
- In the **Edit IdP Configuration** window, select **Enabled** for **SCIM Sync**.
- Copy the **SCIM Service Provider Endpoint**. This is used when configuring SCIM in the IdP.
-
Click **Generate New Token** to create a bearer token. The bearer token is a unique alphanumeric string that is used to authenticate SCIM requests.
The token does not display again after saving. Copy the token to your clipboard before saving.
- Complete the configuration to enable [SCIM](/unified/about-scim) on your IdP.
- (Optional) Select **Enabled** for **SCIM Attributes for Policy** if you want to allow SCIM attributes and SCIM groups from this IdP to be used when configuring [Access Policies](/unified/configuring-access-policies), [Client Forwarding Policies](/unified/configuring-client-forwarding-policies), and [Timeout Policies](/unified/configuring-timeout-policies).
When you first enable **SCIM Attributes for Policy**, an existing user's Client Connector connection also needs to be enabled for SCIM. Policies with SCIM criteria for this user are only evaluated after the user successfully reauthenticates. The reauthentication process does not impact ongoing connections to applications or the ability to use SAML as a criteria in policies for Private Applications.
You must enable this setting for to process SCIM attributes and SCIM groups in policy rules. This setting only applies if **SCIM Sync** is enabled as well. To learn more, see [Configuring an IdP for Single Sign-On](/unified/configuring-idp-single-sign).
- Click **Save**.
![Enabling SCIM for Policy](/downloads/zpa/identity-management/enabling-scim-identity-management/SCIM%20Attributes%20for%20Policy.png)
After SCIM is enabled, Zscaler checks if a user is present in the SCIM database. Based on this information, Zscaler decides if the user is allowed or blocked access to Private Applications. Customers need to ensure SCIM user sync is complete prior to enabling SCIM policies for these users, otherwise the users and policies are not recognized and evaluated. After **SCIM Sync** is enabled, Zscaler recommends waiting a minimum of 48 hours, or up to a week, before enabling SCIM policies. It can take up to several days for the IdP to completely sync all user information to Private Applications. Zscaler recommends that **SCIM Sync** be enabled in advance, prior to enabling **SCIM Attributes for Policy**.
Once you have completed these steps, you can go back into the IdP to configure it for identity management. The following configuration guides provide instructions on how to complete SCIM configuration within the IdP:
- [SCIM Configuration Guide for Microsoft Azure AD](/unified/scim-configuration-guide-microsoft-azure-ad)
- [PingFederate integration with Private Applications](https://docs.pingidentity.com/bundle/integrations/page/exl1587060854790.html)
- [SCIM Configuration Guide for Okta](/unified/scim-configuration-guide-okta)
Users may encounter a connection error in the Client Connector when enabling SCIM sync with Okta. Okta does not sync users to Private Applications in the Okta IdP before you enable SCIM. As a result, users do not initially appear in the SCIM user database when SCIM is enabled in Private Applications. Zscaler recommends the following to resolve the connection error in Client Connector:
- Enable PROVISION_OUT_OF_SYNC_USERS in Okta.
- Unassign and reassign all users and groups from Private Applications in Okta, and then wait for the sync to occur.