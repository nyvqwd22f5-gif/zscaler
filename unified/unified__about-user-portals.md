# About User Portals
Source: https://help.zscaler.com/unified/about-user-portals
PDF: https://help.zscaler.com/pdf/com/en/1492386.pdf

User portals provide visibility to authorized applications for your organization's employees and partners. From a user portal, your users can:
- View all applications they are allowed to access.
- Launch web applications directly from the portal. This includes Browser Access-enabled applications, web applications set up for Zscaler Client Connector access, and public Software-as-a-Service (SaaS) websites.
- Download the Zscaler Client Connector.
For example, when you configure a user portal (e.g., portal.corp.com) the following process is applied:
- A CNAME (e.g., pcname.corp.com) is generated that must be published to your public DNS.
- When a user tries to access the user portal, their browser resolves the portal's domain name to an IP address for Private Applications.
- Prior to accessing the portal, the user is prompted to authenticate against the identity provider (IdP) configured for their organization.
- After the user authenticates successfully, the user portal and it's associated portal links are served. The user can only view portal links to applications that they are allowed to access.
About the User Portals Page
On the User Portals page (Policies > Access Control > Clientless > User Portals), you can do the following:
- [Add a user portal.](/unified/configuring-user-portals)
- View a list of all user portals that were configured. For each portal, you can see the following:
- **Name**: The name of the user portal. When expanded, the following information is displayed:
- **Description**: The description for the portal, if available.
- **Notification Banner Display Text**: The notification message displayed in the portal's banner, if enabled.
- **Portal Server Certificate**: The [Browser Access (web server) certificate](/unified/about-web-server-certificates) associated with the portal.
- **Canonical Name (CNAME)**: The canonical name associated to the user portal. You can click the **Copy** icon to copy the CNAME record to your clipboard.
- **Status**: Indicates that the user portal is enabled or disabled.
- **URL**: The URL that users access to view the portal. You can click the **Link **icon to open the portal in a new browser tab.
- **Notification Banner**: Indicates that the notification banner for the user portal is enabled or disabled.
- [Edit an existing user portal.](/unified/editing-user-portals)
- Delete a user portal.
- Expand all of the rows in the table to see more information about each user portal.
![Viewing and managing user portals in the User Portals page](/downloads/unified/policies/private-applications/access-control/clientless/user-portal/about-user-portals/unified-user-portals-page.png)