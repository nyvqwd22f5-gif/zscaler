# About Disaster Recovery Private Service Edge Groups
Source: https://help.zscaler.com/zpa/about-disaster-recovery-private-service-edge-groups
PDF: https://help.zscaler.com/pdf/com/en/1485396.pdf

Disaster recovery ZPA Private Service Edge groups are ZPA Private Service Edge groups designated as available for disaster recovery to ensure business continuity in the event of a disaster scenario.
Disaster recovery Private Service Edge groups provide the following benefits and enable you to:
- Ensure business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure.
- Provide users with access to critical ZPA Private Service Edges during a disaster scenario.
After a ZPA Private Service Edge group is designated for disaster recovery, both configuration and binary snapshots are saved in the local configuration files on your ZPA Private Service Edge and are used for backup purposes. The Zscaler cloud maintains up to 15 active configuration snapshots and up to 5 active binary snapshots, and updates both snapshots periodically. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery), [Configuring ZPA Private Service Edges](/zpa/configuring-service-edges#addgroup), and [Managing Configuration and Binary Snapshots](/zpa/managing-disaster-recovery-configuration-and-binary-snapshots).
In the scenario where a ZPA Private Service Edge is deployed behind a firewall, your firewalls must be configured to let the ZPA Private Service Edge establish outbound connections to the IP addresses of the ZPA Public Service Edge, and establish inbound connections from App Connectors and Zscaler Client Connectors. To learn more, see [ZPA Private Service Edge Deployment Prerequisites](/zpa/zpa-service-edge-deployment-prerequisites#SpecsSizing).
[]About the Disaster Recovery Private Service Edge Groups Page
On the Disaster Recovery Private Service Edge Groups page (Configuration & Control > Administration Control > Disaster Recovery > Private Service Edge Groups), you can do the following:
- Refresh the Disaster Recovery Private Service Edge Groups page to reflect the most current information.
- Download the [Zscaler DNS Record Generator](/zpa/understanding-and-installing-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key used to verify the activation of Disaster Recovery Mode for use with disaster recovery.
- Expand all the rows in the table to see more information about each Private Service Edge group that is designated for disaster recovery.
- View a list of all deployed ZPA Private Service Edge groups that are designated for disaster recovery.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Administrators](/zpa/about-users) page to add new admins or manage existing admins.
- Go to the [Roles](/zpa/about-roles) page to add new admin roles or manage existing roles.
- Go to the [Audit Logs](/zpa/about-audit-logs) page to view and download admin audit log records.
- Go to the [Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy) page to view or update the AUP for your user portals.
- Go to the [Microtenants](/zpa/about-microtenants) page to add new Microtenants or manage existing Microtenants.
The Microtenants page is only visible for Default Microtenant admins.
- Go to the [Client Sessions](/zpa/about-client-sessions) page to view or delete current sessions.
-
Go to the [Integrations](/zpa/about-integrations) page to set up File Transfer via Zscaler Internet Access (ZIA).
The Integrations page is read-only for [Microtenant](/zpa/about-microtenants) admins.
- Go to the [Client Connector IP Assignment](/zpa/about-client-connector-ip-assignment) page to manage Zscaler virtual IP addresses and view IP bindings for use with server-to-client connectivity.
- Go to the [Disaster Recovery Application Segments](/zpa/about-disaster-recovery-application-segments) page to view the application segments designated for disaster recovery.
- Go to the [Disaster Recovery App Connector Groups](/zpa/about-disaster-recovery-app-connector-groups) page to view the App Connector groups designated for disaster recovery.
- Go to the [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings) page to configure the authentication, disaster recovery public key, and disaster recovery domain name.
![Viewing the Disaster Recovery Private Service Edge Groups](/downloads/zpa/administration/disaster-recovery-administration/about-disaster-recovery-private-service-edge-groups/zpa-disaster-recovery-private-service-edge-groups-page.png)