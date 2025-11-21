# Managing Evidence Configuration
Source: https://help.zscaler.com/dspm/managing-evidence-configuration
PDF: https://help.zscaler.com/pdf/com/en/1529299.pdf

DSPM identifies files and tables containing [sensitive data](/dspm/viewing-sensitive-data-details) and generates evidence data for review. You can configure an AWS S3 bucket or Azure storage account container, to store these classified evidence data snippets. You can also use an existing storage account or S3 bucket present in one of the [regions selected](/dspm/onboarding-aws-organization#step3) while onboarding or allow DSPM to create a new one in the orchestrator account.
The S3 bucket or storage account container cannot be changed after it is added. You can only enable or disable the evidence configuration.
To manage evidence configuration:
- Go to **Administration** > **Configuration** > **Cloud Accounts**.
- Select the onboarded account.
-
Click **Manage**, and then select **Manage Evidence**.
[See image.](#manageevidence)
-
On the **Evidence Configuration** page, click the toggle to enable or disable the evidence configuration.
When disabled, DSPM stops sending evidence data to the specified storage account.
- [AWS](#aws-evidence)
- [Azure](#azure-evidence)
- [][Enable](#enablevidence)
- [Disable](#disableevidence)
[See image.](#enable-disable-toggle)
[]
To configure evidence storage for Azure, Zscaler recommends you to use the latest [onboarding templates](/dspm/viewing-roles-and-templates).
- [Enable](#enable-azureevidence)
- [Disable](#disable-azurevidence)
[See image.](#enable-disable-azure-evidence)
-
[]Select the required storage type:
- [Custom Container](#single-custom-evidence)
- [Zscaler Managed Container](#single-zscaler-evidence)
[See image.](#azure-zscalermanagedcontainer)
-
On the **Apply Changes** page, download the **Evidence **template and run it on the account where the storage account container is present.
[See image.](#applychanges-page)
For **Zscaler Managed Container** storage type, if you selected [Deploy private endpoint for secure communication](/dspm/selecting-orchestrator-and-monitoring-scope) while onboarding, you must add your system's IP address to the [Azure key vault](/dspm/deploying-azure-onboarding-template) created in the orchestrator account before running the evidence template. This is required when multiple users need to apply Terraform from different IP addresses.
To add your IP address:
- Sign in to the Azure portal and go to **Key vaults**.
-
On the **Key vaults** page, search and select the key vault created in the orchestrator account.
[See image.](#keyvaultspage)
- In the left-side navigation, go to **Settings **> **Networking**.
-
On the **Firewalls and virtual networks** tab:
- Select **Allow public access from specific virtual networks and IP addresses**.
- In the **Firewall **section, click **Add your client IP address** and enter your system's IP address.
[See image.](#networking-page)
- Click **Apply**.
[]Enter the existing storage account details:
- **Storage Account Resource ID**: The resource ID of the storage account.
- **Container Name**: The name of the container.
- **Key Vault Resource ID**: The resource ID of the key vault. This key vault is used to encrypt the evidence data in the container.
[See image.](#azure-custommanagedcontainer)
[]DSPM creates a storage container in the orchestrator account to upload the snippet of evidence data.
- []Click **Next**.
- On the **Apply Changes** page, click **Done**.
-
[]Select the required storage type:
- [Custom S3 Bucket](#byon-evidence)
- [Zscaler Managed S3 Bucket](#dspmevidence)
[See image.](#zscaler-s3bucket)
- On the **Apply Changes** page:
- Select the **CloudFormation **or **Terraform **template.
- Download the template and run it on the account where the specified S3 bucket is present.
- Click **Done**.
[]Enter the existing S3 bucket details:
- **S3 Bucket Name**: The name of the S3 bucket.
- **S3 Bucket Account ID**: The 12-digit account ID of the S3 bucket.
- **KMS Key ARN**: The KMS key ARN. This key is used to encrypt the evidence data in the S3 bucket.
[See image.](#customs3bucket)
[]DSPM creates an S3 bucket in the orchestrator account to upload the snippet of classified data.
- []Click **Next**.
- On the **Apply Changes** page, click **Done**.
[]![The Manage actions drop-down menu with list of actions available for the selected cloud account.](/downloads/dspm/administration/cloud-accounts-onboarding/aws-cloud-accounts/managing-evidence-configuration/dspm-manage-evidence.png)
[]![The Evidence Configuration page with toggle option to enable to disable the S3 bucket.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-aws-evidence-config.png)
[]![The Evidence Configuration page with Zscaler Managed S3 bucket option selected.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-zscalermanageds3bucket.png)
[]![The Evidence Configuration page with Custom S3 bucket option selected.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-customs3bucket.png)
[]
![The Apply Changes page displaying the Template type and Evidence template.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-azure-evidencetemplate.png)
[]![The Azure Evidence Configuration page with customer managed container selected.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-azurecustomercontainer-new.png)
[]![The Azure Evidence Configuration page with Zscaler managed container selected.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-zscalermanagedcontainer-new.png)
[]![The Azure Evidence Configuration page with annotation around enable evidence toggle.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-azure-evidence-config.png)
[]![The Key vaults page displaying the list of key vaults in the Azure portal.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-azure-key-vaults-page.png)
[]![The Networking page to add the IP address to the selected key vault.](/downloads/dspm/cloud-accounts-onboarding/cloud-account-management/managing-evidence-configuration/dspm-enter-IP%20address.png)