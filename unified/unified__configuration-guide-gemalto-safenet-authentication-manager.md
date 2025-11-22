# Configuration Guide for Gemalto SafeNet Authentication Manager
Source: https://help.zscaler.com/unified/configuration-guide-gemalto-safenet-authentication-manager
PDF: https://help.zscaler.com/pdf/com/en/1491211.pdf

This guide provides information on how to set up Gemalto SafeNet Authentication Manager (SAM) as a IdP for Private Applications.
Prerequisites
Ensure that you have the following:
- Admin privileges on the system where Gemalto SAM is installed
- A Private Applications account with an administrator role that allows you to add an IdP Configuration
Configuring SAM for SSO
[]To configure SAM as the IdP for Private Applications user and admin SSO:
- [1. Configure Private Applications as a Service Provider (SP) within SAM Policy Management](#ConfigureZPAAsSP)
- [2. Obtain the IdP Metadata from SAM Configuration Manager](#ObtainMetadata)
After configuring your IdP, be sure to [verify the Private Applications to SAM configuration](/unified/configuring-idp-single-sign/).
- []On a Windows system, go to **Start **> **All Programs** >**SafeNet** > **SafeNet Authentication Manager** > **Policy Management**.
The **Active Directory Users and Computers** window appears.
[See image.](#IMG-UsersAndComps)
- In the **Active Directory Users and Computers** window, right-click on the directory name (e.g., rupizscaler.com) and select **Properties**.
[See image.](#IMG-ADProperties)
- In the window that appears, go to the **Token Policy** tab and click **Open**.
[See image.](#IMG-TokenPolicyOpen)
- In the window that appears, select the Token Policy Object Link you want to modify (e.g., Default policy) and click **Edit**.
[See image.](#IMG-TokenPolicyObjectEdit)
The **Token Policy Object Editor** window appears.
- In the **Token Policy Object Editor** window, in the left pane, scroll down to and expand **Protected Application Settings**.
[See image.](#IMG-TPOEdit-ProtAppSett)
- Select **User Authentication**, then double-click on **Application Authentication Settings** in the right pane.
[See image.](#IMG-AppAuthSett)
The **Application Authentication Settings Properties** window appears.
- In the **Application Authentication Settings Properties** window, make sure that **Enabled** is selected, then click **Definitions...**.
[See image.](#IMG-AppAuthSett-Properties)
- In the window that appears, right-click on **Application Authentication Settings** and select **Create a new profile**.
[See image.](#IMG-CreateProfile)
- Right-click on the newly created profile (e.g., Profile1) and select **Rename**.
[See image.](#IMG-RenameProfile)
In this example, we've named the profile **zscaler**.
[See image.](#IMG-ZscalerProfile)
- []In the right pane for the profile, double-click on a **Policy** to enter the proper **Policy Setting** value:
- **Application issuer**: Enter the service provider (i.e., Zscaler) entity ID for user or admin SSO. A **Service Provider Entity ID** is provided for you when you [configure a new IdP configuration](/unified/configuring-idp-single-sign) in the Admin Portal. This ID is specific to your IdP.
-
**SAM issuer**: Enter the entity ID for SAM, which can be any string. When you are [configuring the IdP for SSO](/unified/configuring-idp-single-sign) within the Admin Portal, the ID you specify here must be entered into the **IdP Entity ID** field. For example, we configured the entity ID as sam, so it would be entered as sam for the **IdP Entity ID** field within the Admin Portal.
[See example configuration](#IMG-SAMIssuer)
- **Application's login URL**: Enter the service provider (i.e., Zscaler) single sign-on URL for user or admin SSO. A **Service Provider URL** is provided for you when you [configure a new IdP configuration](/unified/configuring-idp-single-sign) in the Admin Portal. This URL is specific to your IdP.
- **Audience URI**: Enter the service provider (i.e., Zscaler) entity ID for user or admin SSO. This is the same **Service Provider Entity ID** you entered for **Application issuer** above.
- **User mapping**: Select the appropriate mapping as per your IdP configuration (e.g., **eMail**).
- **OTP authentication**: If your users are using one-time password (OTP) authentication, then make sure that this setting is **Enabled**.
All other settings (i.e., **Automatic Windows authentication**, **Certificate-base authentication**, etc.) can remain **Not Defined**.
- Click **Apply**, then **OK**.
- Click **OK** in any other open windows to save your changes.
- []On a Windows system, go to **Start **> **All Programs** > **SafeNet** > **SafeNet Authentication Manager** > **Configuration Manager**.
- In the **Configuration Manager** window, from the **Action** menu select **Cloud Configuration...**.
- In the **Cloud Settings** window, go to the **Info for Service Provider** tab.
- Make note of the **Sign-in page URL** for SAM.
- Click **Export Certificate...** to download the certificate used by SAM for signing SAML assertions.
Also, be sure to take note of the entity ID you specified in [step 1j](#step1j) for the procedure above. You will need this metadata information when [configuring SAM as an IdP](/unified/configuring-idp-single-sign) for SSO within the Admin Portal.
[See image.](#IMG-CloudSettings)
This procedure references SAM version 8.2 as an example, other SAM versions allow you to export the metadata from this window.
- Go to the Admin Portal and [complete the IdP configuration set up](/unified/configuring-idp-single-sign).
[]![Active Directory Users and Computers window in SAM](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-ad-usersandcomputers.png)
[]![Active Directory Users and Computers window with right-click menu displayed](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-ad-usersandcomputersproperties.png)
[]![Properties window for directory with Token Policy tab](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-ad-propertiestokenpolicy.png)
[]![Token Policy Object properties window with Token Policy Object Links displayed](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-ad-edittokenpolicyobject.png)
[]![zpa-sam-tpoeditor-protectedappsetting.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-tpoeditor-protectedappsetting.png)
[]![zpa-sam-tpoeditor-appauthsetting.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-tpoeditor-appauthsetting.png)
[]![zpa-sam-appauthsettings-properties.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-appauthsettings-properties.png)
[]![zpa-sam-appauthsettings-createnewprofile.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-appauthsettings-createnewprofile.png)
[]![zpa-sam-appauthsettings-renameprofile.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-appauthsettings-renameprofile.png)
[]![zpa-sam-appauthsettings-zscalerprofile.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-appauthsettings-zscalerprofile.png)
[]In the image below, our **zscaler **profile specifies the **SAM issuer** as sam.
![zpa-sam-samissuer1.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-samissuer1.png)
So, for the IdP configuration for SAM within the Admin Portal, we must specify the **IdP Entity ID** as sam.
![Add IdP Configuration window with IdP Entity ID field](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-samissuer2_0.png)
[]![zpa-sam-cloudsettings.png](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuring-gemalto-safenet-authentication-manager-single-sign/zpa-sam-cloudsettings.png)