# NSS Collector Deployment Guide for VMware vSphere
Source: https://help.zscaler.com/zia/nss-collector-deployment-guide-vmware-vsphere
PDF: https://help.zscaler.com/pdf/com/en/1463366.pdf

The NSS Collector functionality and the data collected using this functionality are exclusive to [Shadow IT Report](/zia/about-shadow-it-report). To enable this feature for your organization, contact Zscaler Support.
This guide describes the tasks required to deploy [Nanolog Streaming Service (NSS) Collector](/zia/about-nss-collector-servers) to collect logs in real time from third-party security devices inside your network perimeter and stream them to the Zscaler cloud. Each step in the guide links you to the appropriate article for that configuration task on vSphere.
Prerequisites
Ensure you have a [subscription](/zia/viewing-subscriptions) to NSS Collector and review the following specifications and requirements:
- [VM Specs](#vm-specs)
- [Host Specs](#host-specs)
- [Network Specs](#network-specs)
- [Firewall Requirements](#fw-reqs)
- [User Provisioning](#user-provisioning)
Deploying NSS Collector
To deploy NSS Collector:
- [Step 1: Add an NSS Collector Server and Download the SSL Certificate in the ZIA Admin Portal](#step-nss-collector-server-configuration)
- [Step 2: Use the ESX/ESXi Server to Configure and Start the NSS Collector on the VM Instance](#step-deploy-start-nss-collector)
- [Step 3: Configure Third-Party syslog Feed for NSS Collector](#step-third-party-syslog-feed-configuration)
- []2 CPU cores: NSS Collector uses one core for the control plane and another core for the data plane.
- Instance memory:
- 8 GB for up to 15K users
- 16 GB for up to 40K users
- 32 GB for up to 100K users
- Data disk size: 500 GB
- []Hypervisor: VMware ESX/ESXi v5.0 and later
- Host CPU: 64-bit Xeon or equivalent
- Host CPU Speed: Greater than or equal to 2.40GHz
- VMware vSphere Client or vCenter
- []Network Adapter: E1000
- Network Specs:
- VM Network: 2 Virtual NICs. Optionally, you might need two additional virtual NICs.
- Bandwidth for log streaming: 11 Mbps for 10K users is an example average value.
- IP Addresses: The following table lists the IP addresses and the interfaces on which they're configured. Internal IP addresses are allowed. The management IP address and service IP address can be on different subnets, as long as the DNS server can be reached on both subnets.
| Virtual Interface | IP Address | Description |
| ----------------- | ---------- | ----------- |
| em0 (First network adapter) | Management IP Address | This is used for control connections to the Zscaler cloud and to make an SSH connection to the NSS Collector VM for configuration and management.You can customize the deployment and define a separate IP address for the SSH connection to the NSS Collector VM. |
| em1 (Second network adapter) | Service IP Address | This is used for data connections to the Zscaler cloud. |
[]It is mandatory to deploy the NSS Collector instance behind a VM network security group. The NSS Collector instance requires only outbound connections to the Zscaler cloud. It doesn't require any inbound connections to your network from the Zscaler cloud. To view the firewall requirements for your specific account, refer to the Zscaler Cloud Configuration Requirements for your Zscaler cloud: `https://config.zscaler.com/``<Zscaler Cloud Name>``/nss`.
You can find the name of your Zscaler cloud in the URL you use to log in to the Zscaler service. For example, if you log in to admin.zscaler.net, then go to [config.zscaler.com/zscaler.net/nss](https://config.zscaler.com/zscaler.net/nss). To learn more, see [What Is My Cloud Name for ZIA?](/zia/what-my-cloud-name-zia)
The IP ranges are necessary to ensure that the service isn't affected by future Zscaler cloud expansion.
Communication from the NSS Collector to the Zscaler cloud must be excluded from SSL inspection to ensure that the NSS Collector can authenticate to the Nanolog cluster using mutual TLS.
[]To leverage complete Shadow IT Report functionality, users whose traffic traversed through third-party vendor devices need to be provisioned through one of the mechanisms supported by Zscaler. To learn about user provisioning, see [Choosing Provisioning and Authentication Methods](/zia/choosing-provisioning-authentication-methods).
[]You can configure the [NSS Collector server](/zia/about-nss-collector-servers) in the ZIA Admin Portal to obtain the packaged software (VM image) that must be installed in your organization’s network perimeter. To learn more about NSS Collectors and their use in third-party log integration with Zscaler, see [Understanding Nanolog Streaming Service (NSS)](/zia/understanding-nanolog-streaming-service).
An organization can have up to 4 NSS Collector servers.
To add an NSS Collector server:
- Go to **Administration** > **Nanolog Streaming Service**.
- From the **NSS Collector Servers** tab, click **Add NSS Collector Server**.
- In the **Add NSS Collector Server** window:
- **Name**: Enter a name for the NSS Collector server.
- **Vendor**: Select the vendor of the third-party firewall or web proxy service used by your organization for which the logs must be integrated with Zscaler.
- **Status**: Select **Enabled** to allow the NSS Collector to process and stream logs from the third-party firewalls or web proxies to the Zscaler service. When disabled, the NSS Collector does not process or stream logs from third-party security solutions.
- Click **Save**.
[See image.](#add-nss-collector-server)
When the NSS Collector server is added to the ZIA Admin Portal, Zscaler generates the packaged software for installation and issues an SSL certificate to the server.
To download the packaged software and the SSL certificate for the server:
- Click the **Edit** icon displayed against the NSS Collector server.
- In the **Edit NSS Server** window:
- Under the **SSL Certificate** field, you can download the SSL Certificate issued for the NSS Collector server. You can also regenerate a new certificate for the server as required. The SSL certificate must be installed on the NSS Collector VM so that the NSS Collector can authenticate as a client with the Zscaler service.
- Under the **Software** field, you can download the packaged software generated for the server for installation.
[See image.](#edit-nss-collector-server)
You can also download the SSL certificate directly from the NSS Collector Servers table by clicking the **Download** button against the required NSS Collector server under the **SSL Certificate** column.
[See image.](#ssl-certificate-download)
[]Before you configure and start the NSS Collector on the vSphere client, ensure that you have downloaded the NSS Collector OVA file and SSL certificate from the ZIA Admin Portal, as explained in [Step 1](#step-nss-collector-server-configuration) in the guide.
To configure the NSS Collector virtual appliance on the VM, log in to the vSphere client and perform the following actions:
- [a. Import the NSS Collector OVA file.](#import-nss-collector-ova-file)
- [b. Configure the network.](#configure-network)
- [c. Configure the NSS Collector.](#configure-nss-collector)
- [d. Install the SSL certificate.](#install-ssl-certificate)
- [e. Download the NSS Collector binaries.](#download-nss-collector-binaries)
- [f. Start the NSS Collector.](#start-nss-collector)
[]Go to **File** > **Deploy OVF Template** and use the Deploy OVF Template wizard to deploy the NSS Collector VM.
[]
- Select the NSS Collector VM and either click the **Power On** button or power on the virtual machine.
- On the **Console** tab, log in to the ZscalerOS command prompt with the following credentials:
- Username: `zsroot`
- Password: `zsroot`
By default, root login is not permitted. Administrators must use the utility sudo to run a command with higher privileges.
Zscaler strongly recommends that you change this default password by running the command `passwd`. For more details about running this command, [click here.](#password-change)
- Enter the command `sudo nss configure` and complete the following:
- Enter the DNS server IP address (e.g., `192.168.1.1`).
- Enter the management interface IP with CIDR netmask. Use the management IP address for SSH or FTP (e.g., `192.168.3.1/16`).
- Enter the default gateway for the management IP address (e.g., `192.168.1.1`).
- Enter the service IP address with CIDR netmask (e.g., `192.168.3.2/16`). NSS Collector uses the service IP address to communicate with the Zscaler cloud and with the SIEM.
- Enter the default gateway for the service IP address (e.g., `192.168.1.1`).
The management IP address and service IP address can be on different subnets, as long as the DNS server can be reached on both subnets.
[See image.](#vSphere-nss-configure-command-prompt)
- Check the applied network configuration by running the following command:
sudo nss dump-config
- []To change the password, enter `passwd` and your username. For example, if you are using the default username, the command is:
passwd zsroot
- When prompted, specify the following:
- Your current password
- Your new password
![FreeBSD Command Prompt Password](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-collector-deployment-guide-vmware-vsphere/freebsd_command_prompt_password_screenshot.png)
[]Enter the command `sudo nss collector-configure` and then enter the third-party log vendor name (`PANFW`, `FORTIFW`, or `BLUECOAT`).
[]The NSS Collector uses this certificate to authenticate itself to the Zscaler service. Ensure that the SSL certificate is installed on only one active NSS Collector VM at a time. Having multiple NSS Collector VMs that use the same certificate causes cloud connection flapping, which would disrupt the streaming of logs to the Zscaler cloud.
- Navigate to the SSL certificate that you saved.
- Use FTP, SCP, or SFTP to upload it to the management IP address of the NSS Collector.
- On the vSphere client, click the **Console** tab, and log in with the following credentials:
- Username: `zsroot`
- Password: `zsroot`
- Go to the **Console** tab or use SSH to connect to the management IP address.
- Run the following command:
sudo nss install-cert
Specify the path to the uploaded certificate bundle.
- Check the configuration by running the following command:
sudo nss dump-config
[]Before starting the NSS Collector:
- On the vSphere client, click the **Console** tab or use SSH to connect to the management IP address.
- Run the following command to download and install the NSS Collector binaries:
sudo nss update-now
After the first NSS Collector software deployment, the software is automatically updated with new versions.
[]
- On the vSphere client, click the **Console** tab or use SSH to connect to the management IP address.
- Run the following command:
sudo nss start
Ensure that the command shows that the NSS Collector started successfully. It can take a few minutes for the NSS Collector to start collecting logs and sending them to the Zscaler cloud.
After starting the NSS Collector for the first time, you can run the following command to check that the latest NSS Collector software version is installed:
sudo nss checkversion
To enable the NSS Collector to start automatically after a restart, run the following command:
sudo nss enable-autostart
You can also explore other options by running the following command:
sudo nss help
[]The following configuration steps pertain to Palo Alto Networks and they provide information on how to configure a syslog feed for the NSS Collector to collect traffic logs of clients behind the Palo Alto Networks firewall.
The configuration steps cover the minimum information required in each step and use examples where necessary. For details on all of the configuration fields, refer to the [Palo Alto Networks documentation](https://docs.paloaltonetworks.com/).
- [a. Configure Syslog Server Profile](#PAN-configure-syslog-server-profile)
- [b. Configure Log Forwarding Profile](#PAN-configure-log-forwarding-profile)
- [c. Configure a Security Policy to Allow User Traffic and Enable Logging](#PAN-configure-security-policy)
- [d. Configure User Authentication by Enabling Captive Portal](#PAN-configure-captive-portal-settings)
- []Log in to the Palo Alto Networks firewall via the web interface.
- Go to the **Devices** tab, click the **Server Profiles** drop-down menu in the left-side navigation, and select **Syslog**.
- Click **Add** and provide the following information in the window that appears:
- **Name**: Enter a name for the syslog server profile.
-
On the **Servers** tab, click **Add**, and fill out the following information:
- **Name**: Enter a name for the syslog server.
- **Server**: Enter the IP address of the syslog server (i.e., NSS Collector server) deployed for your organization on the Zscaler cloud. This information can be obtained from the [SSL certificate generated and downloaded for the NSS Collector server](#step2-nss-collector-server-configuration) that is configured in the ZIA Admin Portal.
- **Transport**: Select **TCP** as the transport protocol for your syslog messages.
- **Port**: Specify the port number of the syslog server. Default and custom ports are supported.
- **Format**: Select IETF as the syslog format.
- **Facility**: Select **LOG_USER** from the drop-down menu to log user-based traffic.
[See image.](#PAN-syslog-server-profile)
-
On the **Custom Log Format** tab, click **Log Type** to specify a custom log format. In the window that appears, click the **Traffic** field and enter the following string, and click **OK** to save the value:
`CEF:0|Palo Alto Networks|PAN-OS|$sender_sw_version|$subtype|$type|1|rt=$cef-formatted-receive_time deviceExternalId=$serial src=$src dst=$dst suser=$srcuser app=$app spt=$sport proto=$proto act=$action in=$bytes_sent out=$bytes_received start=$cef-formatted-time_generated reason=$session_end_reason`
[See image.](#PAN-custom-log-format-syslog-server-profile)
- Click **OK** to save the settings.
- []Go to the **Objects** tab, click **Log Forwarding** in the left-side navigation, and click **Add** to create a log forwarding profile.
- In the window that appears, enter a name and description for the profile.
-
Click **Add** to add a match list profile and fill out the following details:
- **Name**: Enter a name for the match list profile.
- **Log Type**: Select **traffic** from the drop-down menu.
- **Filter**: Select **All Logs** from the drop-down menu.
- **Forward Method**: Click **Add** and select the syslog server profile configured in the previous step from the list displayed.
[See image.](#PAN-log-forwarding-profile)
- Click **OK** to save the log forwarding profile.
-
[]Go to the **Policies** tab, click **Security** on the left-side navigation, and click **Add**.
Alternatively, you can modify an existing security policy to include the traffic log forwarding configurations.
- On the **General** tab, enter a name for the rule.
-
Configure the rule criteria under the respective tabs as necessary. The rule must be configured to allow traffic coming from the trust zone (LAN) under the **Source** tab to reach the untrust zone (WAN) under the **Destination** tab.
[See image.](#PAN-security-policy-conditions)
-
On the **Actions** tab:
- Under **Action Setting**, select **Allow** for Action.
- Under **Log Setting**:
- Enable **Log at Session Start** and **Log at Session End** options.
- From the **Log Forwarding** drop-down menu, select the log forwarding profile configured in the previous step.
[See image.](#PAN-security-policy-action)
- Click **OK** to save the security policy.
[]The traffic log data forwarded by Palo Alto Networks firewall is processed by Zscaler and made available for analysis in the [Shadow IT Report](/zia/about-shadow-it-report) in the ZIA Admin Portal. The Shadow IT Report provides analytics for the entire organization, as well as on a per user basis. To facilitate report generation on a per user basis, the identity of users must be verified by Palo Alto Networks firewall and logs must be recorded for the user-based traffic. To do this, you need to add the ZIA users to the Palo Alto Networks firewall and configure an authentication mechanism for the users. When the NSS Collector server receives the log data, it matches the user information with the ZIA users and then forwards the logs pertaining to ZIA users to Zscaler for processing.
The following sections provide step-by-step instructions for this configuration:
This configuration uses a captive portal as the authentication mechanism. However, you can use other Palo Alto Networks firewall-supported authentication mechanisms per your deployment. To learn more, refer to the [Palo Alto Networks documentation](https://docs.paloaltonetworks.com/).
- [i. Create an Interface Management Profile](#PAN-create-interface-management-profile)
- [ii. Map the Interface Management Profile with the Client-Side LAN Interface](#PAN-configure-client-LAN-interface)
- [iii. Add Users for the Captive Portal and Map Them to an Authentication Profile](#PAN-configure-authentication-profile)
- [iv. Enable Captive Portal](#PAN-enable-captive-portal)
- []Go to the **Network** tab, click the **Network Profiles** drop-down menu in the left-side navigation, and select **Interface Mgmt**.
- Click **Add** to create an Interface Management profile.
- Enter a name for the profile.
-
Under **Permitted Services**, select **Response Pages** and **User-ID** and any other necessary permitted services. These services are required for enabling captive portal authentication on the trust interface.
[See image.](#PAN-interface-management-profile)
- Click **OK** to save the Interface Management profile.
- []Go to the **Network** tab, click **Interfaces**, and then click **Ethernet**.
- Locate the client-side LAN interface that is typically configured for your environment in the Palo Alto Networks firewall. Click the ethernet interface to modify its settings and map the Interface Management profile configured in the previous step.
-
In the window that appears, go to the **Advanced** tab, and select the Interface Management profile configured in the previous step using the **Management Profile** drop-down menu.
[See image.](#PAN-ethernet-interface-configuration)
-
Click **OK** to save the configuration. The following image shows an example configuration of the client-side LAN interface.
[See image.](#PAN-ethernet-configurations)
- []Go to the **Device** tab, click the **Local User Database** drop-down menu in the left-side navigation, and then select **Users**.
-
Click **Add** displayed at the bottom-left corner of the page and fill out the user information in the window that appears:
The username and password information in the Palo Alto Networks firewall must match the user details configured in the ZIA Admin Portal.
- **Name**: Enter the username.
- **Mode**: Select Password as the mode.
- **Password**: Enter the user's login password.
- **Confirm Password**: Re-enter the user's login password.
- Select **Enable**.
[See image.](#PAN-local-user-configuration)
- Click **OK** to save the configuration.
- On the **Device** tab, click **Authentication Profile** in the left-side navigation, and click **Add**.
-
Fill out the following information in the authentication profile:
- **Name**: Enter a name for the profile.
- On the **Authentication** tab:
- Select **Type** as **Local Database** using the drop-down menu. Local Database authentication type corresponds to the captive portal authentication mechanism used in this example configuration. You can select the authentication type depending on the authentication mechanism used in your firewall deployment.
-
Optionally, you can select the **Username Modifier** using the drop-down menu to restrict the format in which users must enter their username in the authentication portal served by the Palo Alto Networks firewall.
[See image.](#PAN-authentication-profile-configuration)
-
On the **Advanced** tab, click **Add**, and select the list of users configured earlier.
[See image.](#PAN-authentication-profile-user-mapping)
- Click **OK** to save the configuration.
The following image shows an example authentication profile configuration:
[See image.](#PAN-authentication-profile)
- []On the **Device** tab, click **User Identification** in the left-side navigation, and go to the **Captive Portal Settings** tab.
-
Click the **Settings** icon on the top-right to make modifications.
[See image.](#PAN-captive-portal-settings-icon)
-
In the window that appears, select **Enable Captive Portal** and enter the necessary information, such as:
- **Authentication Profile**: Select the authentication profile configured in the previous step using the drop-down menu.
- **Mode**: Select the **Redirect** checkbox to allow the firewall to intercept web requests that match the authentication profile and redirect them to the specified redirect host.
- **Redirect Host**: Enter the IP address of the Palo Alto Networks firewall trust interface to which the client must be redirected for authentication.
[See image.](#PAN-captive-portal-settings)
- Click **OK** to save the configuration.
[]![A screenshot of the Add NSS Collector Server window](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/add-nss-collector.png)
[]![A screenshot of the Edit NSS Collector Server window](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/edit-nss-collector.png)
[]![vSphere NSS Configure Command Prompt](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-collector-deployment-guide-vmware-vsphere/vsphere_nss_configure_command_prompt_screenshot.png)
[]![A screenshot of the  SSL certificate download option for NSS Collector server ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-collector-deployment-guide-vmware-vsphere/nss-collector-ssl-certificate-download.png)
[]![Palo Alto Networks Firewall Syslog Server Profile Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-syslog-server-profile-servers-tab.png)
[]![Custom log format for PAN syslog server profile](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-syslog-server-profile-custom-log-format-tab.png)
[]![Palo Alto Networks Firewall Log Forwarding Profile Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-log-forwarding-profile.png)
[]![Palo Alto Networks Firewall Syslog Security Policy Action](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-security-policy-actions.png)
[]![Palo Alto Networks Firewall Security Policy Conditions](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-security-policy-conditions.png)
[]![Palo Alto Networks Firewall Interface Management Profile](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-interface-management-profile.png)
[]![Palo Alto Networks Firewall Ethernet Interface Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-ethernet-interface-advanced-tab.png)
[]![Palo Alto Networks Firewall Ethernet Interface Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-network-interfaces-ethernet.png)
[]![Palo Alto Networks Firewall Local User Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-local-user.png)
[]![Palo Alto Networks Firewall Authentication Profile Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-authentication-profile-authentication-tab.png)
[]![Palo Alto Networks Firewall Authentication Profile User Configuration](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-authentication-profile-advanced-tab.png)
[]![Palo Alto Networks Firewall Authentication Profile](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-authentication-profile.png)
[]![Palo Alto Networks Firewall Captive Portal Settings Icon](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-captive-portal-settings-icon.png)
[]![Palo Alto Networks Firewall Captive Portal Settings](/downloads/zia/nanolog-streaming-service/nss-collector-deployment-guide-vmware-vsphere/pan-captive-portal-settings.png)