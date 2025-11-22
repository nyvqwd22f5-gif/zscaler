# Configuring Role-Based Administration
Source: https://help.zscaler.com/unified/configuring-role-based-administration
PDF: https://help.zscaler.com/pdf/com/en/1488246.pdf

Zscaler recommends adding roles before adding admins, because you will need to select a role for each admin that you create.
To configure role-based administration:
- Add [admin roles](/unified/adding-admin-roles) or [SD-WAN partner API roles](/unified/adding-sd-wan-partner-api-roles).
Admins can add [API roles](/unified/adding-api-roles) but these roles are never associated with an admin. Instead, an API role is used when configuring an OAuth 2.0 authentication server. The API role is used in the JWT token issued by the authorization server to define the role of the API application client. To learn more, see [Securing Internet & SaaS APIs with OAuth 2.0](/unified/securing-internet-saas-apis-oauth-2-0).
- Add [admins](/unified/about-administrators) or [SD-WAN partner API clients](/unified/adding-sd-wan-partner-api-clients).
- (Optional) [Add auditors](/unified/adding-auditors).