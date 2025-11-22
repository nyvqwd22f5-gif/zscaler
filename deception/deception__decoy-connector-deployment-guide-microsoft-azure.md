# Decoy Connector Deployment Guide for Microsoft Azure
Source: https://help.zscaler.com/deception/decoy-connector-deployment-guide-microsoft-azure
PDF: https://help.zscaler.com/pdf/com/en/1531274.pdf

This deployment guide provides information on prerequisites, how to deploy a Decoy Connector on Microsoft Azure, how to configure the Decoy Connector network interface, and how to connect the Decoy Connectorr to the Zscaler Deception Admin Portal.
Prerequisites
Before deploying a Decoy Connector, Zscaler strongly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
-
Ensure that you have outbound access to TCP port 443 from the Decoy Connector management IP address to the following hosts:
- Deception Admin Portal
- Aggregator
- ib.smokescreen.io
- rs.smokescreen.io
If required, you can [configure proxy for a Decoy Connector](/deception/configuring-proxy-settings-decoy-connector) and pass the network connections through the proxy server. However, you must turn off all inspection features for the hosts in the preceding list and also ensure that the proxy provides unfiltered access to TCP port 443 for these destinations.
- Ensure that you have:
- An Azure account with admin privileges to do the following:
- Upload an image to the Azure Blob storage.
- Create an image from the Decoy Connector image (.vhd file) in the block storage.
- Create a new virtual machine (VM) from the Decoy Connector image.
- 50 GB disk storage. An SSD-backed storage is recommended.
Deploying a Decoy Connector on Azure
Follow these steps to deploy a Decoy Connector on Azure:
- [Step 1: Download the VM Image File From the Deception Admin Portal](#download-image-admin-portal)
- [Step 2: Deploy the Decoy Connector on Azure](#deploy-decoy-connector-azure)
- [Step 3: Add and Connect the Decoy Connector to the Deception Admin Portal](#connect-decoy-connector)
- []Go to **Settings** > **Topology** > **Decoy Connector**.
-
Click **Download Image** and select **HyperV** to download the image (.vhd.zip) file.
[See image.](#download-hyperv-image-file)
- Extract the file to your system. You need to access the virtual hard disk (.vhd) file to complete the deployment.
[]To deploy a Decoy Connector on Azure:
- [a. Create a Decoy Connector VM on Azure.](#create-decoy-connector-vm-azure)
- [b. Add a network interface to the Decoy Connector VM on Azure.](#additional-network-interface)
- []Log in to the [Azure portal](http://portal.azure.com/) using your credentials.
-
Go to **Azure services** > **Storage accounts**.
[See image.](#navigate-to-storage-accounts)
-
Select a storage account.
[See image.](#select-storage-account)
-
In the left-side navigation, go to **Data storage** > **Containers**.
[See image.](#navigate-to-container)
-
Select a container, and then click **Upload**.
[See image.](#upload-container)
-
In the **Upload blob** window, click the **Select a file** icon to find and select the image (.vhd ) file that you downloaded in [Step 1](#download-image-admin-portal), and then click **Upload**.
[See image.](#upload-container-image)
-
Go to **Azure services** > **Images**.
[See image.](#navigate-to-images)
-
Click **Create**.
[See image.](#create-image)
- On the **Basics** tab:
- Under **Project details **section, choose a **Resource group**.
- Under **Instance details **section:
- Enter a **Name** for the image.
- Select a **Region** from the drop-down menu.
- Under **OS disk **section:
- For **OS type**, select **Linux**.
- For **VM generation**, select **Gen 1**.
- For **Storage blob**, click **Browse** and select the image (.vhd) file that you uploaded.
- For **Account type**, select **Standard SSD** from the drop-down menu, and then configure the rest of the general information for the VM.
-
Click **Review + create**.
[See image.](#configure-image-basic-settings)
-
On the **Review + create** tab, review the image configuration, and then click **Create**.
[See image.](#review-create-image)
-
Make sure that the image is deployed successfully.
[See image.](#image-deployed)
-
Go to **Azure services** > **Virtual machines**.
[See image.](#navigate-vm)
-
Click the **Create** drop-down menu, and then click **Azure virtual machine**.
[See image.](#create-vm-azure)
-
On the **Basics** tab:
- Under the **Project details** section, choose a **Resource group **from the drop-down menu.
- Under the **Instance details **section, enter the **Virtual machine name**.
- Select a **Region**. Ensure that you select the same region that you specified while configuring the image.
- For** Image**, select the image that you deployed.
- For **Size**, select **Standard_B2s – 2vcpus**, **4 GiB memory **from the drop-down menu, and then configure the rest of the general information for the VM.
[See image.](#configure-vm-basic-settings)
The Zscaler Deception Decoy Connector VM does not use the administrator's credentials configured at the time of the VM creation.
- On the **Networking** tab, under the **Network interface **section, select **SSH (22) **for the **Select inbound ports** drop-down menu.
-
Click **Review + create**.
[See image.](#configure-vm-network-settings)
-
On the **Review + create** tab, review the VM configuration, and then click **Create**.
[See image.](#review-vm-summary)
After connection of the Decoy Connector to the Deception Admin Portal is completed, the **Public inbound ports** option under the **Networking** tab can be set to **None.**
[See image.](#public-inbound-ports-none)
-
Make sure that the VM is deployed successfully.
[See image.](#vm-deployed)
To add decoys, each Decoy Connector VM needs to have at least two network interfaces. Therefore, you must add another network interface.
- []Log in to the [Azure portal](http://portal.azure.com/) using your credentials.
-
Go to **Azure services** > **Virtual machines.**
[See image.](#navigate-storage-acc-network)
- Select the VM for which you want to configure an additional network interface. Make sure the VM is not running.
-
For the VM, in the left-side navigation, go to **Settings** > **Networking**.
[See image.](#vm-settings-network)
-
On the **Networking **page, click **Attach network interface**.
[See image.](#attach-network-interface)
-
On the **Attach network interface** page, click **Create and attach network interface**, and then click **OK**.
[See image.](#create-attach-network-interface)
-
In the **Create network interface** window, under **Network interface **section:
- Enter a **Name** for the network interface.
- Select a **Subnet** where you want to configure the decoys.
- Select a security group that allows inbound access to the IP address.
- Select either the **Dynamic** or **Static IP** address option per your requirement.
- Click **Create**.
[See image.](#network-interface-settings)
- Make sure the network interface is created on the **Attach network interface** page, select the network interface, and then click **OK**.
-
Start the VM.
[See image.](#start-vm)
- For a VM, each network interface can be in a different subnet. However, all of the network interfaces must be a part of the same virtual network.
- The number of network interfaces that you can add to a VM depends on its image size. The recommended image size is Standard_B2s, which allows you to add three network interfaces to a VM.
- You can deploy only one network decoy on each interface.
[]You need to [add the Decoy Connector and connect it to the Deception Admin Portal.](/deception/adding-connecting-decoy-connector-admin-portal)
[]![Download Hyper-V image file](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-decoy-connectors-page.jpg)
[]![Navigate to Storage accounts in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-navigate-to-storage-account.png?1648038011)
[]![Select a Storage account](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-select-storage-accounts.png?1648036800)
![Upload a container](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-container-upload.png)
[]
[]![Navigate to container](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-navigate-to-container.png?1648036469)
[]![Upload the image in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-upload-image-azure.png)
[]![Navigate to Images in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-select-storage-images.png)
[]![Create an image](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-create-image.png)
[]![Configure Image basic settings](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-image-basic-pane.png)
[]![Review and create an Image on Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-image-review-create.png)
[]![Image deployed on Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-image-complete.png)
[]![Navigate to Virtual machines in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-navigate-vm.png)
[]![Create VM in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-create-vm.png)
[]![Configure VM basic settings in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-vm-basic.png)
[]![Configure VM network settings in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-vm-network.png)
[]![Review VM summary in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-vm-review.png?1648101312)
[]![zscaler-deception-public-inbound-ports.png](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-public-inbound-ports.png)
[]![VM deployed in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-create-vm-deployed.png)
[]![Navigate to Virtual machines in Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-deception-navigate-vm.png)
[]![VM network interface settings](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-decption-interface-settings-networking.png)
[]![Attach network interface](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-decption-interface-attach-network.png)
[]![Create and attach network interface](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-decption-interface-create-attach.png?1648108474)
[]![Network interface settings ](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-decption-interface-network-settings_0.png)
![Start a VM on Azure](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-azure/zscaler-decption-interface-start.png)
[]