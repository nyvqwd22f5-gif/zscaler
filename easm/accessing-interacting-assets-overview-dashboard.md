# Accessing & Interacting with the Assets Overview Dashboard
Source: https://help.zscaler.com/easm/accessing-interacting-assets-overview-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1503536.pdf

The Assets Overview dashboard has a collection of interactive widgets that present information on the assets based on various parameters, such as risk level, risk score, trend, distribution across geographic locations, sensitive information exposure via hostnames, distribution of SSL/TLS versions on the assets, etc. using appropriate graphical visualizations. It provides a consolidated view of your organization's exposed assets, highlighting the most vulnerable and risky assets to help you prioritize safeguarding business-critical assets and taking appropriate risk remediation steps. In addition to interacting with the widgets to visualize the data in the desired representation, you can click on individual data points to examine them in depth.
Accessing the Dashboard
To access the Assets Overview dashboard, go to Dashboard > Assets Overview Dashboard in the EASM Admin Portal. The information presented in the Assets Overview dashboard corresponds to your organization selected on the top-right corner. You can use this drop-down menu to select the organization for which you want to view the dashboard. You can also see the timestamp when the current data displayed on the dashboard has been updated.
Interacting with Dashboard Widgets
The Assets Overview dashboard includes the following widgets:
- [Asset Count by Type](#asset-count-by-type)
- [Assets by Risk Level](#assets-by-risk-level)
- [Assets Over Time by Risk Level](#assets-over-time-by-risk-level)
- [Top Locations by Assets](#top-locations-by-assets)
- [Top 5 Assets by Revealing Hostnames](#top5-assets-by-revealing-hostnames)
- [Top 5 Assets by Risk Level](#top5-assets-by-risk-score)
- [Distribution of SSL/TLS Versions](#distribution-of-ssl-tls-versions)
[]This widget provides information about the different classifications of assets used by Zscaler EASM and the asset distribution across the classifications. The following asset classifications are available:
- Domains
- Hosts
- Web Pages
- Certificates
- ASNs
- IP Addresses
- IP Blocks
For each asset type, you can view the number of assets within that type. You can click the count for a specific asset type to get a filtered, tabulated view of the corresponding assets on the [Assets page](/easm/about-asset-inventory), where you can drill down on each asset for detailed information.
[See image.](#asset-count-by-type-image)
[]This widget provides information on how the assets are distributed across different risk levels such as minimal, low, medium, high, and critical. The categorization of assets based on risk levels enables you to efficiently handle risk remediation by prioritizing the assets based on criticality and allocating appropriate resources. It also helps you quickly assess the overall level of risk exposure based on the volume of assets across risk levels. The risk level assigned to an asset is based on the risk score generated for the asset.
[Mapping Between Risk Level and Risk Score](#table-risk-level-score-mapping)
This widget includes a bar chart that plots the number of assets against risk levels. You can hover over each bar to view the number of assets assigned with a specific risk level. Furthermore, you can click each bar to get a filtered, tabulated view of the corresponding assets on the [Assets page](/easm/about-asset-inventory), where you can drill down on each asset for detailed information.
[See image.](#assets-by-risk-level-image)
[]
| Risk Level | Risk Score Range |
| ---------- | ---------------- |
| Minimal | 0 |
| Low | 1–39 |
| Medium | 40–69 |
| High | 70–89 |
| Critical | 90–100 |
[]This widget provides information about the trends of asset exposure over a specific period of time using a line graph that plots the number of assets against specific timelines. You can customize the information shown by this graph using the following options:
- Select the time frame for which the trend is shown using the time filter on the top-right corner of the widget from last 7 days, last 30 days, last 90 days, and last 180 days.
- Select a risk level using the checkbox at the bottom to view the trend of the assets assigned with that specific risk level. You can select multiple risk levels simultaneously to view the corresponding trends together.
When customizing the graph for a time frame greater than the last 7 days, you can view the assets count for specific days by hovering over the line to the specific day.
[See image.](#assets-over-time-by-risk-level-image)
[]This widget provides a worldwide proportional symbols map that plots the geographical regions or countries with the number of exposed assets attributed to your organization. The size of each circle visually represents the number of assets in each region relative to others; larger circles indicate more assets compared to regions represented by smaller circles.
You can view the exact number of assets in a specific region by hovering over or clicking the region or the country on the map. In addition, the list of countries where the assets are located along with the number of assets for each country is shown on the left pane of the widget.
[See image.](#top-locations-by-assets-image)
[]This widget provides the list of top 5 assets with hostnames containing revealing information that might inadvertently benefit attackers by exposing valuable information about your asset infrastructure. For example, hosts with names that are revealing of the asset's functionality or purpose, exposing the network topology, describing the application type, indicating static IP addresses, etc. might all be valuable information to a bad actor potentially looking to exploit an organization's exposed assets.
The data in this widget is presented in a tabular form and the following information is available for each asset:
- **Name**: The name of the asset with potentially revealing information.
- **Impact Level**: The impact level of the information revealed in the hostname, which correlates with potential disclosed functionality of the asset. The top 5 assets are determined based on the highest level of impact and are listed on a decreasing order of magnitude.
You can click an entry to view the asset and its related discoveries on the [Assets page](/easm/about-asset-inventory). For example, if you click a domain named `api.unlockedai.com`, any subdomains identified for the domain would also be listed on the Assets page. Also, if the domain is classified as both a web page and a host, both entries would be listed on the Assets page, and you can drill down on each entry to view detailed information about the asset and the specifics related to the asset type. You can also click **View All Assets** on the top-right corner of the widget to view the complete list of assets on the Assets page.
[See image.](#top5-assets-by-revealing-hostnames-image)
[]This widget provides the list of top 5 assets with the highest risk score. The data is presented in a tabular form and the following information is available for each asset:
- **Name**: The name of the asset.
- **Risk Score**: A risk score computed for the asset based on the findings that are associated with the asset.
You can click an entry to view the asset and its related discoveries on the [Assets page](/easm/about-asset-inventory). For example, if you click a domain named `api.unlockedai.com`, any subdomains identified for the domain would also be listed on the Assets page. Also, if the domain is classified as both a web page and a host, both entries would be listed on the Assets page, and you can drill down on each entry to view detailed information about the asset and the specifics related to the asset type. To view the complete list of all assets, click **View All Assets** on the top-right corner of the widget and this takes you to the Assets page.
[See image.](#top5-assets-by-risk-level-image)
[]This widget provides a donut chart representing the percentage of SSL/TLS versions distributed across the assets discovered.
Connections are only tested for the following SSL/TLS versions:
- **SSL Versions**: 2.0 and 3.0
- **TLS Versions**: 1.0, 1.1, 1.2, and 1.3
You can hover over a specific area to view the number of connections using that specific SSL/TLS version, with the total number of connections shown in the center of the chart.
[See image.](#distribution-of-ssl-tls-image)
[]![A widget providing information about the different classifications of assets in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-asset-count-by-type.gif)
[]![A widget provides information on how the assets are distributed across different risk levels in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-assets-by-risk-level.gif)
[]![A widget providing information about the trends of asset exposure over time in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-assets-over-time-by-risk-level.gif)
[]![A widget showing a map of top locations with assets attributed to your organization in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-top-locations-by-assets.gif)
[]![A widget showing the list of top 5 assets with hostnames containing revealing information in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-top5-assets-by-revealing-hostnames.gif)
[]![A widget providing the top 5 assets with the highest risk score in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-top5-assets-by-risk-level.gif)
[]![A donut chart representing the percentage of SSL/TLS versions distributed across the assets discovered in EASM's Assets Overview dashboard](/downloads/easm/dashboards/accessing-interacting-assets-overview-dashboard/EASM-distribution-of-ssl-tls.gif)