# Google Cloud Platform - Vulnerabilities
Source: https://help.zscaler.com/uvm/google-cloud-platform-vulnerabilities
PDF: https://help.zscaler.com/pdf/com/en/1528271.pdf

![The Google Cloud Platform Assets tile](/downloads/uvm/configure/sources/google-cloud-platform-vulnerabilities/mceclip0.png)
Google Cloud Platform (GCP) Vulnerabilities scans GCP resources for security vulnerabilities, helping organizations proactively identify and mitigate risks to their cloud infrastructure.
Refer to the [Google Cloud documentation](https://cloud.google.com/asset-inventory/docs/roles-permissions) for the scopes that are utilized by the connector.
Required Parameters
- The appropriate GCP service must be enabled in the chosen account. If you are not using this service there is no data to retrieve.
- Service Account API Keys: A JSON file containing the API keys with access to the GCP project.
To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/security-command-center/docs/reference/rest/v2/folders.sources.findings/list).
GCP Service Account Setup
To set up the GCP service account:
- Log in to the GCP Console.
- From the project drop-down menu, select your project.
- From the left-side navigation, select **IAM & Admin** > **Service Accounts**.
![Selecting IAM & Admin > Service Accounts in the GCP console](/downloads/uvm/configure/sources/google-cloud-platform-vulnerabilities/mceclip1.png)
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
![Assigning the Viewer role to the service account in the GCP console](/downloads/uvm/configure/sources/google-cloud-platform-vulnerabilities/mceclip2.png)
- On the **Keys** tab, from the **Add Key** drop-down menu, select **Create new key**.
![Creating a new key in the service account in the GCP console](/downloads/uvm/configure/sources/google-cloud-platform-vulnerabilities/mceclip3.png)
- Select **JSON** and click **Create**. A JSON file is downloaded.
- Copy the content of the JSON key file into the GCP connector creation workflow.