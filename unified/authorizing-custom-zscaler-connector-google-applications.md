# Authorizing a Custom Zscaler Connector for Google Applications
Source: https://help.zscaler.com/zia/authorizing-custom-zscaler-connector-google-applications
PDF: https://help.zscaler.com/pdf/com/en/1493761.pdf

The Zscaler service supports custom, client-side connector onboarding for access to Gmail, Google Cloud Platform, Google Drive, and Google Workspace. With this functionality, instead of requiring full administrator credentials, the Zscaler service can use a minimum set of credentials to access these Google applications.
When you create a custom connector for these applications, you must configure them with the proper settings so that Zscaler can access the application.
- [Gmail](#gmail)
- [Google Cloud Platform](#GCP)
- [Google Drive](#drive)
- [Google Workspace](#work)
When creating custom connectors, provide the following application-specific API permissions to ensure that the Zscaler service has the access it needs.
- [API/OAuth Scope Permissions for Google Applications](#api-permissions)
[]
- [Gmail](#apigmail)
- [Google Cloud Platform](#api-permissions-gcp)
- [Google Drive](#apidrive)
- [Google Workspace](#apiwork)
[]
- [Read Role](#apiread)
- [Read Role + Webhooks](#apiwebhook)
- [Read/Write Role](#apireadwrite)
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| iam.roles.get | Validation |
| iam.roles.list | Validation |
| storage.buckets.get | Onboarding, Scanning |
| storage.buckets.list | Onboarding, Scanning |
| storage.objects.get | Scanning |
| storage.objects.list | Scanning |
| resourcemanager.projects.get | Onboarding, Scanning |
| resourcemanager.projects.getIamPolicy | Onboarding, Scanning |
| resourcemanager.folders.get | Onboarding |
| resourcemanager.folders.getIamPolicy | Onboarding |
| resourcemanager.folders.list | Onboarding |
| resourcemanager.organizations.get | Validation |
| resourcemanager.organizations.getIamPolicy | Validation |
| storage.objects.getIamPolicy | Scanning |
| storage.buckets.getIamPolicy | Onboarding, Scanning |
| logging.logEntries.list | Scanning, Reporting |
| logging.privateLogEntries.list | Scanning, Reporting |
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| iam.roles.get | Validation |
| iam.roles.list | Validation |
| storage.buckets.get | Onboarding, Scanning |
| storage.buckets.list | Onboarding, Scanning |
| storage.objects.get | Scanning |
| storage.objects.list | Scanning |
| resourcemanager.projects.get | Onboarding, Scanning |
| resourcemanager.projects.getIamPolicy | Onboarding, Scanning |
| resourcemanager.folders.get | Onboarding |
| resourcemanager.folders.getIamPolicy | Onboarding |
| resourcemanager.folders.list | Onboarding |
| resourcemanager.organizations.get | Validation |
| resourcemanager.organizations.getIamPolicy | Validation |
| storage.objects.getIamPolicy | Scanning |
| storage.buckets.getIamPolicy | Onboarding, Scanning |
| logging.logEntries.list | Scanning, Reporting |
| logging.privateLogEntries.list | Scanning, Reporting |
| pubsub.subscriptions.create | Scanning, Reporting |
| pubsub.subscriptions.delete | Scanning, Reporting |
| pubsub.subscriptions.get | Scanning, Reporting |
| pubsub.topics.attachSubscription | Scanning, Reporting |
| pubsub.topics.create | Scanning, Reporting |
| pubsub.topics.setIamPolicy | Scanning, Reporting |
| pubsub.topics.delete | Scanning, Reporting |
| pubsub.topics.getIamPolicy | Scanning, Reporting |
| pubsub.topics.get | Scanning, Reporting |
| pubsub.subscriptions.update | Scanning, Reporting |
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| iam.roles.get | Validation |
| iam.roles.list | Validation |
| logging.sinks.get | Reporting |
| storage.buckets.get | Onboarding, Scanning |
| storage.buckets.list | Onboarding, Scanning |
| storage.objects.get | Scanning |
| storage.objects.list | Scanning |
| resourcemanager.projects.get | Onboarding, Scanning |
| resourcemanager.projects.getIamPolicy | Onboarding, Scanning |
| resourcemanager.folders.get | Onboarding |
| resourcemanager.folders.getIamPolicy | Onboarding |
| resourcemanager.folders.list | Onboarding |
| resourcemanager.organizations.get | Validation |
| resourcemanager.organizations.getIamPolicy | Validation |
| storage.objects.getIamPolicy | Scanning |
| storage.buckets.getIamPolicy | Onboarding, Scanning |
| logging.logEntries.list | Scanning, Reporting |
| logging.privateLogEntries.list | Scanning, Reporting |
| storage.objects.setIamPolicy | Policy action |
| storage.objects.update | Policy action |
| storage.objects.create | Policy action |
| storage.objects.delete | Policy action |
| storage.buckets.update | Policy action |
| storage.buckets.setIamPolicy | Policy action |
| pubsub.subscriptions.create | Scanning, Reporting |
| pubsub.subscriptions.delete | Scanning, Reporting |
| pubsub.subscriptions.get | Scanning, Reporting |
| pubsub.topics.attachSubscription | Scanning, Reporting |
| pubsub.topics.create | Scanning, Reporting |
| pubsub.topics.setIamPolicy | Scanning, Reporting |
| pubsub.topics.delete | Scanning, Reporting |
| pubsub.topics.getIamPolicy | Scanning, Reporting |
| pubsub.topics.get | Scanning, Reporting |
| pubsub.subscriptions.update | Scanning, Reporting |
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| https://www.googleapis.com/auth/pubsub | Scanning |
| https://www.googleapis.com/auth/admin.directory.user | Scanning |
| https://www.googleapis.com/auth/admin.reports.audit.readonly | Scanning, Reporting |
| https://mail.google.com/ | Scanning, Apply Label |
| https://www.googleapis.com/auth/admin.reports.usage.readonly | Scanning |
| https://www.googleapis.com/auth/admin.directory.user.security | Scanning |
| https://www.googleapis.com/auth/admin.directory.group.readonly | Scanning |
| https://www.googleapis.com/auth/admin.directory.orgunit.readonly | Scanning |
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| https://www.googleapis.com/auth/admin.directory.user | Scanning |
| https://www.googleapis.com/auth/drive | Scanning, Policy Actions |
| https://www.googleapis.com/auth/admin.reports.audit.readonly | Scanning |
| https://www.googleapis.com/auth/admin.reports.usage.readonly | Scanning, Reporting |
| https://www.googleapis.com/auth/admin.directory.user.security | Scanning |
| https://www.googleapis.com/auth/admin.directory.group.readonly | Scanning |
| https://www.googleapis.com/auth/admin.directory.orgunit.readonly | Scanning |
| https://www.googleapis.com/auth/drive.admin.labels | Apply Label |
[]
[]
| Google Permission | Associated Zscaler Actions |
| ----------------- | -------------------------- |
| https://www.googleapis.com/auth/admin.directory.user | Scanning |
| https://www.googleapis.com/auth/drive | Scanning |
| https://www.googleapis.com/auth/admin.reports.audit.readonly | Scanning |
| https://www.googleapis.com/auth/admin.reports.usage.readonly | Scanning |
| https://mail.google.com/ | Scanning |
| https://www.googleapis.com/auth/admin.directory.user.security | Scanning |
| https://www.googleapis.com/auth/admin.directory.group.readonly | Scanning |
| https://www.googleapis.com/auth/admin.directory.orgunit.readonly | Scanning |
| https://www.googleapis.com/auth/gmail.settings.sharing | Remediation |
| https://www.googleapis.com/auth/gmail.settings.basic | Remediation |
- [][1. Assign permissions.](#GCPStep1)
- [2. Create a service account.](#GCPStep2)
- [3. Add the service account as an IAM member.](#GCPStep3)
- [4. Enable audit logs for cloud storage.](#GCPStep4)
- [5. Enable Google Cloud APIs.](#GCPStep5)
- [6. Onboard in ZIA.](#GCPStep6)
[]Start by setting up one of the following permission types:
- [Zscaler Read Role](#GCP_Read)
- [Zscaler Read Role and Webhooks](#GCP_Read_Webhooks)
- [Zscaler Read/Write Role](#GCP_ReadWrite)
With these permissions, Report Incident and Action None policy actions will function. Sign-in Events, Webhooks, and other policy actions will not function.
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com).
-
Go to your organization using the **Project Selection** drop-down menu and select the appropriate domain.
[See image.](#GCP01_Org)
-
Log in to the Google Cloud console and click **Activate Cloud Shell**.
[See image.](#GCP02_Shell)
-
At the shell prompt, enter:
``nano zscaler_read_role.yaml``
Use the role name exactly as provided and do not modify or rename the role.
-
Copy the following content into the file:
For more information about the APIs, see the [API Permissions](#readtable) table.
`title: "Zscaler_Read_Role"
description: "Role for supporting Zscaler for performing Storage Scan"
stage: "ALPHA"
includedPermissions:
# get IAM roles to check the Zscaler_Role is present
- iam.roles.get
- iam.roles.list
# get bucket metadata
- storage.buckets.get
# list storage buckets under the project
- storage.buckets.list
# get object metadata
- storage.objects.get
# list objects under the storage buckets
- storage.objects.list
# get project metadata and list projects under organization
- resourcemanager.projects.get
- resourcemanager.projects.getIamPolicy
# this permission is required while listing and getting metadata for folders under organization
- resourcemanager.folders.get
- resourcemanager.folders.getIamPolicy
- resourcemanager.folders.list
# this permission is required for getting the organization metadata
- resourcemanager.organizations.get
- resourcemanager.organizations.getIamPolicy
# get ACLs if any created for an object which will be used to check for visibility of the object(public/private)
- storage.objects.getIamPolicy
# get ACLs and Iam policy attached to the bucket used for checking visibility of buckets
- storage.buckets.getIamPolicy
# get all logging entries
- logging.logEntries.list
- logging.privateLogEntries.list                                    `
- When pasted, press `CTRL+0` to write to file, press `Enter` to not change the file name, and press `CTRL+X` to exit.
-
Run the following commands to create the role and attach it to the organization:
- To create a role for the first time, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles create Zscaler_Read_Role \
--organization=<organization-id> \
--file=zscaler_read_role.yaml`
- To update the existing Zscaler_Read_Role, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles update Zscaler_Read_Role \
--organization=<organization-id> \
--file=zscaler_read_role.yaml`
To get the organization ID, click on the project at the top of the page. In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
[See image.](#GCP03_OrgID)
-
To verify the role is created, run the following command, entering your Organization ID where indicated:
``gcloud iam roles describe --organization=``<organization-id>`` Zscaler_Read_Role``
With these permissions, Report Incident and Action None policy actions will function. Sign-in Events and other policy actions will not function. This configuration provides connector sufficient permission to register webhooks along with keeping read role intact on Google Cloud Storage.
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com).
-
Go to your organization using the **Project Selection** drop-down menu and select the appropriate domain.
[See image.](#GCP01_Org2)
-
Log in to the Google Cloud console and click **Activate Cloud Shell**.
[See image.](#GCP02_Shell2)
-
At the shell prompt, enter:
``nano zscaler_read_role.yaml``
Use the role name exactly as provided and do not modify or rename the role. If you do modify the Zscaler_Read_role, a scan restart is mandatory for the changes to take effect.
-
Copy the following content into the file:
For more information about the APIs, see the [API Permissions](#webhooktable) table.
`title: "Zscaler_Read_Role"
description: "Role for supporting Zscaler for performing Storage Scan"
stage: "ALPHA"
includedPermissions:
# get IAM roles to check the Zscaler_Role is present
- iam.roles.get
- iam.roles.list
# get bucket metadata
- storage.buckets.get
# list storage buckets under the project
- storage.buckets.list
# get object metadata
- storage.objects.get
# list objects under the storage buckets
- storage.objects.list
# get project metadata and list projects under organization
- resourcemanager.projects.get
- resourcemanager.projects.getIamPolicy
# this permission is required while listing and getting metadata for folders under organization
- resourcemanager.folders.get
- resourcemanager.folders.getIamPolicy
- resourcemanager.folders.list
# this permission is required for getting the organization metadata
- resourcemanager.organizations.get
- resourcemanager.organizations.getIamPolicy
# get ACLs if any created for an object which will be used to check for visibility of the object(public/private)
- storage.objects.getIamPolicy
# get ACLs and Iam policy attached to the bucket used for checking visibility of buckets
- storage.buckets.getIamPolicy
# get all logging entries
- logging.logEntries.list
- logging.privateLogEntries.list
# webhook
# create pubsub subscription required for sending notification to Zscaler
- pubsub.subscriptions.create
- pubsub.subscriptions.delete
- pubsub.subscriptions.get
- pubsub.topics.attachSubscription
- pubsub.topics.create
- pubsub.topics.setIamPolicy
- pubsub.topics.delete
- pubsub.topics.getIamPolicy
- pubsub.topics.get
- pubsub.subscriptions.update`
When pasted, press `CTRL+0` to write to file, press `Enter` to not change the file name, and press `CTRL+X` to exit.
-
Run one of following commands to either create or update the role and attach it to the organization:
- To create a role for the first time, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles create Zscaler_Read_Role \
--organization=<organization-id> \
--file=zscaler_read_role.yaml`
- To update the existing Zscaler_Read_Role, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles update Zscaler_Read_Role \
--organization=<organization-id> \
--file=zscaler_read_role.yaml`
To get the organization ID, click on the project at the top of the page. In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
[See image.](#GCP03_OrgID2)
-
To verify the role is created, run the following command, entering your Organization ID where indicated:
``gcloud iam roles describe --organization=``<organization-id>`` Zscaler_Read_Role``
Sign-in Events will not function with these permissions.
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com).
-
Go to your organization using the **Project Selection** drop-down menu and select the appropriate domain.
[See image.](#GCP01_Org3)
-
Log in to the Google Cloud console and click **Activate Cloud Shell**.
[See image.](#GCP02_Shell3)
-
At the shell prompt, enter:
``nano zscaler_readwrite_role.yaml``
Use the role name exactly as provided and do not modify or rename the role.
-
Copy the following content into the file:
For more information about the APIs, see the [API Permissions](#readwritetable) table.
`title: "Zscaler_ReadWrite_Role"
description: "Role for supporting Zscaler for performing Storage Scan"
stage: "ALPHA"
includedPermissions:
# get IAM roles to check the Zscaler_Role is present
- iam.roles.get
- iam.roles.list
# get log sinks created for the project
- logging.sinks.get
# get bucket metadata
- storage.buckets.get
# list storage buckets under the project
- storage.buckets.list
# get object metadata
- storage.objects.get
# list objects under the storage buckets
- storage.objects.list
# get project metadata and list projects under organization
- resourcemanager.projects.get
- resourcemanager.projects.getIamPolicy
# this permission is required while listing and getting metadata for folders under organization
- resourcemanager.folders.get
- resourcemanager.folders.getIamPolicy
- resourcemanager.folders.list
# this permission is required for getting the organization metadata
- resourcemanager.organizations.get
- resourcemanager.organizations.getIamPolicy
# get ACLs if any created for an object which will be used to check for visibility of the object(public/private)
- storage.objects.getIamPolicy
# get ACLs and Iam policy attached to the bucket used for checking visibility of buckets
- storage.buckets.getIamPolicy
# get all logging entries
- logging.logEntries.list
- logging.privateLogEntries.list
# policy action
- storage.objects.setIamPolicy
- storage.objects.update
- storage.objects.create
- storage.objects.delete
- storage.buckets.update
- storage.buckets.setIamPolicy
# webhook
# create pubsub subscription required for sending notification to Zscaler
- pubsub.subscriptions.create
- pubsub.subscriptions.delete
- pubsub.subscriptions.get
- pubsub.topics.attachSubscription
- pubsub.topics.create
- pubsub.topics.setIamPolicy
- pubsub.topics.delete
- pubsub.topics.getIamPolicy
- pubsub.topics.get
- pubsub.subscriptions.update`
Once pasted, press `CTRL+0` to write to file, press `Enter` to not change the file name, and press `CTRL+X` to exit.
-
Run the following command to create the role and attach it to the organization:
- To create a role for the first time, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles create Zscaler_ReadWrite_Role \
--organization=<organization-id> \
--file=zscaler_readwrite_role.yaml`
- To update the existing Zscaler_Read_Role, run the following, entering your Organization ID where indicated:
- `Bash`
- `Copy code`
- `gcloud iam roles update Zscaler_ReadWrite_Role \
--organization=<organization-id> \
--file=zscaler_readwrite_role.yaml`
To get the organization ID, click on the project at the top of the page. In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
[See image.](#GCP03_OrgID3)
-
To verify the role is created, run the following command, entering your Organization ID where indicated:
``gcloud iam roles describe --organization=``<organization-id>`` Zscaler_ReadWrite_Role``
[]In addition to creating the service account, you also download your private key, which is required later for fetching the OAuth token.
-
Select any project within your organization’s folder and create a service account for the project. To do this, in the left-navigation menu, click **Service Accounts** > **Create Service Account**.
[See image.](#GCP04_Service01)
-
Enter a name for the service account, copy the email address, and click **Create and Continue**. Click **Continue** without granting access or permissions to the project.
[See image.](#GCP05_Service02)
-
Paste the copied email address from the previous step into the **Service account users role** field and click **Done**.
[See image.](#GCP06_Service03)
- On the **Service accounts** page, click the service account you created and select the **Keys** tab.
- Click **Add Key** from the drop-down menu and click **Create new key**.
- In the **Create private key for *****<service account>*** dialog box, select the key type as **JSON** and click **Create**. The private key downloads to your computer.
- Click **Close**.
-
[]Select the **Details** tab of the service account and copy the email address. This service account must be added as an IAM member in the organization you are setting up for storage scan.
[See image.](#GCP07_IAM)
- Select the organization you are setting up for storage scan. In the left-side navigation, go to **IAM** > **Add/Grant Access**.
- Paste the service account email address you copied in Step 1 in the **New member** text box of the **Add members to *****<organization>*** window.
- Click **Select a role** and select **Zscaler_Read_Role** or **Zscaler_ReadWrite_Role**.
- Click **Save**.
-
[]With the organization selected at the top of the page, in the left-side navigation, click **Audit logs** under **IAM & Admin**.
[See image.](#GCP08_Audit)
-
On the **Audit Logs** page, search for `Google Cloud Storage` and `Cloud Logging API` and select both services.
[See image.](#GCP09_Logs)
-
With both services selected, in the pane on the right side, select **Data Write**, **Data Read**, and **Admin Read** in the **Log Type** tab and click **Save**.
[See image.](#GCP11_LogType)
[]These instructions allow Zscaler to make API calls to the project resource by enabling the following Google Cloud APIs: Identity and Access Management (IAM) API, Cloud Resource Manager API, Cloud Logging API, Cloud Pub/Sub API, and Cloud Storage API.
- Open the [GCP Cloud Console](https://console.cloud.google.com/).
- Go to the project where you initially created the service account in [Step 2](#GCPStep2) and copy it for the following steps. The Project ID is typically displayed on the main dashboard of the selected project.
-
On the GCP Cloud Console, click the **Activate Cloud Shell** icon.
[See image.](#GCP02_Shell04)
-
To set a default project, run the following command:
`gcloud config set project <project-id>`
-
Enable the APIs by running the following command in a *single line*:
`gcloud services enable cloudresourcemanager.googleapis.com storage.googleapis.com iam.googleapis.com logging.googleapis.com pubsub.googleapis.com cloudkms.googleapis.com `
- In the left-side navigation, click **APIs & Services** and verify API access status.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants** and click **Add SaaS Application Tenant**.
- Select **Google Cloud**.
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique. This name is displayed when configuring the Data at Rest ScanningDLP policy, Malware Detection policy, and Scan Configuration.
- Enter the **Google Cloud Admin Email ID**, which should be the organization admin or user email address. This value is treated as the tenant ID, and Zscaler internally fetches the tenant domain from it.
-
Under Authorize the SaaS Application, select **Custom**.
[See image.](#GCP10_Custom)
- Select either **Read** or **Read Write** for the Connector Role.
-
Enter the **Organization ID** and if you selected **Read Write** as the connector role, also enter the **Quarantine Bucket** name.
The organization ID can be found in the [GCP Cloud Console](https://console.cloud.google.com/). In the **Select from** window, click on the **All** tab and click on the organization that the project is under. The organization name has an accompanying ID.
To learn more about the quarantine bucket, see [Adding SaaS Application Tenants](/zia/adding-saas-application-tenants#GCBucket).
- Upload the private key JSON file that you downloaded in [Step 2](#GCPStep2) while creating a service account and click **Authorize**.
- Click Save and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]![Find your GCP project](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_01_Organization.png)
[]![Find your GCP project](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_01_Organization.png)
[]![Find your GCP project](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_01_Organization.png)
[]![Activate Cloud Shell button](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell.png)
[]![Activate Cloud Shell button](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell.png)
[]![Activate Cloud Shell button](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell.png)
[]![Activate Cloud Shell button](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell.png)
[]![Organization ID number](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_02_OrgID.png)
[]![Organization ID number](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_02_OrgID.png)
[]![Organization ID number](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_02_OrgID.png)
[]![Create a new service account](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_03_CreateServiceAccount.png)
[]![Enter service account name and copy email address](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_04_CreateServiceAccount02.png)
[]![Grant access to service account user role](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_05_CreateServiceAccount03.png)
[]![IAM email address location](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_06_IAMEmail.png)
[]![Audit log location](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_07_AuditLogs.png)
[]![Services to select for audit logs](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_08_AuditLogs02_2.png)
[]![Audit log type selections](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_11_AuditLogs03.png)
[]![Add the custom SaaS connector](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_10_Custom.png)
- [][1. Create a service account for the organization.](#gmail_step1)
- [2. Ensure connector has access to required APIs.](#gmail_step2)
- [3. Add OAuth client to Google Admin.](#gmail_step3)
- [4. Ensure admin role with appropriate permission is present.](#gmail_step4)
- [5. Onboard with ZIA.](#gmail_step5)
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com/) and select any project or create a new project within the organization.
-
[]Create a service account for the selected project. In the left-side navigation, go to **IAM & Admin** > **Service Accounts** > **Create Service Account**.
[See image.](#gmail_service)
- []Provide a name for the service account, copy the email address, and click **Create and Continue**.
-
In the **Grant this service account access to project** section, select the role **Pub/Sub Admin** and click **Continue**.
[See image.](#pubsub)
-
Paste the [copied email address](#gmail_email) into the **Service account users role** section and click **Done**.
[See image.](#gmail_grant)
- []On the **Service accounts** page, note down the OAuth2 Client ID.
- Click the service account you created, and click the **Keys** tab.
- Click **Add Key** and from the drop-down list click **Create new key**.
- In the **Create private key for <service account> dialog** box, select the key type as **JSON** and click **Create**. The private key is downloaded to your computer. Click **Close**.
- []Go to the project you created the service account in [Step 1](#gmail_step1.5) and copy your project ID.
-
To enable APIs for the project, from the main Google Cloud Platform page, click the **Activate Cloud Shell** icon.
[See image.](#gmail_cloudshell)
-
To set a default project, run the following command:
`gcloud config set project <project-id>`
-
To enable the APIs, run the following command:
`gcloud services enable admin.googleapis.com pubsub.googleapis.com gmail.googleapis.com`
- In the left-side navigation, click **APIs & Services** and verify API access status.
- []Log in to the [Google Admin Console](https://admin.google.com/).
-
Go to **Security** > **Access and Data Control** > **API controls**.
[See image.](#gmail_apicontrols)
- Click on **MANAGE DOMAIN WIDE DELEGATION**.
-
Click **Add New**.
[See image.](#gmail_domainnew)
-
Add the Service Account [Client ID](#gmail_clientid) noted down earlier to the **client ID** field, paste in the following scopes to the **OAuth Scopes** field, and click **Authorize**.
For more information about the APIs or OAuth Scopes, see the [API/Oauth Scope Permissions](#gmailtable) table.
`https://www.googleapis.com/auth/pubsub,
https://www.googleapis.com/auth/admin.directory.user,
https://www.googleapis.com/auth/admin.reports.audit.readonly,
https://mail.google.com/,
https://www.googleapis.com/auth/admin.reports.usage.readonly,
https://www.googleapis.com/auth/admin.directory.user.security,
https://www.googleapis.com/auth/admin.directory.group.readonly,
https://www.googleapis.com/auth/admin.directory.orgunit.readonly`
-
[]From the Google Admin Console, go to **Account** > **Admin roles**.
[See image.](#gmail_adminroles)
- Verify that you have one of the following roles:
- A role with Super Admin Role permissions.
-
A custom role that has the following API permissions:
- Organization Units > Read
- Users > Read
- Groups > Read
As well as these admin console privileges:
- Organization Units > Read
- Users > Read
- Groups > Read
These can be found in the right-side navigation after clicking on the role.
- If you need to create a new custom role:
- Click **Create new role** from the **Admin roles** page.
- Enter a name and description for the role and click **Continue**.
- Select the same privileges listed previously in Step b, ii.
- []Once you have the role, select it and go to **Assign role** > **Assign members** to add a user to this role.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants** and click **Add SaaS Application Tenant**.
- Select **Gmail**.
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique. This name is displayed when configuring the Data at Rest ScanningDLP policy, Malware Detection policy, and Scan Configuration.
- Enter the **Google Admin Email ID** associated with the role you [previously assigned](#gmail_role). This value is treated as the tenant ID, and Zscaler internally fetches the tenant domain from it.
-
Under Authorize the SaaS Application, select **Custom**.
[See image.](#gmail_custom)
- Upload the private key JSON file that you downloaded in [Step 1](#gmail_step1) while creating a service account and click **Authorize**.
- If you want to add trusted domains or users, you can add them to either the **External Trusted Domains** or **External Trusted User** fields and click **Add Items**.
- Click Save and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
- [][1. Create a service account for the organization.](#drive_step1)
- [2. Ensure connector has access to required APIs.](#drive_step2)
- [3. Add OAuth client to Google Admin.](#drive_step3)
- [4. Ensure admin role with appropriate permission is present.](#drive_step4)
- [5. Onboard with ZIA.](#drive_step5)
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com/) and select any project or create new project within the organization.
-
Create a service account for the selected project. In the left-side navigation, go to **IAM & Admin** > **Service Accounts** > **Create Service Account**.
[See image.](#drive_service)
- Provide a name for the service account and click **Create and Continue**.
- Click **Continue** without granting access or permissions to the project, then click **Done** without granting user access to the service account.
- []On the **Service accounts** page, note down the OAuth2 Client ID.
- Click the service account you created and click the **Keys** tab.
- Click **Add Key** and from the drop-down list click **Create new key**.
- In the **Create private key for <service account> dialog** box, select the key type as **JSON** and click **Create**. The private key is downloaded to your computer. Click **Close**.
- []Go to the project you created the service account for in [Step 1](#drive_step1) and copy your project ID.
-
To enable APIs for the project, from the main Google Cloud Platform page, click the **Activate Cloud Shell** icon.
[See image.](#drive_cloudshell)
-
To set a default project, run the following command, pasting in your Project ID where indicated:
`gcloud config set project <project-id>`
-
Enable the APIs by running the following command:
`gcloud services enable admin.googleapis.com pubsub.googleapis.com drivelabels.googleapis.com drive.googleapis.com`
- In the left-side navigation, click **APIs & Services** and verify API access status.
- []Log in to the [Google Admin Console](https://admin.google.com/).
-
Go to **Security** > **Access and Data Control** > **API controls**.
[See image.](#drive_apicontrols)
- Click on **MANAGE DOMAIN WIDE DELEGATION**.
-
Click **Add New**.
[See image.](#drive_domainnew)
-
Add the Service Account [Client ID](#drive_clientid) noted down earlier to the **Client ID** field, paste in the following scopes to the **OAuth Scopes** field, and click **AUTHORIZE**.
For more information about the APIs or OAuth Scopes, see the [API/Oauth Scope Permissions](#drivetable) table.
`https://www.googleapis.com/auth/admin.directory.user,
https://www.googleapis.com/auth/drive,
https://www.googleapis.com/auth/admin.reports.audit.readonly,
https://www.googleapis.com/auth/admin.reports.usage.readonly,
https://www.googleapis.com/auth/admin.directory.user.security,
https://www.googleapis.com/auth/admin.directory.group.readonly,
https://www.googleapis.com/auth/admin.directory.orgunit.readonly,
https://www.googleapis.com/auth/drive.admin.labels`
-
[]From the Google Admin Console, go to **Account** > **Admin roles**.
[See image.](#drive_adminroles)
- Verify that you have one of the following roles:
- A role with Super Admin Role permissions.
-
A custom role that has the following API permissions:
- Organization Units > Read
- Users > Read
- Groups > Read
As well as these admin console privileges:
- Services > Drive and Docs > Settings > Move any file or folder into shared drives
- Services > Drive and Docs > Settings > Manage Labels
- Reports
These can be found in the right-side navigation after clicking on the role.
- If you need to create a new custom role:
- Click **Create new role** from the **Admin roles** page.
- Enter a name and description for the role and click **Continue**.
- Select the same privileges listed previously in Step b, ii.
- []Once you have the role, select it and go to **Assign role** > **Assign members** to add a user to this role.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants** and click **Add SaaS Application Tenant**.
- Select **Google Drive**.
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique. This name is displayed when configuring the Data at Rest ScanningDLP policy, Malware Detection policy, and Scan Configuration.
- Enter the **Google Admin Email ID** associated with the role you [previously assigned](#drive_role). This value is treated as the tenant ID, and Zscaler internally fetches the tenant domain from it.
-
Under Authorize the SaaS Application, select **Custom**.
[See image.](#drive_custom)
- Upload the private key JSON file that you downloaded in [Step 1](#drive_step1) while creating a service account and click **Authorize**.
- Click Save and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
- [][1. Create a service account for the organization.](#work_step1)
- [2. Ensure connector has access to required APIs.](#work_step2)
- [3. Add OAuth client to Google Admin.](#work_step3)
- [4. Ensure admin role with appropriate permission is present.](#work_step4)
- [5. Onboard with ZIA.](#work_step5)
- []Log in to the [Google Cloud Platform](https://console.cloud.google.com/) and select any project or create new project within the organization.
-
Create a service account for the selected project. In the left-side navigation, click **IAM & Admin** > **Service Accounts** > **Create Service Account**.
[See image.](#work_service)
- Provide a name for the service account, copy the email address, and click **Create and Continue**.
- Click **Continue** and then click **Done**.
- []On the **Service accounts** page, note down the OAuth2 Client ID.
- Click the service account you created and click the **Keys** tab.
- Click **Add Key** and from the drop-down list click **Create new key**.
- In the **Create private key for <service account> dialog** box, select the key type as **JSON** and click **Create**. The private key is downloaded to your computer. Click **Close**.
- []Go to the project you created the service account for in [Step 1](#work_step1) and in the left-side navigation, go to **APIs & Services** > **Enabled APIs and services**.
-
Click on **ENABLE APIS AND SERVICES**.
[See image.](#work_enable)
- Search for `Gmail` in the search bar in the API Library.
- Click and open **Gmail API**.
- Click on **Enable**.
- Repeat the previous 3 steps for **Admin SDK API** and **Google Drive API**.
- []Log in to the [Google Admin Console](https://admin.google.com/).
-
Go to **Security** > **Access and Data Control** > **API controls**.
[See image.](#work_apicontrols)
- Click on **MANAGE DOMAIN WIDE DELEGATION**.
-
Click **Add New**.
[See image.](#work_domainnew)
-
Add the Service Account [Client ID](#work_clientid) noted down earlier to the **Client ID** field, paste in the following scopes to the **OAuth Scopes** field, and click **Authorize**.
For more information about the APIs or OAuth Scopes, see the [API/Oauth Scope Permissions](#worktable) table.
`https://www.googleapis.com/auth/admin.directory.user,
https://www.googleapis.com/auth/drive,
https://www.googleapis.com/auth/admin.reports.audit.readonly,
https://www.googleapis.com/auth/admin.reports.usage.readonly,
https://mail.google.com/,
https://www.googleapis.com/auth/admin.directory.user.security,
https://www.googleapis.com/auth/admin.directory.group.readonly,
https://www.googleapis.com/auth/admin.directory.orgunit.readonly,
https://www.googleapis.com/auth/gmail.settings.sharing,
https://www.googleapis.com/auth/gmail.settings.basic`
-
[]From the Google Admin Console, go to **Account** > **Admin roles**.
[See image.](#work_adminroles)
- Confirm that the chosen Workspace admin account is assigned the **Super Admin** role.
- []In the ZIA Admin Portal, go to **Administration** > **SaaS Application Tenants** and click **Add SaaS Application Tenant**.
- Select **Google Workspace**.
- Under **Name the SaaS Application Tenant**, enter a name for the SaaS application tenant. It must be unique. This name is displayed when configuring the Data at Rest ScanningDLP policy, Malware Detection policy, and Scan Configuration.
- Enter the **Google Workspace Admin Email ID**, which should be the organization admin or user email address. This value is treated as the tenant ID, and Zscaler internally fetches the tenant domain from it.
-
Under Authorize the SaaS Application, select **Custom**.
[See image.](#work_custom)
- Upload the private key JSON file that you downloaded in [Step 1](#work_step1) while creating a service account and click **Authorize**.
- Click Save and [activate the change](/zia/saving-and-activating-changes-zia-admin-portal).
[]![Create service account](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step1_service_accounts_small.png)
[]![Create service account menu, Grant this service account access to project, Pub/Sub Admin role highlighted.](/downloads/zia/policies/saas-security-api/saas-application-tenants/authorizing-custom-zscaler-connector-google-applications/Pub%20Sub%20role.png)
[]![Create service account](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step1_service_accounts_small.png)
[]![Create service account](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step1_service_accounts_small.png)
[]![Grant user access](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step1_grant_user.png)
[]![Activate Cloud Shell](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell_small.png)
[]![Activate Cloud Shell](/downloads/zia/policies/saas-security-api/authorizing-google/GCP_002_CloudShell_small.png)
[]![Admin API Controls](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_apicontrols.png)
[]![Admin API Controls](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_apicontrols.png)
[]![Admin API Controls](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_apicontrols.png)
[]![Add new API](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_domainnew_small.png)
[]![Add new API](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_domainnew_small.png)
[]![Add new API](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step3_domainnew_small.png)
[]![Admin account admin roles](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step4_adminroles_small.png)
[]![Admin account admin roles](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step4_adminroles_small.png)
[]![Admin account admin roles](/downloads/zia/policies/saas-security-api/authorizing-google/gmail_step4_adminroles_small.png)
[]![Zscaler Custom Connector](/downloads/zia/policies/saas-security-api/authorizing-google/google_step5_custom.png)
[]![Zscaler Custom Connector](/downloads/zia/policies/saas-security-api/authorizing-google/google_step5_custom.png)
[]![Zscaler Custom Connector](/downloads/zia/policies/saas-security-api/authorizing-google/google_step5_custom.png)
[]![Enable APIs and Services](/downloads/zia/policies/saas-security-api/authorizing-google/work_step2_enableapis.png)