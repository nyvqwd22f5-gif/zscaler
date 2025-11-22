# Release Upgrade Summary (2021)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2021

This article provides a summary of all new features and enhancements per Zscaler cloud for the Zscaler Private Access (ZPA) Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).
When Zscaler cloud and Admin Portal updates are deploying, some functionality will not be available until the deployment process completes.

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## December 08, 2021
### Feature Available
#### Cloud Connector Support
Zscaler Private Access (ZPA) now supports a new client type called Cloud Connectors. Admins can view Cloud Connectors and Cloud Connector groups in the ZPA Admin Portal, and use Cloud Connector groups to configure policy rules. To learn more, see [About Cloud Connectors](/zpa/about-cloud-connectors).

## December 01, 2021
### Feature Available
#### Support for Remote Assistance
Zscaler Private Access (ZPA) now supports client-based remote assistance for domain-joined Windows devices and for Zscaler Client Connector versions 3.7 and above. This functionality is accessed from the [Application Segment](/zpa/about-applications) page. To learn more, see [About Client-Based Remote Assistance](/zpa/about-client-based-remote-assistance) and [Validating a Client Hostname](/zpa/validating-client-hostname).

## November 08, 2021
### Feature Available
#### Cloud Update
An update was released to address connectivity issues for ZPA Public Service Edges when updating SCIM attributes.

### Feature Available
#### ZPA Admin Portal Enhancements
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal:
- An update was released to address an issue where deselecting the default port ranges when configuring an Application Segment did not remove the corresponding ports.
- An update was released to address an issue where the incorrect TCP port ranges would be set as default when selecting Web Server from the Default Port Ranges template in the Application Segment.
- An update was made to the ZPA Admin Portal that enables end time in the Applications and Users dashboards. To learn more, see [About the Application Dashboard](/zpa/about-applications-dashboard) and [About the User Dashboard](/zpa/about-users-dashboard).
- An update was released to address a usability issue when editing an Application Segment so that the Application Segment name is displayed in the Edit Application Segment window. To learn more, see [Editing Application Segments](/zpa/editing-application-segments).
- An update was released to address an issue where the start and end time used by the time range filter in the Users dashboard was not being refreshed with the latest time.
- An update was released to address an issue where user metadata was not appearing in the User Activity diagnostics for certain time ranges.
- An update was released that disables the App Connector drilldown menu in the Health dashboard that allows you to view servers and applications.
- An update was released that removes the query string from the filter feature in the App Connectors dashboard. To learn more, see [About the App Connector Dashboard](/zpa/about-app-connector-dashboard).

## November 01, 2021
### Feature Available
#### Comprehensive App Connector Stats
An update was released in the Log Streaming Service (LSS) to provide comprehensive App Connector stats. The new log type can be selected when [configuring a log receiver](/zpa/configuring-log-receiver).

## October 26, 2021
### Feature Available
#### Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- An update was made that improves the lookup service in the Log Streaming Service (LSS) to add the GID to name translations to show ClientZEN and ConnectorZEN names correctly when traffic is processed by a ZPA Private Service Edge.
- An update was released for App Connectors and ZPA Private Service Edges that allows the reporting of CPU steal time from the VM by a Hypervisor.
- An update was released to address an issue where the ZPA Public Service Edge or Private Service Edge rejected the application access request coming from the deactivated user, or from a user whose active status is not synced via SCIM.

