# Configuring VDI Templates
Source: https://help.zscaler.com/cloud-branch-connector/configuring-vdi-templates
PDF: https://help.zscaler.com/pdf/com/en/1471711.pdf

This article provides information on how to configure a Virtual Desktop Infrastructure (VDI) template. To learn more, see [About VDI Templates.](/cloud-branch-connector/about-vdi-agent-templates)
To add a VDI template:
- Log in to the Zscaler Cloud & Branch Connector Admin Portal.
- Go to **Administration** > **VDI Templates**.
- Click **Add VDI Template**.
-
On the **Add VDI Template** page:
- **Name**: Enter a name for the template.
- **Description**: Enter a description for the template.
- **Auth Type**: Select **IdP** or **Hosted DB **as your authentication type.
The authentication type you select here must match the authentication type that Zscaler Internet Access (ZIA) is currently using.** **Select **IdP** only if ZIA is configured for Security Assertion Markup Language (SAML) authentication, and select **Hosted DB** only if ZIA is configured for Form-Based authentication. To learn more, see [Configuring the Default Authentication Profile](/zia/configuring-default-authentication-profile).
- If you select **IdP**, [enable SCIM in Zscaler Private Access (ZPA)](/zpa/about-scim). Use the same IdP in ZIA and ZPA. Then configure the following fields:
- **Domains**: Leave this field empty.
- **IdP Name**: Select an identity provider (IdP) name for the template. The list of IdPs in the drop-down menu is retrieved from the ZIA configuration. You can add new IdPs in the ZIA Admin Portal. To learn more, see [Adding Identity Providers](/zia/adding-identity-providers).
-
**System User**: Select a system user for the template. System users are defined in the ZIA configuration. The list of system users in the drop-down menu is retrieved from the ZIA configuration. You can add new system users in the ZIA Admin Portal. To learn more, see [About Users](/zia/about-users) and [Adding Users](/zia/adding-users).
System users are assigned to traffic leaving the VDI session that cannot be attributed to the current user. The system user attributes the traffic to a mechanism where policies are applied. Admins can then create security policies around the system user to permit, deny, or restrict where system traffic can reach. If you enable this feature, a default system user is created. In the ZIA logs, this user appears in the logging output as system-level traffic that the current user did not generate. You can configure a user on the IdP and select them as the system user. This arrangement is useful if you want different system users assigned based on the location of the VDI infrastructure. For example, some system users might have access to certain resources while others might not.
- If you select **Hosted DB**, select a **System User** for the template. The hosted database information is defined in the ZIA configuration. You can add new users to the hosted database in the ZIA Admin Portal. To learn more, see [Configuring the Hosted User Database](/zia/configuring-hosted-user-database).
[See image.](#AddVDITemplate)
-
Click **Submit**.
To copy the VDI provisioning URL and access token, click the VDI template that you created. If no token value is present, click the **Generate Token** button.
[]![The Add VDI Template page.](/downloads/cloud-branch-connector/zscaler-client-connector-vdi-management/configuring-vdi-templates/ConfiguringVDITemplate.png)