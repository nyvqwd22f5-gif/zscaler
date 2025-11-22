# Deploying Branch Connector with Linux KVM
Source: https://help.zscaler.com/cloud-branch-connector/deploying-branch-connector-linux-kvm
PDF: https://help.zscaler.com/pdf/com/en/1420926.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Branch Connector as a virtual machine (VM) on Linux KVM, and post-deployment configurations.
This procedure describes the steps for deploying Zscaler Branch Connector on Linux KVM. To learn more about deploying Branch Connector using a Terraform script, see[ Deployment Templates for Zscaler Branch Connector & App Connector](/cloud-branch-connector/deployment-templates-zscaler-branch-connector).
[]Prerequisites
The role that you assign admins dictates the level of access they have to the Zscaler Cloud & Branch Connector Admin Portal. Zscaler provides a default [admin ](/cloud-branch-connector/about-administrator)account that provides full access to the portal and scope over the entire organization. Admins must have full access to Branch Connector Provisioning permissions. To learn more, see [About Role Management](/cloud-branch-connector/about-role-management) and [Adding Admin Roles](/cloud-branch-connector/adding-cloud-connector-roles).
Make sure the following prerequisites are met:
- Create a dedicated username for the Branch Connector deployment in the Cloud & Branch Connector Admin Portal.
- Create a dedicated password for the Branch Connector deployment in the Cloud & Branch Connector Admin Portal. The password must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character. The password must not contain a `$`, `&`, `>`, `<`, `;`, `'`, or `"`. If the password does not meet these requirements, the deployment fails.
- Configure a [Branch Provisioning Template](/cloud-branch-connector/configuring-branch-provisioning-template) and copy the [Branch Provisioning URL](/cloud-branch-connector/about-branch-provisioning-template).
- Download the Branch Connector image from the [Branch Connector Images](/cloud-branch-connector/about-branch-connector-images) page for Linux KVM.
- Branch Connector uses an API key to authenticate and register the VM with Zscaler. If you do not already have an API key, generate a new key. Then copy the API key from the [API Key Management](/cloud-branch-connector/about-api-key-management) page.
- Review the following Branch Connector specifications and sizing requirements:
- Small VM: requires 4 GB of memory, two CPU cores, 128 GB data disk size, and 2 network interface cards (NIC)
- Medium VM: requires 8 GB of memory, 4 CPU cores, 128 GB data disk size, and 4 NICs
[]Creating and Applying User Data
You must create a text file containing user data information for your Branch Connector VM. This information is applied to the KVM VM with an International Organization for Standardization (ISO) file that is mounted via a virtual CD-ROM drive.
[List of network drivers to specify in the user data information](#drivers)
-
[]Create your user data in a text file named `userdata.cfg` using one of the following templates, formatted in YAML:
- [Branch Connector with Management DHCP Template](#DHCP)
- [Branch Connector with Static Management IP Template](#Static)
[]The following lists Ethernet devices and the drivers that support them. In the template, replace <Driver> with the value associated with the device you will select during deployment. (The values used in the examples are for illustration only, and are not necessarily typical for the hypervisor type.)
- **Windows VirtIO**: `vtnet`
- **Intel e1000**: `em`
- **Intel Gigabit**: `igb`
- **Intel 10 Gigabit**: `ix`
- **VMware Vxnet3**: `vmx`
- **Hyper-V**: `hn`
[]ZSCALER:
cc_url: <CC_URL>
http_probe_port: 50035 #Optional to change the port for load balancer status checks from the default value 50001 to 50035.
api_key: <API Key>
password: <Admin Password>
username: <Admin Username>
network:
config:
- name: <Driver>
type: physical
subnets:
- type: dhcp
version: '1'
#ssh keys are optional
ssh_authorized_keys:
- ssh-rsa <Key>
[Example user data with default HTTP probe port and no SSH key](#DHCPExample1)
[]ZSCALER:
cc_url: connector.zscaler.net/api/v1/provUrl?name=DemoBC
api_key: adfads2sd
password: demopass
username: bac-demoadmin@12345689.zscaler.net
network:
config:
- name: vmx
type: physical
subnets:
- type: dhcp
version: '1'
[Example user data with non-default HTTP probe port and SSH key](#DHCPExample2)
[]ZSCALER:
cc_url: connector.zscaler.net/api/v1/provUrl?name=DemoBC
http_probe_port: 50035
api_key: adfads2sd
password: demopass
username: bac-demoadmin@12345689.zscaler.net
network:
config:
- name: vmx
type: physical
subnets:
- type: dhcp
version: '1'
ssh_authorized_keys:
- ssh-rsa <Key> AAAAB3NzaC1yc2EAAAADAQABAAABgQCh3ru9CCnEow69WlQyJuxvZJGHcjhcgJzp8XnoKTJk6o1bit+rq4BNyjS0orauMF6fNMHAyGZqDWw6RICvoeh386xNqnD7+AGE9VGz4cPv0CjoV2HvkKnA2Dj8KZFFJ/bBV0BndNdGATsbDnhq0wkJ+WXFmamb9kx4dSDL5ZD15SybFop0b/3JoqXoU+9pxFc0bQ/cediaifCztliI9i7NAmvIUinLy2OlDW/uPEcB8nBgXhAAc9ALe6+Q4wZt8JUdrcF04bgoAHYsNuzyEk4dNvov97JyExCAwzSLomiHFtdzhGw7/o6KhfhxxBRodKy4wQBwDzPbD6EbN9iCqoK8DY4HZ2L7HyQKRjhnnY/Y0uldO0tleogElbk+4LsoyAPjPAbogu89xSOa6D7sl2G+dPpqTlFBmO/3m/2JhBnGU= admin@branchpc
[]ZSCALER:
cc_url: <CC_URL>
http_probe_port: 50035 #Optional to change the port for load balancer status checks from the default value 50001 to 50035.
api_key: <API Key>
password: <Admin Password>
username: <Admin Username>
network:
config:
- name: <Driver>
type: physical
subnets:
- address: <IP Address/Netmask>
gateway: <Gateway>
type: static
- type: nameserver
address:
- <IP Address>
- <IP Address>
search:
- zscaler.net
version: '1'
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
- name: vtnet
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- type: nameserver
address:
- 8.8.8.8
- 8.8.4.4
search:
- zscaler.net
version: '1'
[Example user data with non-default HTTP probe port and SSH key](#StaticExample2)
[]ZSCALER:
cc_url: connector.zscaler.net/api/v1/provUrl?name=DemoBC
http_probe_port: 50035
api_key: adfads2sd
password: demopass
username: bac-demoadmin@12345689.zscaler.net
network:
config:
- name: vtnet
type: physical
subnets:
- address: 10.66.118.71/24
gateway: 10.66.118.254
type: static
- type: nameserver
address:
- 8.8.8.8
- 8.8.4.4
search:
- zscaler.net
version: '1'
ssh_authorized_keys:
- ssh-rsa <Key> AAAAB3NzaC1yc2EAAAADAQABAAABgQCh3ru9CCnEow69WlQyJuxvZJGHcjhcgJzp8XnoKTJk6o1bit+rq4BNyjS0orauMF6fNMHAyGZqDWw6RICvoeh386xNqnD7+AGE9VGz4cPv0CjoV2HvkKnA2Dj8KZFFJ/bBV0BndNdGATsbDnhq0wkJ+WXFmamb9kx4dSDL5ZD15SybFop0b/3JoqXoU+9pxFc0bQ/cediaifCztliI9i7NAmvIUinLy2OlDW/uPEcB8nBgXhAAc9ALe6+Q4wZt8JUdrcF04bgoAHYsNuzyEk4dNvov97JyExCAwzSLomiHFtdzhGw7/o6KhfhxxBRodKy4wQBwDzPbD6EbN9iCqoK8DY4HZ2L7HyQKRjhnnY/Y0uldO0tleogElbk+4LsoyAPjPAbogu89xSOa6D7sl2G+dPpqTlFBmO/3m/2JhBnGU= admin@branchpc
-
Apply your user data to the VM as an ISO image using one of the following procedures:
- [Windows](#Windows)
- [macOS](#MacOS)
- [Linux](#Linux)
[]
- Install the Development Tools component from the [Windows ADK](https://learn.microsoft.com/en-us/windows-hardware/get-started/adk-install).
- Add `oscdimg.exe` to your `PATH `Windows environment variable.
-
Use PowerShell or Command Prompt (CMD) to generate the ISO.
`> mkdir isodir`
-
Edit `isodir\user-data` and insert the contents of your `userdata.cfg` file. The user data file must be named `user-data`.
`> oscdimg.exe -j1 -u1 -lcidata .\isodir\user-data`
[]
-
Install `cdrtools `using a method such as [Homebrew](https://brew.sh/). (This procedure uses Homebrew.)
`$ brew install cdrtools`
-
Use Terminal to generate the ISO.
`> mkdir isodir`
-
Edit `isodir/user-data` and insert the contents of your `userdata.cfg` file. The user data file must be named `user-data`.
`> mkisofs -output user-data.iso -volid cidata -joliet -rock isodir/user-data`
[]
- Install `genisoimage`.
-
On Centos, RedHat, or Rocky Linux:
`sudo yum install genisoimage`
-
On Ubuntu or Debian Linux:
`sudo apt install genisoimage`
-
Generate the ISO.
`> mkdir isodir`
-
Edit `isodir/user-data` and insert the contents of your `userdata.cfg` file. The user data file must be named `user-data`.
`> geniosimage -o user-data.iso -volid cidata -joliet -rational-rock isodir/user-data`
[]Deploying the Branch Connector
After you have met all the [prerequisites](#Prereqs), [created user data, and applied user data to the VM](#UserData), perform the following procedure to deploy your Branch Connector on Linux KVM.
[Deployment Procedure](#procedure)
[]
- Log in to Virtual Machine Manager.
- Go to** File **> **New Virtual Machine**.
[See image.](#SeeImage1)
- In the **New VM **window, select** Import existing disk image**. Then, click **Forward**.
[See image.](#seeimage2)
- Click** Browse** to upload the Linux KVM image downloaded from the [Branch Connector Images](cloud-connector/brnch/about-branch-connector-images) page.
[See image.](#seeimage3)
- For** Choose the operating system you are installing**, select **Free BSD 11.4**. Then, click **Forward**.
[See image.](#seeimage4)
- For **Choose Memory and CPU settings**, configure the memory and CPU settings based on the VM specifications. Then, click **Forward**.
[See image.](#seeimage5)
- Enter a** Name** for the Branch Connector, enable **Customize configuration before install**, and** **select a network under **Network selection**.** **Then, click **Finish**.
[See image.](#seeimage6)
- The Branch Connector configuration window appears displaying an overview of your Branch Connector and hypervisor details. Click **Add Hardware**.
[See image.](#seeimage8)
- In the **Locate or create storage volume **window, select the **user-data.iso** file you created. Then, click **Choose Volume**.
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
[]Managing the Branch Connector
After your VM is fully deployed, you can manage the Branch Connector & App Connector VM from the Cloud & Branch Connector Admin Portal. A deployed VM is displayed in the dashboard. The[ Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation, and status of your VMs deployed in your branch account.
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/cloud-branch-connector/configuring-traffic-forwarding-rule)
- [Log and Control Forwarding](/cloud-branch-connector/configuring-log-and-control-forwarding-rule)
- [DNS Filtering](/cloud-branch-connector/configuring-dns-filtering-rule)
[]![New Virtual Machine selected in the Virtual Machine Manager](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/NewVirtualMachine.png)
[]![Import Existing Disk Image selected for installing the operating system.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/ImportExistingDiskImage.png)
[]![Browse in the Storage Path ](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Browse_StoragePath.png)
[]![Provide existing storage path and choose the operating system you are installing.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/StoragePath_OperatingSystem.png)
[]![The Memory and CPU settings](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Memory_CPU_Settings.png)
[]![Customize configuration before install and network selection. ](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/NetworkSelection_CustomizeConfiguration2.png)
[]![Branch Connector Overview with Add Hardware selected.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/BranchConnectorOverview_AddHardware.png)
[]![Locate or create storage volume window demonstrating user-data.iso file](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/Locate_CreateStorageVolume.png)
[]![The Device Type demonstrating the CDROM device.](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/DeviceType2.png)
[]![Network Source, MAC Address, and Device Model from Network tab. ](/downloads/cloud-connector/deployment-management/deploying-branch-connector-linux-kvm/AddNewVirtualHardware_NetworkConfig.png)
[]