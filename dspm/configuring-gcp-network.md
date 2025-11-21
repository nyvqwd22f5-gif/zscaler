# Configuring the GCP Network
Source: https://help.zscaler.com/dspm/configuring-gcp-network
PDF: https://help.zscaler.com/pdf/com/en/1527036.pdf

DSPM requires a specific network configuration to be able to access the GCP services, scan the resources, compute, and report the findings. You can configure either a custom network in your organization or use the DSPM-provided network setup.
For a custom network, you need to select an orchestrator subscription while [onboarding the GCP organization](/dspm/onboarding-gcp-organization) and create the following virtual private cloud (VPC) in the orchestrator project:
- **Control Plane VPC**: Create this VPC only in the primary region where the orchestrator is going to run.
- **Worker Plane VPC**: Create this VPC in all the regions where the resources exist. For example, if the GCP projects are stored in East US and Central US regions, create the worker plane VPC in both regions.
Ensure that both control and worker plane VPC do not have overlapping Classless Inter-Domain Routing (CIDR).
You can configure the GCP network manually or deploy the predefined templates:
- [1. Create the control plane VPC and associated resources.](#gcp-create-cp-vpc)
- [2. Configure the control plane network firewall rules.](#gcp-edit-cp-vpc)
- [][3. Create the worker plane VPC and associated resources.](#gcp-create-wp-vpc)
- [4. Configure the worker plane network firewall rules.](#gcp-edit-wp-vpc)
- [5. Set up private service access in the worker plane VPC.](#private-service-access)
- [6. Peer the control and worker plane VPCs.](#vpc-peering)
- [7. Configure Cloud NAT gateway resources.](#nat)
[]A Cloud NAT resource is required to allow VMs in a VPC to connect to other VPC resources and outbound internet connections. []The Cloud NAT Gateway is a region-specific and network-specific resource that must be created for each combination. For the primary region where data stores are to be scanned, two Cloud NAT gateways need to be created, one for the control plane VPC and one for the worker plane VPC.
To set up control plane and worker plane Cloud NAT resources in the orchestrator project:
- Go to [Network Services](https://console.cloud.google.com/net-services/) in the Google Cloud console and select **Cloud NAT**.
- Click **CREATE CLOUD NAT GATEWAY**.
- On the **Create Cloud NAT gateway** page:
- **Gateway name**: Enter a name for the Control Plane NAT Gateway.
- **NAT type**: Set the NAT type to **Public**.
- In the **Select Cloud Router** options:
- **Network**: Select the Control Plane VPC Network.
- **Region**: Select the region as the Control VPC network.
- **Cloud Router**: Select **CREATE NEW ROUTER**.
- In the **Create a router** drawer, provide a name for the control plane router and retain the default configurations.
-
Click **CREATE**.
[See image.](#img-ds-gcp-router)
-
In the **Cloud NAT mapping**, for **Source endpoint type**, select the **VM instance, GKE nodes, Serverless**.
Retain the default configurations.
-
Click **Create**.
[See image.](#img-ds-gcp-create-nat)
- Repeat the steps for the Worker Plane Cloud NAT Gateway, for each region where data stores are present, selecting the Worker Plane VPC Network in **Cloud Router** options.
[]![Create Cloud NAT gateway page with required values to configure the NAT gateway. ](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-nat.png)
[]![Create a router pane pane.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-vpc-router.png)
[]After the control and worker plane VPCs are created, they need to be peered so that the control and worker planes can communicate.
To peer the control and worker plane VPCs:
- Go to the **VPC networks** page, and select the created control plane VPC network.
- On the **VPC network details** page, select the **VPC NETWORK PEERING** tab.
- Click **ADD PEERING**.
- On the **Create peering connection** page:
- Provide a name for the peering connection.
-
In the **Peered VPC network** dropdown, select the worker plane VPC in the orchestrator project.
Retain the default selections for the remaining configurations.
-
Click **CREATE**.
The peering status in the control plane VPC is **Inactive**.
[See image.](#img-ds-gcp-vpc-peer)
- Repeat the steps for the worker plane VPC, selecting the control plane VPC in the **Peered VPC network** drop-down menu.
After successful configuration of the peering, the peering status is updated to **Active** for both the control plane VPC and worker plane VPC.
[]![Create peering connection with required values ](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-vpc-peering.png)
[]After the worker plane VPC is created, set up private service access in the worker plane VPC. This is used for scanning GCP Cloud SQL instances.
To set up private access in the worker plane VPC:
- Select the [worker plane VPC](#wp-vpc) network.
-
Select the **Private Services Access** tab.
[See image.](#img-ds-gcp-wp-psa)
- Select the **ALLOCATED IP RANGES FOR SERVICES** tab.
- Click **ALLOCATE IP RANGE** and enter the following values:
- **Name**: Enter `private-service-access-ip-range`.
- **IP range**: Select **Automatic**.
- **Prefix length**: Enter `16`.
-
Click **ALLOCATE**.
[See image.](#img-allocate-internal-ip-range)
- Select the **PRIVATE CONNECTIONS TO SERVICES** tab.
- Click **CREATE CONNECTION** and enter the following values:
- **Connected service producer**: Select **Google Cloud Platform**.
- **Assigned allocation**: Select the IP Range created in the previous step.
- Click **OK**.
-
Click **CONNECT**.
[See image.](#img-ds-gcp-cpc)
After the private service access is configured, Google adds peering from the worker plane VPC to servicenetworking.
[]![Create a private connection page with  the required values to configure.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-cpc.png)
[]![Allocate an internal IP range page with the required values to configure.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-allocate-ip.png)
[]![Private Services Access page to setup private service access for worker plane.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-wp-psa.png)
[]After creating the worker plane VPC network, edit the created VPC to configure the firewall rules.
- To add a rule to deny outbound communication to the orchestrator:
- Go to the **VPC networks** page, and select the created worker plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `deny-all-outbound-rule`.
- **Priority**: Enter `1000`.
- **Direction**: Select **Egress**.
- **Action on match**: Select **Deny**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
[See image.](#img-ds-gcp-wp-rule-deny)
- Click **Create** to save the rule.
- To add a rule to allow inbound communication from the orchestrator to the scanner VPC:
- Go to the **VPC networks** page, and select the created control plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `allow-orchestrator-outbound-rule`.
- **Priority**: Enter `0`.
- **Direction**: Select **Ingress**.
- **Action on match**: Select **Allow**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
- **Protocols and ports**: Select **Specified protocols and ports**.
- **TCP**: Select the checkbox.
- **Ports**: Enter `443`.
[See image.](#img-ds-gcp-wp-rule-allow)
- Click **Create** to save the rule.
- To add a rule to allow outbound communication from the scanner to DSPM:
- Go to the **VPC networks** page, and select the created control plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `allow-https-outbound-rule`.
- **Priority**: Enter `1`.
- **Direction**: Select **Egress**.
- **Action on match**: Select **Allow**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
- **Protocols and ports**: Select **Specified protocols and ports**.
- **TCP**: Select the checkbox.
- **Ports**: Enter `443`.
[See image.](#img-ds-gcp-wp-rule-allow-https)
- Click **Create** to save the rule.
-
To add a rule to allow outbound communication from the scanner to GCP Cloud SQL instances:
- Go to the **VPC networks** page, and select the created control plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `allow-db-outbound-rule`.
- **Priority**: Enter `2`.
- **Direction**: Select **Egress**.
- **Action on match**: Select **Allow**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
- **Protocols and ports**: Select **Specified protocols and ports**.
- **TCP**: Select the checkbox.
- **Ports**: Enter `3306, 5432, 1433`.
[See image.](#img-ds-gcp-wp-rule-allow-gcpcloud)
- Click **Create** to save the rule.
The worker plane firewall rules are configured.
[]![Create a worker plane firewall rule with the values provided to allow outbound communication from the scanner to GCP Cloud SQL Instances.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-wp-rule-allow-gcpcloud.png)
[]![Create a worker plane firewall rule with the values provided to allow outbound communication from the scanner to DSPM. ](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-wp-rule-allow-https.png)
[]![Create a worker plane firewall rule with the values provided to allow inbound communication from the orchestrator to scanner vpc.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-wp-rule-allow.png)
[]![Create a worker plane firewall rule with the values provided to deny all outbound communication](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/img-ds-gcp-wp-rule-deny.png)
[]
-
Go to the **VPC networks** page, and click **CREATE VPC NETWORK**.
[See image.](#img-ds-gcp-create-wp-vpc)
-
On the **Create a VPC network** page:
- **Name**: Enter a name for the VPC network.
- **Subnet creation mode**. Select **Custom**.
-
**Subnets**: Click **ADD SUBNET** and provide a name for the subnet.
- **Region**: Select the primary region where the data stores are located.
- **IPv4 range**: Enter an IPv4 range for the subnet.
- **Private Google Access**: Select **On**.
To add multiple subnets in different regions, click **ADD SUBNET** and repeat these steps for each additional subnet as required.
- Retain the remaining VPC and subnet configurations with their default settings.
[See image.](#img-ds-gcp-create-wp-vpc-details)
- Click **Create**.
The VPC and subnet for the worker plane are created.
After creating the worker plane VPC, [create and configure the Cloud NAT gateway resources](#create-nat) for the new subnet and region in the worker plane.
[]![VPC Network page with an annotation around Create VPC Network.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-create-vpc.png)
[]![Create a VPC network page with annotations around the required fields.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-create-wp-vpc-details.png)
[]After creating the control plane VPC, edit the created VPC to configure the firewall rules.
- To add a rule to deny outbound communication to the orchestrator:
- Go to the **VPC networks** page, and select the created control plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `deny-all-outbound-rule`.
- **Priority**: Enter `1000`.
- **Direction**: Select **Egress**.
- **Action on match**: Select **Deny**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
[See image.](#img-ds-gcp-cp-rule-deny)
- Click **Create** to save the rule.
-
To add a rule to allow outbound communication from the orchestrator to DSPM:
- Go to the **VPC networks** page, and select the created control plane VPC network.
-
Select the **Firewalls** tab, and click **Add Firewall Rule**.
The **Create a firewall rule** window appears.
-
In the **Create a firewall rule** window, provide the following values in the respective fields to deny all outbound communication to the orchestrator:
- **Name**: Enter `allow-https-outbound-rule`.
- **Priority**: Enter `0`.
- **Direction**: Select **Egress**.
- **Action on match**: Select **Allow**.
- **Targets**: Select **All Instances in the network**.
- **Destination filter**: Select **IPv4 ranges**.
- **Destination IPv4 ranges**: Enter `0.0.0.0/0`.
- **Protocols and ports**: Select **Specified protocols and ports**.
- **TCP**: Select the checkbox.
- **Ports**: Enter `443`.
[See image.](#img-ds-gcp-cp-rule-allow)
- Click **Create** to save the rule.
The control plane firewall rules are configured.
[]![Create a control plane firewall rule with the values provided to allow all outbound communication](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-cp-rule-allow.png)
[]![Create a control plane firewall rule with the values provided to deny all outbound communication](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-cp-rule-deny.png)
[]
-
Sign in to the [Google Cloud console](https://console.cloud.google.com/), select the resource from the drop-down menu and then select the orchestrator project.
[See image.](#img-ds-gcp-select-proj)
-
Go to the **VPC networks** page, and click **CREATE VPC NETWORK**.
[See image.](#img-ds-gcp-create-vpc)
-
On the **Create a VPC network** page:
- **Name**: Enter a name for the VPC network.
- **Subnet creation mode**:** **Select **Custom**
- **Subnets**: Click **ADD SUBNET** and provide a name for the subnet.
- **Region**: Select the primary region where the orchestrator will be deployed.
- **IPv4 range**: Enter an IPv4 range for the subnet.
- **Private Google Access**: Select **On**.
- Retain the remaining VPC and subnet configurations with their default settings.
[See image.](#img-ds-gcp-create-vpc-details)
- Click **Create**.
The VPC and subnet for the control plane are created.
[]![GCP Console project selector page with list of projects listed.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-select-proj.png)
[]![VPC Network page with an annotation around Create VPC Network.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-create-vpc.png)
[]![Create a VPC network page with annotations around the required fields.](/downloads/dspm/cloud-accounts-onboarding/custom-network-configuration/configuring-gcp-network/ds-gcp-create-cp-vpc-details.png)