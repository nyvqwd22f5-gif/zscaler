# Managing a Service Provider Certificate Rotation
Source: https://help.zscaler.com/unified/managing-service-provider-certificate-rotation
PDF: https://help.zscaler.com/pdf/com/en/1491121.pdf

When a single sign-on (SSO) certificate is retired, you need to rotate the service provider certificate used by your identity provider (IdP) to ensure admins and end users maintain successful access to applications.
To make these changes, you need the relevant service provider metadata and certificate for your IdP. The service provider metadata and certificate information is specific to your IdP and the Single Sign-On selection made when [configuring your IdP](/unified/configuring-idp-single-sign) within the Admin Portal. You can access this information from the [IdP Configuration page](/unified/about-idp-configuration) in the Admin Portal.
If the original [IdP you configured](/unified/configuring-idp-single-sign) is [Azure](/unified/configuration-guide-microsoft-azure-ad) or [Okta](/unified/configuration-guide-okta), your IdP will download the latest certificate from Private Applications and rotate your account configuration automatically. No further action is required.
Use one of the following options to rotate a certificate:
- [Automatically update the certificate using a metadata URL](#automatic)
- [Manually update the certificate using a metadata URL](#url)
- [Manually update the certificate using metadata and certificate files](#file)
- []Go to **Administration **>** Identity **>** Private Access **>** IDP Configuration**.
- Locate the IdP configuration you want to modify within the table, and click the **Edit** icon.
- In the** Edit IdP Configuration** window, select a different service provider certificate for **User SP Certificate Rotation** or **Admin SP Certificate Rotation**.
- Click **Save**. The IdP automatically updates to use the new service provider certificate.
- []Go to **Administration **>** Identity **>** Private Access **>** IDP Configuration**.
- Locate the IdP configuration you want to modify within the table, and click the **Edit** icon.
- In the** Edit IdP Configuration** window, select a different service provider certificate for **User SP Certificate Rotation** or **Admin SP Certificate Rotation**.
- Click **Save**.
- Locate the IdP you updated within the table, and expand the row to view the IdP details.
- []Find the **Service Provider URL**, and click the **Copy** icon to copy the URL to your clipboard.
![Copy icon for Service Provider URL for an identity provider on the IdP Configuration page](/downloads/zpa/documentation-knowledgebase/authentication/managing-certificate-rotation/zpa-idpconfigpag-copyserviceproviderurl.png)
- Go to your IdP and complete the following based on the IdP:
- [Microsoft Active Directory Federation Services (ADFS) 2.0 and 3.0](#url-adfs)
- [Other IdPs](#url-other)
- Test your logins to ensure SSO is working correctly.
- []Log in to your ADFS server.
- In the Windows server, go to **Administrative Tools** > **ADFS Management** to launch the ADFS management application.
-
In the left-side navigation of the **AD FS** window, click the **Relying Party Trusts** folder.
![Selecting the Relying Party Trusts folder in the AD FS management window](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-adfs-relying-party-trusts.png)
-
In the **Relying Party Trusts** panel, right-click the relying party trust for Private Applications (e.g., Private Applications or Private Applications Admin SSO), and click **Properties.** The **Properties** window appears.
![Select Properties in the AD FS management window for ADFS](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-adfs-relying-party-trusts-properties.png)
-
On the **Monitoring** tab, enter the URL you copied in [step 6](/zpa/managing-service-provider-certificate-rotation#url-step6) above in the **Relying party’s federation metadata URL:** field.
![Adding a service provider URL on the Monitoring tab of the Properties window for ADFS](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-afds-relying-party-trusts-properties-metadataUrl.png)
- Click **Test URL** and wait for a successful validation.
- Click **OK**, click **Apply**, and then close the **Properties** window.
In certain scenarios, AD FS caches the expired certificate. Zscaler recommends deleting any expired certificates from the **Relying Party Trusts** panel after a new certificate is successfully updated.
- []Log in to your IdP portal.
- Go to the applications section where the IdP for Private Applications resides.
- Select the IdP for Private Applications to update its configuration information.
- Enter the URL you copied in [step 6](#url-step6) above.
- Save your changes.
- [][G]o to **Administration **>** Identity **>** Private Access **>** IDP Configuration**.
- Locate the IdP configuration you want to modify within the table, and click the **Edit** icon.
- In the** Edit IdP Configuration** window, select a different service provider certificate for **User SP Certificate Rotation** or **Admin SP Certificate Rotation**.
- Click **Save**.
- Locate the IdP you updated within the table, and expand the row to view the IdP details.
- []Find **Service Provider Certificate**, and click **Download Certificate** to download the certificate file for this IdP.
![Download Certificate button for Service Provider Certificate in the IdP Configuration page ](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-idpconfigpag-downloadserviceprovidercert.png)
- Go to your IdP and complete the following based on the IdP:
- [Microsoft Active Directory Federation Services (ADFS) 2.0 and 3.0](#file-adfs)
- [Other IdPs](#file-other)
- Test your logins to ensure SSO is working correctly.
- []Log in to your ADFS server.
- In the Windows server, go to **Administrative Tools** > **ADFS Management** to launch the ADFS management application.
-
In the left-side navigation of the **AD FS** window, click the **Relying Party Trusts** folder.
![Selecting the Relying Party Trusts folder in the AD FS management window](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-adfs-relying-party-trusts.png)
-
In the **Relying Party Trusts** panel, right-click the relying party trust for Private Applications (e.g., Private Applications or Private Applications Admin SSO), and click **Properties**. The **Properties** window appears.
![Select Properties in the AD FS management window for ADFS](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-adfs-relying-party-trusts-properties.png)
-
On the **Signature** tab, click **Add..** and select the certificate downloaded in [step 6](/zpa/managing-service-provider-certificate-rotation#cert-step6) above.
![Click Add to select a service provider certificate](/downloads/zpa/documentation-knowledgebase/single-sign/idp-configuration/managing-service-provider-certificate-rotation/zpa-managing-sp-cert-rotation-adfs-relying-party-trusts-add-cert.png)
- Click **OK**, click **Apply**, and then close the **Properties** window.
In certain scenarios, AD FS caches the expired certificate. Zscaler recommends deleting any expired certificates from the **Relying Party Trusts** panel after a new certificate is successfully updated.
- []Log in to your IdP portal.
- Go to the applications section where the IdP for Private Applications resides.
- Select the IdP for Private Applications to update its configuration information.
- Enter the URL you copied in [step 6](#cert-step6) above.
- Save your changes.