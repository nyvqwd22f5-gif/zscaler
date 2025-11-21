# Managing App Connector Groups
Source: https://help.zscaler.com/zsdk/managing-app-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1509446.pdf

You can edit or delete App Connector groups from the App Connector Groups page. You can add an App Connector group when you create an App Connector.
To manage your App Connector groups, you can:
- [Add an App Connector group by creating an App Connector.](/zsdk/managing-app-connectors)
- [Edit an App Connector group.](#edit)
- [Delete an App Connector group.](#delete)
Limitations & Considerations
When configuring App Connector groups:
- You can have up to 100 App Connector groups configured. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations).
- You do not need to create a new App Connector group every time you add an App Connector. If the App Connector group to which you want to add a new App Connector already exists, you can assign the App Connector to that group. To learn more, see [Managing App Connectors](/zsdk/managing-app-connectors).
[]
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **App Connector Groups**.
-
Click the **Edit** icon on the App Connector group of your choice.
The **Edit App Connector Group** window appears.
-
In the **Edit App Connector Group** window:
- **Name**: Enter a name for the group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Disable or enable the App Connector group.
- **Description**: (Optional) Enter a description for the App Connector group.
-
**DNS Resolution Option**: Enable the necessary interface for DNS resolution checks. If the App Connectors assigned to that App Connector group should perform DNS resolution checks for applications using only IPv4, select **IPv4**. If the App Connectors assigned to the App Connector group should perform DNS resolution checks for applications using only IPv6, select **IPv6**. If you select **IPv4 and IPv6**, both interfaces can perform resolution checks for applications. The App Connector must have the corresponding interface or interfaces enabled for the DNS resolution checks to work, and the [servers](/zpa/about-servers) hosting your applications must support the selected interface or interfaces. By default, **IPv4 and IPv6** is selected.
Select the **IPv6** option only if you have end-to-end IPv6 support. If you want to use IPv6, make sure your App Connectors are set up for IPv6. To learn more, see [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites) and [Understanding IPv4 and IPv6 Support](/zpa/understanding-ipv4-and-ipv6-support).
- **Disaster Recovery**: When enabled, this designates the App Connector group for [disaster recovery.](/zsdk/understanding-disaster-recovery)
- **Persist Local Version Profile**: Enable if the App Connector group should persist the local version profile. By default, **Disabled** is selected.
- **Version Profile**: Displays the current version profile. The default value is set to **Default**. To learn more, see [Configuring a Version Profile](/zpa/configuring-version-profile).
- **App Connector Software Update Schedule**: Schedule a periodic App Connector software update for the group by selecting the day of the week and start time. You can search for a specific day of the week and start time, or click **Clear Selection** to remove any selections.
- **App Connector Location**: Enter the location where the App Connectors in the group are set up. The map displays the location you've entered. If you click the location marker on the map, the **Latitude**, **Longitude**, and **Location Details** fields are automatically populated.
- **Latitude**: Displays the latitude coordinate.
- **Longitude**: Displays the longitude coordinate.
- **Country Code**: Displays the country code for the location address you’ve entered.
- **Location Details**: Displays the location address you've entered.
[See image.](#img_edit)
- Click **Save**.
[]
- Go to **Configuration & Control** > **Private Infrastructure** > **App Connector Management** > **App Connector Groups**.
-
Click the **Delete** icon on the App Connector group of your choice.
The **Delete Confirmation** window appears.
-
Select the checkbox to confirm the deletion request.
[See image.](#img_delete)
- Click **Delete**.
[]
![Edit App Connector Group](/downloads/zsdk/applications/app-connectors/managing-app-connector-groups/ZSDK-App-Connector-Groups-Edit-2.png)
[]
![Delete App Connector Group](/downloads/zsdk/application-management/app-connectors/managing-app-connector-groups/ZSDK-App-Connector-Groups-Delete.png)