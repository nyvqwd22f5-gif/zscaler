# Deploying Zscaler Cloud Connector on the Google Cloud Platform
Source: https://help.zscaler.com/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1461611.pdf

This deployment guide provides information on prerequisites, how to deploy Zscaler Cloud Connector as a virtual machine (VM) on the Google Cloud Platform (GCP), and post-deployment configurations. This procedure describes the steps for deploying Zscaler Cloud Connector using Terraform. To learn more about the resources created when deploying Zscaler Cloud Connector, see [Deployment Templates for Zscaler Cloud Connector](/cloud-branch-connector/deployment-templates-zscaler-cloud-connector).
Before you run the Terraform deployment scripts, enable the following Google Cloud APIs:
- Compute Engine API
- Cloud DNS API
- Cloud Resource Manager API
- Identity and Access Management (IAM) API
- Secret Manager API
[]Prerequisites
Make sure the following prerequisites are met.
If you already created a dedicated admin role and role-based administrator for Cloud Connector deployment, you can skip steps** 1 **and** 2**.
- [1. Configure a new admin role.](#AdminRole)
- [2. Configure a new role-based administrator.](#Username-Password)
- [3. Retrieve the API key.](#apikey)
- [4. (Optional) Add a location template.](#location)
- [5. Configure a cloud provisioning template.](#cloudprovisioning)
- [6. Review the firewall requirements.](#firewall)
- [7. Create an admin service account used to run Terraform during deployment.](#ServiceAccount)
- [8. Store your secret credentials.](#StoreCredentials)
- [9. Create a service account for each VM to use after deployment.](#VMServiceAcct)
[]Zscaler recommends that you create a dedicated admin role for Cloud Connector deployment. To configure a new [admin role](/cloud-branch-connector/adding-admin-roles):
- Log in to the [Zscaler Cloud & Branch Connector Admin Portal ](/cloud-branch-connector/accessing-navigating-zscaler-cloud-branch-connector-admin-portal)as a[ super admin](/cloud-branch-connector/adding-super-admins).
- Go to **Administration** >** Role Management**.
- Click** Add Admin Role**.
- In the **Add Admin Role** window:
- **Name**: Enter a unique name for the admin role (e.g., CloudConnector-Deployment-Role).
- **Permissions**: Ensure that the admin has full access to **Location Management **and** Cloud Connector Provisioning**. Set all other permissions to** None**.
[See image.](#add-admin-role)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]After you configure the admin role, create a new[ role-based administrator](/cloud-branch-connector/about-administrators) dedicated to Cloud Connector deployment. To add a new [admin](/cloud-branch-connector/adding-admins):
- Go to** Administration >** **Administrator Management** >** Administrators**.
- Click** Add Admin**.
- On the** Add Admin **page:
- **Login ID**: Create a new login username for Cloud Connector deployment (e.g., CloudConnectorDeploy).
- **Email**: Enter your email address.
- **Name**: Enter a new name for the new Cloud Connector deployment account (e.g., Cloud Connector Deploy Service Account).
- **Role**: Select the newly created Cloud Connector deployment role.
- **Status**: Set the status as **Enabled**.
- **Scope**: Set the scope to **Organization**.
- **Password**: Enter a new password for your admin account.
[See image.](#Add-Admin-Dedicated)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]To retrieve the API key:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **API Key Management**.
- From the[ API Key Management](/cloud-branch-connector/about-api-key-management) page, copy the API key and store it in a secure location. Cloud Connector uses the API key to authenticate and register the GCP with Zscaler.
[See image.](#API-Key-Management)
[]You do not need to configure location templates because [locations](/cloud-branch-connector/about-locations) are created automatically when you deploy Cloud Connector to a cloud provider such as GCP. Optionally, you can configure your own location template:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **Location Templates**. The Add Location Template window opens.
- Click [**Add Location Template**](/cloud-branch-connector/configuring-location-template).
- In the **Name **field: Enter a name for the location template.
- In the **Template Prefix** field, enter a prefix for the location template. All locations created using this location template contain this prefix.
-
In the **Gateway Options** section:
- **Enable XFF Forwarding**: Enable this setting if you want the Zscaler service to use the X-Forwarded-For (XFF) headers that your on-premises proxy server inserts in outbound HTTP requests.
- **Enforce Authentication**: Enable this setting to require users from this location to authenticate to the service.
- **Enable Caution**: Enable this setting to display an end user notification for unauthenticated traffic. If you do not enable this setting, the action is treated as an allow policy.
- **Enable AUP**: Enable this setting to display an Acceptable Use Policy (AUP) for unauthenticated traffic and require users to accept it. If you enable this setting, the **Custom AUP Frequency (Days)** field appears. Enter in days how frequently the AUP is displayed to users.
- **Enforce Firewall Control**: Enable this setting to enable the service's firewall controls. If you enable this setting, the **Enable IPS Control** setting appears. Select this setting to enable Intrusion Prevention System (IPS) controls for the location template. To enable IPS controls, you must be subscribed to the advanced firewall SKU.
- **Enforce Bandwidth Control**: Enable this setting to enter the maximum bandwidth limits for Download (Mbps) and Upload (Mbps).
[See image.](#add-location-template-optional)
- Click **Save** and [activate the change](/cloud-branch-connector/saving-and-activating-changes).
[]Configure a [cloud provisioning template](/cloud-branch-connector/configuring-cloud-provisioning-template) and copy the cloud provisioning URL. To configure a cloud provisioning template:
- Log in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration **> **Provisioning Templates **>** Cloud Provisioning**.
- Click **Add Cloud Connector Provisioning Template**.
- On the** Cloud Provisioning Template **page:
- **Name**: Enter a name for the cloud provisioning template.
- **Description**: Enter a description of the cloud provisioning template.
- **Cloud Provider**: Select** GCP**.
- **Location Creation**: This field is set to **Automatic**.
- **Location Template**: From the drop-down menu, select the **Default Location Template **or another template.
- **Cloud Connector Group Creation**: This field is set to** Automatic**.
- **VM Size**: **Small **is set by default.
- Click **Save**.
- From the [Cloud Provisioning Template](/cloud-branch-connector/about-cloud-provisioning-templates) page, click the arrow in the **Template Name** column and copy the cloud provisioning URL. Store the cloud provisioning URL in a secure location.
[See image.](#cloud-provisioning-URL)
[]The Cloud Connector instance requires only outbound connections to the Zscaler cloud. It does not require any inbound connections to your network from the Zscaler cloud. To view the outbound access requirements for your specific account, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/cloud-branch-connector.
You can find the <Zscaler cloud Name> in the URL you use to log in to the Cloud & Branch Connector Admin Portal. For example, if you log in to connector.zscaler.net, then go to https://config.zscaler.com/zscaler.net/cloud-branch-connector. To learn more, see [What Is My Cloud Name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
[]To create the service account:
- Log in to the[ GCP console](https://console.cloud.google.com/).
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**.
- Click **Create Service Account**.
- On the** Service account details **page:
- **Service account name**: Enter a unique display name for the service account.
- **Service account ID**: Enter the service account ID.
- **Service account description**: (Optional) Enter a description of the service account's purpose.
[See image.](#serviceaccountdetails)
- Click **Create and Continue**.
- On the** Grant this service account access to project** page, from the **Select a role** drop-down menu, select **Compute Instance Admin (v1)**.
- Click **Add Another Role** and add the following roles:** Compute Network Admin**, **Compute Security Admin**,** Service Account Admin**,** Service Account User**, **Secret Manager Admin**, **project Iam Admin**, and optionally, **DNS Administrator**.
- Click **Done** to create the service account.
- Select the created service account, then click** Keys**.
- From the **Keys** page, click **Add Key** > **Create new key**.
- Select **JSON **as the **Key Type**, then click **Create**. The private key automatically downloads to your computer.
- Copy the JSON file to a secure location. Later, you use this file to reference the path to authenticate with Terraform.
[]Use one of the following methods to manage and retrieve your secret credentials.
- [GCP Secret Manager](#GCPSecretsManager)
- [Hashicorp Vault](#HashicorpVault)
[]To create and store your secret credentials in Secret Manager from the GCP console:
- Log in to the [GCP console](https://console.cloud.google.com/).
- From the left-side navigation, select **Security** > **Secret Manager**.
- Click **Create Secret**.
- On the** Secret details** page, enter a unique name for your secret.
- Under **Secret value**, enter your secret values using the format shown below:
- **username**: Enter username for the name of your secret key. For the corresponding** **value**,** enter your dedicated Cloud Connector deployment username.
- **password**: Enter password for the name of your secret key. For the corresponding** **value**,** enter your dedicated Cloud Connector deployment password.
-
**api_key**: Enter api_key for the name of your secret key. For the corresponding** **value**,** enter the value you copied from the [API Key Management](/cloud-branch-connector/about-api-key-management) page on the Cloud & Branch Connector Admin Portal.
Ensure that you manually enter the following JSON example so that it is formatted correctly before deployment. JSON does not allow tab spacing, so use regular spacing where appropriate:
`	{
"username": "cc-deploy-user@company.com",
"password": "cc-deploy-user-password",
"api_key": "ZscalerCompanyAPIKey"
}`
[See image.](#secretvalues)
- Under **Encryption key**, select **Google-managed encryption key**.
- Click** Create secret**.
- Copy the secret manager path to a secure location.
[]For information about creating and storing your secrets in Hashicorp Vault, see [Storing Your Secret Credentials in Hashicorp Vault for Google Cloud Platform-Based Cloud Connectors.](/cloud-branch-connector/storing-your-secret-credentials-hashicorp-vault)
[]Each VM needs a service account assigned to it. You can let Terraform create the service account during deployment, or manually create the service account before deployment. To manually create the service account, perform the following procedure:
- Log in to the [GCP Console](https://console.cloud.google.com/).
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**.
- Click **Create Service Account**.
- In the **Service account details** section:
- **Service account name**: Enter a unique display name for the service account. GCP generates a Service account ID based on this name.
-
**Service account ID**: If necessary, change the ID.
You cannot change the ID after the service account is created.
-
**Service account description**: (Optional) Enter a description of the service account's purpose.
[See image.](#SecretCredsSA)
- Click **Create and Continue**.
- On the **Grant this service account access to project** page, do one of the following, depending on the method you use to store and manage your secret credentials:
- **GCP Secret Manager**: From **Role **drop-down menu, select **Secret Manager Secret Accessor**.
- **HashiCorp Vault**: From **Role **drop-down menu, select **Service Account Token Creator**.
- Click **Done** to create the service account.
Deploying the Cloud Connector
After you have met all the prerequisites, deploy the Cloud Connector using Terraform and then modify your route table and associated subnet to send workload traffic to the Cloud Connector.
- [1. Deploy the Cloud Connector using Terraform.](#deploy)
- [2. Route workload traffic to the Cloud Connector.](#traffic)
[]
- Go to the [GCP on GitHub](https://github.com/zscaler/terraform-gcp-cloud-connector-modules) repository.
- On GitHub, click **Code** > **Download ZIP** to download the Terraform ZIP file.
- Log in to the [GCP console](https://console.cloud.google.com/).
- In the upper-right corner, click the **Activate Cloud Shell** icon
- In the upper-right corner of the** Cloud Shell Terminal**, click the three dots and click **Upload** to upload the ZIP file downloaded from GitHub.
- Click **Upload** again to upload the JSON file you secured when you created [the admin service account](#ServiceAccount).
- Unzip the Terraform ZIP file by running the following command:
`unzip terraform-gcp-cloud-connector-modules-main.zip`
- Identify the full path of the Terraform folder and JSON file.
- Navigate to the examples directory by entering `cd terraform-gcp-cloud-connector-modules-main/examples`.
- Enter `./zsec up `to initiate the deployment wizard. The deployment wizard automatically downloads, installs, and initializes the Terraform JSON file.
[]After you complete deployment, modify your route table and the associated subnet to ensure that traffic is sent from the private workload subnet to Cloud Connector. By default, traffic is going out of the workload subnet.
To send traffic to your deployed Cloud Connector:
- Log in to the[ GCP console](https://console.cloud.google.com/).
- From the left-side navigation, select **Compute Engine** > **VM Instances**.
- Select your newly created Cloud Connector workload instance, then click **Edit**.
- Copy the name of the Cloud Connector workload instance (e.g., zscc-workload-host-0yv34zh8).
- Paste the Cloud Connector workload instance under **Network Tags**.
- Click **Save**.
- From the left-side navigation, select **VPC Network** > **Routes**.
- On the **Routes **page, navigate to **Route Management**.
- Click **Create Route**.
- On the** Create a Route **page:
- **Name**: Enter a name for your route table.
- **Network**: Select the VPC where the workload is located (e.g., zscc-service-vpc-0yv34zh8).
- **Route type**: From the drop-down menu, select** Static route**.
- **IP version**: From the drop-down menu, select **IPv4**.
- **Destination IPv4 range**: Enter` 0.0.0.0/0`.
- **Priority**: Set the priority as an integer from `0` to `65535`.
- **Next hop**: From the drop-down menu, select **Specify a forwarding rule of internal TCP/UDP load balancer**.
- **Forwarding rule project**: From the drop-down menu, select the project in which the forwarding rule is located.
- **Forwarding rule name**: From the drop-down menu, select the rule to forward traffic to the Cloud Connector.
[See image.](#createroute)
- Click **Equivalent Command Line **to open the **gcloud command line**.
- Click **Run in Cloud Shell**.
- Attach the** network tag **to the string of the **Cloud Shell**.
- Press `Enter` to run the command in **Cloud Shell**. For example:
`Created [https://www.googleapis.com/compute/beta/projects/cc-poc-host-project-01/global/routes/route-from-workload-to-ilb-to-zscaler-cloud-connector].
NAME: route-from-workload-to-ilb-to-zscaler-cloud-connector
NETWORK: zscc-service-vpc-0yv34zh8
DEST_RANGE: 0.0.0.0/0
NEXT_HOP: 10.1.1.2
PRIORITY: 1000
`
- Go to **VPC Network **>** Routes** > **Route Management** to view your newly created route table.
Managing the Cloud Connector
You can manage the Cloud Connector from the Cloud & Branch Connector Admin Portal. A deployed Cloud Connector is displayed on the dashboard. The [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) page provides information on the name, group, location, geolocation (shown below), and status of the Cloud Connector VM instances deployed in your cloud account.
[See image.](#geo)
[]![The geo view provides the geographical location of the deployed Cloud Connector.](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/GCP_dashboard.png)
After verifying deployment, you can configure the following policies:
- [Traffic Forwarding](/cloud-branch-connector/about-traffic-forwarding)
- [Log and Control Forwarding](/cloud-branch-connector/about-log-and-control-forwarding)
- [DNS Control](/cloud-branch-connector/about-dns-policies)
[]![The Add Admin Role window demonstrating the dedicated admin role for Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/AdminRole-Dedicated-CloudConnectorDeployment.png)
[]![The Add Admin window demonstrating the new Login ID and attached role for Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/Add-Admin-DedicatedDeploymentAccount.png)
[]![The API Key located on the API Key Management page](/downloads/API-Key-CloudConnectorDeployment_2.png)
[]![The Add Location Template window with a location created for Cloud Connector deployment. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/AddLocationTemplate-Deployment.png)
[]![The Cloud Provisioning page demonstrating the Cloud Provisioning URL. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/Copy-CloudprovisioningURL.png)
[]![Service account details in the GCP console. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/3.%20IAM_service%20account%20name%20and%20description_then%20create%20and%20continue.png)
[]![The Create route page in the GCP console. ](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/ilb_route_3.png)
[]![The secret names and their corresponding values on the Secret details page.](/downloads/cloud-branch-connector/deployment-management/cloud-connector-deployment-management/deploying-zscaler-cloud-connector-google-cloud-platform/2.%20Secret%20Manager_name_secret%20value%20formatted_click%20create%20secret%20(1).png)
[]![Service account for VMs to use GCP functions](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/deploying-zscaler-cloud-connector-google-cloud-platform-draft-doc-55117/ServiceAccountforGCP_HCP.png)