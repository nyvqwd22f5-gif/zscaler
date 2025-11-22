# About Disaster Recovery App Connector Groups
Source: https://help.zscaler.com/zpa/about-disaster-recovery-app-connector-groups
PDF: https://help.zscaler.com/pdf/com/en/1485401.pdf

Disaster recovery App Connector groups are App Connector groups designated as available for disaster recovery to ensure business continuity in the scenario of a disaster event.
Disaster recovery App Connector groups provide the following benefits and enable you to:
- Ensure business continuity in the event of a disaster scenario that impacts the global Zscaler cloud infrastructure.
- Provide users with access to critical App Connectors during a disaster scenario.
After an App Connector group is designated for disaster recovery, both configuration and binary snapshots are saved in the local configuration files on your App Connector and are used for backup purposes. The Zscaler cloud maintains up to 15 prior configuration snapshots and up to 5 prior binary snapshots, and updates both snapshots periodically. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery), [Configuring App Connectors](/zpa/configuring-connectors#createconnectorgroup), and [Managing Disaster Recovery Configuration and Binary Snapshots](/zpa/managing-disaster-recovery-configuration-and-binary-snapshots).
About the Disaster Recovery App Connector Groups Page
On the Disaster Recovery App Connector Groups page (Configuration & Control > Administration Control > Disaster Recovery > App Connector Groups), you can do the following:
- Refresh the Disaster Recovery App Connector Groups page to reflect the most current information.
- Download the [Zscaler DNS Record Generator](/zpa/about-zscaler-dns-record-generator). The Zscaler DNS Record Generator creates the DNS TXT records and the public key used to verify the activation of Disaster Recovery Mode for use with disaster recovery.
- Expand all the displayed rows in the table to see more information about each App Connector group that is designated for disaster recovery.
- View a list of all deployed App Connector groups that are designated for disaster recovery.
- [Modify the columns displayed in the table.](/zpa/using-tables)
- Display more rows or a different page of the table.
- Go to the [Disaster Recovery Application Segments](/zpa/about-disaster-recovery-application-segments) page to view the application segments designated for disaster recovery.
- Go to the [Disaster Recovery Private Service Edge Groups](/zpa/about-disaster-recovery-private-service-edge-groups) page to view the ZPA Private Service Edge groups designated for disaster recovery.
- Go to the [Disaster Recovery Settings](/zpa/about-disaster-recovery-settings) page to configure the authentication, the disaster recovery public key, and the disaster recovery domain name.
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
![Viewing the Disaster Recovery App Connector Groups page](/downloads/zpa/administration/disaster-recovery-administration/about-disaster-recovery-app-connector-groups/zpa-disaster-recovery-app-connector-groups-page_0.png)