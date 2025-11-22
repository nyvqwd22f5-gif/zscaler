# Release Upgrade Summary (2020)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2020

This article provides a summary of all new features and enhancements per Zscaler cloud for the ZPA Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com/).

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## December 21, 2020
### Feature Available
#### Resolved Issues
A fix was released to address an issue that prevented some users from connecting to ZPA due to the way SCIM was processing the username formats.

## December 15, 2020
### Feature Available
#### SCIM Policies
You can now configure [access policies](/zpa/configuring-access-policies), [timeout policies](/zpa/configuring-timeout-policies), and [client forwarding policies](/zpa/configuring-client-forwarding-policies) with SCIM attributes and SCIM groups as criteria.
To allow the use of SCIM attributes and SCIM groups in policies, there is the new SCIM Attributes and Groups for Policy setting to enable when creating an identity provider. To learn more, see [Configuring an IdP for Single Sign-On](/zpa/configuring-idp-single-sign).
As part of SCIM policy changes, there are new session status codes related to the disabling of users by SCIM. To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
Admin Portal Improvements
The Health dashboard now identifies disabled App Connectors with a label below the App Connector.
[See image.](#img-disabledappconnector)
A maximum of 100 names can be specified in the filters for App Connector: Name and Service Edge: Name (Public/Private) on the diagnostic pages.
Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where the Admin UI was not detecting duplicate names when creating application segments.
- A fix was released to address an issue where the Last Updated timestamp on the SCIM Group page was not accurately displayed.
- A fix was released to address an issue where hover over text in the ZPA Admin Portal would remain on the screen after the cursor moved.
- A fix was released to address an issue where the list of Current Connected Users on the Users dashboard page showed the “No current connected users at this time” message at the end of a list of users.
- A fix was released to address an issue where ZPA Public Service Edges and ZPA Private Service Edges experienced intermittent performance degradation while processing DNS resolutions during application access.
- A fix was released to address an issue where the ZPA Admin Portal prevented the creation of new App Connector Provisioning Keys when configuring an App Connector.
- A fix was released to address an issue that prevented the creation of an IdP for admin SSO if the SCIM Sync setting was enabled.
[]![Disabled App Connector](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/scim-policies/disabledappconnector.png)

## December 14, 2020
### Feature Available
#### Resolved Issues
A fix was released to address an issue where ZPA Public Service Edges and ZPA Private Service Edges experienced service degradation when processing connections.

## December 02, 2020
### Feature Available
#### Admin Portal Improvements
The Zscaler Private Access (ZPA) Admin Portal was updated to prevent the execution of malicious payload in the UI.

## December 01, 2020
### Feature Available
#### Cloud Updates
The Zscaler Private Access (ZPA) Cloud will now stop health reporting if the number of applications that an App Connector is currently monitoring for reachability is greater than 6000 at one time.

## November 19, 2020
### Feature Available
#### Multiple Posture Profile Condition Sets
You can now configure [access policies](/zpa/configuring-access-policies), [timeout policies](/zpa/configuring-timeout-policies), and [client forwarding policies](/zpa/configuring-client-forwarding-policies) with multiple posture profile condition sets. You can add up to 10 condition sets.
[See image.](#image_postureprofile)
[]![Multiple Posture Profile condition sets for a policy rule](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/multiple-posture-profile-condition-sets/zpa-policies-posturesets.png)

## November 13, 2020
### Feature Available
#### Admin Portal Improvements
The Diagnostic pages have been enhanced to display additional transactions by just scrolling on the page. By default, the first 20 transactions are displayed.

## November 12, 2020
### Feature Available
#### Support for Encrypted Log Delivery to a Log Receiver
You can now configure the ZPA Log Streaming Service (LSS) to encrypt logs between the LSS App Connector and a log receiver using TLS encryption. To learn more, see [Configuring Log Receiver](/zpa/configuring-log-receiver).
Browser Access Log Fields
The Browser Access log fields Origin and CorsToken are now part of the default log template. To learn more, see [About Browser Access Log Fields](/zpa/about-browser-access-log-fields).

## November 09, 2020
### Feature Available
#### Resolved Issues
A fix was released to address an issue where, under certain circumstances, new App Connectors cannot be registered to a customer's ZPA tenant.

## October 29, 2020
### Feature Available
#### Cloud Updates
The Zscaler Private Access (ZPA) Cloud now includes an enhancement to speed up policy processing related to application access.

## October 27, 2020
### Feature Available
#### Browser Access Enhancements
Starting with this release Zscaler Private Access (ZPA) will forward authenticated CORS requests to an App Connector by setting the Access-Control-Allow-Origin header to null for the browser to process the response. For unauthenticated CORS requests, ZPA will redirect them to an authentication domain and set the Origin header to null. To learn more, see [About Browser Access](/zpa/about-browser-access).
The current supported browsers for CORS requests are:
- Firefox 81.0
- Chrome 64_65
- Google Chrome 86.0.4240.75
- Microsoft Edge 86.0.622.43
- Safari 12.0
- Safari 13.0
There are two new Browser Access log fields, Origin and CorsToken, that can be added to a Custom Log Template.To learn more, see [About Browser Access Log Fields](/zpa/about-browser-access-log-fields).
Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where, under certain circumstances, Administrators were unable to edit Access Policies in the ZPA Admin Portal.
- A fix was released to address an issue where, for certain browsers, the authentication cookies issued by ZPA did not have the samesite attribute set.

## October 26, 2020
### Feature Available
#### App Connector Selection using Access Policies
You can now configure an Access Policy to specify the App Connectors that should be used for accessing an application. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies).
As part of this change, the Policy role was updated and new resource types "Policy to Connector Group Association" and "Policy to Server Group Association" were added. To learn more, see [Configuring Administrator Roles](/zpa/configuring-administrator-roles) and [About Audit Logs](/zpa/about-audit-logs).
Session Status Updates
The User Activity log now has a new error code to indicate an App Connector is not configured in a Server Group. (The internal error code is BRK_MT_SETUP_FAIL_CONNECTOR_GROUPS_MISSING.) To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
Resolved Issues
The following issue was resolved:
- A fix was released to address an issue where, under certain circumstances, an error occurred while resetting an Admin account password on the ZPA Admin Portal.

## October 22, 2020
### Feature Available
#### Admin Portal Improvements
For the Time Range filter on the [Application Dashboard](/zpa/about-applications-dashboard) and [Users Dashboard](/zpa/about-users-dashboard), you can now set a Custom Range in increments of 15 minute intervals.

## October 20, 2020
### Feature Available
#### Cloud Updates
The Zscaler Private Access (ZPA) Cloud now includes an enhancement to the communication methodology between the ZPA Public Service Edge and the Path Selection service in order to improve the performance of information sharing between the two components.

## October 15, 2020
### Feature Available
#### Admin Portal Improvements
In order to improve user experience, the [Diagnostic pages](/zpa/dashboard-diagnostics) will now display search results up to 500 pages. You can filter results using the available search criteria.

## October 12, 2020
### Feature Available
#### Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where the ZPA Public Service Edges and ZPA Private Service Edges were not correctly processing updates to policy configurations.
- A fix was released to address an issue where the connection close request from the Zscaler Client Connector was processed by the ZPA Public Service Edge or ZPA Private Service Edge prior to completing the data transfer for that connection.

## October 09, 2020
### Feature Available
#### Graphical View of Configuration Objects in the ZPA Admin Portal
The Zscaler Private Access (ZPA) Admin Portal now provides a visual layout of the different ZPA configuration objects. You can see this graphical view from the following pages:
- [Application Segments](/zpa/about-applications)
- [Segment Groups](/zpa/about-segment-groups)
- [App Connectors](/zpa/about-connectors)
- [App Connector Groups](/zpa/about-connector-groups)
- [Server Groups](/zpa/about-server-groups)
- [Health Dashboard](/zpa/about-health-dashboard)
To view the layout as it relates to a particular object, use the graph icon (![Graph icon](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/graphical-view-configuration-objects/graphicon.png)
).
[See image.](#img_graphicon)
The graphical view shows the object and all the other objects it connects to.
[See image.](#img_graphview)
[]![Graph icon on the Segment Groups page](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/graphical-view-configuration-objects/viewgraphicon.png)
[]![Graphical view of ZPA objects](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/graphical-view-configuration-objects/graphicalviewexample.png)

## October 08, 2020
### Feature Available
#### ZPA Private Service Edge
A ZPA Private Service Edge allows you to host the ZPA Service Edge functionality in your organization’s environment. It is designed to function as single-tenant (per customer) instance, which Zscaler manages. To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
Private Service Edge requires Zscaler Client Connector version 2.1.2 at the minimum.
The Service Edge page displays information on each ZPA Private Service Edge you've configured. To learn more, see [About ZPA Private Service Edges](/zpa/about-zpa-private-service-edges) and [Configuring Service Edges](/zpa/configuring-service-edges).
[See image.](#sepage)
Similar to App Connectors, ZPA Private Service Edges are deployed in groups and use provisioning keys. The Service Edge Group page and the Service Edge Provisioning Keys page allows you to view and manage your groups and the keys for your organization's ZPA Private Service Edges. To learn more, see [About ZPA Private Service Edge Groups](/zpa/about-zpa-service-edge-groups) and [About ZPA Private Service Edge Provisioning Keys](/zpa/about-zpa-service-edge-provisioning-keys).
[See image.](#segrouppg)
[See image.](#seprvsnkeypg)
The Service Edge Status Diagnostics allows for monitoring and tracking all ZPA Public Service Edges and ZPA Private Service Edges. To learn more, see [About ZPA Private Service Edge Status Diagnostics](/zpa/about-zpa-service-edge-status-diagnostics).
[See image.](#sestatusdiagnstc)
In addition, new sections and filters for monitoring and tracking ZPA Public Service Edges and ZPA Private Service Edges were added or updated for Live Logs, User Activity, User Status, App Connector Status, and Application Status. To learn more, see [About Live Logs](/zpa/about-live-logs), [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics), [About User Status Diagnostics](/zpa/about-user-authentication-diagnostics), and [About App Connector Diagnostics](/zpa/about-connector-diagnostics).
[]![Service Edge page](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-private-service-edge/zpa-serviceedgepg-blank.png)
[]![Service Edge Group page](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-private-service-edge/zpa-serviceedgegrouppg_blank.png)
[]![Service Edge Provisioning Keys page](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-private-service-edge/zpa-serviceedge_provisionkeypg_blank.png)
[]![Service Edge Status Diagnostics](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-private-service-edge/zpa-privateserviceedgestatus-blank.png)

## October 05, 2020
### Feature Available
#### Admin Portal Improvements
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal:
- The maximum number of rules for Access policies has increased to 2000 rules. This was raised from 500 policy rules. To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).
- An update was made to the workflow for editing application segments to provide an improved user experience. To learn more, see [Editing Application Segments](/zpa/editing-application-segments).
- The Users dashboard now allows you to download the list of Current Connected Users. To learn more, see [About the Users Dashboard](/zpa/about-users-dashboard).
- The ZPA Admin Portal was updated to ensure that users with admin privileges are not unintentionally deleted or have their permissions downgraded. This only impacts system generated user accounts that start with “admin” or “zpaadmin”.
Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where the Admin UI displayed an error when editing an application segment with browser access applications.
- A fix was released to address an issue where the Admin UI displayed incorrect results when filtering application configuration information with the Contains operator.
- A fix was released to address an issue that sometimes prevented admins from editing policies in the ZPA Admin Portal after returning from the Zscaler Client Connector portal.
- A fix was released to address an issue that prevented the ability to edit policies when an admin was assigned to a custom policy role.
- A fix was released to update the color indication from green to blue for Open or Active transactions on the Diagnostic pages.

## September 28, 2020
### Feature Available
#### Cloud Updates
The Zscaler Private Access (ZPA) now sets the sameSite attribute to None in the ZPA Browser Access authentication cookies.
Resolved Issues
The following issue was resolved:
- A fix was released to address an issue where authentication failed for ZPA Browser Access with [error code 42018](/z-app/zscaler-app-zpa-authentication-errors). In this situation, the Browser Access service will now retry single sign-on more than once.

## September 18, 2020
### Feature Available
#### Admin Portal Enhancements
For a Zscaler Private Access (ZPA) tenant that is associated with Zscaler Client Connector tenants on separate clouds, the ZPA Admin Portal now allows you to select the Zscaler Client Connector tenant and cloud prior to connecting to the Zscaler Client Connector Portal.
Labels and text throughout the ZPA Admin Portal were updated to reflect the Zscaler product name change.
Resolved Issues
The following issue was resolved:
- A fix was released to change the default Health Reporting setting when configuring an application segment from Continuous to On Access.

## September 14, 2020
### Feature Available
#### Cloud Updates
The Zscaler Private Access (ZPA) Cloud now includes an enhancement to the ZPA Policy engine for improved efficiency and scale.
For applications that are still configured to use the already deprecated Application Group policies, transactions will display the following error: "Policy is not configured for access". (The internal error code is BRK_MT_SETUP_FAIL_NO_POLICY_FOUND). To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
Application Group policies were deprecated starting January 2018.
To resolve this error, you need to define access policy rules for applications. To learn more, see [About Access Policy](/zpa/about-access-policy).

## September 10, 2020
### Feature Available
#### Support for OPTIONS Method in Browser Access
When enabling browser access for an application, you can now choose whether to allow ZPA to forward an unauthenticated HTTP preflight OPTIONS request from the browser to the application. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).
Admin Portal Improvements
In order to improve the way application segment health is managed in the ZPA Admin Portal, the Health Reporting and Health Check are now consolidated into one setting within the [Application Segment workflow](/zpa/configuring-application-segments). To learn more, see [Understanding Health Reporting](/zpa/understanding-health-reporting).
Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where browser access logs were not always reaching a log receiver.
- A fix was released to address an issue where the application segment search name filter would not display search results if the case did not match.
- A fix was released to address an issue where ZPA did not reorder Access Policy rules correctly when rules were deleted while a reorder of the rules was in progress.
- A fix was released in the ZPA Admin Portal UI to allow trailing spaces in configuration fields.
- A fix was released to update labels in the Connector Dashboard from **Mtunnel Count** to **New Application Tunnels**.

## September 03, 2020
### Feature Available
#### Admin Portal Enhancements
The following update was made to the Zscaler Private Access (ZPA) Admin Portal:
- Applications can now be defined by only a wildcard (e.g., *). To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).
This configuration method requires approval from Zscaler prior to implementation.

## August 11, 2020
### Feature Available
#### Session Status Updates
In order to better track what causes an App Connector to not complete a transaction, ZPA now has new error codes for file and port exhaustion. To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
Resolved Issues
- A fix was released to address a performance degradation issue that occurred when the Public Service Edge was processing large volumes of traffic.
- A fix was released to address a performance degradation issue that occurred when the Public Service Edge was processing source IP anchoring traffic.
- A fix was released to address an issue where the server IP and port were not displaying for the error code “Connector: Connection request to server timed out” in the [App Connector Diagnostic page](/zpa/about-connector-diagnostics) in the ZPA Admin Portal.

## August 10, 2020
### Feature Available
#### Cloud Updates
The following update was made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released to address an issue where enabling **Zscaler Client Connector can receive CNAME** was not processed correctly when [configuring an application segment](/zpa/configuring-application-segments#tab1).

## August 03, 2020
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released to address an issue where users connect to a Private Service Edge further away than a closer Public Service Edge.

## July 27, 2020
### Feature Available
#### Source IP Anchoring
Source IP Anchoring allows organizations to selectively steer traffic processed by ZIA back to your network. This is done by directing the traffic to the appropriate destination server using the IP address of your choice, which goes through an [App Connector](/zpa/about-connectors). To use Source IP Anchoring, your organization requires both ZIA and ZPA. To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring).
To enable Source IP Anchoring in ZPA, you need to [configure the application segments](/zpa/configuring-application-segments) that require source IP anchoring and [set up access policies](/zpa/configuring-access-policies) for ZIA. To learn more, see [Configuring Source IP Anchoring](/zia/configuring-source-ip-anchoring).

## July 20, 2020
### Feature Available
#### Audit Log in the Log Streaming Service
The Log Streaming Service (LSS) now supports streaming of [Audit Logs](/zpa/about-audit-logs) from your organization’s ZPA tenant to your log receiver. To learn more, see [About the Log Streaming Service](/zpa/about-log-streaming-service).
Admin Portal Improvements
The following changes were made to the Zscaler Private Access (ZPA) Admin Portal:
- The search field on list pages was replaced with filters. This provides an improved way to sort through the configuration.
- To improve load time when displaying a large number of users, pagination was added to the Current Connected Users widget on the [User Dashboard](/zpa/about-users-dashboard).
- To improve the experience of Admins in the ZPA Admin Portal, the relationship graph in the Connector section of the [Health Dashboard](/zpa/about-health-dashboard) has been deprecated.
Resolved Issues
The following issues were resolved:
- A fix was released to address an issue where the UI was incorrectly processing the web server certificate during upload.
- A fix was released to address an issue with displaying the access policy filters in [Live Logs](/zpa/about-live-logs).
- A fix was released to address a problem where User Status logs were not ingested by some SIEMs when empty fields were not properly defined.

## July 14, 2020
### Feature Available
#### Admin Portal Improvements and Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Admin Portal and ZPA Cloud:
- The number of applications per application segment is now 2000 applications. This was raised from 100 applications per application segment. To learn more, see [Ranges & Limitations](/zpa/ranges-limitations).
- By default, Zscaler Client Connector (Z App) receives CNAME DNS records from the App Connectors. The Admin Portal now provides an option where the App Connectors will not send CNAME DNS records to Zscaler Client Connector. This is not applicable for Browser Access applications. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments).
- The ZPA Admin Portal UI will no longer show the application RTT time (i.e., App Connector: App RTT) in the logs. In its place is the time the App Connector takes to process and set up a connection to the application server (i.e., Connection: Setup Time). Connection setup time is connection processing time plus connector to app rtt.
- The Signing Certificate label was changed to Enrollment Certificate in the ZPA Admin Portal for better consistency with certificate’s purpose.
- Your organization can now configure ZPA, so user traffic is processed by a subset of ZPA Public Service Edges that are available in the global ZPA service. Contact Zscaler Support to request access to this feature.
- After the initial authentication from Zscaler Client Connector or App Connectors, the respective control TLS sessions will be established to the the closest available in-country ZPA Public Service Edge.
Resolved Issues
The following issues were resolved
- A fix was released to address a problem where the Total count on the Diagnostics page would not adjust to accommodate numbers greater than 999 million.
- A fix was released to address audit logs not getting generated while updating the identity provider configuration.
- A fix was released to resolve an issue where the Health dashboard did not display health information consistently.
- A fix was released where the authentication service in ZPA always signed the SAML request to the IdP while ignoring the sign request settings from the IdP.

## July 01, 2020
### Feature Available
#### Cloud Update
The following update was made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released to address an issue where the Public Service Edge connection state in the ZPA Central Authority (CA) was incorrect and led to application access issues.

## June 23, 2020
### Feature Available
#### Cloud Updates
The following update was made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released to address an issue with Browser Access applications where ZPA did not correctly process SAML requests and responses that came out of order. The issue was observed for the Azure AD and Okta identity providers.
- A fix was released where updates to permissions for existing roles may take up to two minutes to take effect in the ZPA Admin Portal.
- A fix was released to address an issue with incorrect username formats that prevented SCIM from processing requests to delete users.

## June 17, 2020
### Feature Available
#### Application Segment Updates
The **Application Segment** page of the ZPA Admin Portal is updated to help you gain a better view of your applications. For application segments with more than 3 applications, there is now a link in the table to bring up the Application Segment Details window with all the applications. This is a read only view. From here you can search for applications, ports, certificates, etc. To learn more, see [About Applications](/zpa/about-applications).
[See image.](#appsegdetails)
While editing your application segments, the edit window also provides a search capability and makes sure you do not accidentally enter the same application more than once. Editing now has a multi-tab window similar to configuring an application segment. You can address general application segment details, then manage how applications are defined, and finally review all changes before saving. To learn more, see [Editing Application Segments](/zpa/editing-application-segments).
[See image.](#editappseg)
All browser access applications are still marked by the ![Browser Access icon](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/Application%20Segment%20Updates/BAIcon.png)
icon, and all other applications are now marked by the ![Zscaler Client Connector icon](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/Application%20Segment%20Updates/ZAppIcon.png)
icon.
[]![Application Segment details ](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/Application%20Segment%20Updates/zpa-appsegmentdetails.png)
[]![Edit Application Segment](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/Application%20Segment%20Updates/zpa-editapp.png)

## May 18, 2020
### Feature Available
#### Cloud Updates
The following update was made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released for the ZPA system to issue an error when a SAML response from an identity provider is signed by an expired certificate.

## May 04, 2020
### Feature Available
#### Cloud Updates
The wait time for the browser access service to get a response from a web server has increased from 20 seconds to 300 seconds. This is to ensure the browser access service can support web servers that have a delay in their response.

## April 20, 2020
### Feature Available
#### Cloud Updates
The following updates were made to the Zscaler Private Access (ZPA) Cloud:
- A fix was released to resolve an issue with maintaining a user's connection to the same App Connector.
- A fix was released to address an issue where Zscaler Client Connector (Z App) did not receive the correct port ranges for applications configured in ZPA when the port ranges were configured out of order.
- When a username attribute that was learned via SCIM is updated to a new value, ZPA deletes the former username and its associated information from the database. After this, Zscaler Client Connector will terminate the user’s ZPA session and display a Connection Error if the user is connected to ZPA with the former username. The user has to log out of Zscaler Client Connector and re-log in to connect to ZPA.

## April 10, 2020
### Feature Available
#### App Connector Dashboard
There is now a App Connector dashboard available on the ZPA Admin Portal. This dashboard allows you to monitor the health of your organization's App Connectors and diagnose issues.
[See image.](#dashboard)
From within the dashboard, you can:
- View graphs and charts for elements of a App Connector or that interact with a App Connector.
- Edit the App Connector.
- Access the App Connector Status diagnostic information for a specific App Connector.
[See image.](#chart)
To learn more, see [About the App Connector Dashboard](/zpa/about-connector-dashboard).
Resolved Issues
The following issues were resolved:
- A fix was released to address a traffic steering issue where less optimal App Connectors were selected for Application Segments that were configured with Health Check set to None. This issue was only observed for App Connectors with software version 20.11.20.
[]![App Connector Dashboard](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-connector-dashboard/zpa-connectordashboardpg.png)
[]![CPU graph on App Connector dashboard](/sites/default/files/downloads/zpa/release-notes/release-upgrade-summary-2020/zpa-connector-dashboard/zpa-connectordashboard-cpugraph.png)

## April 01, 2020
### Feature Available
#### User Experience Enhancements
The following user experience enhancements were made to the Zscaler Private Access (ZPA) Admin Portal dashboards:
- Numbers in the banner counters that can be rendered with a comma now will be displayed with the comma. For example, Successful Transactions would previously show a number as 234567. Whereas now, it will appear as 234,567.
- The Application Dashboard and the Users Dashboard were updated to change the default time range from 24 hours to 1 hour to improve usability on the ZPA Admin Portal.
- When selecting a custom date range, the End Date is automatically set to the system's current time.
To learn more, see [About the Applications Dashboard](/zpa/about-applications-dashboard) and [About the Users Dashboard](/zpa/about-users-dashboard).
The following user experience changes were made to the Health dashboard on the Zscaler Private Access (ZPA) Admin Portal:
- When there are more than 200 applications associated with a App Connector, the dashboard will no longer provide a visual representation of those associations when viewing a App Connector.
- The dashboard will no longer show a Servers section.
To learn more, see [About the Health Dashboard](/zpa/about-health-dashboard).
The following changes were made to the Zscaler Private Access (ZPA) Admin Portal:
- During single sign-on (SSO) into the ZPA Admin Portal, a customer's identity provider (IdP) must cryptographically sign the SAML assertion in the response or sign the entire SAML response. ZPA will prevent SSO into the ZPA Admin Portal if either of these two requirements are not met. To learn more, see [About IdP Configuration](/zpa/about-idp-configuration).
Resolved Issues
The following issues were resolved:
- A fix was released to resolve the count mismatch that was occurring between the counts displayed on the Applications and Users dashboards and the count when those data sets were downloaded.
- A fix was released to resolve an issue where application segments, server groups, and access policies were not created or available to update due to a “payload.size.exceeded” error.
- A fix was released to address a problem where some users were logged out of the ZPA Admin Portal after logging in.
- A fix was released to improve search functionality and search response time on the Diagnostic pages. There is now a three character minimum requirement for suggestions to appear in the search drop-down.
- A fix was released to limit the number of suggested entries to 30 in the drop-down list for filters on the Diagnostics page. Administrators will need to specify more granular entries for search values to narrow suggestions in the drop-down list.

## January 27, 2020
### Feature Available
#### Admin Portal UI Warnings for Incomplete Configuration
You can now see warnings when viewing or editing a server, server group, segment group, or application segment that is missing important configuration information.
[See image.](#warn)
To learn more, see [About Servers](/zpa/about-servers), [About Server Groups](/zpa/about-server-groups), [About Segment Groups], and [About Applications](/zpa/about-applications).
[]![Incomplete Configuration Warning for a Segment Group](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/January-27-2020-release-update-summary-admin-portal-ui-warnings-incomplete-configuration/zpa_SegmentGroups_ICW.png)
