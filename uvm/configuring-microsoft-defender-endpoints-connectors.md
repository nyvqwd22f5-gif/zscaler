# Configuring the Microsoft Defender for Endpoints Connectors
Source: https://help.zscaler.com/uvm/configuring-microsoft-defender-endpoints-connectors
PDF: https://help.zscaler.com/pdf/com/en/1530975.pdf

Microsoft Defender for Endpoint is an enterprise-grade endpoint security platform that helps detect, prevent, investigate, and respond to advanced cyber threats. It provides integrated threat protection across devices using behavioral monitoring, automated analysis, and real-time security insights.
To create the Microsoft Defender for Endpoints data source, go to **Configure** > **Sources**. The connector tile appears among the other available data sources. To learn more, see [Creating Data Sources](/uvm/creating-data-sources).
[See image.](#microsoft-defender-endpoints-tiles)
There are five available Microsoft Defender for Endpoints streams. Select those that are in scope based on your Microsoft Defender for Endpoints licenses and use cases:
- Assets: Retrieves device information, which includes device details such as ID and owner, operating system, and network information.
- Vulnerabilities: Retrieves a list of all the vulnerabilities affecting the organization per machine and software.
- Software Vulnerabilities by Machine: Retrieves detailed software vulnerabilities for individual machines, across all platforms and environments.
- Alerts: Retrieves security alerts, which includes details about the alert, impacted resources, severity, detection source, recommendations, and timestamps for incidents or vulnerabilities.
- Incidents: Retrieves security incidents, which includes incident details, affected resources, severity, status, related alerts, and timelines.
These connectors retrieve endpoint data only.
If you’re looking for Microsoft’s Defender for Cloud, see [Configuring the Microsoft Defender for Cloud Connectors](/uvm/configuring-microsoft-defender-cloud-connectors).
[]
![The Microsoft Defender for Endpoints tiles](/downloads/uvm/administration/connectors/sources/source-configuration-guides/configuring-microsoft-defender-endpoints-connectors/microsoft-defender-endpoints-tiles.png)
Authentication
The source authentication configuration requires the following parameters:
- [Application (client) ID and Directory (tenant) ID](#param1)
- [Client Secret](#param2)
- [URL](#param3)
[]
In the Microsoft Azure portal, complete the app registration process. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp?view=o365-worldwide). After completion, the app **Overview** section is automatically opened. In this section, copy the **Application (client) ID** and **Directory (tenant) ID**.
[]
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/) field**, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registration** page, select your app registration.
- From the left-side navigation, from the **Manage** drop-down menu, select **Certificates & secrets**.
- On the **Certificates & secrets** tab, click **New client secret**.
- Enter a description and an expiration date for the secret.
- Click **Add**.
- Copy the **Client Secret Value**.
Save the client secret securely, as it is not available after leaving the process.
[]
The most commonly used resource URI is `https://api.securitycenter.microsoft.com/`. For better performance, you can select a server based on your geo-location:
- US: `https://api-us.securitycenter.microsoft.com/`
- EU: `https://api-eu.securitycenter.microsoft.com/`
- UK: `https://api-uk.securitycenter.microsoft.com/`
- AU: `https://api-au.securitycenter.microsoft.com/`
Retrieval
In the source setup Retrieval section, set the following filters and specifications:
- [Severity field](#severity)
- [Ignore Resolved Incidents checkbox](#incidents)
[]
You can optionally filter the ingested data by severity category.
The Severity field is applicable in the Microsoft Defender for Endpoints - Vulnerabilities stream.
[]
You can optionally filter out resolved incidents.
The Ignore Resolved Incidents checkbox is applicable in the Microsoft Defender for Endpoints - Incidents stream.
Roles and Permissions
To assign the app permissions, on the API permission tab of the app registration process, select the appropriate permissions for the Azure Defender stream you want to set up:
- Log in to the Microsoft Azure portal.
- On the home page, in the **Search resources, services, and docs (G+/) field**, enter `App registrations`. From the drop-down menu, select **App registrations**.
- On the **App registration** page, select your app registration.
- From the left-side navigation, from the Manage drop-down menu, select **API permissions**.
- On the **API permissions** page, select **Add a permission**.
- In the panel, select the **APIs my organization uses** tab.
- Depending on the stream you are connecting to, search for the following relevant API:
- Incidents stream: Select the Microsoft Threat Protection API.
- For all other streams (i.e., Vulnerabilities, Alerts, Assets, or Software Vulnerabilities by Machine): Select the WindowsDefenderATP API.
- Select either **Application** or **Delegated**. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/entra/identity-platform/permissions-consent-overview).
- Add the permissions per stream:
- [Assets](#perm1)
- [Vulnerabilities](#perm2)
- [Software Vulnerabilities by Machine](#perm3)
- [Alerts](#perm4)
- [Incidents](#perm5)
- Click **Grant consent** for each permission you add.
[]
Select the WindowsDefenderATP API and add the following permissions:
| **Permission Type** | **Permission** | **Permission Display Name** |
| ------------------- | -------------- | --------------------------- |
| Application | Machine.Read.All | 'Read all machine profiles' |
[]
Select the WindowsDefenderATP API and add the following permissions:
| **Permission Type** | **Permission** | **Permission Display Name** |
| ------------------- | -------------- | --------------------------- |
| Application | Machine.Read.All | 'Read all machine profiles' |
| Application | Vulnerability.Read.All | 'Read Threat and Vulnerability Management vulnerability information' |
| Delegated (work or school account) | Vulnerability.Read | 'Read Threat and Vulnerability Management vulnerability information' |
| Application | SecurityRecommendation.Read.All | 'Read Threat and Vulnerability Management security recommendation information' |
| Delegated (work or school account) | SecurityRecommendation.Read | 'Read Threat and Vulnerability Management security recommendation information' |
[]
Select the WindowsDefenderATP API and add the following permissions:
| **Permission Type** | **Permission** | **Permission Display Name** |
| ------------------- | -------------- | --------------------------- |
| Application | Machine.Read.All | 'Read all machine profiles' |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated (work or school account) | Machine.Read | 'Read machine information' |
| Delegated (work or school account) | Machine.ReadWrite | 'Read and write machine information' |
[]
Select the WindowsDefenderATP API and add the following permissions:
| **Permission Type** | **Permission** | **Permission Display Name** |
| ------------------- | -------------- | --------------------------- |
| Application | Alert.Read.All | 'Read all alerts’ |
| Application | Alert.ReadWrite.All | 'Read and write all alerts’ |
| Delegated (work or school account) | Alert.Read | 'Read alerts’ |
| Delegated (work or school account) | Alert.ReadWrite | 'Read and write alerts’ |
[]
Select the Microsoft Threat Protection API and add the following permissions:
| **Permission Type** | **Permission** | **Permission Display Name** |
| ------------------- | -------------- | --------------------------- |
| Application | Incidents.Read.All | 'Read all incidents' |
| Application | Incident.ReadWrite.All | 'Read and write all incidents' |
| Delegated (work or school account) | Incident.Read | 'Read incidents' |
| Delegated (work or school account) | Incident.ReadWrite | 'Read and write incidents' |