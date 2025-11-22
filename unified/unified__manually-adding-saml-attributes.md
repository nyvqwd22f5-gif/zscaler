# Manually Adding SAML Attributes
Source: https://help.zscaler.com/unified/manually-adding-saml-attributes
PDF: https://help.zscaler.com/pdf/com/en/1491331.pdf

This article describes how to manually add a SAML attribute. You can have up to 100 attributes in total. For a complete list of ranges and limits per feature, see [Ranges & Limitations](/unified/ranges-limitations#private-applications).
To manually add a SAML attribute:
- Go to **Administration** > **Identity** > **Private Access **> **SAML Attributes**.
- Click **Add SAML Attribute**.
The **Add SAML Attribute** window appears.
- In the **Add SAML Attribute **window:
- **Name**:** **Enter a name for the SAML attribute. This name is only for your reference and doesn't need to be identical to the corresponding entry in **SAML Attribute**. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **SAML Attribute**:** **Enter the corresponding SAML attribute name (for example, Group or Email Address). To find all of the available SAML attribute names, refer to the SAML JSON for your identity provider (IdP).
- **IdP Configuration**: Choose an [IdP configuration](/unified/about-idp-configuration) from the drop-down menu.
![Add SAML Attribute Window ](/downloads/zpa/documentation-knowledgebase/saml-attributes/midp-about-samlattribute-new/zpa-addsamlattr.png)
- Click **Save**.
After saving, you can always return to the [SAML Attributes](/unified/about-saml-attributes) page and edit or delete attributes as necessary.
To learn more about using SAML attributes for defining policies, see [About Access Policy](/unified/about-access-policy), and [About Timeout Policy](/unified/about-timeout-policy).