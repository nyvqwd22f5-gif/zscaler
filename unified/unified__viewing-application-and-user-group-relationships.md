# Viewing Application and User Group Relationships
Source: https://help.zscaler.com/unified/viewing-application-and-user-group-relationships
PDF: https://help.zscaler.com/pdf/com/en/1531251.pdf

Application and User Group Relationships provides you with interactive and actionable insights on the usage of application segments and segment groups by user groups. To help you design better policy, you can gain insights into the relationships of the application and user groups to ensure [least-privileged access](https://www.zscaler.com/resources/security-terms-glossary/what-is-least-privilege-access), a central tenet of Zscaler’s Zero Trust Network Access (ZTNA).
The Application and User Group Relationship insights are provided for the following items:
- Application Segments
- The application segments accessed by user groups.
- The user groups accessing the application segments.
- Segment Groups
- The segment groups accessed by user groups.
- The user groups accessing the segment groups.
Items include application segments, segment groups, and user groups.
[See image.](#UsingGIF)
Application and User Group Relationships Report
Use the Application and User Group Relationships page (Logs > Insights > Private Applications > Usage > Application and User Group Relationships) to view the usage between applications and user groups.
The report consists of the following information:
- **Top Items**: Displays the top items as segment groups, application segments, or user groups with the total number. This automatically updates based on the selection filter and exclusion criteria from the Settings drawer.
-
**Current Report Information**: Displays the current report information based on when it was last updated.
[See image.](#ReportInformation)
- **Launch Tour**: Displays a series of guided steps to interact with the Application and User Group Relationships page.
-
**Run Report**: Generate the report to include data from the selected time range. In the time range drop-down menu, you can select a preset range (e.g., **14 Days** or **30 Days**). By default, the time range of the report is set to **14 Days**. The report automatically expires after 90 days. You cannot run the report if there is no more data to add when the report was recently updated.
Run Report is disabled for 72 hours before and after 12:00 AM on the first Saturday of every other month. Customers with the Segmentation Add-On can generate one report per day, and customers without the license can generate one report every 90 days.
[See image.](#RunReport)
- **Settings**: Customize your page view between Application Segments or Segment Groups. The default is set to Application Segments. You can opt to exclude items.
- **Download**: Download a CSV file for your list of items. Click **Download** to open the **Download CSV File** window. In the **Download CSV File** window, you can select the following report views:
-
**Detailed**: The detailed report includes details about segment groups, application segments, applications (including FQDN, port, and protocol), access policy rule, and user groups and users who have accessed the applications and application segments.
Only customers with the Segmentation Add-On can generate detailed report views for the last 6 reports (i.e., 180 days).
[See image.](#detailedDownloadReport)
- **Summary**: The summary report includes application segments, segment groups, and the count of users and user groups.
[See image.](#summaryDownloadReport)
- **Filtered Report**: The filtered report includes details about segment groups, application segments, applications (including FQDN, port, and protocol), access policy rules, and user groups and users who have accessed the applications and application segments for the filtered application segments.
- **View Filter**: Alternate the view of your page between Application Segments or Segment Groups and User Groups.
The report displays the following graphical representations of the relationship between applications and user groups:
- **Sunburst Chart**: Displays a hierarchical graphical representation of the top items (up to 10) based on selection and view. You can select parts of the sunburst chart to drill down for granular details.
-
**List of Items**: Displays the top items based on selection and shows the total count between applications and user groups. The list shows:
- **Application Segments** or **Segment Groups**: The names of the application segments or segment groups.
- **User Groups**: The names of the user groups.
- **Users Accessed**: The number of users accessing the application (i.e., application segment or segment group).
Your list varies and updates accordingly based on your Settings, View Filter, and Selection Filter. For example, if you select Application Segments in your Settings and User Groups in your View Filter, then your list shows: User Groups, Application Segments, and Users Accessed.
[See image.](#Overview)
Customize the Application and User Group Relationships Page
Zscaler recommends starting with Customize Your View from the Settings drawer to decide what information you want to analyze: Application Segments or Segment Groups.
There are multiple ways to customize the Application and User Group Relationships page:
- [Settings](#custom-your-view)
- [Selection with the Sunburst Chart](#custom-sunburst)
- [Alternate Your View](#alternate)
- [Select](#select)
- [Exclude](#exclude)
- [Reset](#reset)
Viewing Item Details
The Application and User Group Relationships page allows you to display item details in a granular view.
You can click a specific row to open a drawer containing its details.
[See image.](#ListDetails)
[]
You can customize your view to display or exclude application segments or segment groups. To change your view settings:
-
On the **Application and User Group Relationships** page, click **Settings **(![settings-icon-01.png](/downloads/tech-pubs-drafts/zpa-draft-articles/understanding-application-and-user-group-relationships-doc-51159/settings-icon-01.png)
).
The **Settings** drawer appears.
[See image.](#SettingsDrawer)
- In the **Settings **drawer, under **Customize Your View**, select **Application Segments** or **Segment Groups**. The default is Application Segments.
-
In the **Exclude **section, you can exclude specific items depending on what you selected:
- Application Segments or Segment Groups
- User Groups
-
Branch and Cloud Connector access policy rules
The option to exclude Branch and Cloud Connector access policy rules is supported only for Application Segments.
Excluding multiple items uses the OR logic.
-
For **Maximum number of reports to retain**, select the maximum number of reports to retain (e.g., **4**, **5**, or **6**). Older reports are deleted.
The option to retain the maximum number of reports is supported only for Application Segments.
- In the Include section, you can include specific items depending on what you selected:
- **SCIM Attribute**: Select the SCIM attribute value from the drop-down menu.
- **SAML Attribute**: Select the SAML attribute value from the drop-down menu.
- Click **Save**.
Your page is updated based on your selections to view Application Segments or Segment Groups and to exclude the specified items.
[]You can interact with the sunburst chart to view multiple levels of the relationship between the application and user group. The levels are displayed as follows:
-
1st Level: Displays the relationship between the top items and what each individual item is. Up to 10 items are displayed. For example, the top 7 application segments are displayed as a continuous, inner ring and the outer ring displays what those 7 application segments are.
- Inner Ring: Displays the top items as a continuous ring.
- Outer Ring: Displays top items currently associated with the inner ring (e.g., application segments, segment groups, user groups).
Click the inner ring to display the next hierarchy level.
[See image.](#1stLevel)
-
2nd Level: Displays the relationship between the subsequent items and their associated items.
- Inner Ring: Displays the subsequent items from the previous level.
- Outer Ring: Displays the related items to the subsequent items.
- You can also:
- Hover over an item part and click to exclude it.
- Click the **Back **icon (![ZPA-ApplicationUsage-back-icon-02.png](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationUsage-back-icon-02.png)
) to return to the previous level.
Click one of the parts on the inner ring to select the item to display on the next hierarchy level.
[See image.](#2ndLevel)
-
3rd Level: Displays the last level of the hierarchical data between the selected item and who accessed it.
By selecting an item in the 3rd level of hierarchical data, the display switches your view to that item type (e.g., Application Segments > User Groups, User Groups > Application Segments).
[See image.](#3rdLevel)
If there are more than 10 items for the top inner ring or if you exclude items, then the remaining items are displayed as Others in the sunburst chart.
[See image.](#SunburstChart)
[]You can alternate between viewing Application Segments or Segment Groups (based on your Settings) and User Groups.
[See image.](#AlternateViews)
[]You can reset from the following sections:
-
Settings: Clear all exclusions and then click **Save** to reset all items.
[See image.](#ClearAll)
- Sunburst chart: Click the **Back **icon (![ZPA-ApplicationUsage-back-icon-02.png](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationUsage-back-icon-02.png)
) to return to the previous level of the chart.
- Reset: Next to the selection filter, click the **Reset **icon (![ZPA-ApplicationUsage-reset-icon-03.png](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationUsage-reset-icon-03.png)
) to return to the default view.
[]
Select your items to include what you want displayed.
A maximum of 10 items can be selected.
[See image.](#SelectFilter)
[]You can exclude items from:
-
Settings: Select items to exclude.
[See image.](#ExcludeSettings)
-
Sunburst chart: If you click on an individual item in the inner ring, you can exclude it from display.
[See image.](#ExcludeSunburstChart)
If you exclude items, then the sunburst chart, selection filter, and list adjust accordingly.
[]
![Top Items - 1st Level](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-1stLevel.png)
[]
![Application Segments and User Groups](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-2ndLevel.png)
[]
![Selected Application Segment and User Group](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-3rdLevel.png)
[]
![Application Segment Settings in the Application and User Group Relationships Page](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-and-user-group-relationships/zpa-application-user-group-relationships-settings2.png)
![Settings for Segment Groups](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-and-user-group-relationships/zpa-application-user-group-relationships-settings-segment-groups.png)
[]
![Clear All](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-and-user-group-relationships-doc-51159/ZPA-SettingsDrawer-ClearAll.png)
[]
![Selection Filter](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-usage/ZDX-ApplicationUsage-SelectFilter.png)
[]
![Exclude Items in Settings Drawer](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-Settings-Exclude.png)
[]
![Exclude Item from Sunburst Chart](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-usage/ZDX-ApplicationUsage-ExcludeItem.png)
[]
![Sunburst Chart](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationSegmentsUsage-Sunburst-Chart-1.gif)
[]
![Specific Item Details](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-usage/ZDX-ApplicationUsage-ListDetails.png)
[]
![Using the Application and User Group Relationships](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationSegmentsUsage-Sunburst-Chart-1.gif)
[]
![Application and User Group Relationship](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-Overview.png)
[]
![Report Information](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-ReportInformation.png)
[]
![Run Report](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/viewing-application-and-user-group-relationships/ZPA-ApplicationsUsage-RunReport.png)
[]
![Selected Application Segments View](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-usage/ZPA-UsageInsights-View-ApplicationSegments.png)
![Selected Segment Groups View](/downloads/tech-pubs-drafts/zpa-draft-articles/viewing-application-usage/ZPA-UsageInsights-View-SegmentGroups.png)
[]![Detailed Report View within the Download CSV File window in the Admin Portal](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-and-user-group-relationships/zpa-application-user-group-relationships-download-detailed-view.png)
[]![Summary Report View within the Download CSV File window in the Admin Portal](/downloads/zpa/dashboard-diagnostics/applications-and-users-monitoring/applications-users-insights/viewing-application-and-user-group-relationships/zpa-application-user-group-relationships-download-summary-view.png)