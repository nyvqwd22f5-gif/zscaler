# Viewing Offices and Locations on a Map
Source: https://help.zscaler.com/business-insights/viewing-offices-and-locations-map
PDF: https://help.zscaler.com/pdf/com/en/1486506.pdf

This article explains the data displayed on the Offices and Locations page (Workplace > Offices and Locations > Map) in the Map view. Additionally, you can view the metrics on this page as a list or chart. To learn more, see [About Offices and Locations](/business-insights/about-offices-and-locations) or [Viewing Offices and Locations in a Chart](/business-insights/viewing-offices-and-locations-chart).
To analyze the data for a specific data type or time frame, use the following filters:
- **Export as PDF**: Download the data on the page as a PDF file.
- **Time Range**: View data for the last 7 days, a week, a month, or 3 months, then choose the week, month, or 3 months from the right pane. The data aggregation for the custom week, month, or quarter might take some time to process.
- **Type**: The type of workplace (**Offices** or **Inferred Locations**). For **Geolocation**, select the workplaces based on the type selected. Business Insights automatically assigns names for inferred location workplaces that are based on IP addresses and retains the name assigned in the ZIA Admin Portal for [ZIA location](/zia/about-locations)-based workplaces. You can only select to view data for either the configured offices or inferred locations at one time.
-
**Days**: Specific days from the filtered time frame. Enable **Custom Dates **to select custom dates to include or exclude from the insights. By default, Saturdays and Sundays are excluded from the metrics.
[See image.](#days-filter)
- **Departments **or** Divisions**: The department filter is available unless you have at least one department mapping to a division on the [Department Mapping](/business-insights/about-department-mapping) page.
- **Departments**: The departments within your organization. This data is mapped from the ZIA Admin Portal SCIM. If the values are inaccurate, contact a ZIA admin.
- **Divisions**: The division that maps related departments.
- **User Types**: The type of users visiting your organization. Selecting user types doesn't filter the data unless you have defined these user types for your organization in Business Insights. To enable this filter, contact Zscaler Support.
- Enable the **Show ZIA Sub-locations** toggle to view ZIA sub-locations in the list. This option is available when you filter the data for inferred location-based workplaces.
Map View
Switch between **Geography** and **Remote User Density** to view the following insights:
- [Geography](#geography)
- [Remote User Density](#density)
[]View the distribution of workplaces across the globe. You can zoom in and out using your mouse or the icons at the bottom-right corner. Click a workplace to view:
- The name of the workplace.
- The city, state or province, and country where the workplace is located.
- The type of workplace, whether a configured office or inferred location.
- **Average Attendance**: The average attendance for the workplace for the filtered time frame.
- **Average Occupancy**: The average occupancy for the workplace for the filtered time frame.
- **See Details**: Click to view additional details for the workplace. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace).
If you don't see a configured office on the map, metadata for that office is missing. Make sure you specify the city, state or province, and country information when configuring offices to locate the configured office on the map.
You can only select to view data for either the configured offices or inferred locations at one time.
[See image.](#geography-tab)
[]View locations across the globe for remote users. Zoom in and out using your mouse or the icons at the bottom-right corner. You can view:
- The total number of remote users across the globe.
- **Potential Sites Opportunities**: A list of cities with the number and percentage of remote users where you can consider opening an office.
- The total number of remote users working from the country by hovering over a country.
- Countries with darker shade signify more remote users compared to lighter-shaded countries with fewer remote users.
-
Workplaces that show the following information when you hover over them:
- The name of the workplace.
- The city, state or province, and country where the workplace is located.
- The type of workplace, whether a configured office or inferred location.
- **Average Attendance**: The average attendance for the workplace for the filtered time frame.
- **Average Occupancy**: The average occupancy for the workplace for the filtered time frame.
Click on the workplace to view additional details. To learn more, see [Analyzing a Workplace](/business-insights/analyzing-workplace).
[See image.](#remote-user-density)
[]![Geography Tab in Map View](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-map/Business-Inisghts-Offices-Locations-Map-Geography-Tab.png)
[]![Remote User DensityTab](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-map/Business-Inisghts-Offices-Locations-Map-Remote-User-Density-Tab.png)
[]![Days Filter](/downloads/business-insights/workplace-insights/viewing-offices-and-locations-map/Business-Inisghts-Workplace-Days-Filter.png)