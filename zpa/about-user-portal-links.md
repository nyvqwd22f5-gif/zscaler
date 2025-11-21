# About User Portal Links
Source: https://help.zscaler.com/zpa/about-user-portal-links
PDF: https://help.zscaler.com/pdf/com/en/1484321.pdf

After you [create a user portal](/zpa/configuring-user-portals) for your organization, you can add links to any applications that your employees and partners are authorized to access.
User portal links provide the following benefits and enable you to:
- Allow users to view the private applications they’ve been granted access to from access policies. The applications can be accessed via Browser Access, Isolation, or Zscaler Client Connector.
- Provide users a list of static links that they can access from a single user portal, such as providing access to the HR system or payroll application.
There are two types of links you can add to your user portals:
- Web: Users can view and click on these links to launch an application. This includes Browser Access-enabled applications, web applications set up for Zscaler Client Connector access, and public Software as a Service (SaaS) web sites.
- Display: Users can view these links, but they cannot click on them to launch the application in a browser. These links are associated with internal applications that can only be accessed using Zscaler Client Connector.
If a user is connecting to ZPA via Zscaler Client Connector, then they see links for applications that they have access to from all devices that are currently connected to ZPA. However, an access policy restricts access to an application based upon rule criteria.
For example, you could have an access policy rule that allows a user to access the HR Application on their Windows device, but have another rule that allows them to access the Sales Application on their macOS device (taking into consideration device posture and trusted networks for this device). In this example, the user sees links for the HR Application and Sales Application on the user portal, but they can only access an application if they are using the proper device. To learn more, see [About Access Policy](/zpa/about-access-policy) and [About Device Posture Profiles](/zscaler-client-connector/about-device-posture-profiles).
About the Portal Links Page
On the Portal Links page (Resource Management > User Portal > Portal Links), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Portal Links page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add links to a user portal.](/zpa/configuring-application-links-user-portals)
- By default, all available links are displayed. Click the drop-down menu to filter the list and show links for a specific user portal.
- Expand all of the rows in the table to see more information about each link.
- View a list of all links that were configured. For each link, you can see:
- **Name**: The name of the link. When expanded, you can see:
- **User Portal**: The URL for the user portal the link is displayed on.
- **Logo/Favicon**: The logo or favicon for the link, if available.
- **Description**: The description for the link, if available.
- **Display on Portal**: Indicates if the link is enabled and displayed on a user portal.
- **URL**: The user portal name.
- Copy an existing link configuration to create a new link.
- [Edit an existing link on a user portal.](/zpa/editing-application-links)
- Delete a link.
- Modify the columns displayed in the table.
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [User Portals](/zpa/about-user-portals) page to add new user portals or manage existing portals.
- Go to the [Client Connector Download Links](/zpa/viewing-and-managing-zscaler-client-connector-download-links) page to view or update your Zscaler Client Connector download links for each OS.
![Viewing and managing application links](/downloads/zpa/user-portal/about-user-portal-links/zpa-portal-links-page-react.png)