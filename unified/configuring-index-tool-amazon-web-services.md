# Configuring the Index Tool with Amazon Web Services
Source: https://help.zscaler.com/zia/configuring-index-tool-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1443226.pdf

Before you can create index templates for DLP dictionaries (i.e.,[ Exact Data Match (EDM)](/zia/about-exact-data-match) and [Indexed Document Match (IDM)](/zia/about-indexed-document-match) templates), you must configure the virtual machine (VM) image for the Index Tool with Amazon Web Services (AWS), Azure, or VMware.
To learn more about the VMware Index Tool, see [Configuring the Index Tool for Azure VMs](/zia/configuring-index-tool-azure-vms) and [Configuring the Index Tool with VMware](/zia/configuring-index-tool).
Since the Index Tool provides access to highly sensitive information, ensure that everyone who has access to it is authorized and authenticated.
**Deploying a Zscaler Index Tool VM with AWS**
To deploy a Zscaler Index Tool VM on Amazon Web Services:
- [1. Ensure that you meet all the requirements.](#step-1-requirements)
- [2. Request the Index Tool VM from Zscaler Support.](#step-2-request-index-tool)
- [3. Configure the Index tool VM.](#step-3-configure-index-tool-vm)
Updating and Customizing a Deployed Index Tool VM
With your Index Tool VM running, you can update and customize the VM based on your organization's needs.
- [Update the Index tool VM](#update-index-tool-vm)
- [Run the Index Tool VM in Explicit Proxy Mode](#run_the_Index_Tool_VM_in_Explicit_Proxy_Mode)
- [Configure the Index Tool Service to Run without Elevated Privileges](#configure-the-index-tool-to-run-without-elevated-privileges)
- [Enable Remote Access for Zscaler Support](#Enable-remote-access-for-zscaler-support)
Index Tool VM Commands
The following commands can be used to configure, update, and troubleshoot your VM:
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
[]To deploy the Zscaler Index Tool on an Azure VM:
- If your index templates include less than 300 million records, Zscaler recommends the following configuration:
- **Hypervisor**: AWS EC2
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 16 GB
- If your index templates include more than 300 million records, Zscaler recommends the following configuration:
- **Hypervisor**: AWS EC2
- **CPUs**: 4 CPUs. Zscaler requires 4 CPUs because the CPUs ensure that hash generation performance is not impacted.
- **RAM**: 64 GB
- You need a [Zscaler Index Tool](/zia/about-index-tool) added in the ZIA Admin Portal. You need this configuration to complete the VM setup.
[]Request the Index Tool VM from Zscaler Support
Before you can configure the Index Tool VM with AWS, you must contact Zscaler Support and request the Index Tool VM for your shared AWS account and region. Zscaler Support then provides you with the shared Index Tool VM information, Amazon Machine Image (AMI) ID and description to use when configuring the Index Tool with AWS.
Make note of the AMI ID and name that was shared with your account. You need this information when configuring the Index Tool VM with AWS.
[]Configure the Index Tool VM
- Make sure you have [added an Index Tool Configuration](/zia/adding-index-tool-configuration). You need this configuration to complete the VM setup.
- Log in to the AWS Management web UI or console.
- In the **AWS Management console**, click the **Services** icon at the top left of the page. The Services navigation menu is displayed.
[See image.](#services-navigation)
- Go to **Compute > EC2**. The **EC2 Management Console** appears.
[See image.](#Services-Navigation-Menu-Navigation-EC2-Console)
- Create a security group to be used in the configuration of the Index Tool VM:
- In another window, go to [config.zscaler.com](http://config.zscaler.com). The **Zscaler Config** page is displayed.
[See image.](#Zscaler-Config-Page)
- Select your organization's Zscaler cloud from the **Cloud** drop-down menu at the top left of the page.
- Go to **Zscaler Index Tool Requirements**. The **Zscaler Index Tool Requirements** page lists all of the outbound connections that need to be configured for the Zscaler Index Tool to communicate with the Zscaler cloud.
[See image.](#Zscaler-Index-Tool-Requirements-Page)
- Make note of all of the IPs that are listed in the different tables on this page because you need to add them to the security group.
- Return to the **EC2 Management Console**, and go to **Network & Security > Security Groups. **The **Security Groups** page is displayed.
[See image.](#Security-Groups-Page)
- On the **Security Groups** page, click **Create security group **in the top right of the page. The **Create security group** page is displayed.
[See image.](#Create-Security-Group-Page)
-
On the **Create security group **page:
- **Basic details: **Enter a name for the security group in the **Security Group Name** field.
- **Inbound rules:** Add only necessary incoming traffic IPs for the Index Tool VM. The Index Tool VM does not require an open port for internet traffic.
Since the Index Tool provides access to highly sensitive information, ensure that everyone who has access to it is authorized and authenticated.
- **Outbound Rules:** Add the outgoing traffic IPs that you gathered earlier from the **Zscaler Index Tool Requirements** page at [config.zscaler.com](http://config.zscaler.com).
- Click **Create security group **at the bottom right of the page.
- Launch an instance for the Index Tool VM:
- In the **EC2 Management Console**, go to **Instances > Instances.** The **Instances** page is displayed.
[See image.](#Instances-Page)
- On the **Instances page**, click **Launch instances** at the top right of the page. The **Launch an instance** page is displayed.
[See image.](#Launch-an-Instance-Page)
- (Optional) In the **Name and tags** section, enter a name for the Index Tool VM in the **Name** field.
[See image.](#Launch-an-Instance-Name-Tags)
-
In the **Application and OS Images (Amazon Machine Image)** section:
- Click the **My AMIs** tab.
- Select the **Shared with me** option.
- In the **Amazon Machine Image (AMI)** drop-down menu, select the AMI image that Zscaler Support shared with you. For example, Zscaler ADP/EDM 500GB (6.2r.46.331757).
[See image.](#amazon-machine-image-section)
- In the **Instance type** section, in the **Instance type** drop-down menu, select the appropriate instance type required for the Index Tool VM. The instance type depends on the total number of cells that you plan to use within the Index Tool VM. For example, if you plan to use less than 500 million cells, select the **t2.large** instance type,** t3.large** instance type, or something similar. If you plan to use more than 500 million cells, select the **t2.xlarge** instance type, **t3.xlarge** instance type or something similar.
[See image.](#instance-type-section)
- In the **Key pair (login)** section, in the **Key pair name** drop-down menu, select either your key pair name or the **Proceed without a key pair (Not recommended) **option.
[See image.](#key-pair-login-section)
-
In the **Network settings** section, under **Firewall (security groups)**:
- Select the **Select existing security group** option.
- In the **Security groups** drop-down menu, select the security group you previously created.
[See image.](#network-settings-section)
AWS automatically assigns the network IP address for the instance. You do not need to enter the IP address information unless it is required by your organization.
- Click **Launch instance **in the lower right of the page. A message is displayed stating that the launch of the instance was successfully initiated and it lists the instance ID that was created.
[See image.](#successful-instance-launch)
- Right-click the instance ID, and select **Open Link in New Tab**. The **Instances** page is displayed listing the instance with an **Instance state** of **Pending**. After a few seconds, the **Instance state** changes from **Pending** to **Running**.
[See image.](#view-pending-instance)
-
On the **Instances** page, click the **Instance ID**. The **Instance summary** page is displayed. On the **Instance summary** page, you can view the details for the instance, including the IP addresses that were assigned to the instance.
[See image.](#Instance-Summary-Page)
If you are using a public IP address, when you shut down and restart the instance, the IP address changes.
- On the **Instance summary** page, in the **Actions** drop-down menu, select **Monitor and troubleshoot **and then select **Get instance screenshot**. The **Get instance** **screenshot** page is displayed. After the instance is fully started, the page displays the initial root password for the VM instance. The initial root password for this user is randomly generated. Make note of the initial root password.
[See image.](#Get-Instance-Screenshot)
- Log in to the VM as user `zsroot` with the initial root password. Enter an SSH command to the IP address of the VM instance.
[See image.](#login-vm-instance)
-
Change the root password:
-
Enter the following command:
`sudo zadp change-password`
- Enter the initial root password, the one that was randomly generated for you.
- Enter a new root password.
- Re-enter the new root password.
[See image.](#change-vm-password)
After the password is changed, you need to log in to `zsroot` again using the new password.
- Return to the ZIA Admin Portal, and go to **Administration** > **Index Tool**.
- Locate the [Index Tool Configuration](/zia/about-index-tool) you added previously, and under the **SSL Certificate** column, click **Download**.
[See image.](#DownloadCert)
- Copy the SSL client certificate.zip file to the VM and install it:
-
In this example, scp is used to copy the file:
`scp `<SSL_certificate_zip_filename> zsroot@<vm_ip>:~/``
For example:
`scp EdmClientCertificate.zip zsroot@10.66.108.100:~/`
-
Enter the following command to install the SSL certificate:
`sudo zadp configure <SSL_certificate_zip_filename>`
For example: sudo zadp configure EdmClientCertificate.zip
- Enter the domain name that is used for the Index Tool's fully qualified domain name (FQDN). For example, if the Index Tool is reachable from `indextool.mycompany.com`, then the domain name entered here is `mycompany.com.`The self-signed certificate would be generated for `*.mycompany.com.`
[See image.](#VM_CLI5)
-
Enter a passphrase, then re-enter the passphrase to confirm it.
[See image.](#VM_CLI6)
-
You are prompted to enter the full path name to the text file where the passphrase is stored. You can also press `Enter` twice to accept the default location and file, `/home/zsroot/zscaler_zadp_webui_certificate_pass.txt`.
[See image.](#VM_CLI7)
If the service was configured properly, it:
- Checks if the network is configured correctly
- Installs the SSL client certificate you specified
- Generates a self-signed SSL server certificate. If you need to install a custom server certificate, see the next step.
- Downloads the latest install package
- (Optional) If you need to install a self-signed or custom SSL server certificate:
-
Enter the following command to install the server certificate:
`sudo zadp install-server-cert                               `
- Enter the full path to the PEM-formatted certificate file.
-
Enter the following command to restart the Index Tool service:
`sudo zadp restart`
- Go to https://<IP Address of the Index Tool VM> to access the Index Tool. After the Index Tool service has started, you can log in with your ZIA Admin Portal login credentials and create Index Templates to use when creating DLP dictionaries. To learn more, see [Creating an Exact Data Match Template](/zia/creating-exact-data-match-template) and [Creating an Indexed Document Match Template](/zia/creating-indexed-document-match-template).
[]
If you successfully configured the Index Tool, the service automatically downloads the latest install package before it starts. To manually update the service:
- Enter the following command to stop the service:
sudo zadp stop
- Enter the following command to install the update:
sudo zadp update-now
- Enter the following command to start the service:
sudo zadp start
[]You can run the tool in explicit proxy mode. To do this:
- Log in to the VM as user zsroot.
- Enter the following command:
sudo zadp configure-proxy
AWS manages network configuration, so you cannot directly configure the network from the Incident Receiver VM.
- For `Do you require a proxy server configuration?`, enter `y` and press `Enter`.
- For `proxyserver`, enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport`, enter your proxy port number (e.g., `9443`) and press `Enter`.
The VM then tests the connection and when this is successful, the configuration is complete.
To remove the explicit proxy configuration:
- Enter the following command:
`sudo zadp configure-proxy`
- For `Do you require proxy server configuration?`, enter `n` and press `Enter`.
- For `Do you want to delete current proxy configuration?`, enter `y` and press `Enter`.
Requirements for Explicit Proxy Mode
If you're using explicit proxy mode, DNS and NTP connections are not tunneled, meaning, you need an internal DNS server to run in this mode. The Index Tool needs to have DNS resolution for the current Master CA IP, update server, and the NTP server. The Index Tool host also must be able to query a DNS server to resolve the following settings:
- smcacluster.<cloudname>
- update1.<cloudname>
- update2.<cloudname>
- zdistribute.<cloudname>
- The NTP server. By default, the Index Tool VM has the following FQDNs for NTP servers configured:
- 0.freebsd.pool.ntp.org
- 1.freebsd.pool.ntp.org
- 2.freebsd.pool.ntp.org
You can override these FQDNs to your internal IP address in your DNS server configuration or using other methods.
In addition, since the proxy configuration doesn't allow authentication, you must configure the proxy server to allow specific IP/Mac addresses without user and password authentication.
The proxy server must also allow SSL bypass for communication from the VM to a specific set of IP addresses. These IPs are listed at config.zscaler.com/<cloudname>.net/edm. You can find your cloud name in the URL that your admins use to log in to the Zscaler service. For example, if an organization logs in to admin.zscalertwo.net, then that organization's cloud name is zscalertwo.** **So, you would go to config.zscaler.com/zscalertwo.net. To learn more, see [What is my cloud name for ZIA?](/zia/what-my-cloud-name-zia)
[]To configure the Index Tool service to run without elevated privileges:
- Log in to the VM as user `zsroot`.
- Enter the following command to stop the service:
sudo zadp stop
- Open the `/sc/conf/sc.conf` file and update the value for `zadp_ui_port` to a port number higher than 1,000.
- Enter the following command to restart the service:
sudo zadp start
[]
An admin can request remote assistance and allow Zscaler Support to log in to an Index Tool without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your Index Tool:
sudo zadp support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Index Tool.
- To disable Zscaler Support access to your Index Tool:
sudo zadp support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Index Tool:
sudo zadp support-access-status
[]![Viewing the Services navigation menu in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Services-Navigation-Menu.png)
[]![Navigating to the EC2 Management Console in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Services-Navigation-Menu-2.png)
![Viewing the EC2 Dashboard Page in the EC2 Management Console in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-EC2-Dashboard.png)
[]![Viewing the Zscaler Config Page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-Zscaler-Config-Page.png)
[]![Viewing the Zscaler Index Tool Requirements in the Zscaler Config page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-Zscaler-Config-Page-2.png)
[]![Viewing Security Groups on the Security Groups Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Security-Groups-Page.png)
[]![Create Security Groups Page](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Create-Security-Group-Page.png)
[]![Viewing instances in the Instances Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Instances-Page.png)
[]![Viewing the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launch-an-instance-Page.png)
[]![Entering a name for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-name-tags.png)
[]![Selecting an AMI Image for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-AMI.png)
[]![Selecting an instance type for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-Instance-Type.png)
[]![Selecting a key pair for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-Key-Pair.png?1674669285)
[]![Selecting the security group for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-network-settings.png)
[]![Viewing the success message after launching an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Launchaninstancepage-Success-Message.png?1673651389)
[]![Viewing a just launched instance on the Instances page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-Instances-Page-View-Instance.png?1673651220)
[]![Viewing Instance details on the Instance Summary Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-instance-summary-page.png)
[]![Viewing the Instance Screenshot for an instance in AWS](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-AWS-get-instance-screenshot-page.png?1673651680)
[]![Logging in to the AWS VM Instance](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-CLI-Login-VM-Instance.png?1673651781)
[]![Changing the VM Instance Password](/downloads/zia/policies/data-loss-prevention/dlp-index-tool/configuring-index-tool-amazon-web-services/ZIA-CLI-Change-Password.png?1673651894)
[]![The Download link for the Index Tool SSL Certificate in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/configuring-index-tool/ZIA-Download-Index-Tool-SSL-Certificate.png)
[]![zia-indextool-vm7.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm7.png)
[]![zia-indextool-vm8.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm8.png)
[]![zia-indextool-vm9.png](/downloads/zia/documentation-knowledgebase/creating-and-managing-policies/data-loss-prevention-dlp/configuring-dlp/configuring-index-tool/zia-indextool-vm9.png)