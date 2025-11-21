# About Private Cloud Controllers
Source: https://help.zscaler.com/zpa/about-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1507026.pdf

Private Cloud Controllers behave as a per-tenant controller for users, ZPA Private Service Edges, and App Connectors to leverage when the ZPA cloud is not available or reachable.
Private Cloud Controllers provide the following benefits, and perform the following functionalities:
- Downloads and persists a complete copy of customer configuration and policies.
- Distributes customer configuration and policies to onsite ZPA Private Service Edges and App Connectors in active Business Continuity Mode.
- Acts as an authentication redirection endpoint in active Business Continuity Mode.
- Allows for log streaming to a SIEM in active Business Continuity Mode.
- Redirects users to ZPA Private Service Edges in active Business Continuity Mode.
To provide application access during a global ZPA outage, you must configure, enroll, and maintain Private Cloud Controllers. In addition, to ensure that Business Continuity functions properly, Private Cloud Controllers must run on the same or a later software version as the App Connectors and ZPA Private Service Edges. To learn more, see [Configuring Private Cloud Controllers](/zpa/configuring-private-cloud-controllers).
Private Cloud Controller certificate enrollment is valid for one year. To automatically refresh the certificate enrollment, configure the **Certificate Renewal Threshold** when [adding a Private Cloud](/zpa/configuring-private-clouds).
About the Private Cloud Controllers Page
On the Private Cloud Controllers page (Configuration & Control > Business Continuity > Business Continuity Management > Private Cloud Controllers), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to display the filters.
- Refresh the Private Cloud Controller Controllers page to reflect the most current information.
- Filter the information that appears in the table. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
[Add a Private Cloud Controller.](/zpa/configuring-private-cloud-controllers)
Private Cloud Controllers that are managed by Zscaler are read only and cannot be configured. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
- Expand all rows in the table to see more information about each Private Cloud Controller.
- View a list of deployed Private Cloud Controllers. Private Cloud Controllers that you've added, but have not deployed, are not listed. For each Private Cloud Controller, you can see:
- **Name**: The name of the Private Cloud Controller. When expanded, the following information is displayed depending on the Private Cloud Controller:
- **Description**: The description of the Private Cloud Controller, if available.
- **Status**: Indicates whether the Private Cloud Controller is enabled or disabled.
- **Private Cloud Controller Platform**: The platform that the Private Cloud Controller is deployed on (e.g., AWS).
- **Private Cloud Controller Host OS**: The run time OS on which the Private Cloud Controller is running (e.g., CentOS Linux 7).
- **Private Cloud Controller Package OS**: The compile time OS on which the .rpm binary is packaged (e.g. Enterprise Linux 7).
- **Last Software Update**: The date and time the Private Cloud Controller was last updated to a newer software version.
- **Public Service Edge**: The ZPA Public Service Edge that the Private Cloud Controller connects to.
- **Last Connection to Zscaler**: The last time the Private Cloud Controller connected to Zscaler.
- **Last Disconnect from Zscaler**: The last time the Private Cloud Controller disconnected from Zscaler.
- **Location**: The location where the Private Cloud Controller group that the Private Cloud Controller belongs to is set up.
- **Public** **IP**: The public IP address of the Private Cloud Controller. Disconnected Private Cloud Controllers show the last known public IP address.
- **Private IP**: The private IP address of the Private Cloud Controller. Disconnected Private Cloud Controllers show the last known private IP address.
- **Uptime**: The period of time the Private Cloud Controller is available for use. Disconnected Private Cloud Controllers show the value **Not Available**.
- **Enrollment Certificate**: The certificate of the Private Cloud Controller used for enrollment.
- **Business Continuity SP FQDN**: The Business Continuity Service Provider FQDN. Click the **Copy **icon to copy the Business Continuity Service Provider FQDN.
- **Manager Version**: The version of the current Private Cloud Controller Manager software. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).
- **Current Software Version**: The current Private Cloud Controller software version.
- **Connection Status**: The status of the Private Cloud Controller connection.
- **Upgrade Status**: The status of the last Private Cloud Controller software update.
- **Status**: Indicates whether the Private Cloud Controller is enabled or disabled.
- [Edit the configuration of a deployed Private Cloud Controller.](/zpa/editing-deployed-private-cloud-controller)
-
Delete a deployed Private Cloud Controller.
Private Cloud Controllers that are managed by Zscaler are read only and cannot be edited or deleted. To learn more, see [Understanding Zscaler-Managed Business Continuity Cloud](/zia/understanding-zscaler-managed-business-continuity-cloud).
- [Update the Private Cloud Controller.](/zpa/manually-updating-private-cloud-controller-software)
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Private Cloud Controller Groups](/zpa/about-private-cloud-controller-groups) page to view and manage your Private Cloud Controller groups.
- Go to the [Private Cloud Controller Provisioning Keys](/zpa/about-private-cloud-controller-provisioning-keys) page to view and manage Private Cloud Controller provisioning keys.
- Go to the [Private Clouds](/zpa/about-private-clouds) page to add new Private Clouds or manage existing Private Clouds.
- Go to the [Settings](/zpa/configuring-business-continuity-settings) page to configure the Business Continuity settings.
![Viewing and Managing Private Cloud Controllers](/downloads/zpa/business-continuity-management/private-cloud-controllers/about-private-cloud-controllers/zpa-private-cloud-controllers-page.png)