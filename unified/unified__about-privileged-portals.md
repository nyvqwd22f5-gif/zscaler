# About Privileged Portals
Source: https://help.zscaler.com/unified/about-privileged-portals
PDF: https://help.zscaler.com/pdf/com/en/1492571.pdf

When a user clicks on a privileged portal, they are taken to the Privileged Remote Access portal. You need to create privileged portals before you can create privileged consoles, as the privileged consoles need to be assigned to existing privileged portals.
Privileged portals provide the following benefits and enable you to:
- Create a privileged portal that shows your end user all the privileged consoles they can access based on the configured access policies.
- Manage the notification banner message that is shown to users at the top of the Privileged Remote Access portal after login.
- Manage the certificate that is used by the infrastructure when an end user accesses a privileged portal.
About the Privileged Portals Page
On the Privileged Portals page (Policies > Access Control > Clientless > Privileged Portals), you can do the following:
- Expand all rows in the table to see more information about each privileged portal.
- [Add a new privileged portal](/unified/configuring-privileged-portals).
-
Filter the information that appears in the table. By default, no filters are applied.
If you are using a [Microtenant](/unified/about-microtenants), then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the privileged portals configured within that specific Microtenant. The options for the filter are based on access type (**Global** and **Configured within Microtenant**). The **Global** option filters the information in the table that is configured within the Default Microtenant. The only available operator for this filter type is **Equals**.
- View a list of all the privileged portals that are configured for your organization. For each privileged portal, you can see:
- **Name**: The name of the privileged portal.
- **Description**: The description for the privileged portal, if available.
- **Notification Banner Display Text**: The notification message displayed in the privileged portal's banner, if enabled.
- **Portal Server Certificate**: The [Browser Access (web server) certificate](/unified/about-web-server-certificates) associated with the privileged portal.
- **Canonical Name (CNAME)**: The canonical name associated with the Privileged Remote Access portal. You can click the **Copy** icon to copy the CNAME record to your clipboard.
- **Status**: Indicates that the privileged portal is enabled or disabled.
- **URL**: The privileged portal link that end users can access to view the Privileged Remote Access portal.
- **Notification Banner**: Indicates that the notification banner for the privileged portal is enabled or disabled.
- [Edit an existing privileged portal](/unified/editing-privileged-portals).
- Delete an existing privileged portal.
![Viewing and managing privileged portals within the Privileged Portals page](/downloads/unified/policies/private-applications/access-control/clientless/privileged-remote-access-management/privileged-portals/about-privileged-portals/unified-privileged-portals-page.png)