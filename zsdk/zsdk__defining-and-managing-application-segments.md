# Defining and Managing Application Segments
Source: https://help.zscaler.com/zsdk/defining-and-managing-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1508986.pdf

When defining an application within an application segment, you can:
- [Define applications individually](/zpa/about-application-access#AboutApplicationDefinitions) or [enable application discovery](/zpa/about-application-discovery).
- Specify the [server groups](/zsdk/about-server-groups) hosting the applications.
- Specify the [App Connector groups](/zsdk/about-app-connector-groups) that have access to those server groups.
[]Defining Application Segments
You define an application segment by [adding an application segment](#def-add) or [copying an application segment](#def-copy).
Each application segment is defined using the following configuration steps:
- [Step 1: Define Applications](#define-apps)
- [Step 2: Segment Group](#segmentgroup)
- [Step 3: Server Groups](#servergroups)
- [Step 4: Servers](#server)
- [Step 5: Review](#review)
- [Step 6: Policies](#policies)
Managing Application Segments
To manage application segments on the **Defined Application Segments** page (Resource Management > Application Management > Application Segments > Defined Application Segments), you can:
- [Add an application segment.](#add)
- [Copy an application segment.](#copy)
- [Edit an application segment.](#edit)
- [Delete an application segment.](#delete)
Limitations & Considerations
When defining application segments:
- You can define up to 6,000 application segments. To learn more, see [Ranges & Limitations](/zsdk/ranges-limitations).
- If you select a server group that has [Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) enabled, your application segment configuration skips the Servers step and goes to the Review step because the server group automatically discovers the server. After your application segment is defined, your application segment automatically finds the respective server based on the server group. To learn more, see [Managing Server Groups](/zsdk/managing-server-groups).
- If you select multiple server groups when editing, only one server group is saved. This is because multiple server groups mapped to the same application segment can cause the console to disconnect.
- If an application segment is referenced in a segment group and has a policy configured, the delete action is unavailable. An admin must manually review and remove the link to the policy to successfully delete the application segment.
- If there are required fields missing, the Incomplete Configuration** **icon (![ZSDK-SegmentGroup-incompleteicon.png](/downloads/zsdk/application-management/managing-application-segments/ZSDK-SegmentGroup-incompleteicon.png)
) appears next to the missing item in the application segment.
- There are some fields that are recommended to be left to their default setting (e.g., deselected, disabled). These fields do not impact application segments at this time, regardless of whether you choose to select or enable them.
[][]
-
Click **Add Application Segment**.
The **Add Application Segment** window appears.
-
In the **Add Application Segment** window, configure the following as indicated in the [configuration steps](#steps):
- [Define Applications](#define-apps)
- [Segment Group](#segmentgroup)
- [Server Groups](#servergroups)
- [Servers](#server)
- [Review](#review)
- [Policies](#policies)
[See image.](#img_addapplicationsegment)
- Click **Save**.
[][]
-
Locate the application segment you want to modify and click the **Copy **icon.
The **Add Application Segment** window appears.
-
In the **Add Application Segment** window, configure the following as indicated in the [configuration steps](#steps):
- [Define Applications](#define-apps)
- [Segment Group](#segmentgroup)
- [Server Groups](#servergroups)
- [Servers](#server)
- [Review](#review)
- [Policies](#policies)
[See image.](#img_copyapplicationsegment)
- Click **Save**.
[]
-
Locate the application segment you want to modify and click the **Edit **icon.
The **Edit Application Segment** window appears.
-
On the **Application and Ports Configuration** tab, modify the fields as necessary.
[See image.](#img_editapplicationsegment)
-
Click **Next**.
If you click **Save**, the application segment configuration is saved and then the **Edit Application Segment** window exits.
-
On the **General Information** tab, modify any fields as necessary as described in the [General Information step](#generalinfo).
If you select multiple server groups when editing, only one server group is saved. This is because multiple server groups mapped to the same application segment can cause the console to disconnect.
[See image.](#img_editapplicationsegment_generalinfo)
- Click **Save**.
[]
-
Locate the application segment you want to modify and click the **Delete **icon.
The **Confirm: Delete Action** window appears.
-
Click **Delete** to confirm the deletion.
[See image.](#img_deleteapplicationsegment)
[]
-
On the **Define Applications** tab, provide the necessary details for the following sections:
- [][General Information](#define-generalinfo)
- [Applications](#define-applications)
- [Client Connector Access](#define-clientconnector)
- [Common Configuration](#define-cmnconfig)
[See image.](#img_define-apps)
- Click **Next**.
[]
- **Name**: Enter a name for the application segment. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Enable the application segment. If **Disabled**, the defined applications within the application segment are inaccessible to users.
- **Disaster Recovery**: Enable to designate the defined application segment for [disaster recovery](/zsdk/understanding-disaster-recovery). Application segments that are designated for disaster recovery bypass the ZSDK cloud to ensure business continuity in the event of a disaster scenario. Disaster recovery is disabled by default.
- **Source IP Anchor**: (Optional) Leave as **Disabled**.
- **Description**: (Optional) Enter a description.
[]
-
Enter an FQDN, IP address, local domain, or a wildcard domain (e.g., *.safemarch.com) associated with the application. You can't define an application with hyphenated IP address ranges (e.g., 192.168.0.1-10).
You can define the application with a wildcard only (i.e., *), but this should be the only application in the application segment. You can't define an application this way unless approved by Zscaler. Contact Zscaler Support for more information.
The following guidelines apply to configuring FQDNs:
- For some applications, the domain name might be the same as the server name (e.g., RDP and file servers).
- For applications that users access using hostnames (e.g., DFS), ensure that you [configure DNS search suffixes](/zpa/about-applications/dnsDomains) so that ZSDK can automatically add the search domain to the hostname.
To learn more, see [Defining an Application](/zpa/about-application-access#AboutApplicationDefinitions) and [Configuring Application Discovery](/zpa/about-application-discovery#config_appdiscovery).
- **Browser Access**: Leave as deselected.
[]
- **Default Port Ranges**: Enter the port ranges to set as the default for the application segment.
- **TCP Keepalive**: Leave as blank.
-
**TCP Port Ranges**: Enter the TCP port ranges that can be used to access the application.
For example, if you want to specify the port range 80 to 90, for **From...**, enter `80`, and for **To...**, enter `90`. If you only want to specify one port, you can enter the same number (e.g., `80`) for **From...** and **To...**.
Click **Add More** to add more TCP port ranges.
-
**UDP Port Ranges**: Enter the UDP port ranges that can be used to access the application.
For example, if you want to specify the port range 90 to 94, for **From...**, enter `90`, and for **To...**, enter `94`. If you only want to specify one port, you can enter the same number (e.g., `90`) for **From...** and **To...**.
Click **Add More** to add more UDP port ranges.
Zscaler recommends excluding DNS traffic (port 53) from TCP and UDP port ranges.
- **Double Encryption**: Leave as **Disabled**.
- **Bypass**: From the drop-down menu, ensure that **Use Client Forwarding Policy** is selected by default.
- **ICMP Access**: Leave as **Disabled**.
- **Bypass during Reauthentication**: Leave as **Disabled**.
[]
-
**Health Reporting**: Choose whether the App Connector reports the health status of all applications within an application segment continuously (**Continuous**), while a user is accessing it (**On Access**), or not at all (**None**). The default setting is **On Access**. You can see the status of the application on the [Health dashboard](/zpa/about-dashboard/health). To learn more, see [Understanding Health Reporting](/zpa/understanding-health-reporting).
You can't choose **Continuous** health reporting for applications configured with more than 10 ports or if any of the applications in the application segment are defined with only a wildcard (e.g., *). Additionally, if an application has client hostname validation enabled to facilitate client-to-client remote assistance, then the application is not shown on the Health dashboard. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
- **Client Connector can receive CNAME**: Choose whether App Connectors can resolve CNAME records. By default, this is enabled, and Zscaler Client Connector receives CNAME DNS records from the App Connector. Disabling it means App Connectors do not send CNAME DNS records.
-
**App Connector Selection Method**: Choose **Closer to Application** if you prefer the App Connector that is closest to the application to be selected. By default, ZSDK chooses the App Connector as closest to the user (**Closer to User**). After you make a selection, ZSDK selects an App Connector that has the shortest round-trip time towards the requested application.
This setting supports only TCP applications. The limit for the number of targets that check the health of the defined applications at the App Connector is 6,000. If this limit is exceeded, then the **Health Reporting** of the application is set to **None**, and a random selection of App Connectors is chosen.
If **Health Reporting** is set to **None**, the **App Connector Selection Method** feature cannot be enabled and an error message appears.
[][]
You must identify the segment group to which this application segment belongs. Placing the application segment in a segment group allows you to configure user [access policies](/zsdk/about-access-policy) based on that group.
On the **Segment Group** tab, choose one of the following options, and configure the group accordingly:
- [Select Segment Group](#selectappgroup)
- [Add Segment Group](#createappgroup)
To learn more, see [About Segment Groups](/zsdk/about-segment-groups).
[]
-
Choose an existing segment group from the drop-down menu.
You can search for a specific group or click **Clear Selection** to remove any selections.
[See image.](#img_selectappgroup)
- Click **Next**.
[]
-
Enter the following information:
- **Name**:** **Enter a name for the segment group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description of the segment group.
- **Status**: Set to **Enabled**.
[See image.](#img_createappgroup)
- Click **Next**.
[][]
You must identify the server groups in your enterprise data center that host the applications you've defined.
On the **Server Groups** tab, choose one of the following options to configure the server group accordingly:
- [Select Server Group](#selectservergroup)
- [Add Server Group](#createservergroup)
If you select or add a server group with [Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) enabled, the **Servers** step is no longer required because the server group automatically discovers the server.
To learn more, see [About Server Groups](/zsdk/about-server-groups).
[]
-
Ensure the **Server Group Type** is set to **App Connector**.
[See image.](#img_selectsevergroup)
-
Choose an existing server group from the drop-down menu.
You can search for a specific group. Click **Clear Selection** to remove any selections.
- Click **Next**.
You can opt to **Skip** if you want to enable client-to-client remote assistance. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
[]
-
On the **Add Server Group** tab:
- **Name**:** **Enter a name for the server group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description for the server group.
- **Status**:** **Set to **Enabled**.
- **Dynamic Server Discovery**: If enabled, ZSDK automatically discovers the appropriate servers for applications as users request the applications. If disabled, you must manually add defined servers to the server group.
- **Connector Type**: Leave as **App Connector**.
- **App Connector Groups**: Select the App Connector groups with access to the enterprise data center containing the application servers, and click **Done**. You can search for a specific group, or click **Clear Selection** to remove any selections. App Connector groups must be associated with applications that the App Connectors can access (i.e., only assign App Connectors to applications that the App Connector is capable of reaching). ZSDK selects the closest App Connector given the location of the user and the App Connector-to-application latency.
[See image.](#img_addservergroup)
- Click **Next**.
[]
If you select or add a server group with [Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) enabled, the **Servers** tab no longer appears and is no longer required because the server group automatically discovers the server.
You must add servers to the server group you created. On the **Servers **tab, choose one of the following options, and configure the server accordingly:
- [Select Server](#selectserver)
- [Add Server](#addserver)
To learn more, see [About Servers](/zsdk/about-servers).
-
[]Choose one or more existing servers from the drop-down menu, and click **Done**. You can search for a specific group or click **Clear Selection** to remove any selections. If you selected an existing server group in the previous step, then any servers within that group automatically populate this field.
[See image.](#img_selectserver)
- Click **Next**.
[]
-
Click **Add Server**:
- **Name**: Enter a name for the server. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description of the server.
- **Status**: Set to **Enabled**.
- **Domain or IP Address**: Enter an FQDN or an IP address for the server.
- **Server Groups without DSD**: Select server groups. Only server groups that have Dynamic Server Discovery (DSD) are displayed.
[See image.](#img_addserver)
- Click **Next**.
[]
- On the **Review** tab, review your application segment configuration. Click **Previous** if you need to edit the configuration fields.
[See image.](#img_review)
- Click **Save**.
[]
On the **Policies** tab, view a list of access policies that are currently applied to the applications defined within the application segment.
[See image.](#img_policy)
- If you need to add new or modify existing policies, click **Edit Policy**. To learn more, see [About Access Policy](/zsdk/about-access-policy) and [Managing Access Policies](/zsdk/managing-access-policies).
- If you do not need to make any policy changes, click **Cancel**. This saves your newly configured application segment.
[]
![Add Application Segment](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-ApplicationSegments-DefinedApplications-2.png)
[]
![Copy Application Segment](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-ApplicationSegments-DefinedApplications-Copy-2.png)
[]
![Edit Application Segment](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-EditApplicationSegments-.png)
[]
![Delete Application Segment](/downloads/zsdk/application-management/managing-application-segments/ZSDK-DeleteApplicationSegment.png)
[]
![Edit Application Segment - General Information](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-EditApplicationSegments-GeneralInformation-1.png)
[]
![Define Applications Tab](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-ApplicationSegments-DefinedApplications-1.png)
[]
![Select Segment Group](/downloads/zsdk/application-management/managing-application-segments/ZSDK-SegmentGroup-Select.png)
[]
![Add Segment Group](/downloads/zsdk/application-management/managing-application-segments/ZSDK-SegmentGroup-Add.png)
[]
![Server Group Type](/downloads/zsdk/application-management/managing-application-segments/ZSDK-SegmentGroup-SelectServerGroupType.png)
[]
![Select Existing Server](/downloads/zsdk/application-management/managing-application-segments/ZSDK-SelectServer.png)
[]
![Add New Server](/downloads/zsdk/application-management/managing-application-segments/ZSDK-AddServer.png)
[]
![Add Server Group](/downloads/zsdk/applications/application-management/defining-and-managing-application-segments/ZSDK-ServerGroupAdd.png)
[]
![Review](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-ApplicationSegment-Review.png)
[]
![Policies](/downloads/zsdk/application-management/managing-segment-groups/ZSDK-Application-Policy.png)