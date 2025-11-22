# Configuring the Azure Network
Source: https://help.zscaler.com/dspm/configuring-azure-network
PDF: https://help.zscaler.com/pdf/com/en/1510726.pdf

DSPM requires a specific network configuration to be able to access the Azure services, scan the resources, compute, and report the findings. You can configure either a custom network in your organization or use the DSPM-provided network setup.
For a custom network, you need to select an orchestrator subscription while [onboarding the Azure cloud accounts](/dspm/onboarding-microsoft-azure-tenant) and create the following virtual networks (VNets) in the orchestrator subscription:
- **Control Plane VNet**: Create this VNet only in the primary region where the orchestrator is going to run.
- **Worker Plane VNet**: Create this VNet in all the regions where the resources exist. For example, if the Azure storage accounts are stored in East US and Central US regions, create the worker plane VNet in both regions.
Ensure that both control and worker plane VNets do not have overlapping Classless Inter-Domain Routing (CIDR).
Configure Azure Network
You can configure the Azure network manually or deploy the predefined templates:
- [Manual Configuration](#azure_manual_configuration)
- [Deploy Predefined Templates](#azure_template_configuration)
Peer the VNets
After creating the control and worker plane VNets, you need to peer these VNets so they can communicate with each other. This step is common for both manual and template-based configurations.
- Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Virtual networks** page.
- Select the **Control plane VNet**.
- Go to **Settings** > **Peerings** > **Add**.
-
On the **Add peering** page:
- **Peering link name**: Enter a name for the peering link.
- **Virtual network deployment model**: Retain the default selection.
- **Subscription**: Select the orchestrator subcription from the drop-down menu.
- **Virtual network**: Select the worker plane VNet from the drop-down menu.
- **Remote virtual network peering**: Retain the default value.
- **Local virtual network summary**: Enter the peering link name.
- **Local virtual network peering** : Retain the default value.
-
Click **Add**.
[See image.](#ds-azurevnet-peering)
After the peering is successfully configured, the **Peering state** is updated to **Connected** and the **Sync status** to **Fully Synchronized**. Repeat the steps for other target regions
[]To configure the Azure network manually:
- [1. Create the control plane VNet.](#ds-az-createcpvnet)
- [2. Create the worker plane VNet.](#ds-az-createwpvnet)
- [3. Configure the control plane network security group.](#ds-az-edit-cpnetworksg)
- [4. Configure the worker plane network security group.](#ds-az-edit-wpnetworksg)
- [5. Configure the network security group for Azure PostgreSQL Server.](#ds-config-nsg-postgresql)
[][]A network security group needs to be created and configured to ensure communication with Azure PostgreSQL Server.
- Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Network security groups** page, and click **Create**.
-
On the **Create network security group** page:
- **Subscription**: Select the subscription where the custom configuration worker plane is created.
- **Resource group**: Select the resource group where the custom configuration worker plane is created.
- **Name**: Enter a name for the security group.
- **Region**: Select the same region where the [worker plane VNet](#ds-az-createwpvnets) is created.
- Click **Review + Create**.
[See image.](#ds-img-create-nsg-postgresql)
- Click **Create**.
-
Configure security rules.
Add a rule to allow PostgreSQL inbound.
- Open the created security group and go to **Settings** > **Inbound security rules**.
- Click **Add**.
-
On the **Add inbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any** from the drop-down menu.
- **Service**: Select **PostgresSQL** from the drop-down menu.
- **Action**: Select the **Allow **option.
- **Priority**: Set **100**.
- **Name**: Enter a name for the rule.
[See image.](#ds-img-az-sgrule-allow-postgresql-inbound)
- Click **Add**.
Add a rule to deny all inbound communication to the orchestrator.
- Open the created security group and go to **Settings** > **Inbound security rules**.
- Click **Add**.
-
On the **Add inbound security rules** page:
- **Source**: Select **Any** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any** from the drop-down menu.
- **Service**: Select **Custom **from the drop-down menu.
- **Action**: Select the **Deny **option.
- **Priority**: Set **2000**.
- **Name**: Enter a name for the rule.
[See image.](#ds-img-az-sgrule-denyallinbound)
- Click **Add**.
Add a rule to deny internet access.
- Open the created security group and go to **Settings** > **Outbound security rules**.
- Click **Add**.
-
On the **Add outbound security rules** page:
- **Source**: Select **Any** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any** from the drop-down menu.
- **Destination service tag**: Select **Internet** from the drop-down menu.
- **Service**: Select **Custom **from the drop-down menu.
- **Destination port ranges**: Enter an asterisk (*).
- **Priority**: Set **2010**.
- **Name**: Enter a name for the rule.
[See image.](#ds-img-az-sgrule-deny-internet)
- Click **Add**.
[]![Creating an Azure security group rule to deny all outbound traffic to internet.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-az-sgrule-deny-internet.png)
[]![Creating an Azure security group rule to deny all inbound communication.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-az-sgrule-denyallinbound.png)
[]![Creating an Azure security group rule to allow PostgreSQL inbound.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-az-sgrule-allow-postgresql-inbound.png)
[]![Creating a new security group for the Azure PostgreSQL server](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-create-nsg-postgresql.png)
[]To deploy the templates:
- [1. Create a resource group for the control plane.](#RG_control_plane)
- [2. Create a resource group for the worker plane.](#RG_worker_plane)
- [3. Download and configure the template.](#config_template)
- [4. Initialize the template.](#initiate)
- [5. Deploy the control plane template.](#deploy_control_plane_template)
- [6. Deploy the worker plane template.](#deploy_worker_plane_template)
- []Sign in to the [Azure portal](https://portal.azure.com/) and [create a new resource group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal) or select an existing one.
- On the **Create a resource group** page, on the **Basics** tab, provide the details:
- **Subscription**: Select your Azure subscription from the drop-down menu.
- **Resource Group**: Enter a name for the resource group.
- **Region**: Choose the location where you want to create the resource group from the drop-down menu.
-
Click **Next: Tags >**.
[See image.](#ds-img-create-rs-cp)
-
In the **Tags **tab, add the following tags:
- Tag 1: **Name** = `<tag_name>`, **Value** = `<tag_value>`.
- Tag 2: **Name** = `<owner>`, **Value** = `<your_name>`.
Replace `<tag_name>`, `<tag_value>`, `<your_name>` with appropriate values.
[See image.](#ds-img-az-cp-rg-tags)
- Click **Next: Review + create >**.
- In the **Review + create **tab, click **Create**.
[]![Adding tags for the resource group for control plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-az-cp-rg-tags.png)
[]![Creating an Azure resource group for control plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-create-rs-cp.png)
- []Sign in to the [Azure portal](https://portal.azure.com/) and [create a new resource group](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups-portal) or select an existing one.
- On the **Create a resource group** page, on the **Basics** tab, provide the details:
- **Subscription**: Select your Azure subscription from the drop-down menu.
- **Resource Group**: Enter a name for the resource group.
- **Region**: Choose the location where you want to create the resource group from the drop-down menu.
-
Click **Next: Tags >**.
[See image.](#ds-img-create-rs-wp)
-
In the **Tags **tab, add the following tag:
- Tag 1: **Name** = `<owner>`, **Value** = `<your_name>`.
Replace `<your_name>` with the appropriate value.
[See image.](#ds-img-az-wp-rg-tags)
- Click **Next: Review + create >**.
- In the **Review + create **tab, click **Create**.
[]![Adding tags for the resource group for worker plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-az-wp-rg-tags.png)
[]![Creating an Azure resource group for worker plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-img-create-rs-wp.png)
-
[]Download the Azure Network Configuration template file as a ZIP file and extract it to a folder on your system.
[Download the template](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/azure_network_components.zip)
- Open the `control-plane` folder and locate the `backend.tf` file in the folder and open it in a text editor.
-
Update the following details in the `backend.tf` file:
- **resource_group_name**: Update the `<resource_group_name>` with the resource group of the storage account where you want to save the Terraform state files.
- **storage_account_name**: Update the `<storage_account_name>` with the name of the storage account.
- **container_name**: Update the `<container_name>` with the name of the container.
- **key**: unique key for the storage account.
[See image.](#ds-control-plane-backendtf)
For more information on the fields, refer to the `README.md` file.
- Save and close the `backend.tf` file.
- Open the `worker-plane` folder and locate the `backend.tf` file in the folder and open it in a text editor.
-
Update the following details in the `backend.tf` file:
- **resource_group_name**: Update the `<resource_group_name>` with the resource group of the storage account where you want to save the Terraform state files.
- **storage_account_name**: Update the `<storage_account_name>` with the name of the storage account.
- **container_name**: Update the `<container_name>` with the name of the container.
- **key**: unique key for the storage account, including the region where you want to configure the network.
[See image.](#ds-worker-plane-backendtf)
For more information on the fields or region format, refer to the `README.md` file.
- Save and close the `backend.tf` file.
[]![Editing the backend.tf file for updating the configuration details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-controlplane-backend-tf.png)
[]![Editing the backend.tf file for updating the configuration details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-workerplane-backend-tf.png)
[]Use any of the following methods:
- [Cloud Shell](#cloudshell)
- [Command Prompt](#initiate_cmd)
- []Sign in to the Azure portal, and click **Cloud Shell**.
-
In the **Welcome to Azure Cloud Shell** window, select **Bash **or **PowerShell**, as required.
[See image.](#selectpowershell)
-
In the **Getting started** window:
- Select **Mount storage account**.
- Select the storage account subscription from the list.
- Click **Apply**.
[See image.](#gettingstarted-selectsubscription)
-
In the **Mount storage account** window, select **Select existing storage account **and click **Next**.
[See image.](#mountstorage-account)
-
In the **Select storage account** window:
- **Subscription**: Select the subscription where the storage account is created.
- **Resource group**: Select the resource group from the list.
- **Storage account name**: Select the storage account.
- **File share**: Click **Create a file share **and enter a name for the new file.
- Click **Select**.
[See image.](#select-storage-account)
- Use any of the following:
- [Azure PowerShell](#powershell)
- [Bash](#deploy-template-bash)
[]![The Azure Cloud Shell welcome screen with options to select the any of the Bash or PowerShell enviornment.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azure-select-powershell.png)
[]![The Getting Started page, with  options to select a subscription, storage account mounting, and choose a virtual network.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/awzure-powershell-getting-started.png)
[]![The Mount storage account window, with the Select an existing storage option selected.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/select-existing-storage-account.png)
[]![The Select storage account page, with options to select subscription, resource group, storage account name, and file share.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/select-storage-account.png)
- []Open the Command Prompt or any other CLI app in your local system.
- Switch to the directory containing the downloaded Terraform file.
-
Connect to the Microsoft Entra tenant by running the following command:
`az login --tenant <[tenant ID](#tenantID)>`
[See image.](#azurelogintenant)
You are directed to a web browser to authorize the Microsoft Entra tenant. Select your account to confirm the authorization.
[See image.](#authorizationpage)
The command output returns the subscriptions available.
[]![Command prompt window with Azure login command with tenant ID.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-connect-to-azure.png)
[]![Microsoft Azure login screen with options to pick an account, or to use another account.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/azureauthorizationpage.png)
-
[]Zip the modified template and upload the folder to the PowerShell environment:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
[See image.](#upload-template-file)
-
Run the following commands:
-
To move the `azure_network_components.zip` file from its current location to the `/home/``<user_name>``/clouddrive` folder:
`mv azure_network_components.zip  /home/<user_name>/clouddrive`
Replace `<user_name>` with appropriate values.
-
To switch to the clouddrive folder:
`cd /home/<user_name>/clouddrive`
Replace `<user_name>` with appropriate values.
-
To extract the `azure_network_components.zip` file:
`unzip azure_network_components.zip`
The `azure_network_components.zip` file contains two folders: `control-plane` and `worker-plane`.
-
To switch to the extracted template folder:
`cd <folder name>`
Replace `<folder name>` with `control-plane` or `worker-plane`, depending on the template to deploy.
[See image.](#img-azure-powershell-commands)
[]![Azure PowerShell window with the commands.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/ds-byon-azure-powershell-commands.png)
[]![Terminal window showing successful file upload notification.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/ds-byon-azure-powershell-upload.png)
-
[]Run the following commands to prepare the Bash environment:
- Click **Manage files** and select **Upload**.
- Browse for the template and click **Open**.
[See image.](#upload-bash-template-file)
-
Run the following commands:
-
To move the `azure_network_components.zip` file from its current location to the `/home/``<user_name>``/clouddrive` folder:
`mv azure_network_components.zip  /home/<user_name>/clouddrive`
Replace `<user_name>` with appropriate values.
-
To switch to the clouddrive folder:
`cd /home/<user_name>/clouddrive`
Replace `<user_name>` with appropriate values.
-
To extract the `azure_network_components.zip` file:
`unzip azure_network_components.zip`
The `azure_network_components.zip` file contains two folders: `control-plane` and `worker-plane`.
-
To switch to the extracted template folder:
`cd <folder name>`
Replace `<folder name>` with `control-plane` or `worker-plane`, depending on the template to deploy.
[See image.](#img-azure-bash-commands)
[]![Azure Bash window with the commands.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/ds-byon-azure-bash-commands.png)
[]![Terminal window showing successful file upload notification.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/ds-byon-azure-bash-upload.png)
- []Set the Subscription and Initialize the Terraform Configuration
-
Open a terminal and run the following command to set the subscription where the storage containers containing the Terraform state files are stored:
`az account set --subscription <SUBSCRIPTION-ID>`
Replace `<SUBSCRIPTION-ID>` with the actual ID of your subscription.
-
To initialize the working directory and apply Terraform configuration:
`terraform init`
[See image.](#terraform-init)
-
Run the following command to deploy the control plane:
`terraform apply -auto-approve -var='control_plane_component_name=<CONTROL_PLANE_COMPONENT_NAME>' -var='control_plane_region=<CONTROL_PLANE_REGION>' -var='control_plane_vnet_cidr=["<CONTROL_PLANE_VNET_CIDR>"]' -var='control_plane_vnet_subnet_address_range=["<CONTROL_PLANE_VNET_SUBNET_ADDRESS_RANGE>"]' -var='resource_group=<RESOURCE_GROUP>' -var='scanner_subscription_id=<SCANNER_SUBSCRIPTION_ID>' -var='outbound_ips=["<IP_1>","<IP_2>","<IP_3>","<IP_4>"]'`
Replace the placeholders with the actual values:
- `<CONTROL_PLANE_COMPONENT_NAME>`: The name of the control plane component to be deployed.
- `<CONTROL_PLANE_REGION>`: The region where the control plane needs to be deployed in a format supported by the cloud provider, such as `centralus` or `eastus`.
- `<CONTROL_PLANE_VNET_CIDR>`: The CIDR block for the virtual network of the control plane, such as `10.0.0.0/24`.
- `<CONTROL_PLANE_VNET_SUBNET_ADDRESS_RANGE>`: The address range for subnet within the VNet of the control plane, such as `10.0.0.0/24`.
- `<RESOURCE_GROUP>`: The name of the resource group where the control plane needs to be deployed.
- `<SCANNER_SUBSCRIPTION_ID>`: The subscription ID of your cloud environment that will be used by the scanner.
- `<IP_#>`: The DSPM IP address that needs to be placed on the allowlist, such as `["``52.02.19.100``", "``52.02.19.111``", "``91.02.19.101``"]`
[]![The terminal window showing Terraform initialization process.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/onboarding-microsoft-azure-tenant/dspm-azure-terraform-init_0.png)
[]
-
Run the following command to provide back-end details for the new regions:
`terraform apply -auto-approve -var='control_plane_vnet_cidr=["<CONTROL_PLANE_VNET_CIDR>"]' -var='resource_group=<RESOURCE_GROUP>' -var='scanner_subscription_id=<SCANNER_SUBSCRIPTION_ID>' -var='worker_plane_component_name=<WORKER_PLANE_COMPONENT_NAME>' -var='worker_plane_region=<WORKER_PLANE_REGION>' -var='worker_plane_vnet_cidr=["<WORKER_PLANE_VNET_CIDR>"]' -var='worker_plane_vnet_subnet_address_range=["<WORKER_PLANE_VNET_SUBNET_ADDRESS_RANGE>"]' -var='worker_plane_vnet_subnet_postgres_address_range=["<WORKER_PLANE_VNET_SUBNET_POSTGRES_ADDRESS_RANGE>"]' -var='outbound_ips=["<IP_1>","<IP_2>","<IP_3>","<IP_4>"]'`
Replace the placeholders with the actual values for your:
- `<CONTROL_PLANE_VNET_CIDR>`: The CIDR block for the control plane VNet.
- `<RESOURCE_GROUP>`: The name of the resource group for the worker plane.
- `<SCANNER_SUBSCRIPTION_ID>`: The ID of the scanner subscription.
- `<WORKER_PLANE_COMPONENT_NAME>`: The name of the worker plane component.
- `<WORKER_PLANE_REGION>`: The region for the worker plane (e.g. centralus).
- `<WORKER_PLANE_VNET_CIDR>`: The CIDR block for the worker plane VNet.
- `<WORKER_PLANE_VNET_SUBNET_ADDRESS_RANGE>`: The address range for the worker plane VNet subnet.
- `<WORKER_PLANE_VNET_SUBNET_POSTGRES_ADDRESS_RANGE>`: The address range for the worker plane VNet subnet for Postgres.
- `<IP_#>`: The DSPM IP address that needs to be placed on the allowlist, such as `["``52.02.19.100``", "``52.02.19.111``", "``91.02.19.101``"]`
- []Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Virtual networks** page, and click **Create**.
-
On the **Create virtual network** page, on the **Basics** tab:
- **Subscription**: Select the orchestrator subscription from the drop-down menu.
- **Resource group**: Select the resource group from the drop-down menu.
- **Virtual network name**: Enter a name for the virtual network.
- **Region**: Select the primary region where the orchestrator is going to be deployed.
[See image.](#ds-az-create-network)
- Click **Next**.
- On the **Security** tab, select **Virtual network encryption** if the virtual machines used for scanning have network acceleration enabled.
- Click **Next**.
- On the **IP addresses** tab, enter the subnet address space, preferably** **`/24`.
-
Click the **Edit **icon for the subnet.
[See image.](#ds-az-editsubneticon)
- On the** Edit subnet** page, go to the **Security** section and complete the following:
-
Click **Create new** to add a new **NAT Gateway**.
[See image.](#ds-az-natgateway)
-
Enter the **Name**, **Public IP address**, and **Public IP prefix**, then click **OK**.
[See image.](#ds-az-natdetails)
-
Click **Create new** to add a new **Network security group**.
[See image.](#ds-az-netsgroup)
- Provide a name for the **Network security group**, then click **OK**.
- In the **Service Endpoints** section, add the following services:
- Microsoft.KeyVault
- Microsoft.Sql
- Microsoft.Storage.Global
- In the **Network Policy for Private Endpoints** section, select **Disabled**, then click **Save**.
- Click **Next**.
- Add tags for the **virtual network**.
- Click **Next**.
- Click **Create** on the **Review** page. The control plane VNet is created.
- [][]Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Virtual networks** page, and click **Create**.
-
On the **Create virtual network** page, on the **Basics** tab:
- **Subscription**: Select the orchestrator subscription from the drop-down menu.
- **Resource group**: Select the resource group from the drop-down menu.
- **Virtual network name**: Provide a name for the virtual network.
- **Region**: Select the region where the data stores are located.
[See image.](#ds-azure-createwpvnet)
- Click **Next**.
- On the **Security** tab, select **Virtual network encryption** if the virtual machines used for scanning have **Network acceleration** enabled.
- Click **Next**.
-
On the **IP addresses** tab, enter the subnet address space, preferably `/20`.
[See image.](#ds-azure-wp-ipaddresstab)
- Click the **Edit **icon for the default subnet.
-
On the **Edit Subnet **page, go to the **Security** section and complete the following:
- Click **Create new** to add a new **NAT Gateway**.
-
Enter the **Name**, **Public IP address**, and **Public IP prefix**, then click **OK**.
[See image.](#ds-azure-wp-natgw)
- Click **Create new** to add a new **Network security group**.
-
Provide a name for the **Network security group**, then click **OK**.
[See image.](#ds-azure-wp-addnetworksg)
- In the **Service Endpoints** section, add the following services:
- Microsoft.KeyVault
- Microsoft.Sql
- Microsoft.Storage.Global
- In the **Network Policy for Private Endpoints** section, select **Disabled**, then click **Save**.
[See image.](#ds-azure-wp-editsubnet)
- To enable the scanning for Azure PostgreSQL Server, you must [configure a network security group for Azure PostgreSQL Server](#link-config-nsg-postgresql), and then create a delegated subnet:
-
On the **IP addresses** tab, click **Add a subnet**.
[See image.](#img_postgre_addsubnet)
- On the **Add a subnet** page, enter the **Name**, and select the required **Network security group** for the subnet.
-
In the **Subnet Delegation** section, from the **Delegate subnet to a service** drop-down menu, select **Microsoft.DBforPostgreSQL/flexibleServers**, then click **Add**.
[See image.](#img_postgre_subnet_delegation)
- Click **Next**.
- Add tags for the **virtual network**.
- Click **Next**.
-
Click **Create** on the **Review** page.
The worker plane VNet is created. Repeat the steps for other regions where data stores need to be scanned.
[]Add the following inbound and outbound security rules for the control plane network security group. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal#security-rule-settings).
- Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Network security groups** page.
-
Select the **control plane network security group** you created while configuring the control plane.
Add a rule to deny all inbound communication to the orchestrator.
- Go to **Settings** > **Inbound security rules**.
- Click **+ Add**.
-
On the **Add inbound security rules** page:
- **Destination port ranges**: Enter an asterisk (*).
- **Action**: Select **Deny**.
- **Priority**: Enter the value as `2000`.
- **Name**: Enter a name for the rule.
[See image.](#ds-azure-addinbound-secrule)
- Click **Add**.
Add a rule to allow inbound communication from the control plane to the worker plane.
- Click **+ Add** on the **inbound security rules** page to add another rule.
-
On the **Add Inbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select** Service Tag** from the drop-down menu.
- **Destination service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **121** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-cp-inboundworkertocontrol)
- Click **Add**.
Next, add a rule to deny all outbound communication from the orchestrator with lesser priority.
- Go to **Settings** > **Outbound security rules**.
- Click **Add**.
-
On the **Add outbound security rules** page:
- **Destination port ranges**: Enter an asterisk (*).
- **Action**: Select **Deny**.
- **Priority**: Enter the value as `2000`.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-addoutbound-secrule)
- Click **Add**.
Add a rule to allow outbound communication from the orchestrator to DSPM.
- Click **+ Add** on the **Outbound security rules** page to add another rule.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **IP Addresses** from the drop-down menu.
- **Destination IP addresses/CIDR ranges**: Enter the [IP addresses.](#ds-iplist)
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter `443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **100** from the drop-down menu.
- **Name**: Enter the name for the rule.
[See image.](#ds-az-allowhttps-outboundsecurityrule)
- Click **Add**.
Add a rule to allow outbound communication from the orchestrator to Azure cloud.
- Click **+ Add** on the **Outbound security rules** page to add another rule.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select** Service Tag** from the drop-down menu.
- **Destination service tag**: Select **AzureCloud** from the drop-down menu.
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **110** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-cp-azurecloudoutbound)
- Click **Add**.
Add a rule to allow outbound communication from the orchestrator to the scanner.
- Click **+ Add** on the **Outbound security rules** page to add another rule.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select** Service Tag** from the drop-down menu.
- **Destination service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **120** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-cp-virtualnetworkoutbound)
-
Click **Add**.
The control plane network security group is configured.
[]Add the following inbound and outbound security rules for the worker plane network security group. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/azure/virtual-network/manage-network-security-group?tabs=network-security-group-portal#security-rule-settings).
- Sign in to the [Azure portal](https://portal.azure.com/).
- Go to the **Network security groups** page.
-
Select the worker plane network security group that you created earlier.
Add a rule to deny all inbound communication from the orchestrator with lesser priority.
- Go to **Settings** > **Inbound security rules**.
- Click **Add**.
-
On the **Add inbound security rules** page:
- **Destination port ranges**: Enter an asterisk (*).
- **Action**: Select the **Deny** option.
- **Priority**: Enter the value as `2000`.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-inboundrule1)
- Click **Add**.
Add a rule to allow inbound communication from the orchestrator to Azure cloud.
- Click **+ Add** on the **Inbound security rules** page.
-
On the **Add inbound security rules** page:
- **Source**: IP Addresses
- **Source IP addresses/CIDRranges**: Enter the CIDR range of control plane VNet.
- **Destination**: Select **Any** from the drop-down menu.
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Action**: Select the **Allow** option.
- **Priority**: Select **101** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-orchestraterinboundrule)
- Click **Add**.
Next, add an outbound security rule to deny all outbound communication from the orchestrator to Azure cloud.
- Go to **Settings** > **Outbound security rules**.
- Click **Add**.
-
On the **Add outbound security rules** page:
- **Destination port ranges**: Enter an asterisk (*).
- **Action**: Select the **Deny** option.
- **Priority**: Enter the value as `2000`.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-outboundrule1)
- Click **Add**.
Add a rule to allow outbound communication from the worker plane to DSPM.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **IP Addresses** from the drop-down menu.
- **Destination IP addresses/CIDR ranges**: Enter the [IP addresses.](#ds-iplistcidr)
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **100** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-addhttpsoutboundrule)
- Click **Add**.
Add a rule to allow outbound communication from the worker plane to Azure cloud.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **ServiceTag** from the drop-down menu.
- **Destination service tag**: Select **AzureCloud** from the drop-down menu.
- **Service**: Select **HTTPS** from the drop-down menu.
- **Destination port ranges**: Enter** **`443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **101** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-azureoutbound)
- Click **Add**.
Add a rule to allow all outbound communication from the worker plane to the SQL database.
- Click **+ Add** on the **Outbound security rules** page to add another rule.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any** from the drop-down menu.
- **Service**: Select **MS SQL** from the drop-down menu.
- **Destination port ranges**: Enter** **`1443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **102** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-dbportoutbound)
- Click **Add**.
Add a rule to allow all outbound communication from the worker plane to SQL database.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **ServiceTag** from the drop-down menu.
- **Destination service tag**: Select **SQL** from the drop-down menu.
- **Service**: Select **Custom** from the drop-down menu.
- **Destination port ranges**: Enter the value as `11000-11999`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **103** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-outbounddbportredirect)
- Click **Add**.
Add a rule to allow all outbound communication from the worker plane to postgreSQL database.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any** from the drop-down menu.
- **Service**: Select **PostgreSQL** from the drop-down menu.
- **Destination port ranges**: Enter the value as `5432`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **104** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-allowanypostgresql)
- Click **Add**.
Add a rule to allow outbound communication from the worker plane to the control plane.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Service Tag **from the drop-down menu.
- **Destination service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Service**: Select **HTTPS **from the drop-down menu.
- **Destination port ranges**: Enter the value as `443`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **121** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-outbound-wptocp)
- Click **Add**.
Add a rule to deny internet access.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Any** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Service Tag **from the drop-down menu.
- **Destination service tag**: Select **Internet **from the drop-down menu.
- **Service**: Select **Custom **from the drop-down menu.
- **Destination port ranges**: Enter an asterisk (*).
- **Protocol**: Select the **TCP **option.
- **Action**: Select the **Deny** option.
- **Priority**: Enter **2010.**
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-deny-internet)
- Click **Add**.
Add a rule to allow MySQL ports.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any **from the drop-down menu.
- **Service**: Select **MySQL **from the drop-down menu.
- **Destination port ranges**: Enter the value as `3306`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **107** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-mysql-port)
- Click **Add**.
Add a rule to allow Oracle ports.
- Click **+ Add** on the **Outbound security rules** page.
-
On the **Add outbound security rules** page:
- **Source**: Select **Service Tag** from the drop-down menu.
- **Source service tag**: Select **VirtualNetwork** from the drop-down menu.
- **Source port ranges**: Enter an asterisk (*).
- **Destination**: Select **Any **from the drop-down menu.
- **Service**: Select **Custom **from the drop-down menu.
- **Destination port ranges**: Enter the value as `1521`.
- **Protocol**: Select the **TCP** option.
- **Action**: Select the **Allow** option.
- **Priority**: Select **108** from the drop-down menu.
- **Name**: Enter a name for the rule.
[See image.](#ds-az-wp-oracle-port)
- Click **Add**.
- The worker plane network security group is configured. Repeat the steps for other target regions.
[]![Add an outbound security rule window to allow MySQL ports for worker plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/img-ds-az-wp-oracle-port.png)
[]![Add an outbound security rule window to allow MySQL ports for worker plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/img-ds-az-wp-mysql-port.png)
[]![Add an outbound security rule window to allow outbound communication from the worker plane to the control plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-outbound-wptocp.png)
[]![Add outbound security rule windiow for adding an outbound security rule to deny internet.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-deny-internet.png)
[]![Add outbound security rule windiow for adding an outbound security rule to allow outbound communication from the worker to postgreSQL database.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-postgresql.png)
[]![The Create virtual network page, displaying options for selecting the subscription, resorce group, virtual network name, and region to deploy.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-createnetwork.png)
[]![The Create virtual network page, with the IP address tab selected, for the subnet address field with an annotation around edit icon to edit the subnet.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-editsubnet.png)
[]![The Edit subnet page for selecting the NAT gateway and the Network security group.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-newnat.png)
[]![The Create virtual network page with IP Address tab selected, with an annotation around the Add a subnet option.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/postgre_addsubnet.png)
[]![The Add a subnet page with an annotation around the subnet delegation option to assign a subnet to a service.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/postgre_subnet_delegation.png)
[]![The Add a NAT gateway page with fields for name, public IP address, and public IP prefix.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-natgatewaydetails.png)
[]![Add a network security group dialog box with a field to specify the name of the security group.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-netsecuritygroup.png)
[]![The Create virtual network page with the Basics tab selected to choose the subcription, resource group, virtual network name and region to deploy.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-createworkerplanevnet.png)
[]![The Create virtual network page, with the IP address tab selected, for the subnet address field with an annotation around edit icon to edit the subnet.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-createwp-ipaddresstab.png)
[]![The Edit subnet page for selecting the NAT gateway and the Network security group.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-createwp-editsubnet.png)
[]![The Add a NAT gateway page with fields for name, public IP address, and public IP prefix.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-createwp-natgw.png)
[]![The Add peering page to connect two virtual networks.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-peervnets.png)
[]![Add a network security group dialog box with a field to specify the name of the security group.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-wp-addnetworksg.png)
- []US cloud:
- `54.188.198.110`
- `52.38.65.228`
- `35.162.237.153`
- `54.203.244.84`
- `100.20.13.195`
- `44.232.83.106`
- EU cloud:
- `3.78.36.199`
- `18.153.255.114`
- `18.193.231.22`
- `3.78.50.170`
- `35.159.181.237`
- `35.157.194.12`
- []US cloud:
- `54.188.198.110`
- `52.38.65.228`
- `35.162.237.153`
- `54.203.244.84`
- `100.20.13.195`
- `44.232.83.106`
- EU cloud:
- `3.78.36.199`
- `18.153.255.114`
- `18.193.231.22`
- `3.78.50.170`
- `35.159.181.237`
- `35.157.194.12`
[]![Add inbound security rule page to deny all inbound communication.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-addinboundsecrule.png)
+
[]![Add inbound security rule page to allow inbound communication from the worker plane to the control plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-cp-inboundworkertocontrol.png)
[]![Add outbound security rule page to deny all outbound communication.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-addoutboundsecrule.png)
[]![Add outbound security rule page to allow HTTPS traffic.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-allowhttpsoutboundrule.png)
[]![Add inbound security rule page to add an inbound security rule for worker plane](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-denyinboundrule.png)
[]![Add inbound security rule page to add an inbound rule allowing inbound communication.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-orchestratorinboundrule.png)
[]![Add outbound security rule page to add an outbound rule denying  outbound communication.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-denyoutboundrule.png)
[]![Add outbound security rule page to add an outbound rule to allow HTTPS traffic.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-httpsoutboundrule.png)
[]![Add outbound security rule page to add an outbound rule for Azure cloud.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-allow-azureoutboundrule.png)
[]![Add outbound security rule page to add an outbound rule for DB ports.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-allowdb_portsoutboundrule.png)
[]![Add outbound security rule page to add an outbound rule for DB port redirect.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-az-wp-allowdbports-outboundruleredirect.png)
[]![Add outbound security rule page to add an outbound rule for control plane.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-cp-azcloudoutbound.png)
[]![Add outbound security rule page to add an outbound rule for virtual network.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-azure-cp-allow-virtual-network-outbound.png)