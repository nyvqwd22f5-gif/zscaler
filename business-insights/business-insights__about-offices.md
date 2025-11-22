# About Offices
Source: https://help.zscaler.com/business-insights/about-offices
PDF: https://help.zscaler.com/pdf/com/en/1479216.pdf

The Offices page shows the list of offices that you've configured for your organization.
The Offices page provides the following benefits and enables you to:
- Consolidate various [Zscaler Internet Access (ZIA) locations](/zia/about-locations), inferred office IP addresses, and new IP addresses under their corresponding office locations to view accurate office-specific metrics.
- View all your configured offices for your organization.
- View various workplace metrics for each configured office.
- Manage and update office metadata to always generate accurate metrics.
You can view the metrics on this page as a List, Chart, or Map. This article shows the data displayed in the listed form. To understand the data in a map or chart, see [Viewing Offices and Locations in a Map](/business-insights/viewing-offices-and-locations-map) and [Viewing Offices and Locations in a Chart](/business-insights/viewing-offices-and-locations-chart).
An admin account with read-only access to the Business Insights Admin Portal can only view the offices and use the **View** icon to view office configuration details.
About the Offices Page
On the Offices page (Workplace > Offices and Locations > Offices), you can do the following:
- View the metrics on this page as a **List**, **Map**, or **Chart**.
- Download the data on the page as a CSV file.
- Filter the data of the entire page for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
- Filter the insights by **Geolocation**, **Days**, **Departments **or **Division**, **User Types**, or **Tags**. A workplace with an undefined city, state, and country is categorized as Unknown City, State, or Country, respectively. Click **Reset Filters **to remove any applied filters. Selecting **User Types** doesn't filter the data unless you have defined user types for your organization in Business Insights. To enable and use this feature, contact Zscaler Support.
- Search the data in the table by the office name, site ID, or location.
- [Configure an office](/business-insights/configuring-office).
- Select multiple offices for bulk operation (e.g., tagging).
- View a list of configured offices in your organization.
- [View elements for each configured office.](#office-elements)
- [Modify the column menu](/business-insights/using-tables-business-insights).
- Edit a configured office.
-
Link the office to a manual tag, create a new tag category, or go to the [Tag Management](/business-insights/about-tags) page.
[See image.](#tag-drop-down)
- Go to the [Discovered Locations](/business-insights/about-discovered-locations) page to view discovered office network locations.
![Configured Offices Page](/downloads/tech-pubs-drafts/business-insights-draft-articles/about-offices/Business-Insights-Offices-page_0.png)
- []**Name**: The name of the office. If you don't see data for the office, hover over the **Error** icon (![Business-Inisghts-tooltip-icon.png](/downloads/tech-pubs-drafts/business-insights-draft-articles/about-offices-and-locations/Business-Inisghts-tooltip-icon.png)
) next to the office name to see the reason (e.g., the office is not configured correctly, metadata is not added, the office was configured less than 24 hours ago, etc.) for troubleshooting purposes.
- **City**: The city where the office is located.
- **State**: The state or province where the office is located.
- **Country**: The country where the office is located.
- **Attendance**: The attendance at the workplace for the filtered timeframe.
- **Occupancy**: The occupancy of the workplace for the filtered timeframe.
- **Visits Per Day**: The average number of unique visits each day at the workplace.
- **Tags**: The tags linked to the office. To learn more, see [About Tag Management](/business-insights/about-tag-management).
- **Building ID**: The unique building ID assigned to the office building.
- **Site ID**: The ID assigned to the office.
- **Location**: The number of ZIA locations and sublocations assigned to the office. Click the arrow to view all the locations.
- **IP Addresses**: The number of IP addresses linked to the office. Click the arrow to view all the IP addresses.
- **Capacity**: The number of employees the office can accommodate.
- **Assigned Headcount**: The number of users assigned to the office.
- **Size**: The size of the office in square feet.
- **Lease Status**: Indicates whether the office building is leased or owned.
- **Lease End Date**: The date when the office building lease ends.
- **Permanent Desks**: The number of permanent desks in the office.
- **Hotel Desks**: The number of hotel desks available in the office.
- **Address**: The office location address.
- **Notes**: Any notes for the office.
- **Occupancy Goal**: The occupancy goal in percentage for the office. For example, if the occupancy goal is set to 60, the office is expected to be occupied by at least 60% of its assigned users.
- **Attendance Goal**: The attendance goal in percentage for the office (i.e., 20, 40, 60, 80, or 100 for 1, 2, 3, 4, or 5 days per week, respectively). For example, if the attendance goal is set to 40, the users assigned to the office are expected to come into the office at least 2 days per week.
[]![Tag Drop-Down Menu in Configured Offices Page](/downloads/business-insights/workplace-insights/workplace-settings/about-configured-offices/Business-Inisghts-Tagging-Drop-Down.png)