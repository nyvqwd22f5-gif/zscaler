# Configuring the Tenable Security Center Connectors
Source: https://help.zscaler.com/uvm/configuring-tenable-security-center-connectors
PDF: https://help.zscaler.com/pdf/com/en/1528201.pdf

Tenable Security Center (SC) provides a comprehensive and integrated view of enterprise security posture and allows you to accurately identify, investigate, and prioritize vulnerabilities.
To create the Tenable SC data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#tenable-sc-tiles)
There are two available Tenable SC streams. Select those that are in scope based on your Tenable SC licenses and use cases:
- Vulnerabilities: Retrieves vulnerabilities across the scanned assets broken down by CVE.
- Assets: Retrieves data related to assets scanned by Tenable (e.g., endpoints, servers, network devices, and web app)
If you’re looking for Tenable’s Vulnerability Management, see [Configuring the Tenable Vulnerability Management Connectors](/uvm/configuring-tenable-vulnerability-management-connectors).
[]![Tenable Security Center connector tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/tenable%20security%20center.png)
Authentication
The source authentication configuration requires the following parameters:
- [URL](#param1)
- [Access Key](#param2)
- [Secret Key](#param3)
Retrieval
In the source setup Retrieval section, set the Severity Category drop-down menu filters and specifications. The Severity Category drop-down menu allows the user to select the severity level of vulnerabilities to include in the scope of the ingested data.
The Severity Category drop-down menu is applicable in the Vulnerabilities stream.
[]
The URL is the Tenable SC server URL and is required as part of the authentication.
[]
The access key is an API key associated with a user account with the required permissions.
To enable API key authentication:
- Log in to theTenable.sc platform.
- From the left-side navigation, click **System** > **Configuration**.
- Select the **Security** tile to navigate to the **Security Configuration** page.
- In the **Authentication Settings** section, click **Allow API Keys** to enable the toggle.
- Click **Submit**.
To learn more, refer to the [Tenable documentation](https://docs.tenable.com/security-center/Content/EnableAPIKeys.htm).
[]
After enabling API key authentication, you can generate the API access key and secret key. To generate the keys:
- Log in to the Tenable.sc platform with an organizational user that has the appropriate permissions to generate APIs.
- Go to **Users** > **Users** to view the **Users** page.
- Create a dedicated user for the SecOps platform.
- Select the user for which you want to generate an API key.
- Click **API Keys** > **Generate API Key**.
- Click **Generate**. The **Your API Key** window appears, displaying the Access Key and Secret Key for configuring the connector.
- Save the API keys in a safe location.
You are not able to view API secret keys after the initial generation. If you lose your existing secret key, you must generate new API keys. To learn more, refer to the [Tenable documentation](https://docs.tenable.com/security-center/Content/GenerateAPIKey.htm).