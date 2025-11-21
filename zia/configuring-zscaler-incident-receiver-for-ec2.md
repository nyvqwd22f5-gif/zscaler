# Configuring the Zscaler Incident Receiver for Amazon Web Services EC2 VMs
Source: https://help.zscaler.com/zia/configuring-zscaler-incident-receiver-for-ec2
PDF: https://help.zscaler.com/pdf/com/en/1449896.pdf

Before you can use a [Zscaler Incident Receiver](/zia/about-zscaler-incident-receiver), you must configure the VM image for the Incident Receiver on an Amazon Web Services (AWS) EC2 instance, on an Azure VM, or an on-premises VM.
To learn more, see [Configuring the Zscaler Incident Receiver for Azure VMs](/zia/configuring-zscaler-incident-receiver-azure-vms) and [Configuring the Zscaler Incident Receiver for On-Premises VMs](/zia/configuring-zscaler-incident-receiver).
Deploying a Zscaler Incident Receiver VM on AWS
To deploy a Zscaler Incident Receiver VM on AWS:
- [1. Request the Zscaler Incident Receiver AMI from Zscaler Support.](#step-1-request-ami)
- [2. Ensure you meet the requirements.](#step-2-requirements)
- [3. Create a security group to be used in the configuration of the Incident Receiver VM.](#step-3-security-group)
- [4. Set up storage for data from the Incident Receiver.](#step-4-s3-stfp-storage)
- [5. Launch an EC2 Instance for the Incident Receiver VM.](#step-5-launch-instance)
- [6. Configure the Incident Receiver VM.](#step-6-configure-vm)
- [7. (Optional) Configure a load balancer for the Incident Receiver.](#step-7-load-balancer)
Updating and Customizing a Deployed Zscaler Incident Receiver VM
With your Incident Receiver VM running, you can update and customize the VM based on your organization's needs.
- [Update the Incident Receiver VM](#update-incident-receiver)
- [Run the Incident Receiver VM in Explicit Proxy Mode](#explicit-proxy)
- [Run the Incident Receiver VM with Mutual Transport Security Enabled](#mutual-transport-security)
- [Configuring the Zscaler Incident Receiver VM to Allow Multiple SFTP Connections](#multiple-sftp-connections)
- [Enabling Remote Access for Zscaler Support](#enable-remote-access)
- [Upgrade SSH Key to ED25519](#upgrade-ssh-key)
- [Install a New Server Certificate](#install-new-cert)
Zscaler Incident Receiver Commands
You can use the following commands to configure, update, and troubleshoot your VM.
| **Command** | **Description** |
| ----------- | --------------- |
| `sudo zirsvr stop` | Stops the Zscaler Incident Receiver service. |
| `sudo zirsvr start` | Starts the Zscaler Incident Receiver service. |
| `sudo zirsvr update-now` | Updates the Zscaler Incident Receiver service. The service must be stopped before you can run this command. |
| `sudo zirsvr configure-s3` | Updates the S3 bucket used by the Incident Receiver. |
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
[][]Before you can configure your Incident Receiver with AWS, you must contact Zscaler Support and request the Zscaler Incident Receiver AMI for your shared AWS account and region. Zscaler Support then provides you with the shared AMI ID and description to use when launching the EC2 instance that hosts the Zscaler Incident Receiver VM. To learn more, refer to the [AWS documentation.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)
[]To deploy the Zscaler Incident Receiver on an EC2 instance on AWS, you need:
- Access to one of the following types of storage servers where the Incident Receiver can store files:
- An [Amazon S3 storage bucket](#s3-optional-requirement)
- An [SFTP storage server](#sftp-optional-requirement)
- The Zscaler Incident Receiver [Amazon Machine Image (AMI)](/zia/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms#ami-substep).
- A minimum t2.large or t3.large EC2 instance type.
The AMI deployment includes minimum specifications for various settings (e.g., disk size and network interface). You can increase those specifications as needed.
- RAM: 8GB
- (Optional) A static public IP address for the VM.
Zscaler recommends using a static IP address to ensure that the IP address does not change when the VM is rebooted. Alternatively, you can associate the IP address with a fully qualified domain name (FQDN) and then use the FQDN when [configuring the Incident Receiver](/zia/modifying-zscaler-incident-receiver) in the ZIA Admin Portal.
- A [security group](/zia/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms#security-group-substep) configured on the EC2 instance to allow inbound ICAP messages from the FCC cloud to the correct TCP port on the Incident Receiver VM (e.g., port 1344).
- A [Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver) added in the ZIA Admin Portal. You need this configuration to complete the VM setup.
- For Zscaler Incident Receiver to check your network connectivity and get access to and from your IP address, your firewalls must be enabled for the appropriate location. To understand the needed access requirements, see [DLP Incident Receiver Connections](https://config.zscaler.com/zscaler.net/dlp-incident-receiver).
- You must allow a direct IP-based connection to the Zscaler Hub IPs so the Incident Receiver can connect to the IP directly. To learn more, see [Zscaler Hub IP Addresses](https://config.zscaler.com/zscaler.net/hubs).
[]To create a security group in AWS:
- []Log in to the AWS Management web UI or console.
- In the **AWS Management** console, click the **Services** icon. The Services navigation menu is displayed.
- Go to **Compute > EC2**. The **EC2 Management Console** appears, displaying the **EC2 Dashboard**.
- Open a new tab and perform the following steps:
- Browse to [config.zscaler.com](http://config.zscaler.com). The **Zscaler Config** page is displayed.
- Select your organization's Zscaler cloud from the **Cloud** drop-down menu at the top left of the page.
- Select **DLP Incident Receiver **in the left-side navigation, then click the **Zscaler Hub IP Addresses **link in the **Source** column of the table. The **Hub IP Addresses** page is displayed listing all of the outbound connections that need to be configured for the Zscaler Incident Receiver to communicate with the Zscaler cloud.
[See image.](#hub-ip-addresses-page)
- Click **Copy IPs** in the **Required**, **Recommended**, and **Combined** columns as needed so you can add them to the security group.
- Return to the **EC2 Management Console**, and go to **Network & Security > Security Groups. **The **Security Groups** page is displayed.
[See image.](#security-groups-page)
- On the **Security Groups** page, click **Create security group **in the top right of the page. The **Create security group** page is displayed.
- On the **Create security group **page:
- **Basic details**: Enter a name for the security group in the **Security Group Name** field.
- **Inbound rules**: Add the incoming traffic IPs for the Zscaler Incident Receiver VM. Make sure that you add the IPs that you copied from the Zscaler **Hub IP Addresses** page earlier.
- **Outbound Rules**: Add the outgoing traffic IPs for the Zscaler Incident Receiver VM.
[See image.](#AWS-Security-Group-Page-Populated-Data)
- Click **Create security group**.
To learn more, refer to the [AWS documentation.](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
[]![Zscaler Hub IP Addresses page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-hub-ip-addresses-page.png)
[]![Viewing Security Groups on the Security Groups Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-Security-Groups-Page.png)
[]![Viewing a Security Group configuration on the Create Security Group Page in Amazon Web Services](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-Create-Security-Group-Page-Populated.png)
[][][]Because the Zscaler Incident Receiver does not store files locally, it requires either an S3 bucket or an SFTP server to store incident data.
- [S3 storage](#s3-storage-requirement)
- [SFTP storage](#sftp-storage-requirement)
[]To use an S3 bucket, you should configure the EC2 VM with an Identity and Access Management (IAM) role for the Incident Receiver EC2 instance so that the instance has list and write access (ListBucket and PutObject, respectively) to the S3 storage volume.
If you are using your Incident Receiver with [Zscaler Workflow Automation](/zia/what-workflow-automation), two separate S3 buckets are created for you during the creation of the CloudFormation stack in AWS. If you are not using your Incident Receiver with Zscaler Workflow Automation, you can use a single S3 bucket for data and JSON files, or you can use separate buckets. The following example uses separate S3 buckets.
To create an AWS IAM role and then associate it with your EC2 Incident Receiver VM:
- From the EC2 instance, go to **Actions > Security > Modify IAM role**. The **Modify IAM role** page is displayed.
- Click **Create new IAM role**.
[See image.](#modify-iam-role)
The IAM Management Console **Roles** page is displayed in a new tab.
- Click **Create role** in the upper right of the page. The **Select trusted entity** page is displayed.
- Select **AWS service** as the **Trusted entity type**, then select **EC2** in the **Common use cases** section.
[See image.](#select-trusted-entity-page)
- Click **Next**. The **Add permissions** page is displayed.
- Click **Create policy** in the upper right of the page. The **Create policy** page is displayed in a new tab.
- Click the **JSON** tab, then paste the contents of one of the following sample JSON files to create a policy with list and write access to the S3 bucket, depending on whether or not you are using AWS KMS Keys.
- [S3 Without Encryption](#S3-Without-Encryption)
- [S3 with Customer Managed AWS KMS Keys](#S3-With-Customer-Managed-AWS-KMS-Keys)
- Click **Next: Tags**. The **Add tags** page is displayed.
- Specify any optional tags, then click **Next: Review**. The **Review policy** page is displayed.
- Specify a name and optional description for the policy, review the permissions and tags, then click **Create policy**.
[See image.](#review-policy-page)
- Return to the tab where the **Add permissions** page is displayed.
- Click the **Refresh** button next to the **Create policy** button, then select the policy you created from the list.
[See image.](#select-policy)
- Click **Next**. The **Name, review, and create** page is displayed.
- Specify a name and optional description for the role, review the permissions for the role, then click **Create role**.
[See image.](#name-review-create-page)
- Return to the tab where the **Modify IAM role** page is displayed.
- Click the button next to the drop-down menu to refresh the list, then select the IAM role you created from the drop-down menu.
- Click **Update IAM role**.
[See image.](#update-iam-role)
To learn more, refer to the [AWS documentation.](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html)
[][Download a sample JSON file for AWS S3 list and write access](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/AWS-S3-list-and-write.json)
[See image.](#create-permissions-policy)
In the sample JSON file, replace `zirsvr-s3-data-bucket` and `zirsvr-s3-json-bucket` with the names of your S3 data and JSON buckets, respectively. If you are not using your Incident Receiver with [Zscaler Workflow Automation](/zia/what-workflow-automation), you can use a single bucket for data and JSON files. The sample JSON file uses separate buckets but can be adjusted to remove the entry for the second bucket.
[][Download a sample JSON file for AWS S3 list and write access](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/AWS-S3-Encrypted-list-and-write.json)
[See image.](#create-permissions-policy-encrypted)
In the sample JSON file, replace `zirsvr-s3-data-bucket` and `zirsvr-s3-json-bucket` with the names of your S3 data and JSON buckets, respectively. If you are not using your Incident Receiver with [Zscaler Workflow Automation](/zia/what-workflow-automation), you can use a single bucket for data and JSON files. The sample JSON file uses separate buckets but can be adjusted to remove the entry for the second bucket.
[]![The Modify IAM role page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-modify-iam-role.png)
[]![The Select Trusted Entity page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-select-trusted-entity-page.png)
[]![Create permissions policy for AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-create-permissions-policy.png)
[][![Creating an AWS Encrypted Policy in Amazon Web Services](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-Create-Permission-Policy-Encrypted.png)
](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-Create-Permission-Policy-Encrypted.png)
[]![Review and create permissions policy for AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-review-permissions-policy.png)
[]![Select permissions policy for AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-select-permissions-policy.png)
[]![The Name, Review, Create page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-name-review-create-page.png)
[]![Updating an IAM role for an EC2 instance in AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-update-IAM-role.png)
[]If you do not use an S3 bucket to store Incident Receiver data, then you must set up a storage server that supports SFTP/SCP and public key authentication. You must also have a preconfigured account that allows write access to the server’s intended directory. You link the SFTP server to the Incident Receiver VM when you [configure storage options](/zia/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms#storage-options-substep) later in the process.
[]To launch an EC2 instance for the Incident Receiver VM:
- In the **EC2 Management Console**, go to **Instances > Instances.** The **Instances** page is displayed.
- On the **Instances page**, click **Launch instances** at the top right of the page. The **Launch an instance** page is displayed.
- (Optional) In the **Name and tags** section, enter a name for the Incident Receiver VM in the **Name** field.
- In the **Application and OS Images (Amazon Machine Image)** section:
- Click the **My AMIs** tab.
- Select the **Shared with me** option.
- In the **Amazon Machine Image (AMI)** drop-down menu, select the AMI image that Zscaler Support shared with you.
- In the **Instance type** section, in the **Instance type** drop-down menu, select the appropriate instance type required for the Incident Receiver VM (e.g., **t2.medium** or **t3.medium**). The instance type that you select must allow access to either an EC2 serial console or an instance screenshot.
[See image.](#instance-type-section)
-
Specify a **Key pair (login)** option, based on your organization's requirements.
SSH login is only supported with **Key pair (login)**. Password is not supported.
- In the **Network settings** section, under **Firewall (security groups)**:
- Select the **Select existing security group** option.
- In the **Security groups** drop-down menu, select the security group you previously created.
AWS automatically assigns the network IP address for the instance. You do not need to enter the IP address information unless it is required by your organization.
- Click **Launch instance **in the lower right of the page. A message is displayed stating that the launch of the instance was successfully initiated and it lists the instance ID that was created.
- Right-click on the instance ID, and select **Open Link in New Tab**. The **Instances** page is displayed listing the instance with an **Instance state** of **Pending**. After a few seconds, the **Instance state** changes from **Pending** to **Running**.
- On the **Instances** page, click the **Instance ID**. The **Instance summary** page is displayed. On the **Instance summary** page you can view the details for the instance, including the IP addresses that were assigned to the instance.
If you are using a public IP address, when you shut down and restart the instance, the IP address changes.
- Find and make note of the initial root password. When the instance state is running, depending on the type of instance you're using, you can get the initial root password either from the instance screenshot (**Actions > Monitor and troubleshoot > Get instance screenshot**) or from the EC2 serial console. The initial root password for this user is randomly generated.
[See image.](#Get-Instance-Screenshot)
To learn more, refer to the [AWS documentation.](https://aws.amazon.com/premiumsupport/knowledge-center/launch-instance-custom-ami/)
[]![Selecting an instance type for an instance in the Launch an Instance Page in AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-Launchaninstancepage-Instance-Type.png)
[]![Viewing the Instance Screenshot for an Incident Receiver instance in AWS](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-AWS-get-instance-screenshot-ZIRSVR.png)
[]To configure the Incident Receiver VM:
- Ensure that you have [added a Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver) in the ZIA Admin Portal. You need this configuration to complete the VM setup.
- Log in to the VM as user `zsroot`. The initial root password for this user is randomly generated.
- Change the root password:
- Enter the following command to set a password:
sudo zirsvr paawd-zsroot
[See image.](#change-password-command-image)
- Log in to the newly created Zscaler Incident Receiver.
- Enter the initial root password, the one that was randomly generated for you.
- Enter a new root password.
[See image.](#new-root-pass-image)
- Re-enter the new root password.
- Go to the ZIA Admin Portal and go to **Administration** > **DLP Incident Receiver**. Then click the **Zscaler Incident Receiver** tab.
- Locate the Zscaler Incident Receiver you added previously, and under the** Certificate **column click **Download**.
[See image.](#download-certificate-image)
- Copy over the certificate .zip file to the VM and install it:
- In this example, we’re using scp to copy over the file:
scp <certificate_zip_filename> zsroot@<ip>:/home/zsroot
For example: `scp IncidentReceiverCertificate.zip zsroot@10.66.108.100:/home/zsroot`
- Enter the following command to install the SSL certificate:
sudo zirsvr configure ~/<certificate_zip_filename>
For example: `sudo zirsvr configure ~/IncidentReceiverCertifcate.zip`
- For `icaps_port`, enter the Zscaler Incident Receiver port number that you’ve previously added to the Zscaler Incident Receiver URI in the ZIA Admin Portal.
(Optional) You can enter a different port number to change the Incident Receiver’s port number. However, you must also update the Incident Receiver’s URI in the ZIA Admin Portal to include the new port number. To learn more, see [Adding a Zscaler Incident Receiver](/zia/adding-zscaler-incident-receiver).
[See image.](#icaps-port-image)
- []Specify whether the Incident Receiver uses S3 or SFTP storage. For SFTP storage, configure the storage server and public key authentication:
- [S3 storage (with Zscaler Workflow Automation)](#s3-storage-zwa)
- [S3 storage (without Zscaler Workflow Automation)](#s3-storage-no-zwa)
- [SFTP storage](#sftp-storage)
By default, the Incident Receiver Health Check is enabled. The health check notes if there are any changes in behavior and is set to 5 minute intervals. To verify the Health Check is working, you receive the Health Status JSON `<systmld>_<iphash>_ir_health_status_timestamp.json` file in your evidence folder. If you would like to disable the Health Check, contact Zscaler Support.
- [Example of health check file](#health-check-file)
If the Zscaler Incident Receiver was configured properly, it:
- Downloads the latest build
- Installs the certificate you specified
- Checks if the service is configured correctly
- Starts the service
[See image.](#console-successful)
After the Zscaler Incident Receiver service has started, you can add it to the DLP policy rule. To learn more, see [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection), [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection), and [Configuring the SaaS Security API DLP Policy](/zia/configuring-saas-security-api-dlp-policy).
You can log in to the storage server to see information about DLP policy violations. For each policy violation, the storage server creates a directory containing the policy-violating file and a JSON file for the DLP policy scan metadata.
[Download a sample JSON file for Endpoint DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/ENDPOINT-DLP-IR-METADATA.json)
[Download a sample JSON file for DLP policy with and without content inspection](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-example-1-27.json)
[Download a sample JSON file for DLP policy with Evaluate All Rules mode enabled](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/inline-web-DLP-evaluate-all-rules-enabled-example_08.15.25.json)
[Download a sample JSON file for SaaS Security DLP policy](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-for-ec2/SaaS-Security-DLP-policy.txt)
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
[]![Changing the root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/change-password.png)
[]![Entering the new root password for the Zscaler Incident Receiver VM](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-new-password.png)
[]![Download the Zscaler Incident Receiver certificate](/downloads/zia/policies/data-loss-prevention/configuring-zscaler-incident-receiver/ZIA-Download-Incident-Receiver-Certificate.png)
[]![Entering the port number for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver/enter-icaps-port.png)
[]![Console output for a successful Incident Receiver deployment](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-zirsvr-console-successful-deployment.png)
[]
- For `storage_sftp_fqdn`, enter the FQDN for the storage server.
- For `storage_sftp_port`, enter the upload port of the SFTP server.
- For `storage_dir`, enter the storage server directory.
- For `storage_sftp_username`, enter a username for storage server login.
- Enter a password for the username to set up the public key. This password is used temporarily and is not saved.
[See image.](#configure-storage-server-EC2-sftp-image)
If the SFTP server doesn't allow password-based authentication, you receive an error that the service is unable to update the public key on the server. If you receive that error, add the contents of the public key to the `authorized_keys` file on the SFTP server:
- Copy the contents from the file `/.ssh/id_ed25519.pub.`
- On the SFTP server, add the copied content to the end of the following file: `/.ssh/authorized_keys.`
- On the Incident Receiver VM, enter the following command:
sudo zirsvr configure ~/<certificate_zip_filename>
[]
- Specify that your organization uses [Zscaler Workflow Automation](/zia/what-workflow-automation) (`y`).
- For `storage_s3_region_name`, enter the region where the S3 server resides (e.g., `ap-east-1`).
- For `storage_s3_data_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store data.
- For `storage_s3_data_dir`, enter a slash (`/`) to indicate the directory within the S3 bucket where the Incident Receiver can store data. You must enter a slash and not any other directory path. Workflow Automation expects the data to be available in the S3 root directory.
- For `storage_s3_json_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store JSON files that contain incident details.
- For `storage_s3_json_bucket_dir`, enter a slash (`/`) to indicate the directory within the S3 bucket where the Incident Receiver can store JSON files that contain incident details. You must enter a slash and not any other directory path. Workflow Automation expects the data to be available in the S3 root directory.
[See image.](#configure-storage-server-s3-image)
[]
- Specify that your organization does not use [Zscaler Workflow Automation](/zia/what-workflow-automation) (`n`).
- For `storage_s3_region_name`, enter the region where the S3 server resides (e.g., `ap-east-1`).
- For `storage_s3_data_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store data.
- For `storage_s3_data_dir`, enter the directory within the S3 bucket where the Incident Receiver can store data.
- Specify whether you want to use a different bucket for JSON files (`y/n`).
- If you are using a different bucket for JSON files, for `storage_s3_json_bucket_name`, enter the name of the S3 bucket where the Incident Receiver can store JSON files that contain incident details.
- If you are using a different bucket for JSON files, for `storage_s3_json_bucket_dir`, enter the directory within the S3 bucket where the Incident Receiver can store JSON files that contain incident details.
[See image.](#configure-storage-server-s3-no-zwa-image)
[]![Configuring the SFTP storage server for Zscaler Incident Receiver](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/configure-storage-server-EC2-sftp-image.png)
[]![Configuring the S3 storage server for Zscaler Incident Receiver with Zscaler Workflow Automation](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/configure-storage-server-s3.png)
[]![Configuring the S3 storage server for Zscaler Incident Receiver without Zscaler Workflow Automation](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/configure-storage-server-s3-no-zwa.png)
[]To configure a load balancer for the Incident Receiver:
- In the **EC2 Management Console**, go to **Services > EC2**. The **EC2 Dashboard** page is displayed.
- On the **EC2 Dashboard page**, click **Load Balancers** on the bottom left of the page.
[See image.](#dashboard-load-balancers)
The **Load balancers** page is displayed.
- On the **Load balancers** page, select **Create load balancer > Create Network Load Balancer**.
[See image.](#create-network-load-balancer)
The **Create Network Load Balancer** page is displayed.
- In the **Load balancer name** field, provide a name for the load balancer.
- In the **Network mapping** section, select one or more availability zones for the load balancer. To learn more, refer to the [AWS documentation.](https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-subnets.html)
- In the **Security groups - recommended** drop-down menu, select the security group you created for the Incident Receiver.
- In the **Listeners and routing** section, select **TCP** as the **Protocol**, and enter `1344` as the **Port**.
- Click **Create target group**.
[See image.](#create-target-group-option)
The **Specify group details** page is displayed on a new browser tab.
- On the **Specify group details** page:
- In the **Choose a target type** section, select **Instances**.
- In the **Target group name** field, specify a name for the target group.
- Select **TCP** as the **Protocol**, and enter `1344` as the **Port**.
- In the **Health checks** section, select **TCP** from the **Health check protocol** drop-down menu.
- Click **Next**.
[See image.](#specify-group-details-next)
The **Register targets** page is displayed.
- On the **Register targets** page, select the Incident Receiver from the **Available instances **list, then click **Include as pending below**.
[See image.](#register-targets-include-pending)
The Incident Receiver appears in the **Review targets** list.
- Click **Create target group**.
[See image.](#create-target-group-button)
A confirmation page is displayed.
[See image.](#target-group-confirmation-page)
- Return to the browser tab where the **Create Network Load Balancer** page is open.
- In the **Listeners and routing** section, click the **Refresh** button next to the **Default action** drop-down menu, then use the drop-down menu to select the target group you created.
[See image.](#default-action-refresh-button)
- Click **Create load balancer**.
[See image.](#create-load-balancer-button)
A confirmation page for the load balancer appears.
- On the confirmation page for the load balancer, click **View load balancer**.
[See image.](#view-load-balancer-button)
The **Load balancers** page is displayed.
- On the **Load balancers** page, click the name of the load balancer you created.
[See image.](#load-balancers-page)
The **Load balancer details** page is displayed.
- On the **Load balancer details** page, in the **DNS name** section, click the **Copy DNS name to clipboard** button.
[See image.](#copy-dns-name-button)
- Go to the ZIA Admin Portal and go to **Administration** > **DLP Incident Receiver**. Then click the **Zscaler Incident Receiver** tab.
- Locate the Zscaler Incident Receiver you added previously, and click the **Edit** icon.
The **Edit Zscaler Incident Receiver** page is displayed.
- On the **Edit Zscaler Incident Receiver** page, in the **Server URI** field, paste the DNS name for the load balancer (i.e., `icaps://``<DNS Name>`).
[See image.](#ZIR-server-URI-field)
The Incident Receiver is updated to use the AWS load balancer.
[]![Selecting the Load Balancers option.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-LoadBalancers-Option.png)
[]![Create Network Load Balancer option.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-CreateNetworkLoadBalancer-Option.png)
[]![Selecting the Create target group option.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-CreateTargetGroup-Option.png)
[]![Specify group details page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-SpecifyGroupDetails-Page.png)
[]![Register targets page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-RegisterTargets-Page.png)
[]![Create target group button.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-CreateTargetGroup-Button.png)
[]![Target group confirmation page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-TargetGroupConfirmation-Page.png)
[]![Default action drop-down menu.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-DefaultActionDropDown-Menu.png)
[]![Clicking the Create load balancer button.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-CreateLoadBalancer-Button.png)
[]![Clicking the View load balancer button.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-ViewLoadBalancer-Button.png)
[]![The Load balancers page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-LoadBalancers-Page.png)
[]![The Copy DNS name to clipboard button.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-AWS-CopyDNSNameToClipboard-Button.png)
[]![The Edit Zscaler Incident Receiver page.](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-zscaler-incident-receiver-amazon-web-services-ec2-vms/ZIA-DLP-IncidentReceiver-EditZIR-Page_LoadBalancerURI.png)
[]If you have successfully configured the service, the service automatically downloads the latest build before it starts. To manually update the service:
- Enter the following command to stop the service:
sudo zirsvr stop
- Enter the following command to install the update:
sudo zirsvr update-now
- Enter the following command to start the service:
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
- Enter the following command:
sudo zirsvr configure-proxy
- For `Do you require a proxy server configuration?` enter `y` and press `Enter`.
- For `proxyserver` enter the IP address of your proxy server (e.g., `proxy.zscaler.net`) and press `Enter`.
- For `proxyport` enter your proxy port number (e.g., `1344`) and press `Enter`.
The VM then tests the connection and when this is successful, the configuration is complete.
To remove the explicit proxy configuration:
- Enter the following command:
sudo zirsvr configure-proxy
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
sudo zirsvr restart
- Log in to the VM as user `zsroot.`
- Enable MTLS by updating the `icap_mtls_enabled` parameter to 1 (`icap_mtls_enabled=1`). By default, this parameter is disabled.
- Enter the following command to restart the Zscaler Incident Receiver service:
[]You can configure the Zscaler Incident Receiver VM to allow multiple simultaneous SFTP connections if you notice that SFTP upload is slower than expected or if you notice that the Zscaler Incident Receiver internal queue is full. You can find the logs for the Incident Receiver internal queue at `/sc/log/zirsvr.log`. To configure this setting:
- Log in to the VM as user `zsroot`.
- Specify the number of simultaneous SFTP connections by updating the `storage_sftp_conn_max` parameter to a value from 1-16 (e.g., `storage_sftp_conn_max=2`). This parameter has a value of 1 by default.
- Enter the following command to restart the Zscaler Incident Receiver service:
scp sudo zirsvr restart
- Be sure to conduct thorough end-to-end testing before enabling this setting in your production environment.
- If changing this setting does not solve the problem of the Zscaler Incident Receiver internal queue filling up, you may also need to increase the specifications on your SFTP server to ensure faster throughput, or you may need to configure multiple incident receivers with load balancing.
- If you need assistance enabling this setting in your environment, contact Zscaler Support.
[]An admin can request remote assistance and allow Zscaler Support to log in to an Incident Receiver without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your Incident Receiver:
sudo zirsvr support-access-start
This command creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your Incident Receiver.
- To disable Zscaler Support access to your Incident Receiver:
sudo zirsvr support-access-stop
This command brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your Incident Receiver:
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