# Configuring DLP Cloud-to-Cloud Incident Forwarding
Source: https://help.zscaler.com/zia/configuring-dlp-cloud-cloud-incident-forwarding
PDF: https://help.zscaler.com/pdf/com/en/1531158.pdf

Zscaler Cloud-to-Cloud Incident Forwarding allows you to send metadata and evidence from Data Loss Prevention (DLP) violations directly to your public cloud storage without deploying appliances.
To configure Cloud-to-Cloud Incident Forwarding onboarding, you must first onboard your public cloud account:
-
Create storage accounts on your cloud provider to receive incident data from Zscaler.
- [AWS S3](#aws-storage-accounts)
- [Google Cloud](#gcp-create-storage-account)
- [Microsoft Azure](#ms-azure-configure-storage-accounts)
- In the ZIA Admin Portal go to **Administration **> **DLP Incident Receiver **and go to the **Cloud-to-Cloud Incident Forwarding** tab.
- Click **Add Account**.
- Choose or search for the **SaaS Application Provider **(e.g., Azure, Amazon S3, or Google Cloud).
- Enter a **Tenant Name** for the SaaS Application tenant.
- Authorize the SaaS Application:
- [AWS S3](#configure-aws-s3)
- [Google Cloud](#configure-gcp)
- [Microsoft Azure](#configure-ms-azure)
- Click **Save**.
After onboarding is complete, you can configure your DLP policy rules to use Cloud-to-Cloud Incident Forwarding. To learn more, see:
- [Configuring DLP Policy Rules with Content Inspection](/zia/configuring-dlp-policy-rules-content-inspection)
- [Configuring DLP Policy Rules without Content Inspection](/zia/configuring-dlp-policy-rules-without-content-inspection)
- [Configuring DLP Policy Rules with Evaluate All Rules Mode Enabled](/zia/configuring-dlp-policy-rules-evaluate-all-rules-mode-enabled)
- [Configuring Endpoint DLP Policy Rules](/zia/configuring-endpoint-dlp-policy-rules)
- [Configuring Outbound Email Policy Rules](/zia/configuring-outbound-email-policy-rules)
- [Configuring the Data at Rest Scanning DLP Policy with Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-content-inspection)
- [Configuring the Data at Rest Scanning DLP Policy without Content Inspection](/zia/configuring-data-rest-scanning-dlp-policy-without-content-inspection)
[]On the **Create bucket** page in the AWS console, create an S3 bucket for the data bucket and create two containers for evidence and metadata files within that data bucket.
- In the AWS console, search for `**S3**`.
-
In the search results, select **S3**. The Amazon S3 dashboard appears, displaying all the existing buckets.
[See image.](#Amazon-S3-Dashboard)
- Click **Create bucket**. The **Create bucket** page appears.
-
On the **Create bucket** page:
- In the **General configuration** section:
- **Bucket type**: Select **General Purpose**.
- **Bucket name**: Enter the name of the bucket as `<bucketNamePrefix>data` (e.g., `zscaler-dlp-data`). No periods can be used in the name.
- In the **Object Ownership** section, select **ACLs disabled (recommended)**.
- In the **Block Public Access settings for this bucket** section, select the **Block *****all***** public access **checkbox.
- In the **Bucket Versioning** section, select **Disable**.
- In the **Default encryption** section, leave the default settings.
- Click **Create bucket**. The **Buckets **page appears, listing the bucket you have just created.
[See image.](#Create-Bucket-Page)
- On the **Create bucket** page in the AWS console, create an S3 bucket for the metadata bucket.
- On the **Buckets** page, click **Create bucket**. The **Create bucket** page appears.
- On the **Create bucket** page:
- In the **General configuration** section:
- **Bucket type**: Select **General Purpose**.
- **Bucket name**: Enter the name of the bucket as `<bucketNamePrefix>metadata` (e.g.,` zscaler-dlp-metadata`). No periods can be used in the name.
- In the **Object Ownership** section, select **ACLs disabled (recommended)**.
- In the **Block Public Access settings for this bucket** section, select **Block *****all***** public access**.
- In the **Bucket Versioning** section, select **Disable**.
- In the **Default encryption** section, leave the default settings.
- Click **Create bucket**. The **Buckets **page reappears, listing the bucket you have just created.
[]![Amazon S3 Account Dashboard](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/AWS-Amazon-S3-Dboard.png)
[]![Create S3 Buckets on AWS](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/Create-Bucket-AWS-S3.png)
[]Configure a Google Cloud storage account and storage containers for evidence and metadata files within that storage account.
- Log in to the [Google Admin console](https://console.cloud.google.com) and go to the **Google Cloud Storage Overview** page.
-
Click **Create Bucket**.
[See image.](#gcp-create-bucket)
-
On the **Create a bucket **page, enter a name for your Evidence bucket (e.g. Evidence). No periods can be used in the name.
[See image.](#gcp-create-buckets)
- Click **Create**.
-
On the **Google Cloud Storage Overview** page, click **Create Bucket**.
[See image.](#gcp-create-bucket-md)
- On the **Create a bucket **page, enter a name for your Metadata JSON file bucket (e.g. Metadata JSON file). No periods can be used in the name.
- Click **Create**.
[]![Select Create bucket on the Google Cloud storage page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-select-create-bucket.png)
[]![Select Create bucket on the Google Cloud storage page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-select-create-bucket.png)
[]![Enter a name for your bucket then click create](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-create-bucket-page.png)
[]
[]
[]
[]
[]
[]
[]
- [Zscaler Defined](#configure-gcp-defined)
- [Custom](#configure-gcp-custom)
[]
- Enter bucket configuration names:
- Enter the **Configuration Name**.
- Enter the name of your **Evidence Bucket**: The bucket you created [when configuring a Google Cloud storage account](/zia/configure-dlp-cloud-cloud-incident-forwarding#step-1).
- Enter the name of your **Metadata Bucket**: The bucket you created [when configuring a Gogle Cloud storage account](/zia/configure-dlp-cloud-cloud-incident-forwarding).
- Click **Save **and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]
- [a. Assign permissions.](#gcp-assign-permissions)
- [b. Create a service account.](#gcp-create-service-account)
- [c. Grant access to storage accounts.](#gcp-grant-storage-account-access)
- [d. Enable Google Cloud APIs.](#gcp-enable-gc-apis)
- [e. Onboard in ZIA.](#gcp-onboard)
[]
- Log in to the [Google Admin console](https://console.cloud.google.com).
-
Go to your organization using the **Project Selection** drop-down menu and select the appropriate domain.
[See image.](#gcp-select-domain)
-
On the **Google Cloud console**, click **Activate Cloud Shell**.
[See image.](#gcp-activate-cloud-shell)
-
At the Cloud Shell prompt, enter:
``nano Zscaler_GCP_SMIR_role.yaml``
Use the role name exactly as provided and do not modify or rename the role.
-
Copy the following content and paste it into the file:
`title: Zscaler_GCP_SMIR_Role
description: Role Supporting Zscaler SMIR to GCP
stage: ALPHA
incldedPermissions:
- storage.objects.create
- storage.multipartUploads.create
- storage.objects.delete`
- When pasted, press `CTRL+0` to write to file, press `Enter` to not change the file name, and press `CTRL+X` to exit.
-
To create or update a role and attach it to the organization, run the following command, then enter your **Organization ID**:
`gcloud iam roles create Zscaler_GCP_SMIR_Role \
--organization=<organization-id> \
--file=zscaler_readwrite_role.yaml`
To get the organization ID, click on the project at the top of the page. In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
[See image.](#gcp-orgID)
-
To verify the role is created, run the following command, and enter your** Organization ID** where indicated:
`gcloud iam roles describe --organization=<organization-id> Zscaler_GCP_SMIR_Role`
[]![Select your organization in the project selection menu](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-select-domain.png)
[]![Copy your GCP Org ID](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-orgID.png)
[]![Click Activate Cloud Shell](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-activate-cloud-shell.png)
[]In addition to creating the service account, you also download your private key, which is required later for fetching the OAuth token.
-
Select any project within your organization’s folder and create a service account for the project. To do this, in the left-side navigation, click **Service Accounts** > **Create Service Account**.
[See image.](#gcp-service-account-nav)
-
Enter a name for the service account and click **Create and Continue**. Click **Continue** without granting access or permissions to the project.
[See image.](#gcp-service-account-details)
-
On the **Service accounts** page, click the service account you created and select the **Keys** tab.
[See image.](#gcp-keys-tab)
-
Click **Add Key** from the drop-down menu and click **Create new key**.
[See image.](#gcp-create-new-key)
-
In the **Create private key for "<service account>"** window, select the **Key type **as **JSON** and click **Create**.
The private key downloads to your computer.
[See image.](#gcp-create-private-key)
- Click **Close**.
[]![Go to Create Service Account in the GC console](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-create-service-acc-nav.png)
[]![Enter the Service account details on the Create service account page](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-create-service-account.png)
[]![Go to the Keys tab](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-keys-tab.png)
[]![Create a new key in the Google Cloud Platform](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-create-new-keys.png)
[]![Create a private key](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-create-private-key.png)
[]
-
In the [Google Admin console](https://console.cloud.google.com), select the **Details** tab of the service account and copy the email address. This service account must be added as an IAM member in the organization you are setting up for storage scan.
[See image.](#gcp-iam-email)
-
Select the** Evidence bucket** you created.
[See image.](#gcp-create-bucket-md)
You must complete the remaining steps for the Metadata JSON file bucket as well.
-
Click the **Permission** tab.
[See image.](#gcp-permissions-tab)
-
On the **Permissions tab, **click **Grant Access**.
[See image.](#gcp-grant-access)
-
Paste the service account email address you copied previously into the **New principals **text box.
[See image.](#gcp-new-principal)
-
Click **Select a role** and select **Custom, **then select **Zscaler_ReadWrite_Role**.
[See image.](#gcp-assign-roles)
- Click **Save**.
[]![Copy the email from the details page of the Google Cloud Platform](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-iam-email.png)
[]![In the Google Cloud Platform, go to the Permissions tab](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-permissions-tab.png)
[]![On the permissions tab, select Grant access](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-grant-bucket-access.png)
[]![Enter the email address into the new principal text box](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-new-principal.png)
[]![Select which Roles to Assign to the principal](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-assign-roles.png)
[]
- Open the [Google Admin console](https://console.cloud.google.com).
- Go to the project where you initially created the service account and copy it for the following steps. The project ID is typically displayed on the main dashboard of the selected project.
-
In the Google Admin console, click the **Activate Cloud Shell** icon.
[See image.](#gcp-cloud-shell)
-
To set a default project, run the following command:
`gcloud config set project <project-id>`
-
Enable the APIs by running the following command in a single line:
`gcloud services enable storage.googleapis.com`
- In the left-side navigation, click **APIs & Services** and verify API access status.
[]![Click the Activate Cloud Shell icon](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-activate-cloud-shell.png)
[]
In the ZIA Admin Portal:
-
Enter the **Organization ID**.
The organization ID can be found in the [GCP Admin console](https://console.cloud.google.com/). In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
[See image.](#gcp-id)
-
Upload the private key JSON file that you downloaded while creating a service account and click **Authorize**.
[See image.](#gcp-upload-file)
- Under the **Bucket Configuration Names** section:
- **Configuration Name**: Enter a name for the configuration.
- **Bucket Name for Evidence**: Enter the bucket name for evidence you created [when configuring a Google Cloud storage account](/zia/configure-dlp-cloud-cloud-incident-forwarding).
- **Bucket Name for Metadata JSON**: Enter the bucket name for metadata JSON you created [when configuring a Google Cloud storage account](/zia/configure-dlp-cloud-cloud-incident-forwarding).
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]![Copy the Organization ID from the Google Cloud Platform](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-orgID.png)
[]![Click Upload File in the ZIA Admin Portal](/downloads/zia/policies/data-loss-prevention/dlp-incident-receiver/configuring-cloud-to-cloud-incident-forwarding/gcp-upload-file.png)
[]
- [Zscaler Defined](#configure-ms-azure-zs-defined)
- [Custom](#msazure-custom)
[]
- [a. Configure Microsoft Azure.](#config-ms-azure-account-defined)
- [b. Create and assign a role.](#ms-azure-create-roles)
[]
-
Go to **Authorize the SaaS Application** and click **Provide Admin Credentials**, and sign in with your Microsoft Azure account credentials.
[See image.](#msazure-provide-creds)
- For **Register the SaaS Application**:
- Sign in to the Azure portal as an admin and enter:
- Your Microsoft Azure **Enterprise ID**.
- Your **Metadata and Evidence storage accounts**.
- Click **Save**.
[]
-
Copy the **Zscaler SaaS Connector **ID.
[See image.](#zscaler-saas-connector-id)
- Log in to the [Azure portal](https://portal.azure.com/) with your Global Administrator account. Go to **Azure Active Directory **> **Enterprise Application**.
- Copy the application name matching the Zscaler SaaS Connector ID.
- Go back to the Azure portal home page, then go to **Subscriptions** and select your subscription. You must do this for each of your subscriptions.
- Select **Access Control (IAM)** > **Role Assignments** > **Add **> **Add role assignment**.
- Search for `Storage Blob Data Contributor`.
- Select **Storage Blob Data Contributor** then click **Next**.
- Select **Review + assign**.
[]![Click to provide MS Azure Admin Credentials](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-provide-admin-creds.png)
[]![Copy Zscaler SaaS Connector ID](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/zscaler-saas-connector-id.png)
[]
To create a custom Microsoft Azure Blob Storage Connector, you must first create blobs, configure permissions, and assign roles in Azure so that you can provide the client ID, client secret, and tenant ID for the Microsoft Azure Blob Storage account in the ZIA Admin Portal to be able to provide the configuration name, storage account name for evidence, and storage account name for metadata JSON.
- [][a. Create the custom connector and client secret.](#create-custom-connector)
- [b. Generate API permissions for the connector.](#generate-permissions-for-connector)
- [c. Add role assignments.](#add-role-assignments)
- [d. Authorize the custom connector.](#authorize-custom-connector)
[]
- [i. Register the application or service.](#register-client)
- [ii. Configure and copy the client secret.](#configure-client-credentials)
[]
- Sign in to [Azure portal](https://azure.microsoft.com/).
-
In the **Azure Services** section, click **App registrations**.
The **App registrations **page appears.
[See image.](#app-registrations-page)
-
Click **New registration**.
[See image.](#new-app-registration)
The **Register an application** window opens.
- In the **Register an application** window:
- **Name**: Enter a name for the application that is representative of the Zscaler connection you are creating (e.g., `Zscaler Storage Account`).
- **Supported account types**: Ensure that this option is set to the **Accounts in any organizational directory (Any Microsoft Entra ID tenant - Multitenant)** value.
-
**Redirect URI (optional)**: Select **Web** as the platform, then provide the URL of the Zscaler account (e.g., `https://admin.zscalertwo.net/`). Save the URL for later use.
[See image.](#register-new-application)
- Click **Register**.
The application is registered and the application's **Overview** page is displayed. Copy the **Application (client) ID** and **Directory (tenant) ID** values from the **Overview** page and save them for later use.
[See image.](#storage-account-overview)
[]![Copy Application ID and Directory ID](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-storage-account-overview.png)
[]![Register a new application in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-register-an-application.png)
[]![App Registrations in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-app-registrations.png)
[]![On the App registrations page, select New Registration](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/app-registrations-new-registration.png)
[]
-
In the left-side navigation, go to **Manage **> **Certificates & secrets**.
[See image.](#certificates-secrets)
-
On the **Client secrets **tab, click **New client secret**.
[See image.](#new-client-secret)
The **Add a client secret** pane opens.
-
In the **Add a client secret** pane:
- **Description**: Provide information about the client secret.
- **Expires**: Select the appropriate expiration time from the drop-down menu.
[See image.](#add-client-secret)
- Click **Add**.
The client secret value is generated and displayed.
-
Copy the secret value and save it for later use.
[See image.](#client-secret-value)
The client secret value is displayed only once and cannot be retrieved after you navigate away from the page.
[]![Copy the client secret in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-client-secret.png)
[]![Enter a description and select expiration for the client secret in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-add-client-secret-value.png)
[]![Click Add new client secret](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/new-client-secret.png)
[]![Go to Manage and then Certificates and Secrets](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/certificates-sercrets.png)
[]You must assign specific API permissions for each Microsoft connector you create for the Zscaler service.
-
In the left-side navigation, go to **Manage **> **API permissions**.
[See image.](#azure-add-permissions-page)
-
Click **Configured permissions **then **Add a permission**.
[See image.](#azure-add-api-permission)
The **Request API permissions** page is displayed.
- On the **Microsoft APIs** tab, click an API to assign permissions. You need to assign two permissions: Azure Storage and Azure Service Management. Each one maps to the `user_impersonation` permission.
-
In the **Request API permissions **list, select **Azure Service Management**.
[See image.](#select-azure-service-management)
-
Select the permission `user_impersonation` and then click **Add permissions**.
[See image.](#azure-application-permissions)
- On the Microsoft APIs tab, in the **Select permissions** list, select **Azure Storage**.
- Select the permission `user_impersonation` and then click **Add permissions**.
- Click **Add permissions**.
-
Select the permission `user_impersonation`.
The permissions appear in the **Configured permissions** list on the **API permissions** page.
[See image.](#configured-azure-permissions)
[]![API permissions in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-configured-permissions.png)
[]![Click Add permissions to add permissions](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-request-api-add-permission.png)
[]![Select Azure Service Management on the Request API permissions page](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-service-management-api-permissions.png)
[]![Select Add a Permission on the API permissions page](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-api-permission.png)
[]![Go to Manage then click Add permissions](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/add-permissions-azure.png)
[]You must add additional role assignments in Azure to ensure that the Zscaler service can properly access the application:
-
Go to **Azure Services** > **Enterprise Applications** to get to the Overview page.
[See image.](#azure-enterprise-apps)
-
Copy the **Name**, **Application ID**, and the **Object ID.**
[See image.](#azure-storage-overview)
- Go back to the Azure portal home page, then go to **Subscriptions**.
-
**S**elect your subscription.
[See image.](#select-azure-subscription)
The page for the selected subscription opens.
-
Go to **Access Control (IAM).**
[See image.](#azure-go-to-iam)
The Access Control (IAM) page opens.
-
Go to the **Role Assignments** tab, then select **Add **> **Add role assignment**.
[See image.](#azure-add-role-assignment)
-
Search for `Storage Blob Data Contributor`. Select **Storage Blob Data Contributor** then click **Next**.
[See image.](#storage-blob-data-contributor)
-
On the **Add role assignments** page, click **Select members**.
[See image.](#azure-select-members)
-
Select or search for the application you created when [creating the custom connector](#step1-create-custom-connector), then add it as a member to **Storage Blob Data Contributor**. Click **Submit**.
[See image.](#azure-role-select-storage-account)
- Click **Submit**.
[]![Select Storage account for Azure Role](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-select-members-storage-accounts.png)
[]![Click Select members on the role assignments page](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-role-select-member.png)
[]![Search for and select Storage Blob Data Contributor](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-storage-blob-data-contributor.png)
[]![Go to the Role Assignment tab then click Add then click Add role Assignment](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-add-role-assignments.png)
[]![Go to Access Control (IAM)](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-iam-role-assignments.png)
[]![Select your Subscription in the Azure portal](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-subscription.png)
[]![Go to Azure Enterprise applications](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-enterprise-applications.png)
[]![Copy the information from your storage account overview in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-zs-storage-accounts.png)
[]Configure a storage account and configure two containers for evidence and metadata files within that storage account.
If you are integrating your Azure account with Workflow Automation, see [Configuring the Azure DLP Application Integration using Cloud-to-Cloud Incident Forwarding](/workflow-automation/configuring-azure-dlp-application-integration-using-cloud-cloud-incident-forwarding).
- From the Azure homepage, go to **Storage accounts**.
-
Click **Create **to create the storage account for Evidence.
[See image.](#azure-create-storage-account)
-
On the **Basics **tab:
- **Resource group**: Create a new resource group.
- **Storage account name**: Enter a name.
- **Region**: Select a region from the drop-down menu.
- **Primary service**: Select a primary service from the drop-down menu.
- **Performance**: Choose either **Standard **or **Premium**.
- **Redundancy**: Select a redundancy from the drop-down menu.
[See image.](#azure-storage-account-basics)
- Click **Review + create**.
- The **Create a storage account** page opens. Click **Create**.
- Next, you need to create another storage account for Metadata. From the Azure homepage, go to **Storage accounts**.
- Click **Create**.
-
On the **Basics **tab:
- **Resource group**: Create a new resource group.
- **Storage account name**: Enter a name.
- **Region**: Select a region from the drop-down menu.
- **Primary service**: Select a primary service from the drop-down menu.
- **Performance**: Choose either **Standard **or **Premium**.
- **Redundancy**: Select a redundancy from the drop-down menu.
[See image.](#azure-basics-metadata-account)
- Click **Review + create**.
- The **Create a storage account** page opens. Click **Create**.
-
You need to make sure your storage accounts are accessible to the necessary IP addresses. To do so, go to **Security + networking > Networking**.
To learn which IP addresses to connect to, see [Zscaler Hub IP Addresses](https://config.zscaler.com/zscaler.net/hubs).
-
Go to **Data storage **> **Containers **and select **Add container**.
[See image.](#add-azure-container)
- Name your container `evidence` then click **Create**. No periods can be used in the name.
- Select **Add container**.
-
Name your container `metadata` then click **Create**. No periods can be used in the name.
You need the names of the containers you created to enter them in the ZIA Admin Portal.
[]![Add a container in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/add-azure-container.png)
[]![Create storage account for metadata in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-basics-metadata.png)
[]![Create a storage account in Azure](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-basics-page.png)
[]![Select Create to create a storage account](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-create-storage-accounts.png)
[]To authorize a custom connector, you must first manually update the Azure login URL to grant permissions for the application on the tenant. After that, you must provide the client ID, client secret, and tenant ID in the ZIA Admin Portal so that the Zscaler service can access the application.
- In the ZIA Admin Portal, enter the values for the **Application** **Client ID**, **Client Secret**, and **Tenant ID** that you copied earlier, then click **Authorize**.
- Enter the **Configuration Name**.
- Enter the **Bucket Name for Evidence**:
- Go to the Azure portal.
- Select your storage account.
-
Go to the containers section and select the storage account name container to copy its URL:
`	https://<storage_account>.blob.core.windows.net/<container_name>`
-
Enter the **Bucket Name for Evidence**:
- Go to the Azure portal.
- Select your storage account.
-
Go to the containers section and select the storage account name container to copy its URL:
`https://<storage_account>.blob.core.windows.net/<container_name>`
[See image.](#azure-bucket-config)
- Click **Save** and activate the change.
[]![Enter Bucket Config info in the ZIA Admin Portal](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/azure-bucket-config.png)
[]
You need your Zscaler Connector Account Number, Zscaler, Connector User ARN, and External ID to authorize the SaaS Application in the AWS console. Remember these account numbers. [See image.](#aws-connector-accounts)
- [a. Create an IAM role for AWS.](#aws-create-iam-role)
- [b. Specify IAM role permissions.](#aws-specify-iam-role-permissions)
- [c. Edit trust policy.](#aws-edit-trust-relationship)
- [d. Register the SaaS application.](#aws-register-saas-application)
[]You must create roles in AWS to ensure that the Zscaler service can properly access the application:
-
Click **Go to AWS **to give Zscaler access to Amazon S3 and configure roles and permissions.
[See image.](#go-to-aws)
- Go to **Services** > **IAM**.
- In the left-side navigation, go to **Access management** > **Roles**.
- Click **Create role**.
- In **Select type of trusted entity**, select **AWS Account**.
-
From the AWS Account page, click **AWS account **and enter the **Account ID** and the **External ID** from the Zscaler instance that you copied from the ZIA Admin Portal.
[See image.](#add-aws-ids-to-accounts)
- Click **Next**
- In** Edit trust Policy**, click **Edit**.
- Click **Next**.
- In **Attach permissions policies**, do not select permissions.
- Click **Next: Tags**.
- In **Add tags (optional)**, enter a key-value pair.
- Click **Next: Review**.
- In **Review**:
- **Role name**: Enter a role name.
- **Description**: (Optional) Enter additional notes or information.
- Click **Create role**.
[]![Create AWS IAM role in AWS](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/aws-add-account-external-ids.png)
[]You need to create storage accounts for evidence data and metadata files in AWS to configure the appliance:
- Click the **Role Name** of the IAM role you previously created.
-
On the Permissions tab click **Add permissions** > **Create inline policy**.
[See image.](#aws-add-permissions)
-
Click **JSON** in the **policy editor**.
[See image.](#aws-json-editor)
-
Enter the following JSON string with your storage account names and Zscaler Connector User ARN. Names cannot contain periods.
`{
"Version": "2012-10-17",
"Statement": [
{
"Sid": "Statement1",
"Effect": "Allow",
"Action": [
"s3:ListBucket"
],
"Resource": [
"arn:aws:s3:::<metadata-bucket-name>",
"arn:aws:s3:::<evidence-data-bucket-name>"
]
},
{
"Sid": "AllowPutObject",
"Effect": "Allow",
"Action": [
"s3:PutObject"
],
"Resource": [
"arn:aws:s3:::<metadata-bucket-name>/*",
"arn:aws:s3:::<evidence-data-bucket-name>/*"
]
}
]
}
`
- Click **Next**.
- Enter a **Policy name **for your policy.
[]
[]![Go to Create inline policy to add permission to S3](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/aws-add-permissions.png)
[]![Select JSON to edit JSON file in editor](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/aws-json-editor.png)
[]You must edit the Trust relationships for the role you created for the Zscaler service:
- Click the **Role Name** of the IAM role you previously created.
- Go to **Trust Relationships** tab.
- Click **Edit trust policy**.
-
In the **Principal AWS **field delete the existing AWS value, and enter the **Zscaler Connector User ARN **(the number you copied from the ZIA Admin Portal).
[See image.](#zia-aws-connector-arn)
-
Click **Update Policy**.
The **Summary **page appears.
- On the **Summary** page, copy the **Role ARN**.
[]![Zscaler Connector User ARN](/downloads/tech-pubs-drafts/zia-draft-articles/dlp-cloud-cloud-incident-forwarding/zscaler-connector-user-arn.png)
[]
- Use the IAM roles you configured in the AWS S3 page to register the SaaS application:
- **AWS Account ID:** Enter your AWS Account ID.
- **IAM Role**: Enter the role you just created (ARN Role Name).
- **Configuration Name: **Enter a configuration name.
- **Storage Account Name for Evidence: **Enter the name of the evidence storage account you created.
- **Storage Account Name for Metadata: **Enter the name of the metadata storage account you created.
- **Region: **Select a Region.
- Click **Save**.
[]![Click to go to AWS](/downloads/tech-pubs-drafts/zia-draft-articles/configure-dlp-cloud-cloud-incident-forwarding-wip-draft/go-to-AWS.png)
[]![Zscaler Connector Accounts](/downloads/tech-pubs-drafts/zia-draft-articles/configure-dlp-cloud-cloud-incident-forwarding-wip-draft/aws-connector-account-number.png)