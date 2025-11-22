# Configuring Automatic Username Population for IdP Authentication
Source: https://help.zscaler.com/zscaler-client-connector/configuring-automatic-username-population-idp-authentication
PDF: https://help.zscaler.com/pdf/com/en/1349736.pdf

You can configure Zscaler Client Connector to automatically populate the username field for your organization’s IdP login form using either JavaScript or the `login_hint` parameter.
To configure automatic username population:
- In the Zscaler Client Connector Portal, go to **Administration**.
- In the left-side navigation, go to** Client Connector Support**.
- On the **App Supportability** tab, enable **Pre-Populate Client Connector Username**.
-
Select from the following options:
- **Using Javascript**: Use this option to have Zscaler Client Connector use Javascript in the IdP page during the SAML workflow to autofill the username field for your organization’s IdP login form.
- **Using login_hint SAML attribute**: Use this option to have Zscaler Client Connector send the login_hint parameter to both Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA) during authentication. ZIA and ZPA pass the `login_hint` parameter to the IdP as a SAML Subject (`NAMEID`) to pre-populate the user name.
If you select both options, the `login_hint` parameter takes precedence over Javascript.
![Client-Connector-Pre-populate Username](/downloads/tech-pubs-drafts/client-connector-draft-articles/configuring-automatic-username-population-idp-authentication/client-connector-auto-populate-username-IDP.png)