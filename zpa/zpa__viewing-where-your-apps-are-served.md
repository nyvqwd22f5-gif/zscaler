# Viewing Where Your Apps Are Served
Source: https://help.zscaler.com/zpa/viewing-where-your-apps-are-served
PDF: https://help.zscaler.com/pdf/com/en/1529636.pdf

The Where are my apps being served from? page provides a view of hosting providers and analytical details of the App Connectors that have been serving your applications for the last quarter. You can view and understand where your applications are hosted because App Connectors act as a good proxy for your private applications in certain cases. While observing and understanding trends, you can filter and sort to customize your view to focus on details based on your selection.
The report is generated on the same schedule as the [quarterly business reports](/zpa/viewing-quarterly-business-review-reports).
Bar View
The Bar view provides a visual and analytical representation of the number of FQDNs, App Segments, Users, and Transactions using horizontal bar graphs.
![Bar View displays bar graphs of private applications](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-bar-2.png)
In the Bar view, you can:
-
Sort by **FQDNs**, **App Segments**, **Users**, or **Transactions** in ascending or descending order to view private applications.
[See image.](#img_bar_sortby)
-
Filter private applications based upon selection (**AWS**, **Azure**, **Google Cloud**, **Data Center**). At least one private application must be selected to display data.
[See image.](#img_bar_filter)
- Switch between the Map and Bar view.
-
Hover over a bar to view the number of FQDNs, App Segments, Users, Transactions, and Location details.
[See image.](#img_bar_hover)
If hosting provider details are not determined, **Unknown** appears next to the name of the private applications in Bar view. For accurate location tracking regarding data center environments, edit the App Connector group, set **Hosting Detection** to **Manual**, and then select or enter host data center information. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors) and [Editing App Connector Groups](/zpa/editing-connector-groups).
Map View
The Map view displays the geographic locations of all cloud providers based upon your selection. Zscaler uses the user device's location service to determine the general vicinity of the private application's location.
![View insights on the Where are my apps being served from? page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-Where-page-2.png)
In the Map view, you can:
-
Sort by **FQDNs**, **App Segments**, **Users**, or **Transactions** in ascending or descending order to view a list of private applications. Click **Prev** or **Next** to navigate between items. The map automatically adjusts its location based on the items selected.
[See image.](#img_map_sortby)
-
Filter private applications based upon selection (**AWS**, **Azure**, **Google Cloud**, **Data Center**).
[See image.](#img_map_filter)
- Switch between the Map and Bar view.
-
Zoom in, zoom out, center your position, or reset your view to review areas of interest. You can zoom in and out with your mouse's scroll wheel.
[See image.](#img_map_zoom)
-
Hover over a marked location to view the number of FQDNs, App Segments, Users, Transactions, and Location details.
[See image.](#img_map_hover)
[]
![Sort the list of private applications in ascending or descending order or navigate through the list.](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-map-sort-by-2.gif)
[]
![Filter based on private applications](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-map-filters-1.gif)
[]
![Use the Zoom menu to interact with map](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-zoom-menu.png)
[]
![Hover over a location to view more details](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-map-hover.png)
[]
![Use Sort By to select items in ascending or descending order](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-bar-sort-by-1.gif)
[]
![Select filters to specify private applications to view](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-bar-filter-1.gif)
[]
![Hover over a bar to view details of the private application](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-where-are-my-apps-being-served/ZPA-where-bar-hover-1.png)