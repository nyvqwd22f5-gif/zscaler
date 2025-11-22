# Decoy Connector Deployment Guide for Nutanix AHV
Source: https://help.zscaler.com/deception/decoy-connector-deployment-guide-nutanix-ahv
PDF: https://help.zscaler.com/pdf/com/en/1531475.pdf

This deployment guide provides information on prerequisites, how to deploy a Decoy Connector on Nutanix AHV, how to configure the management network, and how to connect the Decoy Connector to the Zscaler Deception Admin Portal.
Prerequisites
Before deploying a Decoy Connector, Zscaler strongly recommends you read the following information and make the necessary changes to your organization's environment, where applicable.
- Ensure that you have a virtual machine (VM) with the following configurations:
- 2 CPU cores
- 4 GB RAM
- 50 GB disk storage. SSD-based storage is strongly recommended.
- Two or more network interfaces. You can use one interface as a dedicated management interface and the other interfaces to host decoys.
- Ensure that you have the following information to configure the Decoy Connector management interface:
- An IP address
- The subnet mask
- The default gateway
- The DNS server details
-
Ensure that you have outbound access to TCP port 443 from the Decoy Connector management interface to the following hosts:
- Deception Admin Portal
- Aggregator
- ib.smokescreen.io
- rs.smokescreen.io
If required, you can [configure proxy for a Decoy Connector](/deception/configuring-proxy-settings-decoy-connector) and pass the network connections through the proxy server. However, you must turn off all inspection features for the hosts in the preceding list and also ensure that the proxy provides unfiltered access to TCP port 443 for these destinations.
- Ensure that you have enabled VLAN trunking on the decoy interface if you want to use more than one VLAN on a single interface.
Deploying a Decoy Connector on Nutanix AHV
Follow these steps to deploy a Decoy Connector on Nutanix AHV:
- [Step 1: Download the VM Image File from the Deception Admin Portal](#download-image-file)
- [Step 2: Deploy a Decoy Connector on the Nutanix AHV Server](#deploy-decoy-connector-nutanix-ahv)
- [Step 3: Configure the Decoy Connector Management Network](#configure-management-network)
- [Step 4: Connect the Decoy Connector to the Deception Admin Portal](#connect-decoy-connector)
- []Go to **Settings** > **Topology** > **Decoy Connectors**.
-
Click **Download Image **and select **Xen/KVM **to download the compressed image file (.tar.gz).
[See image.](#download-decoy-connector-image)
- Use a file archiving and extraction tool to extract the .qcow2 image file from the compressed file.
[]To deploy a Decoy Connector on Nutanix AHV:
- [a. Create an image in Nutanix.](#create-image-nutanix)
- [b. Deploy a Decoy Connector VM in Nutanix.](#deploy-decoy-connector-vm-nutanix)
- []Log in to the Nutanix Web Console.
- Go to **Compute & Storage** > **Images**.
-
Click **Add Image**.
[See image.](#add-image-nutanix)
- In the** Add Images** wizard:
- Set **Image Source** to **Image File**.
- Click **Add File** and select the .qcow2 image file extracted in [Step 1](#download-image-file).
- Enter the **Name **and **Description **for the image.
-
Click **Next**.
[See image.](#select-image-nutanix)
- In the **Select Location **step, choose the **Place image directly on clusters** option as the **Placement Method, **and select the cluster on which the image must be placed.
-
Click **Save**.
[See image.](#placement-method-nutanix)
The image is listed on Nutanix.
Before proceeding to the subsequent steps, make sure that the uploaded image appears on the list along with a value in the **Size **column.
[See image.](#decony-connector-image-nutanix)
- []Log in to the Nutanix Web Console.
- Go to **Compute & Storage** > **VMs**.
-
Click **Create VM**.
[See image.](#create-vm-nutanix)
- In the **Create VM** wizard:
- In the **Configuration **step, enter the **Name **and **Description**.
- Choose a cluster from the **Cluster **drop-down menu.
-
Under **VM Properties**, set **CPU **count to **2**, and set **Memory **to **4 GiB.**
Make sure that the **Enable Memory Overcommit** option is not selected.
[See image.](#create-vm-configuration-nutanix)
- Click **Next**.
-
In the **Resources** step, click **Attach Disk**.
[See image.](#create-vm-resources-add-disk)
- In the **Type** drop-down menu, select **Disk**.
- In the **Operation** drop-down menu, select **Clone from Image**.
- In the **Image** drop-down menu, choose the image uploaded in the previous step.
-
Leave the **Capacity **option to its default value, and set the **Bus Type** to **SCSI**.
[See image.](#create-vm-add-disk-settings)
- Click **Save**.
-
To attach a management network interface, click **Attach to Subnet**.
[See image.](#create-vm-resources-add-subnet)
-
Select the management subnet of your choice, and set the **Network Connection State** to **Connected**.
[See image.](#create-vm-add-subnet-settings)
- Click **Save**.
-
To attach subnets where you want to deploy decoys, click **Attach to Subnet.**
[See image.](#create-vm-second-subnet)
-
Select the subnet where you want to add decoys, and set the **Network Connection State** to **Connected**.
[See image.](#add-subnet)
You can also attach multiple subnets. To do this, repeat steps 14 and 15 for each additional subnet where you want to add decoys.
-
Set the **Boot Configuration** to **Legacy BIOS Mode** with the default boot order priority.
[See image.](#create-vm-review-final)
- Click **Next**.
-
In the **Management **step, set **Timezone **to **UTC**,** **and make sure that the **Use this VM as an Agent VM** option is unselected.
[See image.](#create-vm-management)
- Click **Next**.
- In the **Review** step, review the settings you have configured.
-
Click **Create VM**.
[See image.](#create-vm-review)
-
On the **VMs **> **List **page, locate the newly added VM, and click the VM's name.
[See image.](#vm-list-nutanix)
-
On the VM's page, click the **More** option, and select **Power On**.
[See image.](#power-on-vm)
-
Go to the **Console **tab to interact with the VM's console for the subsequent configuration steps.
[See image.](#vm-console-nutanix)
[]After you deploy the Decoy Connector VM, you need to [configure the Decoy Connector management network](/deception/configuring-decoy-connector-management-network).
[]After the Decoy Connector management network is configured, you need to [add the Decoy Connector and connect it to the Deception Admin Portal](/deception/adding-connecting-decoy-connector-admin-portal).
[]![A screenshot capturing the option to download a decoy connector image](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-topology.png)
[]![A screenshot capturing images option to add an image in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-addimage.png)
[]![A screenshot capturing the option to select image in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-select-image.png)
[]![A screenshot capturing placement method configuration for an image in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-placement%20method.png)
[]![A screenshot capturing the Nutanix interface showing a list of images](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-image-list.png)
[]![A screenshot capturing the option to create a VM in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-createvm.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-configuration.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-resources-attachdisk.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-resources-attachdisk-popup.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-resources-attachtosubnet.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-resources-attachtosubnet-popup.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-addtosubnets.png)
[]![A screenshot capturing the subnet configuration for decoys in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-subnet-popup.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-final.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-management.png)
[]![A screenshot capturing the VM configuration settings in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-cvm-review.png)
[]![A screenshot capturing the newly added VM in the list view in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-select-vm.png)
[]![A screenshot capturing the option to power on the VM in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-power-on.png)
[]![A screenshot capturing the console of a VM in Nutanix](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-nutanix-ahv/zscaler-deception-nutanix-console.png)