# Configuring PingOne as an IdP
Source: https://help.zscaler.com/dspm/configuring-pingone-idp
PDF: https://help.zscaler.com/pdf/com/en/1483296.pdf

This article provides information on how to configure PingOne as an identity provider (IdP) for single sign-on (SSO).
Prerequisites
Ensure that you have:
- A PingOne account with admin privileges.
- An [administrator role](/dspm/about-roles) or any custom role with Add IdP permissions in the DSPM Admin Portal.
Configuring PingOne
To configure PingOne as an IdP for SSO:
- [1. Download the XML metadata from the DSPM Admin Portal.](#downloadxml)
- [][2. Configure PingOne for SSO.](#pingOne)
- [3. Add PingOne IdP in the DSPM Admin Portal.](#addidp)
- [4. Configure group attributes in PingOne.](#group-attributes)
- [5. Assign groups access via PingOne.](#assign-groups)
- []Go to **Administration** > **Single Sign On**.
- Click **Add IdP Configuration**.
-
[]Click **Download XML Metadata**.
[See image.](#downloadxml-metadata)
The XML metadata contains the following information which you need to provide while [configuring PingOne](#step2).
- **entityID**: A unique identifier for a SAML entity.
- **NameIDFormat**: DSPM only supports email address as the Name ID format.
- **Location**: DSPM destination URL where the SAML response must be sent by the IdP.
[See image.](#metadata-file)
- []Log in to the PingOne portal as an administrator.
- Go to **Applications** > **Applications**.
-
Click the **Add** icon.
[See image.](#addapplication)
- In the **Add Application** window:
- **Application Name**: Enter a name for the application.
- **Description:** (Optional) Enter a description for the application.
- **Application Type**: Select **SAML Application**.
-
Click **Configure**.
[See image.](#add-application-window)
-
Under **SAML Configuration**, select **Import Metadata**.
[See image.](#import-metadata)
-
Click **Select a file**, browse and select the [metadata file](#xml-metadata) you downloaded, then click **Open**.
The **ACS URLs** and **Entity ID** fields are automatically populated from the metadata file.
[See image.](#saml0configuration)
- Click **Save**.
-
Click the blue toggle to enable the application.
[See image.](#enableapplication)
-
On the **Configuration** tab, you need the following information while [adding PingOne IdP configuration](/dspm/adding-identity-providers):
- Click **Download Signing Certificate** and select **.crt** file format.
- Copy the **Issuer ID** and **Single Signon Service**.
[See image.](#signing-certificate)
[][Add PingOne IdP configuration](/dspm/adding-identity-providers) for the tenant.
You can configure a single IdP for a tenant.
- []Select the application you created while [configuring PingOne](#pingOne).
-
Select the **Attribute Mappings** tab and click the **Edit** icon.
[See image.](#attribute-mappings-tab)
-
Click **+Add**.
[See image.](#attribute-add)
-
Add and map the following DSPM attributes to PingOne attributes:
| Application attributes | PingOne attributes |
| ---------------------- | ------------------ |
| `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/emailaddress` | Email Address |
| `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier` | Given Name |
| `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/givenname` | Group Names |
-
Select the **Required** checkbox for all the added attributes.
[See image.](#edit-attributemappings)
- Click **Save**.
[]
- Select the application you created while [configuring PingOne](#pingOne).
-
Select the **Access** tab and click the **Edit** icon.
[See image.](#access-tab)
-
Under **Groups**, select the groups that can access the configured application.
[See image.](#select-groups)
Ensure the group name is the same in PingOne and DSPM Admin Portal. This is required for the group and its users to access the application.
- Click **Save**.
[]![Select the groups to assign access](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-edit-access.png)
[]![Edit attribute mappings](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-edit-attribute-mappings_0.png)
[]![Add attribute mapping](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-add-attribute-mapping.png)
[]![Select the Attribute Mappings tab](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/Attribute-mappings-tab_0.png)
[]![Select the Access tab](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-access-tab.png)
[]![Add an application in PingOne](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/dspm-pingone-add-application.png)
[]![Download XML Metadata](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/dspm-add-download-xml-metadata.png)
[]![Download XML Metadata file](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/dspm-metadata-xml.png)
[]![Add an application in PingOne](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-add-application.png)
[]![Import metadata](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/saml-config-import-metadata.png)
[]![Configure SAML Configuration](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/SAML-configuration-pingone.png)
[]![Enable the application](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-enable-application.png)
[]![Download the Signing Certificate](/downloads/dspm/authentication/idp-configuration/configuring-pingone-idp/pingone-configuration-tab.png)