# About User Portals
Source: https://help.zscaler.com/zpa/about-user-portals
PDF: https://help.zscaler.com/pdf/com/en/1484311.pdf

User portals provide visibility to authorized applications for your organization's employees and partners.
User portals provide the following benefits and allow you to:
- View all applications they are allowed to access.
- Launch web applications directly from the portal. This includes Browser Access-enabled applications, web applications set up for Zscaler Client Connector access, and public Software as a Service (SaaS) websites.
- Download Zscaler Client Connector. To learn more, see [What Is Zscaler Client Connector?](/zscaler-client-connector/what-is-zscaler-client-connector)
For example, when you configure a user portal (e.g., portal.corp.com), the following process is applied:
- ZPA generates a CNAME (e.g., pcname.corp.com) that must be published to your public DNS.
- When a user tries to access the user portal, their browser resolves the portal's domain name to an IP address for ZPA.
- Prior to accessing the portal, the user is prompted to authenticate against the identity provider (IdP) configured for their organization.
- After the user authenticates successfully, ZPA serves the user portal and its associated portal links. The user can only view portal links to applications that they are allowed to access.
![Diagram of User Portal Process](/downloads/zpa/user-portal/about-user-portals/About%20User%20Portals%20Diagram.jpg?1610053640)
About the User Portals Page
On the User Portals page (Resource Management > User Portal > User Portals), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the User Portals page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a user portal.](/zpa/configuring-user-portals)
- Expand all of the rows in the table to see more information about each user portal.
- View a list of all user portals that were configured. For each portal, you can see:
- **Name**: The name of the user portal. When expanded, you can see:
- **Description**: The description for the portal, if available.
- **Notification Banner Message Text**: The notification message displayed in the portal's banner, if enabled.
- **Portal Server Certificate**: The [Browser Access (web server) certificate](/zpa/about-browser-access-certificates) associated with the portal.
- **Canonical Name (CNAME)**: The canonical name associated to the user portal. You can click the **Copy** icon to copy the CNAME record to your clipboard.
- **Status**: Indicates that the user portal is enabled or disabled.
- **URL**: The URL that users access to view the portal. You can click the external link icon to open the portal in a new browser tab.
- **Notification Banner**: Indicates that the notification banner for the user portal is enabled or disabled.
- [Edit an existing user portal.](/zpa/editing-user-portals)
- Delete a user portal.
- Modify the columns displayed in the table.
- Display more rows or a different page of the table.
- Open the Zscaler Help Browser and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Portal Links](/zpa/about-user-portal-links) page to add new links for your user portals or manage existing links.
- Go to the [Client Connector Download Links](/zpa/viewing-and-managing-zscaler-client-connector-download-links) page to view or update your Zscaler Client Connector download links for each OS.
![Viewing and managing user portals](/downloads/zpa/user-portal/about-user-portals/zpa-user-portals-page-react.png)