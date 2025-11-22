# Decoy Connector Deployment Guide for VMware Platforms
Source: https://help.zscaler.com/deception/decoy-connector-deployment-guide-vmware
PDF: https://help.zscaler.com/pdf/com/en/1531258.pdf

This deployment guide provides information on prerequisites, how to deploy a Decoy Connector on a VMware platform with vSphere Hypervisor (ESXi) client, how to configure the management network, and how to connect the Decoy Connector to the Zscaler Deception Admin Portal.
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
- Ensure that you have enabled the following options in a port or port group for a distributed virtual switch or standard switch:
- Promiscuous mode
- Forged transmits
- MAC address changes
-
VLAN Trunking
The VLAN Trunking setting is enabled only if you are deploying decoys on more than one VLAN.
Deploying a Decoy Connector on VMware Platform
Follow these steps to deploy a Decoy Connector on VMware platform:
- [Step 1: Download the VM Image File from the Deception Admin Portal](#download-image-admin-portal)
- [Step 2: Deploy a Decoy Connector on the VMware vSphere Hypervisor (ESXi)](#deploy-decoy-connector-vsphere-esxi)
- [Step 3: Configure the Decoy Connector Management Network](#configure-management-network)
- [Step 4: Connect the Decoy Connector to the Deception Admin Portal](#connect-decoy-connector)
- []Go to **Settings** > **Topology** > **Decoy Connectors**.
-
Click **Download Image** and select **VMware** to download the image (.ova) file.
[See image](#download-image-file)
[]To deploy a Decoy Connector on vSphere Hypervisor (ESXi):
- [a. Add a standard port group or a distributed port group.](#add-port-group)
- [b. Deploy a Decoy Connector.](#deploy-decoy-connector-vmware)
[]
- To add a standard port group, [create a new vSphere standard switch](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-DAF824CD-104D-4ED7-8BA3-D769DF688CEB.html) or use an existing standard switch.
- Log in to the vSphere Hypervisor (ESXi) with the vSphere client.
- Go to **Networking** > **Port groups** > **Add port group**.
- In the **Add port group** window:
- Enter a **Name**.
- Enter a **VLAN ID**. If VLAN trunking is required, then enter `4095`.
- Select a standard switch from the **Virtual switch** drop-down menu.
- Under **Security**, select **Accept** for the following options:
- Promiscuous mode
- MAC address changes
- Forged transmits
-
Click **Add**.
[See image.](#standard-port-group)
- To add a distributed port group, [create a new vSphere distributed switch](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-D21B3241-0AC9-437C-80B1-0C8043CC1D7D.html), or use an existing distributed switch.
- Log in to the vSphere Hypervisor(ESXi) with the vSphere client.
- Go to **Menu** > **Networking** and select the distributed switch.
- Right-click the distributed switch and select** New Distributed Port Group** from the drop-down menu.
- In the **New Distributed Port Group** window:
-
Enter a name for the port group, and then click **Next**.
[See image.](#distributed-switch-port-name)
- Configure the required distributed port group settings:
- For **VLAN**, select **None**. If VLAN trunking is required, then select **Trunk**.
-
For **Advanced**, select **Customize default policies configuration**, and** **then click **Next**.
[See image.](#configure-distributed-switch-settings)
-
Select **Accept** for the following security options, and then click **Next**:
- Promiscuous mode
- MAC address changes
- Forged transmits
[See image.](#security-settings-dswitch-port-group)
-
Review the distributed port group settings, and click **Finish**.
[See image.](#create-distributed-port-group)
- []Log in to the vSphere Hypervisor (ESXi) with the vSphere client.
-
Go to **Virtual Machines** > **Create/Register VM.**
[See image.](#create-vm-vmware)
The **New virtual machine **wizard appears.
-
On the **Select creation type** page, select **Deploy a virtual machine from an OVF or OVA file**, and then click **Next**.
[See image.](#deploy-vm-ova)
- On the **Select OVF and VMDK files** page, enter a name for the VM.
- Select the image file (.ova) that you downloaded in [Step 1](#download-image-admin-portal).
-
Click **Next**.
[See image.](#select-ova-file)
- On the **Select storage** page, select a datastore to save the configuration and disk files. An SSD-backed datastore is recommended.
-
Click **Next**.
[See image.](#select-storage)
- On the **Deployment options** page, configure the following options:
- In **Network mappings**:
- For the management interface, select the port group which corresponds to the management IP of the VM.
- For the decoy interface, select the port group with **Promiscious mode**, **MAC address changes**, and **Forged transmits options** enabled.
- In **Disk provisioning**, select **Thick**.
-
Click **Next**.
[See image.](#deployment-options)
-
On the **Ready to complete** page, review the settings, and then click **Finish** to deploy the Decoy Connector VM.
[See image.](#vm-summary)
[]After you deploy the Decoy Connector VM, you need to [configure the Decoy Connector management network.](/deception/configuring-decoy-connector-management-network)
[]After the Decoy Connector management network is configured, you need to [add the Decoy Connector and connect it to the Deception Admin Portal.](/deception/adding-connecting-decoy-connector-admin-portal)
[]![Download VMware image file](/downloads/deception/product-documentation/settings/topology/decoy-connector/decoy-connector-deployment-guides-supported-platforms/decoy-connector-deployment-guide-vmware/zscaler-deception-decoy-connectors-page-vmware.jpg)
[]![Add a standard port group](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-appliance-add-standard-port-group.png)
[]![Configure name and location of the distributed port group on VMWare](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-dswitch-name.png?1649142965)
[]![Configure a distributed port group settings](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-dswitch-settings.png?1649143460)
[]![Configure security settings for a distributed port group](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-dswitch-security.png)
[]![Review and create distributed port group](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-dswitch-finish.png?1649145580)
[]![Create VM in VMware hypervisor](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-create-vm.png?1646125373)
[]![Deploy VM from ova](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-deploy-vm-from-ova.png)
[]![Select .ova image file](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-select-ova.png)
[]![Select storage](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-select-datastore.png)
[]![Select deployment options](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-deployment-options.png)
[]![VM summary](/downloads/deception/product-documentation/settings/topology/appliances/how-import-appliance-vmware/zscaler-deception-vmware-vm-summary.png)