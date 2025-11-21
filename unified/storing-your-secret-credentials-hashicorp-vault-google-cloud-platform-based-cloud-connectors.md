# Storing Your Secret Credentials in HashiCorp Vault for Google Cloud Platform-Based Cloud Connectors
Source: https://help.zscaler.com/unified/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors
PDF: https://help.zscaler.com/pdf/com/en/1520061.pdf

HashiCorp Vault is a cloud-agnostic method for storing and maintaining secret credentials. This article describes how to use HashiCorp IAM authentication to integrate a HashiCorp Vault with a new Cloud Connector based on the Google Cloud Platform (GCP).
You cannot migrate an existing Cloud Connector from GCP Secret Manager to HashiCorp Vault. You must deploy a new Cloud Connector using the Terrarform wizard.
Prerequisites
Make sure the following prerequisites are met:
- A HashiCorp Vault and Vault cluster have already been created.
- The Vault CLI is downloaded to your local machine.
For information, refer to the [HashiCorp Vault documentation](https://developer.hashicorp.com/vault).
Integration
Perform the following procedures to integrate a new GCP-based Cloud Connector with a dedicated public HashiCorp Vault.
This article describes how to configure a dedicated public HashiCorp Vault. The procedures may differ for self-managed Vault deployments. For example, for self-managed deployments, instead of logging in to the HashiCorp Cloud Portal, log in to your self-managed Vault FQDN or IP address.
- [1. Set up the HashiCorp Vault and secrets.](#HashiCorpVaultSetup)
- [2. Enable Vault to authenticate with GCP.](#GCPConfig)
- [3. Configure HashiCorp to enable GCP to authenticate with Vault.](#HashiCorpConfig)
- [4. Gather information for the Terraform deployment wizard.](#ItemsTerraform)
[]To set up the Vault and secrets, perform the following procedure in the [HashiCorp Cloud Portal](https://portal.cloud.hashicorp.com):
- Log in to the [HashiCorp Cloud Portal](https://portal.cloud.hashicorp.com).
- Navigate to your Vault (**Vault Dedicated** > <Vault Cluster Name> > **Launch web ui**).
-
At the bottom of the left-side navigation, set **admin **as the current namespace.
[See image.](#VaultLeftNavNamespace)
- From the left-side navigation, select **Secrets Engines**.
- On the **Secrets Engines** page, click **Enable new engine**. The **Enable a Secrets Engine** page appears.
-
In the **Generic **section, click **KV**.
[See image.](#VaultEnableKVSecretsEngine)
- Another **Enable a Secrets Engine** page appears. In the **Path **field, enter the path (for example, `secretKV`).
-
Click **Enable engine**. The secrets engine** **page appears (in this example, the **secretKV **page).
[See image.](#VaultSecrets_KV_Engine)
- Click **Create secret**. The **Create Secret** page appears. In the **Path for this secret** field, enter your path (for example, `secretKV`).
-
In the **Secret data** section fields:
- Enter `username`. For the corresponding value, enter your dedicated Cloud Connector deployment username. Click **Add**.
- Enter `password`. For the corresponding value, enter your dedicated Cloud Connector deployment password. Click **Add**.
- Enter `api_key`. For the corresponding value, enter the value you copied from the [API Keys](/unified/about-api-configuration) page in the Admin Portal.
[See image.](#CreateSecret)
- Click **Save**.
[]To enable Vault to authenticate with GCP, perform the following procedures in the [GCP Console](https://console.cloud.google.com/):
- [a. Create a service account for Vault to authenticate with GCP.](#CreateServiceAcctforVaultGCP)
- [b. Create a service account key credential file.](#CreateServiceAcctKeyFile)
[]
Instead of using the predefined role as described in this procedure, you can create a custom role and assign the following 5 required permissions: **compute.instanceGroups.list**,** compute.instances.get**,** iam.serviceAccountKeys.get**,** iam.serviceAccounts.get**, and **iamService.signJwt**. (The predefined role has additional roles assigned to it.)
- Log in to the [GCP Console](https://console.cloud.google.com/).
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**.
- Click **Create Service Account**.
- In the **Service account details** section:
-
**Service account name**: Enter a unique display name for the service account.
GCP generates a service account ID based on this name.
-
**Service account ID**: If necessary, change the ID.
You cannot change the ID after the service account is created.
-
**Service account description**: (Optional) Enter a description of the service account's purpose.
[See image.](#CreateServiceAccount)
- Click **Create and Continue**.
-
On the **Grant this service account access to project** page, from the **Role **drop-down menu, select **Service Account Key Admin**.
[See image.](#SelectServiceAccountRole)
- Click **Done** to create the service account.
[]
- Navigate to **IAM & Admin** > **Service Accounts**.
- Select the Vault service account and then click **Keys**.
- From the **Keys **page, click **Add Key** > **Create new key**.
-
Select **JSON **as the **Key type**, then click **Create**. The private key downloads to your computer.
[See image.](#AddKey)
- Copy the JSON file to a secure location. You will need this file in the next section.
[]To enable GCP to authenticate with Vault, perform the following procedures in the [HashiCorp Cloud Portal](https://portal.cloud.hashicorp.com/):
- [a. Enable the GCP secrets engine.](#EnableSecretsEngine)
- [b. Configure the GCP authentication method to use the Vault service account credentials.](#ConfigureGCPAuth)
- [c. Create a policy file and policy.](#Policy)
- [d. Create an access role for an IAM service account.](#RoleforIAM)
[]
- Log in to the [HashiCorp Cloud portal](https://portal.cloud.hashicorp.com/) and navigate to your Vault (**Vault Dedicated** > <Vault Cluster Name> > **Launch web UI**).
- From the left-side navigation, select **Secrets Engines**.
- On the **Secrets Engines** page, click **Enable new engine**. The **Enable a Secrets Engine** page appears.
-
In the Cloud section, click **Google Cloud**.
[See image.](#VaultEnableGCPSecretsEngine)
- Another **Enable a Secrets Engine** page appears. In the **Path** field, enter the path (for example, `gcp`).
- Click **Enable engine**.
[]
- From the left-side navigation, select **Access** > **Authentication methods**.
- Select **gcp**. The gcp page opens.
- On the **Configuration **tab, click **Configure**. The **Configure Google Cloud** page appears.
-
Under **Credentials**, click **Choose File**.
[See image.](#VaultSelectAuthFile)
- Navigate to and select the [**VaultServiceAccountKey.json** file](#CreateServiceAcctKeyFile) you created in the previous section.
[]You must create a policy that grants read and list capabilities to access your secrets path.
- From the left-side navigation, select **Policies **> **ACL Policies**.
- Click **Create ACL policy**. In the **Create ACL Policy** dialog box:
- **Name**. Enter a name for the new policy (for example, `gcp-policy`).
-
**Policy**: Enter the ACL policy rules as shown below:
`# Read permission on the k/v secrets
path "/secretKV/*"
capabilities = ["read", "list"]
}`
where `path` is the **Path for this secret** value you provided in [Set up the HashiCorp Vault and secrets](#HashiCorpVaultSetup) (in this example, `secretKV`), and the `capabilities` are `read` and `list`.
- Click **Create policy**.
[]
You must use the Vault CLI to create this role.
- Open the Vault cluster overview page (<Vault Cluster Name> > **Overview**).
- Under **Quick actions**, select **How to access via **> **Command Line (CLI)**.
-
Enter the following:
`vault write auth/gcp/role/"<Name of Role>" \
type="iam" \
policies="<Name of Policy You Created>" \
bound_service_accounts="<GCP Service Email for Cloud Connector Service Account>"
max_jwt_exp="60m"`
where `bound_service_accounts` is the email address associated with the [VM service account](/unified/deploying-zscaler-cloud-connector-google-cloud-platform#VMServiceAcct) you created previously.
For example:
`vault write Auth/gcp/role/cc-vm-service-account \
type="iam" \
policies="gcp_policy" \
bound_service_accounts="cc-vm-service-account@cc-abc-123456.iam.gserviceaccount.com" \
max_jwt_exp="60m"`
[]Gather the following information to respond to Terraform deployment wizard prompts.
- From the [HashiCorp Cloud Portal](https://portal.cloud.hashicorp.com/):
-
Cluster Public URL. Navigate to your Vault cluster page, and in the Cluster URLs section, click **Public**.
[See image.](#ClusterURL)
-
Full API path for the secret. Navigate to your secret page. The **API path** is displayed in the Paths section.
[See image.](#APIpath)
- Name of the [access role you created for an IAM service account](#RoleforIAM).
- From the [Google Cloud Portal](https://console.cloud.google.com/) (if you answered that you already have a service account when prompted by the Terraform wizard):
- [Service Account email from Vault service account details](/unified/deploying-zscaler-cloud-connector-google-cloud-platform#VMServiceAcct). You must have access to the service account to see this information.
[]![Selecting admin as the namespace](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/VaultNamespace.png)
[]![Creating secrets for KV Secrets Engine](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/VaultEnableKVSecretsEngine_1.png)
[]![Creating secrets for KV Secrets Engine](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/kv_create_secrets_1.png)
[]![Creating a secret for KV Secrets Engine](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/HCPCreateSecretPage_1.png)
[]![Creating service account for Vault to authenticate with GCP](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/GCPCreateServiceAccount_1.png)
[]![Selecting Service Account Key Admin role](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/CreateGCP_HCP_ServiceAccount2.png)
[]![Create private key in Google Cloud Platform](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/GCPAddPrivateKey_1.png)
[]![Enabling the Google Cloud secrets engine](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/VaultEnableGCPSecretsEngine_1.png)
[]![Selecting JSON file for Vault to communicate with Google Cloud](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/VaultSelectAuthFile_1.png)
[]![Copying the cluster URL](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/HCPclusterURL_1.png)
[]![Finding the API path](/downloads/unified/infrastructure/cloud-branch-connector/deployment-management-virtual-devices/cloud-connector-deployment-management/storing-your-secret-credentials-hashicorp-vault-google-cloud-platform-based-cloud-connectors/HCPapiPath_1.png)