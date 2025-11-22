# Generating SAML Details
Source: https://help.zscaler.com/uvm/generating-saml-details
PDF: https://help.zscaler.com/pdf/com/en/1530692.pdf

Setting up single sign-on (SSO) account authentication requires generating a SAML Entity ID and Reply URL in the Zscaler Security Operations (SecOps) platform.
If you don't have access to this feature, contact your Zscaler Account team or Zscaler Support for assistance.
To generate SAML details:
- In the SecOps platform, click the **Profile **menu on the top right of the navigation bar.
- Select **Account Settings**.
- In the **Authenticate** section:
- **Email Domain**: Enter your organization's email domain including the suffix (e.g., `gmail.com`).
-
**Authentication Type**: Select SAML from the drop-down menu.
If the **Authentication Type **drop-down menu is disabled, enter an email domain name and save your changes to enable it.
- **Identity Provider Name**: Select the identity provider your organization uses (e.g., **Okta**).
- Click **Generate SAML Details**.
-
Copy the **Entity ID** and **Reply URL**.
[See image.](#copy-saml-details)
Use the Entity ID and Reply URL to configure your SSO, following the setup steps provided by your SSO provider.
[]**![mceclip2.png](/downloads/uvm/account-management/sso/okta-sso/mceclip2.png)
**