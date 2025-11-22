# Manually Adding SAML Attributes
Source: https://help.zscaler.com/zpa/manually-adding-saml-attributes
PDF: https://help.zscaler.com/pdf/com/en/1483646.pdf

This article describes how to manually add a SAML attribute. You can have up to 100 attributes in total. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
To manually add a SAML attribute:
- Go to **Authentication **>** User Authentication **>** SAML Management**.
- Click **Add SAML Attribute**.
The **Add SAML Attribute** window appears.
- In the **Add SAML Attribute **window:
- **Name**:** **Enter a name for the SAML attribute. This name is only for your reference and doesn't need to be identical to the corresponding entry in **SAML Attribute**. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **SAML Attribute**:** **Enter the corresponding SAML attribute name (for example, Group or Email Address). To find all of the available SAML attribute names, refer to the SAML JSON for your identity provider (IdP).
- **IdP Configuration**: Choose an [IdP configuration](/zpa/about-idps) from the drop-down menu.
![Add SAML Attribute Window in ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/saml-attributes/midp-about-samlattribute-new/zpa-addsamlattr.png)
- Click **Save**.
After saving, you can always return to the [SAML Attributes](/zpa/about-samlattributes#AboutSAMLAttrsPage) page and edit or delete attributes as necessary.
To learn more about using SAML attributes for defining policies, see [About Policies](/zpa/about-policies), [About Access Policies](/zpa/about-accesspolicy), and [About Timeout Policies](/zpa/about-reauthPolicy).