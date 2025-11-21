# Configuring the Zscaler Incident Receiver for On-Premises VMs
Source: https://help.zscaler.com/unified/configuring-zscaler-incident-receiver-premises-vms
PDF: https://help.zscaler.com/pdf/com/en/1493366.pdf

New or clean deployment of Zscaler Incident Receiver requires a virtual machine (VM) image running on Zscaler OS version 24.
Before you can use a [Zscaler Incident Receiver](/unified/about-zscaler-incident-receiver), you must configure the VM image for the Incident Receiver either on an on-premises VM, on an Amazon Web Services (AWS) EC2 instance, or on an Azure VM.
To learn more, see [Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs](/unified/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms) and [Configuring the Zscaler Incident Receiver for Azure VMs](/unified/configuring-zscaler-incident-receiver-azure-vms).
Deploying a Zscaler Incident Receiver VM on an On-Premises VM
To deploy a Zscaler Incident Receiver VM on an on-premises VM:
- [1. Ensure You Meet the Requirements.](#step-1-requirements)
- [2. Download the Zscaler Incident Receiver VM.](#step-2-download-ir-vm)
- [3. Configure the Zscaler Incident Receiver VM.](#step-3-configure-ir-vm)
Updating and Customizing a Deployed Zscaler Incident Receiver VM
With your Incident Receiver VM running, you can update and customize the VM based on your organization's needs.
- [Update the Incident Receiver VM](#update-incident-receiver)
- [Run the Incident Receiver VM in Explicit Proxy Mode](#explicit-proxy)
- [Run the Incident Receiver VM With Mutual Transport Security Enabled](#mutual-transport-security)
- [Configuring the Zscaler Incident Receiver VM to Allow Multiple SFTP Connections](#multiple-sftp-connections)
- [Enabling Remote Access for Zscaler Support](#enable-remote-access)
- [Upgrade SSH Key to ED25519](#migrate-rsa-key)
- [Install a New Server Certificate](#install-new-cert)
Zscaler Incident Receiver Commands
You can use the following commands to configure, update, and troubleshoot your VM.
- [Zscaler Incident Receiver Commands](#incident-receiver-commands)
[]To deploy the Zscaler Incident Receiver, you need:
-
Access to one of the following types of storage servers where the Incident Receiver can store files:
- A storage server that supports SFTP/SCP and public key authentication. You must also have a preconfigured account that allows write access to the server’s intended directory.
- An Amazon S3 storage bucket where the Incident Receiver can store data.
Zscaler recommends using an SFTP storage server to store data for on-premises Incident Receiver VMs. To use an S3 storage bucket with an on-premises VM, you must set up an S3 credentials file on the VM where the Incident Receiver resides. For this method, manually create a `/root/.aws/credentials` file and a `/home/zsroot/.aws/credentials` file with the proper `aws_access_key_id` and `aws_secret_access_key` on the VM. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html).
- A static public IP address for the Incident Receiver VM. Additionally, you need a firewall rule configured to allow inbound ICAP messages from the FCC cloud to the correct TCP port on the Incident Receiver VM (e.g., port 1344).
- VM specifications:
- Hypervisor: VMware ESX/ESXi version 6.0 or later, Oracle VM VirtualBox
- CPUs: 4 CPUs
- RAM: 8 GB
- Disk: 600 GB
- VM Network: 1 Virtual NIC
- For Zscaler Incident Receiver to check your network connectivity and get access to and from your IP address, your firewalls must be enabled for the appropriate location. To understand the needed access requirements, see [DLP Incident Receiver Connections](https://config.zscaler.com/zscaler.net/dlp-incident-receiver).
- You must allow a direct IP-based connection to the Zscaler Hub IPs so the Incident Receiver can connect to the IP directly. To learn more, see [Zscaler Hub IP Addresses](https://config.zscaler.com/zscaler.net/hubs).
[]Before you configure the Zscaler Incident Receiver VM, you must download it.
To download the VM:
- In the Admin Portal, go to **Policies** > **Data Protection** > **Common Resources** > **DLP Incident Receiver**.
- Click the **Zscaler Incident Receiver** tab.
- Click **Download Incident Receiver**.
[See image.](#download-VM-image)
[]![Download the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/ZIA-Download-Incident-Receiver.png)
[]To configure the Incident Receiver VM:
- Make sure you have [added a Zscaler Incident Receiver](/unified/adding-zscaler-incident-receiver) in the Admin Portal. You need this configuration to complete the VM setup.
- In your hypervisor, install the Incident Receiver VM you downloaded previously.
-
Log in to the VM as user `zsroot`. The initial root password for this user is randomly generated.
[See image.](#initial-pass-image)
- Change the root password:
-
Enter the following command:
sudo zirsvr change-password
[See image.](#change-password-command-image)
- Enter the initial root password, the one that was randomly generated for you.
-
Enter a new root password.
[See image.](#new-root-pass-image)
- Re-enter the new root password.
- Configure the network:
-
Enter the following command:
sudo zirsvr configure-network
- For `nameserver`, enter `c` to change the IP address and press `Enter`.
- Enter the IP address and press `Enter`.
- If you want to add a new nameserver enter `y`, otherwise enter `n`, and press `Enter`.
- Optionally, you can use DHCP to obtain the IP address and default router information. If there’s no DHCP server, you can configure the IP address and default router information manually.
-
Enter the VM hostname.
The VM restarts the network and checks the connection.
[See image.](#configure-network-image)
- Go back to the Admin Portal and go to **Policies** > **Data Protection** > **Common Resources** > **DLP Incident Receiver**. Then click the **Zscaler Incident Receiver** tab.
-
Locate the Zscaler Incident Receiver you added previously, and under the** Certificate **column click **Download**.
[See image.](#download-certificate-image)
- Copy over the certificate .zip file to the VM and install it:
-
In this example, we’re using scp to copy over the file:
scp <certificate_zip_filename> zsroot@<ip>:/home/zsroot
For example: `scp IncidentReceiverCertificate.zip zsroot@10.66.108.100:/home/zsroot`
-
Enter the following command to install the SSL certificate:
sudo zirsvr configure ~/<certificate_zip_filename>
For example: `sudo zirsvr configure ~/IncidentReceiverCertifcate.zip`
-
For` icaps_port`, enter the Zscaler Incident Receiver port number that you’ve previously added to the Zscaler Incident Receiver URI in the Admin Portal.
(Optional) You can enter a different port number to change the Incident Receiver’s port number. However, you must also update the Incident Receiver’s URI in the Admin Portal to include the new port number. To learn more, see [Adding a Zscaler Incident Receiver](/unified/adding-zscaler-incident-receiver).
[See image.](#icaps-port-image)
-
Specify whether the Incident Receiver uses SFTP or S3 storage. For SFTP storage, configure the storage server and public key authentication:
- [SFTP storage](#sftp-storage)
- [S3 storage](#s3-storage)
By default, the Incident Receiver Health Check is enabled. The health check notes if there are any changes in behavior and is set to 5 minute intervals. To verify the Health Check is working, you receive the Health Status JSON `<systmld>_<iphash>_ir_health_status_timestamp.json` file in your evidence folder. If you would like to disable the Health Check, contact Zscaler Support.
- [Example of health check file](#health-check-file)
If the Zscaler Incident Receiver was configured properly, it:
- Downloads the latest build
- Installs the certificate you specified
- Checks if the service is configured correctly
- Starts the service
After the Zscaler Incident Receiver service has started, you can add it to the DLP policy rule. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/unified/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/unified/configuring-dlp-policy-rules-without-content-inspection), and [Configuring the SaaS Security API DLP Policy](/unified/configuring-saas-security-api-dlp-policy).
You can log in to the storage server to see information about DLP policy violations. For each policy violation, the storage server creates a directory containing the policy-violating file and a JSON file for the DLP policy scan metadata.
[Download a sample JSON file for Endpoint DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/ENDPOINT-DLP-IR-METADATA.json)
[Download a sample JSON file for DLP policy with and without content inspection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-example-1-27.json)
[Download a sample JSON file for DLP policy with Evaluate All Rules mode enabled](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-evaluate-all-rules-enabled-example_08.15.25.json)
[Download a sample JSON file for SaaS Security DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/SaaS-Security-DLP-IR-METADATA.json)
[]
`{
"ipAddress":"10.66.103.169",
"version":"6.3.2404",
"updatedAt":"1726848892",
"systemId":"65533",
"lastIncidentReceivedAt":"1726828921",
"lastFileUploadSuccessAt":"1726828921",
"storageType": "SFTP",
"storageLocation":"/sc/temp",
"healthcheckIntervalInSec":"300"
}`
[]
- For `storage_sftp_fqdn`, enter the FQDN for the storage server.
- For `storage_sftp_port`, enter the upload port of the SFTP server.
- For `storage_dir`, enter the storage server directory.
- For `storage_sftp_username`, enter a username for storage server login.
-
Enter a password for the username to set up the public key. This password is used temporarily and is not saved.
[See image.](#configure-storage-server-EC2-sftp-image)
If the SFTP server doesn't allow password-based authentication, you receive an error that the service is unable to update the public key on the server. If you receive that error, add the contents of the public key to the `authorized_keys` file on the SFTP server:
- Copy the contents from the file `/.ssh/id_ed25519.pub.`
- On the SFTP server, add the copied content to the end of the following file: `/.ssh/authorized_keys.`
-
On the Incident Receiver VM, enter the following command:
sudo zirsvr configure ~/<certificate_zip_filename>
[]
- Specify whether your organization uses Zscaler Workflow Automation (`y/n`).
- For `storage_s3_region_name`, enter the region where the S3 server resides (e.g., `ap-east-1`).
- For `storage_s3_data_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store data.
- For `storage_s3_data_dir`, enter the directory within the S3 bucket where the Incident Receiver can store data.
- For `storage_s3_json_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store JSON files that contain incident details.
-
For `storage_s3_json_bucket_dir`, enter the directory within the S3 bucket where the Incident Receiver can store JSON files that contain incident details.
[See image.](#configure-storage-server-s3-image)
[]![Configuring the SFTP storage server for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/configure-storage-server-EC2-sftp-image.png)
[]![Configuring the S3 storage server for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/configure-storage-server-s3.png)
[]![Download the Zscaler Incident Receiver certificate](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/ZIA-Download-Incident-Receiver-Certificate.png)
[]![The initial root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/initial-root-password.png)
[]![Changing the root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/change-password.png)
[]![Entering the new root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-new-password.png)
[]![Configuring the network for the Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/configure-network.png)
[]![Entering the port number for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-icaps-port.png)
[]If you have successfully configured the service, the service automatically downloads the latest build before it starts. To manually update the service:
-
Enter the following command to stop the service:
sudo zirsvr stop
-
Enter the following command to install the update:
sudo zirsvr update-now
-
Enter the following command to start the service:
sudo zirsvr start
[]If you receive an error for an expired certificate, you must install a new server certificate. To do so:
-
Run the following command to verify your server certificate is expired:
`sudo zirsvr troubleshoot `
-
Run the following command to create a certificate signing request:
`sudo zirsvr create-server-cert-csr`
- Send the certificate to a well-known CA for signing.
-
Run the following command to install the server certificate:
`sudo zirsvr install-server-cert`
-
Run the following command to restart the Incident Receiver and update the server certificate:
`sudo zirsvr restart`
[]To run the Incident Receiver in explicit proxy mode:
- Log in to the VM as user `zsroot`
-
Enter the following command:
sudo zirsvr configure-network
- For `Do you require a proxy server configuration?` enter `y` and press `Enter`.
- For `proxyserver` enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport` enter your proxy port number (e.g., `1344`) and press `Enter`.
The VM then tests the connection and when this is successful, the configuration is complete.
To remove the explicit proxy configuration:
-
Enter the following command:
sudo zirsvr configure-network
- For `Do you require proxy server configuration?` enter `n` and press `Enter`.
- For `Do you want to delete current proxy configuration?` enter `y` and press `Enter`.
Requirements for Explicit Proxy Mode
If you're using explicit proxy mode, DNS and NTP connections are not tunneled, meaning, you need an internal DNS server to run in this mode. The Zscaler Incident Receiver needs to have DNS resolution for the current Master CA IP, update server, and the NTP server. The Zscaler Incident Receiver host also needs to be able to query a DNS server to resolve the following:
- smcacluster.<cloudname>
- update1.<cloudname>
- update2.<cloudname>
- zdistribute.<cloudname>
- The NTP server. By default, the VM has the following FQDNs for NTP servers configured:
- 0.freebsd.pool.ntp.org
- 1.freebsd.pool.ntp.org
- 2.freebsd.pool.ntp.org
You can override these FQDNs to your internal IP address in your DNS server configuration or using other methods.
In addition, since the proxy configuration doesn't allow authentication, you need to configure the proxy server to allow specific IP/MAC addresses without user and password authentication.
[]You can use the Mutual Transport Layer Security (MTLS) method to support client authentication for the Zscaler Incident Receiver. MTLS is a method for mutual authentication. It ensures that parties at each end of the connection are who they claim to be. Zscaler provides the MTLS CA Certificate for the Zscaler Incident Receiver and you have the option to enable mutual authentication for the Zscaler Incident Receiver, which then uses this certificate for client authentication.
To run the Incident Receiver VM with mutual transport security enabled:
- Log in to the VM as user `zsroot.`
- Enable MTLS by updating the `icap_mtls_enabled` parameter to 1 (`icap_mtls_enabled=1`). By default, this parameter is disabled.
-
Enter the following command to restart the Zscaler Incident Receiver service:
sudo zirsvr restart
[]You can configure the Zscaler Incident Receiver VM to allow multiple simultaneous SFTP connections if you notice that SFTP upload is slower than expected or if you notice that the Zscaler Incident Receiver internal queue is full. You can find the logs for the Incident Receiver internal queue at `/sc/log/zirsvr.log`. To configure this setting:
- Log in to the VM as user `zsroot`.
- Specify the number of simultaneous SFTP connections by updating the `storage_sftp_conn_max` parameter to a value from 1-16 (e.g., `storage_sftp_conn_max=2`). This parameter has a value of 1 by default.
-
Enter the following command to restart the Zscaler Incident Receiver service:
scp sudo zirsvr restart
- Be sure to conduct thorough end-to-end testing before enabling this setting in your production environment.
- If changing this setting does not solve the problem of the Zscaler Incident Receiver internal queue filling up, you may also need to increase the specifications on your SFTP server to ensure faster throughput, or you may need to configure multiple incident receivers with load balancing.
- If you need assistance enabling this setting in your environment, contact Zscaler Support.
[]
| **Command** | **Description** |
| ----------- | --------------- |
| `sudo zirsvr stop` | Stops the Zscaler Incident Receiver service. |
| `sudo zirsvr start` | Starts the Zscaler Incident Receiver service. |
| `sudo zirsvr update-now` | Updates the Zscaler Incident Receiver service. The service must be stopped before you can run this command. |
| `sudo zirsvr configure-sftp` | Updates the SFTP server used by the Incident Receiver. |
| `sudo zirsvr restart` | Restarts the Zscaler Incident Receiver service. |
| `sudo zirsvr status` | Displays whether the Zscaler Incident Receiver service is running or stopped. |
| `sudo zirsvr force-update-now` | Forces the Zscaler Incident Receiver service to update to the latest version regardless of what version is on the VM. The service is automatically stopped before the update begins. |
| `sudo zirsvr troubleshoot` | Runs a series of checks to help troubleshoot issues, such as checking the installed certificate, the zcloud server configuration, all services, and whether or not an update is needed. |
| `sudo zirsvr collect-diagnostics` | Creates a file with diagnostic information to send to Zscaler Support for troubleshooting purposes. |
| `sudo zirsvr configure-syslog-server` | Configures external syslog server forwarding on the Zscaler Incident Receiver to forward file SFTP events and to log any critical changes to the configuration files monitored by the Incident Receiver. The external syslog server forwarding happens over UDP port 514, which cannot be modified. |
| `sudo zirsvr create-server-cert-csr` | Creates a new server certificate to be downloaded to the Incident Receiver. |
| `sudo zirsvr install-server-cert` | Installs server certificates. |
| `sudo zirsvr update-sshkey` | Creates a new SSH key and updates Zscaler Incident Receiver to use the new SSH key as authentication. |
[]An admin can request remote assistance and allow Zscaler Support to log in to an Incident Receiver without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
-
To enable Zscaler Support to access your Incident Receiver:
sudo zirsvr support-access-start
This command creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Incident Receiver.
-
To disable Zscaler Support access to your Incident Receiver:
sudo zirsvr support-access-stop
This command brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
-
To check the status of the Zscaler Support access to your Incident Receiver:
sudo zirsvr support-access-status
[]
If your organization requires you to update your SSH key, upgrade to the ED25519 key. To upgrade:
-
Run the following command:
`sudo zirsvr troubleshoot`
If you see the following warning, you must update your SSH key:
`Checking SFTP server connection
External SFTP server is configured as ...
SFTP server is setup correctly, connection, read, and write are all successful. However, disk quota is not checked.
Warning: SFTP is configured with older key type "rsa", consider upgrading it to newer keytype "ed25519" using command "sudo zirsvr update-sshkey". If your SFTP server is a Windows based server, please read SFTP server's Admin Guide.`
You can do a snapshot of your VM before executing the following command.
-
Run the following command:
``sudo zirsvr update-sshkey``
If the SSH key was migrated correctly:
- It creates an SSH key with ED25519 to the file `authorized_keys` under the directory `/home/zsroot/.ssh`.
- It adjusts the file `/sc/conf/sc.conf` to use the new ED25519 key.
-
On a Linux-based SFTP server, it uses a new public key.
If your SFTP server doesn't support ssh-copy-id, you receive a message that the operation was unsuccessful. To update the SSH public key with the new ED25519 key, contact Zscaler Support.