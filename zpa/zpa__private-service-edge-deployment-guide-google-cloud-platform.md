# Private Service Edge Deployment Guide for Google Cloud Platform
Source: https://help.zscaler.com/zpa/private-service-edge-deployment-guide-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1507506.pdf

This deployment guide provides information on prerequisites, how to deploy an Private Service Edge on Google Cloud Platform (GCP), and post-deployment verification checks. For general information regarding Private Service Edge deployment for ZPA, see [About ZPA Deploying Private Service Edges](/zpa/about-deploying-service-edges).
- [Step 1: Make Sure You Have Met All Private Service Edge Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the Private Service Edge on GCP](#deploy)
- [Step 3: Disable the Password Expiration for the STIG-Hardened Private Service Edge Image](#step3disablepassword)
- [Step 4: Configure the Networking for the Deployed Private Service Edge](#networking)
- Step 5: Verify that the deployed Private Service Edge is [running and healthy](/zpa/managing-deployed-zpa-private-service-edges). Also, check that it is [meeting your sizing requirements](/zpa/managing-deployed-zpa-private-service-edges#VerifySizing).
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges).
After Private Service Edges are deployed, you can:
- [Create application segments](/zpa/configuring-application-segments) and [access policies](/zpa/about-policies) to pass application traffic. For example, to test your configuration, consider setting up a simple application segment that allows SSH access to your Private Service Edges.
- [Configure a log receiver](/zpa/configuring-log-receiver) for your Private Service Edges to receive information about your Private Service Edges or users via the [Log Streaming Service (LSS)](/zpa/about-log-streaming-service).
[]
Before deploying a ZPA Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each ZPA Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the ZPA Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 ZPA Private Service Edges.
500 Mbps of throughput is an aggregate of multiple streams of traffic.
- [ZPA Private Service Edge Specifications and Sizing Requirements](#SpecsSizing)
- [ZPA Private Service Edge Platform Prerequisites](#PlatformPrereqs)
- [ZPA Private Service Edge Security Guidance and Firewall Requirements](#Firewall)
- [ZPA Private Service Edge Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the ZPA Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each ZPA Private Service Edge.
- Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| Active Users | Memory | vCPU or CPU Cores |
| ------------ | ------ | ----------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 32 GB (34 GB with ZDX) | 16 vCPUs or 16 CPUs |
To learn more, see the [ZPA Private Service Edge Deployment Guide](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each ZPA Private Service Edge must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable ZPA for both remote and office users, each ZPA Private Service Edge needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
ZPA Private Service Edges are reachable over the internet for remote users in a disaster recovery scenario, or when the ZPA Private Service Edge is the closest Service Edge.
In the scenario where a ZPA Private Service Edge is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the ZPA Private Service Edge's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the ZPA Private Service Edge. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the ZPA Private Service Edge. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a [publish IP](/zpa/about-zpa-private-service-edges#AbourSvcEdgePage) of the respective ZPA Private Service Edge. In the case of disaster recovery, you must add this IP address as the A record for that ZPA Private Service Edge.
Your firewalls must be configured to let the ZPA Private Service Edge establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors.
The following conditions apply to each ZPA Private Service Edge that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a ZPA Private Service Edge is enrolled, an outbound TLS tunnel over TCP port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the ZPA Public Service Edge
- Policy configuration download
- ZPA Private Service Edge software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional ZPA Private Service Edges at any time, using the same provisioning key to add them to the existing ZPA Private Service Edge group, while ensuring network and internet connectivity. ZPA Private Service Edges are designed to scale elastically. You can deploy additional ZPA Private Service Edges in the same ZPA Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy ZPA Private Service Edges in pairs (N+1), where N is the number of ZPA Private Service Edges as per the sizing requirements. To learn more, see [About Deploying ZPA Private Service Edges](/zpa/about-deploying-service-edges) and [Supported Platforms for ZPA Private Service Edges](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the ZPA Private Service Edge meets your sizing requirements. To learn more, see [Verify ZPA Private Service Edge Sizing Specifications](/zpa/managing-deployed-zpa-private-service-edges#VerifySizing). If disk space fills up in the ZPA Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring ZPA Private Service Edge Performance](/zpa/monitoring-private-service-edge-performance#diskspace_archive).
Understanding ZPA Private Service Edge Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each ZPA Private Service Edge supports up to 500 Mbps throughput. ZPA Private Service Edges communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
500 Mbps of throughput is an aggregate of multiple streams of traffic.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
For example, if you have a 1 Gbps aggregate (i.e., total inbound and outbound) connection in your data center, you can use the 500 Mbps throughput guideline to make sure you have enough ZPA Private Service Edges to support the connection and have room for failover (N+1). In this case, you would need to deploy 2 to 3 ZPA Private Service Edges to support the 1 Gbps connection.
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, AppProtection, or ZDX enabled. Make sure that you have enough ZPA Private Service Edges to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more ZPA Private Service Edges with lower specifications rather than fewer ZPA Private Service Edges with higher specifications. For example, if you have fewer ZPA Private Service Edges with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller ZPA Private Service Edge that fails.
[]Before you begin any procedures within the [ZPA Private Service Edge Deployment Guide](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform, make sure that you have the following:
- Intel x86_64/AMD64-based architecture
- systemd
- Root or sudo access to the system to configure a new package repository and install packages
- DNS resolution and network access
- A [ZPA Private Service Edge provisioning key](/zpa/about-zpa-service-edge-provisioning-keys) obtained from the ZPA Admin Portal
- A static MAC address
[]ZPA Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The ZPA Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the ZPA Private Service Edge and its VMs to ensure that memory growth does not have an impact on the ZPA Private Service Edge performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [ZPA Private Service Edge Deployment Guides](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Security Technical Implementation Guide (STIG) images are provided for AWS, GCP, Microsoft Azure, Nutanix, and VMware by default. To learn more, see [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform). The remaining private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on RHEL 9.x). You can patch these systems when necessary by using the standard yum OS update mechanism. Zscaler recommends that you harden the operating system, including the `sshd-config` file, on the VM images in accordance with your organization's security standards after initial deployment. To learn more, see [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges#Updating).
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting ZPA Private Service Edges using firewall policies. Additionally, if you've installed the ZPA Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a ZPA Private Service Edge in such an environment as long as the ZPA Private Service Edge is able to reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing ZPA Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. ZPA Private Service Edge will not function if the TLS certificates presented by the ZPA Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the ZPA Private Service Edge. This is necessary for allowing the ZPA Private Service Edge to resolve and reach ZPA Public Service Edges. ZPA Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa) It might be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]ZPA Private Service Edges require that the [Zscaler Client Connector](/z-app) be at least on version 2.1.2.
[]For GCP, you must deploy Private Service Edges in your Virtual Private Clouds (VPCs). For each VPC there must be at least a pair of Private Service Edges deployed for resilience and scalability. The Private Service Edges should be deployed across regions and zones to ensure continuity of service in the event of an incident. Zscaler automatically load balances across the Private Service Edges. Additional capacity can be handled by adding additional Private Service Edges into each region and zone.
Private Service Edges should be configured with the right access to applications in the VPC. The VPC configuration should permit the Private Service Edges to connect to the application servers on the appropriate TCP/UDP ports, and enable ICMP reachability and DNS resolution to the applications. The Private Service Edge's VPC configuration should permit outbound access to the internet to connect to the Zscaler cloud. Zscaler recommends deploying the Private Service Edges on a private subnet which connects to the internet through a NAT gateway.
The following architectural diagram shows GCP workloads for Zscaler.
[See image.](#gcp-workload-diagram)
The following prerequisites must be met before deploying the ZPA Private Service Edge instance:
- [Installing the Google Cloud CLI](#Install-Google-Cloud-CLI)
- [Creating a Firewall Rule](#Firewall-Rule)
You can deploy the image on GCP using one of the following methods:
- [Deploying a Private Service Edge Using the Instance Wizard](#Deployment1)
- [Deploying a Private Service Edge Using a Launch Template and Auto Scaling (Advanced Deployment)](#Deployment2)
[]![Diagram of Zscaler for GCP workloads](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-google-cloud-platform/diagram_zpa_app-con_gcp_v2_alt.png)
[]To install the Google Cloud CLI, refer to the [Google Cloud documentation](https://cloud.google.com/sdk/docs/install).
[]This procedure describes how to deploy ZPA in GCP using the Instance wizard, and assumes that you have created an SSH key pair and an image from a .vmdk (virtual disk).
- [Create an SSH key pair.](#PSE-Instance-SSH-Key)
- [Launch the VM in GCP Marketplace.](#LaunchVM)
After you create an SSH key pair and an image from the virtual disk, complete the following steps to deploy using the Instance wizard.
- [See instructions.](#Deploy-PSE-Instance)
[]To launch the VM in GCP Marketplace:
- Go to [ZPA - GCP Marketplace](https://console.cloud.google.com/marketplace/product/zpa-gcp-marketplace/zscaler-private-access-service-edge).
- Click **Launch**.
- On the **Terraform **tab, enter the deployment name (e.g., `zscaler-1`).
- Enter the service account ID.
[See image.](#launchVmStep4)
- Review your configuration and then click **Deploy**.
- Verify the newly created VM on the Management page.
[]![Entering the Service account ID in GCP Marketplace](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-gcp/gcp-create-an-image-window-zmdk-appc-pse.png)
[]To deploy an Private Service Edge using an Private Service Edge instance:
- Log in to the GCP Management Console.
- Create a project.
- Select your project (e.g., **zpa-service-edge**).
-
Go to **Compute** **Engine** > **Images**.
[See image.](#Deploy-PSE-Instance-Images-page)
- Search for the custom image using a filter with the name of the image. An example of the custom name used for this step is **zpa-service-edge-el9-2024-08-99875b50-feature**.
-
Click the **Menu **icon, and then click **Create Instance.**
[See image.](#Deploy-PSE-Instance-filter-image)
The **Create an instance** window appears.
-
In the **Create an instance **window, select **New VM instance.**
[See image.](#Deploy-PSE-Instance-create-instance-window)
-
In the **New VM instance **window for the **Machine Configuration** section, select the **Machine type **with preset amounts of vCPUs and memory that suit the workload. Zscaler recommends using the n2-standard-4 or n2-highcpu-4 specifications:
- **n2-standard-4**: The supported specifications are 4 vCPU, 2 core, and 16 GB memory.
- **n2-highcpu-4**: The supported specifications are 4 vCPU, 2 core, and 4 GB memory.
[See image.](#Deploy-PSE-Instance-Machine-type)
- (Optional) Pass the startup script to the VM instance.
- Click the **Menu **icon, and then click the **Security **tab.
-
In the left-side navigation, go to **Data Protection** > **Secret Manager**.
[See image.](#pkey-secret-manager-page)
-
Click **Create Secret**.
The **Create secret** window appears.
-
In the **Create secret **window:
- **Name**: Enter the name of the secret (e.g., `provisioning_key`).
- **Secret value**: Enter the value for the secret (e.g., `<your provisioning key>`). You can acquire a provisioning key when creating a ZPA Private Service Edge in the ZPA Admin Portal. To learn more, see [About ZPA Private Service Edges Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys) and [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges).
[See image.](#pkey-secret-manager-Create-secret-window)
- Click **Create Secret**.
- For **Access Scope**, select **Allow full access to all Cloud APIs**. This allows access to the provisioning_key present in the secret manager.
- Expand the **Advanced options** section, and then expand the **Management** section.
- Add a description in the **Description** field.
-
Enter the following script for the **Automation** field.
`#!/usr/bin/bash
# Sleep to allow the system to initialize
sleep 15
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-linux-x86_64.tar.gz
tar -xf google-cloud-cli-linux-x86_64.tar.gz
export PATH=$PATH:$PWD
sudo ./google-cloud-sdk/install.sh
# Install Private Service Edge packages
yum install -y zpa-service-edge
# Stop the Private Service Edge service which was auto-started at boot time
systemctl stop zpa-service-edge
# Fetch the secret from Secret Manager
SECRET_NAME="Provision_key"
SECRET_VALUE=$(gcloud secrets versions access latest --secret="$SECRET_NAME")
# Use the secret in your application or script
echo "The secret value is: $SECRET_VALUE"
# Example: Export the secret as an environment variable
export MY_SECRET="$SECRET_VALUE"
# Create a file from the Private service edge provisioning key created in the ZPA Admin Portal
# Make sure that the provisioning key is between double quotes
echo "$SECRET_VALUE" > /opt/zscaler/var/service-edge/provision_key
chmod 644 /opt/zscaler/var/service-edge/provision_key
# Start the Private service edge service to enroll it in the ZPA cloud
systemctl start zpa-service-edge
# Wait for the Private service edge to download the latest build
sleep 60
# Stop and then start the private service edge for the latest build
systemctl stop zpa-service-edge
systemctl start zpa-service-edge
# Run a yum update to apply the latest patches
yum update -y`
- Click **Create**.
-
In the left-side navigation, go to **Compute Engine** > **Virtual Machines **> **VM instances **to verify that you created your instance. The instance name is displayed when creating the instance.
[See image.](#Deploy-PSE-Instance-Vm-verify-instance)
- SSH access is required to configure the GCP Private Key to the Private Service Edge.
- [See instructions.](#security)
- Apply the Private Service Edge provisioning key.
- [See instructions.](#pkeyreal)
-
After the Private Service Edge provisioning key is applied, verify that the deployed Private Service Edge is running using the following commands:
`sudo su
ps aux | grep zpa-service-edge`
For example:
`# ps -aux | grep zpa-service-edge
root         1423  1.2  0.1 525288 16200 ?        Ssl 14:01    0:00 /opt/zscaler/bin/zpa-service-edge
root         1845  0.0  0.0   6412 2176 pts/0     S+  14:02    0:00 grep --color=auto zpa-service-edge`
To learn more, see [Managing Deployed Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges).
- Zscaler highly recommends [updating the Private Service Edge system software](/zpa/managing-deployed-zpa-private-service-edges) before proceeding.
[]![Navigating to the Images page ](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Create-Instance-Compute-Engine-Navigation.png)
[]![Filtering for an image in the Images page of the GCP Management Console](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-gcp/gcp-filtering-image-create-instance-pse.png)
[]![Viewing the Create an instance page](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Create-an-instance-window2.png)
[]![Selecting the machine type when creating an instance](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Create-instance-Machine-type.png)
[]![Verifying the VM instance after its creation in the GCP Management Console](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Create-instance-verify-VM-image2.png)
[]![Viewing the Secret Manager page](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-secret-manager-page.png)
[]![Viewing the Create secret window](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-pkey-secret-manager-create-secret-window.png)
[]To create an SSH key pair:
-
Open the Private Service Edge terminal, and use the following `ssh-keygen` command with the `-c` flag to create a new SSH key pair:
`ssh-keygen -t rsa -f ~/.ssh/gcp_key -C admin -b 2048`
To learn more, refer to the [Google Cloud documention](https://cloud.google.com/compute/docs/connect/create-ssh-keys).
-
In the **Compute Engine** settings, click **Metadata **> **SSH Keys**.
[See image.](#GCP-Compute-Engine-Settings)
- Click **Edit**.
-
Click **Add Item**.
[See image.](#GCP-Compute-Engine-Upload-SSH)
- Upload the SSH public key to the GCP Management Console.
- Click **Save**.
[]![Accessing the SSH Keys page in the GCP Management Console](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Compute-Engine-SSH-Keys.png)
[]![Uploading the SSH key in the GCP Management Console](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Compute-Engine-Upload-SSH-Key.png)
- []Stop running the zpa-service-edge service using the following command. If the provisioning key is not detected when the Private Service Edge first started, then the Private Service Edge is in a sleep cycle and looks for the key again every 24 hours.
sudo systemctl stop zpa-service-edge
- Create a provisioning key file with 644 permissions at /opt/zscaler/var/service-edge/provision_key. For example:
sudo touch /opt/zscaler/var/service-edge/provision_key
sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
sudo vi /opt/zscaler/var/service-edge/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<Private Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-service-edge service using the following command.
sudo systemctl start zpa-service-edge
- Stop and disable the sshd using the following commands.
sudo systemctl stop sshd
sudo systemctl disable sshd
- []Log in to the Private Service Edge console using your GCP Private Key.
- Using a standard SSH client, enter the following command to connect to the GCP instance:
ssh -i <GCP Private Key> admin@<Private Service Edge Private Hostname or IP Address>
In the following example, the private key for the GCP instance is gcp_key and the Private Service Edge IP address is 172.31.255.255:
ssh admin@172.31.255.255-i ~/.ssh/gcp_key
-
When you are asked if you want to continue connecting, enter yes.
![Connecting to gcp_key](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-google-cloud-platform/GCP-SSH-Private-Key.png)
[]To create a firewall rule:
- Log in to the GCP Management Console.
- In the left-side navigation, click **Network Security**.
-
Go to **Cloud NGFW** > **Firewall Policies**.
[See image.](#Firewall-Policies)
The **Firewall policies** window appears.
-
In the **Firewall policies** window, click **Create firewall rule**.
The **Create a firewall rule **window appears.
-
In the **Create a firewall rule **window:
- **Name**: Enter a name for the firewall rule.
- **Network**: Select the network to which the firewall rule applies.
- **Direction of traffic**: Select either **Ingress** (receiving traffic) or **Egress **(sending traffic).
- **Action on match**: Select whether the action permits (**Allow)** or blocks (**Deny**) the connection.
- **Targets**: Select the targets to which the firewall rule applies from the drop-down menu (**All instances in the network**, **Specific target tags**, or **Specified service account**).
- **Source filter**: Select a source filter range (**IPv4 ranges**, **IPv6 ranges**, or **Source tags**). Enter the IP address range in the **Source filter ranges** text box that appears after selecting a source filter range using the network IP/subnet format. An example IPv4 range would be `0.0.0.0/0`.
- **Protocols and ports**: Select **Specified protocols and ports** and specify the protocol (**TCP**, **UDP**, **Other**) and ports. The Private Service Edge must have ingress and egress traffic directions on TCP port 22 for SSH, and egress traffic directions on TCP port 443 to reach ZPA.
[See image.](#Create-firewall-rule-window)
- Click **Create**.
If necessary, egress traffic directions can be restricted to ZPA hosts and ports. For details regarding required IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
[]This procedure describes how you can deploy ZPA in GCP through Launch Templates and Auto Scaling configurations to create a scalable and supportable infrastructure.
To deploy an Private Service Edge on GCP using a Launch Template with Auto Scaling:
- Log in to the GCP Management Console.
- Click **Compute Engine**.
- In the left-side navigation, go to **Instance Groups** > **Instance Groups**.
- Click **Create Instance Group**.
[See image.](#deploy2-CreateInstanceGrp1)
The **Create Instance Group** window appears.
- In the **Create Instance Group** window:
- Enter an **Instance group name**.
- Enter a **Description**.
- On the **Instance template **tab, click the drop-down menu and select the existing instance template, or click **Create a New Instance Template **to create a new instance template.
- [See instructions.](#auto-scaling-new-instance-template)
- Select the region and zone from the drop-down menu.
- On the **Autoscaling** tab:
- Select a minimum and maximum number of instances as 2 and 4 respectively.
- Select **CPU utilization **for the **Signal type **drop-down menu.
- Enter `80` in the **Target CPU utilization** field.
- Enter `300` in the **Initialization period** field.
- Click **Create**.
[]![Navigating to Firewall policies in the GCP Management Console](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Firewall-Policies.png)
[]![Viewing the Create firewall rule window in the GCP Management Console](/downloads/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms/app-connector-deployment-guide-gcp/GCP-Create-firewall-rule-window.png)
- []Enter the instance template **Name**.
- Enter the **Machine configuration **details.
-
Under **Boot disk**, click **Change**.
[See image.](#instance-templace-bootDisk)
- Select the customized zpa-service-edge image that was taken from GCP Marketplace. To learn more, see [ZPA - GCP Marketplace](https://console.cloud.google.com/marketplace/product/zpa-gcp-marketplace/zscaler-private-access-service-edge).
- For **Access scope**:
- Select **Allow full access to all cloud APIs** to access the provisioning key that is present in the secret manager.
- Expand the **Advanced options **section, and then expand the **Management **section.
- In the **Management **section:
- Provide a description in the **Description **field.
-
Add the following script in the **Automation** field.
`#!/usr/bin/bash
# Sleep to allow the system to initialize
sleep 15
curl -O https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-cli-linux-x86_64.tar.gz
tar -xf google-cloud-cli-linux-x86_64.tar.gz
export PATH=$PATH:$PWD
sudo ./google-cloud-sdk/install.sh
# Install Private Service Edge packages
yum install -y zpa-service-edge
# Stop the Private Service edge service which was auto-started at boot time
systemctl stop zpa-service-edge
# Fetch the secret from Secret Manager
SECRET_NAME="Provision_key"
SECRET_VALUE=$(gcloud secrets versions access latest --secret="$SECRET_NAME")
# Use the secret in your application or script
echo "The secret value is: $SECRET_VALUE"
# Example: Export the secret as an environment variable
export MY_SECRET="$SECRET_VALUE"
# Create a file from the Private service edge provisioning key created in the ZPA Admin Portal
# Make sure that the provisioning key is between double quotes
echo "$SECRET_VALUE" > /opt/zscaler/var/service-edge/provision_key
chmod 644 /opt/zscaler/var/service-edge/provision_key
# Start the private service edge service to enroll it in the ZPA cloud
systemctl start zpa-service-edge
# Wait for the private service edge to download the latest build
sleep 60
# Stop and then start the private servic eedge for the latest build
systemctl stop zpa-service-edge
systemctl start zpa-service-edge
sleep 20
# Run a yum update to apply the latest patches
yum update -y`
[See image.](#auto-scaling-instance-template-management)
- Click **Create**.
[]![Selecting the Boot disk for the Auto Scaling Launch Template](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/private-service-edge-deployment-guide-google-cloud-platform/gcp-instance-deploy-launch-template-boot-disk1.png)
[]
[]![Creating the Instance Group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/zpa-private-service-edge-deployment-guide-google-cloud-platform/zpa-pse-gcp-deployment-guide-deployment2-create-instance-group.png)
[]
Before you deploy the ZPA Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a ZPA Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a ZPA Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a ZPA Private Service Edge](#Interfaces)
- [Configure Static Routing for a ZPA Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a ZPA Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a ZPA Private Service Edge](#NTP)
- [Configure a ZPA Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based ZPA Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a ZPA Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based ZPA Private Service Edge.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the connection profile using the following format: `<profile name>`` connection.id ``<new connection name>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN
- Review the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Edit the profile using a static IP address and a default gateway with the following format: `<connection ID>`` ipv4.method manual ipv4.addresses ``<IP addresses> ``ipv4.gateway ``<gateway IP> ``ipv4.dns ``<DNS IP> ``ipv4.dns-search ``<sub.subdomain.domain.com subdomain.domain.com domain.com>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com
- To apply the changes, bring the connection connection ID back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up LAN
- Verify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Verify the default gateway.
[admin@zpa-service-edge ~]$ ip route show default
- Verify the DNS settings.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]If necessary, additional changes can be made to interfaces by configuring new ones using `nmcli connection add con-name` or by renaming existing ones using `nmcli connection modify`.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- View the current connection profiles.
[admin@zpa-service-edge ~]$ nmcli connection show
- Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto
For static, modify the connection profile and identify the IP addresses and gateway using the following format: `<profile name>`` ipv4.method manual ipv4.addresses ``<address>`` ipv4.gateway ``<address>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254
- To apply the changes, bring the connection profile back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Reverify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Reverify the new connection.
[admin@zpa-service-edge ~]$ nmcli connection show
[]To add static routes to the interface control files for a ZPA Private Service Edge:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the static route for an existing Ethernet connection using the following format: `<profile name>`` ipv4.routes ``<address and gateway>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes "192.168.2.241/24 10.10.10.1"
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1" [admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the new route is added.
[admin@zpa-service-edge ~]$ ip route
[]DNS resolution is critical for the successful operation of the ZPA Private Service Edge. ZPA Private Service Edges must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the DNS settings using the following format: `<profile name> ``ipv4.dns`` <nameserver IP>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]To configure ZPA Private Service Edges to use internal NTP servers:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the `/etc/chrony.conf` file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the ZPA Private Service Edge to work through that proxy. The following procedure allows the ZPA Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the ZPA Private Service Edge to work through an explicit proxy:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Create a file named `/opt/zscaler/var/service-edge/proxy`. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: `<Proxy Hostname or IP Address>``:``<Proxy Port>` (e.g., `192.0.2.0:0`).
- To apply the changes, restart the ZPA Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The ZPA Private Service Edge will attempt to create a TLS session through the proxy specified previously.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation. To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
[]
This information applies to Security Technical Implementation Guide (STIG) images that were released on November 24, 2024 and December 12, 2024. STIG images released after these dates are not affected.
If you're using an affected STIG image, passwords automatically expire every 60 days for Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure, or 95 days (60 days + a 35-day grace period) for VMware.
If the password expires without changing it or disabling expiration, admin access to a ZPA Private Service Edge is no longer available. When admin access expires, the only recovery method is to deploy a new ZPA Private Service Edge.
[]STIG-hardened prebuilt Private Service Edge images affected by password expiration were released on:
- AWS and GCP: November 24, 2024
- Azure and VMware: December 12, 2024
To verify if an image is STIG-hardened:
- Go to the Private Service Edges page in the ZPA Admin Portal.
- Expand the row for a Private Service Edge in the table.
- Under **Private Service Edge Host Platform**, if you see `ZSIVersion: 2024.11` or `ZSIVersion: 2024.12` for the ZSIVersion, the image is STIG-hardened.
[See image.](#StigImage)
Zscaler recommends using one of these methods for passwords:
- [Disable or Set a Password for AWS, GCP, and Azure.](#StigMarketplace)
- [Disable or Set a Password for VMware.](#StigOVAs)
- []Disable the password expiration:
-
Enter the following command (replacing `admin` with your admin username):
``[admin@zpa-service-edge ~]$ sudo chage -M -1 adm`in`
-
Verify that the password is set to never expire.
``[admin@zpa-service-edge ~]$ sudo chage -l adm`in
`Last password change                               : Feb 18, 20`25
`Password expires                                   : never`
`Password inactive                                  : never`
`Account expires                                    : never`
Minimum number of days between password change     : 1
Maximum number of days between password change     : -1
Number of days of warning before password expires  : 7`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 days.
-
[]Disable the password expiration by entering the following command (replacing `admin` with your admin username):
`$ sudo chage -M -1 admin`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 or 95 days.
[]
Example STIG-hardened image with `ZSIVersion: 2024.11.`
![Verify STIG-hardened image on a ZPA Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/app-connector-deployment-guide-amazon-web-services-draft-doc-56293/zpa-pse-stig-image-verification-nov2024.png)