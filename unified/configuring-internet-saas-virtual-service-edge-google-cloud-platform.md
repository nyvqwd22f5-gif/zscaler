# Configuring Internet & SaaS Virtual Service Edge for Google Cloud Platform
Source: https://help.zscaler.com/unified/configuring-internet-saas-virtual-service-edge-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1495681.pdf

Zscaler supports standalone Virtual Service Edge for production deployments on the Google Cloud Platform (GCP).
Requirements
Ensure that you meet all of the following requirements:
- Virtual Service Edges only require outbound connections to the Zscaler cloud. Configure your firewall to allow the necessary outbound connections. To view the firewall requirements, log in to the Admin Portal, go to the Help menu, and select Cloud Configuration Requirements.
- Verify that your license is appropriate to your needs. In the Admin Portal, go to the Subscriptions page and look for the Virtual Service Edges, noting the server count.
- Virtual Machine specs for a Virtual Service Edge:
- **CPUs**: 4 CPU cores
- **Recommended Instances Type**: n2-highmem-4
- **RAM**: 32 GB for production
- **Disk**: 500 GB. Zscaler recommends using SSDs
- **Network Interfaces**: 3 interfaces (NIC0 for Virtual Service Edge, NIC1 for Management, and (Optional) NIC2 for the Dual Arm Interface).
- []The required IP addresses are listed in [the following table.](#table)
Configuring a Virtual Service Edge
If you are configuring a Virtual Service Edge, you must download its respective SSL certificate from the Admin Portal. The SSL certificate is unique to the Virtual Service Edge.
To configure a Virtual Service Edge:
- [1. Deploy the Image on GCP](#deploy-image)
- [2. Add the Virtual Service Edge Instance](/unified/adding-virtual-service-edge-instances)
- [3. Download the Virtual Service Edge Certificate](/unified/downloading-virtual-service-edge-certificates)
- [4. Configure the Virtual Service Edge VM](#Sphere)
- [5. (Optional) Deploy GCP Internal Load Balancer (ILB)](#dual-arm-mode)
After you configure a Virtual Service Edge, you can then forward your internet traffic to it using one of the mechanisms described in [Forwarding Traffic to Internet & SaaS Virtual Service Edges](/unified/forwarding-traffic-internet-saas-virtual-service-edges).
Testing and Logging Traffic
To test and log the traffic:
- On the GCP console, go to **VPC network** > **Firewall**.
- Edit the firewall rule for NIC0 to allow the following ports/IP addresses:
- **Egress**: Select **Allow All**.
- **Ingress**: Allow the following ports for Zscaler configuration:
- **9443**
- **443**
- **80**
- **9480**
- **9400**
Ensure to allow ports specifically required by your organization.
- Configure the browser proxy as **NIC0:9443**.
- In the Admin Portal, configure a [URL Filtering](/unified/configuring-url-filtering-policy) rule and a [Firewall Filtering](/unified/configuring-firewall-filtering-policy) policy rule to block/allow traffic.
For example, configure a URL Filtering rule to block URLs belonging to the **Social Networking** category and a Firewall Filtering policy rule to block the San Jose location.
- Make a request to any domain and verify that the traffic is redirected to the Admin Portal.
- Go to **Logs **>** Insights** >** Web Insights **>** Logs**, and retrieve the logs for the last 15 minutes to verify logs for test traffic are present.
For example, logs blocking traffic destined for www.facebook.com belonging to the **Social Networking** category and traffic destined for www.domainsanjose.com, a San Jose-based domain, are present.
[]
-
-
-
-
| IP Address | Purpose | Requirements |
| ---------- | ------- | ------------ |
| Management IP Address | This is used to make an SSH connection to the Virtual Service Edge VM for management. It is also used to download Virtual Service Edge builds from the Zscaler cloud. | Accessible via SSH by the Virtual Service Edge administrator during install, and requires outbound access to the internet. This is configured in the Virtual Service Edge CLI. |
| Proxy IP Address | This is used for the following purposes:Outbound data connection (proxied traffic)Outbound control connection to the Zscaler cloudHealth monitoring by the load balancerIn a Virtual Service Edge standalone, it is used to listen for user traffic | This is used when creating a Virtual Service Edge instance in the Admin Portal. |
[]You can deploy the image on GCP using one of the following methods:
- [GCP Console](#deploy-gcp-gui)
- [gcloud CLI](#deploy-gcp-gcloud-cli)
The newly created VM instance is available on the **Compute Engine** > **VM Instances** page of the GCP console.
[]To deploy the image on the GCP console:
- On the GCP console, go to **Compute Engine** >** Images**.
[See image.](#compute-engine-images)
- Choose the Zscaler OS24 Virtual Service Edge** **image (e.g., zscaleros24-vse-rev10) and click **Create Instance **from the **Actions **menu.
Contact Zscaler Support for the Virtual Service Edge image on GCP.
- On the **Create Instance** page, define the following parameters:
- **Name**: Enter the name of the instance.
- **Region**: Select a region for the instance.
- **Series**: Select **N2**.
- **Machine Type**: Select **n2-highmem-4**.
[See image.](#gcp-create-vm-instance)
- Go to **Advanced options** > **Networking**.
- Select the **Enable **checkbox for **IP forwarding**.
- Select **VirtIO **for **Network interface card**.
- Configure the service interface (NIC0):
- Select an appropriate network from the **Network **field.
The** Subnetwork **field is automatically populated based on the selected network.
- Click **Done**.
[See image.](#gcp-create-instance-network)
- Configure management interface (NIC1):
- Click **Add Network Interface**.
- Select an appropriate network from the **Network **field.
The** Subnetwork **field is automatically populated based on the selected network.
- Click **Done**.
[See image.](#gcp-network-interfaces)
The `zgcpservice_enable` service in the `rc.conf` system configuration file is set to `YES` by default, which adds the following configurations for the management interface automatically:
- `ifconfig_vtne1`
- `defaultrouter`
- `static_routes`
- `route_sbnet1`
- `route_gateway1`
- (Optional) Configure dual arm interface (NIC2):
- Click **Add Network Interface**.
- Select an appropriate network from the **Network **field.
The** Subnetwork **field is automatically populated based on the selected network.
- Click **Done**.
- Click **Create**.
[]To deploy the image using the gcloud CLI:
- Go to gcloud CLI. To learn more, see [Install the gcloud CLI](https://cloud.google.com/sdk/docs/install).
- Run the following command:
gcloud compute instances create <INSTANCE_NAME> \
[--image=<IMAGE> | --image-family=<IMAGE_FAMILY>] \
--image-project=zia-gcp
--machine-type=n2-highmem-4
--zone [ZONE]
[--network-interface [network=<NETWORK>,subnet=<SUBNET>],[stack-type=<STACK_TYPE>],[address=<RESERVED_EXTERNAL_ADDRESS> | no-address], [private-network-ip=<INTERNAL_ADDRESS>] ...]
Replace all text in red with the appropriate values.
Contact Zscaler Support for the Virtual Service Edge image name. If you specify the image-family in this command, a VM instance is created using the latest version of the OS image.
- [See sample command.](#sample-command-gcloud-cli)
To learn more about deploying the image on the GCP using gcloud CLI, see [Create and start a VM instance](https://cloud.google.com/compute/docs/instances/create-start-instance#gcloud) and [Create VMs with multiple network interfaces](https://cloud.google.com/vpc/docs/create-use-multiple-interfaces#gcloud).
[]gcloud compute instances create mygcpvse \
[--image=zscaleros24-vse-rev10] \
--image-project=zia-gcp
--machine-type=n2-highmem-4
--zone=us-west2-a
[--network-interface [network=proxy-vpc,subnet=service-subnet] --network-interface [network=management-vpc,subnet=management-subnet]]
[]![Screenshot of GCP console.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Compute-Engine-Images.png)
[]![Screenshot of Google Cloud Platform Create Instance](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Create-VM-Instance.png)
[]![Screenshot of Google Cloud Platform Create Instance Networking](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Create-VM-Instance-Network.png?1665471715)
[]![Screenshot of Google Cloud Platform Network Interfaces](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Create-VM-Instance-Network-Interfaces.png?1665471786)
[]You must configure the Virtual Service Edge instance as a VM on the GCP console.
Zscaler recommends using different servers for each instance to achieve fault tolerance.
To configure the Virtual Service Edge on the GCP console:
- Go to **Compute Engine** >** VM instances**.
- Select the Virtual Service Edge VM and click either the **Power On** button or **Power On the virtual machine**.
- Click the Virtual Service Edge VM.
[See image.](#gcp-vm-instance)
- Click **Connect to Serial Console**, and log in at the FreeBSD command prompt with the following credentials:
- Username: zsroot
- Password: zsroot
The following guidelines apply:
- Zscaler cloud strongly recommends that you change this default password by running the passwd command.
- Direct root login is not permitted. Administrators must use the sudo utility to run a command with higher privileges.
[See image.](#ssh-in-browser)
- Install the SSL certificate of the Virtual Service Edge instance. This is the certificate you downloaded from the Admin Portal. A Virtual Service Edge uses this certificate to authenticate itself to the Zscaler service.
To install the SSL certificate of the Virtual Service Edge instance:
- Navigate to the SSL certificate that you saved.
- Use SCP or SFTP to upload it to the management IP address of the Virtual Service Edge.
- Go to the **Connect to Serial Console** or use SSH to connect to the management IP address.
- Run the following command:
sudo vzen install-cert <cert-bundle.zip>
Ensure to specify the absolute path to the SSL certificates (e.g., `sudo vzen install-cert /tmp/cert-bundle.zip`).
-
Download the Virtual Service Edge build and start the Virtual Service Edge.
- On the GCP console, click the **Connect to Serial Console** or use SSH to connect to the management IP address.
- Run the following command to download the Virtual Service Edge build:
sudo vzen download-build
The initial build is around 1 GB, so it may take a while depending on your internet connection. The downloaded build is automatically installed. The Virtual Service Edge automatically starts after the installation is complete.
- After the build is deployed, run the following command to check the service status of the Virtual Service Edge:
sudo vzen status
Ensure both the SME and smcdsc are running.
- Run the following commands to check the connectivity with the Zscaler production nodes:
- sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys show=auth
[Sample output of this command.](#auth-status)
Ensure that the authentication state is **SMAUTHENG_READY_STATE**.
- sockstat | grep -i smcdsc
Ensure that there are two connections over 9442.
- sudo vzen troubleshoot connection
[Sample output of this command.](#troubleshoot-connection)
Ensure that **cloud-config** and **log-stream** sessions are present.
- (Optional) if you want to use an SNMP management system to monitor the Virtual Service Edge, [enable SNMP for Virtual Service Edge](/unified/monitoring-virtual-service-edge-clusters#snmp-vse) and configure SNMP parameters. Virtual Service Edges support SNMPv3 only.
- Run the following command:
sudo vzen snmp-admin-configure
- Enter a user name for the SNMPv3 management system that sends queries to the Virtual Service Edge. The Virtual Service Edge accepts queries from this user name only.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
- Run the following command:
sudo vzen snmp-trap-configure
- When asked which traps you want to configure, enter v3 traps.
- Enter the IP address of the SNMP trap management system to which the Virtual Service Edge sends traps.
- Enter a user name for the SNMP management system.
- Enter a password that the Virtual Service Edge uses to authenticate the SNMP management system.
- Specify which authentication protocol the Virtual Service Edge can use to authenticate the SNMP user. Enter either MD5 or SHA1.
- Specify the encryption method the Virtual Service Edge can use to authenticate the SNMP user. Enter either DES or AES.
[]![Screenshot of Sample Output of Virtual Service Edge Connectivity to CA](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-CA-Connectivity.png)
[]![Screenshot of Sample Output of VZEN troubleshoot connection](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-troubleshoot-connection.png)
[]![Screenshot of Google Cloud Platform VM Instance](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-VM-Instance-Connect-Serial-Console.png?1665471870)
[]![Screenshot of Google Cloud Platform Serial Console window](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-VM-Instance-Serial-Console.png)
[]To deploy GCP ILB:
- Create and deploy a pair of Virtual Service Edges with NICs, as previously explained in the deploying the image on GCP step.
- Create a health check to do a TCP port check for port 443 or port 80.
- Create an unmanaged instance group and add these VM instances.
- Create the ILB and configure the front end for all ports and the backend as the instance group.
- Log in to the VMs.
- Enter the following command:
cd /sc/sme/conf
- Create a new file called `vzen_custom.conf`.
- Add the following lines:
[SME]
smnet_dev=vtnet0=nm0:<internal nic ip>/32:<ILB service ip>/32
smnet_route=<Internal nw gw ip>/32/nm0/<Internal n/w gateway MAC>
smnet_route=35.191.0.0/16/<gw ip of internal n/w> [For health check probes]
smnet_route=130.211.0.0/22/<gw ip of internal n/w>
smnet_route=10.x.x.x/24/<gw ip of internal n/w>
smnet_dev=vtnet2=nm1:<ip/mask> Second  interface pvt ip for internet access
smnet_dflt_gw=<gw ip> Gateway ip for internet access
[-end-of-SME]
- (Optional) Add the GCP ILB configuration using the CLI.
- On the GCP console, click the **Connect to Serial Console** or use SSH to connect to the management IP address.
- Run the following command:
vzen gcp-ilb-setup
- Enter `y` to continue configuring GCP ILB.
You are prompted to add the gateway MAC address.
- Enter `y` to add the gateway MAC address.
- Enter the gateway MAC address (e.g., 00:5e:00:53:af).
- Enter the ILB Virtual IP (VIP).
You are prompted to enter the static routes or continue to configure GCP ILB.
- (Optional) If you want to configure the static routes (e.g., 10.1.1.0/24/10.1.1.1), enter them in the following format:
<N/W ip range>/<Mask>/<Gateway ip of internal n/w>
- Enter `q` to complete the GCP ILB configuration.
[See the sample output of this command.](#gcp-ilb-cli)
You can remove the GCP ILB configuration using the `vzen gcp-ilb-clear `command.
- Run the following command to stagger the upgrades on the Virtual Service Edges:
vzen delay-upgrade HH:MM
This avoids parallel upgrade outages as all nodes of GCP Virtual Service Edges are standalone.
- Run the following command to restart the services on the Virtual Service Edge:
sudo vzen restart
[]![Screenshot of Sample Output of GCP ILB Configuration Using CLI](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Sample-Output-VZEN-GCB-ILB.png)