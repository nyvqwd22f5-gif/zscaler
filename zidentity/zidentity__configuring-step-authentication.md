# Configuring Step-Up Authentication
Source: https://help.zscaler.com/zidentity/configuring-step-authentication
PDF: https://help.zscaler.com/pdf/com/en/1531175.pdf

The following article provides information on how to configure step-up authentication in the ZIdentity Admin Portal to allow dynamic requests for stronger authentication when users attempt to access sensitive resources or when risk signals indicate a potential threat.
Prerequisites
Before configuring [step-up authentication](/zidentity/understanding-step-authentication), ensure that:
- Zscaler Client Connector version 4.7 or later is deployed for the users in your organization.
- ZIdentity is enabled for both admins and users.
- Step-up authentication is enabled for ZIdentity, Zscaler Internet Access (ZIA), and Zscaler Private Access (ZPA) tenants.
To learn more about prerequisites specific to an external IdP, refer to their product documentation.
Configuring Step-Up Authentication
To configure step-up authentication in ZIdentity:
Step-up authentication is supported only with OIDC-based external IdP integrations.
- [1. Configure authentication levels in the ZIdentity Admin Portal.](/zidentity/configuring-authentication-levels)
- [2. Enable ACR values and configure the necessary policies in the external IdPs.](#external-idp-configuration)
- [3. Map authentication levels and ACR values in the ZIdentity Admin Portal.](#al-acr-mapping)
- [4. Configure access policies in supported Zscaler services.](#access-policies-mapping)
[]In the [external IdP integrated with ZIdentity](/zidentity/about-external-identity-providers), configure the necessary ACR values and authentication policies. The configuration of ACR values and the necessary policies depend on the specific external IdP. To learn more about the configuration, refer to the respective product documentation. The following list provides detailed steps for configuring ACR values and authentication policies in select IdPs:
- [Enabling Step-Up Authentication in Entra ID](/zidentity/configuring-microsoft-entra-id-external-idp#enabling-step-up-authentication)
- [Enabling Step-Up Authentication in PingOne](/zidentity/configuring-pingone-external-idp#enabling-step-up-authentication)
[]
- Go to **Integration **> **External Identities**.
- Locate the IdP under the **Primary Identity Provider** (or **Secondary Identity Providers**) tab and click the **Edit **icon.
-
In the **Edit Primary IdP** (or **Edit Secondary IdP**) window:
- Select the **Advanced** tab.
-
Under the **Levels to Authentication context mapping** section, enter the **ACR Claim** value for each authentication level. To learn more about the supported ACR claims in external IdP, refer to the respective product documentation.
Ensure that you map proper ACR claims for each level depending on the hierarchy. The highest level of authentication must be mapped to the ACR value for the strongest context.
[See image.](#al-acr-mapping-zidentity)
- Click **Update**.
[]You can configure the necessary policies in the following Zscaler services as required:
- ZPA: [Configure Access Policies](/zpa/configuring-access-policies) for the target application or app segment with the **Conditional Access **as the **Rule Action**. Ensure that the necessary authentication level is selected using the **Step-up Authentication Level** field.
- ZIA: [Configure the URL Filtering Policy](/zia/configuring-url-filtering-policy) and [Cloud App Control Policies](/zia/adding-rules-cloud-app-control-policy) with the **Conditional Access **as the **Action**. Ensure that the necessary authentication level is selected using the **Authentication Level **field.
[]![Mapping authentication levels with ACR values in ZIdentity](/downloads/zidentity/authentication/configuring-step-authentication/zidentity-al-acr-mapping.png)