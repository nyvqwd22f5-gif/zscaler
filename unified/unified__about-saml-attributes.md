# About SAML Attributes
Source: https://help.zscaler.com/unified/about-saml-attributes
PDF: https://help.zscaler.com/pdf/com/en/1491311.pdf

You must configure SAML attributes to use them when defining policy rule criteria. For example, if you want to define users for your policies using email addresses, you must configure the users' email address SAML attribute in the Admin Portal. You can configure SAML attributes using one of the following methods:
- You can import your SAML attributes. This option requires that you generate a complete list of SAML attributes from your IdP, and then import that list into the Admin Portal. To learn more, see [Import SAML Attributes](/unified/importing-saml-attributes).
- You can manually add your SAML attributes. To learn more, see [Manually Adding SAML Attributes](/unified/manually-adding-saml-attributes).
Various authorization attributes can be provided by the IdP to Client Connector in the SAML assertion. The SAML assertion is used with every application access attempt to ensure that only authenticated users gain access.
SAML attributes provide the following benefits and enable you to:
- Define policies for least privileged access.
- Define a streaming policy when configuring a log receiver.
A hosted user database for provisioning is used, so user attributes within SAML assertions cannot be viewed within the Admin Portal. SAML assertions which contain these user attributes are encrypted and stored locally by Client Connector.
About the SAML Attributes Page
The SAML Attributes page is replaced by the Session Attributes page if you are subscribed to ZIdentity for users. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
[]On the SAML Attributes page (Administration** **> Identity > Private Access > SAML Attributes), you can do the following:
-
Add new SAML attributes by [importing the attributes](/unified/importing-saml-attributes) or [adding them manually](/unified/manually-adding-saml-attributes).
The **Add SAML Attribute **action is hidden if you are subscribed to ZIdentity for users. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- View a list of SAML attributes that were imported or added. For each attribute, you can see:
- **Name**: The name specified for the attribute within the Admin Portal when it was imported or added. This name is only for reference and might not be identical to the corresponding entry in the **SAML Attribute **column.
- **SAML Attribute **or **Session Attribute**: The SAML attribute as it is specified in the IdP. If you are subscribed to ZIdentity for users, then the **SAML Attribute** column is replaced with the **Session Attribute** column. To learn more, see [What Is ZIdentity?](/zslogin/what-zslogin)
- **IdP Name**: The name of the IdP configuration in the Admin Portal. This is the IdP where the attribute was imported or added from.
-
By default, **All** SAML attributes available are displayed. Using the drop-down menu you can filter the list to show attributes for a specific IdP.
The ability to filter the list to show attributes for a specific IdP is hidden if you are subscribed to ZIdentity for users.
- [Edit an existing SAML attribute.](/unified/editing-saml-attributes)
-
Delete a SAML attribute.
The **Delete **and** Edit **actions are hidden if you are subscribed to ZIdentity for users.
![Viewing the SAML Attributes page](/downloads/unified/administration/private-applications/identity/idp-device-configuration/saml-attributes/about-saml-attributes/unified-saml-attributes-page1.png)