## October 21, 2021
### Feature Available
#### ZPA Support with ZDX
Zscaler Private Access (ZPA) supports Zscaler Digital Experience (ZDX) so you can measure performance in the cloud path for internal applications. Data is encrypted and stored at rest before being shipped to the ZDX infrastructure using HTTPS. Zscaler recommends [App Connector specifications and sizing requirements](/zpa/connector-deployment-prerequisites#SpecsAndSizing) for ZDX deployments.
To learn more, see [Monitoring the Users Dashboard](/zdx/monitoring-users-dashboard).

## October 20, 2021
### Feature Available
#### ZPA API Improvements
The following improvements were made to the Zscaler Private Access (ZPA) cloud service APIs:
- New management APIs are now available to manage App Connectors, App Connector Groups, Service Edges, Service Edge Groups, and Log Streaming Service (LSS) configurations.
- New prerequisite APIs for enrollment certificates, provisioning keys, and to get version profiles, client types, status codes, and LSS formats are added.
- A new API to reorder policy rules is added.
- The endpoints to get all browser access (BA) certificates, IdPs, posture profiles, trusted networks, and SAML attributes are now deprecated, and new APIs with pagination are provided.
- API endpoints specific to a policy (global/reauth/bypass) are deprecated and replaced by a generic API that takes policyType as a parameter.
- The port range configuration for the application segment has been enhanced for more readability. The tcpPortRanges and udpPortRanges fields are deprecated and replaced with tcpPortRange and udpPortRange.
To learn more, see the ZPA [API Developer's Guide](/zpa/zpa-api/api-developers-guide).
Resolved Issues
An update was released to address an issue where creating or modifying an access policy rule would return an invalid SCIM attribute error.

## October 15, 2021
### Feature Available
#### Cloud Update
An update was released that optimizes the CPU usage for App Connectors by reducing the frequency of journalctl logs being processed.

## October 11, 2021
### Feature Available
#### Cloud Browser Isolation Integration with ZPA
Cloud Browser Isolation is now integrated with Zscaler Private Access (ZPA). This allows ZPA admins to [configure policies](/zpa/configuring-isolation-policies) for isolating web application traffic. To learn more see, [About Isolation Policies](/zpa/about-isolation-policy).
Organizations can now configure isolation profiles in the Zscaler Cloud Browser Isolation Portal for both ZIA and ZPA. To learn more, see [Creating a ZPA Isolation Profile for Cloud Browser Isolation](/zia/creating-zpa-isolation-profile-cloud-browser-isolation).

## October 04, 2021
### Feature Available
#### New Filters for User Activity Trends
An update was released to include new filters for User Activity trends. You can now filter by application domain and port, connection status code, dispatcher ID, machine tunnel, user client type, and username. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics#Trends).

## September 28, 2021
### Feature Available
#### SCIM Sync Logs
SCIM Sync Logs are now available in the ZPA Admin Portal under SCIM Management. Operations that change the state of the users and groups are presented on the SCIM Sync Logs page. To learn more, see [About SCIM Sync Logs](/zpa/about-scim-sync-logs).

## September 21, 2021
### Feature Available
#### New User Activity Filters
An update was released to include new user activity filter types. You can now filter by connection type and forwarded ZPA Public Service Edge or ZPA Private Service Edge name. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).

## September 13, 2021
### Feature Available
#### Admin Portal Enhancement
An update was released that improves the user experience in the Admin Portal when deleting application segments that reference segment groups or policies. If an application segment is linked to any policy, an admin must remove the link to delete the application segment. To learn more, see [About Applications](/zpa/about-applications).

### Feature Available
#### Version Profiles
ZPA now supports the ability to [configure a version profile](/zpa/configuring-version-profile) when adding or editing an App Connector group or ZPA Private Service Edge group in the ZPA Admin Portal.

## August 31, 2021
### Feature Available
#### App Connector Health Visualization
The App Connector dashboard now includes different metrics, new widgets, and expanded visualization to allow you to better monitor the health of your organization's App Connectors and diagnose issues. To learn more, see [About App Connector Dashboard](/zpa/about-app-connector-dashboard).

## August 26, 2021
### Feature Available
#### SCIM Service Schema and Related API Enhancements
The following issues were resolved:
- An update was released to address an issue where a SCIM user attribute returned an incorrect type.
- An update was released to address an issue to remove a duplicate group attribute and correct the reference URL for the group attribute to match the schema when running a GET request for SCIM APIs.
- An update was released to address an issue where a name sub attribute was not being returned in the schema of the SCIM APIs.
Resolved Issues
An update was released to address an issue that caused performance degradation in ZPA Public Service Edges while processing connection requests.

### Feature Available
#### TCP Communication Sockets
You can now enable App Connectors to maintain TCP communication sockets using the TCP Keepalive socket option when adding or editing Segment Groups in the ZPA Admin Portal. To learn more, see [Networking Deployed App Connectors](/zpa/networking-deployed-connectors#Tcpcommunication).

## August 19, 2021
### Feature Available
#### ZPA Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- The Users Dashboard features several updates to the Recent Users and Current Connected Users widgets to view machine tunnel connections in real-time and during selected periods. To learn more, see [About the Users Dashboard](/zpa/about-users-dashboard).
- An update was made to the ZPA Admin Portal which allows you to enable the termination of users’ running application sessions upon re-authentication according to timeout policy. This setting supports termination of existing ZPA Microtunnels (M-Tunnels) upon authentication expiry, or upon policy change denying access mentioned in [ZPA Private Service Edge Version 21.172.1](/zpa/zpa-private-service-edge-release-summary-2021?applicable_version=21.172.1). To learn more, see [About Timeout Policy](/zpa/about-timeout-policy).

## August 18, 2021
### Feature Available
#### Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- An update was released that allows termination of existing ZPA Microtunnels (M-Tunnels) in preparation for functionality changes.
- An update was released for ZPA Public Service Edges and ZPA Private Service Edges to support geofencing at a sub-cloud level.
- An update was released that allows App Connectors to maintain TCP communication sockets using the TCP Keepalive socket option in support for future functionality changes.
- An enhancement was made that improves the App Connector's efficiency for reporting Application registration information.
- An update was released for App Connectors that changes the DNS endpoint for log collection.

## August 16, 2021
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- An update was released to address an issue that caused performance degradation in ZPA Public Service Edges while processing connection requests.
- An update was released to address an issue where some application traffic intended for Source IP Anchoring was going to ZIA instead.

## August 06, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue with IP caching that caused connections timeout errors for some users accessing applications via Browser Access.

## July 29, 2021
### Feature Available
#### ZPA Public Service Edge Update
An update was released to address an issue with disconnected SIPA clients upon ZPA Public Service Edge restart.

## July 22, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue with authentication through Identity Providers (IdPs) that send an IP address in the subject confirmation data of a SAML response.

### Feature Available
#### Service Provider Certificate Rotation
You can now rotate the service provider certificate for your identity providers (IdPs) in the ZPA Admin Portal. This option is available when [editing an IdP](/zpa/editing-idp-configuration) by selecting a different certificate in the User SP Certificate Rotation or Admin SP Certificate Rotation field.
This field may show as SP Certificate Rotation if the original IdP was configured to use Both (i.e., admin and user SSO) when that option was available.
Making this change may require additional changes to the IdP. To learn more, see [Managing a Service Provider Certificate Rotation](/zpa/managing-service-provider-certificate-rotation).

### Feature Available
#### ZPA Admin Portal Enhancement
You can now unlock administrators and API Clients who have failed authentication three times in the ZPA Admin Portal. To learn more, see [About Administrators](/zpa/about-administrators) and [About API Keys](/zpa/about-api-keys).

## July 12, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue for ZPA Public Service Edges and ZPA Private Service Edges due to ICMP application transactions issued during policy checks.

## July 08, 2021
### Feature Available
#### ZPA Private Service Edge Support for SCIM Policies
ZPA Private Service Edges now support SCIM for policies. To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).

## July 07, 2021
### Feature Available
#### Cloud and Admin Portal Updates for ICMP
ICMP functionality is now available. End users can now use ping to determine reachability to internal applications via an IP address or a hostname. This functionality will appear visible in the ZPA Admin Portal, but it requires end-user devices to upgrade to [Zscaler Client Connector version 3.5 for the Windows](/zscaler-client-connector/client-connector-app-release-summary-2021?applicable_category=Windows&applicable_version=3.5) platform.
When setting up an Application Segment, you can now choose whether the Zscaler Client Connector will allow ICMP communication with the App Connector. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).
You can also use an ICMP protocol to filter your [Live Logs](/zpa/about-live-logs) and [User Activity Diagnostic logs](/zpa/about-user-activity-diagnostics).
Resolved Issues
An update was released to address an issue where the App Connector page in the ZPA Admin Portal was showing Uptime as Not Available due to incorrect information reported by the App Connector.

