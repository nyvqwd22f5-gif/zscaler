# Integrating Applications with Zscaler Breach Predictor
Source: https://help.zscaler.com/breach-predictor/integrating-applications-zscaler-breach-predictor
PDF: https://help.zscaler.com/pdf/com/en/1518496.pdf

Breach Predictor uses integrations with various applications to provide added functionality and visibility. To integrate an application with Breach Predictor:
- [Access the Breach Predictor Portal](/breach-predictor/accessing-and-navigating-zscaler-breach-predictor#signing-in-breach-predictor).
- Go to **Profile** > **Integration**.
- Select an integration type:
- [SIEM Integrations](#siem-integration)
- [Ticketing Integrations](#ticketing-integration)
- [Zscaler Integrations](#zscaler-integration)
- Click **Connect**.
[]You can send event data from Breach Predictor to security information and event management (SIEM) applications (e.g., CrowdStrike Next-Gen SIEM and Splunk) to remediate threats. Because Breach Predictor ingests and analyzes vast amounts of Zscaler and third-party data, sending event data from Breach Predictor to your SIEM application lets you take direct action on threats with a holistic view of your organization's threat landscape.
You can share Breach Predictor data with the following SIEM applications:
- [CrowdStrike Next-Gen SIEM](#crowdstrike-integration)
- [Splunk](#splunk-integration)
With the integration configured, every new event that occurs on the tenant is sent automatically to your SIEM application.
[]
- [Jira](#jira-integration)
- [ServiceNow](#servicenow-integration)
[]
- [Sandbox](#sandbox-integration)
[]Upon successful integration, Breach Predictor sends all available event data to your SIEM provider. Because the default data-retention period for CrowdStrike Next-Gen SIEM ranges from 7 to 14 days, any event data sent from Breach Predictor that is outside of the retention period will not be available in CrowdStrike Next-Gen SIEM. To increase the data-retention period, you must contact your CrowdStrike account team.
To integrate Breach Predictor with CrowdStrike Next-Gen SIEM, you need to create a connector with a JSON parser that allows Breach Predictor to share event data:
- Log in to CrowdStrike Falcon using your admin credentials.
- In the left-side navigation, go to **Next-Gen SIEM** > **Data onboarding**.
[See image.](#crowdstrike-next-gen-nav)
The **Connections** page opens.
- On the **Connections** page, click **Add connection**.
[See image.](#crowdstrike-add-connection)
The **Data connectors** window opens.
- In the **Data connectors** window, click **Configure**.
[See image.](#crowdstrike-configure-connection)
- Configure the connection settings as needed, ensuring that you select **json (Generic Source)** as the **Parser** type, then click **Create connection**.
The **Connections** page opens and the new connection appears in the list.
- Locate the new connection in the list and open the **Actions** menu in the **Actions** column.
- Select **Generate API key** from the list.
[See image.](#crowdstrike-generate-api-key)
The **Connection setup** window opens.
- In the **Connection setup** window, copy the **API key** and **API URL** values separately and save them for later use.
[See image.](#crowdstrike-connection-setup-window)
- In the Breach Predictor Portal, click **Profile** > **Integration**.
The **Integration** page opens.
- On the tile for CrowdStrike Next-Gen, click **Connect**.
The **Integrate CrowdStrike Next-Gen** window opens.
- In the **Integrate CrowdStrike Next-Gen** window:
- **URL**: Enter the **API URL** value you copied earlier.
- **Token**: Enter the **API key** value you copied earlier.
[]![Selecting the Data Onboarding Option in CrowdStrike Falcon](/downloads/breach-predictor/25.06/ZBP-CrowdStrike-Falcon-Next-Gen-Data-Onboarding.png)
[]![Selecting the Add Connection Option in CrowdStrike Falcon](/downloads/breach-predictor/25.06/ZBP-CrowdStrike-Falcon-Next-Gen-Add-Connection.png)
[]![Selecting the Configure Option for a New Connector in CrowdStrike Falcon](/downloads/breach-predictor/25.06/ZBP-CrowdStrike-Falcon-Next-Gen-Configure-Connection.png)
[]![Selecting the Generate API Key Option in CrowdStrike Falcon](/downloads/breach-predictor/25.06/ZBP-CrowdStrike-Falcon-Next-Gen-Generate-API-Key.png)
[]![Copying the API Key and API URL on the Connection Setup in CrowdStrike Falcon](/downloads/breach-predictor/25.06/ZBP-CrowdStrike-Falcon-Next-Gen-Connection-Setup.png)
[]To integrate Breach Predictor with Splunk, you need to create a custom index and an HTTP Event Collector (HEC) token to allow Breach Predictor to share event data. Creating a custom index to hold Breach Predictor data is a best practice that allows for better search results and more efficient data retrieval. If you don't create and specify an index, Splunk will use a pre-existing index to hold Breach Predictor data.
To integrate Breach Predictor with Splunk:
- Log in to your Splunk Enterprise tenant as an administrator.
- Click **Settings** > **Indexes**.
[See image.](#splunk-settings-indexes)
The **Indexes** page opens.
- On the **Indexes** page, click **New Index**.
The **New Index** window opens.
- In the **New Index** window:
- **Index Name**: Specify a unique name for the index (i.e., `breachpredictorevents`).
- **Index Data Type**: Select **Events**.
- Configure other settings as needed. To learn more, refer to the [Splunk documentation](https://docs.splunk.com/Documentation/Splunk/9.4.2/Indexer/Setupmultipleindexes#Create_events_indexes_2).
- Click **Save**.
[See image.](#splunk-new-index-window)
- Click **Settings** > **Data Inputs** > **HTTP Event Collector**.
The **HTTP Event Collector** page opens.
- On the **HTTP Event Collector** page, click **New Token**.
The **Add Data** page opens.
- On the **Add Data** > **Select Source** page, specify a unique name for the token, as well as other settings as needed, then click **Next**.
- On the **Add Data** > **Input Settings** page, select the index you created earlier, then click **Review**.
- On the **Add Data** > **Review** page, review the settings for the token and then click **Submit**.
The **New Search** page opens with the information for the token.
- Click **Settings** > **Data Inputs** > **HTTP Event Collector**.
The **HTTP Event Collector** page opens.
- In the **Token Value** column, click **Copy** for the HEC you created. Save this value for later use in the Breach Predictor Portal.
- In the Breach Predictor Portal, click **Profile** > **Integration**.
The **Integration** page opens.
- On the tile for Splunk, click **Connect**.
[See image.](#splunk-integration-tile)
The **Integrate Splunk** window opens.
- In the **Integrate Splunk** window:
- **URL**: Enter the URL for your Splunk tenant. Because Breach Predictor shares event data in JSON format, you must append an endpoint parameter to the URL so that Splunk can properly receive JSON-formatted events (e.g., `/services/collector/event`). To learn more, refer to the [Splunk documentation](https://docs.splunk.com/Documentation/Splunk/9.4.2/Data/UsetheHTTPEventCollector#Send_data_to_HTTP_Event_Collector_on_Splunk_Cloud_Platform).
- **Token**: Enter the token value for the HEC that you copied earlier.
- **Index**: Enter the unique name of the index you created earlier.
[]![Selecting the Indexes Option in Splunk Web](/downloads/breach-predictor/25.06/ZBP-Splunk-Indexes-Option.png)
[]![Selecting the Connect Option on the Splunk Integration Tile in Breach Predictor](/downloads/breach-predictor/25.06/ZBP-Splunk-Integration-Tile.png)
[]![Configuring a New Index in Splunk Web](/downloads/breach-predictor/25.06/ZBP-Splunk-New-Indexes-Window.png)
[]
- On the **Jira** tile, click **Connect**.
The **Integrate Jira** window appears.
-
In the **Integrate Jira** window:
- **Domain Key**: Enter the Jira domain assigned to your organization.
- **Token Key**: Enter the Jira token that allows Breach Predictor to access the Jira domain assigned to your organization.
[See image.](#integrate-jira-window)
To receive the **Domain Key** and **Token Key** for your organization, contact your Zscaler Account team.
[]![The Integrate Jira Window in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-IntegratingApps_IntegrateJira.png)
[]
- On the **Sandbox** tile, click **Connect**.
The **Integrate Sandbox** window appears.
- In the **Integrate Sandbox** window, enter the **Secret Key**. This token allows Breach Predictor to access the Zscaler Sandbox tenant assigned to your organization.
[See image.](#integrate-sandbox-window)
To receive the **Secret Key** for your organization, contact your Zscaler Account team.
[]![The Integrate Sandbox Window in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-IntegratingApps_IntegrateSandbox.png)
[]
- On the **ServiceNow** tile, click **Connect**.
The **Integrate ServiceNow** window appears.
-
In the **Integrate ServiceNow** window:
- **Domain Key**: Enter the ServiceNow domain assigned to your organization.
- **Token Key**: Enter the ServiceNow token that allows Breach Predictor to access the ServiceNow domain assigned to your organization.
[See image.](#integrate-servicenow-window)
To receive the **Domain Key** and **Token Key** for your organization, contact your Zscaler Account team.
[]![The Integrate ServiceNow Window in Zscaler Breach Predictor](/downloads/breach-predictor/25.01/ZBP-IntegratingApps_IntegrateServiceNow.png)