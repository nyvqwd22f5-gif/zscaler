# Integrating with Microsoft Azure Virtual WAN
Source: https://help.zscaler.com/unified/integrating-microsoft-azure-virtual-wan
PDF: https://help.zscaler.com/pdf/com/en/1494626.pdf

Zscalers integration leverages Microsoft's Azure Virtual WAN (VWAN) APIs to discover and configure Azure hubs, including querying and configuring Azure VWAN. When the integration is configured, the Zscaler service can sync hub information from Azure. After hub information is synced to Zscaler, outbound IPSec tunnels from any of the hubs to the nearest Zscaler data center can be created using a one-click configuration process. The one-click process automatically configures the Azure hubs, and provisions [Locations](/unified/about-locations) and [VPN Credentials](/unified/about-vpn-credentials) for these hubs, within the Admin Portal.
Prerequisites
Before you begin the Azure VWAN integration setup, make sure that you have:
- A valid subscription for Azure VWAN which is an additional cost. Refer to [Microsoft Azure pricing](https://azure.microsoft.com/en-us/pricing/details/virtual-wan/) for more details.
- At least one Azure hub configured.
- Added Zscaler as a Security Partner Provider. To learn more, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/firewall-manager/deploy-trusted-security-partner).
You must configure the Zscaler VWAN Hub as a Security Partner Provider in Microsoft Azure, or it fails to sync with the Admin Portal.
Limitations of Zscaler integration to Azure VWAN
There are some limitations to keep in mind while integrating Zscaler with your Azure VWAN.
- Redundant tunnels are not supported. Only one outbound tunnel from an Azure VWAN hub to a Zscaler tenant is supported.
- Azure Government isn't supported.
- No failover to another Zscaler data center based on unavailability or load. This is due to redundant tunnels not being supported.
- No support for sub-locations. Only Zscaler locations are supported.
- No multi-tenancy. Traffic from multiple VNETs belonging to the same organization goes through the same VWAN hub to Zscaler tenant.
- Support for one Zscaler cloud per Azure VWAN hub. Multiple clouds, including beta and production, need additional VWAN hubs. The current VWAN hub limit is one hub per region, per subscription. Refer to Azure documentation for any updates to this.
- Support for one Azure tenant per Zscaler cloud. You cannot terminate tunnels to multiple Azure VWAN hubs across multiple subscriptions.
[]Step 1: Create an Azure Service Principal for Azure VWAN
- Log in to the [Azure portal](https://portal.azure.com).
- Create a service principal in Azure Active Directory (AD). During setup, you must obtain the **Application ID**, **Application Key**, **Tenant ID**, and **Subscription ID** to complete [Step 2 of the integration procedure](#VWANIntegration_Step2):
- [Create a new application registration for Zscaler and obtain the Application ID](#GetApplicationID)
- [Create a service principal authentication key and obtain the key value (i.e., Application Key)](#GetKey)
- [Obtain the Tenant ID (i.e., Directory ID)](#GetTenantID)
- [Obtain the Subscription ID](#GetSubscriptionID)
[]Step 2: Set up your Azure VWAN integration on Zscaler
- Log in to the Admin Portal.
- Go to **Infrastructure **> **Internet & SaaS** > **Traffic Forwarding** > **Partner Integrations**.
-
In the **Azure Virtual WAN** tab, under **Azure AD Authentication Credentials**:
- Enter your **Application ID**.
- Enter your **Application Key**.
- Enter your **Tenant ID** (i.e., Directory ID).
- Enter your **Subscription ID**.
- Click **Test** to be notified if your Azure integration with Zscaler succeeded or not.
[See image.](#Zscaler_Credentials)
If your Azure AD authentication credentials are valid, you can proceed to [Step 3 of the integration procedure](#VWANIntegration_Step3).
If the test was unsuccessful, ensure that Zscaler VWAN Hub is properly configured as a Security Partner Provider to avoid any sync failures with the Admin Portal. To learn more, refer to the [Microsoft documentation](https://docs.microsoft.com/en-us/azure/firewall-manager/deploy-trusted-security-partner).
[]Step 3: Sync and Configure your Azure Hubs on Zscaler
When your Azure AD authentication credentials are validated, click **Sync**. This syncs your Azure hubs to the Zscaler service. The **Azure Hub Locations Sync **section updates, showing the last sync timestamp and the number of hub sites that were successfully synced.
[See image.](#sync-azure-hubs)
Clicking on the hub sites hyperlink takes you to the **Infrastructure** > **Internet & SaaS** > **Traffic Forwarding** > **Location Management** page. Go to the [Azure Virtual WAN Locations](/unified/configuring-azure-virtual-wan-locations) tab. All **Azure Hub** locations, along with the associated **Azure Region**, are displayed. Initially, the tunnel configuration is set to **Not Configured**, and the **Azure Sites**, **Zscaler Location**, **IP Address**, and **VPN Connection** columns are empty.
[See image.](#azure-locations-notconfigured)
Review the table and then edit each location to start the tunnel configuration. To learn more, see [Configuring Azure VWAN Locations](/unified/configuring-azure-virtual-wan-locations).
Troubleshooting
During the Azure Virtual WAN authentication, you might see one of the following errors:
- **INVALID CREDENTIALS**: Tenant ID, Subscription ID, Application ID, and Application Secret are all required. If one of these is not configured, you see this error.
- **DUPLICATE ITEM**: The entered Subscription ID is already associated with another organization.
- **ACCESS FAILURE**: The Subscription ID is not available for this account. This likely means that the Subscription ID was entered incorrectly.
- **NOT AUTHORIZED**: Got 401 or 403 from an Azure API that is called by Zscaler UI. Contact your Azure support representative for assistance.
- **ACCESS FAILURE**: Got 404 when authenticating with Azure portal. Contact your Azure support representative for assistance.
- **UNEXPECTED ERROR**: Contact your Zscaler Support Engineer for assistance.
- []From the left-side navigation, click **Azure Active Directory**.
- In the panel that appears, under **Manage**, click **Properties**.
-
Under **Directory properties**, copy the **Directory ID**. This is the **Tenant ID** you need to complete the integration within the Admin Portal for [Step 2 of the integration procedure](#VWANIntegration_Step2).
[See image.](#AzureAD_GetDirID)
- []From the left-side navigation, click **Azure Active Directory**.
- In the panel that appears, under **Manage**, click **App registrations**.
-
Click **New registration**.
[See image.](#AzureAD_ManageNewAppReg)
-
In the **Register an application **panel that appears:
- Enter a **Name **for the application (e.g., Zscaler API).
- For **Supported account types**, select **Accounts in this organizational directory only**.
- For **Redirect URI**, enter the sign-on URL for the application. This is the Cloud Portal URL for your Zscaler cloud (e.g., https://admin.zscalertwo.net).
- Click **Register**.
[See image.](#AzureAD_CreateNewApp)
-
Copy the **Application ID** for the registered Zscaler application you created in the previous step. This is the **Application ID** you need to complete the integration within the Admin Portal for [Step 2 of the integration procedure](#VWANIntegration_Step2).
[See image.](#AzureAD_GetAppID)
You must assign the registered Zscaler application to a role to access resources in Azure VWAN.
- From the left-side navigation, click **All services**.
-
In the panel that appears, click **General**, then **Resource groups**.
[See image.](#AzureAD_ResourceGroup)
-
Find and select the resource group that you set up for Azure VWAN. If you do not have a resource group, refer to the [Microsoft Azure Virtual WAN documentation](https://docs.microsoft.com/en-us/azure/virtual-wan/).
Zscaler recommends that you use a separate resource group for Azure VWAN to reduce the scope of the changes that can be performed by the service principal.
- Click **Access control (IAM)**.
- Click **Add **> **Add role assignment**.
-
In the **Add role assignment** panel that appears:
- For **Role**, select **Contributor**.
- For **Assign access to**, select **Azure AD user, group, or service principal**.
- For **Select**, select the registered Zscaler application you created previously (e.g., Zscaler API).
- Click **Save**.
[See image.](#AzureAD_AddRoleAssign)
- []From the left-side navigation, click **Azure Active Directory**.
- In the panel that appears, under **Manage**, click **App registrations**.
-
Find and click on the Zscaler application registration (e.g., Zscaler API). To learn more, see [Create a New App Registration for Zscaler and Obtain the Application ID](/unified/integrating-microsoft-azure-virtual-wan#GetApplicationID) above.
[See image.](#AzureAD_ManageNewAppReg2)
-
Click **Certificates & secrets**.
[See image.](#AzureAD_Keys)
- In the panel that appears, under **Client secrets**, click **New client secret**.
-
In the **Add a client secret **panel:
- Enter a **Description **for the key.
- For **Expires**, select an expiration period for the key (e.g., 1 year).
- Click **Add**.
[See image.](#AzureAD_CreateAppKey)
The key’s **Value** appears within the panel after you save. You must copy the key value now. You can't retrieve the key later. The Zscaler service uses the **Application ID** and the key **Value** to authenticate to Azure. This is the **Application Key** you need to complete the integration within the Admin Portal for [Step 2 of the integration procedure](#VWANIntegration_Step2).
[See image.](#AzureAD_GetAppKeyValue)
- []From the left-side navigation, click **All services**.
-
In the panel that appears, under **General**, click **Subscriptions**.
[See image.](#AzureAD_ManageSubs)
- Find the role you associated to the registered Zscaler application within the table and copy the **Subscription ID**. This is the **Subscription ID** you need to complete the integration within the Admin Portal for [Step 2 of the integration procedure](#VWANIntegration_Step2).
[]![zia-azure-getdirectoryid.png](/downloads/zia/documentation-knowledgebase/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-getdirectoryid.png)
[]![Click Azure Active Directory > App registrations > New registration](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-newappreg.png)
[]![Find and select the Zscaler application in Azure](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-appregfind.png)
[]![Register the newly added Zscaler application in Azure](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-registerzscalerapp.png)
[]![Copy the Application (client) ID from Azure](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-zscalerappid.png)
[]![Resource group location](/downloads/zia/documentation-knowledgebase/partner-integrations/integrating-microsoft-azure-virtual-wan/zia-azure-resourcegroups02.png)
[]![Select Certificates & secrets, then click New client secret.](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-zscalerappsettings.png)
[]![Client secret location.](/downloads/zia/documentation-knowledgebase/partner-integrations/integrating-microsoft-azure-virtual-wan/zia-azure-zscalerappkey02.png)
[]![Copy the Application Key value](/downloads/zia/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-zscalerappkeyvalue.png)
[]![Subscription location.](/downloads/zia/documentation-knowledgebase/partner-integrations/integrating-microsoft-azure-virtual-wan/zia-azure-subscriptions02.png)
[]![Partner Integrations page within the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azurevwan-step1.png)
[]![Azure Hub Locations Sync section within Admin Portal](/downloads/zia/documentation-knowledgebase/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-synchubs.png)
[]![Azure Virtual WAN Locations tab within the ZIA Admin Portal](/downloads/zia/documentation-knowledgebase/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azurevwan-locations-notconfigured.png)
[]![zia-azure-resourcegroups-addrole.png](/downloads/zia/documentation-knowledgebase/partner-integrations/configuring-microsoft-azure-virtual-wan-integration/zia-azure-resourcegroups-addrole.png)