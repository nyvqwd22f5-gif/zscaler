# Deploying Zscaler Cloud Connector with Amazon Web Services
Source: https://help.zscaler.com/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services
PDF: https://help.zscaler.com/pdf/com/en/1420746.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Cloud Connector as an Amazon Machine Image (AMI) on Amazon Web Services (AWS), and post-deployment configurations.
Do not run both Auto Scaling Group (ASG) and non-ASG deployments within the same Virtual Private Cloud (VPC).
Prerequisites
Make sure the following prerequisites are met.
If you have already created a dedicated admin role and role-based administrator for Cloud Connector deployment, you can skip the first two steps.
- [1. Configure a new admin role.](#AdminRole)
- [2. Configure a new role-based administrator.](#configure-role-based-admin)
- [3. Retrieve the API key.](#apikey)
- [4. (Optional) Add a location template.](#location)
- [5. Configure a cloud provisioning template.](#cloudprovisioning)
- [6. Review the specifications and sizing requirements.](#specs)
- [7. Review the firewall requirements.](#firewall-requirements)
- [8. Download the deployment templates.](#CFT-Templates)
- [9. Create an EC2 instance access key pair.](#KeyPair)
- [10. Store your credentials in AWS Secrets Manager.](#StoreCredentials)
- [11. Configure your VPC.](#VPC)
- [12. Create an Amazon S3 bucket for Auto Scaling (advanced deployment).](#S3)
[]Zscaler recommends creating a dedicated admin role for Cloud Connector deployment. To configure a new [admin role](/cloud-branch-connector/adding-admin-roles):
- Log in to the [Zscaler Cloud & Branch Connector Admin Portal ](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal)as a[ super admin](/cloud-branch-connector/adding-super-admins).
- Go to **Administration** >** Role Management**.
- Click** Add Admin Role**.
- In the **Add Admin Role** window:
- **Name**: Enter a unique name for the admin role (e.g., CloudConnector-Deployment-Role).
- **Permissions**: Ensure that the admin has full access to **Location Management **and** Cloud Connector Provisioning**. Set all other permissions to** None**.
[See image.](#add-admin-role)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
- [In Zscaler Cloud Connector](#For-cloud-connector)
- [In ZIdentity](#for-zidentity)
[]
After configuring the admin role, create a new[ role-based administrator](/cloud-branch-connector/about-administrators) dedicated to Cloud Connector deployment. To add a new [admin](/cloud-branch-connector/adding-admins):
- Go to** Administration >** **Administrator Management** >** Administrators**.
- Click** Add Admin**.
- On the** Add Admin **page:
- **Login ID**: Create a new login username for Cloud Connector deployment (e.g., CloudConnectorDeploy).
- **Email**: Enter your email address.
- **Name**: Enter a new name for the specified Cloud Connector deployment account (e.g., Cloud Connector Deploy Service Account).
- **Role**: Select the newly created Cloud Connector deployment role.
- **Status**: Set the status to **Enabled**.
- **Scope**: Set the scope to **Organization**.
- **Comments**: (Optional) Enter any additional information about this admin.
- **Password**: Enter a new password for your admin account.
[See image.](#Add-Admin-Dedicated)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]
For a Cloud Connector tenant linked to a ZIdentity service, after configuring the admin role in the Cloud & Branch Connector Admin Portal, create administrators from the ZIdentity Admin Portal. You must create and manage the Cloud Connector admin account within the ZIdentity Admin Portal for these tenants.
To add a new admin:
- Log in to the [ZIdentity Admin Portal](/zidentity/accessing-and-navigating-zidentity-admin-portal).
- Go to **Directory **>** Users**.
-
Click **Add User**.
[See image.](#add-users)
The **Add User** window appears.
-
On the **General **tab:
- **Login ID**:** **Enter a user ID.** **The user ID consists of a username and domain name in email format (e.g., `username@domain.com`). The username must be unique, and its domain must belong to the organization.
- **First Name**: Enter the first name of the user.
- **Last Name**: Enter the last name of the user. The user's full name is created based on what you enter in the **First Name** and **Last Name **fields and is displayed in the **Name **field.
- **Primary Email**: Enter the user's primary email address, where they can receive the password link.
- **Status**: Enable the user.
[See image.](#Add-user-page)
- Click the **Security Settings** tab. From the **Password Option **drop-down menu, select **Set by Administrator**. The following fields appear:
- **Password**: Enter a password for the user.
- **Confirm Password**:** **Re-enter the user's password.
- **Prompt for Password Change After the Initial Log In**: Deselect the checkbox. This option is selected by default.
- [See image.](#security-settings-page)
- Click **Save**. The user is created in the ZIdentity Admin Portal.
-
Go to **Administration **> **Entitlements **> **Administrative **> **Zscaler Cloud and Branch Connector**.
[See image.](#select-cloud-and-branch-connector)
-
On the **Users **tab, click **Assign Users**.
[See image.](#Assign-users)
- On the **Select Users & Roles** page, select the Cloud Connector user that you created in ZIdentity Admin Portal.
-
In the **Role **column, select a role that you configured in the Cloud & Branch Connector Admin Portal in [step 1](#AdminRole).
[See image.](#Role-assignment)
The roles in the Cloud & Branch Connector Admin Portal are automatically synced to ZIdentity at regular intervals. If the role is not visible, you can perform a manual sync from the **Users **tab > **Manage **> **View Roles** page.
[See image.](#manual-sync)
- Click **Next**.
-
On the **Summary **page, review the assignment details and click **Assign**.
[See image.](#summary-page)
The selected users are assigned to the Cloud & Branch Connector with administrative privileges.
[]
![Users page with Add User button highlighted.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/add-users.png)
[]
![Add User page displaying new user creation.](/downloads/zidentity/administration/users/adding-users/zidentity-add-user-drawer.png)
[]
![Security settings tab displaying user configuration for password option and 2FA.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/Secuity-settings1.png)
[]
![Administrative Entitlements page with Zscaler Cloud and Branch Connector service highlighted.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/Admin-entitlements-C-and-B.png)
[]
![Users tab on the Administrative Entitlements page with Assign Users button highlighted.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/Assign-Users1.png)
[]
![Select Users & Roles page displaying users and role assignments for Zscaler Cloud and Branch Connector service.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/Role-assignment.png)
[]
![Summary page displaying the preview of users and role assignments.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/Summary-page.png)
[]
![Application Detail window displaying the roles added for Zscaler Cloud and Branch Connector with Sync button highlighted.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/draft-deploying-zscaler-cloud-connector-amazon-web-services-doc-60361/manual-syc.png)
[]To retrieve the API key:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **API Key Management**.
- From the[ API Key Management](/cloud-branch-connector/about-api-key-management) page, copy the API key and store it in a secure location. Cloud Connector uses the API key to authenticate and register the AMI with Zscaler.
[See image.](#API-Key-Management)
If the API is not available, click **Add Cloud Service API Key** to add an API key. To learn more, see [Managing Organization API Keys](/cloud-branch-connector/managing-organization-api-keys#AddNewKey).
[]You do not need to configure location templates because [locations](/cloud-branch-connector/about-locations) are created automatically when you deploy Cloud Connector to a cloud provider such as AWS. Optionally, you can configure your own location template:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **Location Templates**.
- Click **Add Location Template**. The **Add Location Template** window opens.
- In the **Name **field, enter a name for the location template.
- (Optional) In the **Template Prefix** field, enter a prefix for the location template. All locations created using this location template contain this prefix.
- In the **Gateway Options** section:
- (Optional)** Enable XFF Forwarding**: Enable this setting if you want the Zscaler service to use the X-Forwarded-For (XFF) headers that your on-premises proxy server inserts in outbound HTTP requests.
- (Optional)** Enforce Authentication**: Enable this setting to require users from this location to authenticate to the service.
- (Optional) **Enable Caution**: Enable this setting to display an end user notification for unauthenticated traffic. If you do not enable this setting, the action is treated as an allow policy.
- (Optional)** Enable AUP**: Enable this setting to display an Acceptable Use Policy (AUP) for unauthenticated traffic and require users to accept it. If you enable this setting, the **Custom AUP Frequency (Days)** field appears. Enter in days how frequently the AUP is displayed to users.
- **Enforce Firewall Control**: Enable this setting to enable the service's firewall controls. If you enable this setting, the **Enable IPS Control** setting appears. Select this setting to enable Intrusion Prevention System (IPS) controls for the location template. To enable IPS controls, you must be subscribed to the advanced firewall SKU.
- (Optional)** Enforce Bandwidth Control**: Enable this setting to enter the maximum bandwidth limits for Download (Mbps) and Upload (Mbps).
[See image.](#add-location-template-optional)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]Configure a [cloud provisioning template](/cloud-branch-connector/configuring-cloud-provisioning-template) and copy the cloud provisioning URL to deploy Cloud Connector on AWS. To configure a cloud provisioning template:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **Provisioning & Configuration **>** Cloud Provisioning**.
- Click **Add Cloud Connector Provisioning Template**.
- On the** Cloud Provisioning Template **page:
- **Name**: Enter a name for the cloud provisioning template.
- **Description**: Enter a description of the cloud provisioning template.
- **Cloud Provider**: Select** AWS** as the cloud provider.
- **Location Creation**: This field is set to **Automatic**.
- **Location Template**: From the drop-down menu, select the **Default Location Template **or another template.
- **Cloud Connector Group Creation**: This field is set to** Automatic**.
-
**VM Size**: Select from **Small**,** Medium**, or** Large** for your VM size. **Small** is set by default when Auto Scaling is enabled.
Zscaler recommends selecting the **VM Size** as **Small**.
- **Auto Scaling**: Enable or disable Auto Scaling.
Cloud Connector with Auto Scaling requires a new provisioning template with Auto Scaling set to Enabled. To enable Auto Scaling, contact Zscaler Support.
- Click **Save**.
- From the [Cloud Provisioning Template](/cloud-branch-connector/about-cloud-provisioning-templates) page, in the Template Name column, click the Expand icon and copy the cloud provisioning URL. Store the cloud provisioning URL in a secure location.
[See image.](#cloud-provisioning-URL)
[]To deploy Zscaler Cloud Connector on AWS, ensure the following:
- You have a subscription to Zscaler Cloud Connector in the AWS Marketplace.
- [Commercial AWS Marketplace](https://aws.amazon.com/marketplace/pp/prodview-cvzx4oiv7oljm)
- [China AWS Marketplace](https://awsmarketplace.amazonaws.cn/marketplace/pp/prodview-d2em5t67apisy)
- Your AMI is configured with the latest software version. To learn about identifying the Cloud Connector version in AWS, see [Identifying the Zscaler Cloud Connector Version](/cloud-branch-connector/identifying-zscaler-cloud-connector-version).
- You have a valid AWS account with Administrator permissions.
-
[]Your VM meets the following specifications:
- Small VM: Requires one of the following Elastic Compute Cloud (EC2) instances: m5n.large, c5a.large, m6i.large (recommended), or c6i.large. These VMs deploy with two network interfaces.
- Medium VM (deprecated): Requires one of the following EC2 instances: m5n.4xlarge, m6i.4xlarge (recommended), or c6i.4xlarge. These VMs deploy with 5 network interfaces.
-
Large VM (deprecated): Requires one of the following EC2 instances: m5n.4xlarge, m6i.4xlarge (recommended), or c6i.4xlarge. These VMs deploy with 6 network interfaces.
For details about these instances, refer to the [AWS specifications](https://aws.amazon.com/ec2/instance-types/).
AWS Marketplace restricts instances to those that Zscaler validated. Zscaler periodically reviews and updates this list. Zscaler cannot guarantee that VMs deployed on unsupported instances will function properly. For the best performance and security, always deploy the latest available AMI and the recommended m6i instance.
Your Cloud Connector instance size selection of small, medium (deprecated), or large (deprecated) must match the selected VM size of the [configured cloud provisioning template](/cloud-branch-connector/configuring-cloud-provisioning-template). If the sizing demonstrated in the [cloud provisioning URL](/cloud-branch-connector/about-cloud-provisioning-templates) and the deployment template do not match, Cloud Connector deployment is unsuccessful.
The Amazon EC2 M5 and C5 instance families are no longer available from the AWS Marketplace or Zscaler deployment templates. If you have any existing Cloud Connector deployments based on M5 or C5 instances (such as m5.large or c5.large), redeploy and migrate them to one of the supported instances listed above.
[]
The Cloud Connector instance requires only outbound connections to the Zscaler cloud and does not require any inbound connections to your network from the Zscaler cloud. To view the outbound access requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/cloud-branch-connector.
You can find the <Zscaler Cloud Name> in the URL you use to log in to the Cloud & Branch Connector Admin Portal. For example, if you log in to connector.zscaler.net, then go to https://config.zscaler.com/**zscaler.net**/cloud-branch-connector. To learn more, see [What Is My Cloud Name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
[]Infrastructure as Code (IaC) deployment templates are available for download on [GitHub](https://github.com/zscaler) to help you deploy Cloud Connector in AWS. Use the [AWS CloudFormation repository](https://github.com/zscaler/cloud-native-aws-cloud-connector-deploy) to download and create the deployment resources to deploy and operate Cloud Connector in an existing VPC. There are several different deployment methods depending on the deployment template you select.
To learn more about the resources created when you deploy the AWS CloudFormation templates, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
[]Key pairs are used to connect to your Cloud Connector Instance. To create a key pair:
- Log in to the [Amazon EC2 console](https://console.aws.amazon.com/ec2/).
- From the left-side navigation, select **Key Pairs**.
- Select **Create key pair**.
- On the** Key pair **page:
- **Name**: Enter a name for your key pair.
- **Key pair type**: Select **RSA**.
- **Private key file format**: Select **.pem **to save the private key in a format that can be used with SSH.
[See image.](#keypair2)
- Click **Create key pair**.
[]AWS Secrets Manager helps you manage and retrieve your secret credentials. To create and store your secrets from the AWS Secrets Manager console:
- Log in to the [AWS Secrets Manager console](https://console.aws.amazon.com/secretsmanager/home).
- On the **Service Introduction** page or the **Secrets List** page, select **Store a new secret**.
- On the **Choose Secret type** page, set the secret type to **Other type of secrets**.
- On the **Secret key/value** tab, enter the following secrets:
- **api_key**: Enter api_key for the name of your secret key. For the corresponding** **value**,** enter the value copied from the [API Key Management](/cloud-branch-connector/about-api-key-management) page in the Cloud & Branch Connector Admin Portal.
- **username**: Enter username for the name of your secret key. For the corresponding** **value**,** enter your dedicated deployment Cloud & Branch Connector Admin Portal username.
- **password**: Enter password for the name of your secret key. For the corresponding** **value**,** enter your dedicated deployment Cloud & Branch Connector Admin Portal password.
[See image.](#key)
-
Under **Encryption key**, select **aws/secrets manager**. You can use this encryption key, which is the AWS Key Management Service (KMS) key that AWS Secrets Manager creates by default, or select **Add new key **to create a custom-managed key in the AWS KMS.
If you create a custom AWS KMS key, the IAM user or role must have permissions set to** kms:decrypt**.
- Click** Next**.
- On the** Configure secret** page, enter the following information:
- **Secret name**: Enter a descriptive name to help you find your secrets.
- **Description**: Enter a description of the secrets.
- **Tags - optional**: Enter tags (key and value) associated with your secrets. You can add up to 50 tags.
- **Resource permissions - optional**: Enter a resource policy to access secrets across AWS.
- **Replicate secret - optional**: Replicate your secrets as read-only in other regions.
- Click **Next**.
- On the **Configure rotation - optional **page, configure the following information:
- **Automatic rotation**: Enable this setting to configure AWS Secrets Manager to rotate secrets automatically.
- **Rotation Schedule**: Select either **Schedule expression builder** or** Schedule expression**. For **Schedule expression**, you can enter a fixed rate in days for rotating your secret. For the **Schedule expression builder**, you can define your rotating schedule using cron expressions with a string of 6 inputs.
- **Rotation function**: Select a Lambda function to rotate your secrets. The rotation function updates your credentials in AWS Secrets Manager and updates the secrets to match.
- Click **Next**.
- On the** Review **page, review your secret information.
- Select **Store** to save your changes.
[]For AWS, you must deploy Cloud Connector in your Virtual Private Clouds (VPCs). A VPC is a region-specific, isolated virtual network used to launch resources, including your EC2 Cloud Connector instances. You can configure your VPC with your Cloud Connector instance in either a public or private subnet. When deploying in a public subnet, the subnet's traffic is routed through the internet gateway and can reach the public internet. When deploying in a private subnet, the subnet's traffic is not routed to an internet gateway and is instead routed through the NAT gateway, which has an elastic IP address. Zscaler recommends configuring your VPC with Cloud Connector in a private subnet.
This procedure assumes that you have already created an Amazon VPC. To learn more, refer to the [AWS product documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html).
- [Configure your VPC with Cloud Connector in a private subnet.](#privatesubnet)
- [Configure your VPC with Cloud Connector in a public subnet.](#publicsubnet)
[]
- Log in to the[ Amazon VPC console](https://console.aws.amazon.com/vpc/).
- After your VPC is created, select **Subnets **in the left-side navigation.
- On the **Subnets **page, click **Create subnet **and configure the following **Subnet settings**:
- **VPC ID**: From the drop-down menu, select the VPC.
- **Subnet name**: Enter a name for your subnet. A subnet is a range of IP addresses in your VPC. Create the following subnets:
- **Private-cloudconnector-subnet**: The subnet where the Cloud Connector AMI is deployed.
- **Private-workload-subnet**: The subnet where the workloads send internet traffic to Cloud Connector.
- **Public-nat-subnet**: The subnet where the NAT gateway is deployed. Cloud Connector routes this NAT gateway to establish outbound internet connectivity.
- **Availability Zone**: From the drop-down menu, select the zone where your subnet resides. A VPC spans all of the availability zones in that specified region.
- **IPv4 CIDR block**: Enter the specified IPv4 address range for your subnet. This is the primary Classless Inter-Domain Routing (CIDR) block for your VPC.
- **Tags**: (Optional) Enter tags (key and value) associated with your subnet. You can add up to 50 tags.
The allowed block size is between a /16 netmask (65,536 IP addresses) and /28 netmask (16 IP addresses). To learn more about VPC and subnet sizing, refer to the [AWS product documentation](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html#vpc-sizing-ipv4).
- After creating your subnets, select **Internet Gateways** in the navigation pane, then select **Create internet gateway**.
- On the **Create internet gateway** page, enter the **Name Tag **(key and value) and additional** Tags** (optional).
- Click **Create internet gateway**.
- Select the created internet gateway. Then, from the **Actions** drop-down menu, select **Attach to VPC**.
- Select your** VPC **from the list and click **Attach internet gateway**.
- After the internet gateway is attached to your VPC, select **NAT Gateways **in the navigation pane, then select **Create NAT Gateway**.
- On the **Create NAT gateway **page, enter the following **NAT gateway settings**:
- **Subnet**: From the drop-down menu, select a subnet in which to create the NAT gateway.
- **Elastic IP allocation ID**: From the drop-down menu, select an elastic IP address to assign to the NAT gateway.
- Select **Create a NAT Gateway**. After the status of the NAT gateway changes from** Pending **to** Available**, it is ready for use.
- From the navigation pane, select **Route Tables**, then click **Create route table **to set up where network traffic from your subnet or gateway is directed. To learn more, refer to the[ AWS product documentation](https://docs.aws.amazon.com/vpc/latest/userguide/WorkWithRouteTables.html#create-a-custom-route-table).
- On the **Create route table **page, enter the following **Route table settings**:
- **Name**: Enter a name for your route table. Create corresponding route tables and associate them with the corresponding subnets:
- **Private-cloudconnector-routing**: Associate the **private-cloudconnector-subnet **to the route table and add a default route** destination **CIDR (0.0.0.0/0)to the **target** NAT gateway.
- **Private-workload-routing**: Associate the **private-workload-subnet** to point the route table to Cloud Connector's traffic. After Cloud Connector has deployed, edit the route to redirect traffic to the elastic network interface (ENI) as described under [Managing the Cloud Connector](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services#deployment-status).
- **Public-nat-routing**: Associate the** public-nat-subnet** to the route table and add a default route **destination** CIDR (0.0.0.0/0)to the **target **internet gateway.
- **VPC**: From the drop-down menu, select the VPC for the specified route table.
- **Tags**: Enter tags (key and value) associated with your route table.
- Click **Create route table**.
![VPC configured with  Cloud Connector in a private subnet. ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-cloud-connector-amazon-web-services-draft/ConfigureVPC_PrivateSubnet.png)
[]
- Log in to the[ Amazon VPC console](https://console.aws.amazon.com/vpc/).
- After your VPC is created, select **Subnets **in the navigation pane.
- On the **Subnets **page, click **Create subnet **and configure the following **Subnet settings**:
- **VPC ID**: From the drop-down menu, select the VPC.
- **Subnet name**: Enter a name for your subnet. Create the following subnets:
- **Public-cloudconnector-subnet**: The subnet where the Cloud Connector AMI is deployed.
- **Private-workload-subnet**: The subnet where the workloads send internet traffic to Cloud Connector.
- **Availability Zone**: From the drop-down menu, select the zone where your subnet resides.
- **IPv4 CIDR block**: Enter the IPv4 address range for your subnet.
- **Tags**: (Optional) Enter tags (key and value) associated with your subnet. You can add up to 50 tags.
- After creating your subnets, select **Internet Gateways** in the navigation pane, then select **Create internet gateway**.
- On the **Create internet gateway** page, enter the **Name Tag **(key and value) and additional** Tags** (optional).
- Click **Create internet gateway**.
- Select the created internet gateway. Then, from the **Actions** drop-down menu, select **Attach to VPC**.
- Select your** VPC **from the list and click **Attach internet gateway**.
- From the navigation pane, select **Route Tables**, then click **Create route table **to set up where the Zscaler service directs network traffic from your subnet or gateway. To learn more, refer to the[ AWS product documentation](https://docs.aws.amazon.com/vpc/latest/userguide/WorkWithRouteTables.html#create-a-custom-route-table).
- On the **Create route table **page, enter the following **Route table settings**:
- **Name**: Enter a name for your route table. Create route tables and associate them with the corresponding subnets:
- **Public-cloudconnector-routing**: Associate the **public-cloudconnector-subnet** to the route table and add a default route** destination** CIDR (0.0.0.0/0)to the **target **internet gateway.
- **Private-workload-routing**: Associate the **private-workload-subnet** to point the route table to the Cloud Connector's traffic. After the Cloud Connector has deployed, edit the route to redirect traffic to the elastic network interface (ENI) as described under [Managing the Cloud Connector](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services#deployment-status).
- **VPC**: From the drop-down menu, select the VPC for the specified route table.
- **Tags**: Enter tags (key and value) associated with your route table.
- Click **Create route table**.
![VPC configured with  Cloud Connector in a public subnet. ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-cloud-connector-amazon-web-services-draft/ConfigureVPC_PublicSubnet.png)
Cloud Connector with Auto Scaling requires a new provisioning template with Auto Scaling set to Enabled. To enable Auto Scaling, contact Zscaler Support. To learn more about Auto Scaling, see [Understanding Cloud Connector Deployments with Amazon Web Services Auto Scaling Groups](/cloud-branch-connector/understanding-cloud-connector-deployments-amazon-web-services-auto-scaling-groups).
[]To deploy Cloud Connectors with Auto Scaling, you must first create a new Amazon Simple Storage Service (S3) bucket and store your Lambda ZIP file. To learn more about Amazon S3, refer to the[ AWS product documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
To create an Amazon S3 bucket:
- Log in to the [AWS Management Console](https://console.aws.amazon.com/vpc/).
- Click **S3**.
- On the **Amazon S3** page, click **Create bucket**.
- On the **Create bucket** page:
- **Bucket name**: Enter a unique name for your bucket. Copy the name to a secure location.
- **AWS Region**: From the drop-down menu, select the AWS region where you are deploying the Cloud Connectors with Auto Scaling.
- **Object Ownership**: To ensure that your account owns all objects in the S3 bucket, select **ACLs disabled (recommended)**. Policies specify access to the bucket and its objects.
- **Block Public Access settings for this bucket**: To ensure that public access to the S3 bucket and its objects is blocked, select** Block all public access**.
- **Bucket Versioning**:** Disable** is set by default. To preserve, retrieve, and restore every version of every object stored in your S3 bucket, select **Enable**.
- **Encryption type**: Select **Server-side encryption with Amazon S3 managed keys (SSE-S3)**.
- **Bucket Key**: Select **Disable **for the default server-side encryption of the bucket key.
- **Object Lock**: **Disable** is set by default. To permanently allow objects in your bucket to be locked, select **Enable**.
- Click** Create bucket**.
- Click your newly created S3 bucket.
- On the** Objects** tab, click** Upload**.
- In another web browser, navigate to GitHub and download the [Zscaler Cloud Connector Lambda ZIP file](https://github.com/zscaler/terraform-aws-cloud-connector-modules/blob/main/modules/terraform-zscc-asg-lambda-aws/zscaler_cc_lambda_service.zip).
- Drag and drop the entire ZIP file from the **Downloads** folder on your computer to the Amazon S3** Upload **page.
- Click **Upload**.
- Click the newly uploaded ZIP file.
- On the** Properties** tab, copy the **Key** to a secure location.
You need to select the **S3 Bucket Name **and **S3 Key** when defining parameters for the stack creation in the [AWS CloudFormation console with auto scaling](/cloud-branch-connector/deploying-zscaler-cloud-connector-amazon-web-services#autoscaling).
Deploying the Cloud Connector
This procedure describes the steps for deploying Zscaler Cloud Connector using a CloudFormation template. To learn more about deploying Zscaler Cloud Connector using a Terraform script, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
[]After you have met all the prerequisites, create a stack in the AWS CloudFormation console and deploy your Cloud Connector. Then, modify your route table and associated subnet to send workload traffic to the Cloud Connector.
The AWS CloudFormation console allows you to create stacks by uploading or creating a template file. A stack is a compilation of resources grouped into one collective unit. The template file describes the stack, which contains AWS and Zscaler Cloud Connector resources, and deploys all resources together as a group. To learn more, refer to the [AWS product documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/GettingStarted.html).
- Perform one of the following procedures to create a stack and deploy the Cloud Connector:
- [Create a stack in the AWS CloudFormation console.](#nonautoscaling)
- [Create a stack in the AWS CloudFormation console with Auto Scaling (Advanced Deployment).](#autoscaling)
-
Route workload traffic to the Cloud Connector.
After you finish deploying the Cloud Connector from the AWS CloudFormation console, modify your route table and associated subnet to ensure that traffic is sent from the private workload subnet to Cloud Connector. By default, traffic is going out of the workload subnet.
- Log in to the [Amazon VPC console](https://console.aws.amazon.com/vpc/).
- From the navigation pane, select** Route Tables**.
- Locate and click your workload route table.
- Click** Edit routes**.
- Click **Add route**.
- For the **Destination**, enter 0.0.0.0/0.
- For the **Target**, do one of the following:
- For non-GWLB-based deployments, select** Network Interface **and choose the **ENI** associated with your Cloud Connector service interface instance.
- For GWLB-based deployments, select **Gateway Load Balancer Endpoint** and choose the **GWLB Endpoint ID** associated with your Gateway Load Balancer.
- Click **Save Changes**.
[]
To create a stack in the AWS CloudFormation console:
- Log in to the[ AWS CloudFormation console](https://console.aws.amazon.com/cloudformation/home).
- Click **Create stack**.
- On the **Create stack** page, select **Template is ready**.
-
In** Step 1: Specify template**, select** Upload a template file** and upload the AWS CloudFormation deployment template from [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
To create the pre-deployment resources needed to deploy and operate the Cloud Connector, you must begin deployment in the AWS CloudFormation console with the** **[Pre-Deployment Template](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#pre-deployment). After you upload the** Pre-Deployment Template**, upload the [Starter Deployment Template](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#cf-default-deployment-template) to create the resources needed to deploy and operate the Cloud Connector in an existing VPC. After you upload the **Starter Deployment Template**, use the [Add-on Template with ZPA](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#cf-default-route53) to create the resources needed to enable the Zscaler Private Access (ZPA) DNS resolver capability, and use the [Add-on Template with Gateway Load Balancer (GWLB)](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#CF-GWLB) to distribute requests evenly across the Cloud Connector instances in all enabled availability zones.
- Click **Next**.
- In** Step 2: Specify stack details**, enter a **Stack name**.
- In the **Parameters **section, define the following parameters:
- **Starter Deployment Template**
- **Choose a VPC ID to Deploy Cloud Connector**: From the drop-down menu, select the VPC ID associated with your Cloud Connector.
- **Choose an Availability Zone to Deploy Cloud Connector**: From the drop-down menu, select the desired availability zone.
- **Choose a Subnet ID to Deploy**: From the drop-down menu, select the subnet ID associated with your Cloud Connectors. This subnet must reside in the same availability zone you selected in the previous step.
- **Zscaler Cloud Connector Instance Key Pair**: From the drop-down menu, select your EC2 instance access key pair.
- **Zscaler Cloud Connector Instance Size:** From the drop-down menu, select **small**, **medium**, or **large **for your EC2 instance type. Ensure that the instance type you select matches the VM size selected via the [Cloud Provisioning Template](/cloud-branch-connector/configuring-cloud-provisioning-template).
- **Zscaler Cloud Connector**: For your AWS EC2 instance type for the Cloud Connector instance, Zscaler recommends that you select **m6i.large**.
- **Cloud Connector Provisioning URL**: Enter your [Cloud Connector provisioning](/cloud-branch-connector/about-cloud-provisioning-templates) URL.
- **Secrets Manager Secret Name**: Enter the name of your secrets manager.
- **HTTP Monitor Probe Port**: Enter the HTTP monitor probe port for Cloud Connector to listen for monitoring health probes.
- **EBS Encryption Enabled:** From the drop-down menu, select **true **to enable EBS encryption (default) or **false **to disable it.
- **Add IAM Policy Permissions for AWS Tag Collection:** From the drop-down menu, select **true **to enable Cloud Tag Collection IAM Policy creation (default) or **false **to disable it.
- **Add Management Security Group Rule for Zscaler Support Server Connectivity:** From the drop-down menu, select **true **to enable the creation of a Management Security Group rule that permits egress TCP/12002 Zscaler Support Server Destinations (default) or **false **to disable rule creation. (Disabling is not recommended because this may prohibit Zscaler Support assistance if required.)
You must define the** HTTP Monitor Probe Port** parameter to check the liveliness of the designated Cloud Connectors and to achieve high availability.
- **Add-on Template with ZPA**
- **Your Zscaler Cloud Name**: From the drop-down menu, select the [name](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector) of your Zscaler cloud.
- **Your ZPA Cloud Name**: Select your ZPA cloud name. For all production clouds, your ZPA cloud name is **ZPA**. For all other clouds, your ZPA cloud name is **ZPA-Beta**.
- **ServiceENI ID of Zscaler CC**: Enter the elastic service interface (ENI) of the Zscaler Cloud Connector instance.
- **Domain Names for ZPA Application**: Enter the domain names for the ZPA applications. You can enter up to 10 domain names.
- **Add-on Template with High Availability (deprecated)**
- **Zscaler Cloud Connector Instance ID for each Cloud Connector**: Select the instance ID for each Cloud Connector.
- **Zscaler Cloud Connector Instance HTTP Probe Port for each Cloud Connector**: Enter the HTTP probe for each Cloud Connector.
- **List of Route Tables with affinity for each Cloud Connector**: Enter the route tables associated with each Cloud Connector.
- **S3 Bucket for Lambda Deployment Package**:** **Enter the AWS S3 bucket name for the specified region.
- **S3 Key for Lambda Deployment Package**: Enter the AWS S3 key for the Lambda deployment package ZIP file.
- **Add-on Template with Gateway Load Balancer (GWLB)**
- **ZS CC Instance IDs**: Select the instance ID for each Cloud Connector.
- **ZS CC instance Http Probe Port**: Enter the HTTP probe health check port for each Cloud Connector.
- **ZS CC GWLB enable cross zone forwarding**: To enable the cross-zone GWLB operation, select **true**. If enabled, the Gateway Load Balancer distributes requests evenly across the Cloud Connector instance in all enabled availability zones. If this option is disabled, requests are distributed in the workload's availability zone only.
The **Parameters **section is defined based on the template file selected. If you want to customize the parameters, Zscaler recommends editing the template file and deploying with the edited version.
- Click **Next**.
- In **Step 3:** **Configure stack options**, add **Tags** to apply to your stack and add** Permissions **by choosing an Identity and Access Management (IAM) role to define how CloudFormation can control resources in the stack. If you do not select a role, permissions are based on your user credentials.
- In the** Advanced options **section, set additional options for your **Stack policy**, **Rollback Configuration**, **Notification options**, and **Stack creation options**.
- In** Step 4: Review**, verify your network and Cloud Connector configurations.
- Select the **I acknowledge that AWS CloudFormation might create IAM resources** checkbox.
- Click **Create stack**.
[]
Cloud Connector with Auto Scaling requires a new provisioning template with Auto Scaling set to Enabled. To enable Auto Scaling, contact Zscaler Support.
To create a stack in the AWS CloudFormation console with Auto Scaling and GWLB:
Before uploading the [Starter Deployment Template with Auto Scaling and GWLB](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#cf-default-deployment-template-autoscaling) to the AWS CloudFormation console, you must create a new Amazon Simple Storage Service (S3) bucket and upload the[ Zscaler Cloud Connector Lambda ZIP file](https://github.com/zscaler/terraform-aws-cloud-connector-modules/blob/main/modules/terraform-zscc-asg-lambda-aws/zscaler_cc_lambda_service.zip). To learn more about Amazon S3, refer to the[ AWS product documentation](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html).
- Log in to the[ AWS CloudFormation console](https://console.aws.amazon.com/cloudformation/home).
- Click **Create stack**.
- On the **Create stack** page, select **Template is ready**.
-
In** Step 1: Specify template**, select** Upload a template file**, and upload the AWS CloudFormation deployment template from [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
To create the pre-deployment resources needed to deploy and operate the Cloud Connector, you must begin deployment in the AWS CloudFormation console with the** **[Pre-Deployment Template](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#pre-deployment). After you upload the** Pre-Deployment Template**, upload the [Starter Deployment Template with Auto Scaling and GWLB](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector#cf-default-deployment-template-autoscaling) to create the resources needed to deploy and operate the Cloud Connectors in an existing VPC.
- Click **Next**.
- In the **Parameters **section, define the following parameters:
- **Stack name**: Enter a stack name.
- **VPC ID**: From the drop-down menu, select the VPC ID associated with your Cloud Connectors.
- **Choose Availability Zones to Deploy Cloud Connector Resources**: From the drop-down menu, select the desired availability zones to deploy Zscaler Cloud Connectors in Auto Scaling Group, GWLB, and GWLB endpoints.
- **Subnet IDs for the Zscaler Cloud Connector Auto Scaling Group**: From the drop-down menu, select the subnets where the Auto Scaling Group is deployed.
- **Availability Zone based Auto Scaling Groups**: From the drop-down menu, select **true **to create one Auto Scaling Group for each availability zone (default) or **false **to create a single Auto Scaling Group spanning all selected availability zones.
- **Zscaler Cloud Connector AMI**: (Optional) Enter the ID of the AMI to use for deployment. Leave blank to deploy the latest marketplace AMI (recommended).
- **Zscaler Cloud Connector Instance Key Pair**: From the drop-down menu, select the instance key pair.
- **Existing IAM Role ARN to use for Zscaler Cloud Connector**: (Optional) Enter the Amazon Resource Name (ARN) that uniquely identifies an existing IAM role or instance profile.
- **Add IAM Policy Permissions for AWS Tag Collection**: From the drop-down menu, select **true **to enable Cloud Tag Collection IAM Policy creation (default) or **false **to disable it. This setting is enforced only if CloudFormation creates a new IAM Role.
- **Add Management Security Group Rule for Zscaler Support Server Connectivity**: From the drop-down menu, select **true **to enable the creation of a Management Security Group rule that permits egress TCP/12002 Zscaler Support Server Destinations (default) or **false **to disable rule creation. (Disabling is not recommended because it may prevent Zscaler Support from assisting you if needed.)
- **Existing Security Group ID to use for Zscaler Cloud Connector Management Interface**: (Optional) Enter the ID of an existing security group to apply to the management interface.
- **Existing Security Group ID to use for Zscaler Cloud Connector Service Interface**: (Optional) Enter the ID of an existing security group to apply to the service interface.
- **Secrets Manager Secret Name**: Enter the name of your AWS Secrets Manager. By default, the name is set to** ZS/CC/credentials**.
- **Zscaler Cloud Connector Instance Size**: By default, this field is set to **small**. Other sizes are not yet supported for Auto Scaling.
- **Zscaler Cloud Connector AWS EC2 Instance Type**: For your AWS EC2 instance type for the Cloud Connector instance, Zscaler recommends that you select **m6i.large**.
- **Cloud Connector Provisioning URL**: Enter your [Cloud Connector provisioning](/cloud-branch-connector/about-cloud-provisioning-templates) URL.
- **HTTP Monitor Probe Port**: Enter the HTTP monitor probe port for Cloud Connector to listen for monitoring health probes.
- **EBS Encryption Enabled**: From the drop-down menu, select **true **to enable Elastic Block Store (EBS) encryption (default) or **false **to disable it.
- **Lambda S3 Bucket Name**: Enter the name of the AWS S3 bucket in this region where the Lambda deployment package ZIP file exists.
- **Lambda S3 Key**: Enter the Lambda S3 key.
- **Auto Scaling Group Minimum Size**: Enter the minimum number of Cloud Connectors to maintain in the Auto Scaling group.
- **Auto Scaling Group Maximum Size**: Enter the maximum number of Cloud Connectors to maintain in the Auto Scaling group.
- **Auto Scaling Group Reuse Instances on Scale In**: Select** true **to enable Auto Scaling to reuse instances or **false** to terminate instances.
- **Auto Scaling Group Target CPU Utilization Value**: To track CPU use by the Auto Scaling policy, enter a target value number (recommended default 80%). The threshold triggers a scale in or scale out to keep the average percentage across all instances at or under the number you enter.
- **Auto Scaling Group Warm Pool Enabled**: From the drop-down menu, select **true **to enable Auto Scaling Group warm pool or **false **to disable it. When warm pool is enabled, the Auto Scaling Group can use pre-initialized ("warmed") EC2 instances to handle traffic increases.
- **Auto Scaling Group Warm Pool State**: From the drop-down menu, select the instance state of warm pool resources. Zscaler recommends selecting **Stopped** to reduce cost. This parameter is only enforced if you set **Auto Scaling Group Warm Pool Enabled** to **true**.
- **Auto Scaling Group Warm Pool Minimum Size**: Enter the minimum number of instances to maintain in the warm pool. This parameter ensures that a certain number of warmed instances are always available to handle traffic increases. This parameter is only enforced if you set **Auto Scaling Group Warm Pool Enabled** to **true**.
- **Auto Scaling Group Warm Pool Max Group Prepared Capacity**: Enter the maximum number of instances allowed in the warm pool or in any state except **Terminated** in the Auto Scaling group. This parameter is enforced only if you set **Auto Scaling Group Warm Pool Enabled **to **true**.
- **Log Group Retention**: From the drop-down menu, select the number of days to retain the log events in the specified log group.
- **GWLB Target Failover Rebalance Strategy**: From the drop-down menu, select **rebalance **to enable rebalance failover after you deregister a target or **no_rebalance** to disable it.
- **GWLB Flow Stickiness Strategy**: From the drop-down menu, select the distribution hash. Zscaler recommends selecting **5-tuple **for optimal load disbursement unless otherwise required for your specific environments.
- **Enable Cross-Zone Load Balancing**: From the drop-down menu, select **true **to enable cross-zone load balancing or **false **to disable it.
- **VPC Subnets to Create VPC Endpoints in (one per AZ)**: (Optional) Enter additional VPC subnets to create additional VPC endpoints. One additional subnet is allowed for each availability zone.
- **VPC Endpoint Service Principals**: (Optional) Enter a list of service principal Amazon Resource Names (ARNs) to restrict which VPC endpoints can associate with the GWLB Endpoint Service.
- **Require Acceptance For Newly Created VPC Endpoints?**: From the drop-down menu, select **true** to require the admin to manually accept the newly created VPC endpoints or** false** to not require the admin to manually accept them.
The **Parameters **section is defined based on the template file you select. If you want to customize the parameters, Zscaler recommends editing the template file and deploying with the edited version.
- Click **Next**.
- In **Step 3:** **Configure stack options**, enter **Tags** to apply to your stack and add** Permissions **by choosing an Identity and Access Management (IAM) role to define how CloudFormation can control resources in the stack. If you do not select a role, permissions are based on your user credentials.
- In the** Advanced options **section, set additional options for your **Stack policy**, **Rollback Configuration**, **Notification options**, and **Stack creation options**.
- In** Step 4: Review**, verify your network and Cloud Connector configurations.
- Select the **I acknowledge that AWS CloudFormation might create IAM resources** checkbox.
- Click **Create stack**.
[]
Managing the Cloud Connector
You can manage the Cloud Connector from the Cloud & Branch Connector Admin Portal. A deployed Cloud Connector is displayed on the dashboard. The [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation (shown below), and status of the Cloud Connector AMIs deployed in your cloud account.
[See image.](#geoview)
[]![The geo view provides the geographical location of the deployed  Cloud Connector.](/downloads/cloud-connector/administration/deploying-cloud-connector-amazon-web-services/Geoview_CloudConnector.png)
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding)
- [Log and Control Forwarding](/cloud-branch-connector/about-log-and-control-forwarding)
- [DNS Control](/cloud-branch-connector/about-dns-policies)
If you face any issues with your Cloud Connector deployment, see[ Troubleshooting Cloud Connector with Amazon Web Services.](/cloud-branch-connector/troubleshooting-cloud-connector-amazon-web-services)
[]![The Add Admin Role window demonstrating the dedicated admin role for  Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/AdminRole-Dedicated-CloudConnectorDeployment.png)
[]![The Add Admin window demonstrating the new Login ID and attached role for  Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/Add-Admin-DedicatedDeploymentAccount.png)
[]![The API Key located on the API Key Management page. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/API-Key-CloudConnectorDeployment.png)
[]![The Add Location Template window with a location created for  Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/AddLocationTemplate-Deployment.png)
[]![The Cloud Provisioning page demonstrating the Cloud Provisioning URL. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-cloud-connector-amazon-web-services-draft-doc-43694/CloudProvisioningTemplates_ProvisioningURL_AWS.png)
[]
[]
[]
[]
[]![Specific key/value pairs to be stored in the AWS Secrets Manager. ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-cloud-connector-amazon-web-services-draft/AWS_Secretkeysandvalues.jpg)
[]![The Create Key pair page in the EC2 console. ](/downloads/zscaler-tech-pubs-style-guide/draft-articles/deploying-cloud-connector-amazon-web-services-draft/KeyPair_AWS.jpg)