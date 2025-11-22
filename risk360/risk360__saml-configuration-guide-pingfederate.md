# SAML Configuration Guide for PingFederate
Source: https://help.zscaler.com/risk360/saml-configuration-guide-pingfederate
PDF: https://help.zscaler.com/pdf/com/en/1508781.pdf

This guide illustrates how to configure Ping Identity's PingFederate server as the identity provider (IdP) for Risk360.
Risk360 currently only supports IdP-initiated SSO.
Prerequisites
Ensure that you have the following before you start configuring PingFederate as your IdP:
- [PingFederate Admin Account](http://docs.pingidentity.com/r/en-us/pingfederate-112/help_administrativeaccountstasklet_administrativeaccountsstate)
- [PingFederate Server with the Zscaler Internet Access (ZIA) Connector Add-On](#PingFedAddOn)
- [Export PingFederate Signing Certificate for Zscaler Services](#ExportPingFedSigningCertificate)
- [Zscaler Cloud Name](#ZDX-CloudURL)
- [Risk360 XML Metadata](#ZDX-XML-Metadata)
[]To download the Zscaler Internet Access Connector:
- Go to the [PingFederate Server Add-Ons](https://www.pingidentity.com/en/resources/downloads/pingfederate.html) page.
-
Under **SaaS Connectors**, download **Zscaler Internet Access Connector 1.1**.
[See image.](#PingFederateZIAConnector)
- Unzip the connector folder to extract the `pf-zscaler-zia-quickconnection-1.1.jar` file.
- Add the `pf-zscaler-zia-quickconnection-1.1.jar` file to the **PingFederate** > **Server** > **default** > **deploy **folder.
[]
[]When configuring IdPs, the following information might be required for Risk360:
- ACS URL for Risk360 cloud:
https://admin.zscalerrisk.net/idp-auth
- Download the SAML SSL certificate from the IdP. It must be in Base64-encoded PEM format.
- Entity ID for Risk360 cloud:
admin.zscalerrisk.net
If you have a domain defined on multiple Zscaler Internet Access (ZIA) clouds, enter the ZIA cloud name that is associated with Risk360 in the **Relay State** field (e.g., `zscalertwo.net`) for each application.
You must also create admin accounts for your organization's admins. To learn more, see [Adding Risk360 Admins](/risk360/adding-admins-risk360).
[]
To download the XML Metadata from the Risk360 Admin Portal:
- Sign in to the Risk360 Admin Portal.
- Go to **Administration** > **Administrator Management** > **Administrator Management**.
- Click **Download**.
[See image.](#download-xml-data)
Remember where you saved the metadata as you will upload it for creating a service provider (SP) connection.
To learn more, see [Configuring SAML for Risk360 Admins](/risk360/configuring-saml-admins-risk360).
[]To export your PingFederate signing certificate on the PingFederate admin console:
- Log in to your PingFederate administrative console.
-
Go to **Security** > **Signing & Decryption Keys & Certificates**.
[See image.](#PingFed-Security)
- Click **Select Action** on the certificate you want to use.
-
Click **Export**.
[See image.](#PingFed-Security-SelectAction-Export)
-
On the **Export Certificate** tab, click **Next**.
[See image.](#PingFed-Security-CertificateOptions)
-
On the **Export & Summary** tab, click **Export**.
[See image.](#PingFed-Security-ExportCertificate)
- Rename the downloaded certificate's extension to `.pem`.
- Save this certificate for when you are ready to add PingFederate as an IdP in Risk360.
Configuring SAML SSO on Zscaler Services
You need to register PingFederate as an IdP in Zscaler services for SAML Single Sign-On (SSO).
To add PingFederate as an IdP in Risk360:
- If you haven't renamed your certificate from the prerequisites step, rename your certificate's extension to `.pem`.
- Upload your IdP signing certificate as described in [Configuring SAML SSO for Risk360 Admin.](/risk360/configuring-saml-admins-risk360)
- Click **Save**.
Configuring a Service Provider Connection on PingFederate
To configure a service provider (SP) connection on the PingFederate administrative console:
[]
- Verify the SAML 2.0 entity ID:
- Go to **System** > **Server** > **Protocol Settings** > **Federation Info**.
- In the **SAML 2.0 Entity ID** field, enter a name for PingFederate to use when SAML applications need to identify it.
- Click **Save**.
- Create an SP connection:
- Use the **SP Connections** shortcut or go to **Applications **>** Integration** > **SP Connections**.
-
Click **Create Connection**.
[See image.](#PingFederate-SPConnection-CreateConnection)
- In the Create Connection wizard, configure the following sections:
- [Connection Template](#PingFederate-SPConnection-ConnectionTemplate)
- [Connection Type](#PingFederate-SPConnection-ConnectionType)
- [Connection Options](#PingFederate-SPConnection-ConnectionOptions)
- [General Info](#PingFederate-SPConnection-GeneralInfo)
- [Browser SSO](#PingFederate-SPConnection-BrowserSSO)
- [Credentials](#PingFederate-SPConnection-Credentials)
Initiate SSO
Risk360 and PingFederate support IdP- and Service Provider-initiated single sign-on. PingFederate's documentation provides information for invoking IdP-initiated SSO. To learn more, refer to the [PingFederate documentation](https://docs.pingidentity.com/r/en-us/pingfederate-112/idp_endpoints).
When using IdP-initiated SSO, Risk360 requires the cloud name (e.g., `zscalerthree.net`) passed through the SAML Relay State if you have a domain defined on multiple ZIA clouds. Zscaler recommends using the SAML Relay State in a single ZIA cloud deployment to avoid any disruption if a second ZIA cloud is added in the future. PingFederate supports this by passing the necessary Relay State value by using the TargetResource query parameter in the `/idp/startSSO.ping` application endpoint.
For example (the green text shows where to insert the ZIA Cloud Name associated with Risk360):
https://{PingFederate hostname}/idp/startSSO.ping?PartnerSpId={Risk360 Connection ID}&TargetResource=zscalerthree.net
[]![Start the Create SP Connection Wizard](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-CreateConnection-0.png)
[]
- Select **Use a template for this connection**.
- For **Connection Template**, select **Zscaler ZIA Connector**.
- For **Metadata File**, upload your metadata file.
- Click **Next**.
![SP Connection Connection Template](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-CreateConnection-SelectNext.png)
[]Ensure the **Browser SSO Profiles** checkbox is selected, then click **Next**.
![SP Connection Connection Type](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-CreateConnection-ConnectionType-1-Next.png)
[]Ensure the **Browser SSO** checkbox is selected, then click **Next**.
![Connection Options](/downloads/tech-pubs-drafts/zdx-draft-articles/zdx-admin-saml-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-CreateConnection-ConnectionOptions-0.png)
- []**Partner's Entity ID (Connection ID)**: Verify the partner's entity ID.
- **Connection Name**: Enter a connection name. This might be pre-populated and can be revised to your preference.
-
**Base URL**: Verify the base URL. You must append `:443` to the end of your base URL.
For example, if your base URL is `https://login.zscaler.net`, then your new base URL is `https://login.zscaler.net``:443`
- Click **Next**.
![Configure General Info](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-CreateConnection-GeneralInfo-Enter.png)
- []On the **Browser SSO** page, click **Configure Browser SSO.**
- On the **Assertion Creation **page, click **Configure Assertion Creation**.
- On the **Authentication Source Mapping** page, click **Map New Authentication Policy**.
-
On the **Authentication Policy Contract** tab, select **subject** for the **Authentication Policy Contract** field.
This allows the authentication to be connected to policies. If required, you can configure the contract attribute that is applicable to you.
-
Click **Next**.
[See image.](#pingfederate_browsersso_authenticationpolicycontract)
- On the **Mapping Method **page, select **Retrieve Additional Attributes from a data store -- includes options to use alternate data stores and/or a failsafe mapping**.
-
Click **Next**.
[See image.](#pingfederate_browsersso_mappingmethod)
- On the **Attribute Sources & User Lookup** tab, click **Add Attribute Source**.
- On the **Data Store** page:
- **Attribute Source Description**: Enter a description for the Attribute Source.
- **Active Data Store**: Select **PingDirectory**.
-
Click **Next**.
[See image.](#pingfederate_browsersso_mappingmethod_datastore)
-
On the **LDAP Directory Search** page:
- **Base DN**: Enter `ou=Zscaler Users,dc=example,dc=com`.
- **Search Scope**: Select **Subtree** from the drop-down menu.
- **Attributes to return from the search**:
- **Root Object Class**: Select **<Show All Attributes>**.
- **Attribute**: Select **mail**.
- After **mail** is added, click **Add Attribute** next to it.
[See image.](#pingfederate_mappingmethod_LDAPSearch)
- Click **Next**.
- On the **LDAP Filter** page, for the **Filter** field, enter `uid=${subject}`.
-
Click **Next**.
[See image.](#pingfederate_mappingmethod_LDAPFilter)
- On the **Attribute Contract Fulfillment** page:
- **SAML_Subject**: Select **LDAP (pd)**.
- **Value**: Select **mail**.
-
Click **Next**.
[See image.](#pingfederate_mappingmethod_AttributeContactFulfillment)
- On the **Summary** page, click **Done **after you verify your attribute source configuration.
-
On the **Attribute Sources & User Lookup** page, click **Next** after you verify your data store to supply user information in the SAML assertion to the SP.
[See image.](#pingfederate_mappingmethod_AttributeSourcesUserLookup)
- On the** Failsafe Attribute Source** page, select **Abort the SSO Transaction**.\
-
Click **Next**.
[See image.](#pingfederate_failsafeattributesource)
-
Click **Done** after reviewing your **Authentication Source Mapping** configuration.
[See image.](#pingfederate_assertioncreation_authenticationsourcemapping)
- Click **Done** after reviewing your **Summary**.
-
On the **Assertion Creation** page, click **Next**.
[See image.](#pingfederate_assertioncreation)
-
On the **Protocol Settings** page, click **Next**.
[See image.](#pingfederate_protocolsettings)
-
On the **Summary** page, click **Done** to save your configuration.
[See image.](#pingfederate_browsersso_summary)
-
[]On the **Credentials** page, click** Configure Credentials**.
[See image.](#pingfederate_credentials)
-
Select your Signing Certificate.
Click **Done**.
[See image.](#pingfederate_credentials_select)
[]
![Select ZIA Connector](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-Add-Ons-ZIAConnector.png)
[]![Select Signing & Description Keys & Certificates](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-Security-Signing%26DecriptionKeys%26Certificates-Select.png)
[]![Select a certificate to export.](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-Security-SelectAction-Export.png)
[]![Click Next to confirm Certificate Options](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-Security-CertOptions-Next.png)
[]
[![Export your Export Certificate](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-Security-ExportCert-Select.png)
]
[]
[![Select Authentication Policy Contract](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-AuthenticationPolicyContractPage-Select.png)
]
[]
[![Mapping Method](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-MappingMethod-Select.png)
]
[]
[![Mapping Method - Data Store](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-MappingMethod-DataStore.png)
]
[]
[![Search for mail attribute](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-MappingMethod-LDAP-Search.png)
]
![Added mail attribute](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-MappingMethod-LDAP-AddAttribute.png)
[]
[![Enter the LDAP Filter](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-MappingMethod-LDAPFilter.png)
]
[]
[![Attribute Contract Fulfillment - Select your SAML_Subject](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-AttributeContractFulfillment.png)
]
[]
[![Attribute Sources & User Lookup](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-AttributeSourcesUserLookup.png)
]
[]
[![Failsafe Attribute Source](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-FailsafeAttributeSource.png)
]
[]
[![Authentication Source Mapping](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-AssertionCreation-AuthenticationSourceMapping.png)
]
[]
[![Assertion Creation](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-AssertionCreation.png)
]
[]
[![Protocol Settings](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-ProtocolSettings.png?1684461701)
]
[]
[![Summary of Browser SSO](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnections-BrowserSSO-Summary.png)
]
[]
[![Select Configure Credentials](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnection-Credentials-ConfigureCredentials.png)
]
[]
[![Select your credentials](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-SPConnection-SelectCredentials-0.png)
]
[]![Download XML Metadata.](/downloads/zdx/administration/zdx-admin-saml-scim-configuration-guide-pingfederate/ZDX-PingFederate-ZDX-SAML%20Authentication.png)