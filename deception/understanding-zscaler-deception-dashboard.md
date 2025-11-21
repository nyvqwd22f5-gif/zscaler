# Understanding the Zscaler Deception Dashboard
Source: https://help.zscaler.com/deception/understanding-zscaler-deception-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1531378.pdf

The Zscaler Deception dashboard (Investigate page) is an interactive and graphical representation of real-time alerts that are indicators of attacker activities. When an attacker interacts with the decoys, Deception detects threats, collects information on the attacker's actions and intentions, and generates high-fidelity and real-time alerts that are displayed on the dashboard.
![The Zscaler Deception dashboard (Investigate page)](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/zscaler-deception-dashboard-new.png)
Viewing and Filtering Alerts
Deception detects threats and generates alerts for attacker activities and are displayed in a graphical format on the dashboard. The graph is interactive and includes icons that represent a Deception object or attackers.
The alert graph includes the following icons:
- Zscaler Deception Admin Portal: A single point of configuration and management platform for the entire Deception solution.
- Decoy Connector: Lightweight virtual machines (VMs) that host network decoys. They also act as a network broker to connect the Deception service to on-premises systems and Active Directory (AD) decoys in your environment.
- Decoy Group: Logically organized networks and Threat Intelligence (TI) decoys based on function, location, system type, etc.
- Decoy: A trap to divert attackers. Decoys look like real assets. The moment the adversary interacts with a decoy, it detects the threat and relays all the information to the Deception Admin Portal. Each type of decoy is represented by a unique icon. The icon in the following image depicts a network decoy.
- Attacker: When an attacker interacts with the decoys, it is depicted by either a unique [identicon](https://en.wikipedia.org/wiki/Identicon) or, in the case of TI activity, a country's flag, if available. Icons make it easier to distinguish and visually identify attackers without the need to remember complex IP addresses or hostnames.
[See image.](#graphical-alert-view-dashboard)
You can click an icon on the graph to view the [details pane](/deception/viewing-details-pane) that shows all the attacker activities on the system.
- [Filtering Alerts By Time](#filter-alert-time)
- [Filtering Alerts Using Queries](#filter-alert-queries)
[]You can filter alerts over a period of time between the last 10 minutes and all time.
By default, the dashboard displays information for alerts that occurred in the last 7 days.
To filter alerts by time frame:
-
On the **Investigate** page, click the time selector drop-down menu, and select a time period (e.g., **Last 30 days**).
[See image.](#time-selector-dashboard)
-
To select a custom time frame, provide a **Start **and **End **date in years, months, days, hours, and minutes.
[See image.](#select-custom-time-frame)
[]You can apply filters using queries to focus on specific alerts. You can use the built-in queries or the query builder to create queries to filter alerts.
- [Filtering Alerts Using Saved Queries](#built-in-query-example)
- [Filtering Alerts Using the Query Builder](#query-builder-example)
[]Deception provides a list of saved queries to quickly filter certain types of alerts.
On the **Investigate** page, select a saved query from the **Select Query** drop-down menu. For example, select **Cloud Threat Detection **to filter for threat detections related to AWS or Azure.
[See image.](#select-built-in-query-dashboard)
[]The query builder helps you to construct and modify queries. You can select the built-in syntax to create simple and advanced query expressions and save them for future use.
- [Creating a Simple Query](#create-simple-query)
- [Creating an Advanced Query](#create-advanced-query-example)
- [Saving a Query](#save-query)
[]Simple queries have just one parameter. To build a query to filter attacks from a particular IP address:
- On the **Investigate** page, click the query builder.
-
Enter `attacker.ip`.
As you continue to type, the query builder lists the built-in syntax that matches your query.
[See image.](#create-simple-query-dashboard)
-
Select **attacker.ip** from the drop-down menu and add `is "192.0.2.0"` to the query.
Alerts from the specified attacker's IP address are filtered and displayed on the dashboard.
[See image.](#simple-query-added-dashboard)
You can use various supported fields, parameters, operators, and regular expressions to build queries depending on your requirements. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
When using regular expressions to build dashboard filter queries, make sure that appropriate letter casing is used in the expressions as the dashboard filter does not support case-agnostic expressions nor [the case-insensitivity flag](/deception/understanding-and-building-queries#zd-query-language-regex) (`\I`).
[]Advanced queries are complex queries with Boolean logic statements. To filter alerts that match one or more criteria:
- On the **Investigate** page, click the query builder.
-
Enter `(type)`.
As you type, the query builder lists the built-in syntax that matches your query syntax.
[See image.](#create-advanced-query-dashboard)
-
Select the required built-in syntax from the list and create the advanced query:
`(type is "windows") or (type is "network" and sub_type is "file")`
Alerts that match one of the criteria of the query are filtered and displayed on the dashboard.
[See image.](#advance-query-added-dashboard)
You can use various supported fields, parameters, operators, and regular expressions to build queries depending on your requirements. To learn how to build queries, see [Understanding and Building Queries](/deception/understanding-and-building-queries).
When using regular expressions to build dashboard filter queries, make sure that appropriate letter casing is used in the expressions as the dashboard filter does not support case-agnostic expressions nor [the case-insensitivity flag](/deception/understanding-and-building-queries#zd-query-language-regex) (`\I`).
[]You can create queries and save them for future use.
To save a query:
- On the **Investigate** page, create a [simple query](#create-simple-query) or an [advanced query](#create-advanced-query-example).
- (Optional) Select a time frame from the time selector drop-down menu (e.g., **Last 30 days**).
-
Click **Save Query**.
[See image.](#save-query-option-dashboard)
-
In the **Save Query** window:
- **Name**: Enter the name of the query.
- **Include time period**: (Optional) Enable if you want the query to record the selected time period and restore the time period settings when the query is selected in the future.
[See image.](#save-query-dashboard)
-
Click **Save Query**.
The query is saved and is listed in the **Select Query** drop-down menu.
[See image.](#query-saved-listed-dashboard)
Click the **Delete **icon to delete the query that you saved.
Using the Chronology Slider
The chronology slider shows a graph of attack volume by time. After filtering alerts by timeline, you can drag the controls at both ends of the chronology slider to select a subset of time from your main filter.
For example, if you have filtered alerts for the last 30 days, you can drag the controls at both ends of the chronology slider to trim the timeline to the first 10 days. Click the **Apply Current Range** (![Apply current time range icon](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-chronology-slider-apply-current-range-icon.png?1659593264)
) icon to apply the time range and view the alert graph for the subset of time.
Click the **Start Replay** (![Start replay icon](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-chronology-slider-replay-icon.png)
) icon to replay the registered alerts in the sequence they occurred. This helps you to analyze the chronology of attacks.
[See image.](#chronology-slider-dashboard)
Using Controls
You can use the display controls on the dashboard to customize the alert graphs.
- Zoom Slider: Zooms in and out of the alert graph.
- Fit to Screen: Fits the elements of the graph to the screen resolution.
- Rearrange Elements: Rearranges the elements on the alert graph to their original position, if they are scattered over the screen.
- Lock Elements: Locks all the elements on the alert graph.
- Full Screen: Toggles to full-screen mode.
[See image.](#dashboard-display-buttons)
Using Additional Filters
You can use additional filters to select the alert graph layout, view specific details, filter attack types, etc.
To apply filters:
-
On the **Investigate** page, click the filter icon in the bottom-right corner of the dashboard.
[See image.](#dashboard-additional-filter)
-
In the **Filters** window:
- **Level of Detail**: Allows you to reduce or increase the level of element or object details on the alert graph. The first level is the Deception Admin Portal, followed by Decoy Connectors, Decoy Groups, and Decoys. Click the minus (-) icon to reduce the number of elements on the graph and view basic details of the attack. Click the plus (+) icon to increase the number of elements on the graph and view the in-depth details of the attack. The number on the filter icon shows the current level of detail.
- **Layout**: Select a layout for the alert graph from the drop-down menu:
- **Default**
- **Hierarchy** (Tree layout)
- **Radial** (Circular layout)
- **Threat Level**: Select a threat level from the drop-down menu to filter alerts based on the threat severity:
- **All**
- **Medium and Higher**
- **Only High**
- **Decoy Type**: Select a decoy type from the drop-down menu to filter alerts for the specified decoy type:
- **Active Directory**
- **Endpoint**
- **ITDR**
- **Network**
- **Threat Intelligence**
- **Attack Types**: Select an attack type from the drop-down menu to filter alerts for the specified attack type:
- [List of attack types](#attacktypelist)
- **Demographics**: Select a demographic level to filter the alerts based on the interaction between the attacker and the Deception objects:
- **All**
- **One to Many**
- **Many to One**
- **One to One**
- **Show Only Attacks**: Enable to show only those objects on the alert chart that are attacked.
- **Interactive Only**: Enable to show attacks only when there is an interaction between the attackers and decoys. For example, if **Interactive Only** is enabled, attacks like network reconnaissance are not shown.
- **Attackers as Identicons**: Enable to show attacker icons as identicons. Disable to show a generic attacker icon instead of a unique identicon for each attacker.
- **Attackers as Flags**: Enable to show threat intelligence attack icons as country flags, if available.
- **Attackers as Tags**: Enable to show attacker icons as tagged names. You can tag an attacker icon with an alternate text for your reference. If enabled, the attacker icons are shown with tagged names.
[See image.](#config-additional-filters-dashboard)
- []**AMQP**
- **Cloud**
- **Credential Theft**
- **Custom Service**
- **Endpoint**
- **FTP**
- **File Theft**
- **GenAI**
- **ITDR Threat Detection**
- **MITM**
- **MQTT**
- **MongoDB**
- **MySQL**
- **Network**
- **PostgreSQL**
- **SKADA**
- **SSH**
- **Telnet**
- **Threat Intelligence**
- **Web**
- **Windows**
[]![Graphical alert view on the Zscaler Deception dashboard](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-graphical-alert-view.png)
[]![Select a time period to filter alerts](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-time-selector.png)
[]![Select custom time frame](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-custom-time-range.png)
[]![Select a built-in query to filter alerts](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/select%20query.png)
[]![Create a simple query using the query builder](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-simple-query.png?1659597582)
[]![Alerts are filtered based on the simple query](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-simple-query-added.png)
[]![Create an advanced query using the query builder](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-advance-query.png)
[]![Alerts are filtered based on the advanced query](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-advance-query-added.png)
[]![Save Query option on the dashboard](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/save%20query.png)
[]![Save a query](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/deceptionsave-query-window.png)
![Saved query](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/show%20saved%20query.png)
[]
[]![Chronology slider on the dashboard](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-chronology-slider.png)
[]![Dashboard display icons](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-dashboard-display-buttons.png)
[]![Zscaler Deception dashboard filter icon](/downloads/deception/investigate/about-zscaler-deception-dashboard/zscaler-deception-dashboard-filter-icon.png?1660127186)
[]![Configure additional filters on the dashboard](/downloads/deception/investigate/understanding-zscaler-deception-dashboard/deception-additional-filters.png)