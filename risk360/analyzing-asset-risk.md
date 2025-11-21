# Analyzing an Asset Risk
Source: https://help.zscaler.com/risk360/analyzing-asset-risk
PDF: https://help.zscaler.com/pdf/com/en/1486861.pdf

When you click an asset on the [Assets](/risk360/about-asset-level-risk) page, you are redirected to the Asset Details page where you can view the asset's risk score, its risk score trend, location, events that contributed to the risk score change, metadata information, etc. Asset-level risk monitoring is vital in maintaining a healthy risk score and protecting your organization from various security incidents specific to the asset type, location, user, and other parameters that malicious actors can potentially target.
[See image.](#asset-details)
Analyzing an Asset Risk
The Asset Details page (Assets > Click an asset from the Risky Asset Inventory table) consists of the following sections:
Asset Risk Score
This section shows the Zscaler-computed risk score for the asset. The following severities appear for the score ranges:
- Low (1–25)
- Medium (26–50)
- High (51–75)
- Critical (76–100)
[See image.](#asset-score)
Asset Risk Score Trend
The graph shows the Zscaler-computed risk score trend. Hover over a point in the graph to view the risk score for that date.
[See image.](#score-trend)
Asset Details
This section shows the following metadata for the asset:
- **Asset ID**: The unique ID assigned to the asset by the Zscaler service.
- **Username**: The name of the user with whom the asset is associated.
- **Private IP**: The IP address of the asset.
- **Egress IP**: The gateway IP address that sends the local network traffic to other networks on the internet.
- **Location**: The location ID assigned to the asset's workplace. Displays Road Warrior if the asset isn't tied to a location.
- **Department**: The department to which the asset belongs.
- **Asset Type**: The type of asset (iOS, Android OS, etc.).
- **Last Seen**: The time and date when the last activity was observed on the asset.
- **Authentication Status**: Indicates whether the asset is authenticated or not.
- **Enrolled Device Type Version**: The [Zscaler Client Connector version](/zscaler-client-connector/viewing-information-about-zscaler-client-connector#app-version) installed on the asset.
- **Device Hostname**: The unique ID assigned to the asset to identify it on the internet.
- **OS Type**: The asset's operating system.
- **OS Version**: The operating system version information.
[See image.](#details)
Asset Location
This section shows where the asset is located on the map. Hover over the asset to view the city and country information.
[See image.](#location)
Events Contributing to Risk Score for Last 7 Days
This section lists the top events observed within the last 7 days that have contributed to the risk score change of the asset. These events are listed in ascending order with the timestamp. For each event, you can view the:
- Threat Category
- Threat Name
- URL Category
- URL Name
You can click the **Export **icon (![Risk360-Export-Icon.png](/downloads/tech-pubs-drafts/risk360-draft-articles/analyzing-asset-risk/Risk360-Export-Icon.png)
) to download the risky events to a CSV file and click **View All Events** to view all the risky events in a drawer.
[See image.](#contributing-events)
[]![Asset Details Page](/downloads/risk360/dashboard-analytics/analyzing-asset-risk/Risk360-Asset-Details-Page_0.png)
[]![Asset Risk Score](/downloads/risk360/dashboard-analytics/about-asset-level-risk/Risk360-Asset-Details-Page-Risk-Score.png)
[]![Asset Risk Score Trend](/downloads/risk360/dashboard-analytics/about-asset-level-risk/Risk360-Asset-Details-Page-Risk-Score-Trend.png)
[]![Asset Details](/downloads/risk360/dashboard-analytics/about-asset-level-risk/Risk360-Asset-Details-Page-Detail.png)
[]![Asset Location](/downloads/risk360/dashboard-analytics/about-asset-level-risk/Risk360-Asset-Details-Page-Location.png)
[]![Events Contributing to Risk for Last 7 Days Section](/downloads/risk360/dashboard-analytics/analyzing-asset-risk/Risk360-Asset-Details-Page-Events_0.png)