# Deploying Branch Connector with Hyper-V
Source: https://help.zscaler.com/unified/deploying-branch-connector-hyper-v
PDF: https://help.zscaler.com/pdf/com/en/1517496.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Branch Connector as a virtual machine (VM) on Hyper-V platforms, and post-deployment configurations.
Infrastructure as Code (IaC) deployment templates are not available for Branch Connector deployment on Hyper-V platforms.
[]Prerequisites
The role that you assign dictates the level of access an admin has to the Admin Portal. Zscaler provides a default [admin ](/unified/about-administrators-0)account that provides full access to the portal and scope over the entire organization. Admins must have full access to Branch Connector configuration permissions to perform the procedures in this article. To learn more, see [About Role Management](/unified/about-role-management-1) and [Adding Admin Roles](/unified/adding-admin-roles-0).
Make sure the following prerequisites are met:
- In the Admin Portal, create a dedicated username for the Branch Connector deployment.
- In the Admin Portal, create a dedicated password for the Branch Connector deployment. The password must be at least 8 characters in length and include at least one uppercase letter, one number, and one special character. The password must not contain a `$`, `&`, `>`, `<`, `;`, `'`, or `"`. If the password does not meet these requirements, the deployment fails.
- Configure a [Branch Provisioning Template](/unified/configuring-branch-configuration-template) and copy the Branch Provisioning URL for later use.
- Download the Branch Connector Virtual Hard Disk v2 (VHDX) image from the [Branch Connector Images](/unified/downloading-branch-connector-images) page for Hyper-V.
- Branch Connector uses an API key to authenticate and register the VM with the Zscaler service. If you do not already have an API key, generate a new key. Then copy the API key from the [API Keys](/unified/about-api-configuration) page.
- Review the following Branch Connector specifications and sizing requirements:
- Small VM: Requires 4 GB of memory, two CPU cores, 128 GB data disk size, and two network interface cards (NICs).
- Medium VM: Requires 8 GB of memory, 4 CPU cores, 128 GB data disk size, and 4 NICs.
- If a Hyper-V switch does not already exist, create one.
- VM specification for Branch Connector deployed in high availability (HA): MAC Address Spoofing must be enabled on each network adapter.
[]Creating and Applying User Data
You must create user data information for your Branch Connector VM. You can either apply this information to the VM in the Hyper-V Manager UI with an ISO file that is mounted via a virtual CD-ROM drive or apply it manually in the VM console in the `/etc/cloud/cloud.cfg.d/` directory. For both methods, you must create a text file containing the user data.
-
[]Create your user data in a text file named `userdata.cfg` using one of the following templates, formatted in YAML:
- [Branch Connector with Management DHCP Template](#DHCP)
- [Branch Connector with Static Management IP Template](#Static)
[]ZSCALER:
cc_url: <CC_URL>
http_probe_port: 50035 #Optional to change the port for load balancer status checks from the default value 50001 to 50035.
api_key: <API Key>
password: <Admin Password>
username: <Admin Username>
network:
config:
- name: hn0
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
- name: hn0
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
- name: hn0
type: physical
subnets:
- type: dhcp
version: '1'
ssh_authorized_keys:
- ssh-rsa ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQCh3ru9CCnEow69WlQyJuxvZJGHcjhcgJzp8XnoKTJk6o1bit+rq4BNyjS0orauMF6fNMHAyGZqDWw6RICvoeh386xNqnD7+AGE9VGz4cPv0CjoV2HvkKnA2Dj8KZFFJ/bBV0BndNdGATsbDnhq0wkJ+WXFmamb9kx4dSDL5ZD15SybFop0b/3JoqXoU+9pxFc0bQ/cediaifCztliI9i7NAmvIUinLy2OlDW/uPEcB8nBgXhAAc9ALe6+Q4wZt8JUdrcF04bgoAHYsNuzyEk4dNvov97JyExCAwzSLomiHFtdzhGw7/o6KhfhxxBRodKy4wQBwDzPbD6EbN9iCqoK8DY4HZ2L7HyQKRjhnnY/Y0uldO0tleogElbk+4LsoyAPjPAbogu89xSOa6D7sl2G+dPpqTlFBmO/3m/2JhBnGU= admin@branchpc
[]ZSCALER:
cc_url: <CC_URL>
http_probe_port: 50035 #Optional to change the port for load balancer status checks from the default value 50001 to 50035.
api_key: <API Key>
password: <Admin Password>
username: <Admin Username>
network:
config:
- name: hn0
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
- name: hn0
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
- name: hn0
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
You attach the ISO to your Branch Connector VM in the [Deploying the Branch Connector](#Deployment) procedure.
[]You apply your user data at the end of the [Deploying the Branch Connector](#Deployment) procedure.
[]Deploying the Branch Connector
After you have met all the [prerequisites](#Prereqs), created [user data](#Userdata), and applied user data to the VM (if you used the [ISO method](#ISOMethod)), perform the following procedure to deploy your Branch Connector with Hyper-V.
[Deployment Procedure](#procedure)
[]
-
In Hyper-V Manager, right-click your desired host and select **New** > **Virtual Machine**.
[See image.](#NewVM)
- Complete the **New Virtual Machine Wizard**.
- If the **Before You Begin** tab is displayed, click **Next**.
-
On the **Specify Name and Location** tab, enter the name and location. Then click **Next**.
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
On the **Connect Virtual Hard Disk** tab, select **Use an existing virtual hard disk** and select the location you specified for the VHDX file you downloaded earlier. Then click **Next**.
[See image.](#VirtualHardDisk)
-
On the **Summary** tab, review the information and then click **Finish**.
[See image.](#Summary)
- In Hyper-V Manager, right-click the VM and select **Settings > Hardware**.
-
Select **Processor**. In the **Number of virtual processors** field, select **2** for a Small VM or **4** for a Medium VM. Then click **Apply**.
[See image.](#Processors)
-
If you applied user data to the VM using the [ISO Method](#ISOMethod), select the DVD drive under **IDE Controller 1**. Select **Image file** and map the userdata ISO file you created in the ISO Method procedure to the DVD drive. Then click **Apply**.
[See image.](#DVD)
-
Select **Add Hardware** > **Network Adapter** and then click **Add**. Create two network adapters for a Small VM or 4 network adapters for a Medium VM. For each adapter, select the required virtual switch. If you require VLAN tagging, select the **VLAN ID** checkbox. Then click **Apply**.
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
- []If you are using the [Manual Method](#ManualMethod) to apply user data to the VM:
-
In the VM console, create a new `userdata.cfg` file:
`zsroot@zscaler_node : ~ > sudo ee /etc/cloud/cloud.cfg.d/userdata.cfg`
- Paste in the contents of your user data file.
- Press `Esc` (Escape**)** to exit the editor.
- Press `a` to leave the editor.
- Press `a` to save the file.
-
Reboot the VM:
`zsroot@zscaler_node : ~ > sudo reboot`
[]Managing the Branch Connector
After your VM is fully deployed, you can manage the Branch Connector VM from the Admin Portal. A deployed VM is displayed in the dashboard. The [Cloud & Branch Connector Monitoring](/unified/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation, and status of the VMs deployed in your branch account.
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/unified/about-traffic-forwarding)
- [Log and Control Forwarding](/unified/about-log-and-control-forwarding)
- [DNS Filtering](/unified/about-dns-policies)
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