# Configuring the DLP Application Integration Using Google Cloud Platform
Source: https://help.zscaler.com/workflow-automation/configuring-dlp-application-integration-using-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1532057.pdf

Google Cloud Platform (GCP) only supports the Cloud-to-Cloud Incident Forwarding method for DLP application integration in Workflow Automation.
You must integrate Workflow Automation with the GCP using Zscaler Cloud-to-Cloud Incident Forwarding to allow the Zscaler service to send Data Loss Prevention (DLP) policy violations to GCP cloud storage. Configuring GCP with Zscaler incident forwarding enables your organization to send DLP incident metadata and evidence files to your organization's GCP storage buckets without deploying appliances.
You can also configure the DLP application integration using Amazon Web Services and Microsoft Azure. To learn more, see [Configuring the DLP Application Integration Using Amazon Web Services](/workflow-automation/configuring-dlp-application-integration-using-amazon-web-services) and [Configuring the DLP Application Integration Using Azure](/workflow-automation/configuring-dlp-application-integration-using-azure).
To configure the DLP application integration using Cloud-to-Cloud Incident Forwarding:
- [1. Create cloud resources in GCP.](#create-resource-automatic-c2c)
- [2. Add a DLP GCP application integration in Workflow Automation.](#c2c-add-integration)
- [3. Set Up the DLP Cloud-to-Cloud Incident Forwarding.](#set-up-zscaler-c2c)
After you configure the DLP application integration, the DLP incidents that occur in your organization are displayed on the Incidents page in the Workflow Automation Admin Portal. To learn more, see [Managing Incidents](/workflow-automation/managing-incidents).
[]
- [a. Download the Zscaler script from the Workflow Automation Admin Portal.](#c2c-script-download)
- [b. Create cloud resources for the DLP integration.](#c2c-create-resources)
- [c. Create the service account private key.](#c2c-set-up-service-account)
[]
To download Zscaler deployment script:
-
Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP GCP** application tile. The **Tile View** icon is selected by default.
[See image.](#DLP-GCP-tile-integration-image)
-
Click anywhere within the **DLP GCP** application tile. The **Zscaler DLP GCP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
[See image.](#DLP-GCP-configuration-tab-image)
-
Click the **Configuration Steps** tab. Under **GCP Cloud Resource Stack Setup**, click the **deployment.jinja** link to download the DLP GCP Integration cloud resource stack.
[See image.](#config-steps-tab-image)
[]
To create cloud resources:
- Log in to the [Google Admin Console](https://console.cloud.google.com/).
- Using the **Project Selection** drop-down menu, select your organization.
-
In the resource table that appears, select the appropriate domain.
[See image.](#project-id-image)
-
In the top right of the Google Cloud console, click the **Activate Cloud Shell** icon. The Cloud Shell virtual terminal appears at the bottom of the page.
[See image.](#activate-cloud-shell-image)
-
In the Cloud Shell prompt, run the following command:
nano deployment.jinja
Copy and paste the content from the **deployment.jinja** file you downloaded earlier into the Cloud Shell prompt.
[See image.](#jinja-script-image)
- Check the deployment storage account permissions. You need editor, resource manager, and pubsub admin permissions for the storage accounts used for the deployment:
-
To get the project number, run the following command:
gcloud projects describe <PROJECT_ID> --format="value(projectNumber)"
You are assigned a project number that you can use for the next steps.
-
To check whether you have the required permissions, run the following command:
`gcloud projects get-iam-policy <PROJECT_ID> --flatten="bindings[].members" --filter="bindings.members:'serviceAccount:<PROJECT_NUMBER>@cloudservices.gserviceaccount.com'" --format='table(bindings.role)'`
The following image is an example of the command's output:
[See image.](#storage-acct-permission-output-image)
If you do not have the required permissions for the storage accounts, run the following commands:
-
To provide resource manager permission:
`gcloud projects add-iam-policy-binding <PROJECT_ID> --member="serviceAccount:<PROJECT_NUMBER>@cloudservices.gserviceaccount.com" --role="roles/resourcemanager.projectIamAdmin"`
-
To provide pubsub admin permission:
`gcloud projects add-iam-policy-binding <PROJECT_ID> --member="serviceAccount:<PROJECT_NUMBER>@cloudservices.gserviceaccount.com" --role="roles/pubsub.admin"`
By default, you have editor permissions for the storage accounts.
- Create a deployment for the cloud resources:
-
To create storage buckets with default Google-managed encryption keys, run the following command:
`gcloud deployment-manager deployments create <DEPLOYMENT_NAME> --template=<TEMPLATE_NAME> --properties="prefix:<PREFIX>,location:<LOCATION>`
-
To create storage buckets with customer-managed KMS keys, run the following command:
`gcloud deployment-manager deployments create <DEPLOYMENT_NAME> --template=<TEMPLATE_NAME> --properties="prefix:<PREFIX>,location:<LOCATION>,kms_key:<KMS_KEY>`
The `kms_key` should follow the format: `projects/my-project/locations/us-central1/keyRings/my-key-ring/cryptoKeys/my-key.`
Ensure that you replace the following fields in red with the appropriate values:
- <PROJECT_ID>: The organization's project ID.
- <PROJECT_NUMBER>: The project number of the deployment.
- <DEPLOYMENT_NAME>: The name of the cloud resource deployment.
- <TEMPLATE_NAME>: The name of the deployment script template.
- <PREFIX>: A unique prefix to identify the cloud resources being created. Add this value before topic, data, and metadata buckets. You cannot use dots (.) in the prefix.
- <LOCATION>: The geographical location where the cloud resources are deployed (e.g., us-central1).
-
<KMS_KEY>: (Optional) The full resource name of the cloud KMS key. The buckets are encrypted by default and managed by Google.
If you have access to your own KMS key, run the following command before creating the cloud resource deployment. If you don't run this command, the deployment fails.
`gcloud kms keys add-iam-policy-binding <KEY_NAME> --location <LOCATION> --keyring  --member "serviceAccount:<PROJECT_NUMBER>@cloudservices.gserviceaccount.com"`
The following is an example command:
`gcloud kms keys add-iam-policy-binding zwa-key --location us-central1 --keyring zwa-key-ring --member "serviceAccount:23456710100@cloudservices.gserviceaccount.com".`
- <KEY_NAME>: The name of the KMS key.
- <KEYRING_NAME>: The name of the key ring.
Optionally, you can include the retention period (days) for the data and metadata buckets in the deployment command to manage their lifecycle. The following is an example command:
`gcloud deployment-manager deployments create zwa --template=deployment.jinja --properties="prefix:zwa,location:us-central1,kms_key:projects/my-project/locations/us-central1/keyRings/my-key-ring/cryptoKeys/my-key, retention_period_data:30,retention_period_metadata:30"`
[See image.](#gcloud-script-image)
After completing the deployment, Google Cloud console creates the storage accounts and storage buckets based on your input values.
[]
To create a private key:
- In the Google Cloud console, search for and select **Service Accounts**. The **Service Accounts** page appears.
-
On the **Service Accounts** page, filter to find the newly created cloud resource and select it. The cloud resource page appears.
[See image.](#service-accounts-page-image)
- On the resource page, go to the **Keys** tab.
-
In the **Keys** tab, from the **Add key** drop-down menu, select **Create new key**.
[See image.](#create-new-key-option-image)
-
In the **Create private key** window that appears, select **JSON** as the **Key type** and click** Create**.
[See image.](#create-private-key-window-image)
A file containing the service account key values is downloaded to your local system. These values are required when creating the DLP GCP Integration in the Workflow Automation Admin Portal. The following image displays example key values.
[See image.](#json-private-key-image)
To add a DLP GCP application integration using the GCP service account private key:
-
[]Go to **Setup** > **Integrations**. The **Integrations** dashboard appears, displaying a **DLP** **GCP** application tile. The **Tile View** icon is selected by default.
[See image.](#integrations-dashboard-tile-view-initial)
-
(Optional) On the **Integrations **dashboard, change the view format for the dashboard. Click the **List View** icon to view the **DLP** **GCP** application in a list.
[See image.](#integrations-dashboard-list-view-initial)
- After you select a view option, perform one of the following procedures:
-
In the tile view:
In the DLP GCP application tile, click the **Add** icon. The add **Zscaler DLP GCP Integration** page appears.
-
In the list view:
- Click **Connect** next to the DLP GCP application integration. The **Zscaler DLP GCP Integration** details page appears, displaying a **Configuration Steps** tab and a **Configuration** tab.
- On the **Configuration** tab, click **Add New**. The add **Zscaler DLP GCP Integration** page appears.
[See image.](#zscaler-gcp-application-integration-page-initial)
- On the add **Zscaler DLP GCP Integration** page, in the **Zscaler GCP DLP Integration** section, enter the following:
- **Integration Name**: Enter a name for the integration.
- **Project ID**: From the JSON key downloaded from the GCP console, copy the `project_id` for the DLP integration and enter it here.
- **Private Key**: From the JSON key downloaded from the GCP console, copy the `private_key` for the DLP integration and enter it here.
- **Client Email**: From the JSON key downloaded from the GCP console, copy the `client_email` for the DLP integration and enter it here.
- **Prefix for bucket and topic**: Enter a prefix for the storage bucket and topic.
-
In the **Privacy Settings** section:
- **Hide Evidence Data - Admin**: Select if you do not want admins to be able to generate presigned evidence links for an incident on the** Incident Details** page. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Admin**: Select if you do not want admins to be able to see the trigger data for an incident on the **Incident Details** page. Otherwise, they can see the trigger data.
- **Hide Policy Details - Admin**: Select if you do not want admins to be able to view the policy details for the incident on the **Incident Details** page. Otherwise, they can view the policy details for the incident.
- **Hide Evidence Data - End User**: Select if you do not want end users to be able to generate presigned evidence links for an incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - End User**: Select if you do not want end users to be able to see the trigger data for an incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - End User**: Select if you do not want end users responding to an incident notification to be able to view the policy details for the incident. Otherwise, they can view the policy details for the incident.
- **Hide Evidence Data - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to generate presigned evidence links for the incident. Otherwise, they can generate evidence links.
- **Hide Trigger Data - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to see the trigger data for the incident. Otherwise, they can see the trigger data.
- **Hide Policy Details - Manager/Approver**: Select if you do not want approvers or managers responding to an incident escalation notification to be able to view the policy details for the incident. Otherwise, they can view the policy details for the incident.
[See image.](#add-zscaler-dlp-gcp-integration-page)
If you disable **Hide Evidence Data** or **Hide Trigger Data** in the integration, but you did not enable read access to the storage accounts when creating the cloud resources, no one can generate evidence links or view trigger data in the Workflow Automation Admin Portal.
-
Click **Validate**. The system validates the account credentials that are entered with the GCP integration. You can only add the integration if it passes validation.
If the validation fails for any reason, or if the configuration has been created or updated with the wrong values, you must disable and re-enable the integration after you correct the values for the integration.
- Click **Add**. The **Zscaler DLP GCP Integration** details page appears, displaying the DLP integration under **Connected Accounts** with an **Enabled** status.
To learn more, see [Managing DLP GCP Application Integrations in Workflow Automation](/workflow-automation/managing-dlp-gcp-application-integrations-workflow-automation).
After you add the DLP GCP application integration in Workflow Automation Admin Portal, you can verify whether the DLP application integration was successful in the GCP Console.
To view the integration:
- Log in to the [Google Admin Console](https://console.cloud.google.com/).
- Using the **Project Selection** drop-down menu, select your organization.
- From the resource table that appears, select the appropriate domain.
- Using the Search bar, search for **Subscriptions** and select it. The **Subscription** page appears.
- On the **Subscription **page, filter the DLP integration by name or prefix you provided in the Workflow Automation Admin Portal.
[See image.](#subscription-page-image)
You can view the DLP GCP integration you added in the Workflow Automation Admin Portal.
[]Configure the DLP Cloud-to-Cloud Incident Forwarding on a GCP instance for Workflow Automation. To learn more about configuring Cloud-to-Cloud Incident Forwarding in GCP, see [Configuring DLP Cloud-to-Cloud Incident Forwarding](/zia/configure-dlp-cloud-cloud-incident-forwarding).
[]![Viewing the Integrations Dashboard in Tile View with no integrations configured](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-managing-DLP-GCP-integrations-connected-apps-tile-view.png)
[]![Viewing the Integrations Dashboard in List View with no integrations configured](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-managing-DLP-GCP-integrations-connected-apps-list-view.png)
![The Configuration Steps tab on the GCP application](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-admin-portal-configuration-steps-tab.png)
[]
[]![Viewing the Zscaler DLP GCP Integration details page with no integrations configured ](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-managing-DLP-GCP-integrations-add-new-configuration.png)
[]![Adding a Zscaler DLP GCP Integration on the add Zscaler GCP DLP Integration Page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-managing-DLP-GCP-integrations-editing-contents-enabled-app.png)
![DLP GCP application tile on the Integrations page in the Workflow Automation Admin Portal](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-gcp-tile-integretions-page.png)
[]
![Zscaler DLP GCP Integration page displaying Configuration Steps and Configuration tabs](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-configuration-steps-configuration-tab.png)
[]
![Selecting the Activate Cloud Shell icon in the GCP Portal](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-GCP-portal-activate-cloudshell.png)
[]
![Filtering the Cloud Resource Template on the Service Accounts page](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-cloud-resource-template-service-account-page.png)
[]
![Selecting the Create new key option on the Keys tab on the cloud resource template page](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-service-account-keys-tab-create-new-key.png)
[]
![Selecting the JSON key type in the Create private key window](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-service-account-create-private-key.png)
[]
![The JSON private key parameters downloaded from the GCP Portal - Example key values](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-service-account-key-parameters.png)
[]
![Selecting the organization's project to create the cloud resource template for DLP application integration](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-selecting-organization-project-id.png)
[]
![Running the Deployment Jinja script on the Google Cloudshell prompt](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-cloudshell-jinja-deployment-command.png)
[]
![GCP cloud shell prompt displaying the storage account permissions output](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-storage-account-permissions-output.png)
[]
![Running the Google Cloud deployment Jinja script on the Cloudshell prompt](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-cloudshell-shell-deployment-command.png)
[]
![The Subscriptions page displaying the newly integration DLP application](/downloads/workflow-automation/data-protection/setup/configuring-dlp-application-integration-using-google-cloud-platform/WA-configuring-DLP-GCP-integrations-subscription-page-DLP-application-integration.png)
[]