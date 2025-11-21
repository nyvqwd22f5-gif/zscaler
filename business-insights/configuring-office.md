# Configuring an Office
Source: https://help.zscaler.com/business-insights/configuring-office
PDF: https://help.zscaler.com/pdf/com/en/1490951.pdf

Configuring offices for your organization helps you group various [Zscaler Internet Access (ZIA) locations](/zia/about-locations), inferred IP addresses, and new IP addresses to specific office locations. These configured offices are listed and managed on the [Offices](/business-insights/about-offices) page. This helps to generate more accurate workplace insights by consolidating office traffic to the respective offices.
To configure an office:
- Go to **Workplace** > **Offices and Locations **> **Discovered Locations** or **Offices**.
-
Click **Add Office**.
The **Add Office** drawer appears.
- In the **Add Office** drawer:
- **Office Name**: Enter a name for the office.
- **Add Locations or IP Addresses**: Select the ZIA locations and sublocations that you want to associate with this office. Any new location added to the ZIA Admin Portal is reflected in this field after one day. You can also enter the IP addresses associated with the office. You can enter multiple IP addresses using commas to separate each IP address.
- **Building ID**: Enter a unique building ID for the office building.
- **Address**: Enter the address of the office location. The address autopopulates in the drop-down menu.
- **Capacity**: Enter the number of employees the office can accommodate. This value helps calculate the occupancy of the office.
- **Assigned Headcount**: Enter the number of users that you want to assign to the office. This value helps calculate the attendance metrics for the office.
- **Site ID**: Enter the site ID assigned to the office.
- **Size in Sq Ft**: Enter the size of the office in square feet.
- **Permanent Desks**: Enter the number of permanent desks in the office.
- **Hotel Desks**: Enter the number of hotel desks available in the office.
- **Lease Status**: Specify the office building lease status (leased, owned, etc.).
- **Lease End Date**: Select the date when the office building lease ends, if applicable.
- **Notes**: Add additional notes for the office.
- **Occupancy Goal Percentage**: Enter the occupancy goal. For example, if you set the occupancy to 30, the office is expected to be occupied by at least 30% of its assigned users.
- **Attendance Goal Percentage**: Enter the attendance goal (i.e., 20, 40, 60, 80, or 100 for 1, 2, 3, 4, or 5 days per week, respectively). For example, if the attendance goal is set to 40, the users assigned to the office are expected to come into the office at least 2 days per week.
-
**Tags**: Select the tags that you want to link to this office. You can only manually link a maximum of 8 tags. To learn more, see [About Tag Management](/business-insights/about-tag-management).
[See image.](#add-office-drawer)
-
Click **Save **to configure the office. You can also click **Save and Add Another** to configure another office.
The office is successfully configured. The newly configured office is listed on the [Offices](/business-insights/about-offices) page.
The Business Insights service starts aggregating data for the associated ZIA locations, sublocations, and IP addresses under this office. If you delete the office, the Business Insights service stops data aggregation for the office and initiates the display of metrics for each ZIA location, sublocation, and IP address individually in the Business Insights Admin Portal.
[]![Add Office Drawer](/downloads/business-insights/workplace-insights/workplace-settings/configuring-office/Business-Insights-add-office-drawer_0.png)