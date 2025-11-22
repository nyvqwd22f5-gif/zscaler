# Troubleshooting Cloud Connector with HashiCorp Vault for Google Cloud Platform
Source: https://help.zscaler.com/cloud-branch-connector/troubleshooting-cloud-connector-hashicorp-vault-google-cloud-platform
PDF: https://help.zscaler.com/pdf/com/en/1515891.pdf

This article provides troubleshooting information and guidelines about Cloud Connector deployment in Google Cloud Platform (GCP) with HashiCorp Vault, described in [Storing Your Secret Credentials in HashiCorp Vault for Google Cloud Platform-Based Cloud Connectors](/cloud-branch-connector/storing-your-secret-credentials-hashicorp-vault) and [Deploying Zscaler Cloud Connector on the Google Cloud Platform](/cloud-branch-connector/deploying-zscaler-cloud-connector-google-cloud-platform). You can learn about different issues, potential causes, and corresponding solutions for the deployed Zscaler Cloud Connectors.
Prerequisites
To troubleshoot your Cloud Connector, ensure that you have the following:
- In GCP:
- Access to the GCP console: The ability to view and modify settings and IAM service accounts and roles in GCP.
- Vault/GCP sync service account: A service account with the secrets JSON file exported from GCP and uploaded to HashiCorp with the **Service Account Key Admin** GCP role.
- Cloud Connector virtual machine (VM) service account: A service account assigned to the VM at deployment and referenced in HashiCorp as `bound_service_accounts` with the **Service Account Token Creator** GCP role.
- In HashiCorp:
- Access to the Vault CLI: The ability to view and modify settings in the Vault CLI.
- Vault address: The URL of your Vault instance.
- Secret path: The path within the Vault where secrets are stored.
- GCP IAM authentication: Ensure that the GCP auth method is enabled.
- GCP IAM role: The GCP IAM type authentication role.
Troubleshooting
The following is a step-by-step troubleshooting guide for Cloud Connector deployment in GCP with HashiCorp:
- [Verify the VM service account configuration](#ServiceAccountConfig)
- [Verify the VM configuration](#VMConfig)
- [Verify the Vault configuration](#VaultConfig)
- [Verify your VM network connectivity](#NetworkConnectivity)
The following table displays common issues and resolutions:
-
-
-
-
-
-
-
-
-
-
| **Potential Causes** | **Troubleshooting Action** |
| -------------------- | -------------------------- |
| Permission is denied or authentication fails. | Verify the following:The service account assigned to the Cloud Connector VMs has the **Service Account Token Creator** role.The service account is included in the Vault's `bound_service_accounts`.`max_jwt_exp` is correctly set in the Vault.Check your GCP `jwt`: `https://jwt.ms/` |
| The Vault is unreachable from the VM, causing network connectivity issues. | Verify the following:Firewall rules allow outbound traffic to the Vault on port 8200.The Vault address and DNS resolution are correct from the Cloud Connector.There are no network outages or issues with connectivity or routing. |
| Your access is denied to the secret path after authentication succeeds. | Verify the following:The policies attached to the IAM authentication role include "read and list" permissions for the secret path.The secret exists at the specified path.There are no incorrectly spelled words or incorrect paths. |
[]
To verify your service account configuration:
- Check the service account attached to the VM:
- Sign in to the [GCP console](https://console.cloud.google.com/).
- In the top-left corner of the console, select **Navigation menu (.)**.
- From the left-side navigation, select **Compute Engine** > **VM instances**.
- On the **VM instances** page, select your VM instance.
- On the **Details** tab, under **API and identity management**, verify that the correct **Service account** is displayed.
- Verify the service account permissions:
- Sign in to the [GCP console](https://console.cloud.google.com/).
- In the top-left corner of the console, select **Navigation menu (.)**.
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**
- On the **Service accounts** page, select your service account.
- On the service account page, select the **Permissions** tab.
- On the **Permissions** tab, ensure that the **Service Account Token Creator** role is correctly assigned.
- Confirm the service account in the HashiCorp Vault's `bound_service_accounts` by contacting your Vault administrator to verify that the service account email is listed in the `bound_service_accounts` for the IAM authentication role.
[]
To verify your VM configuration, check your VM metadata:
- Sign in to the [GCP console](https://console.cloud.google.com/).
- In the top-left corner of the console, select **Navigation menu (.)**.
- From the left-side navigation, select **Compute Engine** > **VM instances**.
- On the **VM instances** page, select your VM instance.
- On the **Details** tab, locate the **Custom metadata** section.
-
Verify that the metadata keys for **Vault Address**, **Secret Path**, and **IAM Auth Role** are correctly set per your Vault configuration.
`ZSCALER
hcp_vault_addr: "https://vault-cluster-public-vault-example.z1.hashicorp.cloud:8200"
hcp_vault_secret_path: "admin/secret/data/example-zscaler-secret"
hcp_vault_role_name: "example-iam-auth-role"`
[]
To verify your Vault configuration:
- Confirm your Vault address and accessibility:
- Ensure that the Vault address, protocol, and port number (i.e., 8200) are correct.
- Ensure that the Vault UI or API is reachable from your machine by testing the accessibility.
- Verify your GCP IAM authentication role in the Vault by confirming the following with your administrator:
- The GCP IAM authentication role exists and is named correctly.
- The type is set to `iam`.
- The appropriate policies are attached.
- The `max_jwt_exp` is set to `"60m"`.
- The `bound_service_accounts` include your VM service account.
- Verify your Vault GCP auth credentials:
- Configure the GCP auth method to use the `VaultServiceAccountKey.json` credentials. Ensure that you successfully created a service account with the **Service Account Key Admin** permissions and that the service account credentials are exported and used for `auth/gcp/config` (i.e., `VaultServiceAccountKey.json`).
-
HashiCorp CLI:
`vault write auth/gcp/config \`
`credentials=@VaultServiceAccountKey.json`
[]
To test your network connectivity:
- Verify that your network tags and firewall rules are correctly set:
- Sign in to the [GCP console](https://console.cloud.google.com/).
- In the top-left corner of the console, select **Navigation menu (.)**.
- From the left-side navigation, select **Compute Engine** > **VM instances**.
- On the **VM instances** page, select your VM instance.
- On the **Details** tab, in the **Network tags** section, note the tags assigned to your VM.
- In the top-left corner of the console, select **Navigation menu (.)**.
- From the left-side navigation, select **VPC Network** > **Firewall**.
- On the **Firewall policies** page, ensure that your outbound traffic to the Vault address on port 8200 is permitted.
- Secure Socket Shell (SSH) into your VM instance.
-
Replace `<vault-address>` with your Vault's address. Omit `https://` or `http://`.
`sudo bash
nc -zv vault-cluster-public-vault-abc.xyz.z1.hashicorp.cloud 8200
Connection to vault-cluster-public-vault-abc.xyz.z1.hashicorp.cloud 8200 port [tcp/*] succeeded!`
-
Test the connection using `curl`.
`curl -v <vault-address>:8200/v1/sys/health
A JSON response indicating Vault's health should be returned.`