# Deploying Branch Connector & App Connector with Linux KVM
Source: https://help.zscaler.com/unified/deploying-branch-connector-app-connector-linux-kvm
PDF: https://help.zscaler.com/pdf/com/en/1517491.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Branch Connector & App Connector as a virtual machine (VM) on Linux KVM, and post-deployment configurations.
This procedure describes the steps for deploying Zscaler Branch Connector & App Connector on Linux KVM. To learn more about deploying Branch Connector & App Connector using a Terraform script, see[ Deployment Templates for Zscaler Branch Connector & App Connector](/unified/deployment-templates-branch-connector-app-connector).
[]Prerequisites
The role that admins are assigned dictates the level of access they have to the Admin Portal. Zscaler provides a default [admin ](/unified/about-administrators-0)account that provides full access to the portal and scope over the entire organization. Admins must have full access to Branch Connector Provisioning permissions. To learn more, see [About Role Management](/unified/about-role-management-1) and [Adding Admin Roles](/unified/adding-admin-roles-0).
[]Make sure the following prerequisites are met:
- Create a dedicated username for the Branch Connector & App Connector deployment in the Admin Portal.
- Create a dedicated password for the Branch Connector & App Connectordeployment in the Admin Portal. The password must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character. The password must not contain a `$`, `&`, `>`, `<`, `;`, `'`, or `"`. Otherwise, the deployment fails.
- Configure a [Branch Provisioning Template](/unified/configuring-branch-configuration-template) and copy the [Branch Provisioning URL](/unified/about-branch-configuration-templates).
- Download the combined Branch Connector & App Connector image from the [Branch Connector Images](/unified/downloading-branch-connector-images) page for Linux KVM.
- Branch Connector uses an API key to authenticate and register the VM with Zscaler. If you do not already have an API key, generate a new key. Then copy the API key from the API Keys page.
- Review the following Branch Connector & App Connector specifications and sizing requirements:
- Small VM: requires 4 GB of memory, 2 CPU cores, 128 GB data disk size, and 2 network interface cards (NIC)
- Medium VM: requires 8 GB of memory, 4 CPU cores, 128 GB data disk size, and 4 NICs
[]Creating and Applying User Data
You must create user data information for your Branch Connector & App Connector VM. This information can either be applied to the KVM VM with an ISO file that is mounted via a virtual CD-ROM drive or applied manually to the VM in the `/etc/cloud/cloud.cfg.d/` directory. For both methods, you must create a text file containing the user data.
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
- name: vtnet0
type: physical
subnets:
- address: <IP Address/Netmask> #IP configuration for the management interface
gateway: <Gateway>
type: static
- name: vtnet1
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
enable: yes
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
- name: vtnet0
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- name: vtnet1
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
enable: yes
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
- name: vtnet0
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- name: vtnet1
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
enable: yes
provisioning_key: asldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaksasldkfjalsdkjflaks
ssh_authorized_keys:
- ssh-rsa ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCh3ru9CCnEow69WlQyJuxvZJGHcjhcgJzp8XnoKTJk6o1bit+rq4BNyjS0orauMF6fNMHAyGZqDWw6RICvoeh386xNqnD7+AGE9VGz4cPv0CjoV2HvkKnA2Dj8KZFFJ/bBV0BndNdGATsbDnhq0wkJ+WXFmamb9kx4dSDL5ZD15SybFop0b/3JoqXoU+9pxFc0bQ/cediaifCztliI9i7NAmvIUinLy2OlDW/uPEcB8nBgXhAAc9ALe6+Q4wZt8JUdrcF04bgoAHYsNuzyEk4dNvov97JyExCAwzSLomiHFtdzhGw7/o6KhfhxxBRodKy4wQBwDzPbD6EbN9iCqoK8DY4HZ2L7HyQKRjhnnY/Y0uldO0tleogElbk+4LsoyAPjPAbogu89xSOa6D7sl2G+dPpqTlFBmO/3m/2JhBnGU= admin@branchpc
-
Apply your user data to the VM using one of the following methods:
- [ISO Method](#ISOMethod)
- [Manual Method](#ManualMethod)
[]
- Apply the user data to the VM as an ISO image:
-
On Centos, install the genisoimage:
`sudo yum install genisoimage`
-
On Ubuntu, install the genisoimage:
`sudo apt install genisoimage`
-
Configure the required user data.
The user data file must be named `user-data`.
`zuser@hostname:~$ mkdir isodir
zuser@hostname:~$ cat > isodir/user-data <<EOF #cloud-config
<TEXT FROM TEXT FILE>
EOF
user@hostname:~genisoimage -o user-data.iso -r isodir/user-data`
You attach the ISO to your Branch Connector VM in the [Deploy the Branch Connector](#Deployment) procedure.
[]You apply your user data at the end of the [Deploy the Branch Connector](#Deployment) procedure.
[]Deploying the Branch Connector & App Connector
After you have met all the [prerequisites](#Prereqs), created [user data](#UserData), and applied user data to the VM (if you used the [ISO method](#ISOMethod)), perform the following procedure to deploy your Branch Connector & App Connector on Linux KVM.
[Deployment Procedure](#procedure)
[]
- Log in to Virtual Machine Manager.
- Go to** File **> **New Virtual Machine**.
[See image.](#SeeImage1)
- In the **New VM **window, select** Import existing disk image**. Then, click **Forward**.
[See image.](#seeimage2)
- Click** Browse** to upload the Linux KVM image downloaded from the [Branch Connector Images](/unified/downloading-branch-connector-images) page.
[See image.](#seeimage3)
- For** Choose the operating system you are installing**, select **Free BSD 11.4**. Then, click **Forward**.
[See image.](#seeimage4)
- For **Choose Memory and CPU settings**, configure the memory and CPU settings based on the VM specifications. Then, click **Forward**.
[See image.](#seeimage5)
- Enter a** Name** for the Branch Connector, select a network under **Network selection**, and enable **Customize configuration before install**. Then, click **Finish**.
[See image.](#seeimage6)
- The Branch Connector configuration window appears displaying an overview of your Branch Connector and hypervisor details. Click **Add Hardware**.
[See image.](#seeimage8)
- If you applied user data to the VM using the ISO method: In the **Locate or create storage volume **window, select the **user-data.iso** file created in the [ISO Method](#ISOMethod) procedure. Then, click **Choose Volume**.
[See image.](#seeimage9)
- In the **Add New Virtual Hardware **window, select** Storage** from the left-side navigation, and ensure** Select or create custom storage **is selected.
- For **Device type**, select **CDROM device** from the drop-down menu, then click** Finish**.
[See image.](#seeimage10)
- Select** Network **from the left-side navigation to add another network:
a. For** Network source**, select a network from the drop-down menu.
b. Enable and enter the **MAC address**.
c. For **Device model**, select the device model.
[See image.](#seeimage11)
- Click **Finish**.
- In the Branch Connector configuration window, click **Begin Installation**.
- []If you applied user data to the VM using the* *[Manual Method](#ManualMethod):
-
In the VM console, create a new `userdata.cfg` file:
`zsroot@zscaler_node : ~ > sudo ee /etc/cloud/cloud.cfg.d/userdata.cfg`
- Paste in the contents of your [user data file](#userdatafile).
- Press `ESC` to exit the editor.
- Press `a` to leave the editor.
- Press `a` to save the file.
-
Reboot the VM:
`zsroot@zscaler_node : ~ > sudo reboot`
[]![New Virtual Machine selected in the Virtual Machine Manager](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/NewVirtualMachine.png)
[]![Import Existing Disk Image selected for installing the operating system.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/ImportExistingDiskImage.png)
[]![Browse in the Storage Path ](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Browse_StoragePath.png)
[]![Provide existing storage path and choose the operating system you are installing.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/StoragePath_OperatingSystem.png)
[]![The Memory and CPU settings](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Memory_CPU_Settings.png)
[]![Customize configuration before install and Network selection](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-linux-kvm-draft-doc-51457/NetworkSelection_CustomizeConfiguration4.png)
[]![Branch Connector overview with Add Hardware selected](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-app-connector-linux-kvm-draft-doc-51457/Addhardware_3.png)
[]![Locate or create storage volume window demonstrating user-data.iso file](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Locate_CreateStorageVolume.png)
[]![The Device Type demonstrating the CDROM device.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/DeviceType2.png)
[]![Network Source, MAC Address, and Device Model from Network tab. ](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/AddNewVirtualHardware_NetworkConfig.png)
[]
[]Managing the Branch Connector & App Connector
After your VM is fully deployed, you can manage the Branch Connector VM from the Admin Portal. A deployed VM is displayed in the dashboard. The [Cloud & Branch Connector Monitoring](/unified/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation, and status of your VMs deployed in your branch account.
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/unified/about-traffic-forwarding)
- [Log and Control Forwarding](/unified/about-log-and-control-forwarding)
- [DNS Filtering](/unified/about-dns-policies)