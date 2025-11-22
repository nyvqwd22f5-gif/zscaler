# Private Service Edge Deployment Guide for Google Cloud Platform
Source: https://help.zscaler.com/unified/private-service-edge-deployment-guide-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1517106.pdf

This deployment guide provides information on prerequisites, how to deploy an Private Service Edge on Google Cloud Platform (GCP), and post-deployment verification checks. For general information regarding Private Service Edge deployment for Private Applications, see [About Deploying Private Service Edges for Private Applications](/unified/about-deploying-private-service-edges-private-applications).
- [Step 1: Make Sure You Have Met All Private Service Edge Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the Private Service Edge on GCP](#deploy)
- [Step 3: Configure the Networking for the Deployed Private Service Edge](#networking)
- Step 4: Verify that the deployed Private Service Edge is [running and healthy](/unified/managing-deployed-private-service-edges-private-applications#Status). Also, check that it is [meeting your sizing requirements](/unified/managing-deployed-private-service-edges-private-applications#VerifySizing).
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your Private Service Edge console admin credentials or performing system software updates). To learn more, see [Managing Deployed Private Service Edges for Private Applications](/unified/managing-deployed-private-service-edges-private-applications).
After Private Service Edges are deployed, you can:
- [Create application segments](/unified/configuring-defined-application-segments) and [access policies](/unified/about-policies) to pass application traffic. For example, to test your configuration, consider setting up a simple application segment that allows SSH access to your Private Service Edges.
- [Configure a log receiver](/unified/configuring-log-receiver) for your Private Service Edges to receive information about your Private Service Edges or users via the [Log Streaming Service (LSS)](/unified/about-log-streaming-service).
[]
Before deploying a Private Service Edge on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
Each Private Service Edge supports up to 500 Mbps of throughput. Use the information on this page to determine the Private Service Edge sizing requirements for your deployment. For example, with a 1 Gbps aggregate (i.e., total inbound and outbound) connection, you would need to deploy 2 to 3 Private Service Edges.
- [Private Service Edge Specifications and Sizing Requirements](#SpecsSizing)
- [Private Service Edge Platform Prerequisites](#PlatformPrereqs)
- [Private Service Edge Security Guidance and Firewall Requirements](#Firewall)
- [Private Service Edge Zscaler Client Connector Requirements](#ClientConnector)
After you have met all of the prerequisites, you can deploy the Private Service Edge on a supported platform.
[]The following specifications are recommended by Zscaler for up to 500 Mbps throughput for each Private Service Edge.
- Memory (RAM) and vCPU (for virtual machines) or CPU (for physical machines) cores:
| Active Users | Memory | vCPU or CPU Cores |
| ------------ | ------ | ----------------- |
| Up to 2,000 | 8 GB (10 GB with ZDX) | 4 vCPUs or 4 CPUs |
| Up to 4,000 | 16 GB (18 GB with ZDX) | 8 vCPUs or 8 CPUs |
| Up to 10,000 | 32 GB (34 GB with ZDX) | 16 vCPUs or 16 CPUs |
To learn more, see the [Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
Depending on your deployment use case, each Private Service Edge must be able to accept incoming connections from either internal or external sources or both internal and external sources on TCP port 443. For example, if you enable for both remote and office users, each Private Service Edge needs to accept incoming connections from both internal and external endpoints running Zscaler Client Connector.
Private Service Edges are reachable over the internet for remote users in a disaster recovery scenario, or when the Private Service Edge is the closest Service Edge.
In the scenario where a Private Service Edge is deployed behind a firewall, the firewall performs destination network address translation (DNAT) for the Private Service Edge's private IP address. In this case, the flow of traffic is from Zscaler Client Connector to the Private Service Edge. The firewall then translates the destination public IP address that Zscaler Client Connector connects to on the private IP address of the Private Service Edge. The firewall advertises a public IP address on the internet. It is necessary to configure the public IP address advertised by the firewall as a [publish IP](/unified/about-private-service-edges-private-applications) of the respective Private Service Edge. In the case of disaster recovery, you must add this IP address as the A record for that Private Service Edge.
Your firewalls must be configured to let the Private Service Edge establish outbound connections to the IP addresses of the Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors.
The following conditions apply to each Private Service Edge that is placed behind a firewall:
- They must accept incoming connections from internal sources and remote users and on-premises users (as applicable and dependent on your use case) on TCP port 443.
- They must have a unique private IP address that can be reached over the internal network.
After a Private Service Edge is enrolled, an outbound TLS tunnel over TCP port 443 is established to the cloud infrastructure. This communication channel provides various functionality and includes the following traffic:
- Periodic keepalives to the Public Service Edge
- Policy configuration download
- Private Service Edge software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional Private Service Edges at any time, using the same provisioning key to add them to the existing Private Service Edge group, while ensuring network and internet connectivity. Private Service Edges are designed to scale elastically. You can deploy additional Private Service Edges in the same Private Service Edge group to increase the total throughput as required by your deployment. Zscaler recommends that you deploy Private Service Edges in pairs (N+1), where N is the number of Private Service Edges as per the sizing requirements. To learn more, see [About Deploying Private Service Edges](/unified/about-deploying-private-service-edges-private-applications) and [Supported Platforms for Private Service Edges](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
After deployment, ensure that the Private Service Edge meets your sizing requirements. To learn more, see [Verify Private Service Edge Sizing Specifications](/unified/managing-deployed-private-service-edges-private-applications). If disk space fills up in the Private Service Edge, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance#diskspace_archive).
Understanding Private Service Edge Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). Each Private Service Edge supports up to 500 Mbps throughput. Private Service Edges communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
Zscaler recommends that you check your existing VPN solution's average and peak throughput when determining your sizing requirements. Be sure to only account for user or client VPN traffic and not any site-to-site tunnel traffic.
For example, if you have a 1 Gbps aggregate (i.e., total inbound and outbound) connection in your data center, you can use the 500 Mbps throughput guideline to make sure you have enough Private Service Edges to support the connection and have room for failover (N+1). In this case, you would need to deploy 2 to 3 Private Service Edges to support the 1 Gbps connection.
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, AppProtection, or ZDX enabled. Make sure that you have enough Private Service Edges to support the connection and room for failover (N+1).
To horizontally scale your deployment, Zscaler recommends that you have more Private Service Edges with lower specifications rather than fewer Private Service Edges with higher specifications. For example, if you have fewer Private Service Edges with higher specifications and one fails, you could adversely affect more user application traffic or sessions than a smaller Private Service Edge that fails.
[]Before you begin any procedures within the [Private Service Edge Deployment Guide](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for your platform, make sure that you have met all of the following prerequisites:
- Intel x86_64/AMD64 based architecture
- systemd
- Root or sudo access to the system in order to configure a new package repository and install packages
- DNS resolution and network access
- A [Private Service Edge provisioning key](/unified/about-private-service-edge-provisioning-keys-private-applications)
- A static MAC address
[]Private Service Edges can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Operating System Security
The Private Service Edge VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the Private Service Edge and its VMs to ensure that memory growths do not have an impact on the Private Service Edge performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [Private Service Edge Deployment Guides](/unified/networking/private-applications/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms) for the platform you are using.
Private and public cloud VM images provided by Zscaler are essentially unmodified operating systems (currently based on CentOS 7.x). You can patch these systems when necessary by using the standard yum OS update mechanism. To learn more, see [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications).
Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting Private Service Edges using firewall policies. Additionally, if you've installed the Private Service Edge as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Private Service Edge in such an environment as long as the Private Service Edge is able to reach all Zscaler data centers containing Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
Firewall Requirements and Interoperability Guidelines
All of the Zscaler data centers containing Public Service Edges must be allowed. A partial firewall configuration will result in connectivity problems for end users. Zscaler’s policy is to provide a 90 day notice for activating additional IP CIDR ranges, in order to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Private Service Edge will not function if the TLS certificates presented by the Public Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service, so ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Private Service Edge. This is necessary for allowing the Private Service Edge to resolve and reach Public Service Edges. Private Service Edge requires your firewall configuration to accept the incoming connections from the users. Also, if you need to allowlist additional Zscaler IP addresses, refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). It may be possible to allowlist based on Zscaler cloud hostnames instead of IP addresses.
[]Private Service Edges require that the [Zscaler Client Connector](/z-app) be at least on version 2.1.2.
[]For GCP, you must deploy Private Service Edges in your Virtual Private Clouds (VPCs). For each VPC there must be at least a pair of Private Service Edges deployed for resilience and scalability. The Private Service Edges should be deployed across regions and zones to ensure continuity of service in the event of an incident. Zscaler automatically load balances across the Private Service Edges. Additional capacity can be handled by adding additional Private Service Edges into each region and zone.
Private Service Edges should be configured with the right access to applications in the VPC. The VPC configuration should permit the Private Service Edges to connect to the application servers on the appropriate TCP/UDP ports, and enable ICMP reachability and DNS resolution to the applications. The Private Service Edge's VPC configuration should permit outbound access to the internet to connect to the Zscaler cloud. Zscaler recommends deploying the Private Service Edges on a private subnet which connects to the internet through a NAT gateway.
The following prerequisites must be met before deploying the Private Service Edge instance for Private Applications:
- [Installing the Google Cloud CLI](#Install-Google-Cloud-CLI)
- [Creating a Firewall Rule](#Firewall-Rule)
You can deploy the image on GCP using one of the following methods:
- [Deploying a Private Service Edge using the Instance wizard](#Deployment1)
- [Deploying a Private Service Edge using a Launch Template and Auto Scaling (Advanced Deployment)](#Deployment2)
[]To install the Google Cloud CLI, refer to the [Google Cloud documentation](https://cloud.google.com/sdk/docs/install).
[]This procedure describes how to deploy in GCP for Private Applications using the Instance wizard, and assumes that you have created an SSH key pair and an image from a .vmdk (virtual disk).
- [Create an SSH key pair](#PSE-Instance-SSH-Key)
- [Launch the VM in GCP Marketplace](#LaunchVM)
After you create an SSH key pair and an image from the virtual disk, [complete the following steps to deploy using the Instance wizard.](#Deploy-PSE-Instance)
[]To launch the VM in GCP Marketplace:
- Go to [Private Applications - GCP Marketplace](https://console.cloud.google.com/marketplace/product/zpa-gcp-marketplace/zscaler-private-access-service-edge).
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
- **Secret value**: Enter the value for the secret (e.g., `<your provisioning key>`). You can acquire a provisioning key when creating a Private Service Edge for Private Applications in the Admin Portal. To learn more, see [About Private Service Edges Provisioning Keys for Private Applications](/unified/about-private-service-edge-provisioning-keys-private-applications) and [Configuring Private Service Edges for Private Applications](/unified/configuring-private-service-edges-private-applications).
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
To learn more, see [Managing Deployed Private Service Edges for Private Applications](/unified/managing-deployed-private-service-edges-private-applications).
- Zscaler highly recommends [updating the Private Service Edge system software](/unified/managing-deployed-private-service-edges-private-applications) before proceeding.
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
To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/compute/docs/connect/create-ssh-keys).
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
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
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
- **Protocols and ports**: Select **Specified protocols and ports** and specify the protocol (**TCP**, **UDP**, **Other**) and ports. The Private Service Edge must have ingress and egress traffic directions on TCP port 22 for SSH, and egress traffic directions on TCP port 443 to reach Private Applications.
[See image.](#Create-firewall-rule-window)
- Click **Create**.
If necessary, egress traffic directions can be restricted to hosts and ports for Private Applications. For details regarding required IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
[]This procedure describes how you can deploy in GCP for Private Applications through Launch Templates and Auto Scaling configurations to create a scalable and supportable infrastructure.
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
- On the **Instance template **tab, click the drop-down menu and select the existing instance template, or click **Create a New Instance Template **to create a new instance template. If you click **Create a New Instance Template**, [click here for more instructions.](#auto-scaling-new-instance-template)
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
- Under **Boot disk**, click **Change**.
- Select the customized zpa-service-edge.
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
- Click **Create**.
[]![Creating the Instance Group](/downloads/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms/zpa-private-service-edge-deployment-guide-google-cloud-platform/zpa-pse-gcp-deployment-guide-deployment2-create-instance-group.png)
[]
Before you deploy the Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a Private Service Edge](#Interfaces)
- [Configure Static Routing for a Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](#NTP)
- [Configure a Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/ifcfg-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
In the following example, the edited file is using a Private Service Edge IP address of 192.168.2.100, highlighted in green:
DEVICE="eth0"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- Edit the /etc/sysconfig/network file and configure the default gateway. For example:
NETWORKING=yes
GATEWAY=192.168.2.254
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]If necessary, additional interfaces can be configured by creating additional files in /etc/sysconfig/network-scripts.
- Log in to the Private Service Edge console using your admin credentials.
- Copy the /etc/sysconfig/network-scripts/ifcfg-eth0 file to /etc/sysconfig/network-scripts/ifcfg-eth1. For example:
[admin@zpa-service-edge ~]$ sudo cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth1
- Edit the new /etc/sysconfig/network-scripts/ifcfg-eth1 file with the network configuration information required for the interface. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth1
The content within the new file should be similar to the following:
DEVICE="eth1"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To add static routes to the interface control files for a Private Service Edge:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/route-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/sysconfig/network-scripts/route-eth0
Add additional static routes using the following format: <CIDR> via <GATEWAY> dev <INTERFACE>. For example:
192.168.0.0/16 via 192.0.2.1 dev eth0
172.16.0.0/12 via 192.0.2.1 dev eth0
10.0.0.0/8 via 192.0.2.2 dev eth0
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]DNS resolution is critical for the successful operation of the Private Service Edge. Private Service Edges must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/resolv.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/resolv.conf
Replace the example nameserver IP addresses and search domains with your company-specific configuration. For example:
nameserver 8.34.34.34
nameserver 8.35.35.35
search myexampledomain.com
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To configure Private Service Edges to use internal NTP servers:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the Private Service Edge to work through that proxy. The following procedure allows the Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the Private Service Edge to work through an explicit proxy:
- Log in to the Private Service Edge console using your admin credentials.
- Create a file named, /opt/zscaler/var/service-edge/proxy. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: <Proxy Hostname or IP Address>:<Proxy Port> (e.g., 192.0.2.0:0).
- To apply the changes, restart the Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The Private Service Edge will attempt to create a TLS session through the proxy specified in step 2.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.