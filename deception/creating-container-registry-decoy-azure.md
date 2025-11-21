# Creating a Container Registry Decoy in Azure
Source: https://help.zscaler.com/deception/creating-container-registry-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531496.pdf

An Azure Container Registry (ACR) is a service in Microsoft Azure that hosts Docker and Open Contain Initiative (OCI) images. You can create a container registry decoy (public or private) that detects the following attack paths:
- Pull: Adversaries look for images in the container registry to access the files to extract credentials or steal application code.
- Push: Adversaries can attempt supply chain attacks by pushing a vulnerable image to a container registry for persistence.
You can also use a [landmine policy](/deception/about-policies) to lure attackers to container registry decoys by adding URLs and credentials.
Prerequisites
Before creating a container registry decoy in Azure, you must ensure that you have:
- Configured the [integration between Microsoft Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Container Registry Decoy
To create a container registry decoy:
- Go to **Deceive **> **Cloud Deception **> **Azure **> **Container Registry**.
-
Click **Add Decoy**.
[See image.](#zd-azure-tab-cr)
The **Container Registry Decoy **window appears.
-
In the **Container Registry** **Decoy** window:
- **Name**: Enter a name for the container registry decoy.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed from the drop-down menu.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when selecting an existing resource group, the deployment region of the decoy and the resource group can be different.
- **Description**: Enter a description relevant to the container registry decoy.
[See image.](#zd-container-registry-add)
- Click **Save**.
- Sign in to the [Azure Portal](http://https://portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell** icon on the top navigation bar.
[See image.](#zd-azure-top-navigation-powershell-cr)
The **Cloud Shell** window appears.
-
In the **Cloud Shell** window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy container registry decoys and press `Enter`.
[See image.](#zd-azure-deployment-script-cr)
If you want to add multiple container registry decoys to Microsoft Azure, repeat Step 1 to Step 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the container registry decoy is added to Microsoft Azure. The container registry decoy is part of the Decoys Resource Group configured by Deception [during the integration](/deception/setting-cloud-deception-microsoft-azure). In addition, the **URI **to access the container registry is generated and associated with the decoy automatically. The deployment status is indicated by the icon next to the name of the decoy in the container registry decoys table (Deceive > Cloud Deception > Azure > Container Registry) within the Zscaler Deception Admin Portal. The **URI **value is also shown in the container registry decoys table. To learn how to configure lures using container registry decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![A screeshot capturing the Container Registry tab with Add Decoy icon highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-container-registry-decoy-azure/deception-add-button-ecr-decoy.png)
[]![A screenshot capturing the Container Registry Decoy window](/downloads/deception/deceive/cloud-deception/azure/creating-container-registry-decoy-azure/deception-ecr-decoy-window.png)
[]![A screenshot capturing the option to launch PowerShell in Azure](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-launch.png)
[]![A screenshot capturing the deployment script running in Azure PowerShell](/downloads/deception/deceive/cloud-deception/azure-decoys/zscaler-deception-azure-powershell-script-run-cr.png)