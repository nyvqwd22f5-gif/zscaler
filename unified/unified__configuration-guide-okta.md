# Configuration Guide for Okta
Source: https://help.zscaler.com/unified/configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1491231.pdf

This guide provides information on how to set up Okta as an IdP for Private Applications.
Prerequisites
Ensure that you have the following:
- An Okta account with admin privileges
- A Private Applications account with an administrator role that allows you to add an IdP Configuration
Configuring Okta for SSO
[][]To configure Okta as the IdP for a Private Applications user and admin SSO:
- Log in to the Okta portal as an administrator.
- Within the top banner, make sure that **Classic UI** is selected from the drop-down menu.
You may only see the **Classic UI** if you are in the Okta developer dashboard.
[See image.](#Step1_ClassicUI)
- Go to **Applications** from the top menu.
- Click **Add Application**.
[See image.](#Step2_UserImg)
- In the search toolbar, search for **Zscaler Private Access 2.0**. When the application appears, click **Add**.
[See image.](#Step3_UserImg)
- On the **General Settings** page that appears:
- For **Application label**, make sure that **Zscaler Private Access 2.0** is entered.
- Click **Done**.
[See image.](#Step4_UserImg)
- On the **Assignments** page that appears:
- Select **Assign** > **Assign to People** or **Assign to Groups**.
[See image.](#Step5_UserImg)
- In the window that appears, click **Assign** for the user or group you want to select, then click **Save and Go Back**.
- Repeat step b for all users and groups you want to assign to the Private Applications application, then click **Done**.
- Go to the **Sign On** page, click **Edit**, and complete the following fields. You must use the **SAML 2.0** sign-on option for this application:
- (Optional) If you want to pass Okta group information as part of the SAML response:
- From the **GroupName** drop-down menu, select your preferred group filter (e.g., **Matches Regex**).
- Type in the applicable value for the group filter in the text field.
For example, selecting **Matches Regex** and entering .* sends information for all Okta groups to Private Applications within the SAML response.
[See image.](#GroupName_UserImg)
- Click the **Identity Provider metadata** hyperlink to download the IdP's metadata file. You will need this file later in order to [complete the configuration](/unified/configuring-idp-single-sign) within the Admin Portal.
[See image.](#Step7_UserImg)
- For **Service Provider URL**, the URL that is provided for you when you [configure a new IdP configuration](/unified/configuring-idp-single-sign) in the Admin Portal. This URL is specific to your IdP.
- For **Service Provider Entity ID**, enter the ID that is provided for you when you configure a new IdP configuration in the Admin Portal. This ID is specific to your IdP.
[See image.](#SP_URLandID)
- Click **Save**.
- Go to the Admin Portal and [complete the IdP configuration set up](/unified/configuring-idp-single-sign).
- (Optional) If you are configuring Okta for user SSO and want to use [SCIM](/unified/about-scim), proceed to the [SCIM Configuration Guide for Okta](/unified/scim-configuration-guide-okta).
After configuring your IdP, be sure to [verify the configuration](/unified/configuring-idp-single-sign#VerifyIdP_AdminSSO).
[]![Classic UI vs. Developer Console setting within Okta portal](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-example-okta/zpa-okta-classicui.png)
[]![Applications > Add Application Button within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-okta/zpa-okta-addapplication.png)
[]![Search for an Application within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-okta/zpa-okta-searchapplication.png)
[]![General Settings for the Zscaler Private Access Application within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-okta/zpa-userssookta-generalsettings.png)
[]![Assignments > Assign to People Option within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-examples/configuration-example-okta/zpa-okta-assignusers.png)
[]![Identity Provider metadata link in Sign On > Settings within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-example-okta/zpa-okta-idpmetadatalink.png)
[]![GroupName field in Sign On > Settings within Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-okta/zpa-okta-groupnameexample.png)
[]![Service Provider URL and Service Provider ID in Okta](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration-guides/configuration-guide-okta/zpa-okta-spurlandid.png)