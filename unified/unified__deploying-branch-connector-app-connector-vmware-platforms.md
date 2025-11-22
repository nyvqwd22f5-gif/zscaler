# Deploying Branch Connector & App Connector on VMware Platforms
Source: https://help.zscaler.com/unified/deploying-branch-connector-app-connector-vmware-platforms
PDF: https://help.zscaler.com/pdf/com/en/1517481.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Branch Connector & App Connector as a virtual machine (VM) on VMware platforms, and post-deployment configurations.
This procedure describes the steps for deploying Zscaler Branch Connector & App Connector on VMware platforms. To learn more about deploying Branch Connector & App Connector using a Terraform script, see [Deployment Templates for Zscaler Branch Connector & App Connector](/unified/deployment-templates-branch-connector-app-connector).
[]Prerequisites
Make sure the following prerequisites are met:
-
Grant admins full access to Branch Connector Provisioning permissions.
The role that you assign admins dictates the level of access they have to the Admin Portal. Zscaler provides a default [admin ](/unified/about-administrators-0)account that provides full access to the portal and scope over the entire organization. To learn more, see [About Role Management](/unified/about-role-management-1) and [Adding Admin Roles](/unified/adding-admin-roles-0).
- In the Admin Portal, create a dedicated username and password for the Branch Connector & App Connector deployment. The password must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character. The password must not contain a `$` , `&`, `>`, `<`, `;`, `'`, or `"`. If the password does not meet these requirements, the deployment fails.
- Configure a [Branch Provisioning Template](/unified/configuring-branch-configuration-template) and copy the [Branch Provisioning URL](/unified/about-branch-configuration-templates).
- Download the combined Branch Connector & App Connector OVA image file for VMware ESXi from the [Branch Connector Images ](/unified/downloading-branch-connector-images)page.
- Branch Connector & App Connector uses an API key to authenticate and register the VM with Zscaler. If you do not already have an API key, generate a new key. Then copy the API key from the [API Keys](/unified/about-api-configuration) page.
- The VM requires VMware vSphere Hypervisor (ESXi) version 7.0 or later, or the minimum version [stated by Broadcom](https://support.broadcom.com/).
- Configure an [App Connector Provisioning Key](/unified/about-app-connector-provisioning-keys) in the Admin Portal.
- [Review the Branch Connector specifications and sizing requirements.](#InstanceTypes)
- [Review the virtual machine specifications for Branch Connector deployed in high availability.](#HA)
[]
- Small VM: requires 16 GB of memory, 4 CPU cores, 128 GB data disk size, and three network interface cards (NICs)
- Medium VM: requires 32 GB of memory, 6 CPU cores, 128 GB data disk size, and 5 NICs
[]
- The **Promiscuous mode** option must be enabled (i.e., set to **Accept**) on the vSphere switch (vSwitch) or at the port group level. Branch Connector uses the Common Address Redundancy Protocol (CARP) to process traffic across multiple Branch Connector instances. To support this, you must enable promiscuous mode on your Branch Connector service interface.
- The **MAC address changes** option must be enabled on the vSwitch or port group.
- The **Forged transmits** option must be enabled on the vSwitch or port group.
- Branch Connectors often share the vSwitch with other corporate VMs, and settings you apply on the vSwitch level are applied to all VMs on the vSwitch. When promiscuous mode is enabled, other VMs might be able to detect traffic going through the service interface. To avoid this risk, Zscaler recommends that you create and use a port group for your Branch Connector service interfaces.
- If multiple physical ports exist on the same vSwitch, then the `Net.ReversePathFwdCheckPromisc` advanced option must be enabled (i.e., set to 1) on the ESXi host. If it is not enabled, then multicast traffic loops back to the host, causing CARP not to function properly, and `link states coalesced` messages are sent. To learn more, refer to the [VMware documentation](https://knowledge.broadcom.com/external/article?legacyId=59235).
[]Creating and Applying User Data
You must create user data information for your Branch Connector & App Connector VM. For VMware vCenter, user data information is provided during the OVA file import process. For VMware vSphere Hypervisor (ESXi), you must apply the user data information to the VM. You can apply this information to the VM either with an ISO file that you mount via a virtual CD-ROM drive or do so manually to the `/etc/cloud/cloud.cfg.d/` directory. For both methods, you must create a text file containing the user data.
-
[]Create your user data in a text file named `userdata.cfg` using the following template, formatted in YAML:
- [Branch Connector & App Connector with Static Management IP Template](#Static)
[]ZSCALER:
cc_url: <CC_URL>
http_probe_port: 50035 #Optional to change the port for load balancer status checks from the default value 50001 to 50035.
api_key: <API Key>
password: <Admin Password>
username: <Admin Username>
network:
config:
- name: vmx0 #For the VMXNet3 driver (required)
type: physical
subnets:
- address: <IP Address/Netmask> #IP configuration for the management interface
gateway: <Gateway>
type: static
- name: vmx1 #For the VMXNet3 driver (required)
type: physical
fib: '1'
subnets:
- address: <IP Address/Netmask> #IP configuration for the App Connector interface
gateway: <Gateway>
type: static
- type: nameserver
address:
- <IP Address>
- <IP Address>
search:
- zscaler.net
version: '1'
zscaler_app_connector:
enable: 'yes'
provisioning_key: <Key>
#ssh keys are optional
ssh_authorized_keys:
- ssh-rsa <Key>
[Example user data with default HTTP probe port and no SSH key](#StaticExample1)
[]ZSCALER:
cc_url: connector.zscaler.net/api/v1/provUrl?name=DemoBC
api_key: adfads2sd
password: demopass
username: bac-demoadmin@12345689.zscaler.net
network:
config:
- name: vmx0
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- name: vmx1
type: physical
fib: '1'
subnets:
- address: 10.66.118.72/24
gateway: 10.66.118.254
type: static
- type: nameserver
address:
- 10.66.98.1
- 8.8.8.8
search:
- zscaler.net
version: '1'
zscaler_app_connector:
enable: 'yes'
provisioning_key: asldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaks
[Example user data with non-default HTTP probe port and SSH key](#StaticExample2)
[]ZSCALER:
cc_url: connector.zscaler.net/api/v1/provUrl?name=DemoBC
http_probe_port: 50035
api_key: adfads2sd
password: demopass
username: bac-demoadmin@12345689.zscaler.net
network:
config:
- name: vmx0
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- name: vmx1
type: physical
fib: '1'
subnets:
- address: 10.66.118.72/24
gateway: 10.66.118.254
type: static
- type: nameserver
address:
- 10.66.98.1
- 8.8.8.8
search:
- zscaler.net
version: '1'
zscaler_app_connector:
enable: 'yes'
provisioning_key: asldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaks
ssh_authorized_keys:
- ssh-rsa ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCh3ru9CCnEow69WlQyJuxvZJGHcjhcgJzp8XnoKTJk6o1bit+rq4BNyjS0orauMF6fNMHAyGZqDWw6RICvoeh386xNqnD7+AGE9VGz4cPv0CjoV2HvkKnA2Dj8KZFFJ/bBV0BndNdGATsbDnhq0wkJ+WXFmamb9kx4dSDL5ZD15SybFop0b/3JoqXoU+9pxFc0bQ/cediaifCztliI9i7NAmvIUinLy2OlDW/uPEcB8nBgXhAAc9ALe6+Q4wZt8JUdrcF04bgoAHYsNuzyEk4dNvov97JyExCAwzSLomiHFtdzhGw7/o6KhfhxxBRodKy4wQBwDzPbD6EbN9iCqoK8DY4HZ2L7HyQKRjhnnY/Y0uldO0tleogElbk+4LsoyAPjPAbogu89xSOa6D7sl2G+dPpqTlFBmO/3m/2JhBnGU= admin@branchpc
-
Apply your user data to the VM in one of the following ways:
- [ISO Method](#ISOMethod)
- [Manual Method](#ManualMethod)
[]
- Apply the user data to the VM as an ISO image:
-
On Centos, install the genisoimage:
`sudo yum install genisoimage`
-
On Ubuntu, install the genisoimage :
`sudo apt install genisoimage`
-
Configure the required user data.
The user data file must be named `user-data`.
`zuser@hostname:~$ mkdir isodir
zuser@hostname:~$ cat > isodir/user-data <<EOF #cloud-config
<TEXT FROM TEXT FILE>
EOF
user@hostname:~genisoimage -o user-data.iso -r isodir/user-data`
You attach the ISO to your Branch Connector & App Connector VM in the [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere) procedure.
[]You apply your user data at the end of the [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere) procedure.
[]Deploying the Branch Connector & App Connector
Perform one of the following procedures to deploy your Branch Connector & App Connector:
- [Deploying on VMware vCenter](#vcenter)
- [Deploying on VMware vSphere Hypervisor (ESXi)](#vsphere)
[]After you have met all the [prerequisites](#Prereqs), perform the following steps to deploy your Branch Connector & App Connector with vCenter:
- Log in to the vCenter Server with the vSphere Client.
- Locate the VMware host on which you want to deploy the Branch Connector & App Connector, then right-click and select **Deploy OVF Template**.
[See image.](#SeeImage1)
- On the **Select an OVF template **page, select **Local file**. Then, upload the Branch Connector & App Connector OVA image file that you previously downloaded from the [Branch Connector Images](/unified/downloading-branch-connector-images) page. Then, click **Next**.
[See image.](#seeimage2)
- On the **Select a name and folder** page, enter a unique name and select a target location for the VM. Then, click **Next**.
[See image.](#seeimage3)
- On the **Select a compute resource** page, select the destination compute resource. Then, click **Next**.
[See image.](#seeimage4)
- On the **Review details** page, verify the template details. Then, click **Next**.
[See image.](#seeimage5)
- On the **Configuration** page, select a deployment configuration for the combined Branch Connector & App Connector image. Then, click **Next**.
[See image.](#seeimage6)
- On the** Select storage **page, select the storage for the configuration and disk files. Then, click **Next**.
[See image.](#seeimage8)
- On the **Select networks** page, select a destination network for each source network. Then, click **Next**.
[See image.](#seeimage9)
- On the **Customize template **page, configure the following deployment properties:
- **Branch Connector**
- **Provisioning Template URL**: Enter the [Branch Connector Provisioning URL](/unified/about-api-configuration).
- **API Key**: Enter the API Key from the [API Keys](/unified/about-api-configuration) page.
- **username**: Enter the username you created for the Branch Connector deployment role in the Admin Portal.
- **password**: Enter the password for the Branch Connector deployment role in the Admin Portal.
- **Management Interface IP Address**: Enter the IP address for the management interface.
- **Management Interface Subnet Mask**: Enter the subnet mask for the management interface.
- **Management Interface Default Gateway**: Enter the default gateway for the management interface.
- **Domain**: Enter the domain suffix.
- **DNS Information**: Enter the primary and secondary DNS servers that the Branch Connector should use for DNS resolution.
- **ssh login public key**: Enter the SSH public key for logging in without a password.
- **App Connector**
- **Provision Key**: Enter the App Connector Provisioning Key.
- **Control Interface IP Address**: Enter the IP address for the control interface.
- **Control Interface Subnet Mask**: Enter the subset mask for the control interface.
- **Control Interface Default Gateway**: Enter a default gateway for the control network.
- On the **Ready to complete **page, review all of your configurations. Then, click **Finish **to deploy.
To avoid any time sync issues, Zscaler recommends enabling the** Synchronize guest time with host** option after deploying Branch Connector & App Connector. To learn more, refer to the [VMware product documentation](https://kb.vmware.com/s/article/1014038).
[]![Deploy OVF Template from the vSphere Client](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Deploy_OVFTemplate_BCAppC1.png)
[]![Select an OVF template page demonstrating where to upload files.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/SelectanOVFTemplate_BCAPPC.png)
[]![Select a name and folder page of the Vsphere configuration.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/SelectNameFolder_VSphere_AppCBC.png)
[]![Select a compute resource.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/SelectComputeResource_BCAPPC.png)
[]![Review details tab of the OVF Template](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/ReviewDetails_Vsphere_AppCBC.png)
[]![Configuration page of the Deploy OVF Template](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/DeploymentConfiguration_BranchConnectorAppConnector.png)
[]![Select the storage for the configuration and disk files from the Select storage page.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/SelectStorage_Vsphere_AppCBC.png)
[]![Select Networks page in the Deploy OVF Template window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/SelectNetworks_Vsphere.png)
[]After you have met all the [prerequisites](#Prereqs), created [user data](#userdatafile), and applied user data to the VM (if using the [ISO method](#ISOMethod)), perform the following steps to deploy your Branch Connector & App Connector on vSphere Hypervisor (ESXi):
- Log in to the vSphere Hypervisor (ESXi) Server with the vSphere Client.
- Locate the VMware host on which you want to deploy the Branch Connector & App Connector and click **Create/Register VM**.
[See image.](#SeeImage10)
The** New virtual machine** window appears.
- On the **Select creation type **page, select **Deploy a virtual machine from an OVF or OVA file**. Then, click **Next**.
[See image.](#seeimage11)
- On the **Select OVF and VMDK files **page, enter a unique name for the VM and upload the Branch Connector & App Connector OVA image file that you previously downloaded from the [Branch Connector Images](/unified/downloading-branch-connector-images) page. Then, click **Next**.
[See image.](#seeimage12)
- On the **Select storage** page, select** Standard** as the storage type and select the datastore for the VM's configuration files. Then, click **Next**.
[See image.](#seeimage13)
- On the **Deployment options **page, select the** Network mappings**,** Deployment type**, and** Disk provisioning**. Ensure that the** Power on automatically **option is disabled. Then, click **Next**.
[See image.](#seeimage14)
- On the **Additional Settings** page, skip the additional properties for the VM because values entered on this page will not be configured. Click **Next**.
[See image.](#seeimage15)
- On the** Ready to complete** page, review all of your configurations. Then, click** Finish**.
[See image.](#seeimage16)
- After the VM has fully deployed, locate the VM and click** Edit**.
[See image.](#seeimage17)
The **Edit settings** window appears.
- If you applied user data to the VM using the [ISO Method](#ISOMethod):
-
In the **Edit settings **window, click **Virtual Hardware**. From the** CD/DVD Drive 1** drop-down menu, select **Datastore ISO file**.
[See image.](#seeimage18)
-
In the **Datastore browser **window that opens, click** Upload **to upload the `user-data.iso` file you created in the ISO Method procedure. Then, click** Select**.
[See image.](#seeimage19)
-
Ensure that **Connect** and **Connect at power on** are enabled. Then, click **Save**.
[See image.](#seeimage20)
-
Under **Virtual Machines**,** **locate the deployed Branch Connector and click **Power on**.
[See image.](#seeimage21)
- []If you are applying user data to the VM using the [Manual Method](#ManualMethod):
-
In the VM console, create a new `userdata.cfg` file:
`zsroot@zscaler_node : ~ > sudo ee /etc/cloud/cloud.cfg.d/userdata.cfg`
- Paste in the contents of your user data file.
- Press `Esc `to exit the editor.
- Press `a` to leave the editor.
- Press `a` to save the file.
-
Reboot the VM:
`zsroot@zscaler_node : ~ > sudo reboot`
To avoid any time sync issues, Zscaler recommends enabling the** Synchronize guest time with host** option after deploying Branch Connector & App Connector. To learn more, refer to the [VMware product documentation](https://kb.vmware.com/s/article/1014038).
[]![The VMware ESXi host demonstrating Create/Register VM selection](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Create-RegisterVM-ESXi.png)
[]![Select creation type page in the New virtual machine window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/selectcreationtype-ESXi.png)
[]![Select OVF and VMDK files page in New virtual machine window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Select-OVF-VMDK-Files-BC-AppC.png)
[]![Select storage page of the New virtual machine window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Select-Storage-ESXi.png)
[]![Deployment options page in the New virtual machine window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/DeploymentOptions-ESXi-BC-AppC.png)
[]![Skip the Additional Settings page in the New virtual machine window](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/AdditionalSettings-ESXi.png)
[]![Review your settings on the Ready to complete page in the New virtual machine window.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Readytocomplete-esxi-bc-appc.png)
[]![Edit selected on a deployed Virtual Machine in VMware ESXi.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/DeployedVM-Edit-ESXi2.png)
[]![Datastore ISO file selection from the CD/DVD Drive 1 drop-down menu](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/EditSettings-DataStore-ESXi.png)
[]![Datastore browser upload for the userdata.iso file](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Datastore-browser-esxi.png)
[]![Edit settings window with CD/DVD Drive 1 configurations](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/EditSettings-Connect-ConnectPowerOn_0.png)
[]![Power on the virtual machine.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-vmware-platforms-draft-doc-51457/Power-On-ESXi.png)
[]Managing the Branch Connector & App Connector
After your VM is fully deployed, you can manage the Branch Connector & App Connector VM from the Admin Portal. A deployed VM is displayed in the dashboard. The [Cloud & Branch Connector Monitoring](/unified/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation, and status of your VMs deployed in your branch account.
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/unified/about-traffic-forwarding)
- [Log and Control Forwarding](/unified/about-log-and-control-forwarding)
- [DNS Filtering](/unified/about-dns-policies)