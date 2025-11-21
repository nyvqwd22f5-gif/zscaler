# Understanding Business Continuity
Source: https://help.zscaler.com/zpa/understanding-business-continuity
PDF: https://help.zscaler.com/pdf/com/en/1507011.pdf

Business Continuity in ZPA allows users to continue to access applications during ZPA-related cloud outages or Internet Service Provider (ISP) outages. Business Continuity helps organizations achieve uninterrupted access to applications without any manual intervention.
[]Prerequisites
The following prerequisites must be met for Business Continuity:
- Ensure the following:
- End users' machines are running Zscaler Client Connector versions 4.6 and later for Windows.
- Private Cloud Controllers can receive inbound connections from end users, App Connectors, and ZPA Private Service Edges on port 443.
- End users are able to resolve the Business Continuity FQDNs and can connect to the Private Cloud Controllers and ZPA Private Service Edges using the Business Continuity SNIs on port 443.
- App Connectors and ZPA Private Service Edges can resolve the Business Continuity FQDNs, and can connect to the Private Cloud Controllers outbound connections on port 443.
- The ZPA Private Service Edge can receive inbound connections from end users and all App Connectors on port 443.
To ensure that Business Continuity functions properly, Private Cloud Controllers must run on the same or a later software version as the App Connectors and ZPA Private Service Edges.
- All applications must be [configured](/zpa/configuring-application-segments) before entering Business Continuity.
- All access policies must be [configured](/zpa/configuring-access-policies) before entering Business Continuity.
- Customers must provide the following infrastructure:
- DNS servers.
- Per-tenant IdP to be used during Business Continuity.
- The following infrastructure changes are optional:
- SIEM for visibility or logging during Business Continuity.
- Microsoft's Group Policy Object (GPO) or Mobile Device Management functionalities to install Zscaler Client Connector with customer-specific configurations for new user enrollment.
Overview
The following procedures assume the [prerequisites](#prereq) are met and provide an overview of the steps needed to configure Business Continuity within the ZPA Admin Portal:
- Configure the [Business Continuity settings](/zpa/configuring-business-continuity-settings).
-
Add [Private Clouds](/zpa/about-private-clouds), [Private Cloud Controllers](/zpa/about-private-cloud-controllers), and [Private Cloud Controller Groups](/zpa/about-private-cloud-controller-groups). App Connectors and ZPA Private Service Edges leverage Private Clouds and Private Cloud Controllers when the ZPA cloud is not available or reachable. Private Clouds, Private Cloud Controllers, and Private Cloud Controller groups that are managed by Zscaler are read only and cannot be configured, edited, or deleted.
Private Clouds are the logical grouping of Private Cloud Controller groups, App Connector groups, ZPA Private Service Edge groups, and log receivers. If you are using [Zscaler-managed Business Continuity](/zia/understanding-zscaler-managed-business-continuity-cloud), you can still associate a Private Cloud Controller group, ZPA Private Service Edge group, and App Connector group to a Private Cloud. To learn more, see [Configuring Private Cloud Controllers](/zpa/configuring-private-cloud-controllers) and [Configuring Private Clouds](/zpa/configuring-private-clouds).
- In the Zscaler Client Connector Portal, use one of the following options:
- Enable Business Continuity per App Profile. To learn more, see [Configuring Zscaler Client Connector App Profiles](/client-connector/configuring-zscaler-client-connector-app-profiles).
- Go to **Administration **> **Settings **> **Business Continuity Configuration**, and then sync, download, and copy the thumbprint of the Business Continuity configuration. To learn more, see [About Business Continuity](/zscaler-client-connector/about-business-continuity).
- Deploy Zscaler Client Connector with the Business Continuity installation parameters. To learn more, see [Customizing Zscaler Client Connector with Install Options for EXE](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-exe#RunZAppEXECmdLine) and [Customizing Zscaler Client Connector with Install Options for MSI](/zscaler-client-connector/customizing-zscaler-client-connector-install-options-msi).
To learn more about how to enter and exit Business Continuity, see [Entering and Exiting Business Continuity](/zpa/entering-and-exiting-business-continuity).
Limitations
The following limitations apply for Business Continuity:
- For new users who enrolled during active Business Continuity:
- Mutual TLS authentication between users and ZPA Private Service Edges are not supported.
- SCIM attributes are not supported. Only SAML attributes are supported for access policies, timeout policies, and client forwarding policies.
- While in active Business Continuity, configuration changes (including deployment of ZPA Private Service Edges and App Connectors) are not supported.
- Browser Access, Source IP Anchoring, Cloud Connector, and Branch Connector client types are not supported.
- Machine Tunnels are not supported for new and enrolled Zscaler Client Connector users.
-
On-premises server components (i.e., App Connectors, ZPA Private Service Edges, and Private Cloud Controllers) cannot renew their certificates while in active Business Continuity. These components maintain certificate validity for one year, but can be renewed earlier by specifying the **Certificate Renewal Threshold** when [configuring a Private Cloud](/zpa/configuring-private-clouds).
App Connectors, ZPA Private Service Edges, and Private Cloud Controllers do not automatically upgrade in Business Continuity.