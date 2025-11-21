# Release Upgrade Summary (2019)
Source: https://help.zscaler.com/zpa/release-upgrade-summary-2019

This article provides a summary of all new features and enhancements per Zscaler cloud for the ZPA Admin Portal. To see scheduled maintenance updates for your cloud, visit the [Trust Portal](https://trust.zscaler.com).

**Clouds:** private.zscaler.com, zpatwo.net, zpabeta.net, zpapreview.net
The following service updates were deployed to private.zscaler.com on

## November 22, 2019
### Feature Available
#### System for Cross-domain Identity Management (SCIM)
You can now configure SCIM for user and group management. It allows for faster deprovisioning of users from ZPA when you delete them in your user directory. To learn more, see [About SCIM](/zpa/about-scim).
The **Edit IdP Configuration** window allows you to enable SCIM syncing between ZPA and an IdP.
[See image.](#enable)
To learn more, see [Enabling SCIM for Identity Management](/zpa/enabling-scim-identity-management).
When you enable SCIM syncing and configure an IdP for SCIM, the **SCIM Attributes** page allows you to view all SCIM attributes coming from the IdP.
[See image.](#attributes)
To learn more, see [About SCIM](/zpa/about-scim).
Microsoft Azure Active Directory (AD) supports SCIM for ZPA. To learn more, see [About SCIM](/zpa/about-scim) and [SCIM Configuration Guide for Microsoft Azure AD](/zpa/scim-configuration-guide-microsoft-azure-ad).
[]![Enable SCIM](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/november-22-2019-release-update-summary-system-cross-domain-identity-management-scim/SCIM-Enable.png)
[]![SCIM Attributes](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/november-22-2019-release-update-summary-system-cross-domain-identity-management-scim/ZPA-SCIM-attributes-page_blank.png)

## October 30, 2019
### Feature Available
#### Client Forwarding Policy
You can now create policy rules that define when application requests are forwarded to ZPA from the Zscaler Client Connector (Z App). When configuring a client forwarding policy rule, you can apply one of the following actions:
- **Bypass ZPA** - If selected, Zscaler Client Connector (Z App) will not send application requests to ZPA. This setting is the equivalent of selecting **Always** for the **Bypass** setting within an application segment.
- **Only Forward Allowed Applications** - If you only want Zscaler Client Connector to forward user requests for applications that they are allowed to access, select this action. The list of applications that the user has access to is defined by the access policy. To learn more, see [About Access Policy](/zpa/about-access-policies). This setting also controls the list of applications that Zscaler Client Connector processes when evaluating application requests for ZPA. Zscaler Client Connector will forward requests for applications that the user is not allowed to access on their local network. So, these requests will not be logged in Zscaler Client Connector or ZPA.
- **Forward to ZPA** - If selected, Zscaler Client Connector will forward application requests to ZPA. This includes requests to applications that the user is not authorized to access. This is selected by default.
[See image.](#add_clientfwdpolicy)
To learn more, see [About Client Forwarding Policy](/zpa/about-client-forwarding-policy) and [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies).
In addition, the **Add Application Segment** window now displays the following options for the **Bypass **setting:
- **Use Client Forwarding Policy** (formerly **Never**): The decision to forward a user’s application request to ZPA is defined by the client forwarding policy. If none of the policy rules apply, then access to the application is implicitly set to **Forward to ZPA**. This is also the case if you do not define any client forwarding policy rules at all within the ZPA Admin Portal. This option is selected by default.
- **Always**: Users can always bypass ZPA when accessing an application. Only choose this option if you've enabled [dynamic application discovery](/zpa/about-application-access#ApplicationDiscovery) and you want users to access the defined application without ZPA.
- **On Corporate Network**: Users can bypass ZPA when accessing an application from a trusted network. ZPA checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/z-app/configuring-forwarding-profiles-zscaler-app).
[See image.](#bypass)
To learn more, see [Configuring Application Segments](/zpa/about-application/onboard#tab1) and [Configuring Bypass Settings](/zpa/configuring-bypass-settings).
Updates to Diagnostics and Log Streaming Service
In addition to the above changes, the [User Activity](/zpa/about-user-activity-diagnostics), [User Status](/zpa/about-user-authentication-diagnostics), and [App Connector Status](/zpa/about-connector-diagnostics) **Log Types** under **Diagnostics** were all updated to support Client Forwarding Policy field data, and provide user metadata information in particular. The [User Status](/zpa/about-user-status-log-fields) and [User Activity](/zpa/about-user-activity-log-fields) log fields used to define [Log Stream Content](/zpa/configuring-log-receiver#Step2) for the Log Streaming Service (LSS) were also updated.
Resolved Issues
The **SUCCESSFUL** filter that appears at the top of the **Diagnostics **> **User Activity** page now displays the correct abbreviated text when the value is over 100 million (i.e., 100M+ is displayed instead of the complete number).
[]![Add Client Forwarding Policy window with Rule Actions](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/october-30-2019-release-update-summary-client-forwarding-policy/zpa-addclientfwdingpolicy-relnotes.png)
[]![Add Application Segment window with Bypass setting](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/october-30-2019-release-update-summary-client-forwarding-policy/zpa-addapplicationsegment-relnotes.png)

## October 18, 2019
### Feature Available
#### User Experience Improvements to Dashboard
The following enhancements were made to the dashboards within the ZPA Admin Portal in order to improve usability:
- On the **Applications** dashboard, the **Discovered Applications** widget was renamed to **Applications Discovered in Past 14 Days**.
- You can now download application and user information to a file (.csv) for the following widgets on the **Applications** and **Users **dashboards:** [Applications Accessed](/zpa/about-applications-dashboard#aa)**, [**Applications Discovered in Past 14 Days**](/zpa/about-applications-dashboard#da), and [**Recent Users**](/zpa/about-users-dashboard#uaccess).
[See image.](#download)
- The **Applications Accessed** and **Applications Discovered in Past 14 Days** widgets now display the application's port number.
[See image.](#app_port)
To learn more, see [About the Applications Dashboard](/zpa/about-applications-dashboard) and [About the Users Dashboard](/zpa/about-users-dashboard).
[]![Applications Accessed dashboard widget within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/october-18-2019-release-update-summary-user-experience-improvements-dashboard/zpa-appsdashboard-appsaccessed-relnotes.png)
[]![Applications Dashboard within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/october-18-2019-release-update-summary-user-experience-improvements-dashboard/zpa-appsdashboard-relnotes.png)

## September 19, 2019
### Feature Available
#### User Portals for End-Users & Partners
You can now create user portals for your end-users that contain direct links to private and public applications that they have access to.
[See image.](#add_userportal)
A new **User Portal** section within the ZPA Admin Portal' main navigation menu is available, where you can:
- Configure your user portals. To learn more, see [About User Portals](/zpa/about-user-portals).
- Configure the links that appear within your user portals. To learn more, see [About Portal Links](/zpa/about-user-portal-links).
- Configure the download links for the Zscaler Client Connector, so end-users can download and install Zscaler Client Connector directly from a user portal. To learn more, see [About Zscaler Client Connector Download Links](/zpa/about-zscaler-app-download-links).
- Configure an Acceptable Use Policy (AUP) for your user portals. To learn more, see [About User Portal Acceptable Use Policy](/zpa/about-user-portal-acceptable-use-policy).
[See image.](#ex_zpaenduser)
To learn more about how end-users can access and navigate your portals, see [Accessing a User Portal](/zpa/accessing-user-portal).
When an end-user's session expires, the user portal might become unresponsive. If this occurs, they will need to reauthenticate into the portal in order to continue accessing applications.
In addition, the following session status error codes were added and updated:
- ZPA BA: TLS Wrong Version Number (EXPTR_MT_TLS_SETUP_FAIL_VERSION_MISMATCH)
- ZPA BA: CA Not Trusted (EXPTR_MT_TLS_SETUP_FAIL_NOT_TRUSTED_CA)
- ZPA BA: Certificate Chaining Issue (EXPTR_MT_TLS_SETUP_FAIL_CERT_CHAIN_ISSUE)
- ZPA BA: TLS setup failed (EXPTR_MT_TLS_SETUP_FAIL_PEER)
To learn more, see [About ZPA Session Status Codes](/zpa/about-zpa-session-status-codes).
[]![Add User Portal window within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/september-19-2019-release-update-summary-user-portals-end-users-partners/zpa-relnotes-adduserportal.png)
[]![Example user portal for ZPA end-users](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/september-19-2019-release-update-summary-user-portals-end-users-partners/zpa-relnotes-exampleuserportal.png)

## July 12, 2019
### Feature Available
#### DNS Search Domain Enhancements
Within the **DNS Search Domains** window, you can now specify if you want the Zscaler Client Connector (Z App) to resolve invalid domains as NXDOMAINs (non-existent domains).
This functionality is only available to users running Zscaler Client Connector 1.5.1 or later.
In addition, you can now remove domains from the list by mousing over the field and clicking the **Remove** icon:
[See image.](#dns)
To learn more, see [Adding DNS Search Domains](/zpa/about-applications/dnsDomains).
ZPA Admin Portal Enhancements
The following enhancements where made to the ZPA Admin Portal in this release:
- The ability to remove items (i.e., domains, applications, port ranges, etc.) within a configuration using the **Remove** icon. You can also remove the first entry in the list.
[See image.](#remove_icon)
- Zscaler recommends excluding DNS traffic (port 53) from TCP and UDP port ranges within an application segment. So, the **Add/Edit Application Segment** window will display a warning message whenever you attempt to include port 53 within a TCP/UDP port range.
- The **Expand/Collapse All** option was moved to the top of each page.
[See image.](#expand_collapse)
- ZPA now supports a maximum SAML assertion size of 1MB when authenticating users via Browser Access or Zscaler Client Connector (Z App). If a user’s SAML assertion size is greater then 60KB, then Zscaler Client Connector 2.0.1 is required on PCs. For mobile devices, the maximum SAML assertion size that Zscaler Client Connector supports will continue to be 60KB.
[]![DNS Search Domains window within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/july-12-2019-release-update-summary-dns-search-domain-enhancements/zpa-removeicon-x-relnotes.png)
[]![DNS Search Domains window within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/july-12-2019-release-update-summary-dns-search-domain-enhancements/zpa-removeicon-x-relnotes.png)
[]![Expand All Icon within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/july-12-2019-release-update-summary-dns-search-domain-enhancements/zpa-expandcollapseall-relnotes.png)

## June 30, 2019
### Feature Available
#### ZPA Admin Portal User Experience Enhancements
The following enhancements were made to the ZPA Admin Portal in order to improve usability:
- Using the new **Admin Portal Session Timeout** field on the **Administration **> **Settings** page, you can specify how long ZPA admins can be inactive on the Admin Portal before they are logged out.
[See image.](#settings)
To learn more see, [Configuring Authentication Settings](/zpa/configuring-authentication-settings). Also, when adding or editing ZPA admin roles, the **Authentication **access control section was updated to include **Settings**.
[See image.](#admin_roles)
To learn more, see [Configuring Administrator Roles](/zpa/configuring-administrator-roles#Authentication).
- The **Remote Assistance** field was moved from the **Settings** page to the **Help** (![Help icon within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/june-30-2019-release-update-summary-zpa-admin-portal-user-experience-enhancements/zpa-helpicon-relnotes.png)
) menu.
To learn more, see [About Remote Assistance](/zpa/about-remote-assistance).
- You can now search by application segment name, domain name, or IP address on the **Administration **> **Application Segments** page. To learn more, see [About Applications](/zpa/about-applications).
- If you have the [ZPA Read Only Administrator role](/zpa/about-roles), you will now be able to view audit logs. To learn more, see [About Audit Logs](/zpa/about-audit-logs).
[]![Settings page in ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/june-30-2019-release-update-summary-zpa-admin-portal-user-experience-enhancements/zpa-settingspage_relnotes.png)
[]![Add Role window within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/june-30-2019-release-update-summary-zpa-admin-portal-user-experience-enhancements/zpa-addrole-settings-relnotes.png)

## May 23, 2019
### Feature Available
#### Multiple Identity Provider Support for Single Sign-On
You can now add and configure multiple identity providers (IdPs) in order to support single sign-on (SSO) for users and admins. This allows you to add as many IdPs for user and admin SSO as your organization requires, while enabling you to configure policies for the user traffic coming into ZPA from those various IdPs.
The **Add IdP Configuration** window displays a workflow that guides you through the configuration process:
[See image.](#add_idp)
The **IdP Configuration** page also displays new information on each IdP you've configured:
[See image.](#idp_config)
If you have any existing IdP configurations, the IdP will continue to work as desired. However, for the **Single Sign-On** field, the **Both** setting is no longer an option for new IdP configurations as you can now configure as many IdPs as needed for both admin and user SSO.
To learn more, see [About IdP Configuration](/zpa/about-idps) and [Configuring an IdP for Single Sign-On](/zpa/about-idp/new).
When you [import](/zpa/importing-saml-attributes) or [manually add](/zpa/about-samlattribute/new) SAML attributes from an IdP, these attributes are associated to the IdP configuration. The **SAML Attributes** page allows you to view imported and manually added attributes filtered by the **IdP Name**:
[See image.](#saml_attributes)
To learn more, see [About SAML Attributes](/zpa/about-samlattributes).
Your access policy and timeout policy rules can now include SAML attributes that come from a specific IdP, or multiple IdPs, that you have configured for user SSO.
[See image.](#config_policy)
To learn more, see [Configuring Access Policies](/zpa/about-accesspolicy/new) and [Configuring Timeout Policies](/zpa/about-reauthPolicy/new).
Resolved Issues
- A fix was released to resolve an issue where application segment names on the [Application Segments](/zpa/about-applications#appsegs_page) page were are not being displayed in alphabetical order.
- A fix was released to resolve an issue where admins could not fully logout of the ZPA Admin Portal when they authenticated using SSO.
- A fix was released to resolve an issue, which only occurred in certain scenarios, where ZPA incorrectly matched access policy rules for wildcard domains over FQDNs.
[]![Add IdP Configuration window within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/march-23-2019-release-update-summary-multiple-identity-provider-support-single-sign-on/zpa-addidp-step1-relnotes.png)
[]![IdP Configuration page within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/march-23-2019-release-update-summary-multiple-identity-provider-support-single-sign-on/zpa-idpconfig-relnotes.png)
[]![SAML Attributes page within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/march-23-2019-release-update-summary-multiple-identity-provider-support-single-sign-on/zpa-samlattrs-relnotes.png)
[]![Add Access Policy window with SAML Attributes rule criteria](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/march-23-2019-release-update-summary-multiple-identity-provider-support-single-sign-on/zpa-accesspolicy-samlattrs-relnotes.png)

## May 13, 2019
### Feature Available
#### Aggregations and Multi-Value Filters
The ZPA Admin Portal now supports aggregations in the **Dashboard** and multi-value filters in **Diagnostics**.
- [On the Dashboard page:](#dashboard)
- [On the Diagnostics pages:](#diagnostics)
App Connector Health Check Enhancement
For application access over UDP for LDAP (port 389), Kerberos (port 88), and DNS (port 53) a App Connector will perform a TCP health check in addition to the UDP health check for purposes of reporting reachability and data mining RTT.
Session Status Code Updates
The following session status code updates were applied in this release:
- Two new Info session status codes were added:
- "ZEN: Connector closed app TLS connection" (MT_CLOSED_TLS_CONN_GONE_AST_CLOSED)
- "ZEN: Client closed app TLS connection" (MT_CLOSED_TLS_CONN_GONE_CLIENT_CLOSED)
- The "Timeout policy closed idle connection" (BRK_MT_TERMINATED_IDLE_TIMEOUT) session status was moved from a Policy Block code to an Info code.
- The existing "ZEN: TLS session not present" (MT_CLOSED_TLS_CONN_GONE) session status was moved from an Error code to an Info code.
- The "Timeout policy blocked access" (BRK_MT_SETUP_FAIL_REAUTH_EXPIRED) session status no longer applies to Zscaler Client Connector 1.4.3 and later versions, and was deprecated.
To learn more, see [ZPA Session Status Codes](/zpa/zpa-session-status-codes).
Resolved Issues
- A fix was released to resolve an issue where the DNS Search Domains list was being arranged in alphabetical order after save.
- A fix was released which adds a "_deleted" suffix to the names of deleted objects (e.g., App Connector names, application segment names, etc.) in filters on the **Diagnostics** pages.
[]For **Applications**:
- This dashboard highlights aggregates **Access Policy Blocks** and **Successful Transactions** for the specified time range. The aggregate for **Errors** was deprecated.
[See image.](#dashboard_image)
- The **Errors and Policy Blocks** widget was split into two separate widgets: **Top Errors** and **Top Policy Blocks**.
- For **Top Errors**, you can view or drilldown by **Connection Status Codes**, **Applications**, **App Connectors**, and **ZENs** (now Service Edges). You can also filter further into **Diagnostics**.
[See image.](#Top_Errors)
- For **Top Policy Blocks**, you can view or drilldown by **Access Policy Blocks**, and **Timeout Policy Blocks**. You can also filter further into **Diagnostics**.
[See image.](#Top_PolicyBlocks)
- No changes were made to the widgets on the **Users** or **Health** dashboards.
To learn more, see [About the Applications Dashboard](https://help.zscaler.com/zpa/about-dashboard/appsDashboard).
- []You can now view the number of **Timeout Policy Blocks** and **Info **events for the specified time range. **Info** is a new category that highlights application connections that terminated because the user or App Connector abruptly ended the TLS session (e.g., user laptop enters sleep mode which ends the TLS session) or the application's connection gracefully timed out.
- Using the new Query Builder, you can visualize filters and apply them to all log types. Once filters are applied, you can copy the query and share it with other admins with access to the ZPA Admin Portal so they can view the same data.
- For specific fields within the **Diagnostics **table, you can perform further drilldowns into the logs by clicking a **Filter **icon, which automatically adds the filter to the Query Builder.
- You can specify multiple values for all filters to aid in troubleshooting issues.
- Within the **Diagnostics** table, you can copy the log information for the event as well as view the raw logs.
- Real-time events, formerly displayed on the **Diagnostics **page, now appear within the new **Live Logs** page.
- New filters were added to [User Activity Diagnostics](https://help.zscaler.com/zpa/about-diagnostics/txnUsersDiagnostics) for viewing information related to users, policies, ZPA Public Service Edges (formerly Zscaler Enforcement Nodes or ZENs), App Connectors, and applications.
To learn more, see [User Activity Diagnostics](https://help.zscaler.com/zpa/about-diagnostics/txnUsersDiagnostics), [User Status Diagnostics](https://help.zscaler.com/zpa/about-diagnostics/authUsersDiagnostics), [App Connector Status Diagnostics](https://help.zscaler.com/zpa/about-diagnostics/connectorsDiagnostics), and [About Live Logs](https://help.zscaler.com/zpa/about-live-logs).
[]![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/may-13-2019-release-update-summary-aggregations-multi-value-filters/zpa-topaccesserrors.png)
[]![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/may-13-2019-release-update-summary-aggregations-multi-value-filters/zpa-toppolicyblocks.png)
[]![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/may-13-2019-release-update-summary-aggregations-multi-value-filters/zpa-dashboard-relnotes.png)

## April 05, 2019
### Feature Available
#### UI Redesign
The ZPA Admin Portal's design was updated for easier navigation. Menus were consolidated into a single navigation bar on the left of the screen. All workflows remain the same.
[See image.](#newui)
In addition to the improved menu navigation, the following UI enhancements were made:
- You can search for a specific section in the menu navigation bar. To learn more, see [Searching on the ZPA Admin Portal](https://help.zscaler.com/zpa/searching-zpa-admin-portal).
- You can access the [Zscaler Trust Portal](https://trust.zscaler.com/cloud-status) from the Help menu.
- You can show/hide the filters menu within [Diagnostics](https://help.zscaler.com/zpa/dashboard-diagnostics).
Resolved Issues
- A fix was released to resolve an issue where the "ZEN: TLS session not present" (MT_CLOSED_TLS_CONN_GONE) session status was incorrectly displayed as an error code within Diagnostics. Typically, application sessions are closed by the ZPA Public Service Edge when users disconnect from the service and no further action is required. So, this session status now properly displays as a success code within Diagnostics.
- A fix was released that added three new session status codes in order to improve diagnostics and aid in troubleshooting App Connector issues:
- "App Connector: Timeout connecting to server" (AST_MT_SETUP_ERR_OPEN_SERVER_TIMEOUT)
- "App Connector: Error connecting to server" (AST_MT_SETUP_ERR_OPEN_SERVER_ERROR)
- "App Connector: Connection between server and App Connector was closed" (AST_MT_SETUP_ERR_OPEN_SERVER_CLOSE)
For the [March 19, 2019 App Connector Release](/zpa/march-19-2019-connector-release-update-summary) these codes only appeared under **Internal Reason** within Diagnostics. In this release, you can now view these codes within the Dashboard and filter on them within Diagnostics.
To learn more, see [ZPA Session Status Codes](/zpa/zpa-session-status-codes).
![ZPA Admin Portal with new left navigation bar](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/april-5-2019-release-update-summary-ui-redesign/zpa-uiredesign-relnotes.png)
[]

## March 19, 2019
### Feature Available
#### Segment Group Policy Migration
In October 2017, Zscaler began to phase out segment group policy (formerly known as "application group policy") creation under the **Group Policy** tab and consolidate this functionality within [access policy](https://help.zscaler.com/zpa/about-accesspolicy) rules. To learn more, see [Release Update Summary: ZPA Policy Consolidation](https://help.zscaler.com/zpa/release-notes-october-23-2017). In this release, you can easily migrate any existing segment group policy rules to access policy rules using the ZPA Admin Portal.
[See image.](#segmtgrp)
If you want to retain or modify an existing segment group policy rule, you must migrate it. However, if you have already updated your access policy rules to include the proper segment groups, or you simply no longer need these existing segment group policy rules for your organization, you can delete them without migrating.
To learn more, see [Migrating and Deleting Segment Group Policies](https://help.zscaler.com/zpa/about-applicationgrouppolicy/edit).
Copy App Connector Provisioning Key Enhancement
In the **Add App Connector** window, under **6. Deploy App Connector**, a copy button for the **Copy Provisioning Key** field is now available. To learn more, see [Configuring App Connectors](https://help.zscaler.com/zpa/about-connectorprovisioningwizard#vm).
![Edit Segment Group window with Group Policy tab](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/march-19-2019-release-update-summary-segment-group%3Dpolicy-migration/zpa-migratepolicy-relnotes.png)
[]

## February 13, 2019
### Feature Available
#### Access and Timeout Policy Improvements
The following enhancements were made to the **Access Policy** and **Timeout Policy** pages within the ZPA Admin Portal in order to improve usability:
- You can now expand/collapse all rows within the tables.
[See image.](#expandcollapse)
- On the **Access Policy** page, the **Rule Action and Criteria** column was renamed to **Rule Action** and contains information on whether the policy rule is **Allow Access** or **Block Access**.
- On the **Add/Edit Access Policy** window, **Device Posture Profiles** was renamed to **Zscaler Client Connector Posture Profiles**.
- On the **Timeout Policy** page, the **Rule Action and Criteria** column was renamed to **Timeouts** and contains information on the policy rule's **Authentication Timeout** and **Idle Connection Timeout** settings.
- For access and timeout policy rules, you can still view the **Criteria** information for the rule when you expand the row. Under **Criteria**:
- If **Application Segments** or **Segment Groups** are included in the rule, they will link to their applicable edit window.
- Only explicitly configured policy rule criteria will be displayed. In the example image below, **Application Segments**, **SAML Attributes**, and **Zscaler Client Connector Posture Profiles** were explicitly configured for the first policy rule and no criteria was specified in the second rule.
[See image.](#criteria)
To learn more, see [About Access Policies](https://help.zscaler.com/zpa/about-accesspolicy) and [About Timeout Policies](https://help.zscaler.com/zpa/about-reauthPolicy).
Resolved Issues
A fix was released to resolve an issue where adding a new access policy rule, when there were no other policy rules present, caused an error to display within the ZPA Admin Portal.
[]![Access Policy page within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-13-2019-release-update-summary-access-timeout-policy/zpa-accesspolicypage-relnotes.png)
[]![Access Policy page within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-13-2019-release-update-summary-access-timeout-policy/zpa-policyimprov-criteria-relnotes.png)

## February 05, 2019
### Feature Available
#### Custom Support Portal for MSSPs
Managed Security Service Provider (MSSP) partners can now change the [Submit a Ticket](/zpa/getting-started/introduction-zpa-admin-portal#help) URL within the ZPA Admin Portal to a website that is applicable to their organization.
[See image.](#partnerinfo)
To learn more, see [About Partner Information](/zpa/about-partner-information).
Menu and Table User Experience Improvements
The following enhancements were made to the ZPA Admin Portal in order to improve usability:
- Within certain drop-down menus you now have the option to **Select All** application segments or segment groups, where applicable.
[See image.](#SelectAll)
- The ability to search and **Clear Selection** was added to the drop-down menus within the [Audit Logs](/zpa/about-audit-logs) page.
[See image.](#AuditLogs)
- On certain pages, you can now expand/collapse all rows within a table.
[See image.](#ExpandAll)
Resolved Issues
- A fix was released to resolve an issue where logs were not being sent to a log receiver after the receiver's configuration was modified.
- A fix was released to resolve an issue where the **App Connectors **page within the ZPA Admin Portal did not load when the enrollment (CA) certificate could not be found for the App Connector. In this release, if the certificate cannot be found, the page loads and **Not Available** is displayed under **Signing Certificate**.
[]![Partner Information page with Customer Support URL setting for MSSPs](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-5-2019-release-update-summary-custom-support-portal-mssps/zpa-relnotes-zappcertificateicon.png)
[]![Drop-down menu within ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-5-2019-release-update-summary-custom-support-portal-mssps/zpa-selectalloption-relnotes.png)
[]![Drop-down menu within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-5-2019-release-update-summary-custom-support-portal-mssps/zpa-auditlogs-timerange.png)
[]![Collapsed table within the ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/february-5-2019-release-update-summary-custom-support-portal-mssps/zpa-expandalloption-relnotes.png)

## January 23, 2019
### Feature Available
#### User Experience Improvements
The following enhancements were made to the ZPA Admin Portal in order to improve usability:
- The [User Activity Diagnostics](/zpa/about-diagnostics/txnUsersDiagnostics#viewdata) and Application Diagnostics pages were updated to include the following changes:
- Under the **App Connector** column, the **App Connector Group Name** and **App Connector Group ID** fields were added.
- The **Application Segment** column was renamed to **Application**. Under the **Application** column:
- The **Domain or IP Address** field was renamed to **Application**.
- The **Double Encryption** field was added.
To learn more, see [About User Activity Diagnostics](/zpa/about-diagnostics/txnUsersDiagnostics) and [About Application Diagnostics](/zpa/about-applications-dashboard).
- Within the **Administrators** page, the mailto:// hyperlinks on each admin name were removed from the **Admin ID** column. You can also search for a ZPA admin name. To learn more, see [About Administrators](/zpa/about-users).
- Within the **Add/Edit Roles** window, the **Reset to Recommended Settings** option will only appear if you make a selection that differs from the default selection. To learn more, see [Configuring Administrator Roles](/zpa/about-role/new).
- The **Enrollment Certificates** and **Browser Access Certificates** pages, will now display a specific icon and tooltip next to the certificate name, if:
- Your certificate has expired (![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-certificateexpiredicon.png)
).
- Your certificate is due to expire in less than 7 days (![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-certificate7dayicon.png)
).
- Your certificate is due to expire in less than 30 days (![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-certificate30dayicon.png)
).
- You have a certificate request pending, and you need to upload it (![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-certificatependingicon.png)
).
To learn more, see [About Enrollment (CA) Certificates](/zpa/about-EnrollmentCertificates) and [About Browser Access (Web Server) Certificates](/zpa/about-BrowserAccessCertificates).
- The Zscaler Client Connector and Browser Access icons (![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-zappcertificateicon.png)
and ![''''](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-browseraccess-globeicon.png)
) were updated.
- You can now perform full or partial string searches or clear any previous selections within specific drop-down menus.
[See image.](#stringsrch)
Resolved Issues
A fix was released to resolve an issue within [Diagnostics](/zpa/dashboard-diagnostics) where the **Action** (displayed under the **Policy** column) for blocked transactions erroneously changed based on the policy rule action. With this fix, the following transaction details apply within Diagnostics:
- For allow transactions, both the access policy and timeout policy are displayed in the column and their **Action** is set to **Allow**.
- For error transactions, both the access policy and timeout policy are displayed in the column and their **Action** is set to **Allow**.
- For policy block transactions, when the Session Status is:
- "Timeout policy closed idle connection" only the timeout policy is displayed in the column and its **Action** is set to **Deny**.
- "Timeout policy blocked access" only the timeout policy is displayed in the column and its **Action** is set to **Deny**.
- "Application policy blocked access" only the access policy is displayed in the column and its **Action** is set to **Deny**.
- "Policy is not configured for access" only the access policy is displayed in the column with **Access Policy Name**, **Action**, and **Policy ID** set to **Unavailable**.
To learn more, see [ZPA Session Status Codes](/zpa/zpa-session-status-codes).
[]![App Connector Groups drop-down menu within ZPA Admin Portal](/sites/default/files/downloads/zpa/documentation-knowledgebase/release-notes/zpa-release-notes/january-23-2019-release-update-summary-user-experience-improvements/zpa-relnotes-dropdownexample.png)
