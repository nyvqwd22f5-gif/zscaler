# Configuring the Azure DLP Application Integration Using Cloud-to-Cloud Incident Forwarding
Source: https://help.zscaler.com/workflow-automation/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding
PDF: https://help.zscaler.com/pdf/com/en/1531120.pdf

Workflow Automation DLP application integration with an Azure instance using Zscaler Cloud-to-Cloud Incident Forwarding enables your organization to send Data Loss Prevention (DLP) incident metadata and evidence files to your organization's Azure storage containers in your Azure account without deploying appliances.
To configure the DLP application integration using Cloud-to-Cloud Incident Forwarding:
- [1. Create a resource in Microsoft Azure.](#create-resource-c2c)
- [2. (Optional) Set up Azure Front Door to access the storage account through a private endpoint.](#c2c-setup-azure-front-door)
- [3. Add a DLP Azure application integration in Workflow Automation using the output from the bash script and the Azure resource manager stack.](#c2c-add-integration)
- [4. Set Up the DLP Cloud-to-Cloud Incident Forwarding.](#set-up-zscaler-c2c)
[]You can create Microsoft Azure resources automatically by using a bash script in Azure, or you can create them manually.
- [Creating resources automatically using a bash script](#resource-automatic-c2c)
- [Creating resources manually using the Azure console](#resource-manual-c2c)
[]
- [a. Download the Zscaler bash script and the Azure resource manager template files from the Workflow Automation Admin Portal.](#c2c-bash-script-download)
- [b. Set up the resource manager stack in Azure using the script and template files that Zscaler provides.](#c2c-setup-resource-manager)
[]You can set up the resource manager stack in the Azure portal using the bash script and the template files you previously downloaded from the Workflow Automation Admin Portal.
To set up the resource manager stack:
- [i. In Azure, create the app registration for the DLP Integration.](#c2c-create-app-registration)
- [ii. Deploy the resource manager template for DLP Integration in Azure.](#c2c-deploy-template-dlp-integration)
[]
- [a. Create the app registrations for the DLP integration using the Azure console.](#app-registration-manual-c2c)
- [b. Deploy the Azure resources for DLP Integration.](#deploy-resource-manager-dlp-integration-c2c)
[]You must complete the following steps to deploy the resource manager template for DLP integration:
- [Create Storage Accounts](#c2c-storage-accounts)
- [Create Role Assignments](#c2c-role-assignments)
- [Create Event Grid System Topics](#c2c-event-grid-system-topic)
[]Configure the DLP Cloud-to-Cloud Incident Forwarding on an Azure instance for Workflow Automation. To learn more about configuring Cloud-to-Cloud Forwarding in Azure, see [Configuring DLP Cloud-to-Cloud Incident Forwarding](/zia/configure-dlp-cloud-cloud-incident-forwarding).
[]
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP Azure** application tile. The **Tile View** icon is selected by default.
[See image.](#Integrations-Dashboard-Initial-View)
-
Click anywhere within the **DLP Azure** application tile. The **Zscaler DLP Azure Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
[See image.](#Zscaler-DLP-Azure-Integration-Page-Initial-View)
- Click the **Configuration Steps** tab. Under **Azure Resource Stack Setup**, click the following links:
- Click the **create-app-registration-c2c.sh **link to download the Zscaler bash script.
- Click the **ZscalerAzureIntegrationRM_C2C.json** link to download the Azure DLP Integration resource manager template.
[See image.](#zscaler-dlp-azure-integration-details-page-config-steps)
[]
- Log in to the Azure portal as a user with Owner permission in Azure.
-
In the top right of the Azure portal, click the **Cloud Shell** icon and select **Bash** as a shell. The Cloud Shell virtual terminal appears at the bottom of the page.
[See image.](#access-cloud-shell)
-
At the top of the Cloud Shell virtual terminal, click the **Upload/Download **icon.
[See image.](#step-2-A-upload-download-icon)
-
Click **Upload** and select the bash script file (create-app-registration.sh) that you previously downloaded from the Workflow Automation Admin Portal. A message appears at the bottom right when the upload is complete.
[See image.](#cloudshell-bash-script-uploaded)
-
Enter the following command and press `Enter`:
`bash create-app-registration-c2c.sh -d <customer display name> -y <number of years in which the secret is valid>`
For example, `bash create-app-registration-c2c.sh -d zscaler-Azure-Integration - y 3`. This script creates the app registrations for both the DLP Integration, along with the client secrets for those apps. By default, the script creates a password/secret with one-year validity for the service principal, but you can change the number of years. The customer display name value that you enter in the command is used for the containers and storage accounts in Azure.
-
Copy and save the output values you receive from the script for both the DLP Integration app registration. You use the output values for the DLP Integration app registration later when you set up the integration in Workflow Automation.
The following is an example of output received from the DLP Integration app registration:
`{
"applicationClientSecret": "k1r8Q~xxxxxxxxxxxxxxxxx.xxxxxxxxxxx",
"tenantId": "aa698f79-a76e-4d05-8330-xxxxxxxxxx",
"appName": "zscaler-Azure-Integration",
"applicationObjectId": "929cbf20-c9ce-418b-xxxx-xxxxxxxxxx",
"servicePrincipalObjectId": "5c4de7fb-xxxx-4b69-xxxx-xxxxxxxxxxx"
}`
The system enters the customer display name value that you entered in the bash command as the `appName` for the registration.
The output values from the script include credentials that you must protect and keep secure.
[]
- Log in to the Azure portal as a user with Owner permission in Azure. Owner permission is required because you add role definitions and assignments during this procedure.
-
In the Azure portal, under Azure services, click the **Deploy a custom template** icon. The **Custom deployment** page appears.
[See image.](#custom-deployment-page)
-
On the **Custom deployment** page, click **Build your own template in the editor**. The **Edit template** page appears.
[See image.](#edit-template-page-initial)
-
On the **Edit template** page, click the **Load file** icon at the top of the page and select the DLP Integration template (ZscalerAzureIntegrationRM.json) you previously downloaded from Workflow Automation. The template file is displayed on the **Edit template** page.
[See image.](#step-2-C-edit-page-load-file)
-
Click **Save**. The **Custom deployment** page reappears.
[See image.](#custom-deployment-page-after-template-add)
- On the **Custom deployment** page:
- In the **Project details** section:
- **Subscription**: From the drop-down menu, select a subscription. The subscription associated with your account appears by default. You can find the subscription name by going to the **Subscriptions** page in Azure.
- **Resource Group**: From the drop-down menu, select the resource group where you want to deploy the storage account, blob containers, system topics, role definition, etc. If you want to create a new resource group, click **Create new**.
-
In the **Instance details** section:
- **Region**: From the drop-down menu, select a region. The region associated with the resource group appears by default.
- **Storage Account Name**: Enter the name of the storage account. Ensure that you do not use dots (`.`) in the storage account name.
- **App Service Principal Object Id**: Enter the `servicePrincipalObjectId` value from the output of the create app registration DLP integration script.
- **Enable Read Access To Data Blob**: To enable read access to the incident violation details in the Workflow Automation Admin Portal, select **yes**. **Yes** appears by default.
[See image.](#custom-deployment-page-data-populated)
- Click **Review + Create**. Azure runs a final validation of the template. Wait until the template passes the validation.
-
Click **Create**. The deployment **Overview** page appears, displaying the deployment details.
Wait until the deployment is complete. After the deployment completes successfully, a message appears at the top of the page with a green check mark, stating that the deployment is complete.
[See image.](#Deployment-Overview-Page)
- From the left-side navigation, select **Outputs**. The deployment **Outputs **page appears.
-
On the **Outputs** page, click the **Copy to clipboard** icon next to the **storageAccountName** and the **systemTopicResourceId** fields and store in your local system. These values are required when creating the DLP Azure Integration in the Workflow Automation Admin Portal.
[See image.](#deployment-outputs-page)
Different storage containers that share a common name prefix are used for storing DLP incident data and metadata files. The names of the data and metadata containers are set to `<storageAccountNamePrefix>-data` and `<storageAccountNamePrefix>-metadata`, respectively. The Zscaler DLP Incident Management service reads and stores the incident metadata file (with trigger data stripped), but it never reads or stores the incident data files.
To notify the service when new incidents are uploaded to the storage container, an Event Grid topic is created in the Azure account. The metadata storage container is configured to publish BlobCreated notifications to the Event Grid topic. The Zscaler service hosts a Webhook endpoint, which is used to subscribe to the Event Grid topic. When the Zscaler service receives a notification on the Webhook endpoint, it reads the metadata file associated with the notification from the storage container. To do so, a service principal is created in the Azure account that has permissions to read from the metadata storage container and, optionally, the data storage container. The read permission for the data storage container is only required if you want users who respond to incidents to be able to view incident data files through short-lived, pre-signed Shared Access Signature (SAS) URL links.
[]For more information about the app registration process on the Microsoft Azure console, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app#register-an-application).
- Log in to the Microsoft Azure console.
-
On the main page, click the** App registrations** option. You can also search for `app registrations` and select the** App registrations** option. The **Register an application **page appears.
[See image.](#app-registration-option-image-C2C)
- On the **Register an application **page, enter the following details:
- **Name**: Enter a display name for your application.
- **Supported account types**: Select **Accounts in any organizational directory and personal Microsoft accounts**. This option allows you to register a multitenant application that can support users who have organizational and personal Microsoft accounts.
- **Redirect URI (optional)**: From the drop-down menu, select **Web**.
-
Click **Register** to complete the app registration. The new application's overview page appears.
[See image.](#register-app-dlp-image-C2C)
-
On the overview page, copy and save the following details for future use:
- Display name
- Application (client) ID
- Object ID
- Directory (tenant) ID
[See image.](#dlp-app-overview-image-C2C)
-
Next to the **Client credentials**, click **Add a certificate or secret**. The **Certificates & secrets** page appears.
[See image.](#add-client-certificate-image-C2C)
-
On the **Certificates & secrets** page, click **New client secret**. The **Add a client secret** pane opens.
[See image.](#add-client-secret-option-image-C2C)
- In the **Add a client secret **pane, enter the following details:
- **Description**: Enter a description for the client secret.
- **Expires**: From the drop-down menu, select an expiration timeline for the client secret. You can also enter a custom timeline based on your requirements.
-
Click **Add**. The client secret value and secret ID display on the **Certificates & secrets** page.
[See image.](#add-client-secret-pane-image-C2C)
-
On the **Certificates & secrets** page, ensure that you copy and save the client secret's value for future use.
You cannot view the secret value again after you leave this page.
[See image.](#new-client-secret-id-image-C2C)
[]To deploy the Azure resources for DLP integration:
- Log in to the Microsoft Azure console.
- On the main page, select the **Storage accounts** option. You can also search for `storage accounts` and select the **Storage accounts** option. The **Storage accounts** page appears.
-
On the **Storage accounts **page, click **Create**. The **Create a storage account **page appears.
[See image.](#create-storage-accounts-image)
-
On the **Create a storage account **page, on the **Basics **tab, do the following:
- In the **Project details** section:
- **Subscription**: From the drop-down menu, select a subscription. The subscription associated with your account appears by default.
- **Resource group**: From the drop-down menu, select an existing resource group. The resource group must be the same one you used for creating the VM.
- In the **Instance details** section:
- **Storage account name**: Enter a name for your storage account. Ensure that you do not use dots (.) in the storage account name.
- **Region**: From the drop-down menu, select the region for the storage account.
- **Performance**: Leave the default setting.
- **Redundancy**: Leave the default settings.
[See image.](#basics-tab-storage-account-image)
- On the **Networking **tab, do the following:
- In the **Network connectivity** section, in the **Network access **field, select **Enable public access from selected virtual networks and IP address**.
- In the **Virtual networks **section:
- **Virtual Network Subscription**: Select the subscription that you selected on the **Basics** tab.
-
**Virtual Network**: Click **Create virtual network**. The **Create virtual network** pane** **appears.
- **Name**: Enter a name for your virtual network.
- **Resource Group**: From the drop-down menu, select the resource group you used earlier.
- **Location**: From the drop-down menu, select a location for the virtual network.
- **Address space**: Enter the public IP addresses that you want to allowlist.
-
**Subnets**: Enter the subnets of the IP addresses that you want to allowlist.
To view the various IP addresses of different Workflow Automation clouds associated with Zscaler, see [NAT Gateway IP addresses](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Workflow%20Automation%20-%20NAT%20Gateway%20IPs.txt).
- Click **OK**.
[See image.](#create-virtual-network-pane-image)
- In the **Network routing** section, for the **Routing preference **field, select **Microsoft network routing**.
-
Click** Review**. The **Review** tab appears.
[See image.](#networking-tab-storage-accounts-image)
-
On the **Review** tab, review the values and settings you entered, and then click **Create**. The deployment **Overview** page appears, displaying the deployment details.
[See image.](#review-tab-storage-accounts-image)
After the storage account successfully deploys, you must create two containers for the storage account.
To create the containers:
- Go to the newly created storage account.
- On the storage account page, go to **Data storage** > **Containers**. The **Containers** page appears.
-
Click **Container**. The **New container** pane appears.
[See image.](#container-option-image)
-
In the **New container** pane, do the following:
- **Name**: Enter a name for your container. Use the name of your storage account followed by the word `data`. For example, if your storage account name is Zscaler, then make your container name `Zscaler-data`.
- Click **Create**.
[See image.](#create-new-container-image)
Similarly, create another container with a name consisting of your storage account name followed by `metadata`. For example, `<storageAccountName>-metadata`.
Different storage containers that share a common name suffix are used for storing DLP incident data and metadata files. The name of the data bucket is set to `<storageAccountNamePrefix>-data`, and the name of the metadata bucket is set to `<storageAccountNamePrefix>-metadata`. The Zscaler DLP Incident Management service reads and stores the incident metadata file (with trigger data stripped), but it never reads or stores the incident data files.
[See image.](#three-container-image)
[]You need to create a role for the DLP application.
To create a role for DLP:
- Go to the resource group you created.
-
On the resource group page, in the left-side navigation, go to **Access control (IAM)**. The **Access control (IAM) **page appears.
[See image.](#access-control-IAM-image)
-
On the **Access control (IAM) **page, select** Add** > **Add custom role**. The **Create a custom role** page appears.
[See image.](#add-custom-role-dlp-role-image)
- On the **Create a custom role** page, do the following:
-
On the **Basics** tab, enter a name for the role in the **Custom role name** field. You can leave the other default settings on the page.
[See image.](#basics-tab-new-dlp-role-image)
-
On the **JSON** tab, click** Edit** and replace the action parameters that appear by default with the following JSON. Then click **Save**.
"actions": [                                                                                                                                                                                                                                                                         "Microsoft.Storage/storageAccounts/blobServices/containers/read",                                                                                                                                                                                                                                                                                        "Microsoft.Storage/storageAccounts/blobServices/generateUserDelegationKey/action",                                                                                                                                                                                                                                                                                        "Microsoft.EventGrid/systemTopics/eventSubscriptions/write",                                                                                                                                                                                                                                                                                        "Microsoft.EventGrid/systemTopics/eventSubscriptions/read",                                                                                                                                                                                                                                                                                       "Microsoft.EventGrid/systemTopics/eventSubscriptions/delete"                                                                                                                                                                                                                                                   ]                                                                                                                                                                                                                                                                                             "dataActions": [                                                                                                                                                                                                                                                                                      "Microsoft.Storage/storageAccounts/blobServices/containers/blobs/read"                                                                                                                                                                                                                                                        ]
[See image.](#json-tab-new-dlp-role-image)
- Click **Create**. The **Review + create** tab appears.
-
On the **Review + create** tab, review the values and settings you entered, and then click **Create**.
[See image.](#review-tab-new-dlp-role-image)
After creating the role, assign it to the DLP application.
To complete role assignments:
-
On the **Access control (IAM) **page, select **Add** > **Add** **roles assignments**. The **Add role assignment** page appears.
[See image.](#add-role-assignment-option-image)
-
On the **Role** tab, search for and select the role you created for DLP app registration.
[See image.](#role-tab-role-assignment-image)
- On the **Members** tab, do the following:
- **Assign Access to**: Select **User, group, or service principal**.
-
**Members**: Click **Select members**. The **Select members** pane appears.
- In the **Select members** pane, from the drop-down menu, select the DLP app registration you created.
- Click **Select**.
[See image.](#members-tab-role-assignment-image)
- Click **Review + assign**. The **Review + assign **tab appears.
-
Review the values and settings you entered, and then click **Review + assign**.
[See image.](#review-assign-role-assignment-image)
[]To create the event grid system topics for the storage account:
- Log in to the Microsoft Azure console.
- On the main page, select **Event Grid System Topics**. You can also search for `Event Grid System Topics` and select it. The **Event Grid | System topics** page appears.
-
Click **Create**. The **Create** **Event Grid System Topics** page appears.
[See image.](#event-grid-create-image)
-
On the **Create** **Event Grid System Topic** page, on the** Basics** tab, do the following:
- In the **Topic Details** section:
- **Topic Types**: From the drop-down menu, select **Storage Accounts (blob & GPv2)**.
- **Subscription**: From the drop-down menu, select the subscription associated with your account.
- **Resource Group**: From the drop-down menu, select the resource group you created.
- **Resource**: From the drop-down menu, select the storage account you created.
- In the **System** **Topic Details** section:
- **Name**: Enter a name for the system topic.
- **Location**: Select a location for the system topic.
Leave the other default settings.
[See image.](#event-grid-bascis-tab-image)
- Click **Review + create**. The **Review + create **tab appears.
-
Review the details you entered and then click **Create**. The deployment **Overview** page appears, displaying the deployment details.
[See image.](#event-grid-review-create-image)
You can view the newly created system topic on the **Events** tab of your storage account.
[]After you create the storage account, you can set up Azure Front Door Premium to use private endpoints when configuring Zscaler Azure DLP integration. This step is optional and only required if you want Workflow Automation to access the storage account through private endpoints. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/frontdoor/standard-premium/how-to-enable-private-link-storage-account).
To set up private endpoints to access the storage account:
- Go to the storage account you created.
-
From the left-side navigation, click **Front Door and CDN**. The **Front Door and CDN **page appears.
[See image.](#front-door-cdn-page)
- On the **Front Door and CDN** page, in the **New Endpoint** section, configure the following:
- **Service type**: Select** Azure Front Door**.
- **Create new/use existing profile**: Select **Create new**.
- **Profile name**: Enter a name for your profile.
- **Endpoint name**: Enter a name for the new endpoint.
- **Endpoint host name**: This field is populated automatically.
- **Origin host name**: From the drop-down menu, select the origin host name.
- **Pricing tier**: Select **Azure Front Door Premium Security optimized**.
- **Private link:** Select **Enable private link**.
- **Region**: From the drop-down menu, select a region for your endpoint.
- **Target sub resource**: From the drop-down menu, select** blob**.
-
Click **Create**. The deployment **Overview** page appears, displaying the deployment details.
[See image.](#new-endpoint-front-door-cdn)
-
On the **Overview** page, click **Go to resource**. You are redirected to the storage account page.
[See image.](#new-endpoint-deployment-page)
-
On the storage account page, from the left-side navigation, select **Networking**.
[See image.](#networking-page-private-endpoint)
-
On the **Networking** page, on the **Private endpoint connections** tab, select the newly created private endpoint and click **Approve**.
[See image.](#private-endpoint-connections-tab)
-
Go to the **Front Door and CDN** page, where the endpoint is successfully approved for usage. You can also view details such as the **Host name**, **Profile name**, **Service type**, **Tier**, and **Status**, of your private endpoint.
[See image.](#approved-private-endpoint)
You must approve the new private endpoints to use them when configuring the Zscaler Azure DLP integration.
Similarly, you can create additional private endpoints.
-
[]Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP** **Azure** application tile. The **Tile View** icon is selected by default.
[See image.](#integrations-dashboard-card-view-initial)
-
(Optional) On the **Integrations **dashboard, change the format for the dashboard. Click the **List View** icon to view the integrations in a list.
[See image.](#integrations-dashboard-list-view-initial)
- After you select a view option, perform one of the following procedures:
- In the tile view: In the DLP Azure application tile, click the **Add** icon. The add **Zscaler DLP Azure Integration** page appears.
- In the list view:
-
Next to the DLP Azure application integration, click **Connect**. The **Zscaler DLP Azure Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
[See image.](#zscaler-azure-application-integration-page-initial)
The **Configuration Steps** tab provides the instructions for configuring a DLP Azure application integration, a link to download the bash script, and links to download the Zscaler resource manager template files.
- On the **Configuration** tab, click **Add New**. The add **Zscaler DLP Azure Integration** page appears.
- On the add **Zscaler DLP Azure Integration** page, in the **Zscaler Azure DLP Integration** section, enter an **Integration Name**.
- In the **Account Credentials** section:
- **Tenant ID**: Copy the `TenantId` output from the bash script for the DLP integration and enter it here.
- **Client ID**: Copy the `applicationClientId` output from the bash script for the DLP integration and enter it here.
- **Client Secret**: Copy the `applicationClientSecret` output from the bash script for the DLP integration and enter it here.
- In the **Zscaler Azure DLP Integration** section:
- **Storage Account Name**: Copy the `storageAccountName` output from the deployment of the resource manager template for DLP integration and enter it here.
- **Custom Storage Endpoint URL**: (Optional) If you do not want Workflow Automation to access the storage account through a default public endpoint, enter a custom storage endpoint URL in the format `https://<custom endpoint>`. If you want to use a public endpoint, leave the field blank.
- **Event Grid System Topic Resource Id**: Copy the `systemTopicResourceID` output from the deployment of the resource manager template for DLP integration and enter it here.
-
In the **Privacy Settings** section:
- **Hide Evidence Data - Admin**: Select if you do not want admins to be able to generate presigned evidence links for an incident on the** Incident Details** page. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Admin**: Select if you do not want admins to be able to see the trigger data for an incident on the **Incident Details** page. Otherwise, they can see the trigger data.
- **Hide Policy Details - Admin**: Select if you do not want the admins to be able to view the policy details for the incident on the **Incident Details** page. Otherwise, they are able to view the policy details for the incident.
- **Hide Evidence Data - End User**: Select if you do not want end users to be able to generate presigned evidence links for an incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - End User**: Select if you do not want end users to be able to see the trigger data for an incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - End User**: Select if you do not want the end users responding to an incident notification to be able to view the policy details for the incident. Otherwise, they are able to view the policy details for the incident.
- **Hide Evidence Data - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to generate presigned evidence links for the incident. Otherwise, they are able to generate evidence links.
- **Hide Trigger Data - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to see the trigger data for the incident. Otherwise, they are able to see the trigger data.
- **Hide Policy Details - Manager/Approver**: Select if you do not want the approvers or managers responding to an incident escalation notification to be able to view the policy details for the incident. Otherwise, they are able to view the policy details for the incident.
[See image.](#add-zscaler-dlp-azure-integration-page)
If you disable **Hide Evidence Data** or **Hide Trigger Data** in the integration, but you did not enable read access to the data blob when creating the resource manager stack, no one can generate evidence links or view trigger data in the Workflow Automation Admin Portal.
-
Click **Validate**. The system validates the account credentials that are entered with the Azure integration. It also checks whether the format is correct for the **Event Grid System Topic Resource Id**. You can only add the integration if it passes validation.
If the validation fails for any reason, or if the configuration has been created or updated with the wrong values, you must disable the integration, correct the values for the integration, and re-enable it.
-
Click **Add**. The **Zscaler DLP Azure Integration** details page appears, displaying the DLP integration under **Connected Accounts** with an **Enabled** status.
[See image.](#Zscaler-DLP-Azure-Integration-Page-After-Add)
To learn more, see [Managing DLP Azure Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-azure-application-integrations-workflow-automation).
![Screenshot of the App registrations option in the Azure console](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-app-registration-option-dlp.png)
[]
![Screenshot of the Register an App page for DLP application in the Azure console](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-register-application-page-dlp.png)
[]
![Screenshot of the DLP application overview page after registration in the Azure console](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-app-registration-overview-page.png)
[]
![Screenshot of the Add Client Certificate or Secret field in the DLP application overview page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-app-registration-overview-page-add-client-secret.png)
[]
![Screenshot of the add New Client Secret option in the Certificates&Secrets page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-certificates-secrets-page-new-client-secret.png)
[]
![Screenshot of the Add a Client Secret pane in the Certificates&Secrets page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-add-new-client-secret-pane.png)
[]
![Screenshot of the newly added client secret ID and  client value](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/App%20registration/WA-configuring-dlp-azure-copy-client-secret-value.png)
[]
[]![Viewing the initial view of the Integrations dashboard in the Tile view](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Integrations-Dashboard-Initial-Display-TileView.png)
[]![Viewing the Zscaler DLP Azure Integration details page with no integrations configured in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Zscaler-DLP-Azure-Integration-Details-Page-Configuration-Tab-Initial.png)
[]
![Zscaler DLP Azure Integration details page - Downloading files from Configuration Steps tab](/downloads/workflow-automation/data-protection/setup/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding/WA-c2c-DLP-Azure-Integration-details%20page-downloading-links-portal.png)
![Accessing the Power Shell in Microsoft Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Integration-Powershell.png)
[]
![Clicking the Upload/Download icon in the Cloud Shell terminal in Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Integration-Powershell-Upload-Icon.png)
[]
[]![Bash script uploaded successfully in the Cloud Shell in Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Integration-Powershell-Template-Upload.png?1683662478)
[]![Viewing the Custom Deployment page in Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Custom-Deployment-Page.png?1683752783)
[]![Viewing the Edit Template page in Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Edit-Template-Page-Template-Initial.png)
![Viewing the Edit template page in Azure  after the template file is uploaded. ](/downloads/workflow-automation/data-protection/setup/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding/WA-c2c-DLP-Azure-Integration-Edit-Template.png)
[]
[][![Viewing the Custom deployment page - Basics tab in Microsoft Azure](/downloads/workflow-automation/data-protection/setup/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding/WA-c2c-DLP-Azure-Integration-Custom-Deployment-Basics.png)
](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Custom-Deploy-PG-Basics-Tab.png)
[][![Entering Information on the Custom deployment Page in Microsoft Azure](/downloads/workflow-automation/data-protection/setup/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding/WA-c2c-DLP-Azure-Integration-Custom-Deployment-Basics-fields-filled.png)
](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Custom-Deploy-PG-Fields-Populated.png)
[][![Viewing the deployment Overview Page in Microsoft Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Deployment-OV-PG.png)
](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Deployment-OV-PG.png)
[]![Viewing the deployment Outputs page in Azure](/downloads/zia/policies/data-loss-prevention/zscaler-workflow-automation/setup/configuring-dlp-application-integration-using-azure/ZIA-WA-Azure-Deployment-Output-Page.png)
[]![Viewing the initial view of the Integrations Dashboard in the Tile view ](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Integrations-Dashboard-Initial-Display-TileView3.png)
[]![Viewing the initial view of the Integrations Dashboard in the List view ](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Integrations-Dashboard-Initial-Display-ListView.png)
[]![Viewing the Zscaler DLP Azure Integration details page with no integrations configured in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Zscaler-DLP-Azure-Integration-Details-Page-Configuration-Tab-Initial3.png)
[]![Adding a Zscaler DLP Azure Integration on the add Zscaler Azure DLP Integration Page in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Add-Zscaler-DLP-Azure-Integration-Page.png)
[]![Viewing the Zscaler DLP Azure Integration details page with an integration enabled in the Workflow Automation Admin Portal](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-Azure-Zscaler-DLP-Azure-Integration-Details-Page-Integration-Enabled.png)
![Screenshot of the Create option in the Storage Accounts page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-storage-accounts-create.png)
[]
![Screenshot of the Basics tab of the Storage Accounts page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-create-storage-accounts-page-basics-tab.png)
[]
![Screenshot of the Create Virtual Network pane of the Storage Accounts page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-create-virtual-network-pane.png)
[]
![Screenshot of the Networking tab of the Storage Accounts page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-create-storage-accounts-page-review-networking-tab-.png)
[]
![Screenshot of the Review tab of the Storage Accounts page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-create-storage-accounts-page-review-tab-create.png)
[]
![Screenshot of the Container option in the Storage Accounts > Containers](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-storage-accounts-container.png)
[]
![Screenshot of the Create a New Container pane in the Storage Accounts > Containers](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-storage-accounts-create-new-container.png)
[]
![Screenshot of the all the two newly created container option in the Storage Accounts > Containers](/downloads/workflow-automation/data-protection/setup/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding/WA-C2C-configuring-dlp-azure-storage-accounts-two-container.png)
[]
![Screenshot of the Access Control option in the new Storage Account for creating a new DLP role](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-resource-group-access-control-(IAM)-option.png)
[]
![Screenshot of the Add custom role option in Resource Group > Access Control page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-resource-group-IAM-Add-custom-role.png)
[]
![Screenshot of the Access Control - Basics tab for the new DLP role](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-create-new-roles-basics-tab.png)
[]
![Screenshot of the Access Control - JSON tab for the new DLP role](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-create-new-roles-json-tab-dlp.png)
[]
![Screenshot of the Access Control - Review + Create tab for the new DLP role](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-create-dlp-new-roles-review-create-tab.png)
[]
![Screenshot of the Add Role Assignment option in the Access Control page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-access-control-add-role-assignments.png)
[]
![Screenshot of the Roles tab in the Add Role Assignment page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-add-role-assignment-page-roles-tab.png)
[]
![Screenshot of the Members tab in the Add Role Assignment](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/WA-configuring-dlp-azure-add-role-assignment-page-members-tab.png)
[]
![Screenshot of the Review + Assign tab in the Add Role Assignment page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/DLP%20Role%20Assignments/WA-configuring-dlp-azure-add-role-assignment-page-review-assign-tab.png)
[]
![Screenshot of the Create icon on the Event Grid System topics page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Event%20Grid/WA-configuring-dlp-azure-event-system-grid-create.png)
[]
![Screenshot of the Basics tab on the Event Grid System topics page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Event%20Grid/WA-configuring-dlp-azure-event-system-grid-basics-tab.png)
[]
![Screenshot of the Review + Create icon on the Event Grid System topics page](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Event%20Grid/WA-configuring-dlp-azure-event-system-grid-review-create-tab.png)
[]
![Screenshot of the Front Door and CDN page for the Storage Account to use private endpoint](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-configuring-Azure-dlp-integration-Front-door-cdn-page.png)
[]
![Screenshot of creating New Endpoint in the Front Door and CDN page for the Storage Account](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-Configuring-Azure-DLP-Integration-Front-Door-CDN-PG-New-Enpoint.png)
[]
![Screenshot of New Endpoint deployment page and Go to resource option in the for the Storage Account](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-configuring-Azure-dlp-integration-new-endpoint-overview-page.png)
[]
![Screenshot of the Networking page for the Storage Account to use private endpoint](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-configuring-Azure-dlp-integration-networking-page.png)
[]
![Screenshot of the Private endpoint connections tab in the Networking page for the Storage Account](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-configuring-Azure-dlp-integration-networking-private-endpoint-tab.png)
[]
![Screenshot of the approved private endpoint details in the Front Door and CDN page for the Storage Account](/downloads/workflow-automation/setup/configuring-dlp-application-integration-using-azure/Azure%20Front%20Door%20Premium/WA-configuring-Azure-dlp-integration-Front-door-cdn-approved-endpoint.png)
[]