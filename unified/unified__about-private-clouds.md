# About Private Clouds
Source: https://help.zscaler.com/unified/about-private-clouds
PDF: https://help.zscaler.com/pdf/com/en/1528631.pdf

Private Clouds are a logical grouping of Private Cloud Controller groups, App Connector groups, Private Service Edge groups for Private Applications, and log receivers. [Configuring a Private Cloud](/unified/configuring-private-clouds) is required for uninterrupted access to applications without any manual intervention via [Business Continuity](/unified/understanding-business-continuity).
Private Clouds provide the following benefits and enable you to:
- Logically group your Private Cloud Controller groups, App Connector groups, Private Service Edge groups for Private Applications, and log receivers to support Business Continuity.
- Configure certificate renewal threshold for enrollment certificates of associated App Connectors, Private Service Edges for Private Applications, and Private Cloud Controllers before expiration.
Private Clouds and App Connectors establish the control channel to Private Cloud Controllers within the same Private Cloud.
About the Private Clouds Page
On the Private Clouds page (Infrastrucutre > Private Access > Business Continuity > Private Clouds), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/unified/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Private Clouds page to reflect the most current information.
- Filter the information that appears in the table. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
[Add a Private Cloud.](/unified/configuring-private-clouds)
Private Clouds that are managed by Zscaler are read only and cannot be configured. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/unified/understanding-zscaler-managed-business-continuity-cloud).
- Expand all rows in the table to see more information about each Private Cloud.
- View a list of all Private Clouds that are configured for your organization. For each Private Cloud, you can see:
- **Name**: The name of the Private Cloud. When expanded, the following information is displayed depending on the Private Cloud:
- **Status**: Indicates whether the Private Cloud is enabled or disabled.
- **Description**: The description of the Private Cloud, if available.
- **App Connector Groups**: The App Connector groups associated with the Private Cloud.
- **Private Cloud Controller Groups**: The Private Cloud Controller groups associated with the Private Cloud.
- **Private Service Edge Groups**: The Private Service Edge groups for Private Applications associated with the Private Cloud.
- **Log Receivers**: The log receivers associated with the Private Cloud.
- **Status**: Indicates whether the Private Cloud is enabled or disabled.
-
**Certificate Renewal Threshold**: Specifies the number of days before the certificate expires to automatically renew the enrollment certificate for Private Cloud Controllers, App Connectors, and Private Service Edges for Private Applications.
The **Certificate Renewal Threshold** cannot be a value greater than 180 days or less than 30 days.
- **Force Business Continuity Mode**: Indicates whether Force Business Continuity is enabled or disabled.
- [Edit the configuration of a Private Cloud.](/unified/editing-private-clouds)
-
Delete the Private Cloud.
Private Clouds that are managed by Zscaler are read only and cannot be edited or deleted. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/unified/understanding-zscaler-managed-business-continuity-cloud).
- [Modify the columns displayed in the table.](/unified/using-tables)
- Display more rows or a different page of the table.
![Viewing and Managing Private Clouds on the Private Clouds Page](/downloads/unified/infrastructure/private-applications/business-continuity-management/private-clouds/about-private-clouds/experience-center-private-clouds.png)