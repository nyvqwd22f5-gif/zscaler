# SCIM Configuration Guide for Microsoft Azure AD
Source: https://help.zscaler.com/unified/scim-configuration-guide-microsoft-azure-ad
PDF: https://help.zscaler.com/pdf/com/en/1491516.pdf

This guide provides information on how to set up Microsoft Azure Active Directory (AD) to use SCIM in Private Applications. This configuration information is different from [setting up Azure AD](/unified/configuration-guide-microsoft-azure-ad) as an IdP for Private Applications.
Prerequisites
Ensure that you have:
- A premium Azure AD subscription
- An existing directory in Azure AD
- A Private Applications account with an administrator role that allows you to add a SCIM Configuration
Configuring SCIM for Identity Management
Using SCIM allows you to quickly remove users from Private Applications when you delete them in your user directory. To use [SCIM](/unified/about-scim), you must configure it in Azure AD.
The following procedure applies to SCIM configurations for Private Applications in Azure AD. You need to begin the [SCIM configuration](/unified/enabling-scim-identity-management) process in the Admin Portal to get the required information in steps 5 and 6.
- Log in to the [Azure portal](http://portal.azure.com/) and go to **Azure Active Directory** > **Enterprise applications** in the left-side navigation.
[See image.](#AzurePortal)
- Click **All applications**, then click the **Zscaler Private Access (ZPA)** application you added (in steps 1 to 4) as part of configuring Azure as an IdP. To learn more, see [Configuration Guide for Microsoft Azure AD](/unified/configuration-guide-microsoft-azure-ad).
[See image.](#AzureAllApps)
- Click **Provisioning** in the left-side navigation.
- Select **Automatic** from the **Provisioning Mode** drop-down menu.
[See image.](#AzureProvisioningAutomatic)
- In the **Tenant URL** field, enter the **SCIM Service Provider Endpoint** that is provided when [enabling SCIM](/unified/enabling-scim-identity-management) in the Admin Portal.
[See image.](#AzureEndpoint)
- In the **Secret Token** field, enter the **Bearer Token** that is provided when [enabling SCIM](/unified/enabling-scim-identity-management) in the Admin Portal.
[See image.](#AzureBearerToken)
- Click **Test Connection**. The Azure Active Directory attempts to connect to the SCIM endpoint. When the connection is successful, a verification message appears.
If the attempt fails, error information is displayed. Resolve any errors before moving forward.
- Click **Save** after a successful connection to save your credentials.
[See image.](#AzureSaveProvisioning)
- Set the **Provisioning Status** to **On**.
[See image.](#AzureProvisioningStatus)
- Set the **Scope** to **Sync only assigned users and groups**.
- Click **Save** again to start the Azure AD provisioning service.
After SCIM is enabled, Zscaler checks if a user is present in the SCIM database. Based on this information, Zscaler decides if the user is allowed or blocked access to Private Applications. Customers need to ensure SCIM user sync is complete prior to enabling SCIM policies for these users, otherwise the Private Applications service does not recognize the users and evaluate policies for them. After **SCIM Sync** is enabled, Zscaler recommends waiting a minimum of 48 hours, or up to a week, before enabling SCIM policies. It can take up to several days for the IdP to completely sync all user information to Private Applications. Zscaler recommends that **SCIM Sync** be enabled in advance, prior to enabling **SCIM Attributes for Policy**. To learn more, see [Enabling SCIM for Identity Management](/unified/enabling-scim-identity-management).
[]![Azure Portal](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_enterprise_applications.png)
[]![Azure Enterprise All Applications](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_enterprise_allapps.png)
[]![Azure Provisioning Automatic](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_SCIM_provisioning_automatic.png)
[]![Azure Enter Service Provider Endpoint](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_SCIM_provisioning_ServiceProviderEndpoint.png)
[]![Azure Enter SCIM Bearer Token](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_SCIM_provisioning_BearerToken.png)
[]![Azure Save Provisioning](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_SCIM_provisioning_save.png)
[]![Azure Provisioning Status](/downloads/zpa/authentication/scim-configuration-guide-microsoft-azure-ad/Azure_SCIM_provisioning_status.png)