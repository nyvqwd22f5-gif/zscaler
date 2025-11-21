# Adding Orchestrator Details and Configuring Regions
Source: https://help.zscaler.com/dspm/adding-orchestrator-details-and-configuring-regions
PDF: https://help.zscaler.com/pdf/com/en/1520276.pdf

The first step in the [onboarding process](/dspm/onboarding-aws-account) is to provide the orchestrator details and configure regions. DSPM uses the account details to generate a template to connect to the AWS account.
To add the orchestrator details and configure regions:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Click **Add New**.
-
In the **Select Cloud Provider **window:
- Under **Select Cloud Type**, click the** AWS **tile.
- Under **Select Onboarding Type**, click the **Standalone Account** tile.
[See image.](#select-cloud-provider)
- Click **Next**.
-
In the **Orchestrator Configuration** section:
- **DSPM Alias**: Enter a user-friendly name for the account.
- **Role Name**: Enter a unique role name. This role name is added as a prefix to all the IAM roles that are created during the onboarding process.
- **Orchestrator Account ID**: Enter the account ID of the account where you want to deploy the orchestrator template.
- **Select Orchestrator Region**: Select the region to deploy the template.
- **Network Configurations**: Select one of the following options:
- [Zscaler](#zscaler-regions)
- [Custom](#custom-network)
[See image.](#orch-configuration)
-
Click **Apply **to continue. Click **Reset **if you want to change the details.
If all the details are accurate, you are directed to the [Additional Configuration](https://help-internal.zscaler.com/tech-pubs-drafts/adding-orchestrator-details-and-configuring-regions-draft-1#additionalconfig) section.
[]In the **Additional Configuration** section, you can configure [custom tags](/dspm/managing-custom-tags) and [evidence storage](/dspm/managing-evidence-configuration). Click **Skip This Step **to configure the additional details after completing the onboarding process and go to [Deploy Orchestrator](/dspm/deploying-orchestrator-template) section.
[See image.](#skip-additionalconfig)
- [Custom Tags](#singleaccount-customtags)
- [Evidence Storage](#singleacct-evidence)
[See image.](#addtionalconfig)
After configuring, you are directed to the [Deploy Orchestrator](/dspm/deploying-orchestrator-template) section to deploy the orchestrator template.
[]DSPM discovers files and tables containing sensitive data and generates snippets of evidence data to investigate and validate the findings. You can choose an existing S3 bucket or configure a new one to store these evidence snippets.
To add evidence storage:
- Click **Add Evidence Storage**.
-
On the **Evidence Configuration** page, select one of the following storage types:
- [Custom S3 bucket](#single-custom-evidence)
- [Zscaler Managed S3 bucket](#single-zscaler-evidence)
[See image.](#customs3-bucket)
[]Click **Configure Services **to select the services and regions that DSPM must monitor.
-
On the **Manage services to monitor** page, select the AWS services and click **Next**. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
[See image.](#zscaler-services)
The **Unmanaged Database** service is disabled for Zscaler network configuration.
- On the **Configure regions for monitoring and scanner's configuration** page, select the regions. DSPM creates and deploys resources required for scanning only in the selected regions.
-
Click **Done**.
[See image.](#configure-regions-zscaler)
- []Enter the following information for the orchestrator instance:
- **Subnet ARN**: The private subnet ARN.
- **Security Group ID**: The security group ID.
- Click **Configure Services **to select the services and regions that DSPM must monitor.
-
On the **Manage services to monitor** page, select the AWS services and click **Next**. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
[See image.](#custom-services)
-
On the **Configure regions for monitoring and scanner's configuration** page, select the regions and enter the following for each selected region. DSPM creates and deploys resources required for scanning only in the selected regions.
- **Subnet ARN**: The subnet where the scanner instances must be launched.
- **Security Group ID**: The security group ID that controls network traffic to and from the scanner instances.
- **DB Subnet Group ARN**: (Optional) The database subnet group ARN. This is required for DSPM to scan the RDS databases.
[See image.](#byon-configure-regions)
[]You can use an existing S3 bucket to collect evidence data. DSPM uploads classified data into the specified S3 bucket.
- **S3 Bucket Name**: The name of the S3 bucket.
- **S3 Bucket Account ID**: The 12-digit account ID.
- **KMS Key ARN**: The symmetric KMS key ARN. This key is used to encrypt the evidence data in the S3 bucket.
[]DSPM creates an S3 bucket in the orchestrator account to upload classified data.
[]Custom tags are attached to the resources created by DSPM that enable you to distinguish resources in the organization.
To add custom tags:
- Click **Add Custom Tags**.
-
On the **Add Custom Tags** page, enter a key and value pair for the tag.
Ensure to [follow the guidelines](/dspm/managing-custom-tags) while entering key-value pairs for custom tags.
-
Click **Add More**, and enter key-value pairs to add more tags.
[See image.](#addcustomtags)
- Click **Done**.
[]![The select cloud provider window with annotations around aws and standalone account tiles.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-select-cloudtype-onboarding-type.png)
[]![The configure regions page with list of regions supported by DSPM.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-zscaler-regions_0.png)
[]![The configure regions page for custom network with the list of regions supported by DSPM/](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-custom-regions_0.png)
[]![The Manage services to monitor page with list of available AWS services.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-zscaler-services_0.png)
[]![The Manage services to monitor page with list of available AWS services.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-custom-services_0.png)
[]![The Orchestrator configuration section with the required fields and options to configure services, custom tags, and evidence.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-orchestrator-configuration.jpg)
[]![The Evidence configuration page for Custom S3 bucket.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-aws-evidenceconfig.png)
[]
![The Add Custom Tags page to add key and value pairs that must be attached to the DSPM resources.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-add-custom-tags.jpg)
[]
![The Additional Configuration section with annotation around Skip this step option.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-aws-additionalconfig-skipstep.png)
[]
![The Additional Configuration section with the list of actions available.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-account/adding-orchestrator-details-and-configuring-regions/dspm-aws-single-account-additional%20config.png)