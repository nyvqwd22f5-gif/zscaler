# Adding a Google Cloud Platform Account
Source: https://help.zscaler.com/cloud-branch-connector/adding-google-cloud-platform-account
PDF: https://help.zscaler.com/pdf/com/en/1528924.pdf

This article provides information on how to onboard a Google Cloud Platform (GCP) account to enable tag discovery services within the Zscaler Cloud & Branch Connector Admin Portal. To learn more, see [About Google Cloud Platform Accounts](/cloud-branch-connector/about-google-cloud-platform-accounts).
Adding a GCP Account
To add a GCP account:
- Sign in to the Cloud & Branch Connector Admin Portal.
- Go to **Administration** > **Partner Integrations** > **GCP**.
-
Click **Add Account**.
[See image.](#addaccount)
The **Add GCP Account** window appears.
- In the **Add GCP Account** window:
- On the **Account Name And Credential** tab:
- **Account Name**: Enter a name for your GCP account.
- **Zscaler Service Account Email**: If you plan to deploy the GCP account without Terraform, copy and save the email that appears in this field. If you are deploying the GCP account with Terraform, you do not need to copy and save the email.
- **Customer Service Account Email**: Enter your service account email to grant the Zscaler service permission to use the service account to discover workloads. To retrieve this email address, configure your GCP environment. To learn more, see [Configuring Workload Discovery for Workloads in Google Cloud Platform](/cloud-branch-connector/configuring-workload-discovery-workloads-google-cloud-platform).
-
**Terraforming Script**: (Optional) Click the **Download Script** button and run the script in your GCP account to create the service account. Running the script provides appropriate permissions for the Zscaler service to have read access to your projects. To learn more, see [Configuring Workload Discovery for Workloads in Google Cloud Platform](/cloud-branch-connector/configuring-workload-discovery-workloads-google-cloud-platform).
[See image.](#namecredential)
- On the **Projects and Regions** tab:
- **Projects**: Select the projects that are visible to the Zscaler service. The available options depend on the credentials you entered on the **Account Name and Credentials** tab.
-
**Region**: Select the regions where the GCP account operates.
[See image.](#projectsregions)
-
On the **Cloud Connector Group** tab, select the checkboxes of the Cloud Connectors that you want to add to the GCP account.
[See image.](#cloudconnectorgroup)
- On the **Review** tab, confirm that the information is correct and click **Save and Next**.
[]
![The Add Account button on the GCP tab of the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-workload-discovery-service-google-cloud-platform-accounts/AddGCPAccountbutton.png)
[]
![The Account Name and Credentials tab in the Add Google Cloud Account window of the Partner Integrations page in the Zscaler Cloud & Branch Connector Admin Portal  ](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-workload-discovery-service-google-cloud-platform-accounts/cloud-connector-partner-integrations-gcp-account-name-credentials.png)
[]
![The Projects and Regions tab of the Add Google Cloud Account window on the Partner Integrations page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/configuring-workload-discovery-service-google-cloud-platform-accounts/cloud-connector-partner-integrations-gcp-projects-regions.png)
[]
![The Cloud Connector Group tab of the Add Google Cloud Account window on the Partner Integrations page of the Zscaler Cloud & Branch Connector Admin Portal](/downloads/cloud-branch-connector/administration/cloud-connector-partner-integrations/adding-google-cloud-platform-account/CloudConnectorGroup.png)