# Importing SAML Attributes
Source: https://help.zscaler.com/zpa/importing-saml-attributes
PDF: https://help.zscaler.com/pdf/com/en/1483826.pdf

Within the ZPA Admin Portal, you can have up to 100 SAML attributes. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To import SAML attributes:
- Go to **Authentication **>** User Authentication **>** IdP Configuration**.
- []In the **IdP Configuration** page, expand the configuration for the identity provider (IdP) you want to import SAML attributes from.
- Click **Import**.
![Expanded IdP Configuration and Import SAML Attributes button](/downloads/zpa/documentation-knowledgebase/authentication/saml-attributes/importing-saml-attributes/Import%20update_0.png)
- You are redirected to your IdP's login page. Log in with your credentials. After login, the **Import SAML Attributes** page is displayed.
- The **Import SAML Attributes** page only displays new attributes that can be imported, as well as the SAML JSON from the IdP. Customize the entries in the **Name **column as necessary. These names are only for your reference and don't need to be identical to the corresponding entry in the **SAML Attribute Name **column.
![Import SAML Attributes Page in ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/saml-attributes/importing-saml-attributes/zpa-importsamlattrspage.png)
- Click** Save**.
After saving, you can always return to the [SAML Attributes](/zpa/about-samlattributes#AboutSAMLAttrsPage) page and edit or delete attributes as necessary.
To learn more about using SAML attributes for defining policies, see [About Policies](/zpa/about-policies), [About Access Policies](/zpa/about-accesspolicy), and [About Timeout Policies](/zpa/about-reauthPolicy).