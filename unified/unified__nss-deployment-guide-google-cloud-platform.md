# NSS Deployment Guide for Google Cloud Platform
Source: https://help.zscaler.com/unified/nss-deployment-guide-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1514401.pdf

Zscaler’s [Nanolog Streaming Service (NSS)](/unified/understanding-nanolog-streaming-service) supports the configuration and deployment of an NSS virtual machine (VM) on Google Cloud Platform (GCP).
After configuring and deploying an NSS VM on GCP, you can stream your organization’s Web or Firewall logs from the Zscaler cloud to your security information and event management (SIEM) system.
The following guide describes the deployment procedure with sample configurations
Prerequisites
[]Before you begin deployment, you must get access to the Zscaler-owned NSS VMDK file. To get access, contact Zscaler Support.
[]You must also have a Google Cloud Storage bucket for storing the VMDK file. To learn more about creating Google Cloud Storage buckets, refer to the [Google Cloud documentation](https://cloud.google.com/storage/docs/creating-buckets).
Additionally, ensure you have a [subscription](/unified/viewing-subscriptions) to either NSS for Web or NSS for Firewall and review the following specifications and requirements:
- [VM Specs](#vm-specs)
- [Network Specs](#network-specs)
- [Firewall Requirements](#firewall-reqs)
Deploying NSS
To deploy NSS:
- [Step 1: In the Admin Portal, Add an NSS Server and Download the SSL Certificate](#add-nss-server-ssl-certificate)
- [Step 2: In the Admin Portal, Add an NSS Feed](#article-adding-nss-feeds)
- [Step 3. In the Google Cloud Console, Transfer the VMDK File into the Bucket](#step-transfer-vmdk-file)
- [Step 4: In the Google Cloud Console, Create an NSS Image from the VMDK File](#step-create-nss-image)
- [Step 5: In the Google Cloud Console, Create a VM Instance with the NSS Image](#step-create-vm-instance)
- [Step 6: In the Google Cloud Console, Configure and Start the NSS on the VM Instance](#step-configure-start-nss)
Post-Deployment Tasks
After you have verified your deployment, you can perform additional tasks:
- [Troubleshooting Deployed NSS Servers](#article-troubleshooting-deployed-nss-servers)
- [Configuring Advanced NSS Settings](#article-configuring-advanced-nss-settings)
- [Deploying Multiple NSS Virtual Machines for Reliability](#deploying-multiple-nss-vms-reliability)
[]You [create a VM instance](/unified/nss-deployment-guide-google-cloud-platform#create-vm-instance) as a step in the deployment procedure. The VM must meet the following requirements:
- vCPUs: 2 vCPU (1 shared core)
- CPU speed: Greater than or equal to 2.40GHz
- Instance memory:
- 8 GB for up to 8K users
- 16 GB for up to 20K users
- 32 GB for up to 50K users
- 48 GB for up to 75K users
- 64 GB for more than 75K users
The following VM specs are recommended:
- Machine family: General purpose
- Boot disk type: Standard persistent disk
- Boot disk size: 500 GB
To learn more about machine types, refer to the [Google Cloud documentation](https://cloud.google.com/compute/docs/machine-resource).
- []Two network interfaces: You [create two network interfaces](/unified/nss-deployment-guide-google-cloud-platform#create-vm-instance) as a step in the deployment procedure.
- The first network interface is the management IP address. It is used for control connections to the Zscaler cloud and to make an SSH connection to the NSS VM for configuration and management. You can customize the deployment and define a separate IP address for the SSH connection to the NSS VM.
- The second network interface is the service IP address. It is used for data connections to the Zscaler cloud and to the SIEM.
- Two public IP addresses: The two public IP addresses are not required when using a NAT. A NAT network configuration works correctly as long as it has sufficient network bandwidth.
- Bandwidth for log download: 11 Mbps for 10K users is an example average value.
[]It is mandatory to deploy the NSS VM instance behind a network security group. The NSS VM instance requires only outbound connections to the Zscaler cloud. It doesn't require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, refer to the Zscaler configuration requirements for your Zscaler cloud: https://config.zscaler.com/<Zscaler Cloud Name>/nss.
You can find the name of your Zscaler cloud in the URL that you use to log in to the Zscaler service. For example, if you log in to admin.zscaler.net, then go to [https://config.zscaler.com/zscaler.net/nss](https://config.zscaler.com/zscaler.net/nss).
The Zscaler Hub IP address ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
Communication from the NSS to the Zscaler cloud must be excluded from SSL inspection to ensure that the NSS can authenticate to the Nanolog cluster using mutual TLS.
Zscaler does not recommend or support forwarding outbound traffic from the NSS to or through the Internet & SaaS Public Service Edge as this can result in networking, latency, and administration issues.
[]
- Go to **Logs **>** Log Streaming **>** Nanolog Streaming Service**.
-
From the **NSS Servers **tab, click **Add NSS Server**.
The **Add NSS Server** window appears.
-
In the **Add NSS Server **window:
- **Name**: Enter a name for the NSS server.
-
**Type**: **NSS for Web** is selected by default. To add an NSS server for Firewall logs, select **NSS for Firewall**.
If you have a subscription to Cloud & Branch Connector, the **NSS for Firewall** (NSS type) is displayed as **NSS for Firewall, Cloud & Branch Connector**.
- **Status**: The NSS server is **Enabled** by default.
[See image.](#img-add-nss-server)
-
Click **Save**.
The NSS server is added to the Admin Portal.
-
Click **Download** in the **SSL Certificate** column of the newly added NSS server, and then save the SSL certificate. You later [copy the SSL certificate to the VM instance](/unified/nss-deployment-guide-google-cloud-platform#configure-start-nss).
[See image.](#img-download-ssl-certificate)
[]
A Nanolog Streaming Service (NSS) feed specifies the data from the logs that the NSS sends to the security information and event management (SIEM) system. You can filter the data so that you send only the data you need to the SIEM. You can add up to 16 NSS feeds for each [NSS server](/zia/about-nss-servers). ([Web](/zia/adding-nss-feeds-web-logs) and [Firewall](/zia/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS server to ensure optimal performance.) Each feed can have different filters and fields, and a different output format (e.g., CSV). To learn more about how to configure each feed, see:
- [Adding NSS Feeds for Web Logs](/zia/adding-nss-feeds-web-logs)
- [Adding MCAS NSS Feeds](/zia/adding-mcas-nss-feeds)
- [Adding NSS Feeds for Firewall Logs](/zia/adding-nss-feeds-firewall-logs)
- [Adding NSS Feeds for DNS Logs](/zia/adding-nss-feeds-dns-logs)
- [Adding NSS Feeds for Tunnel Logs](/zia/adding-nss-feeds-tunnel-logs)
- [Adding NSS Feeds for SaaS Security Logs](/zia/adding-nss-feeds-saas-security-logs)
- [Adding NSS Feeds for SaaS Security Activity Logs](/zia/adding-nss-feeds-saas-security-activity-logs)
- [Adding NSS Feeds for Alerts](/zia/adding-nss-feeds-alerts)
- [Adding NSS Feeds for Admin Audit Logs](/zia/adding-nss-feeds-admin-audit-logs)
- [Adding NSS Feeds for Endpoint DLP Logs](/zia/adding-nss-feeds-endpoint-dlp-logs)
- [Adding NSS Feeds for Email DLP Logs](/zia/adding-nss-feeds-email-dlp-logs)
When adding the feed, note the SIEM IP address and TCP port for later [verifying the NSS-to-SIEM connection](/unified/nss-deployment-guide-google-cloud-platform#verify-nss-configuration).
- []In the Google Cloud Console, go to **Cloud Storage** >** Buckets** and select the bucket that you [previously created](#prereq-storage-bucket).
The **Bucket details** page appears.
-
On the **Bucket details** page, click **Upload** > **Upload files** and upload the TSV file that you [previously obtained](#prereq-contact-support) from Zscaler Support. The TSV file contains the signed URL of the Zscaler-owned NSS VMDK file [later used to create an NSS image](/unified/nss-deployment-guide-google-cloud-platform#step-create-nss-image).
[See image.](#img-bucket-upload-file)
The signed URL expires after 24 hours. If your signed URL expires, and you require a new one, contact Zscaler Support.
- After uploading, select the TSV file to open its **Object details** page.
-
On the **Object details** page, copy the **gsutil URI** for use in the subsequent steps.
[See image.](#img-object-details-gsutil-URI)
- Return to the **Bucket details **page.
-
Click **Transfer data** > **Transfer data in**.
[See image.](#img-bucket-transfer-data-in)
The **Create a transfer job** panel opens.
-
In the **Create a transfer job** panel:
-
**Get started**: Select **URL list** as the **Source type**, leave **Google Cloud Storage** as the **Destination type**, and then click **Next step**.
[See image.](#img-source-type-URL-list)
-
**Choose a source**: Enter the **gsutil URI** that you previously copied in the **URL of TSV file** field and then click **Next step**.
[See image.](#img-choose-source-TSV-file-URL)
-
**Choose a destination**: Specify the path of your destination bucket and then click **Next step**.
[See image.](#img-choose-destination-bucket-path)
-
**Choose when to run job**: Ensure **Run once** and **Starting now** are selected and then click **Next step**.
[See image.](#img-run-job-once-starting-now)
- **Choose settings**: No specific settings are required.
-
Click **Create**.
[See image.](#img-create-transfer-job)
You are redirected to the **Bucket details** page and a status message appears. In the status message, you can click **Go to job** to monitor the job in Storage Transfer Service.
[See image.](#img-transfer-job-status)
On the **Operations **tab of the** Job details **page, you can see the job status is 100 percent successful.
[See image.](#img-storage-transfer-success)
When the job status is 100 percent successful, you can see the NSS VMDK file in your specified destination bucket.
[See image.](#img-VMDK-file-bucket)
[]With the NSS VMDK file in your Cloud Storage bucket, you can import it into **Compute Engine** as a custom image.
To create an NSS image from the VMDK file:
- Go to **Compute Engine** > **Images**.
-
Click **Create Image**.
The **Create an image **page appears.
- On the **Create an image** page:
- **Name**: Enter a name for the image.
-
**Source**: Select **Virtual disk (VMDK, VHD)**.
When prompted, select **Go to new Image Import** and continue configuring the remaining fields.
[See image.](#img-new-image-import)
- **Source Cloud Storage file**: Browse to and select the NSS VMDK file in your Cloud Storage bucket.
- **Region**: Select the desired region for the image.
-
**Target project**: Select the target project for the image.
[See image.](#img-create-image-new-image-import)
(Optional) To add a new target project:
-
Click **Manage Targets**.
[See image.](#img-manage-targets)
You are redirected to the **Migrate to Virtual Machines** page.
-
On the **Migrate to Virtual Machines** page, click **+ Add**.
[See image.](#img-migrate-vms-target-projects)
The **Add target projects **panel opens.
-
In the **Add target projects** panel, select the target project and click **Add**.
[See image.](#img-add-target-projects)
-
Click **Create** to start the import process.
If the image creation fails due to a permission issue, copy the command provided in the error message that appears and run the command in Cloud Shell to resolve the issue. The following image shows an example.
[See image.](#img-image-creation-failure-command)
[]To create a VM instance with the NSS image:
- [a. Create two VPC networks.](#create-vpc-networks)
- [b. Create a firewall policy.](#create-firewall-policy)
- [c. Create a VM instance.](#create-vm-instance)
- []In the Google Cloud console, go to **VPC Network** > **VPC networks**.
-
Click **Create VPC Network**.
The **Create a VPC network** page appears.
- On the **Create a VPC network** page:
- **Name**: Enter a name for the VPC network (e.g., nss-test). This first network is later used for assigning an internal IP address to the first network interface (i.e., the management interface). The management IP address is used to control connections to the Zscaler cloud and to make an SSH connection to the NSS VM for configuration and management.
- **Maximum transmission unit (MTU)**: Zscaler recommends **1460**.
-
**Subnet creation mode**: Zscaler recommends **Automatic**, which creates a subnet in each region. If you want to manually define subnets, select **Custom**. To learn more about subnet creation mode, refer to the [Google Cloud documentation](https://cloud.google.com/vpc/docs/vpc?_gl=1*5ojig8*_ga*NjE2MjIyMjM0LjE3MDgyODUyODQ.*_ga_WH2QY8WWF5*MTcyNDk5MzUyMC4yOC4xLjE3MjQ5OTM5MTkuNTUuMC4w#subnet-ranges).
[See image.](#img-create-vpc-network)
- (Optional) In the **Firewall rules** section, you can select from existing firewall rules if they are appropriate for the VPC network. To learn more, see the [Firewall Requirements](/unified/nss-deployment-guide-google-cloud-platform#firewall-reqs) section. If you want to configure new rules, you can configure a firewall policy and associate it with the VPC network in the [subsequent step](/unified/nss-deployment-guide-google-cloud-platform#create-firewall-policy). For example, if you are creating custom subnets, you can create an appropriate firewall policy to manage them.
- Click **Create**.
- Repeat the previous steps to create the second VPC network (e.g., nss-test2) for assigning an internal IP address to the second network interface (i.e., the service interface). The service IP address is used for data connections to the Zscaler cloud and your SIEM.
- []Go to **VPC Network** > **Firewall**.
-
Click **Create Firewall Policy**.
The **Create a network firewall policy** page appears.
- On the **Create a network firewall policy **page:
-
In the **Configure policy** section, enter a name for the firewall policy, and then click **Continue**.
[See image.](#img-configure-firewall-policy)
-
In the **Add rules** section, create and add firewall rules for incoming (ingress) and outgoing (egress) traffic according to your organization’s policies, and then click **Continue**. To learn more about creating firewall rules, see the [Firewall Requirements](/unified/nss-deployment-guide-google-cloud-platform#firewall-reqs) section and refer to the [Google Cloud documentation](https://cloud.google.com/firewall/docs/firewalls).
[See image.](#img-create-firewall-rule)
- In the **Associate policy with VPC networks** section:
-
Click **Associate**.
The **Associate policy with VPC networks** panel opens.
-
On the **Associate policy with VPC networks** panel, select the VPC networks that you created (e.g., nss-test and nss-test2), and then click **Associate**.
[See image.](#img-associate-vpc-networks)
- Click **Continue**.
- Click **Create**.
- []Go to **Compute Engine** > **Images**.
-
Select the NSS image that you created, and then click **Create Instance**.
The **Create an instance** page appears.
- On the **Create an instance** page:
- **Name**: Enter a name for the instance.
- **Region**: Select the region for the instance.
-
**Zone**: Select the zone for the instance.
[See image.](#img-create-instance)
-
In the **Machine configuration** section, select a machine that meets the requirements in the [VM Specs](/unified/nss-deployment-guide-google-cloud-platform#vm-specs) section. The following image shows an example of a machine that meets the requirements:
[See image.](#img-machine-config)
-
In the **Boot disk **section, ensure your appropriate boot disk** Type** (e.g., Standard persistent disk) and **Size** (e.g., 500 GB) are configured. If not, click **Change** and configure.
[See image.](#img-boot-disk)
- In the **Advanced options** >** Networking** section:
- **IP forwarding**: Enable this setting.
-
**Network interface card**: Select **VirtIO**.
[See image.](#img-network-performance-config)
- **Network interfaces**: Add two network interfaces: the first as the management interface, and the second as the service interface. To add the two network interfaces:
- **Network**: Select the network that you created for the management interface (e.g., nss-test).
- **Subnetwork**: Select an appropriate subnetwork.
- **Primary internal IPv4 address**: Select **Ephemeral (Automatic)** to allocate an internal IP address from the subnet range. Select **Ephemeral (Custom) **to manually enter one.
-
**External IPv4 address**: Select **Ephemeral** to assign an external IP address from a shared pool. Alternatively, you can use a reserved static external IP address. To learn more about network interface IP address allocation, refer to the [Google Cloud documentation](https://cloud.google.com/vpc/docs/create-use-multiple-interfaces).
[See image.](#img-add-network-interfaces)
- Click **Done**.
-
Click **Add a Network Interface** and add the second network interface, configuring the network (e.g., nss-test2), subnetwork, and internal and external IP addresses for the service interface.
After creating the network interfaces, the management interface is assigned to `vtnet0` and the service interface is assigned to `vtnet1`, as shown in the configuration file in the [subsequent step](/unified/nss-deployment-guide-google-cloud-platform#verify-network-interfaces).
- Click **Create** and wait for the VM instance to be provisioned.
[]To configure and start the NSS on the VM instance:
- [a. Configure and start the NSS on the VM instance.](#configure-start-nss)
- [b. Verify the NSS configuration.](#verify-nss-configuration)
- []Go to the newly created VM instance (**Compute Engine** > **VM Instances**) and connect via SSH or the [Serial Console](https://cloud.google.com/compute/docs/troubleshooting/troubleshooting-using-serial-console), if connecting to serial ports is enabled.
- When prompted, enter the username and password (e.g., `zsroot `/ `zsroot`).
- Copy the downloaded SSL certificate to the VM instance.
-
Run the following command to install the SSL certificate:
nss install-cert <certificate>
Replace the parameter in red with the SSL certificate file name (e.g.,
`NssCertificate.zip`) if you are in the path of the file. If not, use the file path (e.g., `/usr/home/zsroot/NssCertificate.zip`).
The NSS uses the SSL certificate to authenticate itself to the Zscaler service. Ensure that the SSL certificate is installed on only one active VM at a time. Having multiple VMs that use only one certificate causes cloud connection flapping, which disrupts log streaming.
-
Run the following command to configure the NSS:
sudo nss configure
-
When prompted, enter the following IP addresses:
- Nameserver IP address
- Internal service IP address associated with the service interface
- Default gateway for the internal service IP address
The following configuration is an example. Replace the values in red with the IP addresses for your deployment:
[root@nss /usr/home/zsroot]# nss dump-config
Configured Values:
CloudName:zscalerthree.net
nameserver:169.254.169.254
Mgmt IP:
Default gateway for Mgmt IP:
Internal Mgmt IP:
route_net:
Service IP Address:/dev/tap0:192.168.4.13/24
Default gateway for Service IP:192.168.4.1
Routes for Siem N/w:
-
Before starting the NSS, run the following command to download and install the NSS binaries:
`sudo nss update-now`
After the first NSS software deployment, the software is automatically updated with new versions.
-
Run the following command to start the NSS:
sudo nss start
The NSS starts within a few minutes.
[]To verify the NSS configuration, run the following command:
sudo nss troubleshoot netstat | less
The output of the command shows the following TCP connections:
- **Connection to the Zscaler cloud on port 443**: This is the control connection that is used to authenticate the NSS to the Zscaler Central Authority (CA) and to download the configuration. It is also the data connection to the Zscaler Nanolog so that it can stream the logs.
- **Connection to the SIEM**: This is the long-lived TCP connection to the SIEM on the specified log data port (e.g., 192.168.0.3.34561). If there are multiple feeds configured, then multiple connections must be listed.
The following image shows a sample output verifying the TCP connections are established:
[See image.](#img-verified-nss-configuration)
Troubleshooting
If the NSS does not start, open the `/etc/rc.conf` file to verify the following configuration:
#configurable per-machine info goes here (vtnet0 is mgmt and vtnet1 is service int)
network_interfaces="lo0 vtnet0 vtnet1"
ifconfig_vtnet0="UP"
ifconfig_vtnet0="DHCP"
ifconfig_vtnet0="SYNCDHCP mtu 1460"
The configuration confirms that there are two network interfaces (i.e., management and service), and that the management interface (i.e., `vtnet0`) is working as expected. If the configuration is not present in `/etc/rc.conf`, add it to the file and save, and then run the following command to restart the service:
/etc/rc.d/netif restart
If the NSS connection with the Zscaler CA fluctuates (i.e., it is established and then disconnects), run the following command:
ifconfig vtnet1 -rxcsum -txcsum -rxcsum6 -txcsum6 -tso4
If the NSS connection with the SIEM is not established:
-
Add `smnet_route` in the `/sc/conf/sc.conf` file, replacing the following parameters shown in red with the values for your deployment.
smnet_route=<SIEM IP Address>/32/<SIEM Gateway IP Address>
The following is an example: `smnet_route=``192.168.0.2``/32/``192.168.4.1`
-
Run the following command to restart the NSS service:
sudo nss restart
Zscaler recommends adding a custom route in the `sc.conf `file if your downstream SIEM IP address is in the same subnet.
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
[]An [NSS server](/unified/adding-nss-servers) represents the NSS virtual machine (VM) in the Admin Portal. When you create an NSS server in the portal, an SSL certificate is generated. You download the SSL certificate from the portal and upload it to the NSS VM that you configure and [deploy](/unified/deploying-nss-virtual-appliances). The newly configured NSS VM uses the SSL certificate to authenticate itself to the Zscaler service.
Each NSS server supports up to 16 [NSS feeds](/unified/adding-nss-feeds). ([Web](/unified/adding-nss-feeds-web-logs) and [Firewall](/unifieda/adding-nss-feeds-firewall-logs) logs are each limited to 8 feeds per NSS to ensure optimal performance.) Each NSS feed can have different filters and fields and a different output format (e.g., CSV).
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
![Upload files to Google Cloud Storage bucket](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/bucket-upload-file.png)
[]![gsutil URL of TSV file in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/object-details-gsutil-URI.png)
[]
![Transfer data into Cloud Storage bucket](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/bucket-transfer-data-in.png)
[]
![Source type URL list](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/source-type-destination-type.png)
[]
![URL of TSV file](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/choose-source-TSV-file-URL.png)
[]
![Path of destination Cloud Storage bucket](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/choose-destination-bucket-path.png)
[]
![Run transfer job once in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/run-job-once-starting-now.png)
[]![Create a transfer job in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-transfer-job.png)
[]
![Transfer job status in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/transfer-job-status.png)
[]![Transfer job success in Storage Transfer ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/storage-transfer-operations-job-success.png)
[]
![NSS VMDK file in Google Cloud Storage bucket](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/bucket-NSS-VDMK-file.png)
[]
![New Image Import in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-image-new-image-import.png)
[]
![Create an image in Google Cloud using new Image Import](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-image-new-image-import-config.png)
[]
![Manage target projects in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/target-project-manage-targets.png)
[]
![Add target projects in Migrate to Virtual Machines](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/migrate-virtual-machines-add-target-project.png)
[]
![Add target projects in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/add-target-projects.png)
[]
![Failed to create image with command in Google Cloud](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/image-creation-failure-command.png)
[]![Create a VPC network in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-vpc-network.png)
[]![Create a network firewall policy in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/configure-firewall-policy.png)
[]![Create a network firewall policy in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-firewall-rule.png)
[]![Create a network firewall policy in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/associate-vpc-networks.png)
[]![Create an instance in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-instance.png)
[]![Create an instance in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-instance-machine-configuration.png)
[]![Create an instance in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-instance-boot-disk.png)
[]![Create an instance in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/create-instance-network-performance-config.png)
[]![Add network interfaces in Google Cloud Platform](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/add-network-interface.png)
[]![Add NSS server ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/add-nss-server_0.png)
[]![Download SSL certificate from NSS server](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/download-ssl-certificate_0.png)
[]![Verified NSS connections to the Zscaler Central Authority and SIEM](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-deployment-guide-google-cloud-platform/nss-connections-established_0.jpg)