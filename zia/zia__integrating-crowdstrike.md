# Integrating with CrowdStrike
Source: https://help.zscaler.com/zia/integrating-crowdstrike
PDF: https://help.zscaler.com/pdf/com/en/1401291.pdf

Zscaler's integration leverages CrowdStrike APIs to provide endpoint detection and response (EDR) visibility for [Sandbox](/zia/about-sandbox)-detected malware. Once the integration is configured, the Zscaler service calls the CrowdStrike Falcon API and requests information for endpoints that have been exposed to the malicious file. CrowdStrike uses the new file signature to detect compromised points throughout your organization's network.
You can view information about the affected endpoints in the [Sandbox logs and reports](/zia/viewing-sandbox-reports-data) of the ZIA Admin Portal. You can also contain endpoints from the ZIA Admin Portal and go to the CrowdStrike portal for further investigation and remediation. These automated workflows reduce the threat dwell time and remediation time.
Prerequisites
Before you begin the CrowdStrike integration, ensure you have:
- CrowdStrike Falcon
- A CrowdStrike admin account with the Falcon Administrator role
- [Zscaler Advanced Sandbox](/zscaler-deployments-operations/advanced-sandbox-deployment-and-operations-guide)
To learn more, refer to the [CrowdStrike documentation](https://www.crowdstrike.com/blog/tech-center/).
[]Step 1: Create an API Client for CrowdStrike
To create an API client for CrowdStrike:
- Log in to the [CrowdStrike portal](https://falcon.crowdstrike.com/login/).
- You must obtain the **Client ID**, **Secret**, and **Customer ID** to complete [Step 2](#step2-zscaler):
- [Obtain the Client ID and Secret](#api-client)
- [Obtain the Customer ID](#customer-ID)
[]Step 2: Set Up Your CrowdStrike Integration with Zscaler
To set up your CrowdStrike integration in the ZIA Admin Portal:
- Log in to the ZIA Admin Portal.
- Go to **Administration **> **Partner Integrations**.
- Click the **CrowdStrike** tab.
- Under **CrowdStrike Authentication Credentials**:
- **API Auth FQDN**: The fully qualified domain name (FQDN) for the CrowdStrike OAuth API. It's typically api.crowdstrike.com. If your organization accesses APIs using a different FQDN, enter it instead.
- **Client ID**: Enter your client ID.
- **Secret**: Enter your client secret.
- **Customer ID**: Enter your customer ID.
Only alphanumeric symbols are accepted for the Customer ID. Remove any dashes from the value you enter.
[See image.](#crowdstrike-configuration)
- Click **Save**.
If your CrowdStrike credentials are valid, the Zscaler service can call the CrowdStrike Falcon APIs and sync your endpoint hits to the Zscaler service. You then can view file and endpoint information in the [CrowdStrike Endpoint Hits report](/zia/viewing-crowdstrike-endpoint-hits-report).
[]To create an API client for CrowdStrike and obtain the client ID and secret:
- In the left-side navigation, go to **Support** > **API Clients and Keys**.
[See image.](#api-clients-keys)
The **API key** page appears.
- In the **API Clients **section, click **Add new API client**.
[See image.](#add-api-client)
The **Add new API client** window appears.
- In the **Add new API client** window:
- **Client Name**: Enter a name for the API client (e.g., Zscaler API).
- **Description**: (Optional) Enter a description for the API client.
- **API Scopes**: Select the following API scopes:
- **Detections** (**Read** only)
- **Hosts** (**Read** and **Write**)
- **IOCs** (**Read** only)
[See image.](#new-api-client)
- Click **Add**.
The **API client created** window appears.
- In the **API client created** window, copy the **Client ID** and **Secret** values.
You must copy the client **Secret** now. You aren't able to retrieve the client secret later. The Zscaler service uses the **Client ID** and **Secret** to authenticate to CrowdStrike. You need this **Secret** to complete the integration in the ZIA Admin Portal for [Step 2](#step2-zscaler).
[See image.](#api-client-created)
- Click **Done**.
[]To obtain the CrowdStrike customer ID:
- In the left-side navigation, click the **Profile** icon.
[See image.](#profile-menu)
The **User Profile** page appears.
- Under **User Details**, copy the **Customer ID**. You need it to complete the integration in the ZIA Admin Portal for [Step 2](#step2-zscaler).
[See Image.](#cutomer-ID)
[]![Screenshot highlighting the API Clients and Keys option in the CrowdStrike Support menu.](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-Support-API-Clients-Keys-Menu.png)
[]![Screenshot highlighting the Add new API client option on the API key page.](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-API-key-Add-new-API-client.png)
[]![Screenshot of the configured Add new API client window in CrowdStrike](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-Add-New-API-Client-window.png)
[]![Screenshot of the Client ID and Secret fields in the CrowdStrike API client created window.](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-API-client-created-window.png)
[]![Screenshot of the Profile menu icon in the CrowdStrike portal](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-User-Profile-Menu.png)
[]![Screenshot highlighting the Customer ID under the CrowdStrike User Details section.](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/CrowdStrike-User-Details-Customer-ID.png)
[]![Screenshot of the completed CrowdStrike partner integration in the ZIA Admin Portal.](/downloads/zia/partner-integrations/configuring-crowdstrike-integration/ZIA-Partner-Integrations-CrowdStrike-Configuration.png)