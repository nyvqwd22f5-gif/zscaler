# Onboarding a Google Cloud Platform Account
Source: https://help.zscaler.com/zpc/onboarding-google-cloud-platform-account
PDF: https://help.zscaler.com/pdf/com/en/1394166.pdf

Zscaler Posture Control (ZPC) supports onboarding Google Cloud Platform (GCP) cloud accounts. When onboarded, ZPC provides insight into your account's security posture. ZPC provides two automation bash scripts, initial script and onboarding script, that you can run on your Google Cloud Console.
- [Initial script](#initial-script)
- [Onboarding script](#onboarding-script)
To onboard a GCP cloud account:
- [1. Ensure all prerequisites are met.](#gcp-prerequisites)
- [2. Onboard a GCP cloud account.](#gcp-onboarding)
When you onboard a cloud account, you can verify whether the cloud account is onboarded successfully and configuration metadata is being collected. To learn more, see [About Cloud Accounts](/zpc/about-cloud-accounts).
In addition to onboarding your GCP cloud accounts on ZPC, you can configure ZPC to collect additional configuration metadata:
- Set up vulnerability scanning for your GCP cloud workloads and cloud container registries. To learn more, see [Configuring Vulnerability Scanning for Cloud Accounts](/zpc/configuring-vulnerability-scanning-cloud-accounts).
- Connect your Google Kubernetes Engine (GKE) clusters with ZPC to gain visibility into your cluster security posture. To learn more, see [Onboarding a Google Kubernetes Engine Cluster](/zpc/onboarding-google-kubernetes-engine-cluster).
[]
The inital script:
- Recognizes the GCP organization. You can choose which projects in the organization you want to onboard to ZPC.
- Enables the following API services for ZPC on each selected project:
- `admin`
- `apikeys`
- `cloudasset`
- `cloudresourcemanager`
- `iam`
- `monitoring`
- `orgpolicy`
- Creates a service account with the name `ZPC-${TENANT_HASH}` in the GCP project where the script is run on the GCP Cloud Shell.
- Binds IAM policies to the service account for the following roles on the organization level:
- `roles/browser`
- `roles/iam.organizationRoleViewer`
- `roles/resourcemanager.folderViewer`
- Binds IAM policies to the service account for the following roles on the ZPC service account:
- `roles/iam.serviceAccountTokenCreator`
- `roles/iam.securityReviewer`
[]
The onboarding script:
- Updates the following permissions for the service account for the entire organization, folders, or projects:
- `roles/viewer`
- `roles/cloudasset.viewer`
- `roles/bigquery.dataViewer`
- `roles/actions.Viewer`
- Creates a custom role with the name `ZPC_${TENANT_HASH}` and assigns it the `storage.buckets.get` permission.
- Assigns the following additional roles to the service account, if you have vulnerability scanning enabled:
- `roles/containerregistry.ServiceAgent`
- `roles/cloudkms.cryptoKeyEncrypterDecrypter`
[]
You need to meet the following prerequisites before onboarding a GCP cloud account:
- Be an administrator. To learn more, see [About Administrators](/zpc/about-administrators).
- Have the GCP owner role.
- Make sure all GCP projects have the Cloud Assets API enabled.
[]
To onboard a GCP cloud account:
- Go to **Administration** > **Cloud Accounts**.
- Click **Add Account**.
- Under **Select Cloud Type**, click the **GCP** tile.
- On the **Configuration** page, you can:
- View the prerequisites for running the configuration script. The configuration bash script lists all the GCP accounts.
- Copy the configuration bash script.
[See image.](#gcp-configuration)
- Access the [GCP Cloud Console](https://console.cloud.google.com/), and use the project drop-down menu to select a project or organization where you want the ZPC service account to be created.
- Click the **Activate Cloud Shell** icon.
- Verify that you are in the intended project by running the following command:
gcloud projects describe $(gcloud config get-value project) --format="value(name)"
- Paste and run the script command you copied earlier.
- In the **Authorize Cloud Shell** pop-up window, click **Authorize**.
- After the script successfully runs, click **Grant Consent to Service Account**. This allows the service account to collect configuration and identity metadata.
- Select your Google account, then click **Allow**.
- After the script is deployed, in the ZPC Admin Portal, click **Next**.
- If you onboarded a GCP organization, you can select the projects you want to onboard to ZPC.
[See image.](#account-selection)
- Select your business unit from the drop-down menu.
[See image.](#business-unit-selection)
- On the **Deploy Template** page, you can:
- View the prerequisites for running the deploy template bash script. The deploy template script onboards all selected GCP accounts on to ZPC.
- Copy the deploy template bash script.
[See image.](#deploy-template-script)
- Access the [GCP Cloud Console](https://console.cloud.google.com/), and run the script command you copied eariler.
- After the script is deployed, in the ZPC Admin Portal, click **Finish**.
[]
![View the configuration page for onboarding a GCP organization.](/downloads/zpc/administration/cloud-accounts/onboarding-google-cloud-platform-account/zpc-gcp-organization-onboarding.png)
[]
![View the select accounts page for GCP onboarding.](/downloads/zpc/administration/cloud-accounts/onboarding-google-cloud-platform-account/zpc-account-selection-onboarding.png)
[]
![View the select business units page for GCP onboarding.](/downloads/zpc/administration/cloud-accounts/onboarding-google-cloud-platform-account/zpc-select-business-unit-onboarding.png)
[]
![View the deploy template page for GCP onboarding.](/downloads/zpc/administration/cloud-accounts/onboarding-google-cloud-platform-account/zpc-gcp-deploy-script-onboarding.png)