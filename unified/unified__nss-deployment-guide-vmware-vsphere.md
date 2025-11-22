# NSS Deployment Guide for VMware vSphere
Source: https://help.zscaler.com/unified/nss-deployment-guide-vmware-vsphere
PDF: https://help.zscaler.com/pdf/com/en/1496681.pdf

Zscaler's [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service) can be deployed via VMware vSphere. This guide describes the tasks required for NSS deployment, enabling you to stream either Web or Firewall logs to a security information and event management (SIEM) system.
Prerequisites
Ensure you have a [subscription](/unified/viewing-subscriptions) to either NSS for Web or NSS for Firewall and review the following specifications and requirements:
- [VM Specs](#vm-specs)
- [Host Specs](#host-specs)
- [Network Specs](#network-specs)
- [Firewall Requirements](#fw-reqs)
Deploying NSS
To deploy NSS:
- [Step 1: In the Admin Portal, Add an NSS Server and Download the SSL Certificate](#step-add-nss-server-download-ssl-certificate)
- [Step 2: In the Admin Portal, Compute the Recommended VM Instance Specifications](#step-compute-recommended-vm-instance-specs)
- [Step 3: Using the ESX/ESXi Server, Configure and Start the NSS on the VM Instance](#step-configure-start-nss-vm-instance)
- [Step 4: In the Admin Portal, Add NSS Feeds](#step-add-nss-feeds)
Post-Deployment Tasks
After you have verified your deployment, you can perform additional tasks:
- [Deploying Multiple NSS Virtual Machines for Reliability](#deploying)
- [Configuring Advanced NSS Settings](#Networking)
- [Troubleshooting the NSS](#Troubleshooting)
[]
- 2 CPU cores: NSS uses one core for the control plane and another core for the data plane.
- Instance memory:
- 8 GB for up to 15K users
- 16 GB for up to 40K users
- 32 GB for up to 100K users. If you have more than 100K users, contact Zscaler Support.
- Data disk size: 500 GB
For recommended VM instance specifications, see Step 2.
- []Hypervisor: VMware ESX/ESXi v5.0 and later
- Host CPU: 64-bit Xeon or equivalent
- Host CPU Speed: Greater than or equal to 2.40GHz
- VMware vSphere Client or vCenter
- []Network Adapter: E1000
- Network Specs:
- VM Network: 2 Virtual NICs. Optionally, you might need two additional virtual NICs as described in [Configuring Advanced NSS Settings](/unified/configuring-advanced-nss-settings).
- Bandwidth for log download: 11 Mbps for 10K users is an example average value.
- IP Addresses: The following table lists the IP addresses and the interfaces on which they're configured. Internal IP addresses are allowed. The management IP address and service IP address can be on different subnets, as long as the DNS server can be reached on both subnets.
[](/unified/configuring-advanced-nss-settings)[](/unified/configuring-advanced-nss-settings)
| Virtual Interface | IP Address | Description |
| ----------------- | ---------- | ----------- |
| em0 (First network adapter) | Management IP Address | This is used for control connections to the Zscaler cloud and to make an SSH connection to the NSS VM for configuration and management.You can customize the deployment and define a separate IP address for the SSH connection to the NSS VM. To learn more, see Configuring Advanced NSS Settings. |
| em1 (Second network adapter) | Service IP Address | This is used for data connections to the Zscaler cloud and to the SIEM. |
| em2 (Third network adapter) | (Optional) Second Management IP Address | In cases where the default management interface cannot be used for SSH due to VLAN restrictions, Zscaler recommends that you add an additional interface just for management, so the first interface is used only for control connections to the cloud. To learn more, see Configuring Advanced NSS Settings. |
| em3 (Fourth network adapter) | (Optional) Second Service IP Address | In cases where the default service interface cannot be used to connect to the Zscaler cloud and to the SIEM, you can add an additional service interface, so one service interface can be used to connect to the Zscaler cloud, and a separate interface can be used to connect to the SIEM. |
[]It is mandatory to deploy the NSS instance behind a VM network security group. The NSS instance requires only outbound connections to the Zscaler cloud. It doesn't require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, refer to the Zscaler Cloud Configuration Requirements for your Zscaler cloud: https://config.zscaler.com/<Zscaler Cloud Name>/nss.
You can find the name of your Zscaler cloud in the URL you use to log in to the Zscaler service. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/nss](https://config.zscaler.com/zscaler.net/nss).
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
Communication from the NSS to the Zscaler cloud must be excluded from SSL inspection to ensure that the NSS can authenticate to the Nanolog cluster using mutual TLS.
Zscaler does not recommend or support forwarding outbound traffic from the NSS to or through the Internet & SaaS Public Service Edge as this can result in networking, latency, and administration issues.
[]
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
From the **NSS Servers **tab, click **Add NSS Server**.
The **Add NSS Server** window appears.
-
In the **Add NSS Server **window:
- **Name**: Enter a name for the NSS.
-
**Type**: **NSS for Web** is selected by default. If you are configuring an NSS for firewall logs, select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **Status**: The NSS is **Enabled** by default.
[See image.](#add_nss_server_img)
- Click **Save**.
-
Click **Download** in the **SSL Certificate** column of the NSS that you are configuring, and then save the certificate. You later upload the certificate to the vSphere Client.
[See image.](#ssl_cert_download_img)
[]![Add NSS Server](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-server-vmware-vsphere.png)
[]![NSS SSL Certificate Download](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-server-web-ssl-certificate.png)
[]You must enter information about your traffic and users so that the Zscaler service can compute the appropriate resources for your NSS.
The NSS buffers the logs for at least one hour. If a SIEM goes offline for maintenance or if the connection between the NSS and the SIEM is disrupted, the NSS buffers the logs and sends them once the connection is re-established. The amount of memory required to buffer the logs is incorporated into the VM spec computation. The buffer size increases proportionally to the amount of RAM allocated to the NSS.
To compute the appropriate resources for your NSS:
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
Click **Deploy NSS Virtual Appliance**.
The **NSS Virtual Appliance Deployment** window appears.
-
In the **NSS Virtual Appliance Deployment **window, choose either of the following NSS types:
- [NSS for Web](#nss_web)
- [NSS for Firewall](#nss_fw)
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- For your platform, select **VMware**.
-
Click **Compute**.
The recommended VM Specs and Hypervisor Specs are listed.
[See image.](#vm_hypervisor_specs_img)
- Click **Download NSS Virtual Appliance** to download the NSS OVA file.
- Click **Close**.
[]![VMware recommended VM and hypervisor specs](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-virtual-appliance-vmware-vsphere-specs.png)
[]To determine the memory and bandwidth requirements:
- **Number of Users**:** **Enter the number of users. The service displays the recommended resources for the NSS and the ESX/ESXi hypervisor.
- **Peak Transactions per Hour**: The peak number of transactions in an hour. You can retrieve this data by going to **Internet & SaaS** > **Dashboard **> **Web Overview**. This is recommended to fine-tune the VM specification to your organization’s workload.
[See image.](#nss_web_img)
The recommended internet bandwidth is the peak bandwidth required to download the logs from the Nanolog in the Zscaler cloud. If the NSS is not allocated the bandwidth it needs, the logs can accumulate in the Nanolog. This can result in frequent connection resets and the logs are not streamed to the NSS.
[]![NSS for Web for VMware](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-virtual-appliance-vmware-vsphere-web.png)
[]To determine the memory and bandwidth requirements:
- **Number of Users**:** **Enter the number of users. The service displays the recommended resources for the NSS and the ESX/ESXi hypervisor.
- **Peak Sessions Per Hour**:** **The peak number of sessions in an hour. You can retrieve this data by going to **Internet & SaaS** > **Dashboard** > **Firewall Overview**. This is recommended to fine-tune the VM specification to your organization’s workload.
- **Peak DNS Requests Per Hour**: The peak number of DNS requests in an hour. You can retrieve this data by going to **Internet & SaaS** > **Dashboard** > **DNS Overview**. This is recommended to fine-tune the VM specification to your organization’s workload.
[See image.](#nss_fw_img)
The recommended internet bandwidth is the peak bandwidth required to download the logs from the Nanolog in the Zscaler cloud. If the NSS is not allocated the bandwidth it needs, the logs can accumulate in the Nanolog. This can result in frequent connection resets and the logs are not streamed to the NSS.
[]![NSS for Firewall for VMware](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-virtual-appliance-vmware-vsphere-fw.png)
[]Before you configure and start the NSS on the vSphere Client, ensure that you have [downloaded the SSL certificate](/unified/nss-deployment-guide-vmware-vsphere#step-add-nss-server-download-ssl-certificate) and [NSS OVA file](/unified/nss-deployment-guide-vmware-vsphere#step-compute-recommended-vm-instance-specs) from the Admin Portal.
To configure the NSS virtual appliance on the VM, log in to the vSphere Client and:
- [a. Import the NSS OVA file.](#import)
- [b. Configure the network.](#network)
- [c. Install the SSL certificate.](#installssl)
- [d. Download the NSS binaries.](#downloadbinaries)
- [e. Start the NSS.](#startnss)
- [f. Verify the configuration.](#verifyconfig)
Optionally, you can also install the VMware tools for the NSS OVA.
To install VMware tools:
- Log in (SSH) to the NSS and run the following command:
sudo bash
You are prompted to enter a password.
- In `/etc/pkg/FreeBSD.conf`, change the `url` to the following:
"http://pkg.zspreview.net/FreeBSD:11:amd64/latest/"
`/etc/pkg/FreeBSD.conf` should contain only the following lines:
FreeBSD: {
url: "http://pkg.zspreview.net/FreeBSD:11:amd64/latest/",
enabled: yes
}
- Run the following command:
pkg install open-vm-tools
- Edit the `/etc/rc.conf` and add the following entries to it:
vmware_guestd_enable="YES"
vmware_guest_vmmemctl_enable="YES"
vmware_guest_vmxnet_enable="YES"
- Reboot from the vSphere menu for the NSS instance.
- Check the status of the VMware tools under the **General Information** section.
- Run the following command to check the status:
/usr/local/etc/rc.d/vmware-guestd status
[]
- In the left-side navigation, go to **Virtual Machines**.
-
Click **Create / Register VM**.
[See image.](#img-vsphere-create-vm-button)
The **New virtual machine wizard** appears.
- In the **New virtual machine wizard**:
-
Select **Deploy a virtual machine from an OVF or OVA file** and click **Next**.
[See image.](#img-vsphere-vm-wizard-select-creation-type)
-
Enter a name for the VM and upload the OVA file that you downloaded from the Admin Portal. Click **Next**.
[See image.](#img-vsphere-vm-wizard-name-ova)
-
Select storage for the VM and click **Next**.
[See image.](#img-vpshere-vm-wizard-storage)
-
Select a **VM Network** and click **Next**.
[See image.](#img-vpshere-vm-wizard-deployment-options)
-
Review your settings before clicking **Finish** to close the wizard and deploy the VM.
[See image.](#img-vpshere-vm-wizard-review)
-
[]Power on the newly deployed NSS VM.
[See image.](#img-vsphere-power-on-vm)
-
Click the **Console** tab and log in to the ZscalerOS command prompt with the following credentials:
- Username: `zsroot`
- Password: `zsroot`
[See image.](#img-vpshere-command-prompt-login)
The default login credentials are different from those that were used in NSS VM versions earlier than 4.2.1. By default, root login is not permitted. Administrators must use the utility `sudo` to run a command with higher privileges.
Zscaler strongly recommends that you change this default password by running the command `passwd`. For more details about running this command, [click here.](#password)
- Enter the command `sudo nss configure` and complete the following:
- Enter the DNS server IP address (e.g., `72.52.97.10`).
- Enter the management interface IP with CIDR netmask. Use the management IP address for SSH or FTP (e.g., `192.168.3.1/16`).
- Enter the default gateway for the management IP address (e.g., `192.168.1.1`).
- Enter the service IP address with CIDR netmask (e.g., `192.168.3.2/16`). NSS uses the service IP address to communicate with the Zscaler cloud and with the SIEM.
- Enter the default gateway for the service IP address (e.g., `192.168.1.1`).
The management IP address and service IP address can be on different subnets, as long as the DNS server can be reached on both subnets.
[See image.](#sudonssconfig_img)
- Check the applied network configuration by running the following command:
sudo nss dump-config
[]![Screenshot of FreeBSD command prompt showing the sudo nss configure configuration. This is to configure an NSS on the vSphere client.](/downloads/zia/vsphere_nss_configure_command_prompt_screenshot.png)
- []To change the password, enter `passwd`** **and your username. For example, if you are using the default username, the command is:
passwd zsroot
- When prompted, specify the following:
- Your current password. For example, if you are using the default password, enter `zsroot`.
- Your new password
![Screenshot of FreeBSD command prompt login to change your password](/downloads/zia/freebsd_command_prompt_password_screenshot.png)
[]The NSS uses the SSL certificate to authenticate itself to the Zscaler service. Ensure that the SSL certificate is installed on only one active NSS VM at a time. Having multiple NSS VMs that use only one certificate causes cloud connection flapping, which disrupts the streaming of logs to the NSS.
- Navigate to the SSL certificate that you saved from the Admin Portal.
- Use FTP, SCP, or SFTP to upload it to the management IP address of the NSS.
- On the vSphere Client, click the **Console** tab and log in with the following credentials:
- Username: `zsroot`
- Password: `zsroot`
- Use to the **Console** tab or use SSH to connect to the management IP address.
- Run the following command, specifying the path to your uploaded certificate bundle. The path shown in red is an example.
sudo nss install-cert /usr/home/zsroot/NssCertificate.zip
- Check the configuration by running the following command:
sudo nss dump-config
[]Before starting the NSS:
- On the vSphere Client, click the **Console** tab or use SSH to connect to the management IP address.
- Run the following command to download and install the NSS binaries:
sudo nss update-now
After the first NSS software deployment, the software is automatically updated with new versions.
- []On the vSphere Client, click the **Console** tab or use SSH to connect to the management IP address.
- Run the following command:
sudo nss start
Ensure that the command shows that the NSS virtual appliance started successfully. It can take a few minutes for the NSS to start streaming logs to the SIEM.
[See image.](#img-vpshere-command-prompt-start-nss)
After starting the NSS for the first time, you can run the following command to check that the latest NSS software version is installed:
sudo nss checkversion
To enable the NSS to start automatically after a restart, run the following command:
sudo nss enable-autostart
You can also explore other options by running the following command:
sudo nss help
[]To verify the configuration, run the following command:
sudo nss troubleshoot netstat|grep tcp
When the output of the command is displayed, verify the following TCP connections are established:
- `Connection to the Zscaler cloud on port 443`: This is the control connection that is used to authenticate the NSS to the Zscaler Central Authority (CA) and to download the configuration (e.g., 10.66.69.215.443). It's also the data connection to the Nanolog so it can stream the logs (e.g., 10.66.126.443).
-
`Connection to the SIEM`: This is the long-lived TCP connection to the SIEM on the specified log data port (e.g., 10.66.69.43.44332). If there are multiple feeds configured, multiple connections must be listed.
[See image.](#img-vpshere-command-prompt-tcp-connections)
The absence of any one of the preceding connections, even after waiting a few minutes, usually indicates that there is a firewall configuration issue and the logs cannot be streamed. To troubleshoot issues, see [Troubleshooting Deployed NSS Servers](/unified/troubleshooting-deployed-nss-servers).
[]![Create / Register VM button in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-create-vm-button.png)
[]![New virtual machine wizard in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-select-creation-type.png)
[]![New virtual machine wizard in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-select-ovf-vmdk-files.png)
[]![New virtual machine wizard in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-select-storage.png)
[]![New virtual machine wizard in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-deployment-options.png)
[]![Reviewing settings of VM in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-review-settings-finish.png)
[]![ Power On VM task in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-power-on-vm.png)
[]![Logging in to the command prompt as zsroot](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-command-prompt.png)
[]![Starting the NSS service in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-start-success.png)
[]![verifying TCP connections in VMware vSphere](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-vmware-vsphere/zia-nss-vsphere-tcp-connections.png)
[]An NSS feed specifies the data from the logs that the NSS sends to the SIEM. You can filter the data so that you send only the data you need to the SIEM. You can add up to 16 NSS feeds for each NSS server. ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS server to ensure optimal performance.) Each feed can have different filters and fields, and a different output format (e.g., CSV). To learn more about how to configure each feed, see [Adding NSS Feeds](/unified/adding-nss-feeds).
[]An [NSS server](/unified/adding-nss-servers) represents the NSS virtual machine (VM) in the Admin Portal. When you create an NSS server in the portal, an SSL certificate is generated. You download the SSL certificate from the portal and upload it to the NSS VM that you configure and [deploy](/unified/deploying-nss-virtual-appliances). The newly configured NSS VM uses the SSL certificate to authenticate itself to the Zscaler service.
Each NSS server supports up to 16 [NSS feeds](/unified/adding-nss-feeds). ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unified/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS to ensure optimal performance.) Each NSS feed can have different filters and fields and a different output format (e.g., CSV).
For site reliability, you can deploy multiple NSS VMs, either in an active-active or active-passive configuration.
Active-Active Configuration
Zscaler recommends leveraging two NSS servers per NSS type (i.e., NSS for Web and NSS for Firewall) and deploying each pair in an active-active configuration. In this configuration, you create two NSS servers of the same NSS type in the Admin Portal with separate SSL certificates.
Running multiple active NSS VMs with the same SSL certificate causes cloud connection flapping, which disrupts the streaming of logs to the NSS.
Optionally, for optimal reliability, you can configure the NSS VMs to stream logs to two separate SIEMs. In this configuration, each NSS VM runs independently, streaming logs to its respective SIEM at the same time.
Zscaler does not recommend configuring two NSS VMs of the same NSS type to stream logs to a single SIEM. In this case, each NSS VM sends copies of the same logs to the SIEM, which might not be able to deduplicate them.
Active-Passive Configuration
Alternatively, you can deploy multiple NSS VMs in an active-passive configuration. In this configuration, you create one NSS server (for Web or Firewall) in the Admin Portal and use the generated SSL certificate to deploy one active NSS VM; the second VM serves as a cold standby. Both NSS VMs use the same SSL certificate in this configuration, but they should not connect to the Zscaler Nanolog at the same time as this results in connection flapping.
If the active NSS VM fails, you must perform failover activities, ideally within one hour of the failure to prevent data loss. In this time frame, you can leverage the following NSS reliability mechanisms:
- **NSS to SIEM**: The NSS buffers the logs in the VM memory to increase its resiliency to transient network issues between the SIEM and the NSS. If the connection drops, the NSS replays logs from the buffer, according to the Duplicate Logs setting.
- **Nanolog to SIEM**: If the connectivity between the Zscaler cloud and the NSS is interrupted, the NSS misses logs that arrived at the Nanolog cluster during the interruption, and they are not delivered to the SIEM. When the connection is restored, the NSS one-hour recovery allows the Nanolog to replay logs up to one hour back.
To learn more about NSS for Web, NSS for Firewall, and NSS Log Recovery subscriptions, contact Zscaler Support.
[]
This article describes additional features that facilitate deploying the NSS in cases where you have specific requirements or restrictions. It includes the following topics:
The first three sections listed pertain to the [NSS deployment over VMware vSphere](/zia/nss-deployment-guide-vmware-vsphere) only.
- [Configuring a Second Management Interface](#Management)
- [Configuring a Second Service Interface](#Service)
- [Configuring the Additional Interfaces from the Console](#Additional)
- [Configuring a Local NTP Server](#Local)
- [Configuring NSS in Explicit Proxy Mode](#proxy)
- [Updating an NSS VM Hostname](#update_hostname)
- [Allowing SSH Access to the NSS Only from a Specific Subnet or IP](#allowing)
- [Setting Up Key-Based Authentication to the NSS](#key_based_auth)
[]Sometimes, the default management interface can't be used for SSH due to VLAN restrictions. In those cases, Zscaler recommends that you add an additional interface just for management, so the first interface is used only for control connections to the cloud.
There are two ways to add a second management interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- [Alternatively, you can manually configure the second management interface.](#second-management-manual)
[]To manually add a management interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Update the system configuration file `/etc/rc.conf` to configure the interface automatically after each system restart. To do this, run the following command:
sudo vi /etc/rc.conf
- Add the em2 interface to the list of network interfaces. Modify the line that starts with `network_interfaces` and change it to:
network_interfaces="em0 em1 em2 lo0"
- Add a new line at the end of the file:
ifconfig_em2="<subnet-ip-address>"
Ensure that you replace <subnet-ip-address> with the IP address of the subnet. For example:
ifconfig_em2="192.168.1.100/24”
- The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN for the newly added em2 interface, add the following lines at the end of the file:
static_routes="em2"
route_em2="-net <destination-subnet> <gateway-ip-address>"
Replace <destination-subnet> with the IP address of the destination subnet, and replace <gateway-ip-address>** **with the appropriate gateway IP address. For example:
static_routes="em2"
route_em2="-net 198.51.100.0/24 192.168.1.3"
- Reboot the VM.
- To verify the changes, ping the newly added subnet gateway and run the following command to print the route information:
sudo netstat -rn
[]The NSS typically uses the service interface to download logs from the Nanolog in the Zscaler cloud and send them to the security information and event management (SIEM) system.
Some organizations might need to use one interface to connect to the Zscaler cloud and another interface to connect to the SIEM. For example, an organization might have a SIEM in a management LAN that is not routed to the internet, and it might also have a service LAN that is routed to the internet but not to the management LAN, as shown in the following diagram.
![Diagram of one interface connecting to the Zscaler cloud and another interface connecting to the SIEM. ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/mgmt_service_lan_siem_nss_diagram.png.png)
If your organization has a similar requirement, you can configure a second service interface. You can then use one interface to connect to the Zscaler cloud to download the logs and a different interface to send the logs to the SIEM located in the management LAN.
There are two ways to add a second service interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- [Alternatively, you can manually configure the second service interface.](#second-service-manual)
[]To manually add a second service interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Copy the `sc.conf` file.
cp /sc/conf/sc.conf /sc/conf/sc.conf.old
- Use the vi Editor to edit the `sc.conf` file. Run the following command:
vi /sc/conf/sc.conf
- Add the following lines to the file, replacing the sample values in red per your configuration:
smnet_dev=em2=zs1:192.168.223.41/24
smnet_route=10.0.0.0/8/192.168.223.1
In this example, em2=zs1 is the second service interface and 192.168.223.41/24 is the service IP address with the subnet mask. If your SIEM is in the same subnet, then the second line is not required. If your SIEM is in a different subnet, add `smnet_route` and define values in the second line. For example, to reach 10.0.0.0/8, use gateway 192.168.223.1.
- Save the changes in the file and then restart the NSS by running the following command:
sudo nss restart
- Verify if the NSS is using the second service interface by running the following command:
sudo nss dump-config
[]To configure a second management interface and service interface, first ensure that you run the following** **command to set your network settings:
sudo nss configure
Then, run the following command to specify the IP addresses for the additional interfaces and their corresponding routes:
sudo nss configure split-interface
****![Screenshot of FreeBSD command prompt showing the command sudo nss configure split-interface](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/NSS%20sudo%20route%201.png)
****
During a split-interface configuration, the NSS asks for an `smnet_route`. If your SIEM is in a different network compared to the NSS smnet interface (em3=zs1) subnet, you can enter specific routes for feeds.
See the following example:
[root@NSS /sc/update]# nss configure split-interface
ifconfig_em2 (Internal Management interface IP address with netmask) [1.1.1.1/23]:
route_net:-net 1.1.1.2/12 2.1.1.1 (Options <c:change, d:delete, n:no change>) [n]
Do you wish to add a new route_net? <n:no y:yes> [n]:
smnet_dev=em3 (Internal Service interface IP address with netmask) [10.10.35.20/24]:
Do you wish to add a new smnet_route? <n:no y:yes> [n]: y
Atleast one entry required for smnet_route
smnet_route (Static route for Siem N/w ,e.g (network/subnet/gateway): 172.12.1.0/21/10.10.35.1) []: 1.3.2.1/2/2.2.1.2
Do you wish to add a new smnet_route? <n:no y:yes> [n]: 2.1.2.3/2/43.3.3.2
[]If you have a local NTP Server, you can configure the NSS to synchronize time with that server:
- Run the following as root:
crontab -e
- Add the following command:
PATH=/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/usr/games:/sc/update:/home/zsroot/bin:/sc/update
- Add the following command:
*/10 * * * * ntpdate <ntp-server-name>
Replace <ntp-server-name> with your local NTP server's FQDN or IP address.
- Save and exit.
The time synchronization command runs every 10 minutes. You can find logs for the NTP process in `/var/log/cron.`
[]Some customers might have a [no default route environment](/zia/implementing-zscaler-no-default-route-environments). This prevents the NSS from establishing connections to the Zscaler cloud. For this scenario, you can configure the NSS in explicit proxy mode, so that it tunnels all Zscaler cloud-bound connections through a proxy. These include [network connections](https://config.zscaler.com/zscaler.net/nss) and TCP connections from the NSS to the:
- Nanolog (SMSM)
- Zscaler Central Authority (CA) (SMCA)
- Update server (SMCDSS) for software updates
- Kafka server for audit log streaming
Connections from the NSS to the SIEM are not tunneled.
The NSS in explicit proxy mode can tunnel Zscaler cloud-bound connections. Based on your configuration, you can tunnel these connections without the need for internet-facing DNS resolution.
If you configure the `dnsoverproxy` flag to `1`, then the NSS in explicit proxy mode makes a CONNECT request to the following domains and the explicit proxy performs the name resolution:
- msmca.<cloudname> for the connection to the Zscaler CA
- zdistribute.<cloudname> for the connection to the update server
- kproxy.hdeu1.zdataservices.net for the connection to the Kafka server
If you configure the `dnsoverproxy` flag to `0`, then the NSS needs DNS resolution for the connections to the current master CA IP address, update server, and Kafka server.
NTP connections are not tunneled. The NSS needs DNS resolution for the NTP server. To learn more, see [Configuring a Local NTP Server](/zia/configuring-advanced-nss-settings#Local).
To configure the NSS in explicit proxy mode:
- Run the `nss configure` command to configure the two network interfaces.
- Run the `nss configure proxy` command. For example:
[root@NSS /usr/home/zsroot]# nss configure proxy
proxyserver (Proxy Host ) [10.81.153.26]:
proxyport (Proxy Port ) [443]:
dnsoverproxy (DNS over proxy: 0/1 ) []: 1
Successfully configured proxy
To undo this configuration, you can use `remove`:
nss configure proxy remove
-
Run the `sudo nss restart` command to restart the NSS service.
When the NSS starts, it tries to connect to the Zscaler CA or Nanolog using the proxy it configured.
-
Run the `nss troubleshoot netstat` command to verify the proxy (e.g., 10.81.153.26) connections for the Zscaler CA and Nanolog.
[See image.](#nss-explicit-proxy-mode-tcp-connections)
[]![Screenshot of established TCP connections to the Zscaler CA and Nanolog ](/downloads/tech-pubs-drafts/zia-draft-articles/draft-configuring-advanced-nss-settings-doc-51613/zia-nss-explicit-proxy-mode_0.png)
[]
- Log in to your NSS VM.
- Edit the file `/etc/rc.conf` using the vi Editor.
[zsroot@New_Hostname ~/$ vi /etc/rc.conf
- Add the hostname entry to the file.
hostname=<name>
- Run the `reboot` command.
root@New_Hostname:/usr/home/zsroot # reboot
- After the NSS restarts, your new hostname appears.
[]You can restrict SSH access based on IP/Subject using the following configuration in `sshd_config`:
AllowUsers zsroot@10.66.70.*
In this example, SSH is allowed only from the source IP range 10.66.70.0/24. Then, run the following** **command to make the configuration change effective:
service sshd restart
[]
- Create a .ssh directory in the home directory:* *`/home/zsroot/` under the user` root`*.*
- Upload your user public key file to the file `authorized_keys` under the directory `/home/zsroot/.ssh.`
- Adjust the file `/etc/ssh/sshd_config` with the following updates. Make a backup of this file before changing it.
ChallengeResponseAuthentication no
PasswordAuthentication no
These entries are set to `yes` by default. You can set them to `no`** **or comment them out.
- Use the following command to restart the sshd service:
service sshd restart
Replace option `restart` with `stop` and `start` as required.
- Test the new configuration on the client side using SSH (e.g., PuTTY).
[]
You can use the following commands within the virtual machine (VM) console for your platform to configure and troubleshoot the NSS server. By default, root login is not permitted, so admins must use the `sudo` utility to run a command with higher privileges.
- To start the service:
sudo nss start
- To stop the service:
sudo nss stop
- To restart the service:
sudo nss restart
- To smoothly shut down the operating system:
sudo nss halt
- To change the network configuration (i.e., IP addresses, gateway information) for the service:
sudo nss configure
To learn more, see the [NSS deployment guide](/zia/deploying-nss-virtual-appliances) for your platform.
- To configure additional interfaces:
sudo nss configure split-interface
To learn more, see [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- To configure an explicit proxy:
sudo nss configure proxy
To learn more, see [Configuring NSS in Explicit Proxy Mode](/zia/nss-advanced-deployment#proxy).
- If you configured additional interfaces using the `sudo nss configure split-interface` command and want to remove the configuration:
sudo nss configure split-interface --wipe
- To remove the network settings that were configured using the `sudo nss configure` command:
sudo nss configure --wipe
- To display the configuration file that was changed using the `sudo nss configure` command:
sudo nss dump-config
- To install NSS certificates from a specified certificate bundle file:
sudo nss install-cert <certificate bundle file>
- To check if a new NSS version is available:
sudo nss checkversion
- To manually update the NSS to the latest version:
sudo nss update-now
- To force the NSS to update, regardless of whether a new version is available:
sudo nss force-update-now
- To check the firewall configuration:
sudo nss test-firewall
This command does active firewall configuration probing by attempting to resolve the DNS names and establishing outbound connections to the Zscaler cloud. This command doesn't reset the management IP interface, so you can run it on an SSH connection.
- To view troubleshooting help command information:
sudo nss troubleshoot help
- To show the active connections on the service IP address:
sudo nss troubleshoot netstat
The output is similar to that of the netstat utility.
- To show the connections and their status:
sudo nss troubleshoot connection
This command probes the connection status over a period of time and indicates whether the connections are stable or flapping.
- To show the status of the NSS feeds:
sudo nss troubleshoot feeds
This command probes the status of the feeds and determines if the logs are queued due to the slow consumption of logs by the security information and event management (SIEM) system.
- To generate diagnostic information to send to Zscaler Support:
sudo nss collect-diagnostics
This command collects the configuration, vital statistics regarding the health of the NSS, and error statistics, and then downloads the data to a local file. This file can be emailed to Zscaler Support for troubleshooting purposes.
- To reset the network configuration:
sudo nss reset-network
- To change the SNMP admin user configuration:
sudo nss snmp-admin-configure
- To change the SNMP trap configuration:
sudo nss snmp-trap-configure
- To automatically start the NSS after reboot:
sudo nss enable-autostart
- To disable the automatic start of the NSS after reboot:
sudo nss disable-autostart
- To set up and enable MCAS:
sudo nss configure-mcas2
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. To learn more, see [Integrating with Microsoft Cloud App Security](/zia/integrating-microsoft-cloud-app-security).
- To disable MCAS:
sudo nss disable-mcas
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. You can re-enable MCAS by re-issuing the `sudo nss configure-mcas2` command.
Enabling Remote Access
An admin can request remote assistance and allow Zscaler Support to log in to their NSS server without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your NSS server:
sudo nss support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your NSS server.
- To disable Zscaler Support access to your NSS server:
sudo nss support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your NSS server:
sudo nss support-access-status
This checks the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your NSS server.
- To enable a remote debugging session:
sudo nss enable-remote-debugging
- To disable a remote debugging session:
sudo nss disable-remote-debugging
Error Codes
The following are error codes that you might encounter when executing an `sudo nss update-now` command:
| Error Code | Description |
| ---------- | ----------- |
| Error Code 96 | Invalid client certificate |
| Error Code 97 | Timeout occurred while contacting upgrade server |
| Error Code 99 | A problem occurred while downloading and installing the latest version. The `sudo force-update-now` command needs to be explicitly issued. |
Use Case
You can use the following commands to check the DNS resolution issues on the service interface and routes to the surface interface.
- To check the reachability of a server IP address using ICMP:
/sc/bin/smmgr -ys smnet='ping <IP address or Domain Name>'
- To print the server interface IP config details:
/sc/bin/smmgr -ys smnet=ifconfig
- To check the DNS resolution of a hostname:
/sc/bin/smmgr -ys smnet='route'/sc/bin/smmgr -ys host="<Domain Name>" -ys connect=dns
- To check the communication or port reachability of a server:
/sc/bin/smmgr -ys host="<FQDN of SIEM server>" -ys port=<Listening port> -ys connect=tcp
What happens if the NSS goes down?
In the event of a connection loss between the NSS server and the cloud [Nanolog](/zia/about-zscaler-cloud-architecture), the cloud retransmits the logs to the NSS up to a maximum of one hour. If the NSS is down for more than an hour, the logs falling out of the one-hour window aren't retrieved by the NSS.