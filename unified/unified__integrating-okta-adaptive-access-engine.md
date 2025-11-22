# Integrating Okta with Adaptive Access Engine
Source: https://help.zscaler.com/unified/integrating-okta-adaptive-access-engine
PDF: https://help.zscaler.com/pdf/com/en/1508501.pdf

The Adaptive Access Engine receives user-related context signals from Okta, which are required to control user access to applications via Zscaler. You can configure the Okta settings in the Experience Center and establish the connection between Okta and the Adaptive Access Engine. Okta shares the context signals (Credentials Change and Session Revoked) with the Adaptive Access Engine.
This feature is in limited availability. Contact Zscaler Support for assistance.
Prerequisites
Ensure that you have:
- An Okta account with admin privileges.
- An admin role in Experience Center that allows you to configure the Okta settings.
- [Created an app integration.](#aae-okta-appinteg)
Configure Okta SSF
To configure the Okta SSF settings in Experience Center:
- [1. Configure the Okta integration in Experience Center.](#aae-configureoktainec)
- [2. Configure the SSF settings in the Okta portal.](#aae-oktassf)
- [3. Test the integration in Experience Center.](#aae-oktatestinteg)
- []Log in to the [Okta portal](https://login.okta.com/).
- Go to **Applications**.
- Click **Create App Integration**.
- Select **API Services** as the sign-in method, then click **Next**.
- On the **New API Services App Integration** page, enter a name for the app integration.
- Click **Save**.
- The app integration is successful.
- Go to **Applications** and select the **General** tab to see the app integration details. Copy and save the **Client ID**, as you need to provide this value while configuring Okta in the Experience Center.
- []Go to **Policies** > **Common Configuration** > **Adaptive Access** > **Integrations**.
-
On the **Integrations** page, click the **Edit** icon for Okta.
[See image.](#aae-mainintpage)
-
In the **Integrations** window:
- **Base URL**: Enter the URL as `<customeraccountname>-okta.com`. Replace `<customeraccountname>` with your organization's account name.
- **Client ID**: Enter the Client ID that you copied from the Okta portal while creating the app integration.
- **Public Keys URL**: Click **Generate Keys** to generate a URL. Copy and save this URL, as you need to provide this value in the Okta portal.
- **Status**: Click to enable the status.
-
**Signal** and **Value Type**: The context signal type (Credentials Change and Session Revoke) that Okta shares with the Adaptive Access Engine.
Under **General Settings**, the **Proof of Possession** option is selected by default. Make sure to disable this option, as it is currently not supported.
[See image.](#aae-oktaintegrationspage)
- []Log in to the [Okta portal](https://login.okta.com/) and complete the following steps:
- Go to **Applications** and search for the app that you integrated earlier and select it.
- Click **Edit** to update the client credentials.
-
Under **Public Keys**, enter the URL that was generated in the Experience Center.
[See image.](#aae-publicurl)
- Click **Save**.
-
Next, select the **Okta API Scope** tab and ensure the **SSF.read** and **SSF.manage** API scopes are enabled.
[See image.](#aae-apiscopes)
For Apple services, if the SSF scopes are not shown, locate and enable the **Managed Apple ID Federation and Provisioning** feature. [See image.](#aae-appleoption) To learn more, refer to the [Okta documentation](https://help.okta.com/oie/en-us/content/topics/apps/configure-apple-business-manager.htm).
- Click **Save**.
- On the **Admin Roles** tab, ensure that you are assigned the Super Adminsitrator role.
- []Go back to Experience Center and on the **Integrations** page:
- Click **Test Integration** to verify the connection between Adaptive Access Engine and Okta. A message appears indicating that the connection is successful.
-
Click **Save**.
The Okta configuration is completed. You can proceed to [create user and device profiles](/unified/adding-profile).
[]![Add the details to configure the Okta integration](/downloads/unified/policies/adaptive-access-engine/integrating-okta-adaptive-access-engine/aae-addokta-integration.png)
[]![Provide the authentication and public key details](/downloads/unified/policies/adaptive-access-engine/integrating-okta-adaptive-access-engine/aae-oktaurl.png)
[]![List of granted API scopes](/downloads/unified/policies/adaptive-access-engine/integrating-okta-adaptive-access-engine/aae-apiscopes.png)
[]![Edit the Okta configuration](/downloads/unified/policies/adaptive-access-engine/integrating-okta-adaptive-access-engine/aae-mainintpage.png)
[]
![Enable the option to be able to select the required scopes](/downloads/unified/policies/adaptive-access-engine/integrating-okta-adaptive-access-engine/aae-applefeature.png)