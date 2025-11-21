# Configuring the CrowdStrike Connectors
Source: https://help.zscaler.com/uvm/configuring-crowdstrike-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530822.pdf

CrowdStrike is a cybersecurity platform that communicates and shares information with other security tools and platforms, enhancing threat detection and response capabilities.
To create the CrowdStrike data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#crowdstrike-tiles)
There are five available CrowdStrike streams. Select those that are in scope based on your CrowdStrike licenses and use cases:
- Vulnerabilities: Retrieves vulnerabilities, which includes IDs, severity levels, affected systems, and descriptions to facilitate risk assessment across the environment.
- Managed Hosts: Retrieves devices managed by CrowdStrike (i.e., endpoints running the Falcon sensor).
- Environmental Assets: Retrieves assets in your environment, which includes those unsupported and unmanaged by CrowdStrike.
- Incidents: Retrieves security incidents, which includes incident IDs, timestamps, status, severity, descriptions, affected resources, and other details related to the incident's lifecycle and context.
- Alerts: Retrieves security alerts, which includes activity IDs, timestamps, alert descriptions, affected resources, source account information, location, and severity.
Incidents and Alerts data is used to enrich Vulnerabilities and Assets data.
If you’re looking for CrowdStrike’s CSPM connectors, see [Configuring the CrowdStrike CSPM Connectors](/uvm/configuring-crowdstrike-cspm-connectors). If you’re looking for CrowdStrike’s Identity Protection connectors, see [Configuring the CrowdStrike Identity Protection Connectors](/uvm/configuring-crowdstrike-identity-protection-connectors).
[]
![The CrowdStrike - Incidents, CrowdStrike - Managed Hosts, CrowdStrike - Environment Assets, CrowdStrike Vulnerabilities, and CrowdStrike Alerts tiles](/downloads/tech-pubs-drafts/uvm-secops-draft-articles/connector-drafts/configuring-source-name-connector/crowdstrike-tiles.png)
Authentication
The source authentication configuration requires the Client ID & Client Secret parameter.
To create the API keys, you need to have a Falcon Administrator role.
To generate the Client ID and Client Secret:
- Log in to the CrowdStrike console.
-
Select the **Menu** icon from the top left navigation.
[See image.](#menu)
-
Go to **Support and resources** > **API clients and keys**.
[See image.](#api-clients-keys)
-
On the **OAuth2 API clients** page, select **Create API client**.
[See image.](#create-api-client)
- In the **Create API client** window:
- **Client name**: Enter a name.
- **Description**: Enter a description.
-
**Scope**: Select the relevant permissions for the source:
- Vulnerabilities: Select the Spotlight Vulnerabilities: read permission checkbox.
- Managed Hosts: Select the Hosts: read permission. To retrieve IoT assets in addition to hosts, select the Discover: read permission. If you cannot find the Discover: read permission, you might not have IoT assets to retrieve. If so, remove IoTs from the selected Asset Types on the source setup page.
- Environment Assets: Select the Assets: read permission.
- Incidents: Select the Detects: read, Incidents: read, and Hosts: read permissions.
- Alerts: Select the Alerts: read permission.
[See image.](#create-api-client-details)
- Click **Add**.
- Save the Client ID and Client Secret securely.
The Client Secret is not available after you close the window.
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Assets Types drop-down menu](#assets-types)
- [(Optional) CrowdStrike cloud region drop-down menu](#crowdstrike-cloud-region)
- [Number of days to fetch field](#number-of-days-to-fetch)
- [Product drop-down menu](#product)
- [(Optional) Split Finding by Apps checkbox](#split-finding-by-apps)
- [CVE Severity drop-down menu](#cve-severity)
- [(Optional) Fetch vulnerabilities from the past selected days field](#fetch-vulnerabilities-from-the-past-selected-days)
[]
- Hosts: A traditional computing device (e.g., desktop computer, laptop, or server).
- IoT: Internet-connected devices that are not traditional computers (e.g., cameras or printers).
By default, both Hosts and IoT devices are retrieved. If you only have Hosts, select Hosts to filter the results.
The Assets Types drop-down menu is applicable in the CrowdStrike - Managed Hosts stream.
[]
The CrowdStrike cloud region drop-down menu allows you to specify your CrowdStrike cloud region and corresponding base URL. The available CrowdStrike cloud regions and their corresponding base URLs are listed in the following table. This field is optional, and if left unselected, the default region is US1, `https://api.crowdstrike.com`, which also supports the US2 and EU1 regions.
| **Region** | **Base URL** |
| ---------- | ------------ |
| US1 | `https://api.crowdstrike.com` |
| US2 | `https://api.us-2.crowdstrike.com` |
| EU1 | `https://api.eu-1.crowdstrike.com` |
| USGOV1 | `https://api.laggar.gcw.crowdstrike.com` |
| USGOV2 | `https://api.us-gov-2.crowdstrike.mil` |
The CrowdStrike cloud region drop-down menu is applicable in the CrowdStrike - Managed Hosts stream.
[]
The Number of days to fetch field allows you to choose the number of days you want to retrieve on each run.
The Number of days to fetch field is applicable in the following streams:
- CrowdStrike - Incidents
- CrowdStrike - Alerts
[]
EPP, IDP, Mobile, XDR, Overwatch, CWPP (default - all products)
The Product drop-down menu is applicable in the CrowdStrike - Alerts stream.
[]
The Split Finding by Apps checkbox allows you to separate records containing more than one app into individual entries.
The Split Finding by Apps checkbox is applicable in the CrowdStrike - Vulnerabilities stream.
[]
The CVE Severity drop-down menu allows you to select the severity level of vulnerabilities to include in the scope of the ingested data.
The CVE Severity drop-down menu is applicable in the CrowdStrike - Vulnerabilities stream.
[]
The Fetch vulnerabilities from the past selected days field allows you to adjust the number of days for which you want to retrieve vulnerabilities on each run.
The Fetch vulnerabilities from the past selected days field is applicable in the CrowdStrike - Vulnerabilities stream.
Troubleshooting and FAQs
| **Question** | **Answer** |
| ------------ | ---------- |
| Why can I not see all the scopes outlined in the cloud region table when creating the API keys? | You might not have access to the relevant CrowdStrike module. The available scopes are determined by the products your organization is subscribed to and the cloud region where your account is hosted. Only scopes corresponding to your subscribed products and cloud region are visible.This discrepancy suggests that the connector you are attempting to set up may not be compatible with your current CrowdStrike license configuration. |
[]
![The Open menu icon in the CrowdStrike console](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-connectors/crowdstrike-menu.png)
[]
![Selecting API clients and key from Support and resources in the CrowdStrike console](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-connectors/crowdstrike-support-resources-api-clients-keys.png)
[]
![Selecting Create API client on the OAuth2 API clients page from the Support and resources page of the CrowdStrike console](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-connectors/crowdstrike-create-api-client.png)
[]
![The Create API client window in the CrowdStrike console](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-crowdstrike-connectors/crowdstrike-create-api-client-details.png)