## June 28, 2021
### Feature Available
#### Admin Portal Enhancements
The number of [DNS search domains](/zpa/about-applications/dnsDomains) that can be added as suffixes to application names is now limited to 50. Customers that currently have more than the limit will not be able to add more DNS suffixes, but you will be able to replace existing ones. To learn more, see [Ranges and Limits](/zpa/ranges-limitations).

### Feature Available
#### Updated Package for App Connectors in AWS and Microsoft Azure Marketplace
An updated package for App Connectors is available in AWS and Microsoft Azure Marketplace. You are not required to update existing App Connectors in AWS and Azure. The updated package is only required for new instances of the App Connector. The package includes recently released updates for Centos 7.
Resolved Issues
An update was released to disable GSS authentication in App Connectors in order to address a Redhat user enumeration vulnerability.

## June 17, 2021
### Feature Available
#### Export Application Segment Configurations
You can now export your organization’s application segment configurations from the ZPA Admin Portal. To learn more, see [About Applications](/zpa/about-applications).
[See image.](#img-exportappconfig)
[]![Export Application Segment Configuration information from the Application Segments page in the ZPA Admin Portal](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2021/export-application-segment-configurations/zpa-exportappsegmentconfigurations.png)

## June 14, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue where logs on the Private Service Edge Status Diagnostics page were not appearing in the ZPA Admin Portal.

## May 26, 2021
### Feature Available
#### Cloud and Admin Portal Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud and Admin Portal:
- An update was released to address an issue where in certain situations single sign-on to the ZPA Admin Portal was not successful.
- An update was released to address an issue where certain incomplete access policy rules created using the ZPA Public API prevented the ZPA Admin Portal from correctly displaying the corresponding Access Policy configurations.

## May 19, 2021
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- An enhancement was made to improve the efficiency of processing policies in ZPA.
- Improvements were made to different components to ensure the security and integrity of the ZPA cloud infrastructure.
- An improvement was released to limit the Microtunnel ​​​​​(M-Tunnel) requests per user to 100/second.

## May 18, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue where ZPA was incorrectly processing the API gateway for EU customers.

## May 12, 2021
### Feature Available
#### Cloud Update
An update was made to exclude machine tunnels for Recent Users and Connected Users counts in the [Users Dashboard](/zpa/about-users-dashboard).

## May 11, 2021
### Feature Available
#### Cloud Update
An update was released to address an issue where customerId was not correctly interpreted for certain ZPA APIs.

## May 06, 2021
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- After enabling SCIM Attributes for Policy for an IdP in the ZPA Admin Portal, ZPA now requires a user to reauthenticate in Zscaler Client Connector. ZPA will only evaluate policies with SCIM criteria for this user after the user successfully reauthenticates. To learn more, see Configuring an IdP for Single Sign-On
- An update was made to address an issue where the ZPA API was not fetching the records by customerId.

## April 09, 2021
### Feature Available
#### User Experience Enhancements
The Zscaler Private Access (ZPA) Admin Portal will now provide a warning to alert Admins when the current number of applications definitions is close to 6000. The maximum number of supported application definitions is 6000.

## April 01, 2021
### Feature Available
#### Cloud Updates
An update was released to address an issue related to communication between ZPA Private Service Edges and ZPA Public Service Edges that caused the ZPA Public Service Edges to experience intermittent degradation.

## March 31, 2021
### Feature Available
#### SCIM API Support
The SCIM Service in ZPA was enhanced to return a list of groups for a specific user.

## March 29, 2021
### Feature Available
#### Cloud Updates
The ZPA Cloud update includes improvements to infrastructure that supports TLS encryption across different components.
Resolved Issues
The following issues were resolved:
- An update was released to address an issue where ZPA Public Service Edges were sending additional messages to the Zscaler Client Connector after authentication was achieved.
- An update was released to address an issue where the country code for App Connector groups were not appearing in the App Connector Status Logs.
- An update was released to address an issue where the search functionality was unavailable when editing an Application Segment in the ZPA Admin Portal.
- An update was released to address an issue in the ZPA Admin Portal that prevented deleting or moving existing Access Policy rules that have names containing special characters.

## March 26, 2021
### Feature Available
#### Admin Portal Improvements
An update was released to address an issue where an error message would appear when searching by SCIM User Name on the SCIM Groups page in the ZPA Admin Portal.

## March 23, 2021
### Feature Available
#### ZPA API
Zscaler Private Access (ZPA) now supports customer facing APIs for managing application segments and policies. To learn more, see [About ZPA API](/zpa/about-zpa-api).
API access requires an API key, which you can add in the ZPA Admin Portal. To learn more, see [About API Keys](/zpa/about-api-keys).
Admin Portal Improvements
Zscaler now allows the termination of Admin sessions created using an API key or via the Admin Portal. To learn more see, [About Client Sessions](/zpa/about-client-sessions).
Cloud Updates
Zscaler has made enhancements to the ZPA Cloud for improving load balancing of application requests across App Connectors. As part of this enhancement, ZPA will account for CPU, memory, and UDP port consumption for each eligible App Connector, and it will try to select an App Connector with lower utilization by using a probability mass function (PMF) algorithm.

## March 15, 2021
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- ZPA Public Service Edges now cache App Connector selection decisions based on earlier application requests.
- ZPA Private Service Edges now support Machine Tunnels. To learn more, see [About Machine Tunnels](/zscaler-client-connector/about-machine-tunnels).

## March 10, 2021
### Feature Available
#### Admin Portal Improvements
The Access Policy, Client Forwarding Policy, and Timeout Policy pages now include the ability to filter the tables by rule criteria. To learn more, see [About Access Policy](/zpa/about-access-policy), [About Timeout Policy](/zpa/about-timeout-policy), and [About Client Forwarding Policy](/zpa/about-client-forwarding-policy).

## March 08, 2021
### Feature Available
#### Admin Portal Enhancements
When setting up an App Connector, you can now configure the App Connector group to perform IPv4 only DNS resolution checks for applications. To learn more, [Configuring App Connectors](/zpa/configuring-connectors).
Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- The Zscaler Private Access (ZPA) Cloud now includes enhancements that improve the processing of browser access application requests when access policies use SCIM attributes.
- The Zscaler Private Access (ZPA) Cloud now includes an enhancement that improves the App Connector’s efficiency for reporting Application reachability information.
Resolved Issues
The following issues were resolved:
- An update was released to address an issue where scrolling to the end of the Users Blocked By Policies list in the [Users dashboard](/zpa/about-users-dashboard) resulted in the list resetting to no users.
- An update was released to improve the accuracy of the connection setup time (i.e., Connection: Setup Time) in Diagnostics.
- An update was released to improve the processing of App Connector Group configurations in Access Policies with respect to the App Connector selection.
- An update was released to improve how an App Connector verifies its permissions to specific directories on the host.

## March 04, 2021
### Feature Available
#### Cloud Updates
The following issues were resolved:
- An update was released to address an issue that caused performance degradation in ZPA Public Service Edges due to high memory consumption.
- An update was released to address an issue where, in certain cases, ZPA Public Service Edges did not learn the entire application configuration information.

## February 26, 2021
### Feature Available
#### Trend Charts
The Diagnostics section of the Zscaler Private Access (ZPA) Admin Portal now displays trend charts for User Activity logs. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics).

