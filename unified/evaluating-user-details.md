# Evaluating User Details
Source: https://help.zscaler.com/zdx/evaluating-user-details
PDF: https://help.zscaler.com/pdf/com/en/1391316.pdf

To better understand the digital experience for a user, view the user details page for user and device metrics.
To access user details, choose one of the following options:
- From the User Overview page, select one or more applications from the Applications filter drop-down menu and click **Apply. **Click the table cell for User or Devices to view a page with details about the user's digital experience.
- Search for a user in the Search and view their page. To learn more, see [Using Search in the ZDX Admin Portal](/zdx/using-user-search-zdx-admin-portal).
Any filters used on the User Overview page remain in place after selecting a user or the user's device. Click **Reset **to adjust or remove the filters.
[See image.](#image-indivuserpg)
You can access the following user details:
- [User Devices](#userdevices)
- [Applications](#apps)
- [Viewing ZDX Score Over Time](#scoregraph)
- [Analyzing the ZDX Score: Single Date and Time](#analyze-single)
- [Analyzing the ZDX Score: Time Range](#analyze-range)
- [Comparing ZDX Scores](#compare-scores)
- [Web Probe Metrics](#webprobemetrics)
- [Cloud Path](#cloudpath)
- [Device Health](#devicehealth)
- [User Device Events](#events)
- [Diagnostics](#DeepTracing)
[]This section displays the devices in use and specific device information, such as the OS type and version, CPU, Memory, Private IP, Public IP, etc. If there is more than one device, the first device is automatically selected. You can also use the scroll bar on the left to select and view device information when multiple devices are in use. The device remains selected even with time range and other filter changes. Devices in this section are displayed depending on the time selected and factors such as device network issues, offline/sleep status, etc. The data on the rest of the page also populates depending on the device selected.
The Tunnel Type that displays depends on the device profile. The available tunnel types are:
- Tunnel 1.0 or TWLP
- Tunnel 2.0 in DTLS Mode
- Tunnel 2.0 in TLS Mode
- Tunnel Unknown
If a Tunnel Type is Unknown, it means ZDX could not detect it.
![View device details in the user details page](/downloads/zdx/analytics/users/evaluating-user-details/zdx-user-details-more-device-details5.png)
The User Device Information window displays additional device information organized under the Hardware, Network, or Software tabs. Click the different tabs to view additional information. For example, on the Software tab, you can view the ZDX and Zscaler Client Connector versions for the device.
![View Additional User Device Details](/downloads/zdx/analytics/users/evaluating-user-details/zdx-sw-tab-device-profile4.png)
[]All the applications selected in the Applications Filter are shown. You can see the period of time that is covered above the applications.
Each application has a ZDX Score. Compare the different applications to understand how they are impacting a user's particular ZDX Score. If there are more than three applications, scroll left or right to see more applications. By default, the application with the lowest ZDX Score is selected.
![Select application on user details page](/downloads/zdx/analytics/users/evaluating-user-details/zdx-user-details-application-card_0.png)
Selecting an application updates the rest of the information that appears in the page. By changing the application, the subsequent sections update accordingly. Each of these allow you to further understand the application and its impact to the user for the selected point in time. The metric information is based on what was chosen when setting up a probe. To learn more, see [Configuring a Probe](/zdx/configuring-probe).
[]The ZDX Score Over Time graph shows how the ZDX Score trends over the selected time period for this user by device. If a device is not selected, this graph is not populated.
In the ZDX Score Over Time graph on the User page, the Smooth ZDX Score displays by default. The Smooth ZDX Score uses historical data to reduce short-term variations in the ZDX Score and to provide a more representative metric with reduced variability. Select the checkbox option below the graph to view the ZDX Score. This selection remains even when changing filters and applications.
Both scores track as lines across the graph. Scores fall into three categories:
- **Good**: The score is above an acceptable threshold and ranges from 66–100. The color for this range is green.
- **Okay**: The score is acceptable and ranges from 34–65. The color for this range is amber.
- **Poor**: The score is below an acceptable threshold and ranges from 0–33. The color for this range is red.
You can select a point on the graph to see the exact date, time, and Smooth ZDX Score for that period in a tooltip. If the ZDX Score option is selected for the graph, the tooltip displays the ZDX Score at that time as well. If there is an **Error** icon (![Error icon on the ZDX Score Over Time graph](/downloads/zdx/analytics/about-users-dashboard/zdx-devicedetails-alerticon.png)
) at the point, you can view more information about the cause and the related application. Click the **Details **icon (![Details icon in the ZDX Score Over Time graph](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-score-details-icon_0.png)
) next to the score in the tooltip to go to the Applications page for further details about the application.
[See image.](#image-zdxscoregraph)
A **Zoom In** icon (+) appears as you hover over the ZDX Score Over Time graph. Use this icon to select the time period to zoom in for greater detail. This shows the graph over that smaller time period. The Web Probe Metrics, Device Health, and Cloud Path also reflect the same period of time. The time limit to zoom in is 5 minutes. Click **Zoom Out** to view the original graphs.
You can also enable and display incident data in the ZDX Score Over Time graph that's reflected on the Incidents Dashboard, based on the timeline of a particular incident. To view incident data:
- Click **Show Incidents**.
- Hover over an icon that represents one of the incident types: Wi-Fi, Last Mile ISP, Zscaler, or Application. The names of the incident type and epicenter are displayed, along with the number of impacted users.
- Click **View Incident** to see the incident's details and key metrics.
[See image.](#incidents-zdx-score)
To learn more about incident types, see [Monitoring the Incidents Dashboard](/zdx/monitoring-incidents-dashboard).
[]For Poor scores that range from 0–33, the ZDX Score Over Time graph includes a feature to help identify reasons for the low score. The application tile with the lowest Poor score is preselected, and ZDX runs root cause analysis automatically on the most recent Poor score. As a result of the analysis, potential factors are provided that might have contributed to the score. If you select a different application tile, ZDX analyzes its most recent Poor score within your selected timeline.
Automated analysis for Poor ZDX Scores is not applicable to ZDX Call Quality applications.
![Automated analysis for the lowest Poor ZDX Score](/downloads/zdx/analytics/users/evaluating-user-details/zdx-yengine-analyze-auto-analysis.png)
If you select a different data point on the graph for a Poor score at a specific date and time, click **Analyze Score** within the tooltip to, again, trigger potential factors that might have contributed to the score.
![Analyze Score button in tooltip of ZDX Score Over Time graph with corresponding table](/downloads/zdx/analytics/users/evaluating-user-details/zdx-yengine-analyze-button-and-table34.png)
The analysis table provides the following information for a particular date and time in the graph:
- **Factor**: Shows a probable cause for the low score.
- **Explanation**: Addresses why the corresponding factor might be the issue.
- **Confidence Level**: Quantifies the assumed accuracy of the analysis, based on probes with similar issues.
- **Provide Feedback**: Lets Zscaler know the accuracy level of the analysis.
- Click the **thumbs-up** icon (![Thumbs-up icon](/downloads/zdx/analytics/evaluating-user-details/thumbs-up1.png)
) if the analysis for the low score was helpful. A success message confirms Zscaler has received your feedback.
- Click the **thumbs-down** icon (![Thumbs-down icon](/downloads/zdx/analytics/evaluating-user-details/thumbs-down1.png)
) if you believe the analysis was inaccurate and the low score is related to a different issue.
- Select one of the potential factors from the drop-down menu. If you believe a different factor caused the issue, select **Other **and specify the factor.
- Share any other details about the issue.
- Click **Submit**.
![Pop-up to provide feedback when analysis results are inaccurate](/downloads/tech-pubs-drafts/zdx-draft-articles/evaluating-user-details-draft-c/zdx-yengine-analyze-thumbdown2.png)
[]As an additional method of analyzing Poor ZDX Scores beyond a particular date and time, the ZDX Score Over Time graph also includes an option to analyze scores within a time range. After you select a point on the graph for a Poor score at a specific date and time, complete the following steps:
- Move the slider to the right on a second point in the graph. This point represents the end of your time range.
- Click **Analyze Range **to display potential factors that might have contributed to the low scores within your specified time range.
![Analyze Range button with corresponding table](/downloads/zdx/analytics/users/evaluating-user-details/zdx-analyze-range-button-and-table2_1.png)
To learn more about the details in the analysis table, see [Analyzing the ZDX Score: Single Date and Time](#analyze-single).
[]You can compare ZDX Scores for an application to understand why they might vary at different points in time. A score comparison can highlight why a current score might be considerably different from a previous score. The feature utilizes web, device, and Cloud Path metrics to help determine differences in scoring.
Web metrics are not used or provided when comparing scores for a Network application.
After selecting a point within the ZDX Score Over Time graph to start your comparison, do one of the following from the Compare to** **drop-down menu:
- Compare the ZDX Score of your selected point to a previous ZDX Score.
- Compare the ZDX Score of your selected point to a future ZDX Score, up to the current date and time.
![Drop-down options to compare ZDX scores](/downloads/tech-pubs-drafts/zdx-draft-articles/evaluating-user-details-draft-c/zdx-yengine-compare-options2.png)
To compare your selected point to a previous ZDX Score, use a provided timeline from the drop-down menu:
- Click **Compare to**.
- Select **Last known good score** or one of the time range options. The option for **Last known good score** searches the score history for the last available score between 66 and 100. The time range options show the score from the same time on the previous day, 2 days, or 7 days. The **Compare ZDX Scores** page appears.
[See image.](#compare-zdx-scores)
The page provides the following details and metrics:
- **Analyzed Point **and **Comparison Point**: The **Analyzed Point** represents the initial date and time you selected for the application. The **Comparison Point** represents the date and time to which you're comparing the **Analyzed Point**. Use the **Comparison Point** time range filter if you need to specify a different date and time for comparison.
-
**ZDX Score**: Shows the side-by-side ZDX Score graphs for each selected point. To learn more about ZDX Scores, see [About the ZDX Score](/zdx/about-zdx-score).
[See image.](#points-scores)
- **Key Differences**: Shows the differences in metric values for each selected point. The higher value for each metric is highlighted.
-
**Cloud Path**: Shows the hop views for each selected point. Click **View Detailed Cloud Path **to access either a larger **Hop View** or the **Command Line View**.
[See image.](#diff-cp)
-
**Hop View**: Shows a comparison and any differences in the Cloud Paths from the user's device to the application. To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[See image.](#compare-hops)
-
**Command Line View**: Shows a text-based comparison of the Cloud Paths. To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[See image.](#compare-cl)
- **Cloud Path Metrics**: Shows the Cloud Path metric values for each selected point. The higher value for each metric is highlighted.
- **Web Metrics**: Shows the web metric values for each selected point. The higher value for each metric is highlighted. Web metrics are not provided for Network applications.
-
**Device Metrics**: Shows the device metric values for each selected point.
[See image.](#cp-web-device)
To compare your selected point to either a previous ZDX Score at a custom date and time or to a future ZDX Score (up to the current date and time), use the **Custom time** option:
- Click **Compare to**.
- Select **Custom time **from the drop-down menu. The **Compare ZDX Scores** page appears.
- Select your **Comparison Point** in the ZDX Score Over Time graph. Use the time range filter if you need to specify a different time range not shown in the graph.
[See image.](#select-compare-point)
- Click **Compare** to show ZDX Score details for both the **Analyzed Point** and the **Comparison Point**.
[See image.](#custom-compare-button)
[]The Web Probe Metrics section shows the application being monitored and provides the following metrics for the application:
- Page Fetch Time
- Server Response Time
- DNS Resolve Time
- Availability
Web probe metrics are not provided for Network applications. To learn more, see [Monitoring the Performance Dashboard](/zdx/monitoring-performance-dashboard).
Page Fetch Time reflects how long it takes the selected application to load a page for the user. The Page Fetch Time graph includes a baseline for any given region with at least one active device. For predefined applications, the baseline represents an average score based on device metrics across all organizations. For custom applications, the baseline represents an average score based on device metrics from a given organization.
Baseline metrics are calculated daily for each application on a rolling timeline of the previous 7 days. The baseline value is measured in milliseconds, as shown in the following example:
![Example graph for Web Probe Metrics with baseline](/downloads/zdx/analytics/about-users-dashboard/zdx-wpm-pft-baseline2.png)
Users with an Advanced Plus subscription can view a tooltip with DNS, SSL, TCP, TTFB (Time to First Byte), and TTLB (Time to Last Byte) metrics that comprise the total Page Fetch Time. Additional graphs are displayed for PAC parsing time, DNS time, TCP connect time, HTTP connect time, and SSL time. Where applicable, individual server redirects are included for each graph to reflect one of the following:
- Client to Public Service Edge
- Public Service Edge to the application
- Client to the application
If more than one redirect is displayed, the last redirect indicates the time to the final destination.
![Page Fetch Time metrics](/downloads/zdx/analytics/users/evaluating-user-details/zdx-pft-metrics-rev.png)
Click **View Details** within the tooltip to see the Total Page Fetch Time, as well as the metrics for Total Bytes Transferred and Total Throughput. Hover over the bar graph to view the individual time metrics for each server redirect.
![Page Fetch Time detailed metrics](/downloads/zdx/analytics/users/evaluating-user-details/zdx-pft-metrics-details-rev.png)
All metrics are preselected, but you can click the menu and deselect metrics that are not relevant to your understanding of the application. Click a point on a graph to see the value or percentage for that exact date and time. When you click a point on one graph, all graphs show their values for that same point.
Whenever traffic is steered through Source IP Anchoring (SIPA), **via SIPA** is displayed and the corresponding traffic within the timeline is highlighted in the graphs. Traffic forwarding through SIPA enables you to control the source IP address of the traffic to the final destination without bypassing the Zscaler security service. To learn more, see [Understanding Source IP Anchoring](/zia/understanding-source-ip-anchoring).
If SIPA traffic is intermittent within a particular timeline, only the time windows with SIPA Web probes are highlighted, as shown in the following example:
![SIPA rendered in Web Probe Metrics](/downloads/zdx/analytics/users/evaluating-user-details/zdx-sipa-web-rendered6.png)
At times, you might see icons that indicate warnings, errors, or Zscaler Private Access (ZPA) rate limiting. For example, the following graph shows the icon that represents ZPA Web probe rate limiting. Click the icon to display related metrics information.
![Example icon for rate limiting in Web Probe Metrics](/downloads/zdx/analytics/about-users-dashboard/zdx-rate-limiting-graph-example2.png)
To learn more about possible errors associated with the icons, see [Web Probe Errors](/zdx/web-probe-errors).
[]Depending on the device the user was on at the time, different information is available about that device. The Network and Disk options are preselected by default, and you can choose the elements you want to review. This selection remains even when navigating to a different user page or viewing a Diagnostics session. To learn more about Diagnostics, see [About Diagnostics](/zdx/about-diagnostics).
![View Device Health metrics in the user details page](/downloads/zdx/analytics/about-users-dashboard/zdx-device-health-overview2.png)
Select a place on a graph to see the value or percentage for that exact date and time. By selecting a point on one graph, all graphs show their values for that same point. For users with an Advanced Plus subscription, the most impacted processes are also displayed for applicable CPU, Memory, Disk I/O, and Network I/O, regardless of which graph is selected. A maximum of 5 processes is shown for each element within a given 5-minute interval. Click the **Expand **icon or **Collapse **icon to the right of the section label to expand or collapse this section.
[See image.](#image-devicehealthvalues)
[]The Cloud Path provides a path visualization of metrics between hop points of traffic. It can capture a direct traffic path, as in the case of Zscaler Client Connector to Egress to destination, or tunneling through a ZIA Public Service Edge (from Zscaler Client Connector to Egress to ZIA Public Service Edge to destination). To learn more, see [Evaluating the Cloud Path](/zdx/evaluating-cloud-path).
[]User Device Events tracks the events for a device over a selected period of time. Each event is categorized in terms of severity, as represented at the bottom of the timeline: Informational, Warning, Error, and Critical. To interpret events based on a single severity level, you can filter these events by clicking directly on the severity labels.
Additionally, click on the event to view detailed information about each event in a side panel. The side panel reveals a granular breakdown that includes timestamps, category, and attribute changes related to the event. The table below provides detailed descriptions of each event type.
| Event Name | Description |
| ---------- | ----------- |
| Informational | Events that display non-critical details, like a notification. |
| Warning | Events that warn of potential issues, indicating a component or application is not in an ideal state and could lead to a critical error. |
| Error | Events that indicate problems without requiring immediate attention. |
| Critical | Events that require immediate attention, often at the system-wide level, indicating failures or unresponsive applications. |
![User Device Events ](/downloads/tech-pubs-drafts/zdx-draft-articles/evaluating-user-details-draft/User-Device-Events-Severity.jpg)
![User Device Events](/downloads/tech-pubs-drafts/zdx-draft-articles/evaluating-user-details-draft/User-Device-Events-Side-Panel.jpg)
The Category drop-down menu provides the option to filter the event categories for Zscaler, Hardware, Software, Network, and Microsoft Endpoint:
![Screen shows the device event icons and the category drop-down menu](/downloads/zdx/analytics/users/evaluating-user-details/zdx-ept-swim-lane6.png)
[]Diagnostics in ZDX can provide deeper granularity into process-level information for a user. Click **Start Diagnostics **to begin a Diagnostics session. This opens a session window with user details prefilled. To learn more, see [About Diagnostics](/zdx/about-diagnostics).
[]![Start a Diagnostics session from the user details page](/downloads/zdx/analytics/users/evaluating-user-details/zdx-user-details-DT-link5.png)
To learn more about performance data on the Users Overview page, see [Monitoring the Users Overview](/zdx/monitoring-users-overview).
[]![Select applications from filter to view user details](/downloads/zdx/analytics/users/evaluating-user-details/zdx-user-details-applications-filter5.png)
[]![Graph showing Smooth ZDX Score](/downloads/zdx/analytics/about-users-dashboard/zdx-smooth-zdx-score.png)
[]![Compare ZDX Scores page that shows last good score](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-last-good-score2.png)
[]![Comparing ZDX points and scores](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-points-and-score.png)
[]![Compare key differences and cloud paths](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-key-diff-and-cloudpath.png)
[]![Compare Hop Views](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-hop-view.png)
[]![Compare Command Line Views](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-command-line-view.png)
[]![Compare cloud path, web, and device metrics](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-cp-web-device.png)
[]![Custom Comparison Point](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-custom-comparison-point.png)
[]![Compare button for custom compare](/downloads/zdx/analytics/evaluating-user-details-draft-e/zdx-yengine-compare-custom-button.png)
[]![Device Health Process Stats](/downloads/zdx/analytics/evaluating-user-details/zdx-device-health-process-stats2.png)
[]![Show incidents in ZDX Score Over Time graph](/downloads/zdx/analytics/users/evaluating-user-details/zdx-incident-integration-icon2.png)