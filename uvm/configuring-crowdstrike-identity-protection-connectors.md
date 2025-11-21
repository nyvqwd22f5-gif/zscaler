# Configuring the CrowdStrike Identity Protection Connectors
Source: https://help.zscaler.com/uvm/configuring-crowdstrike-identity-protection-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530837.pdf

CrowdStrike is a cybersecurity platform that communicates and shares information with other security tools and platforms, enhancing threat detection and response capabilities. CrowdStrike Identity Protection provides identity threat detection and response (ITDR) and endpoint security.
To create the CrowdStrike Identity Protection data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#crowdstrike-identity-protection-tiles)
There are two available CrowdStrike Identity Protection streams. Select those that are in scope based on your CrowdStrike Identity Protection licenses and use cases:
- Security Assessment: Retrieves security risk details, including factors, likelihood, severity, recommendations, and overall assessment scores for risk evaluation.
- Domain Users: Retrieves user data, including display names, risk scores, admin status, and archival status for identity protection insights.
If you’re looking for CrowdStrike’s Connectors, see [Configuring the CrowdStrike Connectors](/uvm/configuring-crowdstrike-connectors). If you’re looking for CrowdStrike’s CSPM, see [Configuring the CrowdStrike CSPM Connectors](/uvm/configuring-crowdstrike-cspm-connectors).
[]
![The CrowdStrike Identity Protection - Security Assessment and CrowdStrike Identity Protection - Domain Users tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-identity-protection-connectors/crowdstrike-identity-protection-tiles.png)
Authentication
The source authentication configuration requires the Client ID & Client Secret parameters. The client ID and client secret have the credentials of a user account with the required permissions. To create the API keys, you need to have a Falcon Administrator role.
To generate CrowdStrike client API and secret key:
- Log in to the CrowdStrike console.
- Go to **Menu** > **Support and Resources** > **API clients and keys**
- On the **API clients and keys** page, on the **OAuth2 API clients** tab, select **Create API client**.
- In the **Create API client** window:
- **Client Name**: Enter a name.
- **Description**: Enter a description.
-
In the **Scope** section, set the following permissions:
- For **Identity Protection Assessment**, select the **Read** checkbox.
- For **Identity Protection GraphQL**, select the **Write** checkbox.
- For **Identity Protection Entities**, select the **Read** checkbox. This is for domain users.
[See image.](#create-api-client)
- Click **Create**.
Save the client ID and client secret securely. The client secret is unavailable after you close the window.
Retrieval
In the source setup Retrieval section, set the Fetch Only Active Directory Domains checkbox filters and specifications.
The Fetch Only Active Directory Domains checkbox is applicable in the CrowdStrike Identity Protection - Security Assessment stream.
[]
![The Create API client window accessed from the API clients and keys page in the CrowdStrike console](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-identity-protection-connectors/crowdstrike-identity-protection-create-api-client.png)