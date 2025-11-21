# Configuration Guide for Ping Identity PingOne
Source: https://help.zscaler.com/zpa/configuration-guide-ping-identity
PDF: https://help.zscaler.com/pdf/com/en/1483766.pdf

This guide provides information on how to set up Ping Identity PingOne as a IdP for ZPA.
Zscaler and Ping Identity are technology partners. To learn more about integrating Zscaler and Ping Identity, see the [Zscaler and Ping Identity Deployment Guide](/zscaler-technology-partners/zscaler-and-pingone-deployment-guide).
Prerequisites
Ensure that you have the following:
- A Ping Identity PingOne account with admin privileges
- A ZPA account with an administrator role that allows you to add an IdP Configuration
Configuring PingOne for SSO
[]To configure PingOne as the IdP for ZPA user and admin SSO:
- Log in to the PingOne portal as an administrator and select **Applications**.
- In the **My Applications **tab, click **Add Application**.
[See image.](#ConfigPing1)
- Select **Search Application Catalog **from the drop-down menu.
[See image.](#ConfigPing2)
- In the search toolbar, search for "Zscaler Private Access". If you are:
- Configuring the IdP for ZPA user SSO, click the **Zscaler Private Access 2.0** application.
- Configuring the IdP for ZPA admin SSO, click the **Zscaler Private Access Administrator 2.0** application.
[See image.](#ConfigPing3_userSSO)
The following steps are identical for both applications.
- Click **Setup** to configure the ZPA application.
[See image.](#ConfigPing4_userSSO)
- For **SSO Instructions**, click **Continue to Next Step**.
[See image.](#ConfigPing5)
- For **Connection Configuration**:
- Log into the ZPA Admin Portal, [complete step 2 of the new IdP configuration procedure](/zpa/about-idp/new#AddIdPConfig_UserSSO). During this procedure, you must click **Download Metadata**. You can then **Pause** the configuration.
- Go back to the PingOne portal, for **Upload Metadata**, click **Select File**.
- Navigate to and upload the SP metadata file you downloaded previously.
[See image.](#ConfigPing6_userSSO)
The **ACS URL** and **Entity ID** fields will automatically be populated with the proper **Service Provider URL** and **Service Provider Entity ID** information, respectively. Also, the **Primary Verification Certificate** will have the proper certificate file (.cer) applied. The SP URL, Entity ID, and certificate provided are specific to your IdP.
- Click **Continue to Next Step**.
- For **Attribute Mapping**, map the identity bridge attributes to the attributes required by ZPA, then click **Continue to Next Step**.
[See image.](#ConfigPing7)
- For **PingOne App Customization**, enter the **Name** and **Description **for ZPA, then click **Continue to Next Step**.
[See image.](#ConfigPing8_userSSO)
- For **Group Access**, add user groups for ZPA as needed, then click **Continue to Next Step**.
[See image.](#ConfigPing_userSSO_grpAccess)
- For **Review Setup**:
- Scroll down to **SAML Metadata** and click **Download **to export the IdP metadata file.
[See image.](#ConfigPing9_userSSO)
- Review the **Identity Bridge Attribute** fields, then click **Finish**.
[See image.](#ConfigPing10)
After you have configured ZPA, it appears in your **My Applications** list.
[See image.](#ConfigPing11)
- Go to the ZPA Admin Portal and [complete the IdP configuration set up](/zpa/about-idp/new#IdP_BothSSO).
For PingOne, the IdP metadata file you upload to the ZPA Admin Portal will populate the **Name**, **Single Sign-On URL**, and **IdP Entity ID** fields. **ZPA (SP) SAML Request **is set to **Signed** and the **IdP Certificate** is uploaded automatically.
After configuring your IdP, be sure to [verify the configuration](/zpa/about-idp/new#Verify_SSO).
[]![Ping Identity portal with My Applications](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-addapplication-both.png)
[]![My Applications page in the PingOne portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-searchappcatalog-both.png)
[]![Application Catalog on PingOne portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-appcatalog-both.png)
[]![Application Catalog on PingOne portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-searchandsetup-usersso.png)
[]![SSO Instructions on PingOne Portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/pa-pingindentity-ssoinstructions-both.png)
[]![Connection Configuration on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingindentity-configconnection-usersso.png)
[]![Attribute Mapping on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-attributemapping-usersso.png)
[]![PingOne App Customization on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingindentity-customization-usersso.png)
[]![Group Access on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-groupaccess-usersso.png)
[]![Review Setup on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingidentity-reviewsamlmetadata-usersso.png)
[]![Review Setup on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingindentity-reviewandfinish-both.png)
[]![My Applications on PingOne](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-ping-identity/zpa-pingindentity-myapplications-both.png)