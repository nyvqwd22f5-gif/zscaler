# Google Cloud Platform - Misconfigurations
Source: https://help.zscaler.com/uvm/google-cloud-platform-misconfigurations
PDF: https://help.zscaler.com/pdf/com/en/1528266.pdf

![The Google Cloud Platform Misconfigurations tile](/downloads/uvm/configure/sources/google-cloud-platform-misconfigurations/mceclip0.png)
Google Cloud Platform (GCP) Misconfigurations automatically detects and alerts users to misconfigurations in their Google Cloud environments, helping to prevent security breaches and compliance violations.
Refer to the [Google Cloud documentation](https://cloud.google.com/asset-inventory/docs/roles-permissions) for the scopes that are utilized by the connector.
Required Parameters
- Username
- Service Account API Keys: A JSON file containing the API keys with access to the GCP project.
To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/security-command-center/docs/reference/rest/v2/folders.sources.findings/list).
GCP Service Account Setup
To set up the GCP service account:
- Log in to the GCP Console.
- From the project drop-down menu, select your project.
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**.
- On the **Service accounts** page, select **Create service account**.
- On the **Create service account** page, configure the following:
- On the **Create service account** tab:
- **Service account name**: Enter a name for the service account.
- **Service account ID**: Enter a unique ID for the service account.
- **Service account description**: Enter a description for the service account.
- On the **Permissions (optional)** tab, configure your permissions.
- On the **Principals with access (optional)** tab, you can grant access to users or groups.
- On the **Service accounts** page, select the service account you created.
- From the **Select a role** drop-down menu, in the **Quick Access** section, click **Basic**.
- In the **Roles** section, select **Viewer** and click **Done**.
- On the **Keys** tab, from the **Add Key** drop-down menu, select **Create new key**.
- Select **JSON** and click **Create**. A JSON file is downloaded.
- Copy the content of the JSON key file into the GCP connector creation workflow.