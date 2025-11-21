# Configuring the Index Tool with VMWare
Source: https://help.zscaler.com/zia/configuring-index-tool-vmware
PDF: https://help.zscaler.com/pdf/com/en/1400651.pdf

New or clean deployment of Index Tool requires VM image running on Zscaler OS version 24.
Before you can create index templates for DLP dictionaries (i.e.,[ Exact Data Match (EDM)](/zia/about-exact-data-match) and [Indexed Document Match (IDM)](/zia/about-indexed-document-match) templates), you must install and configure the virtual machine (VM) image for the Index Tool with Amazon Web Services (AWS), Azure, or VMware.
To learn more about the AWS Index Tool, see [Configuring the Index Tool with Amazon Web Services](/zia/configuring-index-tool-amazon-web-services) and [Configuring the Index Tool for Azure VMs](/zia/configuring-index-tool-azure-vms).
Since the Index Tool provides access to highly sensitive information, ensure that everyone who has access to it is authorized and authenticated.
Deploying a Zscaler Index Tool with VMware
To deploy a Zscaler Index Tool VM with VMware:
- [1. Ensure that you meet all the requirements.](#step-1-requirements)
- [2. Download the Index Tool VM](#download-the-index-tool-VM)
- [3. Configure the Index Tool VM](#configure-the-index-tool-VM)
Updating and Customizing a Deployed Index Tool VM
With your Index Tool VM running, you can update and customize the VM based on your organization's needs.
- [Update the Index Tool VM](#update-the-index-tool-vm)
- [Run the Index Tool VM in Explicit Proxy Mode](#explicit-proxy-mode)
- [Configure the Index Tool Service to Run without Elevated Privileges](#configure-index-tool-without-elevated-privileges)
- [Enable Remote Access for Zscaler Support](#enable-remote-access-for-zscaler-support)
Index Tool VM Commands
The following commands can be used to configure, update, and troubleshoot your VM.
| **Command** | **Description** |
| ----------- | --------------- |
| `sudo zadp stop` | Stops the Zscaler Index Tool service. |
| `sudo zadp start` | Starts the Zscaler Index Tool service. |
| `sudo zadp update-now` | Updates the Zscaler Index Tool service. The service must be stopped before you can run this command. |
| `sudo zadp restart` | Restarts the Zscaler Index Tool service. |
| `sudo zadp status` | Displays whether the Zscaler Index Tool service is running or stopped. |
| `sudo zadp force-update-now` | Forces the Zscaler Index Tool service to update to the latest version regardless of what version is on the VM. The service is automatically stopped before the update begins. |
| `sudo zadp troubleshoot` | Runs a series of checks to help troubleshoot issues, such as checking the installed certificate, the zcloud server configuration, all services, and whether or not an update is needed. |
| `sudo zadp collect-diagnostics` | Creates a file with diagnostic information to send to Zscaler Support for troubleshooting purposes. |
| `sudo zadp configure-syslog-server` | Configures external syslog server forwarding on the Zscaler Index Tool to forward file SFTP events and to log any critical changes to the configuration files monitored by the Index Tool. The external syslog server forwarding happens over UDP port 514, which cannot be modified. |
[]To deploy the Zscaler Index Tool on VMware:
- If your index templates include less than 300 million records, Zscaler recommends the following configuration:
- **Hypervisor**: VMware ESX/ESXi version 6.0 or later.
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 16 GB
- **Disk**: 600 GB
- **VM Network**: 1 Virtual NIC
- If your index templates include more than 300 million records, Zscaler recommends the following configuration:
- **Hypervisor**: VMware ESX/ESXi version 6.0 or later.
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 64 GB
- **Disk**: 1 TB
- **VM Network**: 1 Virtual NIC
- A [Zscaler Index Tool](/zia/about-index-tool) added in the ZIA Admin Portal. You need this configuration to complete the VM setup.
[]Before you configure the Index Tool VM, you must download it.
If your index templates include less than 300 million records, you can download the Index Tool VM image from the ZIA Admin Portal. To download the Index Tool VM:
- Go to **Administration **> **Index Tool**.
- Click **Download Index Tool**.
[See image.](#DownloadIndexTool)
[]To configure the Index Tool VM:
- Make sure you have [added an Index Tool Configuration](/zia/adding-index-tool-configuration). You need this configuration to complete the VM setup.
- In ESX/ESXi, install the Index Tool VM image you downloaded previously.
- Log in to the VM as user zsroot. The initial root password for this user is randomly generated.
[See image.](#VM_CLI1)
-
Change the root password:
-
Enter the following command:
`sudo zadp change-password`
- Enter the initial root password, the one that was randomly generated for you.
[See image.](#VM_CLI2)
- Enter a new root password.
[See image.](#VM_CLI3)
- Re-enter the new root password.
After the password is changed, you need to log in to `zsroot` again using the new password.
- (Optional) By default, the VM starts using DHCP to obtain the IP address and default router information. If there's no DHCP server available, you can configure this manually:
-
Enter the following command:
`sudo zadp configure-network`
- For nameserver, enter c to change the IP address and press `Enter`.
- Enter the IP address and press `Enter`.
- If you want to add a new nameserver enter y, otherwise enter n, and press `Enter`.
The VM restarts the network and checks the connection.
[See image.](#VM_CLI4)
- Go back to the ZIA Admin Portal, and go to **Administration **> **Index Tool**.
- Locate the [Index Tool Configuration](/zia/about-index-tool) you added previously, and under the **SSL Certificate** column, click **Download**.
[See image.](#DownloadCert)
- Copy over the SSL client certificate.zip file to the VM and install it:
-
In this example, we're using scp to copy over the file:
`scp <SSL_certificate_zip_filename> zsroot@<vm_ip>:~/`
For example: `scp EdmClientCertificate.zip zsroo@10.66.108.100:~/`
-
Enter the following command to install the SSL certificate:
`sudo zadp configure <SSL_certificate_zip_filename>`
For example: `sudo zadp configure EdmClientCertificate.zip`
- Enter the domain namethat is used for the Index Tool's fully qualified domain name (FQDN). For example, if the Index Tool is reachable from `indextool.mycompany.com`, then the domain name entered here would be `mycompany.com`. The self-signed certificate would be generated for `*.mycompany.com`.
[See image.](#VM_CLI5)
- Enter a passphrase, then re-enter the passphrase to confirm it.
[See image.](#VM_CLI6)
-
You are prompted to enter the full path name to the text file where the passphrase is stored. You can also press `Enter` twice to accept the default location and file, `/home/zsroot/zscaler_zadp_webui_certificate_pass.txt`.
[See image.](#VM_CLI7)
If the service was configured properly, the service:
- Checks if the network is configured correctly.
- Installs the SSL client certificate you specified.
- Generates a self-signed SSL server certificate. If you need to install a custom server certificate, see the next step.
- Downloads the latest install package.
- (Optional) If you need to install a self-signed or custom SSL server certificate:
-
Enter the following command to install the server certificate:
`sudo zadp install-server-cert`
- Enter the full path to the PEM formatted certificate file.
-
Enter the following command to restart the Index Tool service:
`sudo zadp restart`
Go to https://<IP Address of the Index Tool VM> to access the Index Tool. After the Index Tool service has started, you can log in with your ZIA Admin Portal login credentials and create Index Templates to use when creating DLP dictionaries. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template) and [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template).
[]
If you successfully configured the Index Tool, the service automatically downloads the latest install package before it starts.
To manually update the service:
-
Enter the following command to stop the service:
`sudo zadp stop`
-
Enter the following command to install the update:
`sudo zadp update-now`
-
Enter the following command to start the service:
`sudo zadp start`
[]Run the Index Tool VM in Explicit Proxy Mode
- Log in to the VM as user `zsroot`.
- Enter the following command:
sudo zadp configure-network
- For `Do you require a proxy server configuration?`, enter `y` and press `Enter`.
- For `proxyserver`, enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport`, enter your proxy port number (e.g., `9443`) and press `Enter`.
The VM then tests the connection and when this is successful, the configuration is complete.
To remove the explicit proxy configuration:
-
Enter the following command:
`sudo zadp configure-network`
- For `Do you require proxy server configuration?`, enter n and press `Enter`.
- For `Do you want to delete current proxy configuration?`, enter y and press `Enter`.
Requirements for Explicit Proxy Mode
If you're using explicit proxy mode, DNS and NTP connections are not tunneled, meaning, you need an internal DNS server to run in this mode. The Index Tool needs to have DNS resolution for the current Master CA IP, update server, and the NTP server. The Index Tool host also needs to be able to query a DNS server to resolve the following settings:
- smcacluster.<Zscaler cloud Name>
- update1.<Zscaler cloud Name>
- update2.<Zscaler cloud Name>
- zdistribute.<Zscaler cloud Name>
- The NTP server. By default, the Index Tool VM has the following FQDNs for NTP servers configured:
- 0.freebsd.pool.ntp.org
- 1.freebsd.pool.ntp.org
- 2.freebsd.pool.ntp.org
You can override these FQDNs to your internal IP address in your DNS server configuration or using other methods.
In addition, since the proxy configuration doesn't allow authentication, you need to configure the proxy server to allow specific IP/MAC addresses without user and password authentication.
The proxy server must also allow SSL bypass for communication from the VM to a specific set of IP addresses. These IPs are listed at config.zscaler.com/<Zscaler cloud Name>.net/edm. You can find your cloud name in the URL that your admins use to log in to the Zscaler service. For example, if an organization logs in to admin.zscalertwo.net, then that organization's cloud name is zscalertwo.** **So, you would go to config.zscaler.com/zscalertwo.net. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
[]
To configure the Index Tool service to run without elevated privileges:
- Log in to the VM as user `zsroot`.
- Enter the following command to stop the service:
sudo zadp stop
- Open the `/sc/conf/sc.conf` file and update the value for `zadp_ui_port` to a port number higher than 1,000.
- Enter the following command to restart the service:
sudo zadp start
[]An admin can request remote assistance and allow Zscaler Support to log in to an Index Tool without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your Index Tool:
sudo zadp support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Index Tool.
- To disable Zscaler Support access to your Index Tool:
sudo zadp support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Index Tool:
sudo zadp support-access-status
[]![The Download Index Tool link in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/configuring-index-tool/ZIA-Download-Index-Tool.png)
[]![zia-indextool-vm2.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm2.png)
[]![zia-indextool-vm4.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm4.png)
[]![zia-indextool-vm5.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm5.png)
[]![zia-indextool-vm6.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm6.png)
[]![The Download link for the Index Tool SSL Certificate in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/configuring-index-tool/ZIA-Download-Index-Tool-SSL-Certificate.png)
[]![zia-indextool-vm7.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm7.png)
[]![zia-indextool-vm8.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm8.png)
[]![zia-indextool-vm9.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm9.png)