## February 23, 2021
### Feature Available
#### Pre-Windows Login
Zscaler Private Access now supports a new client type called Machine Tunnel. By using a machine tunnel, a user’s Windows device can be configured to access internal applications even when the device’s Zscaler Client Connector is not connected to ZPA. To learn more, see [About Machine Groups](/zpa/about-machine-groups).
To use this feature, you need to [configure Machines groups and Machine Provisioning keys](/zpa/configuring-machine-provisioning-keys) in the ZPA Admin Portal and add keys to Zscaler Client Connector profile [rules for Windows](/z-app/configuring-zscaler-app-profiles#windows). It also requires the [Zscaler Client Connector version 3.2 for Windows](/zscaler-client-connector/client-connector-app-release-summary-2021?applicable_category=Windows&applicable_version=3.2.0.87) at the minimum.
Resolved Issues
A fix was released to address an issue where ZPA incorrectly processed configurations for a Log Receiver set up for the Log Streaming Service (LSS) and prevented the user from accessing the Log Receiver over ZPA.

## February 12, 2021
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- An update was released to the improve the efficiency of a database service used by ZPA.
- A fix was released to address an issue that caused ZPA to send User Activity logs with certain Session Codes to a log receiver, even when these Session Codes were excluded in the Log Receiver configuration.

## February 08, 2021
### Feature Available
#### Time Zone Selection
The Zscaler Private Access (ZPA) Admin Portal now allows you to choose a time zone in your account settings. Timestamps and time interval selection in the ZPA Admin Portal will reflect your local or chosen time zone. To learn more, see [About the ZPA Admin Portal](/zpa/about-zpa-admin-portal#username).
Session Pinning
The ZPA Admin Portal now includes a Session Pin setting when creating admins. This setting ensures that a session token connects to the user to whom it was issued. It is enabled by default. To learn more, see [Configuring ZPA Administrators](/zpa/about-user/new).
[See image.](#img_sessionpinning)
Admin Portal Improvements
For the Time Range filter on the [Application Dashboard](/zpa/about-applications-dashboard) and [Users Dashboard](/zpa/about-users-dashboard), you can now set a Custom Range in increments of 5 minutes.
[]![Session Pinning for Configuring an Admin](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2021/time-zone-selection/createadmin_pinsession.png)

## February 01, 2021
### Feature Available
#### Cloud Updates
An update was released to address an issue where, in certain conditions, users were unable to connect to Zscaler Private Access (ZPA) if SCIM attributes were configured as criteria in ZPA policy rules.

## January 27, 2021
### Feature Available
#### Admin Portal Improvements
The [Health dashboard](/zpa/about-health-dashboard) now identifies disconnected ZPA Private Service Edges with a Disconnected label below the ZPA Private Service Edge.

## January 21, 2021
### Feature Available
#### Cloud Updates
Zscaler has made load balancing enhancements to improve transmission of logs from ZPA Public Service Edges to ZPA's log infrastructure.

## January 19, 2021
### Feature Available
#### Country Code for App Connectors
Zscaler Private Access (ZPA) automatically populates the country code for an App Connector’s location based on the address specified for the App Connector group. ZPA will now use the country code to determine an App Connector’s location for App Connector selection decisions. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors#createconnectorgroup).
As part of enabling this functionality across ZPA, the Zscaler Operations team will perform a one time update to the ZPA database. This will result in an Audit Log corresponding to the Admin ID showing [user]@root.zscaler.com. It is available to review in an organization’s tenant under Administration > Audit Logs. To learn more, see [About Audit Logs](/zpa/about-audit-logs).

## January 07, 2021
### Feature Available
#### Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where, in certain situations, ZPA's Path Selection micro-service did not correctly process application reachability information that was reported by App Connectors.
- A fix was released to address an issue related to processing SCIM attributes that, for certain users, prevented Zscaler Client Connector from setting up a connection to ZPA.
