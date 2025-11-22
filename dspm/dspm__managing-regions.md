# Managing Regions
Source: https://help.zscaler.com/dspm/managing-regions
PDF: https://help.zscaler.com/pdf/com/en/1507481.pdf

You can choose to deploy the scanner instances in specific regions to control resource allocation and costs. This allows you to limit the deployment of scanner instances in selected regions and scan for sensitive data.
You must be assigned either an [Administrator role](/dspm/predefined-roles-and-permissions) or a custom role with the Configure Monitoring Scope permission in the DSPM Admin Portal.
To select the regions:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the cloud account.
-
Click **Manage**, and then select **Manage Regions**.
[See image.](#manage_regions)
- On the **Manage Regions** page:
- [If you select the Zscaler network configuration while onboarding the cloud account](#zscalermode)
- [If you select the custom network configuration while onboarding the cloud account](#custommode)
- Click **Next**.
- On the **Apply Changes** page:
- [For AWS](#aws_template)
- [For Azure](#azure_template)
- [For GCP](#gcp_template)
- Click **Done**.
After the templates are deployed, the regions are updated in the DSPM Admin Portal and subsequent [data scans](/dspm/about-scan-settings) are performed on the resources in the selected regions.
[]Download the deploy the GCP Onboarding template. To learn more, see [Onboarding a GCP Organization](/dspm/onboarding-gcp-organization#download_gcp_onboarding).
[]Download the orchestrator template and extract it to your local system.
To deploy the CloudFormation template:
- Sign in to the orchestrator account in the [AWS Management Console](https://aws.amazon.com/console/) and go to **CloudFormation **> **StackSets**.
- Identify and select the StackSet created while running the orchestrator template.
-
Click **Actions **and select **Add stacks to StackSet**.
[See image.](#addstackstostackset)
-
On the **Set deployment options** page:
- **Add stacks to stack set**: Select **Deploy new stacks**.
- **Accounts**:
- **Deployment locations**: Select **Deploy stacks in accounts**.
- **Account numbers**: Enter the AWS account ID of the orchestrator account.
- **Specify regions**: Select the new regions that you selected in the DSPM Admin Portal to deploy the resources required for scanning.
[See image.](#stedeployment-add)
- Click **Next**.
- On the **Specify overrides** page, click **Next**.
-
On the **Review** page, review the StackSet details and click **Submit**.
The new regions are added to the StackSet.
On the **Operations **tab, you can view the status of the StackSet.
On the **Stack instances** tab, you can view the stack instances created for each region you selected.
-
Click **Actions **and select **Edit StackSet details**.
[See image.](#editstackset)
-
On the **Choose a template** page:
- **Prerequisite - Prepare template**: Select **Replace current template.**
- **Specify template**: Select **Upload a template file** and click **Choose file**. Browse to the location where the template file is extracted, select the YAML file, and then click **Open**.
[See image.](#choosetemplate-page)
- Click **Next**.
- On the **Specify StackSet details** page, click **Next**.
- On the **Configure StackSet options** page, select the **I acknowledge** checkbox and then click **Next**.
-
On the **Set deployment options** page:
- **Deployment locations**: Select **Deploy stacks in accounts**.
- **Account numbers**: Enter the AWS account ID of the orchestrator account that you selected in the DSPM Admin Portal.
- **Specify regions**: Select the new and the existing regions to deploy the resources required for scanning.
[See image.](#setdeployment-edit)
- On the **Review** page, review the StackSet details and click **Submit**.
[]Download and deploy the Azure Onboarding template. To learn more, see [Onboarding a Microsoft Azure Tenant](/dspm/onboarding-microsoft-azure-tenant#grantpermidspm).
[]Select the checkbox for the regions where you want to deploy the resources. For each region, update the following details.
- [For AWS](#aws)
- [For Azure](#azure)
- []Enter the **Subnet ARN**.
- Enter the **Security Group ID**.
- Add the **DB Subnet Group ARN** (if required).
[See image.](#img_aws)
- []Enter the **Subnet ID**.
- Enter the **Network Security Group ID**.
- Add the **Postgres Delegated Subnet ID** (if required).
- Enter the **Storage Account Resource ID** (This field is displayed only if you have enabled the option to create storage accounts in each region while onboarding the Azure accounts using a [custom configuration](/dspm/onboarding-microsoft-azure-tenant#custom_configuration).)
[See image.](#img_azure)
[]Select the checkbox for the regions where you want to deploy the resources. This allows DSPM to monitor the resources only in the selected regions.
[See image.](#select-regions)
[]![List of regions with some selected regions. ](/downloads/dspm/administration/cloud-account-management/managing-regions/select_regions.png)
[]![List of managing actions with annotation around Manage Regions option. ](/downloads/dspm/administration/cloud-account-management/managing-regions/manage-regions.png)
[]![Selected regions with sensitive information in each field for each region. ](/downloads/dspm/administration/cloud-account-management/managing-regions/aws_mnr.png)
[]![Selected regions with sensitive information in each field for each region. ](/downloads/dspm/administration/cloud-account-management/managing-regions/azure_mnr.png)
[]![The Actions drop-down menu with annotation around Edit StackSet details option.](/downloads/dspm/administration/cloud-account-management/managing-regions/dspm-aws-edit-stackset-details.png)
[]![The Actions drop-down menu with annotation around Add stacks to StackSet option.](/downloads/dspm/administration/cloud-account-management/managing-regions/dspm-aws-add-stacks-to-stackset.png)
[]![The Set deployment options page with required fields.](/downloads/dspm/administration/cloud-account-management/managing-regions/dspm-set-deployment-options.png)
[]![The Choose a template page with all required fields to upload the orchestrator template.](/downloads/dspm/administration/cloud-account-management/managing-regions/dspm-choose-template-page.png)
[]![The Set deployment options page with required fields.](/downloads/dspm/administration/cloud-account-management/managing-regions/dspm-aws-set-deployment-options.png)