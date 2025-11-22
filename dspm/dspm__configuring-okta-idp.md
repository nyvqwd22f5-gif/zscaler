# Configuring Okta as an IdP
Source: https://help.zscaler.com/dspm/configuring-okta-idp
PDF: https://help.zscaler.com/pdf/com/en/1478151.pdf

This article provides information on how to configure Okta as an identity provider (IdP) for single sign-on (SSO).
Prerequisites
Ensure you have an Okta account with admin privileges.
Configuring Okta
To configure Okta as an IdP for SSO:
- [1. Download the XML metadata from the DSPM Admin Portal.](#downloadxml)
- [][2. Configure Okta for SSO.](#okta)
- [3. Add Okta IdP in the DSPM Admin Portal.](#addidp)
- [4. Assign users or groups via Okta.](#assignuserorgroups)
- [5. Configure group attributes in Okta.](#groupattributes)
- []Go to **Administration** > **Single Sign On**.
- Click **Add IdP Configuration**.
-
Click **Download XML Metadata**.
[See image.](#downloadxmldata)
The XML Metadata contains the following information which you need to provide while [configuring Okta](#oktaconfig):
- **Name Identifier Format**: DSPM only supports email address as the Name ID format.
- **Entity ID**: A unique identifier for a SAML entity.
- **Assertion Consumer Service (ACS) URL**: DSPM destination URL where the SAML response must be sent to by the IdP.
[See image.](#xmlfile)
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
-
Click **Create App Integration**.
[See image.](#createappintegration)
-
In the **Create a new app integration** window, select **SAML 2.0**, and click **Next**.
[See image.](#saml20)
-
In the **General Settings** tab, enter your **App Name**, and click **Next**.
[See image.](#generalsettings)
-
[]Under **SAML Settings**:
- For **Single sign-on URL**, enter the AssertionConsumerService location URL provided in the [XML Metadata](#downloadxml) that you downloaded from the DSPM Admin Portal.
- Select the **Use this for Recipient URL and Destination URL** checkbox.
- For **Audience URI (SP Entity ID)**, enter the entityID provided in the [XML Metadata](#downloadxml) that you downloaded from the DSPM Admin Portal.
- From the **Name ID format** drop-down menu, select **EmailAddress **from the drop-down menu.
[See image.](#configuresaml)
- Click **Next**.
- Select **I'm an Okta customer adding an internal app**, then click **Finish**.
-
On the **Sign On** tab, under **SAML 2.0**, click **More details**. Copy and save the **Sign on URL** and **Issuer** because you need them when [adding identity providers](/dspm/adding-identity-providers)[.]
[See image.](#signondetails)
-
Under **Signing Certificate**, click **Download** to download the IdP certificate.
[See image.](#signingcertificate)
[][Add Okta IdP configuration](/dspm/adding-identity-providers) for the tenant.
You can add only a single IdP configuration for one tenant.
- []Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the application that you created [when configuring Okta for SSO](#step2).
- Click **Assignments**.
-
Select **Assign** > **Assign to People **or **Assign to Groups** depending on whether you want to assign access to a single user or a group of users.
[See image.](#assignpeopleorgroup)
-
In the window that appears, click **Assign** for the user or group you want to select, then click **Done**.
[See image.](#assignusers)
- Repeat the previous step for all users and groups you want to assign to DSPM.
[]
- Log in to the Okta portal as an administrator.
- Go to **Applications** > **Applications**.
- Select the application that you created [when configuring Okta for SSO](#step2).
- Select **General** and scroll down to the **SAML Settings** section, and click **Edit**.
- On the **General Settings **page, click **Next**.
-
On the **Configure SAML page**, under **Group Attribute Statements (optional)**:
- **Name**: Enter `http://schemas.xmlsoap.org/claims/Group`.
- **Name Format**: Select **URI Reference **from the drop-down menu.
- **Filter**: You can select the required value (**Starts with**, **Equals**, **Contains**, and **Matches Regex**) from the drop-down menu. This value is used to match against the Okta group name values and added to the SAML assertion.
[See image.](#grpattribute)
- Click **Next**, and then click **Finish**.
[]![Download XML metadata](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/dspm-add-download-xml-metadata.png)
[]![DSPM metadata xml file](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/dspm-metadata-xml.png)
[]![Create an application in Okta](/downloads/dspm/authentication/idp-configuration/configuring-okta-idp/okta-app-integration.png)
[]![Create a new app integration](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-select-saml-2.0.png)
[]![Enter a name for the app integration](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-create-saml-integration-general-settings.png)
[]![Update the SSO URL](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-configure-samle-page.png)
[]![View the app details](/downloads/dspm/authentication/idp-configuration/configuring-okta-idp/okta-signon-issuer.png)
[]![Download signing certificate](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-download-signing-certificate.png)
[]![Assign users or groups](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-assign-people-group.png)
[]![Assign groups to app integration](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-assign-usersor-groups.png)
[]![Update group attributes](/downloads/dspm/authentication/idp-configuration/saml-configuration-guide-okta/okta-group-attributes.png)