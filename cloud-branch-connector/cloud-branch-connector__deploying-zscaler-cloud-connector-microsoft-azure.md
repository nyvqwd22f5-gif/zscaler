# Deploying Zscaler Cloud Connector with Microsoft Azure
Source: https://help.zscaler.com/cloud-branch-connector/deploying-zscaler-cloud-connector-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1420751.pdf

Do not run both Virtual Machine Scale Set (VMSS) and non-VMSS deployments within the same virtual network (VNet).
This deployment guide provides information on prerequisites, how to deploy Zscaler Cloud Connector as a virtual machine (VM) in Microsoft Azure, and post-deployment configurations.
The Azure Routing Intent and Routing Policies feature for secured virtual Wide Area Network (WAN) hubs is incompatible with Cloud Connector.
This procedure describes two methods for deploying Cloud Connector.
-
Zscaler Cloud Connector Application in the Azure Marketplace: The Azure Marketplace Application method is available for static deployment of Cloud Connector.
The Zscaler Cloud Connector Application in the Azure Marketplace is available in all regions except China. If you are deploying Cloud Connector from the China region, you must use Terraform.
-
Terraform: The Terraform method provides support for a richer set of functions, including the option to deploy using VMSS. To learn more about the resources created when deploying Cloud Connector using a Terraform script, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#azure-terraform). To learn more about VMSS, see [Understanding Cloud Connector Deployments with Azure Virtual Machine Sets](/cloud-branch-connector/understanding-cloud-connector-deployments-azure-virtual-machine-scale-sets).
VMSS is the name of the feature in the Azure Marketplace and the Terraform templates. Auto Scaling is the name of the same feature in the Cloud Provisioning template.
Prerequisites
[]Make sure the following prerequisites are met.
The role that you assign admins dictates the level of access they have to the Zscaler Cloud & Branch Connector Admin Portal. Zscaler provides a default [admin ](/cloud-branch-connector/about-administrators)account that provides full access to the Cloud & Branch Connector Admin Portal and scope over the entire organization. Admins must have full access to API Key Management, Location Management, and Cloud Connector Provisioning permissions. To learn more, see [About Role Management](/cloud-branch-connector/about-role-management) and [Adding Admin Roles](/cloud-branch-connector/adding-cloud-connector-roles).
- Ensure that you have the following roles assigned to your Azure subscription: User Access Administrator, Contributor, and Key Vault Administrator.
- From the[ API Key Management ](/zia/about-api-key-management)page, retrieve and copy the API key. Cloud Connector uses the API key to authenticate and register the VM with Zscaler.
- Add a[ Location Template](/cloud-branch-connector/configuring-location-template). Locations identify the various networks from which your organization sends its traffic.
- Add a [Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template) and copy the Cloud Provisioning URL.
- Confirm that you have enough address space for the virtual network. The minimum IPv4 address space for the VNet is 24 (`/24`). The minimum IPv4 address space for the subnet (`zsccSubnet`) into which Cloud Connectors are deployed is 28 (`/28`).
-
Configure your firewall. The Cloud Connector instance requires only outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the outbound access requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/cloud-branch-connector.
You can find the <Zscaler Cloud Name> in the URL you use to log in to the Cloud & Branch Connector Admin Portal. For example, if you log in to connector.zscaler.net, then go to https://config.zscaler.com/zscaler.net/cloud-branch-connector. To learn more, see [What is my cloud name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
- [Create user-assigned managed identities.](#managedidentity)
- [Create an Azure key vault.](#keyvault)
- [Create secrets to add to your Azure key vault.](#secrets)
- [Create an SSH key pair.](#SSH)
[]
[]
User-assigned managed identities are required for deploying Cloud Connector. Ensure that Cloud Connector is not assigned an Azure System Managed Identity because that identity overrides the deployment requirements.
There are two user-assigned managed identities:
- Cloud Connector: Managed identity associated with Cloud Connectors to perform Azure operations such as network interface discovery and metric publishing.
- Function App (VMSS only): Managed identity associated with an Azure Function app. Azure Functions make API calls to perform operations such as instance termination, instance replacement, and metric reading.
Deployments without VMSS require only the Cloud Connector managed identity and the Network Contributor role.
Deployments with VMSS require both managed identities and the following roles:
- Cloud Connector
- Network Contributor
- Monitoring Metrics Publisher (VMSS only)
- Storage Queue Data Contributor
- Function App (VMSS only)
- Network Contributor
- Virtual Machine Contributor
- Monitoring Contributor
- Managed Identity Operator
- Storage Blob Data Reader
To create managed identities and assign roles:
- Log in to the [Azure Portal](https://portal.azure.us).
- Under** Services**, search for` Managed Identities`.
- Click **Create**.
The **Create User Assigned Managed Identity** page appears.
- On the **Basics** tab:
- **Subscription**: Select the subscription with user access administrator permission to manage deployed resources.
- **Resource group**: Click **Create new **and enter a name for the resource group.** **A resource group is a collection of resources that share the same lifecycle, permissions, and policies.
- **Region**: Select the desired region for your deployment.
- **Name**: Enter a name for your user-assigned managed identity.
[See image.](#ManagedIdentity-Basics)
- Click **Next: Tags >**.
- On the **Tags** tab, configure tags to categorize resources, then click **Next: Review + create >**.
- On the **Review + create **tab, review your managed identity configuration, and then click** Create**.
- After your managed identity has been created, go to **Managed Identities** and select your managed identity.
- From the left-side navigation, click **Azure role assignments**, then click **Add role assignment (Preview)**.
- In the **Add role assignment (Preview) **window:
- **Scope**: From the drop-down menu, select** Subscription**.
- **Subscription**: From the drop-down menu, select your subscription.
- **Role**: From the drop-down menu, select the role or roles specified [above](#managedidentity), one at a time.
[See image.](#addrole-preview)
- Click **Save**.
- (Scale Set deployments only) Repeat this procedure for the second managed identity.
[]Create an Azure key vault to securely store and access your secrets:
- Log in to the [Azure Portal](https://portal.azure.us).
- Go to** Key vaults**, then click **Create**.
The **Create a key vault **page appears.
- On the **Basics** tab:
- **Subscription**: Select the subscription with user access administrator permission to manage deployed resources.
- **Resource group**: Select the resource group in which you want to create the key vault.
- **Key vault name**: Enter a name for your key vault.
- **Region**: Select the desired region for your deployment.
- **Pricing tier**: Select either** Standard **or **Premium (includes support for HSM backed keys)**.
- **Soft-delete**: This setting is automatically enabled on this key vault. Soft-delete allows you to recover or permanently delete a key vault and secrets.
- **Days to retain deleted vaults**: Enter the desired period for retaining deleted vaults.
- **Purge protection**: Select either **Disable purge protection (allow key vault and objects to be purged during retention period) **or **Enable purge protection (enforce a mandatory retention period for deleted vaults and vault objects)**.
[See image.](#keyvault-basics)
- Click **Next**.
-
Perform one of the following procedures to configure the key vault permission model.
Zscaler strongly recommends the Azure Role-Based Access Control method, because it provides a clear delineation between security operations and administrative tasks. For example, with this method, only the Owner and User Access Administrator roles can grant access to keys, secrets, and certificates.
- [Azure Role-Based Access Control (recommended)](#RBACPolicy)
- [Vault Access Policy](#VaultAccessPolicy)
-
[]
On the **Access configuration** tab:
- **Permission model**: Select **Azure role-based access control (recommended)**.
-
**Resource access**: Select **Azure Resource Manager for template deployment**.
[See image.](#createkeyvault-accesspolicyIAM)
- Click **Next**.
-
On the **Networking **tab, select **Enable public access**, and then select **All networks**.
[See image.](#networkingIAM)
- Click **Next**.
- On the **Tags** tab, configure tags to categorize resources.
- Click **Review + Create** and then click **Create.**
- The key vault **Overview **page shows the status of the deployment.
-
After the deployment is complete, click **Go to resource**.
[See image.](#GoToResource)
-
On the key vault page, in the left navigation, select **Access control (IAM)**. On the **Access control (IAM)** page, click **Role assignments** > **Add** > **Add role assignment**.
[See image.](#IAMAddRoleAssignment)
-
On the **Add role assignment** page, on the **Job function roles** tab, search for and select the **Key Vault Secrets User** role. Click **Next**.
[See image.](#KeyVaultSecretsUser)
- On the **Members **tab, for **Assign access to**, select **Managed identity**.
-
Click **Select members**.
[See image.](#IAMSelectManagedIdentity)
- On the **Select managed identities** window that opens, filter by your subscription name or ID.
-
Search for and select the Cloud Connector [managed identity](#managedidentity) you created earlier, click **Select**,** **and then click **Review + assign**.
[See image.](#IAMSelectManagedIdentityWindow)
-
On the **Role assignments** tab of the **Access control (IAM)** page, click **Role Assignments**, enter `Key Vault Secrets` in the search bar, and confirm the managed identity account that is being assigned to Cloud Connector.
[See image.](#IAMVerify)
- []**Access configuration**: Select **Vault access policy **as the permission model.
-
**Resource access**: Select** Azure Resource Manager for template deployment**.
[See image.](#createkeyvault-accesspolicy)
- Under **Access policies**, click **Create**.
- In the **Create an access policy** window:
-
**Secret permissions**: On the **Permissions **tab, under **Secret permissions**, select **Get** and **List**, then click **Next**.
[See image.](#secretpermissions)
-
**Principal**: On the **Principal **tab, select your recently created managed identity, then click **Next**.
[See image.](#select-principal)
- Click **Create**.
- Click** Next**.
- On the **Networking **tab, select **Enable public access**, and then select **All networks**. Click **Next.**
- On the **Tags** tab, configure tags to categorize resources. Click **Next**.
- On the **Review + Create** tab, review the summary of your configurations and click** Create**.
[]Create secrets to store in your key vault:
- Log in to the [Azure Portal](https://portal.azure.us/).
- Go to **Key vaults**, then select your newly created key vault.
- In the left-side navigation, click** Secrets**, then click** Generate/Import**.
The **Create a secret **page appears.
- Add the following secrets:
- **api-key**: For the **name **of your secret, enter `api-key`. For the corresponding **value**, enter the value from the [API Key Management](/zia/about-api-key-management) page on the Cloud & Branch Connector Admin Portal.
- **password**: For the **name **of your secret, enter `password`. For the corresponding **value**, enter your Cloud & Branch Connector Admin Portal password.
- **username**: For the **name **of your secret, enter `username`. For the corresponding **value**, enter your Cloud & Branch Connector Admin Portal username.
[See image.](#enabled-secrets)
- Click** Create**.
[See image.](#create-secret)
[]Create an SSH key pair:
- Log in to the [Azure Portal](https://portal.azure.us/).
- Go to **SSH keys**, then click** Create**.
The **Create an SSH key **page appears.
- On the **Basics** tab:
- **Subscription**: From the drop-down menu, select the subscription with user access administrator permission to manage deployed resources.
- **Resource Group**: Select the resource group in which you want to create the SSH key pair or click **Create new** to create a new resource group.
- **Region**: From the drop-down menu, select the desired region in which to deploy the newly created resource group. If you do not select a region, the SSH key region will be in the same region as the existing resource group selected above.
- **Key pair name**: Enter a name for your key pair.
-
**SSH public key source**: From the drop-down menu, select **Generate new key pair**.
[See image.](#SSHKey-Basics)
- Click **Next: Tags >**.
- On the **Tags** tab, configure tags to categorize resources, then click **Next: Review + create >**.
- On the **Review + create **tab, review your SSH key configurations, and then click** Create**.
Deploying the Cloud Connector
If you want to configure your own virtual network and subnets, you must do so before launching the Zscaler Cloud Connector Application. When you deploy Cloud Connector in the Azure Marketplace, accelerated networking is enabled by default. To learn more about accelerated networking, refer to the [Azure documentation](https://learn.microsoft.com/en-us/azure/virtual-network/accelerated-networking-overview).
After you have met all the prerequisites, perform the following procedures to deploy your Cloud Connector:
- [1. Deploy the Zscaler Cloud Connector Application.](#deploy)
- [2. Send traffic to your load balancer.](#traffic)
- [3. Disable disk network access.](#disablenetwork)
[]Use one of the following methods to deploy your Cloud Connector:
- [Zscaler Cloud Connector Application in the Azure Marketplace](#deployMarketplace)
- [Terraform (Required for VMSS and deployment in China)](#deployTerraform)
[]
To deploy your Cloud Connector using Azure Marketplace:
- Log in to the [Azure Portal](https://portal.azure.us/).
- Under **Marketplace**, search for `Zscaler Cloud Connector Application`.
- Click **Create** and then select **Zscaler Cloud Connector Application**.
The **Zscaler Cloud Connector Application** page appears.
- On the **Basics** tab:
- **Subscription**: Select the subscription with user access administrator permission to manage deployed resources.
- **Resource group**: Click **Create new** to create a new resource group or select an existing resource group to deploy the Zscaler Cloud Connector Application.
-
**Region**: Select the desired region for your deployment.
[See image.](#zscalercloudconnector-basics)
- Click **Next**.
- On the **Zscaler Settings** tab:
- **Provisioning Template URL**: Paste your Cloud Connector provisioning template URL.
- **Cloud Connectors Instance Type**: The Cloud Connector instance type is set to **Small** by default.
- **Zscaler Cloud Connector VM Size for small CC Instance Types**: The VM size is set automatically to **1x Standard D2s v3**. To change the VM size, click **Change size**.
- **Enable Encryption At Host**: Select the checkbox to enable end-to-end encryption using encryption at host. The subscription's account admin must enable this feature. To learn more about host encryption, refer to the[ Azure product documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/disks-enable-host-based-encryption-portal?tabs=azure-powershell&WT.mc_id=Portal-Microsoft_Azure_CreateUIDef).
- **Zscaler Cloud Connector VM Public Key Source**: Select **Azure Key Pair** to select an existing SSH key pair or **SSH Public Key **to paste your SSH key directly.
- **Zscaler Cloud Connector VM SSH Keys**: From the drop-down menu, select your SSH key.
- **Zscaler Cloud Connector Key Vault Source**: Select the source that your key vault belongs to.
- **Zscaler Cloud Credentials Key Vault**: Select the key vault where your Zscaler cloud credentials are stored.
- **User assigned managed identity**: Click **Add** to add the user-managed identity with access to the key vault and network contributor role. You must select a user-assigned managed identity before you can move to the next step.
- [See image.](#zscalercloudconnector-zscalersettings)
- Click **Next**.
- On the **Load Balancer Settings **tab:
- **Opt out from configuring a Load Balancer**: Select this setting to opt out from configuring a load balancer. Only select this setting when deploying in a non-production environment.
- **Choose an existing load balancer**: Select this setting to choose a load balancer that is already operating in this environment.
- **Number of Cloud Connectors**: Select the number of Cloud Connectors.
- **HTTP Probe Port for Load Balancer**: Enter the HTTP Probe Port `80` or `1024` to `65535`. If selecting an existing load balancer, ensure that the ports match.
-
**Availability Sets and Availability Zones**: Select either **Availability Sets** or **Availability Zones**.
[See image.](#loadbalancersettings)
- Click **Next**.
- On the **Network Settings **tab:
-
**Availability Zones**: Select up to three availability zones. This option is only displayed if you selected **Availability Zones **on the **Load Balancer Settings **tab.
[See image.](#networksettings-availabilityzone)
- **Virtual Network**: The virtual network in the resource group into which the Cloud Connector is deployed. By default, a new virtual network is automatically created. Alternatively, you can select another virtual network from the drop-down menu.
-
**zsccSubnet1**: The subnet in the resource group and virtual network into which the Cloud Connector is deployed. By default, a new subnet is automatically created. Alternatively, you can select another subnet from the drop-down menu. The subnet options that appear in the drop-down menu depend on the number of availability zones you select. There can be one subnet per availability zone.
[See image.](#zscalercloudconnector-networksettings)
- On the **Tags** tab, configure tags to categorize resources, then click **Next**.
- On the **Review + Create** tab, review the summary of your configurations, then click** Create**.
[]
Cloud Connector with VMSS deployment requires using the [Terraform Deployment Template with Virtual Machine Scale Sets (VMSS)](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector) and a new [Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template) with **Auto Scaling** set to **Enabled**. To enable Auto Scaling, contact Zscaler Support.
To deploy your Cloud Connector using Terraform:
- Go to the [Azure on GitHub](https://github.com/zscaler/terraform-azurerm-cloud-connector-modules) repository.
- On GitHub, click **Code **> **Download Zip** to download the Terraform zip file.
- Log in to the [Azure Portal](https://portal.azure.us).
- In the upper-right corner, click the **Cloud Shell** icon.
- Select **Manage Files** > **Upload** to upload the ZIP file you downloaded from GitHub.
- Click **Upload **again to upload the service account JSON file created.
-
Unzip the Terraform ZIP file by running the following command:
`unzip terraform-azure-cloud-connector-modules-main.zip`
- Identify the full path of the Terraform folder and JSON file.
- Navigate to the examples directory by entering `cd terraform-azure-cloud-connector-modules-main/examples`.
- Enter` ./zsec up` to initate the deployment wizard. The deployment wizard automatically downloads, installs, and initiates the Terraform JSON file.
[]After you complete your deployment from the Azure Portal, you must create a routing table and a workload subnet to redirect traffic to your load balancer.
To send traffic to your load balancer:
- Log in to the [Azure Portal](https://portal.azure.us/).
- Go to **Virtual networks**, then select the virtual network into which your Cloud Connector is deployed.
- In the left-side navigation, click **Subnets**, then click **+ Subnet**.
- In the **Add subnet **window that appears, add a **Name **and a **Subnet address range** for the workload subnet.
- Click **Save**.
- Go to** Route tables**.
- Click **Create**.
The **Create Route table** page appears.
- On the **Basics** tab:
- **Subscription**: Select the subscription with user access administrator permission to manage deployed resources.
- **Resource Group**: Select the resource group in which you want to create the workload route table.
- **Region**: From the drop-down menu, select the desired region for your deployment.
- **Name**: Enter a name for your workload route table.
- **Propagate gateway routes**: Select **Yes** to propagate gateway routes, or **No** to prevent the propagation of routes to the network interfaces in associated subnets.
[See image.](#Create-routetable)
- Click **Next: Tags >**.
- On the **Tags** tab, configure tags to categorize resources, then click **Next: Review + create >**.
- On the **Review + create **tab, review the summary of your configurations, and then click** Create**.
- Select your newly created workload route table and click **Routes**.
- Click **Add**.
- On the** Add route** page, enter the following information:
- **Route name**: Enter a name for the workload route.
- **Address prefix destination**: From the drop-down menu, select **IP Addresses**.
- **Destination IP addresses/CIDR ranges**: Enter 0.0.0.0/0.
- **Next hop type**: From the drop-down menu, select **Virtual appliance**.
- **Next hop address**: Enter the front-end IP address of your load balancer. To find the IP address, locate your deployed load balancer and select** Frontend IP configuration**.
[See image.](#Addroute)
- Click **OK**.
- Click **Subnets**, then click **Associate**.
- In the **Associate subnet **window, from the drop-down menu, select your **Virtual network** and workload **Subnet**.
- Click **OK**.
[]Zscaler recommends manually disabling network access to the managed disks attached to your deployed Cloud Connector.
To disable network access:
- Log in to the [Azure Portal](https://portal.azure.us/).
- Go to **Resource groups**, then locate the Cloud Connector resource group and click the deployed Cloud Connector.
[See image.](#resourcegroup-ccvm)
- In the left-side navigation, click **Disks**. Under **OS Disk**, select the **Disk name**.
[See image.](#OSdisk)
- In the left-side navigation, click **Networking**.
- Under **Network access**, select** Disable public and private access**.
[See image.](#disablenetworkaccess)
- Click **Save**.
Managing the Cloud Connector
[]After your VM is fully deployed, you can manage the Cloud Connector from the Cloud & Branch Connector Admin Portal. A deployed Cloud Connector is displayed on the dashboard. The [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation (shown below), and status of your Cloud Connector VMs deployed in your cloud account.
[See image.](#geo)
[]![An active VM from the Branch and Cloud Connector Monitoring page](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-51570/cc-active-azure-vm.png)
After verifying deployment, you can configure the following policies:
- [Zscaler Internet Access Gateways](/cloud-branch-connector/about-zia-gateways)
- [Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding)
- [Log and Control Forwarding](/cloud-branch-connector/about-log-and-control-forwarding)
- [DNS Control](/cloud-branch-connector/about-dns-control)
If you are deploying Cloud Connector in China, Zscaler recommends creating a custom gateway with Zscaler China data centers and traffic forwarding policies referencing your China location and custom gateway. To learn more, see [China Premium Internet Access ](/zia/china-premium-internet-access)and[ Deploying Zscaler Internet Access in China](/zia/deploying-zscaler-internet-access-china).
[]![The Basics tab of the Create User Assigned Managed Identity window. ](/downloads/cloud-connector/deploying-cloud-connector-microsoft-azure/CreateUserAssignedManagedIdentity_Basics.png)
[]![The Add role assignment (Preview) window in Microsoft Azure. ](/downloads/cloud-connector/deploying-cloud-connector-microsoft-azure/Addroleassignment(Preview).png)
[]![The Basics tab of the Azure Key Vault. ](/downloads/cloud-connector/deploying-cloud-connector-microsoft-azure/KeyVault-Basicstab.png)
[]![The Create a Key Vault page where you configure access configuration settings](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMCreateKeyVault.png)
[]![Networking tab where you configure key vault network access](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMCreateKeyVaultNetworking.png)
[]![Key vault Overview page with link to the new key vault](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMGoToResource.png)
[]![Key vault Access control page where you add a role assignment](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMAddRoleAssignment.png)
[]![Assigning the Key Vault Secrets User role from a table with columns for Name, Description, Type, Category, and Details](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/role_assignment_KeyVaultSecretsUser.png)
[]![Defining key vault access to a managed identity. The Assign access to options are User, group, or service principal and Managed identity, which is the correct option. There is an optional Description text field, and a Select members link that opens the Select managed identities window used in the next step.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMAddRoleAssignmentMembers.png)
[]![Selecting the managed identity to assign to the Key Vault Secrets User. There are fields for Subscription, Managed identity type, and a list of managed identities to select from](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMSelectManagedIdentiesPane.png)
[]![Image]()
![Verifying the managed identity associated with the Key Vault Secrets User role](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-52833/IAMVerify.png)
[]![The Access policy tab of the Create a Key Vault window for Vault access policy. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/CreateKeyVault-AccessPolicyTab.png)
[]![The secret permissions in the Create an access policy window. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/CreateanAccessPolicy-SecretPermissions.png)
[]![Managed Identity ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-doc-48566/Demo-Managed-Identity.png)
[]![The Create a secret window in Azure. ](/downloads/cloud-connector/deploying-cloud-connector-microsoft-azure/Createasecret_Azure.png)
[]![The Basics tab of the Create an SSH Key Pair window. ](/downloads/cloud-connector/deploying-cloud-connector-microsoft-azure/CreateSSHKeyPair_Basics.png)
[]![The Basics tab of the Zscaler Cloud Connector Application in Azure. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/Basicstab_Azure_3.png)
[]![The Network settings tab of the Zscaler Cloud Connector Application in Azure. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/NetworkSettings_AvailabilitySets_Azure.png)
[]![The Zscaler Settings tab of the Zscaler Cloud Connector Application in Azure. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-microsoft-azure-draft-doc-48507-doc-47788/ZscalerSettings_ZscalerCloudConnector_AzurePortal.png)
[]![The Basics tab of the Create a Route Table in Azure. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/Routetable-LoadBalancer.png)
[]![The Add route window in Azure. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/AddRouteforLoadBalancer2.png)
[]![Secrets including the api-key, password, and username added to the Azure Key Vault.](/downloads/cloud-connector/getting-started/admin-portal/about-cloud-connector-portal/Secrets-Keyvault.png)
[][![The Load Balancer Settings tab in Zscaler Cloud Connector Application in the Azure Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/LoadBalancerSettings_AvailabilityZones.png)
](undefined)
[][![The Network Settings tab in Zscaler Cloud Connector Application in the Azure Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure/NetworkSettingswithAvailabilityZones_Azure.png)
](undefined)
[]![The deployed Cloud Connector via the Cloud Connector Resource Group in the Azure Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure-draft-doc-47755/ResourceGroup_DeployedCloudConnector_Azure.png)
[]![The Cloud Connector VM from the Disks page in the Azure Portal.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure-draft-doc-47755/Disks_OSDisk_DiskName_CloudConnector_Azure.png)
[]![Disable public and private access under Network access via the Networking tab.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-microsoft-azure-draft-doc-47755/DisableNetworkAccess_CloudConnector_Azure.png)