# Decoy Connector Deployment Guide for Microsoft Hyper-V
Source: https://help.zscaler.com/deception/decoy-connector-deployment-guide-microsoft-hyper-v
PDF: https://help.zscaler.com/pdf/com/en/1531273.pdf

This deployment guide provides information on prerequisites, how to deploy a Decoy Connector on Microsoft Hyper-V (Windows Server 2012 R2 or later), how to configure the Connector management network, and how to connect the Decoy Connector to the Zscaler Deception Admin Portal.
Prerequisites
Before deploying a Decoy Connector, Zscaler strongly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- Ensure that you have a virtual machine (VM) with the following configurations:
- 2 CPU cores
- 4 GB RAM
- 50 GB disk storage. An SSD-backed storage is recommended.
- Two or more network interfaces. You can use one interface as a dedicated management interface and the other interfaces to host decoys.
- Ensure that you have the following details to configure the Decoy Connector management interface:
- An IP address
- The subnet mask
- The default gateway
- The DNS server details
-
Ensure that you have outbound access to TCP port 443 from the Decoy Connector management IP address to the following hosts:
- Deception Admin Portal
- Aggregator
- ib.smokescreen.io
- rs.smokescreen.io
If required, you can [configure proxy for a Decoy Connector](/deception/configuring-proxy-settings-decoy-connector) and pass the network connections through the proxy server. However, you must turn off all inspection features for the hosts in the preceding list and also ensure that the proxy provides unfiltered access to TCP port 443 for these destinations.
- Enable the **MAC address spoofing** option on the network adapter.
Deploying a Decoy Connector on Microsoft Hyper-V
Follow these steps to deploy a Decoy Connector on Microsoft Hyper-V:
The Decoy Connectors do not support VLAN trunking in the Hyper-V platform. If you need to configure two or more VLANs, a virtual NIC for each VLAN must be configured.
- [Step 1: Download the VM Image File from the Deception Admin Portal](#download-image-file)
- [Step 2: Deploy a Decoy Connector on Hyper-V](#deploy-decoy-connector-hyperv)
- [Step 3: Configure the Decoy Connector Management Network](#configure-management-network)
- [Step 4: Add and Connect the Decoy Connector to the Deception Admin Portal](#connect-decoy-connector)
- []Go to **Settings** > **Topology** > **Decoy Connectors**.
-
Click **Download Image**, and then select **HyperV** to download the image (.vhd.zip) file.
[See image.](#download-hyperv-image-file)
- Extract the file to your system. You need to access the virtual hard disk (.vhd) file to complete the deployment.
[]To deploy a Decoy Connector on Hyper-V:
- [a. Create a Decoy Connector VM on Hyper-V.](#create-decoy-connector-vm-hyperv)
- [b. Add a network interface to the Decoy Connector VM on Hyper-V.](#add-decoy-connector-network-interface)
- []Open the Hyper-V Manager.
-
Go to **Actions** > **New** > **Virtual Machine…**.
[See image.](#create-vm-hyperv)
The **New Virtual Machine Wizard** appears.
- On the **Before You Begin** page, click **Next**.
-
On the **Specify Name and Location** page:
- Enter a name for the VM.
- Click **Browse...** to choose a location where you want to save the VM configuration files, and then click **Next**.
[See image.](#vm-name-location-hyperv)
-
On the **Specify Generation** page, select **Generation 1**, and then click **Next**.
[See image.](#vm-generation-hyperv)
-
On the **Assign Memory** page, enter the **Startup memory **amount that you want to allocate to the VM. For example, enter `4096` to allocate 4 GB of RAM, and then click **Next**.
[See image.](#assign-vm-memory-hyperv)
-
On the **Configure Networking** page, select a virtual switch from the **Connection **drop-down menu, and then click **Next**.
[See image.](#virtual-switch-hyperv)
-
On the **Connect Virtual Hard Disk** page, select **Use an existing virtual hard disk** and click **Browse...** to find the .vhd file you extracted in [Step 1](#download-image-file), and then click **Next**.
[See image.](#virtual-hard-disk-hyperv)
-
On the **Summary** page, review the VM description, and then click **Finish**.
[See image.](#review-vm-summary)
To add decoys, you need to add a network interface to the Decoy Connector VM on Hyper-V.
- []Open the Hyper-V Manager.
- Select the VM to which you want to add the network interface.
-
Right-click on the VM that you created, and then click **Settings...**.
[See image.](#config-network-settings)
The Settings page for the Decoy Connector VM opens.
- In the left-side navigation, go to **Hardware** > **Add Hardware**.
- In the **Add Hardware** pane, select **Network Adapter**.
-
Click **Add**.
[See image.](#add-network-adapter)
- In the left-side navigation, go to **Hardware** > **Network Adapter** > **Virtual Switch**.
-
In the **Network Adapter** pane, select a virtual switch that you want to assign to the decoy network.
[See image.](#add-virtual-switch)
- In the left-side navigation, go to **Network Adapter** > **Advanced Features**.
- In the **Advanced Features** pane, under **MAC address**, select the **Enable Mac address spoofing **checkbox.
-
Click **Apply**, and then click **OK**.
[See image.](#enable-mac-address-spoofing)
- Select the Decoy Connector VM, then from the **Action** menu, select **Start**.
[]After you deploy the Decoy Connector on Hyper-V, you need to [configure the Decoy Connector management network.](/deception/configuring-decoy-connector-management-network)
[]After the Decoy Connector management network interface is configured, you need to [add the Decoy Connector and connect it to the Zscaler Deception Admin Portal.](/deception/adding-connecting-decoy-connector-admin-portal)
[]![Download Hyper-V image file](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-decoy-connectors-page.jpg)
[]![Create VM in Hyper-V](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-hyperv-create-vm.png?1647860786)
[]![Select VM name and location ](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-hyperv-vm-name-location.png)
[]![Specify VM generation](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-vm-generation.png?1647861648)
[]![Assign VM memory](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-vm-assign-memory.png)
[]![Select virtual switch](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-vm-config-virtual-switch.png)
[]![Connect virtual hard disk](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-vm-connect-virtual-hard-disk.png)
[]![Review VM summary](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-vm-summary.png)
[]![Configure network settings](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-config-nw-settings.png)
[]![Add a network adapter](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-config-add-hardware.png)
[]![Add virtual switch](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-config-add-virtual-switch.png)
[]![Enable MAC address spoofing](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-microsoft-hyper-v/zscaler-deception-enable-mac-add-proof.png)