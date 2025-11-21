# About Private Service Edges for Private Applications
Source: https://help.zscaler.com/unified/about-private-service-edges-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496521.pdf

The Private Service Edges are brokers that are a single-tenant instance that provide the functionality of a Public Service Edge in an organization’s environment. Your organization hosts them either within your site or on a cloud service, but Zscaler manages them. On the other hand, Public Service Edges are deployed in Zscaler data centers around the world. To learn more, see [Understanding Private Service Edges](/unified/understanding-service-edges).
As with a Public Service Edge, a Private Service Edge manages the connections between Zscaler Client Connector and App Connectors. It registers with the Cloud. This allows a Private Service Edge to download the relevant policies and configurations so it can enforce all policies. It also caches path selection decisions.
Private Service Edges provide the following benefits and enable you to:
- Implement Zero Trust Network Access (ZTNA) for on-premises users.
- Securely access applications when Public Service Edges in data centers are not conveniently located between users and the applications they need to reach.
- Ensure business continuity and continued access to critical apps during disaster events.
- Keep application data traffic local to help meet compliance and regulatory requirements.
Private Service Edges can be deployed in several forms. Zscaler distributes images for deployment in enterprise data centers and local private cloud environments such as VMware.
- [List of platforms supported](#supportedse)
Before you begin, see [Private Service Edges Deployment Prerequisites](/unified/private-service-edge-deployment-prerequisites), which provides detailed information on virtual image (VM) sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
Configuring Private Service Edges involves two main tasks:
- [Adding Private Service Edge](/unified/configuring-private-service-edges-private-applications) using the Admin Portal, which includes obtaining a [Private Service Edge Provisioning Key](/unified/about-private-service-edge-provisioning-keys-private-applications).
- [Deploying Private Service Edges](/unified/about-deploying-private-service-edges-private-applications) on the [supported platform](#supportedse) of your choice.
After a Private Service Edge is added and deployed, it is displayed on the Private Service Edge page. You can perform additional software management and maintenance tasks after deployment. To learn more, see [Managing Deployed Private Service Edges for Private Applications](/unified/managing-deployed-private-service-edges-private-applications) and [About Private Service Edge for Private Applications Software Updates](/unified/understanding-private-service-edge-software-upgrades-private-applications).
The Private Service Edge uses the public IP of the user who connects to the Private Service Edge to access private resources. After a user connects to a Private Service Edge, the location of the user is determined by its public IP address, and then a country-based policy for the mapped country is enforced. To learn more, see [About Access Policy](/unified/about-access-policy).
If a user connects to a Private Service Edge with an RFC 1918 IP address, then the location of the Private Service Edge is used to evaluate policies with country criteria.
If the location of the Private Service Edge Group is updated for an existing connection, the Private Service Edge uses the old location until the next time it makes a new connection. Location changes via a GeoIP configuration override are not supported for Private Service Edges. To learn more, contact Zscaler Support.
[]About the Private Service Edges Page
On the Private Service Edge page (Infrastructure > Private Access Components > Private Service Edges), you can do the following:
- Expand all of the rows in the table to see more information about each Private Service Edge.
-
[Add a new Private Service Edges](/unified/configuring-private-service-edges-private-applications).
Private Service Edges that are managed by Zscaler are read only and cannot be configured.
- Refresh the Private Service Edge page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all deployed Private Service Edges. Private Service Edges that you've added, but have not deployed, are not listed. For each deployed Private Service Edge, you can see:
- **Name**: The name of the Private Service Edge. When expanded, the following information is displayed depending on the defined Private Service Edge:
- **Description**: The description of the Private Service Edge, if available.
- **Private Service Edge Group**: The Private Service Edge Group that the Private Service Edge is a member of.
- **Private Service Edges Host Platform**: The platform that the Private Service Edge is deployed on (e.g., AWS, ESXi (VMWare)).
- **Private Service Edges Host OS**: The run time OS on which the Private Service Edge is running (e.g., CentOS Linux 7).
- **Private Service Edge Package OS**: The compile time OS on which the .rpm binary is packaged (e.g. Enterprise Linux 7).
- **Last Software Update**: The date and time the Private Service Edge was last updated to a newer software version.
- **Public Service Edge**: The Public Service Edge that the Private Service Edge connects to.
- **Last Connection to Zscaler**: The last time the Private Service Edge connected to Zscaler.
- **Last Disconnect from Zscaler**: The last time the Private Service Edge disconnected from Zscaler.
- **Location**: The location where the Private Service Edge Group that the Private Service Edge belongs to is set up.
- **Public IP**: The public IP address of the Private Service Edge. Disoconnected Private Service Edges show the last known public IP address.
- **Private IP**: The private IP address of the Private Service Edge. Disoconnected Private Service Edges show the last known private IP address.
- **Uptime**: The period of time the Private Service Edge is available for use. Disoconnected Private Service Edges show the value **Not Available**.
- **Enrollment Certificate**: The certificate of the Private Service Edge used for enrollment.
-
**Supporting Files Upgrade Status**: When enabled, this field indicates the upgrade status and current version of the supporting files used to map the public IP of the Private Service Edge to the country where the IP is registered.
The Private Service Edge indicates Partial Failure for the Upgrade Status if a supporting file fails to upgrade. The **Information **icon appears next to the supporting file that failed to upgrade. To learn more, see [Troubleshooting Private Service Edges for Private Applications](/unified/troubleshooting-private-service-edges-private-applications).
​​​​[See image.](#partialFailure)
- **Publish IPs or Domains**: The IP addresses and domains that clients and App Connectors can use to open a connection to the Private Service Edge. If this is not specified, then the clients and App Connectors try to connect using the Listen IPs.
- **Listen IPs**: The IP addresses that the Private Service Edge listens on for connection requests from clients and App Connectors only at set addresses. If not configured, the Private Service Edge listens to all interfaces.
- **Manager Version**: The version of the current Private Service Edge Manager software. To learn more, see [Understanding the Manager Software](/unified/understanding-manager-software).
- **Current Software Version**: The current Private Service Edge software version.
- **Connection Status**: The status of the Private Service Edge session.
- **Upgrade Status**: The status of the last Private Service Edge software update.
- **Status**: Indicates whether the Private Service Edge is enabled or disabled.
- [Edit the configuration of a deployed Private Service Edge](/unified/editing-deployed-private-service-edge-for-private-applications).
-
Delete a deployed Private Service Edge configuration.
Private Service Edges that are managed by Zscaler are read only and cannot be edited or deleted.
- Go to the [Private Service Edge Groups](/unified/about-private-service-edges-private-applications) page to manage your Private Service Edge groups.
- Go to the [Private Service Edge Provisioning Keys](/unified/about-private-service-edge-provisioning-keys-private-applications) page to manage your Private Service Edge provisioning keys.
![Viewing and managing Private Service Edges in the Admin Portal](/downloads/unified/networking/private-applications/private-service-edge-management/private-service-edge/about-private-service-edges-private-applications/private-service-edges-page.jpg)
- [][Amazon Web Services (AWS)](/unified/app-connector-deployment-guide-amazon-web-services)
- [Microsoft Azure](/unified/service-edge-deployment-guide-aws)
- [Linux](/unified/private-service-edge-deployment-guide-linux)
- [VMware Platforms](/unified/private-service-edge-deployment-guide-vmware-platforms)
[]![Version Error for Supporting Files Upgrade Status](/downloads/zpa/private-service-edge-management/private-service-edge-managing-troubleshooting/troubleshooting-zpa-private-service-edges/zpa-supporting-files-upgrade-status-version-error.png)