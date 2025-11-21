# Monitoring the Network Intelligence Dashboard
Source: https://help.zscaler.com/zdx/monitoring-network-intelligence-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1529289.pdf

Network Intelligence provides end-to-end multi-path network visibility from Last Mile Internet Service Providers (ISPs) to Zero Trust Exchange to applications. ZDX runs Cloud Path probes to gather network metrics (e.g., network latency, packet loss) to establish a baseline for network latency and compares the network performance against the baseline. ZDX detects and analyzes network anomalies to create a deep analysis and allows you to investigate root causes. You can analyze and pinpoint Last Mile or Intermediate ISP issues, understand root causes, and assess their impact on end users using ML-based algorithms to extract patterns and identify anomalies, and then you can observe and determine the most optimal routing paths to data centers. With all this knowledge at your disposal, you can take proactive measures to resolve network issues to improve the overall organization's digital experience.
Prerequisites
To access the Network Intelligence Dashboard, you must have the following:
- Your ZDX subscription level supports Network Intelligence. To learn more, see [Ranges and Limitations](/zdx/ranges-limitations).
- View Only permission for the Network Intelligence Dashboard. To learn more, see [Adding ZDX Roles](/zdx/adding-zdx-roles).
Overview of Network Health
The Network Intelligence dashboard opens with a high-level overview of network health. This section displays recent network anomalies for the last 14 days, cities with the highest user count, and top Autonomous System Numbers (ASNs) showing elevated latency. Together, these widgets summarize where and how network performance is impacted across your organization.
- **Network Anomalies for Last 14 Days**: Displays total anomalies per 24-hour period, highlighting severe and medium issues across geolocations with more than 50 users. Selecting a bar adjusts the dashboard’s time range to that day.
- **Top 5 Cities by User Count**: Lists the cities with the highest user counts and corresponding anomaly levels. Clicking a city highlights it across other charts and widgets but does not set a global filter.
- **Top 5 High-Latency ASNs**: Shows the ASNs with the highest measured latency compared to a baseline. Taller red bars indicate above-baseline latency, while thinner marks show near-baseline performance.
[See image.](#img_top_summary)
[]
![Top Summary widgets showing 14-day anomalies, top cities, and high-latency ASNs](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/networkintelligencetopsummarywidget.png)
Interactions in these widgets do not apply global filters. Use the map or filter bar to adjust the dashboard scope.
Adjusting Network Intelligence View
To adjust your Network Intelligence Dashboard view, you can:
-
Filter by **Zero Trust Exchange**, **Application**, **Zscaler Locations**, or **Geolocations**.
When you select the **Application** filter, the map displays all geolocations where users are accessing the selected application and does not contain flickering anomalies. Instead, anomalies are detected at runtime and you must select a geolocation on the map to populate the anomaly data.
- Select a time range (**2 Hours**, **4 Hours**, **6 Hours**, **12 Hours**, **24 Hours**, **48 Hours**, **Current**, **Custom**).
You can view the total of each impacted geolocation when the network latency deviates from the baseline and is considered an anomaly.
On the map, you can:
- View highlighted geolocations with a rippling effect which indicate a network latency deviation from the performance baseline. Each geolocation is categorized into green, orange, or red. Click a flickering anomaly location on the map to zoom in to the location.
- Use the left-side panel to navigate anomalies by region. It lists** Continents**, then **Countries**, then **Cities**, each sorted by anomaly count for faster navigation. Click a continent to expand its countries; click a country to expand its cities. Selecting any item filters the map to that scope.
- Pan around, zoom in, or zoom out to adjust the view. Click **Reset** to revert to the default world map view.
[See image.](#img_NI_Map)
[]
![Top Summary widgets showing 14-day anomalies, top cities, and high-latency ASNs](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/network-intelligence-map-view.png)
A rippling effect appears on the map for geolocations with more than 50 users. For geolocations with fewer than 50 users, anomalies are detected at runtime and do not have the rippling effect.
Viewing Network Anomalies
After selecting a network anomaly geolocation from the drill-down view, you can view:
- [User Experience & Network Insights](#chart_overtime)
- [ISP or ASN View](#view_asnorisp)
- [Performance Tables](#tables_performance)
If you do not select a network anomaly geolocation from the drill-down view, the network data is not populated.
[]User Experience & Network Insights
The User Experience & Network Insights chart provides a graphical representation of when anomalies occur, probe count, packet loss, the network latency, and the number of users with a poor ZDX Score. The network latency and ZDX Score are used to indicate how users are impacted over time when the network latency is high.
A drop-down menu on the chart allows you to select the metric displayed in the chart. Available metrics include the following:
- **Network Latency:** Displays the latency over time on the selected network.
- **Users with Poor ZDX Score:** Shows the number of users experiencing a poor ZDX Score over time.
- **Probe Count:** Displays the number of network probes available during the selected time frame.
- **Packet Loss (P95):** Displays the 95th-percentile value of packet loss over time.
The chart updates dynamically based on your selection.
You can drag and drop the time range slicer to view a selected time range of up to 4 hours. You can also expand or condense the selected time range to focus only on the time range. Other Network Intelligence data is updated based on the selection. The red shade indicates a high number of anomalies while a gray-shaded region indicates users have a poor ZDX Score and are experiencing a poor digital experience.
![Drag and drop the time range slicer](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-time-range-slicer-1_0.png)
If there is a network anomaly (red shade) and no users with poor ZDX Score (gray shade), then the network anomaly is not impacting the users' digital experience. For example, if the network latency goes from 10 to 40 ms, then this is considered an anomaly since it is 3 times the baseline of 10 ms. However, a network latency of 40 ms does not normally impact the users' digital experience.
[]ISP or ASN View
The ISP or ASN View displays a Sankey visualization for the aggregation of all the IP addresses that belong to the same ASN. After you click an ASN node, you can see all the IP addresses connected to the ISP over the internet, and then you can determine if there is a network problem.
You can switch between the following ISP or ASN view:
-
**Client to Application**: View the pathways from the client's ISP to the application.
[See image.](#img_asnipview-client-app)
- **Client to Zero Trust Exchange**: View pathways from the client's ISP to the Zero Trust Exchange.
-
**Forward Path**: View the paths from the ISP to the Zero Trust Exchange data center.
[See image.](#img_asnipview-client-zte-forward)
-
**Reverse Path**: View the reverse underlay path from Zero Trust Exchange to the Last Mile ISP.
[See image.](#img_asnipview-client-zte-reverse)
-
**Zero Trust Exchange to Application**: View the pathways from the Zero Trust Exchange to the application. You can switch between path views:
[See image.](#img_asnipview-zte-app)
-
**Client Application (Direct)**: View the path to the application.
[See image.](#img_asnipview-client-app-direct)
Applications with a poor ZDX Score are outlined with a dotted red highlight to indicate potential application-side impact.
When the line connections on the Sankey visualization are highlighted:
- **Yellow**: The IP addresses are impacted by at least 2 times the baseline with a minimum latency threshold of 25 ms and considered a medium severity.
- **Red**: The IP addresses are impacted by at least 3 times the baseline with a minimum latency threshold of 50 ms and considered a high severity.
If a baseline is not established, then the baseline uses the values of 50 ms (red) and 25 ms (yellow). If the IP addresses experience a latency threshold between 25 ms and 50 ms, then it is a medium (yellow) severity. If the IP addresses experience a latency threshold of more than 50 ms, then it is considered high (red) severity.
ASN Details
- **Intra ASN**: Refers to metrics within the same Autonomous System Number (ASN).
- **Inter ASN**: Refers to metrics between two Autonomous System Numbers (ASNs).
- **P50 Latency**: The 50th percentile latency for probes traversing this link during the selected time window. Half of the probes have latency at or below this value; half are higher.
- **Severity**: Indicates the level of latency severity based on the P50 Latency deviation from the baseline:
- **High**: P50 ≥ 3× baseline
- **Medium**: P50 ≥ 2× and < 3× baseline
- **Low**: P50 < 2× baseline
- **Probe Count**: The total number of measurement probes sent to and from this ASN during the selected time interval.
- **Number of Users**: The count of unique end-users whose traffic passed through this ASN during the selected time window.
- **Average Latency**: The average latency of probes between ASNs or within the same ASN during the selected time interval.
- **P90 Latency**: The 90th percentile latency. 90% of probes have latency at or below this value; 10% are higher.
- **P95 Latency**: The 95th percentile latency. 95% of probes have latency at or below this value; 5% are higher.
- **Average Leg Latency**: The mean latency for individual legs of the path to and from the Zero Trust exchange during the selected time window.
- **Leg Loss**: The percentage of packet loss for individual legs of the path to and from the Zero Trust exchange during the selected time window.
- **Peer Impact Analysis**: Indicates whether other customers on the same Inter ASN path are also impacted, and shows the number of impacted customers when applicable.
- **Deviation from Baseline**: Displays deviation from baseline metrics (P50, P90, P95, average latency, average leg latency, and leg loss) with up and down arrows.
[See image.](#img_ASNdetail)
[]
![Image of ASN details from selecting the ASN links](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-node-detail.png)
IP View
You can click an ISP circle to view granular details on its network performance by clicking **IP View**.
View a Sankey visualization of all impacted IP addresses and their geolocation to observe their connections to the ISP. You can switch between the IP views:
-
**IP by ASN**: View IP addresses based on how they connect to the ISP.
[See image.](#img_ipview_asn)
-
**IP by Geo**: View geolocations with IP addresses on how they connect to the ISP.
[See image.](#img_ipview_geo)
Click **Return to ASN** to revert to the **ISP or ASN View**.
[]Performance Tables
The performance tables summarize how well the Last Mile ISP or application is doing. Depending on what your ISP or ASN View is, you might have one or both of the performance tables.
The ISP Performance Table displays the top 200 Last Mile ISPs by ASN with the following information:
- **Last Mile ISP (ASN)**: The name of the Last Mile ISP and its associated ASN.
- **Users**: The total number of impacted users.
- **Avg Hops**: The average number of hops from the the user to the Last Mile ISP.
- **Avg Latency**: The average latency of the Last Mile ISP over the selected time range.
- **P50 Latency**: The latency for the 50th percentile of impacted users.
- **P95 Latency**: The latency for the 95th percentile of impacted users.
- **Baseline**: The established baseline for the Last Mile ISP from the previous 7 days when users access the Last Mile ISP.
- **Baseline Deviation**: The deviation from the baseline for the Last Mile ISP. This information determines the Last Mile ISP performance by comparing it to the baseline.
- Zero Trust Exchange: The names of the Zero Trust Exchange data centers connected to the ISP.
[See image.](#img_table-isp)
The Application Performance Table displays the performance of applications that are accessed by users with the following information:
- **Applications**: The name of the application.
- **ZDX Score**: The ZDX Score of the application. To learn more, see [About the ZDX Score](/zdx/about-zdx-score).
- **Users**: The number of users accessing the application.
- **Avg Hop**: The average number of hops the application encounters.
- **Avg Latency**: The average latency the application experiences.
- **P50 Latency**: The network latency for the 50th percentile of impacted users.
- **P95 Latency**: The network latency for the 95th percentile of impacted users.
- **Baseline**: The established baseline from the previous 7 days when users access the application.
- **Baseline Deviation**: The deviation from the baseline that determines the performance of the application.
[See image.](#img_table-application)
**Default sort**: The ISP Performance Table is sorted by **Baseline Deviation** by default to surface the most deviated ISPs first.
[]
![View how the client connects to the application](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-client-app-1_0.png)
[]
![Forward Path view of the Client to Zero Trust Exchange](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-client-zte-forward-1_1.png)
[]
![Reverse Path view of the Client to Zero Trust Exchange](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-client-zte-reverse-1_0.png)
[]
![View Zero Trust Exchange to App pathways](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-zte-app-1_0.png)
[]
![View the Client to Application pathways](/downloads/tech-pubs-drafts/zdx-draft-articles/doc-59631-monitoring-network-intelligence-dashboard/zdx-network-intelligence-asn-client-direct.png)
[]
![View the impacted IPs](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-IP-View-1.png)
[]
![View how geolocations connect](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-ipview-geo.png)
[]
![View the ISP Performance Table](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-tables-ISP_0.png)
[]
![View the Application Performance table](/downloads/zdx/analytics/monitoring-network-intelligence-dashboard/zdx-network-intelligence-tables-Application_0.png)