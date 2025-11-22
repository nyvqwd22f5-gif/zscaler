# About User Portal Links
Source: https://help.zscaler.com/unified/about-user-portal-links
PDF: https://help.zscaler.com/pdf/com/en/1492401.pdf

After you [create a user portal](/unified/configuring-user-portals) for your organization, you can add links to any applications that your employees and partners are authorized to access.
User portal links provide the following benefits and enable you to:
- Allow users to view the private applications they’ve been granted access to from access policies. The applications can be accessed via Browser Access or Zscaler Client Connector.
- Provide users a list of static links that they can access from a single user portal, such as providing access to the HR system or payroll application.
There are two types of links you can add to your user portals:
- Web: Users can view and click on these links to launch an application. This includes Browser Access-enabled applications, web applications set up for Zscaler Client Connector access, and public Software as a Service (SaaS) web sites.
- Display: Users can view these links, but they cannot click on them to launch the application in-browser. These links are associated with internal applications that can only be accessed using Zscaler Client Connector.
If a user is connecting via Zscaler Client Connector, then they will see links for applications that they have access to from all devices that are currently connected to Private Applications. However, access policy will restrict access to an application based upon rule criteria.
For example, you could have an access policy rule that allows a user to access the "HR Application" on their Windows device, but have another rule that allows them to access the "Sales Application" on their macOS device (taking into consideration device posture and trusted networks for this device). In this example, the user will see links for the "HR Application" and "Sales Application" on the user portal, but they will only be able to access an application if they are using the proper device. To learn more, see [About Access Policy](/unified/about-access-policy) and [About Device Posture](/unified/about-device-posture-profiles).
About the Portal Links Page
On the Portal Links page (Policies > Access Control > Clientless > Portal Links), you can do the following:
- By default, **All** links available are displayed. Using the drop-down menu you can filter the list to show links for a specific user portal.
- Expand all of the rows in the table to see more information about each link.
- [Add links to a user portal.](/unified/configuring-user-portal-links)
- View a list of all links that were configured. For each link, you can see the following:
- **Name**: The name of the link. When expanded, the following information is displayed:
- **User Portal**: The URL for the user portal the link is display on.
- **Logo/Favicon**: The logo/favicon for the link, if available.
- **Description**: The description for the link, if available.
- **Display on Portal**: Indicates if the link is enabled and displayed on a user portal.
- **URL**: The user portal name.
- Filter the information that appears in the table. By default, no filters are applied.
- Copy an existing link configuration to create a new link.
- [Edit an existing link on a user portal.](/unified/editing-user-portal-links)
- Delete a link.
![Viewing and managing user portal links within the Portal Links page](/downloads/unified/policies/private-applications/access-control/clientless/user-portal/about-user-portal-links/unified-user-portal-links-page.png)