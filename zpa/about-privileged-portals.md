# About Privileged Portals
Source: https://help.zscaler.com/zpa/about-privileged-portals
PDF: https://help.zscaler.com/pdf/com/en/1485096.pdf

[Watch a video about Privileged Portals.](https://fast.wistia.net/embed/iframe/cezvq8xi26)
When a user clicks on a privileged portal, they are taken to the Privileged Remote Access (PRA) Portal. You need to create privileged portals before you can create privileged consoles, as the privileged consoles need to be assigned to existing privileged portals.
Privileged portals provide the following benefits and enable you to:
- Create a privileged portal that shows your end user all the privileged consoles they can access based on the configured access policies.
- Manage the notification banner message that is shown to users at the top of the Privileged Remote Access portal after login.
- Manage the certificate that is used by the ZPA infrastructure when an end user accesses a privileged portal.
About the Privileged Portals Page
On the Privileged Portals page (Resource Management > Privileged Remote Access > Privileged Portals), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Privileged Portals page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
If you are using a [Microtenant](/zpa/about-microtenants), then the **Microtenant Ownership Type** filter is available. By default, the **Configured within Microtenant** filter option is applied to show the privileged portals configured within that specific Microtenant. The options for the filter are based on access type (**Global** and **Configured within Microtenant**). The **Global** option filters the information in the table that is configured within the Default Microtenant. The only available operator for this filter type is **Equals**.
- [Add a new privileged portal](/zpa/configuring-privileged-portals).
- View a list of all the privileged portals that are configured for your organization. For each privileged portal, you can see:
- **Name**: The name of the privileged portal.
- **Description**: The description for the privileged portal, if available.
- **Notification Banner Display Text**: The notification message displayed in the privileged portal's banner, if enabled.
- **Portal Server Certificate**: The [Browser Access (web server) certificate](/zpa/about-browser-access-certificates) associated with the privileged portal.
- **Canonical Name (CNAME)**: The canonical name associated with the Privileged Remote Access portal. You can click the **Copy** icon to copy the CNAME record to your clipboard.
- **Status**: Indicates that the privileged portal is enabled or disabled.
- **URL**: The privileged portal link that end users can access to view the Privileged Remote Access portal.
- **Notification Banner**: Indicates that the notification banner for the privileged portal is enabled or disabled.
- Expand all rows in the table to see more information about each privileged portal.
- [Edit an existing privileged portal](/zpa/editing-privileged-portals).
- Delete an existing privileged portal.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Privileged Approvals](/zpa/about-privileged-approvals) page to add new approvals or manage existing approvals.
- Go to the [Privileged Consoles](/zpa/about-privileged-consoles) page to add new consoles or manage existing consoles.
- Go to the [Privileged Credentials](/zpa/about-privileged-credentials) page to add new credentials or manage existing credentials.
![Privileged Portals page within ZPA Admin Portal](/downloads/zpa/privileged-remote-access-management/privileged-portals/about-privileged-portals/Privileged%20Portals%20page%20w%20steps_0.png)