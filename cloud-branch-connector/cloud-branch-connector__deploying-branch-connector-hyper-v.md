# Deploying Branch Connector with Hyper-V
Source: https://help.zscaler.com/cloud-branch-connector/deploying-branch-connector-hyper-v
PDF: https://help.zscaler.com/pdf/com/en/1478956.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Branch Connector as a virtual machine (VM) on Hyper-V platforms, and post-deployment configurations.
Infrastructure as Code (IaC) deployment templates are not available for Branch Connector deployment on Hyper-V platforms.
[]Prerequisites
The role that you assign dictates the level of access an admin has to the [Zscaler Cloud & Branch Connector Admin Portal](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal). Zscaler provides a default [admin ](/cloud-branch-connector/about-administrator)account that provides full access to the portal and scope over the entire organization. Admins must have full access to Branch Connector configuration permissions to perform the procedures in this article. To learn more, see [About Role Management](/cloud-branch-connector/about-role-management) and [Adding Admin Roles](/cloud-branch-connector/adding-cloud-connector-roles).
Make sure the following prerequisites are met:
- In the Cloud & Branch Connector Admin Portal, create a dedicated username for the Branch Connector deployment.
- In the Cloud & Branch Connector Admin Portal, create a dedicated password for the Branch Connector deployment. The password must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character. The password must not contain a `$`, `&`, `>`, `<`, `;`, `'`, or `"`. If the password does not meet these requirements, the deployment fails.
- Configure a [Branch Provisioning Template](/cloud-branch-connector/configuring-branch-configuration-template) and copy the Branch Provisioning URL for later use.
- Download the Branch Connector Virtual Hard Disk v2 (VHDX) image from the [Branch Connector Images](/cloud-branch-connector/downloading-branch-connector-images) page for Hyper-V.
- Branch Connector uses an API key to authenticate and register the VM with the Zscaler service. If you do not already have an API key, generate a new key. Then copy the API key from the [API Key Management ](/cloud-branch-connector/about-api-key-management)page.
- Review the following Branch Connector specifications and sizing requirements:
- Small VM: Requires 4 GB of memory, 2 CPU cores, 128 GB data disk size, and 2 network interface cards (NICs).
- Medium VM: Requires 8 GB of memory, 4 CPU cores, 128 GB data disk size, and 4 NICs.
- If a Hyper-V switch does not already exist, create one.
- VM specification for Branch Connector deployed in high availability (HA): MAC Address Spoofing must be enabled on each network adapter.
[]Creating and Applying User Data
You must create a text file containing user data information for your Branch Connector VM. You apply this information to the VM in the Hyper-V Manager UI with an International Organization for Standardization (ISO) file that is mounted via a virtual CD-ROM drive.
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
After you have met all the [prerequisites](#Prereqs), [created user data, and applied user data to the VM](#Userdata), perform the following procedure to deploy your Branch Connector with Hyper-V.
[Deployment Procedure](#procedure)
[]
-
In Hyper-V Manager, right-click your desired host and select **New** > **Virtual Machine**.
[See image.](#NewVM)
- Complete the **New Virtual Machine Wizard**.
- If the **Before You Begin** tab is displayed, click **Next**.
-
On the **Specify Name and Location** tab, enter the **Name**. Select the **Store the virtual machine in a different location** checkbox if you do not want to use the default folder. Then click **Next**.
[See image.](#NameLocation)
-
On the **Specify Generation** tab, select **Generation 1** as the VM generation to support your VHDX file. Then click **Next**.
[See image.](#Generation)
-
On the **Assign Memory** tab, in the **Startup memory** field, enter `4096` for a Small VM or `8192` for a Medium VM. Deselect the **Use Dynamic Memory for this virtual machine** checkbox. Then click **Next**.
[See image.](#Memory)
-
On the **Configure Networking** tab, select the virtual switch you want the provided network adapter to use. Then click **Next**.
[See image.](#Networking)
-
On the **Connect Virtual Hard Disk** tab, select **Use an existing virtual hard disk** and select the **Location **you specified for the VHDX file you downloaded earlier. Then click **Next**.
[See image.](#VirtualHardDisk)
-
On the **Completing the New Virtual Machine Wizard**, click **Summary**, review the information, and then click **Finish**.
[See image.](#Summary)
- In Hyper-V Manager, right-click the VM and select **Settings > Hardware**.
-
Select **Processor**. In the **Number of virtual processors** field, select **2** for a Small VM or **4** for a Medium VM. Then click **Apply**.
[See image.](#Processors)
-
Select **DVD Drive **under **IDE Controller 1**. Select **Image file** and map the userdata ISO file you created earlier to the DVD drive. Then click **Apply**.
[See image.](#DVD)
-
Select **Add Hardware** > **Network Adapter**. Click **Add**, and select the required virtual switch. If you require VLAN tagging, select the **VLAN ID** checkbox. Then click **Apply**.
Repeat this step as needed for a total of 2 network adapters for a Small VM or 4 network adapters for a Medium VM.
[See image.](#NetworkAdapter)
-
For each network adapter, click **+** and select **Advanced Features**. Under **MAC address**, select the **Enable MAC address spoofing** checkbox. Then click **Apply**.
[See image.](#MACAddressSpoofing)
MAC address spoofing must be enabled for high availability (HA) deployments. Zscaler recommends that you enable MAC address spoofing for non-HA deployments, as well.
-
Select **BIOS**. In the boot device **Startup order** list, move **IDE** above **CD**. Then click **OK**.
[See image.](#BIOS)
-
In Hyper-V Manager, right-click the VM and select **Start**.
[See image.](#Start)
[]Managing the Branch Connector
After your VM is fully deployed, you can manage the Branch Connector VM from the Cloud & Branch Connector Admin Portal. A deployed VM is displayed in the dashboard. The [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation, and status of the VMs deployed in your branch account.
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/cloud-branch-connector/configuring-traffic-forwarding-rule)
- [Log and Control Forwarding](/cloud-branch-connector/configuring-log-and-control-forwarding-rule)
- [DNS Filtering](/cloud-branch-connector/configuring-dns-filtering-rule)
[]![Create New Virtual Machine menu](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_NewVM.PNG)
[]![Name and Location Wizard screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_NameAndLocation.PNG)
[]![Specify Generation wizard screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_Generation.PNG)
[]![Assign Memory wizard screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_MemoryMedium.PNG)
[]![Configure Networking wizard screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_VirtualSwitch.PNG)
[]![Connect Virtual Hard Disk wizard screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_HardDisk.PNG)
[]![Wizard Summary screen](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_Summary1.png)
[]![Processor hardware settings](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_ProcessorMedium1.png)
[]![DVD drive hardware settings](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Wizard_DVD1.png)
[]![Add Network adapter hardware settings](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Settings_NetworkAdapter1.png)
[]![MAC address spoofing](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-branch-connector-hyper-v-draft2-doc-51457/Settings_MACAddressSpoofing1.png)
[]![BIOS boot order hardware setting](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/Settings_BIOSBoot1.png)
[]![Navigation to start virtual machine](/downloads/cloud-branch-connector/deployment-management/branch-connector-deployment-management/deploying-branch-connector-hyper-v/VM_Start.PNG)