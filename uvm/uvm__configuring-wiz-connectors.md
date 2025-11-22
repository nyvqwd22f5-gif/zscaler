# Configuring the Wiz Connectors
Source: https://help.zscaler.com/uvm/configuring-wiz-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530953.pdf

Wiz analyzes all layers of the cloud stack to identify high-risk attack vectors to be prioritized and fixed.
To create the Wiz data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#wiz-tiles)
There are three available Wiz streams. Select those that are in scope based on your Wiz licenses and use cases:
- Vulnerability Findings: Retrieves details on detected vulnerabilities, such as affected software, version, and remediation recommendations with each being tied to a specific resource.
- Issues: Retrieves details on active security threats (e.g., vulnerabilities, misconfigurations, or exposed secrets) which includes severity, affected resources, and remediation recommendations for each identified threat.
- Configuration Findings: Retrieves misconfigurations in cloud resources, which includes the failed security checks associated with each resource.
[]
![The Wiz - Vulnerability Findings, Wiz - Issues, and Wiz - Configuration Findings tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-qualys-vmdr-pc-connectors/wiz-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [Client ID and Client Secret](#param1)
- [URL](#param2)
- [Token URL](#param3)
[]
To retrieve the client ID and client secret:
- Log in to the Wiz console.
- Go to **Settings** > **Service Accounts**.
- Click **+ Add Service Account**. In the window:
- Enter a name for the new service account.
- (Optional) Narrow the scope of this service account to specific projects.
-
Select the scopes you wish to grant the new service account.
Zscaler recommends assigning the scopes listed in the Roles and Permissions section.
- Click **Add Service Account**.
-
Copy the client ID and client secret.
Save the credentials securely. You cannot copy the client secret after this stage.
[]
The URL is the API endpoint URL used to send requests to the Wiz GraphQL API.
To retrieve your API endpoint URL:
- Log in to the Wiz console.
- Click the **User Profile** icon in the top-right of the page.
- Click **User Settings**.
- In the left-side navigation, click **Tenant**.
- Copy the **API Endpoint URL**.
An example of an API endpoint URL is `https://api.us1.app.wiz.io/graphql`. The aspects in the base URL that vary are the data center region (e.g., us1) and the suffix, which can be `.io` or `.us` depending on your Wiz tenant.
[]
The token URL is the authentication URL used to request an access token for a Wiz service account using client credentials.
To retrieve your token URL:
- Log in to the Wiz console.
- Go to **Settings** > **Service Accounts**.
-
The token URL is located at the top of the page in the service account description.
[See image.](#token-url)
Depending on your Wiz tenant, there are three possible token URLs:
| **Tenant** | **Endpoint** |
| ---------- | ------------ |
| Wiz Commercial | `https://auth.app.wiz.io/oauth/token` |
| Wiz for Gov (FedRAMP) | `https://auth.app.wiz.us/oauth/token` |
| Wiz Commercial hosted on AWS GovCloud | `https://auth.gov.wiz.io/oauth/token` |
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Project ID field](#project-id)
- [Asset Type drop-down menu](#asset-type)
- [Fetch configuration findings from the past selected days field](#fetch-configuration-findings)
- [Findings Status drop-down menu](#findings-status)
- [Issue Type drop-down menu](#issue-type)
- [Issue Severity drop-down menu](#issue-severity)
- [Issue Status drop-down menu](#issue-status)
[]
The project ID is the specific project where the data should be retrieved. You can limit data synchronization to a single project. If no project is specified, the connector fetches data from all projects accessible to the configured service account.
You can only specify one project.
To retrieve the project ID:
- Log in to Wiz console.
- Go to the **Projects** page.
- Click the three dot options menu to the right of the relevant project.
- Copy the project ID.
Ensure that the service account that is used to generate the token has the necessary permissions to access the specified project ID or, if no IDs are specified, to all projects accessible to the service account.
The Project ID field is applicable in the following streams:
- Wiz - Vulnerability Findings
- Wiz - Issues
- Wiz - Configuration Findings
[]
Use the Asset Type drop-down menu filter to limit vulnerability findings to specific asset categories. The following values are supported values:
- Virtual Machine
- Container Image
- Serverless
- Container
Only findings related to the selected asset type are retrieved. If no filter is applied, findings from all asset types are included.
The Asset Type drop-down menu is applicable in the Wiz - Vulnerability Findings stream.
[]
Enter the number of days to retrieve configuration findings that were first analyzed within that timeframe. For example, entering 30 returns configuration findings that were first analyzed within the last 30 days.
The Fetch configuration findings from the past selected days field is applicable in the Wiz - Configuration Findings stream.
[]
Select the statuses to include in the scope of the ingested data (i.e., Open, In Progress, Resolved, Rejected).
The Findings Status drop-down menu is applicable in the Wiz - Configuration Findings stream.
[]
Select the types of issues to include in the scope of the ingested data (i.e., Toxic Combination, Threat Detection, Cloud Configuration).
The Issue Type drop-down menu is applicable in the Wiz - Issues stream.
[]
Select the issue severity levels to include in the scope of the ingested data (i.e., Critical, High, Medium, Low, Informational).
The Issue Severity drop-down menu is applicable in the Wiz - Issues stream.
[]
Select the status you want to include in the scope of the ingested data (i.e., Open, In Progress, Resolved, Rejected, or All Statuses).
The Issue Status drop-down menu is applicable in the Wiz - Issues stream.
Roles and Permissions
The client ID generated for connecting this source must carry the following permissions:
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
-
| **Stream** | **Permissions** |
| ---------- | --------------- |
| Wiz - Vulnerability Findings | create:reportsupdate:reportsread:reportsread:vulnerabilities |
| Wiz - Issues | create:reportsupdate:reportsread:reportsread:issues |
| Wiz - Configuration Findings | update:reportsread:reportsread:cloud_configuration |
Troubleshooting
Your Wiz - Issues source may return fewer results than expected or miss data due to a 50,000 row limit on full report runs, enforced by Wiz. If your dataset exceeds this threshold, only the first 50,000 rows are included in the export. The remainder is omitted. For larger datasets, use incremental exports, which support up to 500,000 rows to ensure full data coverage.