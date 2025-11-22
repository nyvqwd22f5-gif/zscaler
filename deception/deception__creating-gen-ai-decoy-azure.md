# Creating a Gen AI Decoy in Azure
Source: https://help.zscaler.com/deception/creating-gen-ai-decoy-azure
PDF: https://help.zscaler.com/pdf/com/en/1531618.pdf

Microsoft Azure allows you to build generative AI (Gen AI) applications using various foundation models through Azure AI Foundry. You can create a Gen AI decoy using Azure OpenAI models in Azure AI Foundry. The Gen AI decoys are interactive, and you can customize the decoys to generate fake responses to lure attackers into entering more prompts.
Prerequisites
Before configuring a Gen AI decoy in Azure, you must ensure that you have:
- Configured the [integration between Azure and Zscaler Deception](/deception/setting-cloud-deception-microsoft-azure).
- Obtained the necessary PowerShell command to run the deployment script using one of the following methods:
- [Automated Download Method](/deception/obtaining-deployment-script-azure#zd-direct-download-script)
- [Manual Download Method](/deception/obtaining-deployment-script-azure#zd-manual-download-script)
Creating a Gen AI Decoy
To create a Gen AI decoy:
- In the Zscaler Deception Admin Portal, go to **Deceive **> **Cloud Deception **> **Azure **> **GenAI**.
-
Click **Add Decoy**.
[See image.](#add-gen-ai-decoy)
The **GenAI Decoy **window appears.
-
In the **GenAI Decoy **window:
- **Name**: Enter a name for the Gen AI decoy application.
- **Tenant ID**: Select the tenant ID of the Azure account where you want to deploy the decoy.
- **Subscription ID**: Select the subscription ID of the Azure account where you want to deploy the decoy.
- **Resource Group**: If this is your first decoy in the account (Tenant ID and Subscription ID combination) or if you want to create a new resource group, enter a name for the resource group that must hold the decoy. If there is an existing resource group for the account (Tenant ID and Subscription ID combination), select the resource group from the drop-down menu.
-
**Region**: Select the region where the decoy must be deployed.
If you are creating a new resource group while adding the decoy, the resource group is created in the region selected for the decoy. However, when you select an existing resource group, the deployment region of the decoy and the resource group can be different.
-
**Model**: Select the foundation model that must be used for creating the decoy.
Ensure that the OpenAI model you want to deploy is available in the selected [Azure region](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/models?tabs=global-standard%2Cstandard-chat-completions#models-by-deployment-type).
- **Instructions**: Enter instructions for the Gen AI decoy to customize how it responds to prompts. The instructions are given as Gen AI prompts.
- **Description**: Enter a description for the decoy.
[See image.](#gen-ai-decoy-window)
- Click **Save**.
- Sign in to the [Azure Portal](https://https//portal.azure.com) as a Cloud Device Administrator or Global Administrator.
-
Launch Cloud Shell by clicking the **Cloud Shell **icon on the top navigation bar.
[See image.](#cloud-shell-icon)
The **Cloud Shell **window appears.
-
In the **Cloud Shell **window:
- Set your shell environment to PowerShell.
- Run the deployment script using the command obtained via the [automated download method](/deception/obtaining-deployment-script-azure#zd-direct-download-script) or [manual download method](/deception/obtaining-deployment-script-azure#zd-manual-download-script).
- Enter the option to deploy Gen AI decoys and press `Enter`.
[See image.](#options-in-script)
If you want to add multiple Gen AI decoys to Microsoft Azure, repeat steps 1 through 4 for each decoy and then run the script to sync all decoys simultaneously.
Upon successful execution of the script, the Gen AI decoy is added to Azure. The deployment status is indicated by the icon next to the name of the decoy in the Gen AI decoys table (Deceive > Cloud Deception > Azure > GenAI) within the Deception Admin Portal.
Azure obfuscates the last octet of IP addresses of the users that interact with Gen AI decoys. Zscaler recommends avoiding containment of these IP addresses from the [Investigate page](/deception/taking-action-from-the-dashboard#third-party-containment) or through [Orchestration rules](https://help.zscaler.com/deception/v4_29/creating-orchestration-rule#response-automation).
To learn how to configure lures using Gen AI decoys, see [Configuring Lures Using Azure Decoys](/deception/configuring-lures-using-azure-decoys).
[]![Image]()
![Adding a generative AI decoy in Azure](/downloads/deception/deceive/cloud-deception/azure/creating-generative-ai-decoy-azure/zscaler-deception-add-deceoy-genai-ai-azure.png)
[]![Configuring a generative AI decoy in Azure](/downloads/deception/deceive/cloud-deception/azure/creating-generative-ai-decoy-azure/deception-azure-gen-ai-decoy-details.png)
[]![Option to launch Azure Cloud Shell](/downloads/deception/deceive/cloud-deception/azure/creating-generative-ai-decoy-azure/zscaler-deception-azure-powershell-launch%20(4).png)
[]![Deployment script options with the option to deploy geenrative AI decoys highlighted](/downloads/deception/deceive/cloud-deception/azure/creating-generative-ai-decoy-azure/deception-power-shell-azure-gen-ai-decoy.png)