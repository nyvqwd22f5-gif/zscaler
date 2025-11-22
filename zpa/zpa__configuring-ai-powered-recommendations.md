# Configuring AI-Powered Recommendations
Source: https://help.zscaler.com/zpa/configuring-ai-powered-recommendations
PDF: https://help.zscaler.com/pdf/com/en/1485171.pdf

AI-powered recommendations for application segments provide you with helpful configuration options and additional application segment opportunities for your consideration. When you find an AI-powered recommendation that you want as a defined application segment, you can [merge it with an existing defined application](/zpa/merging-recommended-application-segments), or you can add the AI-powered recommendation on its own. You can configure the requirements for AI-powered recommendations on the [Application Segments Settings](/zpa/about-application-segments-settings) page. This article provides steps to configure an AI-powered recommendation to become a defined application segment and move it to the **Defined Application Segments** page.
The AI-Powered Recommendations page is only populated with data for users who have activated it. To activate this feature, click **Activate Recommendations** on the AI-Powered Recommendations page.
To add an AI-powered recommendation to the **Defined Application Segments** page:
- Go to **Resource Management** > **Application Management** > **Application Segments** > **AI-Powered Recommendations**.
-
Locate the AI-powered recommendation you want to add to the Defined Application Segments page, and click the **Add **icon.
The **Add AI-Powered Recommendation **window appears.
- In the **Add AI-Powered Recommendation** window:
- [Step 1: AI-Powered Recommendation](#Step1)
- [Step 2: Define Applications](#Step2)
- [Step 3: Segment Group](#Step3)
- [Step 4: Server Groups](#Step4)
- [Step 5: Servers](#Step5)
- [Step 6: Review](#Step6)
- [Step 7: Policies](#Step7)
After you have successfully added the AI-powered recommendation, it appears on the Defined Application Segments page as a defined application segment.
[]On the **AI-Powered Recommendation** tab:
- Review the following prepopulated information for the selected AI-powered recommendation:
- **Name**:** **The name of the application segment for the application.
- **Attack Surface Reduction**: The percentage reduction in the attack surface (i.e., percentage difference between potential users and recommended users). All recommendations that provide greater than a 75% reduction are presented.
- **Current Configuration**: The number of Applications, Defined Application Segments, and Current Users.
- **Recommended Configuration**: The number of Applications, Recommended Users, and Observed Users for the AI-Powered recommendation.
-
**Recommended Users**: If [SCIM Sync](/zpa/enabling-scim-identity-management) is enabled, the number of suggested users for this recommended application segment is displayed. Click the number of users to list the recommended users. You can search by email.
If SCIM Sync or SCIM Attributes for Policy are not enabled, the user recommendations appear as N/A in the recommendations.
- **Recommended Basis**: Lists the recommendation's basic information to configure.
- **Number of Transactions**:** **The total number of transactions.
- **TCP Port Ranges**:** **The TCP port ranges used to access applications.
- **UDP Port Ranges**:** **The UDP port ranges used to access applications.
- **Grouping Reasons**:** **The 5 categories that a recommended application segment can be grouped by (**IP Similarity**, **User Access Similarity**, **Domain Name Similarity**, **Co-occurring Applications Similarity**, and **Ports and Protocols Similarity**).
- **Description**: Information about the recommendation.
- **Applications**: The list of applications assigned to the selected application segment. Click **Next** or **Previous** at the bottom of the table to view additional applications. You can filter the information that appears in the table. By default, no filters are applied.
- **Application**: The name of the application.
- **Defined Application Segment**: The defined application segment merged with this application, if applicable.
- **Port and Protocol**: The web server port and protocol used by the application.
- **Server IP**: The web server IP address (e.g., 192.0.2.0).
- Click **Next**.
[See image.](#tab1)
[]
![Add Recommended Application Segment window.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-Recommendation.png)
[]
-
Check the following prepopulated information for the AI-powered recommendation:
- [][General Information](#define-generalinfo)
- [Applications](#define-apps)
- [Client Connector Access](#define-clientconnector)
- [Common Configuration](#define-cmnconfig)
[See image.](#img_define-apps)
- Click **Next**.
AI-Powered recommendations do not support Extranet.
- []**Name**: Enter a name for the application segment. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Enable the application segment. If **Disabled**, the defined applications within the application segment are inaccessible to users.
-
**Disaster Recovery**: Enable to designate the application segment for disaster recovery. Application segments that are designated for disaster recovery ensure business continuity in the event of a disaster scenario. Disaster recovery is disabled by default. To learn more, see [Understanding Disaster Recovery](/zpa/understanding-disaster-recovery) and [About Disaster Recovery Application Segments](/zpa/about-disaster-recovery-application-segments).
Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. To learn more, see [Creating DNS TXT Records](/zpa/creating-dns-txt-records).
-
**Source IP Anchor**: (Optional) Enable Source IP Anchoring.
This setting is tied to Source IP Anchoring for ZIA. When enabled, you can connect to it in ZIA. You can't delete the application while in use by a ZIA entity. There are ranges and limitations for Source IP Anchoring. To learn more, see [About Source IP Anchoring](/zia/about-source-ip-anchoring) and [Ranges & Limitations](/zpa/ranges-limitations#ApplicationManagement).
- **Description**: (Optional) Enter a description.
-
[]Enter a fully qualified domain name (FQDN), IP address, local domain, or a wildcard domain (e.g., *.safemarch.com) associated with the application. You can't define an application with hyphenated IP address ranges (e.g., 192.168.0.1–10).
You can also define the application with a wildcard only (i.e., *), but this should be the only application in the application segment. You can't define an application this way unless approved by Zscaler. Contact Zscaler Support for more information.
The following guidelines apply to configuring FQDNs:
- For some applications, the domain name might be the same as the server name (e.g., RDP and file servers).
- For applications that users access using host names (e.g., DFS), ensure that you [configure DNS search suffixes](/zpa/about-applications/dnsDomains) so that ZPA can automatically add the search domain to the host name.
When defining applications for Browser Access, you can only configure FQDNs.
To learn more, see [Defining an Application](/zpa/about-application-access#AboutApplicationDefinitions) and [Configuring Application Discovery](/zpa/about-application-discovery#config_appdiscovery).
- []Select the **Browser Access** checkbox to enable browser access for an application, and then [complete the following steps.](#BAsteps)
- Select the checkbox to enable **Privileged Remote Access** for an application, and then [complete the following steps.](#PRAsteps)
[]ZPA Browser Access requires that the application server supports TLS 1.2 encryption.
- Select a web server certificate from the drop-down menu. You can click **Clear Selection** to remove any selections. To learn more, see [About (Web Server) Certificates](/zpa/about-BrowserAccessCertificates).
- (Optional) Enter a domain in the **Domain for Browser Isolation** field that ZPA can use in place of the application domain for browser isolation. To learn more, see [What Is Isolation?](/zia/about-cloud-browser-isolation)
- From the drop-down menu, select the certificate you want ZPA to use when a request is made to access the application. If your web server supports **HTTPS**, select this protocol from the drop-down menu. Otherwise, select **HTTP**. You can click **Clear Selection** to remove any selections.
-
From the drop-down menu, select the protocol (**Dynamic**, **HTTP**, or **HTTPS**). The **Dynamic** protocol option allows the certificate to be [generated by the AppProtection Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates). This option is handled by the back end that the application domain is mapped to. If you select this option, you can view the Protocol Discovery details on the [Protocol Discovery Dashboard page](/zpa/viewing-protocol-discovery-dashboard), along with the diagnostics for the related ports on the [Protocol Discovery Diagnostics page](/zpa/accessing-protocol-discovery-diagnostics). If you want to select **HTTP** or **HTTPS**, if your web server supports **HTTPS**, select this protocol. Otherwise, select **HTTP**. You can click **Clear Selection** to remove any selections.
ZPA inserts a Via header in HTTP requests made using Browser Access.
If you selected **Enabled** for **Active Directory Inspection**, the drop-down menu includes the **Active Directory Protocol** options **LDAP**, **SMB**, and **Kerberos**.
You can also select the Active Directory protocol options from the **Default Port Ranges** drop-down menu.
-
Enter the port number. By default, port **80** is entered for **HTTP** and **443 **is entered for **HTTPS**.
If **Active Directory Inspection** is enabled, additional drop-down menus are provided to the right of the port range fields with the options **Inspect None**, **Inspect LDAP**, **Inspect SMB**, and **Inspect Kerberos**.
If an Active Directory Inspection-enabled application segment contains a domain or port range that is different from the set protocol traffic, it cannot be inspected.
[See image.](#inspectoptions)
-
[]If you selected **HTTPS** in step iv, **Use Untrusted Certificates** is selected by default. If this setting is not selected, requests to access the application using untrusted web server certificates are not successful.
Selecting **Use Untrusted Certificates **results in successful application connectivity, regardless of verification of the certificate.
- (Optional) Select **Allow Unauthenticated OPTIONS Request** to allow ZPA to forward an unauthenticated HTTP preflight OPTIONS request from the browser to the application.
ZPA only accepts valid OPTIONS requests that include the headers Access-Control-Request-Headers, Access-Control-Request-Method, and Origin in the HTTP request. If these are not present, ZPA doesn't forward the OPTIONS request to the application.
ZPA accepts CORS requests if the requests are issued by one valid Browser Access domain to another Browser Access domain. The application server requires `with credentials mode` be added to JavaScript. This is to allow the browser to pass cookies to the JavaScript front end. The application server must also allow requests where the Origin header is set to null or to a valid Browser Access application.
[]Privileged Remote Access requires that the application server supports VNC, RealVNC, SSH, or RDP.
- Select the privileged console from the **Protocol** drop-down menu. You can select **VNC**, **RealVNC**, **SSH**, or **RDP**.
If you select RDP for Windows, Microsoft recommends configuring network-level authentication. To learn more, refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-allow-access#why-allow-connections-only-with-network-level-authentication).
- Enter the port number for the VNC, RealVNC, SSH, or RDP. By default, port 5900 is entered for VNC and RealVNC, port 3389 is entered for RDP, and port 22 is entered for SSH.
If you want to use the File Transfer feature with a VNC-enabled or RealVNC-enabled privileged console, you need to additionally enter port 22 for both the TCP and UDP port ranges. You need to run SSH on port 22 on the target machine where the VNC or RealVNC server is running. The SSH credentials must be the same as the VNC or RealVNC credentials.
- (Optional) If you select **RDP**, you need to enter the Connection Security. You can select **TLS**, **RDP**, or **NLA**. If the application server you select has network-level authentication enabled, select **Any** to provide access to the server.
[See image.](#PRAbox)
Client-based remote assistance is only available for end users connecting to ZPA using Zscaler Client Connector.
- Click **Add More** to add more domains or IP addresses for each application you want to define.
When two or more application segments cover the same destination address, Zscaler Client Connector attempts to match traffic to the more granular application segment. If there is no match in this application segment, Zscaler Client Connector bypasses ZPA and sends traffic directly. To learn more, see [About Application Access](/zpa/about-application-access).
[]If you enable **AppProtection**, then **Inspect AppProtection Application** is selected by default.
-
Select a web server certificate from the drop-down menu. You can click **Clear Selection** to remove any selections. To learn more, see [About (Web Server) Certificates.](/zpa/about-BrowserAccessCertificates)
The same certificate is used if **Browser Access** is also selected.
-
From the drop-down menu, select the protocol you want ZPA to use when a request is made to access the application (**Dynamic**, **HTTPS** or **HTTP**). The Dynamic protocol option allows the certificate to be [generated by the AppProtection Certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates). This option is handled by the back end that the application domain is mapped to. If you select this option, you can view the Protocol Discovery details on the [Protocol Discovery Dashboard page](/zpa/viewing-protocol-discovery-dashboard), along with the diagnostics for the related ports on the [Protocol Discovery Diagnostics page](/zpa/accessing-protocol-discovery-diagnostics). If you want to select **HTTP** or **HTTPS**, if your web server supports **HTTPS**, select this protocol. Otherwise, select **HTTP**. You can click **Clear Selection** to remove any selections.
To select both **Browser Access** and the **AppProtection**, **HTTP** or **HTTPS** needs to be selected.
-
If you selected **HTTP** in step ii, **Use Untrusted Certificates** is selected by default. Select **Use Untrusted Certificates** to allow inspection with private certificates. This option maintains the TLS connection between the inspection and the application. The verification of the private CA certificate would otherwise fail if this option wasn’t selected. If you do not select **Use Untrusted Certificates** and you are using private CA certificates that are not verified by ZPA, requests to access applications with inspection fail. If you enable **AppProtection**, then the **Use Untrusted Certificates** option is selected by default. This is because it needs to be selected to verify the CA certificate related to the AppProtection-enabled applications. If you deselect the **Use Untrusted Certificates** checkbox, the App Connector verifies the certificate of the server. Since it’s a self-signed certificate and not recognized by CA, it cannot be established and fails.
Selecting **Use Untrusted Certificates** results in successful application connectivity, regardless of verification of the certificate.
If **Browser Access** and **AppProtection** are selected, the **Use Untrusted Certificates** checkbox is automatically selected. To use the Browser Access feature, this option needs to remain selected.
[See image.](#Applications-InspectApplication)
[]
- **Default Port Ranges**: Enter the port ranges to set as the default for the application segment.
- **TCP Keepalive**: Enables the App Connector to periodically send TCP keepalives to an application server when a user has accessed that server on a TCP port. TCP keepalive is disabled by default. To learn more, see [Networking Deployed App Connectors](/zpa/networking-deployed-connectors#Tcpcommunication).
-
**TCP Port Ranges**: Enter the TCP port ranges that can be used to access the application.
For example, if you want to specify the port range 80 to 90, for **From...** enter `80`, and for **To...**, enter `90`. If you only want to specify one port, you can enter the same number (e.g., `80`) for **From...** and **To...**.
If you selected **Browser Access** for any application, the port range must include the port specified.
Click **Add More** to add more TCP port ranges.
-
**UDP Port Ranges**: Enter the UDP port ranges that can be used to access the application.
For example, if you want to specify the port range 90 to 94, for **From...**, enter `90`, and for **To...**, enter `94`. If you only want to specify one port, you can enter the same number (e.g., `90`) for **From...** and **To...**.
If you selected **Browser Access** for any application, you must use TCP port ranges.
Click **Add More** to add more UDP port ranges.
Zscaler recommends excluding DNS traffic (port 53) from TCP and UDP port ranges.
-
**Double Encryption**: Traffic between Zscaler Client Connector and the ZPA Public Service Edge is encrypted using TLS 1.2 by default. Enable double encryption if you want to enable a second layer of encryption for traffic between Zscaler Client Connector on your users' devices and the App Connector that provides them with access to your enterprise applications.
If you selected **Browser Access **or** Source IP Anchoring** for any application, you can’t enable **Double Encryption**.
To learn more, see [Understanding Double Encryption](/zpa/about-double-encryption).
-
**Bypass**: From the drop-down menu, choose when users can bypass ZPA to access an application. You can choose from the following options:
- **Use Client Forwarding Policy**: This option is selected by default. If selected, the decision to forward a user’s application request to ZPA is defined by the [client forwarding policy](/zpa/about-client-forwarding-policy). If none of the policy rules apply, then access to the application is implicitly set to **Forward to ZPA**. To learn more, see [Configuring Client Forwarding Policies](/zpa/configuring-client-forwarding-policies). This is also the case if you do not define any client forwarding policy rules at all within the ZPA Admin Portal.
- **Always**: If selected, users can always bypass ZPA when accessing an application.
- **On Corporate Network**: If selected, users can bypass ZPA when accessing an application from a trusted network. ZPA checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/zscaler-client-connector/configuring-forwarding-profiles-zscaler-client-connector).
You can click **Clear Selection** to remove any selections.
The **Bypass** setting within an application segment always takes precedence over any newly added client forwarding policy rule. To learn more, see [Configuring Bypass Settings](/zpa/configuring-bypass-settings). Also, if the same FQDN is defined in multiple application segments, and one of them has the **Bypass** setting set to **Always**, then that application segment takes precedence.
- **ICMP Access**: Enable for various ZPA clients (Zscaler Client Connector, Cloud and Branch Connectors, or Source IP Anchoring) to allow ICMP communication to the applications in this Application Segment. By default, this is set to **Disabled**. ZPA allows or blocks ICMP requests based on [access policies](/zpa/about-access-policy). If you configure an application for ICMP Access, there are some things to consider when using ICMP with ZPA:
- If ICMP is enabled for a specific application in an application segment and the same application is disabled for ICMP in a different application segment, then Zscaler Client Connector considers ICMP enabled for that application and forwards the ICMP request to ZPA.
- Zscaler Client Connector doesn't intercept ICMP requests for a destination IP that has the same subnet as the user's machine since this is considered an unreachable host.
- The [IP](/zpa/about-user-activity-diagnostics#connector) data appears and the Internal Status Code on the [User Activity Diagnostics page](/zpa/about-user-activity-diagnostics#time) shows as successful (e.g., BRK_MT_TERMINATED) after the App Connector is selected, even though it is unreachable. This can occur if the App Connector is set up to provide on access or no [health reporting](/zpa/about-health-reporting), as health reporting does not work well with ICMP.
- If an application is blocked based on an [access policy](/zpa/about-access-policy), Zscaler Client Connector creates a new Microtunnel request for every ICMP echo request.
- ICMP does not work with Double Encryption, so you might not want to enable Double Encryption for application segments where you enabled ICMP.
-
**Multimatch**: Enable to configure inclusive policies that allow an application request to match multiple application segments. To learn more, see [Using Application Segment Multimatch](/zpa/using-app-segment-multimatch).
Multimatch is not supported for applications that have Browser Access, Privileged Remote Access, AppProtection, or Source IP Anchoring enabled. If Multimatch is enabled, Health Reporting on an app segment can only be set to On Access or None.
-
**Bypass during Reauthentication**: Choose whether application access during reauthentication bypasses ZPA (**Enabled**) or not (**Disabled**). For example, if your IdP is configured to do multi-factor authentication (MFA) for off-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts the user for MFA. For on-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts them for MFA. This feature requires versions Zscaler Client Connector 4.3 or later for Windows and macOS.
If you select **Always** for the **Bypass** option, then **Bypass during Reauthentication** is automatically disabled and cannot be enabled.
[]
-
[]**Health Reporting**: Choose whether the App Connector reports the health status of all applications within an application segment continuously (**Continuous**), while a user is accessing it (**On Access**), or not at all (**None**). The default setting is **On Access**. You can see the status of the application on the [Health dashboard](/zpa/about-dashboard/health). To learn more, see [About Health Reporting](/zpa/about-health-check-and-reporting#about-health-reporting).
You can't choose **Continuous** health reporting for applications configured with more than 10 ports or if any of the applications in the application segment are defined with only a wildcard (e.g., *). Additionally, if an application has client hostname validation enabled to facilitate client-to-client remote assistance, then the application is not shown on the Health Dashboard. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
-
**App Connector Selection Method**: Choose **Closer to Application** if you prefer the App Connector closest to the application to be selected. By default, ZPA chooses the App Connector closest to the user (**Closer to User**). After you make a selection, ZPA selects an App Connector that has the shortest round-trip time towards the requested application.
This setting supports only TCP applications. The limit for the number of targets that check the health of the defined applications at the App Connector is 6,000. If this limit is exceeded, then the **Health Reporting** of the application is set to **None**, and a random selection of App Connectors is chosen.
If Health Reporting is set to **None**, the **App Connector Selection Method** feature cannot be enabled and an error message appears.
-
**Client Connector can receive CNAME**: Choose whether App Connectors resolve CNAME records. By default, this is enabled, and Zscaler Client Connector receives CNAME DNS records from the App Connector. Disabling means App Connectors do not send CNAME DNS records.
This setting is not applicable for Browser Access applications, and ZPA functions as if the option is disabled. If Zscaler Client Connector is on a macOS or an iOS device and the application needs to be accessed by CNAME, it is best to disable this setting.
[]You must identify the segment group to which this application segment is associated with. Placing the application segment in a segment group allows you to configure user [access policies ](/zpa/about-policies)based on that group.
On the **Segment Group **tab, choose one of the following options, and configure the group accordingly:
- [Select Segment Group](#seggroupoption)
- [Add Segment Group](#seggroupoptionb)
Click **Next**.
[]Choose an existing segment group from the drop-down menu. You can search for a specific group or click **Clear Selection** to remove any selections.
[See image.](#tab3a)
[]
Complete the following:
- **Name**: Enter a name for the segment group. The name cannot contain special characters, except for periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the segment group.
- **Status**: Make sure that the segment group is enabled.
[See image.](#tab3b)
[]
![Select Segment Group](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-segment-group_0.png)
[]
![Add Segment Group](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-add-segment-group_0.png)
[]You must identify the server groups in your enterprise data center that host the applications you've defined.
On the **Server Groups** tab, choose one of the following options to configure the server group accordingly, or select **Skip** if you want to enable client-to-client remote assistance. To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
When you configure server groups, only group servers that are capable of hosting the same applications.
- [Select Server Group](#servgroup)
- [Add Server Group](#tab4b)
If you select or add a server group with [Dynamic Server Discovery](/zpa/enabling-dynamic-server-discovery) enabled, the **Servers** step is no longer required because the server group automatically discovers the server.
Click **Next**.
[]Choose an existing server group from the drop-down menu. You can search for a specific group, click **Clear Selection** to remove any selections, or select **Skip**.
[See image.](#tab4a)
[]
![Select Server Group](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-select-server-group_0.png)
[]
Complete the following:
- **Name**: Enter a name for the segment group. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the segment group.
- **Status**: Make sure that the segment group is enabled.
- **Dynamic Server Discovery**: If enabled, ZPA automatically discovers the appropriate servers for applications as users request the applications. If disabled, you must manually add defined servers to the server group.
- **App Connector Groups**: Choose the App Connector groups with access to the enterprise data center containing the application servers, and click **Done**. You can search for a specific group, or click **Clear Selection** to remove any selections. App Connector groups must be associated with applications that the App Connectors can access (i.e., only assign App Connectors to applications that the App Connector is capable of reaching). ZPA selects the closest App Connector given the location of the user and the App Connector-to-application latency.
[See image.](#servgroupb)
[]
![Add Server Group](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-add-server-group_0.png)
[]You must add servers to the server group you just created.
On the **Servers** tab, choose one of the following options, and configure the server accordingly:
- [Select Server](#selserv)
- [Add Server](#Addserv)
Click **Next**.
[]Choose an existing server from the drop-down menu. You can search for a specific server, click **Clear Selection** to remove any selections, or select **Skip**.
[See image.](#selservop)
[]
Complete the following:
- **Name**: Enter a name for the server. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Description**: (Optional) Enter a description for the server.
- **Status**: Make sure that the server is enabled.
- **Domain or IP Address**: The FQDN or IP address of the server.
- **Server Groups without DSD**: Select server groups. Only server groups that have Dynamic Server Discovery (DSD) are displayed.
[See image.](#AddServimg)
[]
![Select Server](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-select-server.png)
[]
![Add Server](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-add-server.png)
[]On the **Review** tab, review your application segment configuration, then click **Save**.
[See image.](#tab6)
[]
![Review tab in Add Recommended Application Segment window within the Recommended Application Segment page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-Review_0.png)
[]On the **Policies** tab, you see a list of access policies that are applied to the applications defined within the application segment. If you need to add new or modify existing policies, click **Edit Policy**. To learn more, see [About Access Policy](/zpa/about-access-policy).
If you do not need to make any policy changes, click **Cancel**.
[See image.](#tab7)
[]![Policies tab in Add Recommended Application Segment window within the Recommended Application Segment page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-Policy-1_0.png)
[]
![Define Applications](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-recommended-application-segments/Configuring-AI-Powered-Define-Applications-1.png)
[]![Active Directory Inspection port range options in the Add Application Segment window](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Config%20port%20range.png)
[]![Add Application Segment window with Applications section and Privileged Remote Access checkbox selected](/downloads/zpa/documentation-knowledgebase/applications/application-segments/onboard/Config%20App%20Segment.png)
[]
![Add Application Segment window with Applications section and Inspect Application checkbox selected](/downloads/zpa/documentation-knowledgebase/applications/application-segments/configuring-application-segments/Inspect%20access%20type.png)