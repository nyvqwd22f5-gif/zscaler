# Configuring the AWS Network
Source: https://help.zscaler.com/dspm/configuring-aws-network
PDF: https://help.zscaler.com/pdf/com/en/1510886.pdf

DSPM requires a specific network configuration to be able to access the services, scan the data in the resources, compute, and report the findings. You can configure a custom network in your organization or use the DSPM provided network setup.
For a custom network, you need to select an orchestrator account while [onboarding the AWS cloud accounts](/dspm/onboarding-microsoft-azure-tenant) and create the following control plane and worker plane virtual private clouds (VPCs) in the orchestrator account:
- **Control Plane VPC**: Create this VPC only in the primary region where the orchestrator is going to run.
- **Worker Plane VPC**: Create this VPC in all the regions where the resources exist. For example, if the S3 buckets are stored in US West and US East regions, create the worker plane VPCs in both regions.
Ensure that both control and worker planes do not have overlapping Classless Inter-Domain Routing (CIDR).
Configure AWS Network
You can configure the AWS network manually or deploy the predefined templates:
- [Manual Configuration](#aws_manual_configuration)
- [Deploy Predefined Templates](#aws_template_configuration)
After the control plane and worker plane network components are created, peer the VPCs between the control plane and all worker plane.
Peer the VPCs
After creating the control and worker plane VPC, you need to peer these VPCs, so they can communicate with each other. This step is common for both manual and template-based configurations.
- In the [AWS console](https://aws.amazon.com/console/), go to the **Peering Connections** page.
-
Click **Create peering connection**.
[See image.](#ds-aws-createpeerconnectionbutton)
-
On the **Create peering connection** page:
- **Name**: Enter a name for the VPC peering connection.
- **VPC ID (Requestor)**: Select the control plane VPC.
-
**VPC ID (Accepter)**: Select the worker plane VPC.
[See image.](#ds-aws-peersettings)
- Click **Create peering connection**.
The peering connection is displayed on the **Peering connections** page, and it is in the **Pending acceptance** state.
-
From the **Actions** drop-down menu, select **Accept request**.
[See image.](#ds-aws-accept-peerrequestoption)
-
Review the details and click **Accept request**.
[See image.](#ds-aws-acceptreqbutton)
- Update the route tables for both control plane and worker plane VPCs to enable traffic flow between the VPCs.
- [Update control plane VPC route table](#rt-cp-vpc)
- [Update worker plane VPC route table](#rt-wp-vpc)
- Add the private subnets of the control and worker planes.
-
For **NAT Gateway**, add a route with destination `0.0.0.0/0` as needed.
[See image.](#ds-aws-editroutes)
- Confirm that the route tables reflect the correct peering connections and IP ranges.
Repeat the steps for other target regions.
- []Go to the **Route Tables**, and select the route table associated with the control plane VPC.
-
In the **Routes** tab, click **Edit routes**.
[See image.](#img-ds-aws-cp-rt)
-
Click **Add route** and configure:
- **Destination**: Enter the IP address of your worker plane VPC.
- **Target**: Select **Peering Connection**, and then choose the appropriate peering connection.
[See image.](#img-ds-aws-cp-rt-edit)
- Click **Save changes**.
[]![Route table showing control plane VPC routes, and peering connection configuration in AWS console.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-cp-rt.png)
[]![Edit routes configuration screen for peering connections and internet gateway in AWS VPC route table.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-cp-rt-edit.png)
- []Go to the **Route Tables**, and select the route table associated with the worker plane VPC.
-
In the **Routes** tab, click **Edit routes**.
[See image.](#img-ds-aws-wp-rt)
-
Click **Add route** and configure:
- **Destination**: Enter the IP address of your control plane VPC.
- **Target**: Select **Peering Connection**, and then choose the appropriate peering connection.
[See image.](#img-ds-aws-wp-rt-edit)
- Click **Save changes**.
[]![Route table showing worker plane VPC routes, and peering connection configuration in AWS console.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-wp-rt.png)
[]![Edit routes configuration screen for peering connections and internet gateway in AWS VPC route table.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-wp-rt-edit.png)
- [][1. Create the control plane VPC.](#ds-aws-createcp-vpc)
- [2. Create the worker plane VPC.](#ds-aws-createwp-vpc)
- [3. Create the control plane security group.](#ds-aws-createcontrolplane-sg)
- [4. Create the worker plane security group.](#ds-aws-createworkerplane-sg)
- [5. Create the DB subnet group.](#ds-aws-createdbsubnet)
[]To deploy the templates, Identify the template type you want to use.
- [CloudFormation Template](#cf_template)
- [Terraform Template](#tf_template)
[]To deploy the Terraform template:
- [1. Download the Terraform template.](#download_tf)
- [2. Update and deploy Terraform to create control plane VPC.](#tf_control_vpc)
- [3. Update and deploy Terraform to create worker plane VPC.](#tf_worker_vpc)
- []Open a file explorer and browse to the location where the downloaded `.zip` file was extracted. Then, open the `control-plane` folder.
- Locate and open the** **`backend.tf` file in a text editor.
-
Update the file with the name of the storage services where you want to store the Terraform state files.
For example:
- `**resource_group_name**: "``<resource_group_name>``"`
- `**storage_account_name**: "``<storage_account_name>``"`
- `**container_name**: "``<container_name>``"`
- `**key**: "``dspm-control-plane-network-configuration.tfstate``"`
Replace the placeholders with the actual values for your storage services.
[See image.](#ds-control-plane-backendtf)
- Save the updated file.
-
Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To execute the planned changes to your infrastructure:
`terraform apply -auto-approve`
The `-auto-approve` flag skips the interactive approval step, automatically applying the changes.
Executing these steps creates the control plane network components.
- []Open a file explorer and browse to the location where the downloaded `.zip` file was extracted. Then, open the `worker-plane` folder.
- Locate and open the** **`backend.tf` file in a text editor.
-
Update the file with the name of the storage services where you want to store the Terraform state files.
For example:
- `**resource_group_name**: "``<resource_group_name>``"`
- `**storage_account_name**: "``<storage_account_name>``"`
- `**container_name**: "``<container_name>``"`
- `**key**: "``<name>``.tfstate``"`
Replace the placeholders with the actual values for your storage services.
[See image.](#ds-worker-plane-backendtf)
- Save the updated file.
-
Run the following commands:
-
To initialize the Terraform working directory:
`terraform init`
-
To verify the changes in the Terraform configuration:
`terraform plan`
-
To execute the planned changes to your infrastructure:
`terraform apply -auto-approve`
The `-auto-approve` flag skips the interactive approval step, automatically applying the changes.
Executing these steps creates the worker plane network components.
[]![Editing the backend.tf file for updating the configuration details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-workerplane-backend-tf.png)
[]![Editing the backend.tf file for updating the configuration details](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-controlplane-backend-tf.png)
[]Download the Terraform templates file as a ZIP file and extract it to a folder on your system.
[Download the Terraform templates](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/aws_network_components_tf.zip)
The `.zip` file includes two folders, one for worker plane and another for control plane that contain policies and permissions required for DSPM to create required network configurations in the AWS organization.
[]To deploy the CloudFormation template:
- [1. Download the CloudFormation template.](#download_CFT)
- [2. Create Stack for control plane VPC in the AWS Management Console.](#create_controlplane_stacks)
- [3. Create Stack for worker plane VPC in the AWS Management Console.](#create_workerplane)
[]Download the CloudFormation templates file as a ZIP file and extract it to a folder on your system.
[Download the CloudFormation templates](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/aws_network_components_cft.zip)
The `.zip` file includes two YAML files that contains policies and permissions required for DSPM to create required network configurations in the AWS organization.
[]
- Sign in to the root account [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **Stacks**.
-
Click **Create Stack**, and then select **With new resources (standard)**.
[See image.](#create-worker_stack)
-
On the **Create stack** page:
- **Prerequisite - Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Browse to the location where the downloaded .zip file is extracted, select the **aws_worker_plane_network_components_cft.yml** file, and then click **Open**.
[See image.](#choose_worker-template)
- Click **Next**.
-
On the **Specify Stack Details** page:
- **Stack name**: Enter a unique name for the Stack.
- For the **Parameters** section:
- **Name for the network components**: Enter the name for the network components.
- **Worker plane VPC CIDR range**: Enter the IPV4 address range for the VPC, preferably `/24`.
- **Worker plane public subnet A CIDR range**: Enter the IPV4 address range for the first public subnet CIDR, preferably `/24`.
- **Worker plane public subnet B CIDR range**: Enter the IPV4 address range for the second public subnet CIDR, preferably `/24`.
- **Worker plane private subnet A CIDR range**: Enter the IPV4 address range for the first private subnet CIDR, preferably `/24`.
- **Worker plane private subnet B CIDR range**: Enter the IPV4 address range for the second private subnet CIDR, preferably `/24`.
- **Control plane VPC CIDR range**: Enter the IPv4 address range for the control plane VPC.
[See image.](#specify-workerplane-details)
- Click **Next**.
- On the **Configure Stack options** page, click **Next**.
-
On the **Review and create** page, review the Stack details of worker plane VPC.
[See image.](#workerplane-review)
- Click **Submit**.
Repeat steps for all other worker regions.
If you encounter a conflicting S3 bucket error during Stack creation, try deleting the existing bucket and retry the Stack creation. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/delete-bucket.html).
[]![Specifying the stack details for the control plane network in AWS CloudFormation.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/specify-workerplane-details.png)
[]![Creating a stack set in AWS CloudFormation and selecting the worker plane YAML file to configure the network.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/upload_worker_plane.png)
[]
Before creating a new Stack for the new control plane, delete the old control plane's existing infrastructure to avoid conflicts.
- Sign in to the root account [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation**.
- In the left-side navigation, select **Stack**.
-
Click **Create Stack**, and then select **With new resources (standard)**.
[See image.](#create-stack-orch)
-
On the **Choose a template** page:
- **Prerequisite - Prepare template**: Select **Choose an existing template**.
- **Specify template**: Select **Upload a template file** and click **Choose file**. Browse to the location where the downloaded .zip file is extracted, select the **aws_control_plane_network_components_cft.yml** file, and then click **Open**.
[See image.](#choose-template)
- Click **Next**.
-
On the **Specify Stack Details** page:
- **Stack name**: Enter a unique name for the Stack.
- For the **Parameters** section:
- **Name for the network components**: Enter the name for the network components.
- **Control plane VPC CIDR range**: Enter the IPV4 address range for the VPC, preferably `/24`.
- **Control plane public subnet CIDR range**: Enter the IPV4 address range for the public subnet CIDR, preferably `/24`.
- **Control plane private subnet CIDR range**: Enter the IPV4 address range for the private subnet CIDR, preferably `/24`.
[See image.](#specify-controlplane-details)
- Click **Next**.
-
On the **Review** page, review the Stack details of control plane VPC.
[See image.](#controlplane-review)
- Click **Submit**.
If you encounter a conflicting S3 bucket error during Stack creation, try deleting the existing bucket and retry the Stack creation. To learn more, refer to the [AWS documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/delete-bucket.html).
[]![Reviewing the stack set details for the worker plane network in AWS CloudFormation.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-stack-workerplane-review.png)
[]![Reviewing the stack set details for the control plane network in AWS CloudFormation.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-stack-controlplane-review.png)
[]![Specifying the stack set details for the control plane network in AWS CloudFormation.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/specify-controlplane-details.png)
[]![Creating a stack set in AWS CloudFormation and selecting the worker plane YAML file to configure the network.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/upload_control_plane.png)
[]![The Stacks page with an annotation around the option with new resources (standard).](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-create-stack.png)
[]![The Stacks page with an annotation around the option with new resources (standard).](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-create-stack.png)
- []Sign in to the [AWS console](https://aws.amazon.com/console/).
- Go to the **VPC **page and click **Create VPC**.
-
Under **Create VPC**:
- **Resources to create**: Select **VPC and more**.
- **Name tag auto-generation**: Enter the name tag for the VPC and its associated resources.
- **IPV4 CIDR block**: Enter the IPV4 address range for the VPC, preferably `/24`.
- **IPv6 CIDR block**: Select **No IPv6 CIDR block**.
- **Tenancy**: Retain the default value.
- **Number of Availability Zones (AZs)**: Select at least 1 AZ.
- **Customize AZs**: Retain the default value.
- **Number of public subnets**: Select **1**.
- **Number of private subnets**: Select **1**.
- **Customize subnets CIDR blocks**: Retain the default value.
- **NAT ateways**: Select **In 1AZ**.
- **VPC endpoints**: Select **S3 Gateway**.
- **DNS options**: Select the **Enable** **DNS hostnames** and **Enable** **DNS resolution** checkboxes.
[See image.](#ds-aws-createvpc)
- Click **Create VPC**.
- []Sign in to the [AWS console](https://aws.amazon.com/console/).
- Go to the **VPC** page and click **Create VPC**.
-
Under **Create VPC**:
- **Resources to create**: Select **VPC and more**.
- **Name tag auto-generation**: Enter the name tag for the VPC and its associated resources.
- **IPV4 CIDR block**: Enter the IPV4 address range for the VPC, preferably `/24`.
- **IPv6 CIDR block**: Select **No IPv6 CIDR block**.
- **Tenancy**: Retain the default value.
- **Number of Availability Zones (AZs)**: Select **at least 2 AZs**.
- **Customize AZs**: Retain the default value.
- **Number of public subnets**: Select **2**.
- **Number of private subnets**: Select **2**.
- **Customize subnets CIDR blocks**: Retain the default value.
- **Private subnet**: Ensure that at least 50 IPs are available.
- **NAT gateways**: Select** In 1 AZ**.
- **VPC endpoints**: Select **S3 Gateway**.
- **DNS options**: Select the **Enable** **DNS hostnames** and **Enable** **DNS resolution** checkboxes.
[See image.](#ds-aws-createworkerplanevpc)
- Click **Create VPC**.
Repeat the steps for other target regions.
- []In the [AWS console](https://aws.amazon.com/console/), go to the **Security group** page.
- Click **Create Security Group**.
- Enter the **Name** and **Description** for the security group.
- Select the **Control plane VPC** created in the previous section.
- Do not add any inbound rules.
- In the **Outbound rules** section:
- **Type**: Select **HTTPS**
- **CIDR**: Select **0.0.0.0/0**.
-
Add tags if required.
[See image.](#ds-aws-createsg)
- Click **Create Security Group**.
- []In the [AWS console](https://aws.amazon.com/console/), go to the **Security group** page.
- Click **Create Security Group**.
- Enter the **Name** and **Description** for the security group.
- Select the worker plane VPC created in the previous section.
- In the **Inbound rules** section, select the following from the **Type** and **Destination** drop-down menus respectively:
- **HTTPS**, **Control plane VPC**
- **PostgreSQL**, **Worker plane VPC**
- **MYSQL/Aurora**, **Worker plane VPC**
- In the **Outbound rules** section, select the following from the **Type** and **Destination** drop-down menus respectively:
- **HTTPS**, **0.0.0.0/0**
- **PostgreSQL**, **Worker plane VPC**
- **MYSQL/Aurora**, **Worker plane VPC**
-
Add tags if required.
[See image.](#ds-aws-wp-sg)
-
Click **Create Security Group**.
Repeat the steps for other target regions.
The DB subnet group is required for DSPM to be able to scan the RDS databases.
- []In the [AWS console](https://aws.amazon.com/console/), go to the **Subnet group** page.
- Click **Create DB subnet group**.
- Enter the **Name** and **Description** for the DB subnet group.
- Select the worker plane VPC from the drop-down menu.
-
Select at least two AZs and their corresponding private subnet in those zones.
[See image.](#ds-aws-add-dbsubnetgrp)
-
Click **Create**.
The DB subnet group is created. Repeat the steps to create DB subnet groups in other target regions.
[]![The Create VPC section with fields to input VPC settings.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-createvpc-page.png)
[]![The Create security group page with fields for basic details, inbound and outbound rules, and tags.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-createsgpage.png)
[]![The Create VPC section with fields to input worker plane VPC settings.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-aws-workerplanevpc.png)
[]![The Peering connections page with an annotation around the Create peering connection.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-aws-createpeerbutton.png)
[]![The Create peering connections page, configuring the settings for a new peer connection.](/downloads/dspm/administration/cloud-accounts-onboarding/microsoft-azure-cloud-accounts/configuring-azure-network/ds-aws-addpeersettings.png)
[]![The new vpc peering page displaying the details of the vpc, with an annotation around the Accept request option.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-acceppeeringoption.png)
[]![The Accept the peer connection request page displaying the vpc details to accept the vpc peering.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-acceptpeerreq.png)
[]
![The Create security group page with fields for basic details, inbound and outbound rules, and tags.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-workerplanesecuritygroup.png)
[]![The Create DB subnet group page with fields for group details, adding subnets, and selected subnets.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-addsubnetgroup.png)
[]![The Edit routes page for adding private subnets for control, worker planes, and route for NAT Gateway.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/configuring-aws-network/ds-aws-edit-routetable.png)