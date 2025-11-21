# Selecting the AWS Orchestrator and Monitoring Scope
Source: https://help.zscaler.com/dspm/selecting-aws-orchestrator-and-monitoring-scope
PDF: https://help.zscaler.com/pdf/com/en/1525801.pdf

After deploying the [tree discovery](/dspm/deploying-aws-tree-discovery-template) template, select the network configuration, orchestrator, and monitoring scope.
Under **Orchestrator & Monitoring Scope**:
- [1. Select the network configuration.](#SelectNetworkConfiguration.)
- [][2. Configure the orchestrator.](#config-orchestrator-account-step3)
- [3. Set a monitoring scope.](#setmonitoring-scope-aws)
To modify the configured accounts, click **Reset.**
When you have configured the network and scopes successfully, you are directed to the [Additional Configuration](#additionconfig) section.
[]In the **Additional Configuration** section, you can configure [custom tags](/dspm/managing-custom-tags), [evidence storage](/dspm/managing-evidence-configuration), and [data events](/dspm/managing-data-events). Click **Skip This Step** to configure the additional details after completing the onboarding process and go to the [Grant Permissions](/dspm/deploying-orchestrator-and-monitoring-scope-templates) section.
- [Custom Tags](#customtags)
- [Evidence Storage](#evidencestorage)
- [Data Events](#dataevents-onb)
[See image.](#additionalconfiguration)
After the configuration is completed, you are directed to the [Grant Permissions](/dspm/deploying-orchestrator-and-monitoring-scope-templates) section to deploy the orchestrator and monitoring scope templates.
[]You can choose any of the following network configurations:
- **Zscaler**: Use Zscaler resources to deploy the orchestrator and monitoring scope.
- **Custom**: Use your organization's resources to deploy the orchestrator and monitoring scope.
[See image.](#byon_config)
Changing the network configuration resets the existing configurations.
[]To configure the orchestrator, click **Configure Orchestrator**.
The orchestrator configuration depends on the network configuration you chose earlier.
- [If you have selected the Zscaler network configuration](#zscaler_configuration)
- [If you have selected the custom network configuration](#custom_configuration)
-
[]On the **Configure an Orchestrator Account** page, select an account and the primary region where you want to deploy the orchestrator template and click **Next**.
You need to specify this primary region while [creating the StackSets](#specifyorchregion).
[See image.](#configureorchestratorpage)
-
On the **Select which services to monitor** page, select the services that DSPM must monitor. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
[See image.](#zscalermode-awsservices)
- The Unmanaged Database service is disabled for Zscaler network configuration.
- DSPM automatically excludes Amazon S3 buckets used for storing logs.
-
[]On the **Configure Regions** **for monitoring and scanner's configuration **page, select the regions that DSPM must monitor. DSPM creates and deploys resources required for scanning only in the selected regions.
You need to specify these [regions](#setdeploymentpage) while deploying the orchestrator template.
[See image.](#configure-regions)
- Click **Done**.
-
[]On the **Configure an Orchestrator Account** page, select an account and the primary region where you want to deploy the orchestrator template, and then provide the following details for that selected region:
- **Subnet ARN**: Enter the private subnet ARN for the orchestrator instance.
- **Security Group ID**: Enter the secruity group ID for the orchestrator instance.
You need to specify this primary region while [creating StackSets](#specifyorchregion).
[See image.](#configurecustomorchestratorpage)
- Click **Next**.
-
On the **Select which services to monitor** page, select the services that DSPM must monitor. By default, all the services are selected. DSPM permissions are restricted to monitor and scan the data only in the selected services.
[See image.](#custommode-services)
DSPM automatically excludes Amazon S3 buckets used for storing logs.
-
[]On the **Configure regions for monitoring and scanner configuration** page, select the regions that DSPM must monitor, and enter the following for each selected region:
- **Subnet ARN**: Enter the subnet where the scanner instances must be launched.
- **Security Group ID**: Enter the ID of the security group that controls network traffic to and from the scanner instances.
- **DB Subnet Group ARN**: Enter the ARN of the database subnet group. This is required for DSPM to scan the RDS databases.
You need to specify these [regions](#setdeploymentpage) while deploying the orchestrator template.
[See image.](#configure-custom-regions)
- Click **Done**.
-
[]Click **Set Monitoring Scope**.
[See image.](#setmonitoringscopebutton)
-
On the **Configure Monitoring Scope** page, select the target accounts that DSPM must monitor, then click **Next**.
[See image.](#configuremon-scope-step3)
If you want all the accounts in an organizational unit (OU) to be scanned, select the OU. An OU is a logical group of accounts that perform similar or related functions. To learn more about OUs, refer to the [AWS documentation](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_ous.html).
Select **Autodetection** at the OU level if you want DSPM to automatically include and scan new accounts that are added to the OU in the future. This eliminates the need to manually onboard the new accounts.
[See image.](#configureautodetection)
You must activate [automatic deployment](#auto-deployment-options) in AWS to automatically deploy stack instances for newly added accounts in the future.
-
On the **Assign Business Units** page, assign a business unit to the OU. All the accounts in the OU are mapped to the selected business unit.
[See image.](#assignbupage)
The default business unit is assigned to the OU. You can [change the business units](/dspm/changing-bu-mapping) for the OU if required, after completing the onboarding process.
- Click **Done.**
[]DSPM discovers files and tables containing sensitive data and generates evidence data to investigate and validate the findings. You can choose an existing S3 bucket or configure a new one to store these evidence snippets.
- Click **Add Evidence Storage**.
-
On the **Evidence Configuratio**n, select one of the following:
- [Custom S3 bucket](#custom-evidence)
- [Zscaler Managed S3 bucket](#zscaler-evidence)
When configured, the S3 bucket cannot be modified. You can only enable or disable the evidence configuration.
[See image.](#evidence-configrpage)
- Click **Done**.
[]Data events provide information on the activities performed on or within AWS data stores. You can provide the CloudTrail details to allow DSPM to collect these data events and analyze the activity logs.
- Click **Add Data Events**.
- On the **Configure Data Events** page, under **Storage Information**, select one of the following:
-
**Same S3 bucket as management events**: If the data events are stored in the same S3 bucket where the management events are stored.
[See image.](#sames3bucket)
-
**New S3 bucket**: If the data events are stored in a different S3 bucket:
- **CloudTrail Type**: Select the **OrgCloudTrail **checkbox, if it is an organization CloudTrail.
- **CloudTrail Bucket Name**: Enter the S3 bucket name where the CloudTrial data events are logged.
- **Prefix **(Optional): Enter the prefix specified in the CloudTrail bucket path, if any.
- **Bucket Account ID**: Enter the AWS account ID where the CloudTrail S3 bucket is present.
[See image.](#news3bucket)
- Click **Done**.
[]Custom tags are attached to the resources created by DSPM that enable you to distinguish resources in the organization.
To add custom tags:
- Click **Add Custom Tags**.
-
On the **Add Custom Tags** page, enter a key and value pair for the tag.
Ensure to [follow the guidelines](/dspm/managing-custom-tags) while entering key-value pairs for custom tags.
-
Click **Add More**, and enter key-value pairs to add more tags.
[See image.](#addcustomtagspage)
- Click **Done**.
[]You can use an existing S3 bucket to configure evidence data. DSPM uploads the classified data into the specified S3 bucket.
- **S3 Bucket Name**: The name of the S3 bucket name.
- **S3 Bucket Account ID**: The 12-digit account ID.
- **KMS Key ARN**: The KMS key ARN. This key is used to encrypt the evidence data in the S3 bucket.
[]DSPM creates an S3 bucket in the orchestrator account to upload the classified data.
[]![Select the Required Network Configuration](/downloads/tech-pubs-drafts/dspm-draft-articles/onboarding-aws-organization-draft/dspm-aws-org-onboarding-network-configurations.png)
[]![The Configure an Orchestrator Account page with list of AWS accounts available in the root account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-zscaler-configure-orch.png)
[]![Configure regions page displaying the list of supported AWS regions.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-configure-regions.png)
[]![The Configure an Orchestrator Account page with list of AWS accounts available in the root account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-configure-orch.png)
[]![The Configure regions page with list of supported AWS regions and details of Subnet ARN, Security Group ID blurred.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-configure-regions-custom.png)
[]![The Orchestrator & Monitoring Scope section with annotation around Set Monitoring Scope button](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/selecting-aws-orchestrator-and-monitoring-scope/dspm-setmonitoringscope.png)
[]![The Configure Monitoring Scope page with list of AWS accounts in the Root account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-configure-monitoring-scope01.png)
[]![The Configure Monitoring Scope page with list of AWS accounts in the Root account and annotation around Autodetection.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-autodetection01.png)
[]![The Assign Business Units page with the list of accounts and default business unit assigned.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-assign-bu01.png)
[]![Add Custom tags page displaying the list of key and value pairs added.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-aws-customtags.png)
[]![The evidence configuration page with the available storage type](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/selecting-aws-orchestrator-and-monitoring-scope/dspm-aws-evidenceconfig.png)
[]
![The Configure Data Events page with Same S3 bucket as management events option selected.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-configure-data-events-same-s3bucket.jpg)
[]![The Configure Data Events page with the New S3 bucket option selected and the fields that must be updated.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-configure-data-events-new-s3bucket.jpg)
[]![The Additional Configuration sections with the list of optional actions available.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/selecting-aws-orchestrator-and-monitoring-scope/dspm-aws-additional-configuration.png)
[]![Select services to monitor page displaying the list of available AWS services.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-select-services-tomonitor.png)
[]![Select services to monitor page displaying the list of available AWS services.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/aws-organization/onboarding-aws-organization/dspm-select-services-custom.png)