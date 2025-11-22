# Configuring Role-Based Administration
Source: https://help.zscaler.com/zia/configuring-role-based-administration
PDF: https://help.zscaler.com/pdf/com/en/1399706.pdf

Zscaler recommends adding roles before adding admins, because you will need to select a role for each admin that you create.
To configure [role-based administration](/zia/about-administrators):
- Add [admin roles](/zia/adding-admin-roles) or [SD-WAN partner API roles](/zia/adding-partner-admin-roles).
Admins can add [API roles](/zia/adding-api-roles) but these roles are never associated with an admin. Instead, an API role is used when configuring an OAuth 2.0 authentication server. The API role is used in the JWT token issued by the authorization server to define the role of the API application client.
To learn more, see [Securing ZIA APIs with OAuth 2.0](/zia/securing-zia-apis-oauth-2.0).
- Add [admins](/zia/adding-admins) or [SD-WAN partner API clients](/zia/adding-partner-admin-roles).
- (Optional) [Add auditors](/zia/adding-auditors).
For example scenarios of role-based administration, see [Role-Based Administration Configuration Examples](/zia/examples-role-based-administration).