# Configuring the Snyk Connectors
Source: https://help.zscaler.com/uvm/configuring-snyk-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530957.pdf

Snyk is a platform that helps developers find and fix vulnerabilities in open-source libraries and containers integrated into their workflows.
To create the Snyk data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#snyk-tiles)
There are two available Snyk streams. Select those that are in scope based on your Snyk licenses and use cases:
- Static Application Security Testing (SAST): Retrieves potential vulnerabilities discovered by analyzing your source code.
- Snyk: Retrieves SCA (Software Composition Analysis) vulnerabilities discovered in your project dependencies.
[]
![The Snyk - SAST and Snyk tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/snyk-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [API Token](#param1)
- [Org ID](#param2)
[]
The API token used for setting up an API source depends on your Snyk plan. If you are on an Enterprise plan, it is recommended to use a service account to generate the token. When setting up the service account, ensure it has at least a **Group Viewer** role or higher. For more details on service accounts, refer to the [Snyk documentation](https://docs.snyk.io/enterprise-setup/service-accounts).
If you are on a non-Enterprise plan, you can continue using a personal API key. To set up your personal API key:
- Log in to your Snyk account.
- Go to **Account Settings** > **General** > **Auth Token**.
- In the **Key** section, click **click to show** and copy your API token. You can create a new API key by clicking **Revoke & Regenerate**.
[]
To retrieve your organization ID:
- Log in to your Snyk account.
- From the left-side navigation, click **Settings**.
- On the **General** tab, in **Organization ID** section, click **Copy** to copy your organization ID.