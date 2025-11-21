# About ZPA Private Service Edges
Source: https://help.zscaler.com/zpa/about-zpa-private-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1484466.pdf

[Watch a video about ZPA Private Service Edges.](https://fast.wistia.net/embed/iframe/476cwkzro2)
ZPA Private Service Edges are single-tenant instance brokers that provide the functionality of a ZPA Public Service Edge in an organization’s environment. Your organization hosts them either within your site or on a cloud service, but Zscaler manages them. On the other hand, ZPA Public Service Edges are deployed in Zscaler data centers around the world. To learn more, see [Understanding Private Service Edges](/zpa/understanding-service-edges).
As with a ZPA Public Service Edge, a ZPA Private Service Edge manages the connections between Zscaler Client Connector and App Connectors. It registers with the ZPA Cloud. This allows a ZPA Private Service Edge to download the relevant policies and configurations so it can enforce all ZPA policies. It also caches path selection decisions.
ZPA Private Service Edges provide the following benefits and enable you to:
- Implement Zero Trust Network Access (ZTNA) for on-premises users.
- Securely access applications when ZPA Public Service Edges in data centers are not conveniently located between users and the applications they need to reach.
- Ensure business continuity and continued access to critical apps during disaster events.
- Keep application data traffic local to help meet compliance and regulatory requirements.
ZPA Private Service Edges can be deployed in several forms. Zscaler distributes images for deployment in enterprise data centers and local private cloud environments such as VMware.
- [List of platforms supported by ZPA](#supportedse)
Before you begin, see [ZPA Private Service Edges Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites), which provides detailed information on virtual image (VM) sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
Configuring ZPA Private Service Edges involves two main tasks:
- [Adding ZPA Private Service Edges](/zpa/configuring-service-edges) using the ZPA Admin Portal, which includes obtaining a [ZPA Private Service Edge Provisioning Key](/zpa/about-zpa-service-edge-provisioning-keys).
- [Deploying ZPA Private Service Edges](/zpa/about-deploying-service-edges) on the [supported platform](#supportedse) of your choice.
After a ZPA Private Service Edge is added and deployed, it is displayed on the Private Service Edge page. You can perform additional software management and maintenance tasks after deployment. To learn more, see [Managing Deployed ZPA Private Service Edges](/zpa/managing-deployed-zpa-private-service-edges) and [About ZPA Private Service Edge Software Updates](/zpa/about-service-edge-software-updates).
The ZPA Private Service Edge uses the public IP address of the user who connects to the ZPA Private Service Edge to access private resources. After a user connects to a ZPA Private Service Edge, the location of the user is determined by its public IP address, and then a country-based policy for the mapped country is enforced. To learn more, see [About Access Policy](/zpa/about-access-policy).
If a user connects to a ZPA Private Service Edge with an RFC 1918 IP address, then the location of the ZPA Private Service Edge is used to evaluate policies with country criteria.
If the location of the ZPA Private Service Edge Group is updated for an existing connection, the ZPA Private Service Edge uses the old location until the next time it makes a new connection. Location changes via a GeoIP configuration override are not supported for ZPA Private Service Edges. To learn more, contact Zscaler Support.
[]About the Private Service Edges Page
On the Private Service Edges page (Configuration & Control > Private Infrastructure > Private Service Edge Management > Private Service Edges), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the Private Service Edges page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
-
[Add a new ZPA Private Service Edges](/zpa/configuring-service-edges).
ZPA Private Service Edges that are managed by Zscaler are read only and cannot be configured.
- Expand all the rows in the table to see more information about each ZPA Private Service Edge.
- View a list of all deployed ZPA Private Service Edges. ZPA Private Service Edges that you've added but have not deployed are not listed. For each deployed ZPA Private Service Edge, you can see:
- **Name**: The name of the ZPA Private Service Edge. When expanded, the following information is displayed depending on the defined ZPA Private Service Edge:
- **Description**: The description of the ZPA Private Service Edge, if available.
- **Private Service Edge Group**: The ZPA Private Service Edge group that the ZPA Private Service Edge is a member of.
- **Private Service Edge Host Platform**: The platform that the ZPA Private Service Edge is deployed on (e.g., AWS, ESXi (VMWare).
- **Private Service Edge Host OS**: The run time OS on which the ZPA Private Service Edge is running (e.g., RHEL Linux 9).
- **Private Service Edge Package OS**: The compile time OS on which the .rpm binary is packaged (e.g. Enterprise Linux 7).
- **Last Software Update**: The date and time the ZPA Private Service Edge was last updated to a newer software version.
- **Public Service Edge**: The ZPA Public Service Edge that the ZPA Private Service Edge connects to.
- **Last Connection to Zscaler**: The last time the ZPA Private Service Edge connected to Zscaler.
- **Last Disconnect from Zscaler**: The last time the ZPA Private Service Edge disconnected from Zscaler.
- **Location**: The location where the ZPA Private Service Edge group that the ZPA Private Service Edge belongs to is set up.
- **Public IP**: The public IP address of the ZPA Private Service Edge. Disconnected ZPA Private Service Edges show the last known public IP address.
- **Private IP**: The private IP address of the ZPA Private Service Edge. Disconnected ZPA Private Service Edges show the last known private IP address.
- **Uptime**: The period of time the ZPA Private Service Edge is available for use. Disconnected ZPA Private Service Edges show the value **Not Available**.
- **Enrollment Certificate**: The certificate of the ZPA Private Service Edge used for enrollment.
-
**Supporting Files Upgrade Status**: When enabled, this field indicates the upgrade status and current version of the supporting files used to map the public IP address of the ZPA Private Service Edge to the country where the IP address is registered.
The ZPA Private Service Edge indicates Partial Failure for the Upgrade Status if a supporting file fails to upgrade. The **Information **icon appears next to the supporting file that failed to upgrade. To learn more, see [Troubleshooting ZPA Private Service Edges](/zpa/troubleshooting-zpa-private-service-edges#partialFailure).
​​​​[See image.](#partialFailure)
- **Publish IPs or Domains**: The IP addresses and domains that clients and App Connectors can use to open a connection to the ZPA Private Service Edge. If this is not specified, then the clients and App Connectors try to connect using the Listen IPs.
- **Listen IPs**: The IP addresses that the ZPA Private Service Edge listens on for connection requests from clients and App Connectors only at set addresses. If not configured, the ZPA Private Service Edge listens to all interfaces.
- **Manager Version**: The version of the current ZPA Private Service Edge Manager software. To learn more, see [Understanding the Manager Software](/zpa/about-manager-software).
- **Current Software Version**: The current ZPA Private Service Edge software version.
- **Connection Status**: The status of the ZPA Private Service Edge session.
- **Upgrade Status**: The status of the last ZPA Private Service Edge software update.
- **Status**: Indicates whether the ZPA Private Service Edge is enabled or disabled.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- [Edit the configuration of a deployed ZPA Private Service Edge](/zpa/editing-deployed-service-edge).
-
Delete a deployed ZPA Private Service Edge configuration.
ZPA Private Service Edges that are managed by Zscaler are read only and cannot be edited or deleted.
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [Private Service Edge Groups](/zpa/about-zpa-service-edge-groups) page to manage your ZPA Private Service Edge groups.
- Go to the [Private Service Edge Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys) page to manage your ZPA Private Service Edge provisioning keys.
![Private Service Edges page in the ZPA Admin Portal](/downloads/zpa/private-service-edge-management/private-service-edge/about-zpa-private-service-edges/zpa-about-pse-page_0.png)
- [][Amazon Web Services (AWS)](/zpa/private-service-edge-deployment-guide-amazon-web-services)
- [Docker](/zpa/private-service-edge-deployment-guide-docker)
- [Google Cloud Platform (GCP)](/zpa/private-service-edge-deployment-guide-google-cloud-platform)
- [Linux](/zpa/private-service-edge-deployment-guide-linux)
- Microsoft Azure
- [VMware Platforms](/zpa/private-service-edge-deployment-guide-vmware)
ZPA provides Security Technical Implementation Guide (STIG) images are available for AWS, GCP, Microsoft Azure, and VMware by default. To learn more, see [ZPA Private Service Edge Software by Platform](/zpa/zpa-private-service-edge-software-by-platform).
[]![Version Error for Supporting Files Upgrade Status](/downloads/zpa/private-service-edge-management/private-service-edge-managing-troubleshooting/troubleshooting-zpa-private-service-edges/zpa-supporting-files-upgrade-status-version-error.png)