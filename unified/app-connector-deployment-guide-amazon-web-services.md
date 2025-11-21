# App Connector Deployment Guide for Amazon Web Services
Source: https://help.zscaler.com/unified/app-connector-deployment-guide-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1496131.pdf

This deployment guide provides information on prerequisites, how to deploy an App Connector on Amazon Web Services (AWS), and post-deployment verification checks. For general information regarding App Connector deployment for Private Applications, see [About Deploying App Connectors](/unified/about-deploying-app-connectors).
To learn more about Private Applications for AWS, see the [Solution Brief](https://www.zscaler.com/resources/solution-briefs/zscaler-private-access-and-amazon-web-services-partner.pdf).
- [Step 1: Make Sure You Have Met All App Connector Deployment Prerequisites](#Prereqs)
- [Step 2: Deploy the App Connector on AWS](#deploy)
- [Step 3: Configure the Networking for the Deployed App Connector](#networking)
- Step 4: Verify that the deployed App Connector is [running and healthy](/zpa/managing-deployed-connectors#Status). Also, check that it is [meeting your sizing requirements](/unified/managing-deployed-app-connectors#VerifySizing).
After you have verified your deployment, you can perform additional tasks to maintain the system (i.e., changing your App Connector console admin credentials or performing system software updates). To learn more, see [Managing Deployed App Connectors](/unified/managing-deployed-app-connectors).
After App Connectors are deployed, you can:
- [Create application segments](/unified/configuring-defined-application-segments) and [access policies](/unified/about-access-policy) to pass application traffic. For example, to test your configuration, consider setting up a simple application segment that allows SSH access to your App Connectors.
- [Configure a log receiver](/unified/configuring-log-receiver) for your App Connectors to receive information about your App Connectors or users via the [Log Streaming Service (LSS)](/unified/about-log-streaming-service).
[]
Before deploying a ZPA App Connector on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- [App Connector Specifications and Sizing Requirements](#SpecsAndSizing)
- [App Connector Platform Prerequisites](#PlatformPrereqs)
- [App Connector Security Guidance and Firewall Requirements](#SecurityAndFirewallReqs)
After you have met all the prerequisites, you can deploy the App Connector on a supported platform.
[]The following specifications are recommended by Zscaler for each ZPA App Connector:
- Memory: 4 GB RAM
For Zscaler Digital Experience (ZDX) deployments, Zscaler recommends App Connectors to have 8 GB of RAM.
- CPU:
- 2 CPU cores (Xeon E5 class) for physical machines without hyperthreading
- 4 CPU cores (Xeon E5 class) for virtual machines (VMs) with hyperthreading
- Both Amazon Web Services (AWS) and Google Cloud Platform (GCP) require a minimum of 4 CPU cores due to hyperthreading
- To deploy an App Connector on AWS, Zscaler recommends using t3.xlarge (for non-production or low traffic App Connectors) or m5a.xlarge (for production or high traffic App Connectors)
- To deploy an App Connector on GCP, Zscaler recommends using a Linux RPM on n2-standard-4 or n2-highcpu-4
- Azure VMs older than V3 require 2 CPU cores, while VMs V3 and later require 4 CPU cores due to hyperthreading
- To deploy an App Connector on Azure, Zscaler recommends using Standard_F4s_v2 or Standard_D4s_v3 or later
To enable AppProtection using the default AppProtection profile provided by Zscaler, we recommend that your App Connectors have at least 8 CPU cores and 8 GB of memory. Ensure that your App Connectors are less than 40% for peak memory utilization and peak CPU utilization. If your CPU or memory utilization is above the suggested maximum, you need to add App Connectors to reach the maximum peak of 40% CPU and memory without AppProtection enabled. This rule also applies if you are using a smaller VM (4 CPUs, 4 GB). Your App Connector throughput might be 100 to 200 Mbps depending on App Connector sizing when using AppProtection. Monitor your App Connectors by going to the [App Connector dashboard](/zpa/pselabel/viewing-app-connectors-dashboard).
The AppProtection recommendations are based on a mix of web traffic, 85% GET requests, and 15% POST and payload and response sizes of 32 KB. Smaller payload and response sizes might require less App Connector resources and result in higher throughput.
For ZDX deployments, Zscaler recommends App Connectors to have 4 CPU cores.
Using the [PassMark Software Pty Ltd](https://www.cpubenchmark.net/cpu_list.php) benchmark to verify the CPU Mark score, Zscaler recommends using a minimum CPU benchmark score of 2640 when choosing a CPU processor. The Intel Advanced Encryption Standard New Instructions (AES-NI) instruction set must also be enabled on the CPU processor.
To learn more, see the [App Connector Deployment Guide](/zpa/pselabel/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform.
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
For VMware platform deployment, the default configuration to allow the host to dynamically allocate VM resources is not recommended. Configure the VM setting to reserve the following memory and CPU allocations:
- Memory: 8 GB RAM
- CPU: total CPU GHz (the number of cores (2 or 4 cores) multiplied by the GHz per core)
To learn more, refer to the [VMware documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-8B88D3D8-E9D9-4C05-A065-B3DE1FFFB401.html).
Using these specifications, each App Connector supports up to 500 Mbps of throughput. To learn more, see [Understanding App Connector Throughput](/zpa/pselabel/connector-deployment-prerequisites#ConnectorThroughput) in this article. Based on Zscaler's recommendations, determine the App Connector sizing requirements for your deployment. If disk space fills up in the App Connector, Zscaler recommends archiving files and creating more log space. To learn more, see [Monitoring App Connector Performance](/zpa/pselabel/monitoring-connector-performance#diskspace_archive).
After an App Connector is enrolled, an outbound TLS tunnel over port 443 is established to the ZPA cloud infrastructure. This communication channel provides various functionality and utilizes minimal bandwidth, which includes the following traffic:
- Periodic keepalives to ZPA Public Service Edges or ZPA Private Service Edges
- Application learning
- Application health reporting
- App Connector software upgrades (upgrades are completed based on a weekly schedule)
You can deploy additional App Connectors at any time, using the same provisioning key to add them to the [existing App Connector Group](/zpa/pselabel/about-connectorgroups), while ensuring network and internet connectivity. App Connectors are designed to scale elastically. You can deploy additional App Connectors in the same App Connector Group to increase the total throughput as required by your deployment. Zscaler recommends you have a minimum of two healthy App Connectors to always ensure an available path. To learn more, see [About Deploying App Connectors](/zpa/pselabel/about-deploying-connectors) and [Supported Platforms for App Connectors](/zpa/pselabel/app-connector-management/app-connector-deployment-guides-supported-platforms).
After deployment, ensure that the App Connector meets your sizing requirements. To learn more, see [Verify App Connector Sizing Requirements](/zpa/pselabel/managing-deployed-connectors#VerifySizing).
[]Understanding App Connector Throughput
Throughput numbers are aggregate (i.e., total inbound and outbound). The following best practices apply regarding App Connector throughput sizing:
- Check your existing VPN solution's average and peak throughput. Be sure to only account for user/client VPN traffic and not any site-to-site tunnel traffic.
- App Connectors communicate over the provided (default) gateway, which is most likely your ISP WAN broadband connection.
- Using double encryption affects throughput. However, the effect varies based on the number of applications that are enabled for double encryption.
So, if you have a 1 Gbps connection (aggregate) in your data center, you can use the throughput guidelines in the following table to make sure that you have enough App Connectors to support the connection and room for failover (N+1). For example, with a 1 Gbps connection, you would need to deploy 2 to 3 App Connectors if your applications are not using double encryption, but 4 to 6 App Connectors if they are. To learn more, see [Understanding Double Encryption](/zpa/pselabel/understanding-double-encryption).
The following throughput guidelines apply based upon the recommended App Connector specifications:
| % of Applications with Double Encryption | Per App Connector Throughput |
| ---------------------------------------- | ---------------------------- |
| 0% | 500 Mbps |
| 25% | 437.5 Mbps |
| 50% | 375 Mbps |
| 75% | 312.5 Mbps |
| 100% | 250 Mbps |
It is possible to increase App Connector throughput up to 1 Gbps per App Connector by running the App Connector on hardware with more memory and CPUs along with increased network link speed. If you have a 10 Gbps connection (aggregate) in your data center, and you want to increase the App Connector throughput up to 1 Gbps per App Connector, you can increase the underlying VM spec as follows:
- 8 vCPU cores for virtual machines or 4 CPU cores for physical machines
- 8 GB RAM
The exact throughput can vary and depends on other network factors such as your internal network setup, latency, and whether you have double encryption, App Protection, and/or ZDX enabled. Make sure that you have enough App Connectors to support the connection and room for failover (N+1).
Zscaler recommends that you have more App Connectors with lower specifications rather than fewer App Connectors with higher specifications to horizontally scale your deployment. For example, if you have fewer App Connectors with higher specifications and one fails, you could adversely affect more user application traffic/sessions than a smaller App Connector that fails.
[]Before you begin any procedures within the [App Connector Deployment Guide](/zpa/pselabel/app-connector-management/app-connector-deployment-guides-supported-platforms) for your platform, make sure that you have the following:
-
Intel x86_64/AMD64-based architecture
-
systemd
-
Root or sudo access to the system to configure a new package repository and install packages
-
DNS resolution and network access
-
An App Connector [provisioning key](/zpa/pselabel/about-connectorprovisioning) obtained from the ZPA Admin Portal
-
A static MAC address
[]App Connectors can be deployed in different ways (as private cloud VMs, public cloud VMs, or OS packages), so the security features for each deployment type are slightly different.
Zscaler recommends treating access to App Connectors as privileged, so only authorized personnel can access an App Connector's console. By limiting access, there is the added benefit of shielding inter-process communication within the App Connector from attack.
Operating System Security
The App Connector VMs distributed by Zscaler for use in private clouds are configured without any remotely accessible services running. Swap partitions are disabled on the App Connector VMs to ensure that memory growth does not have an impact on App Connector performance. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. To learn more, see the [App Connector Deployment Guide](/zpa/pselabel/app-connector-management/app-connector-deployment-guides-supported-platforms) for the platform you're using.
ZPA provides Security Technical Implementation Guide (STIG) VM images for AWS, GCP, Microsoft Azure, Nutanix, and VMware by default. To learn more, see [App Connector Software by Platform](/zpa/pselabel/zpa-app-connector-software-by-platform). The remaining private and public cloud VM images provided by Zscaler are configured with minimal listening services to reduce the remotely exploitable attack surface. Because these are essentially unmodified operating systems (currently based on RHEL 9.x), you can patch these systems when necessary by using the standard yum OS update mechanism. Zscaler recommends that you harden the operating system, including the `sshd-config` file, on the VM images in accordance with your organization's security standards after initial deployment. To learn more, see [Update App Connector System Software](/zpa/pselabel/managing-deployed-connectors#Updating).
To learn more about support for CentOS 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
Because vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends either patching or using new Zscaler-distributed VM images on a regular basis, or protecting App Connectors using firewall policies. Additionally, if you've installed the App Connector as a package, Zscaler recommends that you take similar precautions.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy an App Connector in such an environment as long as the App Connector is able to reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/pselabel/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All the Zscaler data centers containing ZPA Public Service Edges must be allowed. A partial firewall configuration can result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. App Connectors do not function if the TLS certificates presented by the ZPA Public Service Edges or ZPA Private Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable to maintain the integrity of the service. Ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the App Connector. This is necessary for allowing the App Connector to resolve and reach ZPA Public Service Edges or ZPA Private Service Edges. If you need to allowlist additional Zscaler IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/pselabel/what-my-cloud-name-zpa)
For ZPA integration with ZDX, App Connector firewall requirements must align with the respective ZDX configuration. You must configure the firewall to allow egress traffic on the TCP, UDP, and ICMP protocols. App Connectors must be able to egress traffic to port 443 for Zscaler Service Edge connections and the ports of all configured applications (i.e., ports that are configured in all application segments that are registered on the App Connector).
[]For AWS, you must deploy App Connectors in your Virtual Private Clouds (VPCs). For each VPC there should be a pair of App Connectors deployed for resilience and scalability. The App Connectors should be deployed across Availability Zones to ensure continuity of service in the event of an incident. Zscaler automatically load balances across the App Connectors. Additional capacity can be handled by adding additional App Connectors into each Availability Zone.
App Connectors should be in appropriate Security Groups to enable access to applications in the VPC. The Security Groups should permit the App Connectors to connect to the application servers on the appropriate TCP/UDP ports, and enable ICMP reachability and DNS resolution to the applications. The App Connectors' Security Group should permit outbound access to the internet to connect to the Zscaler cloud. There is no requirement for inbound connectivity to the App Connectors from the internet. Zscaler recommends deploying the App Connectors on a private subnet which connects to the internet through a NAT gateway.
[See image.](#AWS-Deployment-Diagram)
- [Deploying an App Connector using the Instance wizard](#Deployment1)
- [Deploying an App Connector using a Launch Template with Auto Scaling (Advanced Deployment)](#Deployment2)
[]This procedure describes how you can deploy Private Applications in AWS using the Instance wizard. If you require a more scalable solution, Zscaler recommends [deploying the App Connector using a Launch Template with Auto Scaling](/unified/app-connector-deployment-guide-amazon-web-services#Deployment2).
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances. It is also assumed that you already have a Security Group created and have edit access to it.
To deploy an App Connector on AWS using the Instance wizard:
- Log in to the AWS Management Console.
- Click **EC2**.
- On the **EC2 Dashboard** page, under the **Create Instance** section, click **Launch Instance**.
Within the EC2 Management Console, the instance wizard appears.
- In **Step 1: Choose an Amazon Machine Image (AMI)**, under **AWS Marketplace**, search for zscaler.
[See image.](#Step1_SearchAnAMI)
- When the **Zscaler Private Access App Connector** AMI appears, click **Select**.
- In **Step 2: Choose an Instance Type**, select an instance type that supports the App Connector's [sizing requirements](#Prereqs).
- Click **Next: Configure Instance Details**.
[See image.](#Step1_SelectSizing)
- In **Step 3: Configure Instance Details**:
- Choose suitable values for your VPC.
- For **Auto-assign Public IP**, choose **Enable**.
[See image.](#Step3_InstanceDetails)
- Click **Review and Launch**.
[See image.](#Step3_InstanceReview)
- In **Step 7: Review Instance Launch**, verify the instance configuration.
An App Connector only needs outbound access on TCP port 443. So, ensure that the Security Group is configured accordingly.
[See image.](#Step7_ReviewLaunch)
- Click **Launch** to power on the instance.
- Verify that the instance launched successfully and that the **Instance State** is **running**.
[See image.](#Step12_Running)
- Click **Connect**.
[See image.](#Step13_PemFileInfo)
In the **Connect To Your Instance** window that appears, take note of the private key name (i.e., a .pem file) and the public hostname or IP address for your instance. You need this information for step 14.
If the proper columns are shown, you can also see this information within the table on the **Instances** page.
- Update the Security Group associated to the App Connector to temporarily allow inbound access on port 22, then complete the following steps to connect to the instance. SSH access is required in order to configure the provisioning key for the App Connector.
- [See instructions.](#security)
- Apply the App Connector provisioning key.
- [See instructions.](#pkeyreal)
After the App Connector provisioning key is applied, be sure to verify that the deployed App Connector is [running and healthy](/unified/managing-deployed-app-connectors#Status).
- Zscaler highly recommends [updating the App Connector system software](/unified/managing-deployed-app-connectors#Updating) before proceeding.
- []Stop the running the connector service. If the provisioning key is not detected when the App Connector first started, then the App Connector is in a sleep cycle and looks for the key again every 24 hours.
[admin@zpa-connector ~]$ sudo systemctl stop zpa-connector
- Create a provisioning key file with 644 permissions, at /opt/zscaler/var/provision_key. For example:
[admin@zpa-connector ~]$ sudo touch /opt/zscaler/var/provision_key
[admin@zpa-connector ~]$ sudo chmod 644 /opt/zscaler/var/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-connector ~]$ sudo vi /opt/zscaler/var/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key:
echo "<App Connector Provisioning Key>" | sudo tee /opt/zscaler/var/provision_key
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-connector ~]$ sudo cat /opt/zscaler/var/provision_key
The output should return the provisioning key you entered in the previous step.
- Start the zpa-connector service.
[admin@zpa-connector ~]$ sudo systemctl start zpa-connector
In AWS, be sure to disable inbound access on port 22 for the Security Group associated to the App Connector.
- []Log in to the App Connector console using your AWS Private Key.
AWS App Connectors do not support password-based authentication, so using default password-based credentials won't work as a login method. Only certificate-based authentication is allowed with AWS App Connectors. Log in using the AWS Private Key (i.e., a .pem file). SSH access is enabled by default on AWS App Connectors, so there is no need to enable the service manually.
- Using a standard SSH client, enter the following command to connect to the AWS instance:
ssh -i <AWS Private Key> admin@<App Connector Public Hostname or IP Address>
In the following example, the private key for the AWS instance is AWS.pem and the App Connector IP address is 35.160.130.25:
ssh -i AWS.pem admin@35.160.130.25
- When you are asked if you want to continue connecting, enter yes.
**![connect to aws.png](/downloads/zpa/documentation-knowledgebase/connectors/supported-platforms-connectors/connector-deployment-amazon-web-services-aws/m8twwuu8qfg8dyq_nkqkqslozmyftbqfu6gmhtirwdrk9mt91ogdfi9zlfjupuveh4bwoi9miv0m2lml2j05revie9l_vycnhsultzwvgbfhv79vhvlkpr_7emvf9u0ryigpdelx.png)
**
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-guide-amazon-web-services/zpa-awsdeploymentguide-step1.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-step2.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-step3.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-step3clickreview.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-step7.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-step12running.png)
[]![Amazon EC2 Management Console with Instance wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-awsdeploymentguide-connectinstance.png)
[]This procedure describes how you can deploy Private Applications in AWS through Launch Templates and Auto Scaling configurations in order to create a scalable and supportable infrastructure.
This procedure assumes that you have an Amazon Virtual Private Cloud (VPC) created and that you also have full access to create EC2 instances. It is also assumed that you are deploying the App Connector in a private subnet which has internet access via a NAT gateway. You can deploy the App Connector in a public subnet, but because no connectivity is required from the internet to the App Connector, this would not be the most secure place to deploy.
To deploy an App Connector on AWS using a Launch Template with Auto Scaling:
- Log in to the AWS Management Console.
- Click **EC2**.
- From the menu on the right, under **Network & Security**, click **Security Groups**.
- Click **Create Security Group**.
[See image.](#deploy2-CreateSecGrp1)
The **Create Security Group** window appears.
- In the **Create Security Group** window:
- Enter a **Security group name**.
- Enter a **Description**.
- Select the proper **VPC **from the drop-down menu.
- On the **Outbound **tab, allow access to 0.0.0.0/0 on all ports.
If necessary, outbound access can be restricted to hosts and ports. For details regarding required IPs, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
- Click **Create**.
[See image.](#deploy2-CreateSecGrp2)
The new group appears in the **Security Groups** page.
- From the menu on the right, under **Instances**, click **Launch Templates**.
- Click **Create launch template**.
[See image.](#deploy2-CreateLaunchTemp1)
Within the EC2 Management Console, the **Create launch template** page appears.
- In the **Create launch template** page:
- Make sure that **Create a new template** is selected.
- Enter a **Launch template name**.
- Enter a **Template version description**.
- Under the **Launch template contents** section, click **Search for AMI**.
- In the **Search for AMI** window that appears:
- From the **AMI catalog** menu, select **AWS Marketplace**.
- From the **AMI menu**, filter for zpa-connector and select it from the list.
- For **Instance type**, select a type that supports the App Connector's [sizing requirements](#Prereqs).
- Select the proper SSH **Key pair name** to deploy.
- For **Network type**, make sure **VPC** is selected.
- From the **Security Groups** drop-down menu, select the group you previously created in step 5.
- (Optional) You can customize your **Network interfaces**, if necessary. However, the default settings are adequate for deployment.
- (Optional) You can add **Tags** to the launch template, if necessary. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html).
- Expand the **Advanced details** section.
- Within the **User data** field enter the following script:
#!/bin/bash
#Stop the App Connector service which was auto-started at boot time
systemctl stop zpa-connector
#Create a file from the App Connector provisioning key created in the ZPA Admin Portal
#Make sure that the provisioning key is between double quotes
echo "<App Connector Provisioning Key>" > /opt/zscaler/var/provision_key
#Run a yum update to apply the latest patches
yum update -y
#Start the App Connector service to enroll it in the ZPA cloud
systemctl start zpa-connector
#Wait for the App Connector to download latest build
sleep 60
#Stop and then start the App Connector for the latest build
systemctl stop zpa-connector
systemctl start zpa-connector
In the echo statement above, make sure that you have included the App Connector provisioning key you copied from the Admin Portal, for example:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
echo "1|api.private.zscaler.com|IhQ9C+gJG+x1AFcO3XGlrMW1SDkIuuyRsNwfB4B+cDc2RNNPePNGuI26N/zZJ08ZjaGW5EKiIQ28rfE9TobevoQAt192+CcUgiKUCtGO7w5+2MeOmhiOTjB+Ox/PlWEoJSqqZFKR5EdNDZr+zd2/gYXTNAn8oG+BDT7NMV7YocvcnvBZG6DfOImAwtSlOSY45tJprEtoCSpT+SCsijyPCuv61QdqObIJcnA5Cs8jo6LjSqqlVYkBYgTEJgZdNKHlMkV5lxk/Ayh43A4hGLCnY+InMTj0sF7US8/NZlR/2mdAbAbmf+1ujDr/k1YgC9QQX3alr7qpHIFO/HxvyutzIu9+QXqkdCA6tL8o+RQiFrDJ7YTiQ/HxlVPlN0tKyw2K" > /opt/zscaler/var/provision_key
For all other fields within this section, the default settings are adequate for deployment.
- Click **Create launch template**.
[See image.](#deploy2-CreateLaunchTemp3)
- On the confirmation page that appears, click **Create Auto Scaling group**.
[See image.](#deploy2-CreateLaunchTemp4)
Within the EC2 Management Console, the **Create Auto Scaling Group** wizard appears.
- In **Step 1: Configure Auto Scaling group details**, the **Launch Template** you created previously is automatically selected:
- Enter a **Group name**.
- Set the **Group size** to **Start with **2** instances**.
- Select a **Subnet** from the drop-down menu. This is where your App Connectors are deployed. As stated previously, for each VPC there should be a pair of App Connectors deployed for resilience and scalability. So make sure that you select 2 subnets from the drop-down menu.
- Click **Next: Configure scaling policies**.
[See image.](#deploy2-CreateAutoScalingGrp1)
- In **Step 2: Configure scaling policies**:
- Select **Use scaling policies to adjust the capacity of this group**.
- Enter the minimum and maximum size for the scale between instances.
- Enter a **Name **for the group.
- From the **Metric type** drop-down menu, select **Average CPU Utilization**.
- Enter a **Target value** of 50.
Your scaling policy should start with the initial deployment of 2 App Connectors; each App Connector is capable of passing 400-500 Mbps traffic. An additional App Connector can be added once this limit is reached, which occurs once the App Connector runs at about 50% CPU utilization. To learn more about App Connector throughput, see [App Connector Specifications and Sizing Requirements](#Prereqs).
- Click **Next: Configure Notifications**.
[See image.](#deploy2-CreateAutoScalingGrp2)
- In **Step 3: Configure Notifications**, set up your notifications as needed and click **Next: Configure Tags**. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/ASGettingNotifications.html#as-configure-asg-for-sns).
- In **Step 4: Configure Tags**, set up your tags as needed and click **Review**. To learn more, see the [AWS product documentation](https://docs.aws.amazon.com/autoscaling/ec2/userguide/autoscaling-tagging.html).
- In **Step 5: Review**, verify your configuration settings and click **Create Auto Scaling group**.
[See image.](#deploy2-CreateAutoScalingGrp3)
After the App Connectors are initialized, they'll be provisioned into the App Connector Group you specified in the Admin Portal. The provisioning is based on the provisioning key included in the script you entered in the **User data** field for the Launch Template (step 8.m.) and Auto Scaling Group configuration.
- Zscaler highly recommends [updating the App Connector system software](/unified/managing-deployed-app-connectors#Updating) before proceeding.
[]![Diagram of ZPA in AWS Deployment](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-deployment-diagram.jpg)
[]![AWS EC2 Management Console on Security Groups page](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createsecuritygroup.png)
[]![AWS EC2 Management Console with Create Security Group window](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createsecuritygroup2.png)
[]![AWS EC2 Management Console on Launch Templates page](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createlaunchtemplate.png)
[]![AWS EC2 Management Console on Create Launch Template wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-guide-amazon-web-services/zpa-aws-createlaunchtemplate1.png)
[]![AWS EC2 Management Console with Create Launch Template success confirmation page](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createlaunchtemplate2.png)
[]![AWS EC2 Management Console with Create Auto Scaling Group wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createautoscalinggroup1.png)
[]![AWS EC2 Management Console with Create Auto Scaling Group wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createautoscalinggroup2.png)
[]![AWS EC2 Management Console with Create Auto Scaling Group wizard](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/connector-deployment-amazon-web-services-aws/zpa-aws-createautoscalinggroup-review.png)
[]
After you have deployed the App Connector on a supported platform, you can complete the following networking configurations:
- [Configure Additional Interfaces for an App Connector](#Interfaces)
- [Configure an App Connector to Use an Explicit Proxy Server](#proxy)
- [Configure DHCP IP Addressing for an App Connector](#DHCP_IP)
- [Configure Domain Name System (DNS) Resolver for an App Connector](#DNS)
- [Configure Network Time Protocol (NTP) Servers for an App Connector](#NTP)
- [Configure a Proxy Bypass for an App Connector](#proxybypass)
- [Configure Static IP Addressing for an App Connector](#Static_IP)
- [Configure Static Routing for an App Connector](#Routing)
- [Configure TCP Communication Sockets for an App Connector](#Tcpcommunication)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
- [Verify That Keepalive Is Enabled for TCP Sessions](#verify-keep-alive)
[]By default, virtual machine-based App Connectors are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for the App Connector.
[]If DHCP is not available, you can configure a static IP address on a VM-based App Connector.
- Log in to the App Connector console using your admin credentials.
- View the current connection profile.
[admin@zpa-connector ~]$ nmcli connection show
- Modify the connection profile using the following format: <profile name> connection.id <new connection name>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
- Review the current connection profile.
`[admin@zpa-connector ~]$ nmcli connection show`
- Edit the profile using a static IP and a default gateway with the following format: <connection ID> ipv4.method manual ipv4.addresses <IP addresses> ipv4.gateway <gateway IP> ipv4.dns <DNS IP> ipv4.dns-search <domain name>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
- To apply the changes, bring the connection ID back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection up LAN `
- Verify the IP address.
`[admin@zpa-connector ~]$ ip addr show`
- Verify the default gateway.
[admin@zpa-connector ~]$ ip route show default
- Verify the DNS settings.
[admin@zpa-connector ~]$ sudo cat /etc/resolv.conf
[]If necessary, additional changes can be made to interfaces by configuring new ones using nmcli connection add con-name or by renaming existing ones using nmcli connection modify.
- Log in to the App Connector console using your admin credentials.
- View the IP address.
[admin@zpa-connector ~]$ ip addr show
- View the current connection profiles.
[admin@zpa-connector ~]$ nmcli connection show
- Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For static, modify the connection profile and identify the IP addresses and gateway using the following format: <profile name> ipv4.method manual ipv4.addresses <address> ipv4.gateway <gateway IP>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254`
- To apply the changes, bring the connection profile back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1" `
- Reverify the IP address.
`[admin@zpa-connector ~]$ ip addr show`
- Reverify the new connection.
`[admin@zpa-connector ~]$ nmcli connection show`
[]To add static routes to the interface control files for an App Connector:
- Log in to the App Connector console using your admin credentials.
- Edit the static route for an existing Ethernet connection using the following format: <profile name> ipv4.routes <address and gateway>. For example:
[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes "192.168.2.241/24 10.10.10.1"
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-connector ~]$ sudo nmcli connection down "Profile 1" [admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1"
- Verify the new route is added.
[admin@zpa-connector ~]$ ip route
[]DNS resolution is critical for the successful operation of the App Connector. App Connectors use DNS to discover applications, as well as enumerate each of the IP addresses that an application DNS name resolves to as a separately tracked and load-balanced server. During dynamic application discovery, DNS is used as the initial reachability check from each App Connector in an App Connector group. It is possible for App Connectors to function in partitioned environments where a subset of App Connectors are able to resolve a given DNS name without additional configuration. App Connectors must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the App Connector console using your admin credentials.
- View the current connection profile.
[admin@zpa-connector ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection down "Profile 1"`` [admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1"`
- Verify the nameservers record was added.
`[admin@zpa-connector ~]$ sudo cat /etc/resolv.conf`
[]You cannot configure NTP servers for App Connectors running on the Amazon Web Services (AWS) or Microsoft Azure platforms.
To configure App Connectors to use internal NTP servers:
- Log in to the App Connector console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@zpa-connector ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list, for example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-connector ~]$ systemctl restart chronyd
- To verify the NTP servers, check that NTP is working successfully using the following command:
[admin@zpa-connector ~]$ chronyc sources
[]The proxy setting on the App Connector is used to proxy the traffic between the App Connector and the ZPA Private Service Edge. It is not used to proxy the traffic between the App Connector and internal applications.
If your traffic is going through a proxy (i.e., traffic between the App Connector and the ZPA Public Service Edges or ZPA Private Service Edges), you must manually configure the App Connector to work through that proxy. The following procedure allows the App Connector to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the App Connector to work through an explicit proxy:
- Log in to the App Connector console using your admin credentials.
- Create a file named /opt/zscaler/var/proxy. Use an editor, such as vi.
[admin@zpa-connector ~]$ sudo vi /opt/zscaler/var/proxy
Enter the proxy information using the following format: <Proxy Hostname or IP Address>:<Proxy Port> (e.g., 192.0.2.0:0).
- To apply the changes, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
The App Connector attempts to create a TLS session through the proxy specified previously.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.
To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
[]If an App Connector is configured to send traffic to a proxy, you can set up a proxy bypass on it for the traffic that needs to be exempted from the proxy (i.e., traffic between the App Connector and the ZPA Public Service Edges or Public Service Edges). To use a proxy bypass for an App Connector, a proxy bypass file needs to be added to the App Connector.
To configure the App Connector to do a proxy bypass:
- Log in to the App Connector console using your admin credentials.
- Create a file named `opt/zscaler/var/proxy-bypass`. Use an editor, such as vi. For example:
[admin@zpa-connector ~]$sudo vi /opt/zscaler/var/proxy-bypass
- Enter the necessary bypass entries using IP addresses, subnets, domains, or domains with a prefix wildcard. For example:
1.2.3.4
111.222.33.0/24
myexampledomain.com
*.internal.local
- To apply the changes, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
[]To temporarily configure TCP communication sockets using the profs interface and the `SO_KEEPALIVE` socket option for an App Connector:
- Enable **TCP Keepalive** for your segment group in the ZPA Admin Portal. To learn more, see [Configuring Defined Application Segments](/zpa/pselabel/configuring-application-segments).
The socket used for TCP communication is set to `SO_KEEPALIVE` and establishes an App Connector-to-Server connection. Communication using this socket looks at the system value corresponding to `SO_KEEPALIVE` and performs the action according to the parameters.
- Tune your App Connector's kernel to configure the TCP parameters and choose how the keepalive packets are sent using the following commands:
# echo 600 > /proc/sys/net/ipv4/tcp_keepalive_time
# echo 60 > /proc/sys/net/ipv4/tcp_keepalive_intvl
# echo 20 > /proc/sys/net/ipv4/tcp_keepalive_probes
Default values are used if no system parameters are chosen. The values in red represent examples of values that can be configured.
Changes to the App Connector's kernel to configure the TCP parameters using the profs interface are temporary and return to default after reboot.
To permanently configure TCP communication sockets using the sysctl interface:
- Enable **TCP Keepalive** for your segment group in the ZPA Admin Portal. To learn more, see [Configuring Defined Application Segments](/zpa/pselabel/configuring-application-segments).
- Edit your `/etc/sysctl.conf` using the following command:
# vi /etc/sysctl.conf
- Tune your App Connector's kernel to configure the TCP parameters and choose how the keepalive packets are sent using the following commands:
net.ipv4.tcp_keepalive_time = 60
net.ipv4.tcp_keepalive_intvl = 10
net.ipv4.tcp_keepalive_probes = 6
Default values are used if no system parameters are chosen. The values in red represent examples of values that can be configured.
- To load the settings, enter the following command:
# sysctl -p
The keepalive packets have the following parameters:
| Parameter | Definition | Default Value |
| --------- | ---------- | ------------- |
| `tcp_keepalive_time` | The interval between the last data packet sent (simple ACKs are not considered data) and the first keepalive probe; after the connection is marked to need keepalive, this counter is not used any further. | 7,200 seconds (2 hours) |
| `tcp_keepalive_intvl` | The interval between subsequent keepalive probes, regardless of what the connection has exchanged in the meantime. | 75 seconds |
| `tcp_keepalive_probes` | The number of unacknowledged probes to send before considering the connection dead and notifying the application layer. The `tcp_keepalive_probes` value is a pure number. | 9 |
For example:
- If the `tcp_keepalive_time value` is one hour, the keepalive routines wait for one hour before sending the first keepalive probe, and then resend it at a 75-second interval according to the `tcp_keepalive_intvl` value.
- If the `tcp_keepalive_intvl` value is 60 seconds, the keepalive probes are sent every 60 seconds after the initial `tcp_keepalive_time` value.
- If the `tcp_keepalive_probes` value is 7, and no ACK response is received after 7 consecutive times, then the connection is marked as broken.
If there is no data communication within the `tcp_keepalive_time` value, it sends out a keepalive probe to the app server:
- If ACK is returned, another keepalive probe is sent after 2 hours (`tcp_keepalive_time`) if no data communication happens in between.
- If RST is returned, then the socket closes.
- If there is no reply, it resends the keepalive every 75 seconds (`tcp_keepalive_intvl`) for a reply, and it retries 9 times (`tcp_keepalive_probes`). If there is no reply after 9 probes, the socket closes.
To learn more about configuring a kernel, refer to the [Linux documentation](https://tldp.org/HOWTO/html_single/TCP-Keepalive-HOWTO/#configuringkernel).
[]To see which TCP sessions have `keepalive` enabled and what their current timer is, run the `ss` command on the App Connector with the `-t` (tcp only) and `-o` (show timers) options:
`# ss -to
State  Recv-Q  Send-Q  Local Address:Port  Peer Address:Port
ESTAB  0       0       10.18.4.210:42452   10.251.33.110:https  timer:(keepalive,29sec,0)`
For sessions that have `keepalive` enabled, timer information (`timer:(<timer_name>,<expire_time>,<retrans>)`) indicates when `keepalive` will be sent. To learn more, refer to the [Linux documentation](https://www.man7.org/linux/man-pages/man8/ss.8.html).