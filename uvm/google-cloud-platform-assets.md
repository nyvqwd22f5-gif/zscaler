# Google Cloud Platform - Assets
Source: https://help.zscaler.com/uvm/google-cloud-platform-assets
PDF: https://help.zscaler.com/pdf/com/en/1528261.pdf

![The Google Cloud Platform - Assets tile](/downloads/uvm/configure/sources/google-cloud-platform-assets/mceclip0.png)
Google Cloud Platform (GCP) Assets is a metadata inventory service that allows you to view, monitor, and analyze all your Google Cloud assets. The GCP Assets supports the following assets:
- storage.googleapis.com/Bucket
- artifactregistry.googleapis.com/Repository
- artifactregistry.googleapis.com/DockerImage
- compute.googleapis.com/Instance
- container.googleapis.com/Cluster
To learn about the scopes utilized by the connector, refer to the [Google documentation](https://www.googleapis.com/auth/cloud-platform).
Required Parameters
- API scopes: The API scope `Cloud asset.assets.listResourceIAM` permission is required on the specified resource parent.
- Service account API Keys: A JSON file containing the API keys with access to the GCP project.
To learn more, refer to the [Google Cloud documentation](https://cloud.google.com/asset-inventory/docs/reference/rest/v1/assets/list).
Prerequisites
To allow the platform to access your Google Cloud Assets via API, ensure that your **Cloud Asset API** is enabled.
To enable the API for your project:
- Log in to the Google Cloud console.
- Go to **APIs & Services** > **Library**.
[![Navigating to the APIs & Services page and selecting the Library tab in the Google Cloud console](/downloads/uvm/configure/sources/google-cloud-platform-assets/f5bb9085-fa90-48db-be94-043237cef2f0.png)
](https://APIs%20&%20Services%20Library)
- In the **Search for APIs & Serivces** field, enter `Cloud Asset API`. Then, select **Cloud Asset API**.
- Click **Enable**.
To learn more, refer to the [Google documentation](https://support.google.com/googleapi/answer/6158841?hl=en).
Retrieving the Parameters
To set up the GCP service account:
- Log in to GCP console.
- From the project drop-down menu, select the project.
- From the **IAM & Admin** left-side navigation, select **Service Accounts**.
![Selecting IAM & Admin > Service Accounts in the GCP console](/downloads/uvm/configure/sources/google-cloud-platform-assets/mceclip1.png)
- Click **Create service account**.
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
![mceclip2.png](/downloads/uvm/configure/sources/google-cloud-platform-assets/mceclip2.png)
- On the **Keys** tab, from the **Add Key** drop-down menu, select **Create new key**.
![mceclip4.png](/downloads/uvm/configure/sources/google-cloud-platform-assets/mceclip4.png)
- Select **JSON** and click **Create**. A JSON file is downloaded.
- Copy the content of the JSON key file into the GCP connector creation workflow.