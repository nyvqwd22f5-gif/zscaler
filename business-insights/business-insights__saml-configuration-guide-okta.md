# SAML Configuration Guide for Okta
Source: https://help.zscaler.com/business-insights/saml-configuration-guide-okta
PDF: https://help.zscaler.com/pdf/com/en/1475106.pdf

The Business Insights service supports identity provider (IdP)-initiated SAML authentication for admins. Admins can log in to the Business Insights Admin Portal directly from a single sign-on (SSO) provider's portal by clicking the Business Insights application icon. This guide explains how to configure SAML SSO with Okta for the Business Insights service.
Prerequisites
Ensure that you have the following before you start configuring Okta:
- An Okta account with admin privileges.
- Admins created for the Business Insights service in the Okta directory.
Configuring SAML SSO with Okta
To configure Okta SAML SSO for Business Insights:
- [1. Create Business Insights app (SAML configuration) in Okta.](#create-app-integration)
- [2. Assign admins to Business Insights.](#assign-admins)
- [3. Download the SAML signing certificate from Okta.](#download-certificate)
- [4. Configure SAML SSO in the Business Insights Admin Portal.](/business-insights/configuring-saml-admins-business-insights)
After you complete the preceding steps, admins can access the Business Insights Admin Portal using their Okta credentials or the Business Insights tile on their Okta homepage.
[See image.](#okta-home-img)
[]To add the Business Insights application to Okta:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Click **Create App Integration**.
[See image.](#create-app-img)
- Select **SAML 2.0 **as the **Sign**-**in method**.
[See image.](#select-saml-img)
- Click **Next**.
- In the **General Settings** section, enter the display name for the service in the **App name** field (e.g., `Business Insights`).
- Click **Next**.
- In the **Configure SAML** section:
- **Single sign-on URL**: Enter `https://admin.zscaleranalytics.net/idp-auth`
- **Audience URI (SP Entity ID)**: Enter `https://admin.zscaleranalytics.net/idp-auth`
- **Default RelayState**: Enter your Business Insights cloud name. You can view the cloud from the My Profile page in the Business Insights Admin Portal. [See image.](#my-profile)
[See image.](#saml-section-img)
- Click **Next**.
- In the **Feedback** section, select **I'm a software vendor. I'd like to integrate my app with Okta **and** **click **Finish**.
[See image.](#feedback-section-img)
The Business Insights integration is created in Okta. You can assign admins to the application.
[]To assign admins to the Business Insights application:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Select the Business Insights application from the list.
- Click **Assign **> **Assign to People**.
[See image.](#assign-peope-img)
- Click **Assign **next to the users that you want to assign the application.
[See image.](#assign-option-img)
- Click **Save and Go Back**, then click **Done**.
The admins are assigned to the Business Insights application.
[]To download the SAML signing certificate:
- Log in to your Okta account.
- In the Admin Console, go to **Applications **> **Applications**.
- Select the Business Insights application from the list.
- In the** SAML Signing Certificates **section, download the SHA-2 type certificate by clicking **Actions** > **Download certificate**.
[See image.](#saml-certificate-img)
The certificate is downloaded to your system. Upload the certificate as part of Step 4 in the **IdP SAML Certificate **field.
[]![Screenshot of Create App Integration option in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-create-integration-option%20(2).png)
[]![Screenshot of the SAML 2.0 option in OKta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-select-saml%20(1).png)
[]![My Profile page in the Risk360 Admin Portal](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-my-profile-page.png)
[]![Screenshot of the Configure SAML section in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-configure-saml-section_0.png)
[]![Screenshot of the Feedback section in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-feedback%20(1).png)
[]![Screenshot of SAML Signing Certificate section in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-saml-sigining-certificate%20(1).png)
[]![Screenshot of the Assign to People option in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-assiging-people%20(1).png)
[]![Screenshot of the Assign option in Okta](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-assign-option%20(1).png)
[]![Screenshot of Okta Homepage with RIsk360 tile](/downloads/zia/documentation-knowledgebase/analytics/dashboards-reports-and-logs/insights/viewing-user-reports-web-insights/Business-Insights-Okta-homepage-risk360-tile_0.png)