# Configuring Defined Application Segments
Source: https://help.zscaler.com/zpa/configuring-defined-application-segments
PDF: https://help.zscaler.com/pdf/com/en/1483606.pdf

When defining a new application within an application segment, you can:
- [Define applications individually](/zpa/about-application-access#AboutApplicationDefinitions) or [enable application discovery](/zpa/about-application-discovery). This includes defining applications for [Browser Access](/zpa/about-BrowserAccess) and for use with ZIA as part of [Source IP Anchoring](/zia/about-source-ip-anchoring).
- Specify the [server groups](/zpa/about-servergroups) hosting the applications.
- Specify the [App Connector groups](/zpa/about-connectorgroups) that have access to those server groups.
For a complete list of ranges and limits per feature, see [Ranges & Limitations](/zpa/ranges-limitations).
If your IdP is defined as an application within an application segment, the [Authentication Timeout](/zpa/about-reauthPolicy/new) for the IdP application must be set to **Never**. If an IdP domain overlaps with a domain configured for [application discovery](/zpa/about-application-discovery), you must bypass the IdP domain in ZPA to avoid user reauthentication failure.
To add an application segment:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **Defined Application Segments**.
- Click **Add Application Segment**.
The **Add Application Segment** window appears.
- In the **Add Application Segment** window:
- [Step 1: Define Applications](#tab1)
- [Step 2: Segment Group](#tab2)
- [Step 3: Server Groups](#tab3)
- [Step 4: Servers](#tab4)
- [Step 5: Review](#tab5)
- [Step 6: Policies](#tab6)
- []If you [defined a Browser Access-enabled application](/zpa/about-application/onboard#tab1) within this application segment, complete the following steps after saving the configuration:
- Go to the [Browser Access](/zpa/about-BrowserAccess#BAPage) page.
- Expand to view the application within the table.
- Click the **Copy** icon next to the **Canonical Name (CNAME)**. You need this CNAME record for your public DNS.
[See image.](#CopyCNAME)
- If you select a custom certificate, add the CNAME information you just copied to your public DNS, and verify that the FQDN for the Browser Access-enabled application resolves to the record. If you selected a Zscaler-managed certificate, Zscaler manages the public DNS entries and verifies the FQDN.
To properly resolve Browser Access-enabled applications, the App Connector must use an internal DNS. If an internal DNS is not used, it results in a DNS loop.
For example, for a CNAME of:
marketing.mockcompany.com. CNAME 3077.217246660302995456.h.d.zpa-app.net.
You would need to verify that marketing.mockcompany.com. resolves to 3077.217246660302995456.h.d.zpa-app.net..
Your users should now be able to access the [applications you defined](/zpa/about-application/onboard#tab1) within the application segment, based upon the [policies](/zpa/about-application/onboard#tab6) applied.
- []On the **Define Applications** tab, provide the necessary details for the following sections:
- [General Information](#define-generalinfo)
- [Inspection Type](#ADProtection)
- [Applications](#define-apps)
- [Client Connector Access](#define-clientconnector)
- [Common Configuration](#define-cmnconfig)
- Click **Next**.
- []**Name**: Enter a name for the application segment. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Enable the application segment. If disabled, the defined applications within the application segment are inaccessible to users.
- **Disaster Recovery**: Enable to designate the application segment for disaster recovery. Application segments that are designated for disaster recovery ensure business continuity in the event of a disaster scenario. For extranet, select **Disabled** since disaster recovery is not supported. This setting is disabled by default. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery) and [About Disaster Recovery Application Segments](/zpa/about-disaster-recovery-application-segments).
Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. To learn more, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
- **Source IP Anchor**: (Optional) Enable Source IP Anchoring. If you are creating this segment for extranet resources, select **Disabled **since Source IP Anchor is not supported.
This setting is tied to Source IP Anchoring for ZIA. When enabled, you can connect to it in ZIA. You can't delete the application while in use by a ZIA entity. There are ranges and limitations for Source IP Anchoring. To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring) and [Ranges & Limitations](/zpa/ranges-limitations#ApplicationManagement).
- **Description**: (Optional) Enter a description.
- **Inspect Traffic with ZIA**: Enable to leverage single posture for securing internet or SaaS and private applications and apply Data Loss Prevention policies to the application segment you are creating. If **Source IP Anchor** is enabled, you must disable it prior to enabling **Inspect Traffic with ZIA** as both features cannot be enabled at the same time.
[See image.](#img-define-gnrlinfo)
- []**Active Directory Inspection**: Enable to allow this application segment's traffic to be inspected by Active Directory Inspection. The Active Directory Inspection data can be found on the [AD Protection Diagnostics page](/zpa/accessing-ad-protection-diagnostics). This setting is disabled by default.
- **Auto AppProtection**: Enable to allow this application segment's traffic to be inspected by AppProtection. If enabled, you will need to [generate an Enrollment (CA) Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates). If you are creating this segment for extranet resources, select **Disabled **since AppProtection is not supported. This setting is disabled by default.
If **Active Directory Inspection** is enabled, then **Auto AppProtection** cannot be enabled. If **AppProtection** is enabled, **Active Directory Inspection** cannot be enabled.
[See image.](#ADinspection)
- []Enter a fully qualified domain name (FQDN), IP address, local domain, or a wildcard domain (e.g., *.safemarch.com) associated with the application. You can't define an application with hyphenated IP address ranges (e.g., 192.168.0.1–10).
You can also define the application with a wildcard only (i.e., *), but this should be the only application in the application segment. You can't define an application this way unless approved by Zscaler. Contact Zscaler Support for more information.
The following guidelines apply to configuring FQDNs:
- For some applications, the domain name might be the same as the server name (e.g., RDP and file servers).
- For applications that users access using host names (e.g., DFS), ensure that you [configure DNS search suffixes](/zpa/about-applications/dnsDomains) so that ZPA can automatically add the search domain to the host name.
When defining applications for Browser Access, you can only configure FQDNs.
To learn more, see [Defining an Application](/zpa/about-application-access#AboutApplicationDefinitions) and [Configuring Application Discovery](/zpa/about-application-discovery#config_appdiscovery).
[See image.](#img-define-apps)
- []Select the **Browser Access** checkbox to enable Browser Access for an application, and then [complete the following steps.](#BAsteps)
- []Select the **Inspect AppProtection Application** checkbox to enable AppProtection for an application, and then [complete the following steps.](#protectsteps)
- Select the **Privileged Remote Access** checkbox to enable Privileged Remote Access for an application, and then [complete the following steps.](#PRAsteps)
[]ZPA Browser Access requires that the application server supports TLS 1.2 encryption.
- (Optional) Enter a domain in the **Domain for Browser Isolation** field that ZPA can use in place of the application domain for browser isolation. To learn more, see [What Is Isolation?](/zia/about-cloud-browser-isolation)
- Select the certificate type. If you select **Custom**, continue with the following substeps. If you want to use a Zscaler-managed certificate, select **Managed** and go to the next step.
-
From the drop-down menu, select the protocol (**Dynamic**, **HTTP**, or **HTTPS**). The **Dynamic** protocol option allows the certificate to be [generated by the AppProtection Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates). This option is handled by the back end that the application domain is mapped to. If you select this option, you can view the Protocol Discovery details on the [Protocol Discovery Dashboard page](/zpa/viewing-protocol-discovery-dashboard), along with the diagnostics for the related ports on the [Protocol Discovery Diagnostics page](/zpa/accessing-protocol-discovery-diagnostics). If you want to select **HTTP** or **HTTPS**, if your web server supports **HTTPS**, select this protocol. Otherwise, select **HTTP**. You can click **Clear Selection** to remove any selections.
ZPA inserts a Via header in HTTP requests made using Browser Access.
- If you selected **Enabled **for **Active Directory Inspection**, the drop-down menu includes the **Active Directory Protocol** options **LDAP**, **SMB**, and **Kerberos**.
You can also select the Active Directory protocol options from the **Default Port Ranges** drop-down menu.
-
Enter the port number. By default, port **80** is entered for **HTTP** and **443** is entered for **HTTPS**. If **Active Directory Inspection** is enabled, additional drop-down menus are provided to the right of the port range fields with the options **Inspect None**, **Inspect LDAP**, **Inspect SMB**, and **Inspect Kerberos**. If an Active Directory Inspection-enabled application segment contains a domain or port range that is different from the set protocol traffic, it cannot be inspected.
[See image.](#inspectoptions)
- Enter the port number. By default, port **80** is entered for **HTTP** and **443** is entered for **HTTPS**.
- Select a web server certificate from the drop-down menu. You can click **Clear Selection** to remove any selections. To learn more, see [About (Web Server) Certificates](/zpa/about-web-server-certificates).
- (Optional) If you select **Managed** as the **Certificate Type**, the following fields appear:
- For **External URL**, enter the domain prefix that you want the certificate managed by Zscaler to be assigned to.
- Select the domain suffix from the drop-down menu that you want the certificate managed by Zscaler to be assigned to.
- Click the **Copy** icon to copy the URL.
- For **Internal URL**, select **HTTP **or **HTTPS **from the drop-down menu. If your web server supports HTTPS, select this protocol.
- Enter the domain for the internal URL.
-
Enter the port number. By default, port **80** is entered for **HTTP **and **443 **is entered for HTTPS.
[See image.](#manage)
- []If you selected **HTTPS** previously, **Use Untrusted Certificates** is selected by default. If this setting is not selected, requests to access the application using untrusted web server certificates are not successful.
- Selecting **Use Untrusted Certificates **results in successful application connectivity, regardless of verification of the certificate.
-
(Optional) Select **Allow Unauthenticated OPTIONS Request** to allow ZPA to forward an unauthenticated HTTP preflight OPTIONS request from the browser to the application.
ZPA only accepts valid OPTIONS requests that include the headers Access-Control-Request-Headers, Access-Control-Request-Method, and Origin in the HTTP request. If these are not present, ZPA doesn't forward the OPTIONS request to the application.
ZPA accepts CORS requests if the requests are issued by one valid Browser Access domain to another Browser Access domain. The application server requires `with credentials mode` be added to JavaScript. This is to allow the browser to pass cookies to the JavaScript front end. The application server must also allow requests where the Origin header is set to null or to a valid Browser Access application.
[See image.](#BrowserAccess)
[]If you enable **AppProtection**, then **Inspect AppProtection Application** is selected by default.
-
Select a web server certificate from the drop-down menu. You can click **Clear Selection** to remove any selections. To learn more, see [About (Web Server) Certificates.](/zpa/about-BrowserAccessCertificates)
The same certificate is used if **Browser Access** is also selected.
-
From the drop-down menu, select the protocol you want ZPA to use when a request is made to access the application (**Dynamic**, **HTTPS**, or **HTTP**). The Dynamic protocol option allows the certificate to be [generated by the AppProtection Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates). This option is handled by the back end that the application domain is mapped to. If you select this option, you can view the Protocol Discovery details on the [Protocol Discovery Dashboard page](/zpa/viewing-protocol-discovery-dashboard), along with the diagnostics for the related ports on the [Protocol Discovery Diagnostics page](/zpa/accessing-protocol-discovery-diagnostics). If you want to select **HTTP** or **HTTPS**, if your web server supports **HTTPS**, select this protocol. Otherwise, select **HTTP**. You can click **Clear Selection** to remove any selections.
To select both **Browser Access** and the **AppProtection**, **HTTP** or **HTTPS** needs to be selected.
-
If you selected **HTTP** in step ii above, **Use Untrusted Certificates** is selected by default. Select **Use Untrusted Certificates** to allow inspection with private certificates. This option maintains the TLS connection between the inspection and the application. The verification of the private CA certificate would otherwise fail if this option wasn’t selected. If you do not select **Use Untrusted Certificates** and you are using private CA certificates that are not verified by ZPA, requests to access applications with inspection fail. If you enable **AppProtection**, then the **Use Untrusted Certificates** option is selected by default. This is because it needs to be selected to verify the CA certificate related to the AppProtection-enabled applications. If you deselect the **Use Untrusted Certificates** checkbox, the App Connector verifies the certificate of the server. Since it’s a self-signed certificate and not recognized by CA, it cannot be established and fails.
Selecting **Use Untrusted Certificates** results in successful application connectivity, regardless of verification of the certificate.
If **Browser Access** and **AppProtection** are selected, the **Use Untrusted Certificates** checkbox is automatically selected. To use the Browser Access feature, this option needs to remain selected.
[See image.](#Applications-InspectApplication)
[]Privileged Remote Access requires that the application server supports VNC, RealVNC, SSH, or RDP.
-
Select the privileged console from the **Protocol** drop-down menu. You can select **VNC**, **RealVNC**, **SSH,** or **RDP**.
If you select RDP for Windows, Microsoft recommends configuring network-level authentication. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-allow-access#why-allow-connections-only-with-network-level-authentication).
-
Enter the port number for the VNC, RealVNC, SSH, or RDP. By default, port 5900 is entered for VNC and RealVNC, port 3389 is entered for RDP, and port 22 is entered for SSH.
If you want to use the File Transfer feature with a VNC-enabled or RealVNC-enabled privileged console, you need to additionally enter port 22 for both the TCP and UDP port ranges. You need to run SSH on port 22 on the target machine where the VNC or RealVNC server is running. The SSH credentials must be the same as the VNC or RealVNC credentials.
-
(Optional) If you select **RDP**, you need to enter the Connection Security. You can select **TLS**, **RDP**, or **NLA**. If the application server you select has network-level authentication enabled, select **Any** to provide access to the server.
[See image.](#PRAbox)
Client-based remote assistance is only available for end users connecting to ZPA using Zscaler Client Connector.
-
Click **Add More** to add more domains or IP addresses for each application you want to define.
When two or more application segments cover the same destination address, Zscaler Client Connector attempts to match traffic to the more granular application segment. If there is no match in this application segment, Zscaler Client Connector bypasses ZPA and sends traffic directly. To learn more, see [About Application Access](/zpa/about-application-access).
- []**Default Port Ranges**: Enter the port ranges to set as the default for the application segment.
- **TCP Keepalive**: Enables the App Connector to periodically send TCP keepalives to an application server when a user has accessed that server on a TCP port. This setting is disabled by default. To learn more, see [Networking Deployed App Connectors](/zpa/networking-deployed-connectors#Tcpcommunication).
- **TCP Port Ranges**: Enter the TCP port ranges that can be used to access the application.
For example, if you want to specify the port range 80 to 90, for **From...** enter 80, and for **To...**, enter 90. If you only want to specify one port, you can enter the same number (e.g., 80) for **From...** and **To...**.
If you selected **Browser Access** for any application, the port range must include the port specified.
Click **Add More** to add more TCP port ranges.
- **UDP Port Ranges**: Enter the UDP port ranges that can be used to access the application.
For example, if you want to specify the port range 90 to 94, for **From...**, enter 90, and for **To...**, enter 94. If you only want to specify one port, you can enter the same number (e.g., 90) for **From...** and **To...**.
If you selected **Browser Access** for any application, you must use TCP port ranges.
Click **Add More** to add more UDP port ranges.
Zscaler recommends excluding DNS traffic (port 53) from TCP and UDP port ranges.
- **Double Encryption**: Traffic between Zscaler Client Connector and the ZPA Public Service Edge is encrypted using TLS 1.2 by default. Enable double encryption if you want to enable a second layer of encryption for traffic between Zscaler Client Connector on your users' devices and the App Connector that provides them with access to your enterprise applications.
If you selected **Browser Access **or** Source IP Anchoring** for any application, you can’t enable **Double Encryption**. Additionally, extranet applications don't use a traditional App Connector, so double encryption should be disabled if you're creating an application segment for it.
To learn more, see [Understanding Double Encryption](/zpa/understanding-double-encryption).
- **Bypass**: From the drop-down menu, choose when users can bypass ZPA to access an application. You can choose from the following options:
- **Use Client Forwarding Policy**: This option is selected by default. If selected, the decision to forward a user’s application request to ZPA is defined by the [client forwarding policy](/zpa/about-client-forwarding-policy). If none of the policy rules apply, then access to the application is implicitly set to **Forward to ZPA**. To learn more, see [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies). This is also the case if you do not define any client forwarding policy rules at all within the ZPA Admin Portal.
- **Always**: If selected, users can always bypass ZPA when accessing an application.
- **On Corporate Network**: If selected, users can bypass ZPA when accessing an application from a trusted network. ZPA checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/z-app/configuring-forwarding-profiles-zscaler-app).
You can click **Clear Selection** to remove any selections.
The **Bypass** setting within an application segment always takes precedence over any newly added client forwarding policy rule. To learn more, see [Configuring Bypass Settings](/zpa/configuring-bypass-settings). Also, if the same FQDN is defined in multiple application segments, and one of them has the **Bypass** setting set to **Always**, then that application segment takes precedence.
- **ICMP Access**: Enable for various ZPA clients (Zscaler Client Connector, Cloud and Branch Connectors, or Source IP Anchor) to allow ICMP communication to the applications in this Application Segment. By default, this is set to **Disabled**. ZPA allows or blocks ICMP requests based on [access policies](/zpa/about-access-policy). If you configure an application for ICMP Access, there are some things to consider when using ICMP with ZPA:
- If ICMP is enabled for a specific application in an application segment and the same application is disabled for ICMP in a different application segment, then Zscaler Client Connector considers ICMP enabled for that application and forwards the ICMP request to ZPA.
- Zscaler Client Connector doesn't intercept ICMP requests for a destination IP that has the same subnet as the user's machine since this is considered an unreachable host.
- The [IP](/zpa/about-user-activity-diagnostics#connector) data appears and the Internal Status Code on the [User Activity Diagnostics page](/zpa/about-user-activity-diagnostics#time) shows as successful (e.g., BRK_MT_TERMINATED) after the App Connector is selected, even though it is unreachable. This can occur if the App Connector is set up to provide on access or no [health reporting](/zpa/understanding-health-reporting), as health reporting does not work well with ICMP.
- If an application is blocked based on an [access policy](/zpa/about-access-policy), Zscaler Client Connector creates a new Microtunnel request for every ICMP echo request.
- ICMP does not work with Double Encryption, so you might not want to enable Double Encryption for application segments where you enabled ICMP.
- **Bypass during Reauthentication**: Choose whether application access during reauthentication bypasses ZPA (**Enabled**) or not (**Disabled**). For example, if your IdP is configured to do multi-factor authentication (MFA) for off-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts the user for MFA. For on-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts them for MFA. This feature requires Zscaler Client Connector version 4.3 or later for Windows, macOS, and iOS.
[See image.](#img-define-clientcnntr)
- [][]**Health Reporting**: Choose whether the App Connector reports the health status of all applications within an application segment continuously (**Continuous**), while a user is accessing it (**On Access**), or not at all (**None**). The default setting is **On Access**. If you are creating the segment for an extranet application, select **None**. You can see the status of the application on the [Health dashboard](/zpa/about-dashboard/health). To learn more, see [Understanding Health Reporting](/zpa/understanding-health-reporting).
You can't choose **Continuous** health reporting for applications configured with more than 10 ports or if any of the applications in the application segment are defined with only a wildcard (e.g., *). Additionally, if an application has client hostname validation enabled to facilitate client-to-client remote assistance, then the application is not shown on the Health Dashboard. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
- **App Connector Selection Method**: Choose **Closer to Application** if you prefer the App Connector is closest to the application to be selected. By default, ZPA chooses the App Connector as closest to the user (**Closer to User**). After you make a selection, ZPA selects an App Connector that has the shortest round-trip time towards the requested application.
This setting supports only TCP applications. The limit for the number of targets that check the health of the defined applications at the App Connector is 6,000. If this limit is exceeded, then the **Health Reporting** of the application is set to **None**, and a random selection of App Connectors is chosen.
If Health Reporting is set to **None**, the **App Connector Selection Method** feature cannot be enabled and an error message appears.
- **Client Connector can receive CNAME**: Choose whether App Connectors resolve CNAME records. This setting is enabled by default, and Zscaler Client Connector receives CNAME DNS records from the App Connector. Disabling means App Connectors do not send CNAME DNS records.
This setting is not applicable for Browser Access applications, and ZPA functions as if the option is disabled. If Zscaler Client Connector is on a macOS or an iOS device and the application needs to be accessed by CNAME, it is best to disable this setting.
- **Multimatch**: Enable to configure inclusive policies that allow an application request to match multiple application segments. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
Multimatch is not supported for applications that have Browser Access, Privileged Remote Access, AppProtection, or Source IP Anchoring enabled. If Multimatch is enabled, Health Reporting on an app segment can only be set to **On Access** or **None**. To learn more about limitations, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
[See image.](#img-define-cmmnconfig)
[]![General Information section for Define Applications in the Add Application Segment window within the ZPA Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-defined-application-segments-draft-doc-47541/Updated%20app%20segment%20inspect%20zia.png)
[]![Inspection Type options](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Updated%20app%20segment%20inspection%20types.png)
[]![Applications section for Define Applications in the Add Application Segment window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/Application%20access%20type.png)
[]![Client Connector Access section for Define Applications in the Add Application Segment window within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/zpa-configuring-app-segments-client-connector2.png)
[]![Enable or disable the following options.](/downloads/tech-pubs-drafts/zpa-draft-articles/configuring-defined-application-segments-draft-doc-47400/zpa-common-configuration-app-segment-config-1.png)
[]You must identify the segment group to which this application segment belongs. Placing the application segment in a segment group allows you to configure user [access policies](/zpa/about-policies) based on that group.
On the **Segment Group** tab, choose one of the following options, and configure the group accordingly:
- [Select Segment Group](#selectappgroup)
- [Add Segment Group](#createappgroup)
[]Choose an existing segment group from the drop-down menu, and click **Next**. You can search for a specific group or click **Clear Selection** to remove any selections.
[See image.](#seeimage4)
[]![Select Segment Group Section](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-c2c-configuring-application-segments.png)
- []Click **Add Segment Group**:
- **Name**:** **Enter a name for the segment group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description for the segment group.
- **Status**: Make sure that the segment group is enabled.
[See image.](#seeimage5)
- Click **Next**.
[]![Create a segment group section](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-c2c-configuring-application-segments2.png)
[]You must identify the server groups in your enterprise data center that host the applications you've defined.
On the **Server Groups** tab, choose one of the following options to configure the server group accordingly, or select **Skip** if you want to enable client-to-client remote assistance. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
When you configure server groups, only group servers that are capable of hosting the same applications.
- [Select Server Group](#selectservergroup)
- [Add Server Group](#createservergroup)
[]
- Under **Server Group Type**:
- Select **App Connector **to connect to applications that are available on your network.
-
Select **Extranet **to connect to a partner site or offshore development center that is not directly available on your organization’s network.
**Extranet **only appears if your organization has the Extranet Application Support feature enabled. To learn more, see [About Extranet](/zia/about-extranet).
If you select **Extranet**, choose **Extranet Resource** and select a partner that was configured in ZIA to connect to the application. You can choose only one partner.
- Select an existing server group from the drop-down menu, and click **Next**. You can search for a specific group, click **Clear Selection** to remove any selections, or select **Skip**.
[See image.](#seeimage7)
[]![Selecting an existing server group for an application within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/zpa-c2c-configuring-application-segments3.png)
- []Click **Add Server Group**:
- **Name**:** **Enter a name for the server group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**:** **(Optional) Enter a description for the server group.
- **Status**:** **Make sure that the server group is enabled.
- **Dynamic Server Discovery**: If enabled, ZPA automatically discovers the appropriate servers for applications as users request the applications. If disabled, you must manually add defined servers to the server group.
- **Connector Type: **Choose one of the following options:
-
Select** App Connector **to use an ZPA App Connector to connect to applications that are available on your network.
If you select** App Connector**, choose the **App Connector Groups **that have access to the data center or virtual private cloud (VPC) that contains the servers in this server group, and click **Done**. You can search for a specific group, or click **Clear Selection** to remove any selections.
-
Select **Extranet **to use ZPA to connect to an application at a partner site or offshore development center that is not directly available on your organization’s network, and then choose options for connecting to that site:
Make sure that you set extranet options at the tenant level as Microtenants aren't supported.
- **Extranet Resource: **Choose a partner outside your organization that was configured in ZIA to connect to the application. You can choose only one partner per server group.
-
**Extranet Location Groups: **Choose a location group if your organization created extranet location groups in ZIA. The location group represents the set of all the IPSec tunnels that can reach the application at partner locations.
You can expand the location group to view all locations associated with that group. If you want to include all those locations, you do not need to select an option for **Extranet Locations**. If you want to select a subset of those locations, you can select those in **Extranet Locations**.
- **Extranet Locations: **Choose the locations that can reach the application at a partner site using an IPSec tunnel.
[See image.](#seeimage8)
- Click **Next**.
[]![Creating a new server group for an application within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/zpa-c2c-configuring-application-segments4.png)
[]If you selected **App Connector** for the server group, you must add servers to the server group you just created. On the **Server **tab, choose one of the following options, and configure the server accordingly.
- [Select Server](#selectserver)
- [Add Server](#createserver)
If you selected **Extranet** for the server group, continue to Step 5: Review.
- []Choose one or more existing servers from the drop-down menu, and click **Done**. You can search for a specific group, or click **Clear Selection** to remove any selections. If you selected an existing server group in the previous step, then any servers within that group automatically populate this field.
[See image.](#seeimage10)
- Click **Next**.
[]![Select an existing server section](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-c2c-configuring-application-segments5.png)
- []Click **Add Server**:
- **Name**: Enter a name for the server. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the server.
- **Status**: Make sure that the server is enabled.
- **Domain or IP Address**: Enter a fully qualified domain name (FQDN) or an IP address for the server.
[See image.](#seeimage11)
- Click **Next**.
[]![Create a new server section](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-c2c-configuring-application-segments6.png)
[]On the **Review** tab, review your application segment configuration, then click **Save**.
[See image.](#seeimage12)
[]![Add Application window with Review tab](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-c2c-configuring-application-segments7.png)
[]On the **Policies** tab, you see a list of access policies that are applied to the applications defined within the application segment. If you need to add new or modify existing policies, click **Edit Policy**. To learn more, see [About Access Policy](/zpa/about-access-policy).
If you do not need to make any policy changes, click **Cancel**.
[]![Add Application window with Policies tab](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/zpa-addapp-policies.png)
[]![Add Application Segment window with Application section and Browser Access checkbox selected](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/BA%20access%20type.png)
[]![Add Application Segment window with Applications section and Inspect Application checkbox selected](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/Inspect%20access%20type.png)
[]![Add Application Segment window with Applications section and Privileged Remote Access checkbox selected](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Config%20App%20Segment_0.png)
[]![Application Segment page with Canonical Name (CNAME) within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/zpa-appsegment-copycname.png)
[]![Active Directory Inspection port range options in the Add Application Segment window](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Config%20port%20range.png)
[]![Selecting the Managed Certificate Type for Browser Access in the Adding Application Segment window](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Config%20app%20segment%20with%20BA.png)