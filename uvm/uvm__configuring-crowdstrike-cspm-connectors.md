# Configuring the CrowdStrike CSPM Connectors
Source: https://help.zscaler.com/uvm/configuring-crowdstrike-cspm-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530835.pdf

CrowdStrike is a cybersecurity platform that communicates and shares information with other security tools and platforms, enhancing threat detection and response capabilities. CrowdStrike cloud security posture management (CSPM) provides visibility into your cloud security and strengthens your compliance posture.
To create the CrowdStrike CSPM data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#crowdstrike-cspm-tiles)
There are two available CrowdStrike CSPM streams. Select those that are in scope based on your CrowdStrike CSPM licenses and use cases:
- Indicators of Misconfiguration (IOM): Flags suspicious or unauthorized usage patterns within monitored systems or networks.
- Indicators of Attack (IOA): Flags potential signs of active threats or malicious activities detected by CrowdStrike.
If you’re looking for CrowdStrike’s Connectors, see [Configuring the CrowdStrike Connectors](/uvm/configuring-crowdstrike-connectors). If you're looking for CrowdStrike's Identity Protection Connectors, see [Configuring the CrowdStrike Identity Protection Connectors](/uvm/configuring-crowdstrike-identity-protection-connectors).
[]
![The CrowdStrike CSPM - IOM and CrowdStrike CSPM - IOA tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-cspm-connectors/crowdstrike-cspm-tiles.png)
Authentication
The source authentication configuration requires the Client ID & Client Secret parameters. The client ID and client secret have the credentials of a user account with the required permissions. To create the API keys, you need to have a Falcon Administrator role.
To generate CrowdStrike client API and secret key:
- Log in to the CrowdStrike console.
- Select the **Menu** icon from the top left navigation.
- Go to **Support and resources** > **API clients and keys**.
- On the **OAuth2 API clients** page, select **Create API client**.
- In the **Create API client** window:
- **Client Name**: Enter a name.
- **Description** field: Enter a description.
-
In the **Scopes** section, select the CSPM Registration **Read** checkbox.
[See image.](#add-new-api-client)
- Click **Create**.
- Save the client ID and client secret securely.
The client secret is unavailable after you close the window.
Retrieval
In the source setup Retrieval section, set the Cloud Provider drop-down menu filters and specifications. Select the cloud provider (i.e., AWS, Azure, or GCP) that you have configured CrowdStrike CSPM to scan and monitor for security posture.
The Cloud Provider drop-down menu is applicable in the following streams:
- CrowdStrike - IOM
- CrowdStrike - IOA
[]
![The Add new API client window in the CrowdStrike platform](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-cspm-connectors/crowdstrike-cspm-create-api-client.png)