# Merging AI-Powered Recommendations
Source: https://help.zscaler.com/unified/merging-ai-powered-recommendations
PDF: https://help.zscaler.com/pdf/com/en/1492111.pdf

AI-powered recommendations for application segments can become defined application segments. You can [add an AI-powered recommendation](/unified/configuring-ai-powered-recommendations-settings%20), which moves it to the [Defined Application Segment](/unified/about-applications) page as a new defined application segment. You can also merge an AI-powered recommendation with an existing defined application segment. This option allows you to combine application segments that have the same grouping reasons.
To merge an AI-powered recommendation with an existing defined application segment:
- Go to **Policies** > **Access Control** > **Private Applications** > **App Segments** > **AI-Powered Recommendations**.
- In the table, locate the AI-powered recommendation you want to merge with a defined application segment, and click the **Merge** icon.
- In the **Merge Defined Application Segment with Recommended Application Segment** window:
- [Step 1: Defined Application Segment](#definedappsegment)
- [Step 2: AI-Powered Recommendation](#ai-powered)
- [Step 3: Application and Ports Configuration](#appports)
- [Step 4: General Information](#general)
After you have merged the defined application segment with an AI-powered recommendation, the merged application segments are shown in the **Defined Application Segment** table.
[]On the** Defined Application Segment** tab, select the defined application segment you want to merge:
- View a list of all application groups that were configured for your organization. Click **Next** or **Previous** at the bottom of the table to view additional application groups. Filter the information that appears in the table. By default, no filters are applied. For each application group, you can see:
- **Name**: The name of the defined application segment.
- **Applications**: A list of up to three defined applications within the application segment.
- **Status**: Indicates that the application segment is enabled or disabled.
- **Health Reporting**: Indicates whether [health reporting](/unified/understanding-health-reporting) for the application is **Continuous**, **On Access**, or **None**.
- Click **Next**.
[See image.](#img_definedappsegment)
[]
![Defined Application Segment tab in the Merge Defined Application Segment window within the Recommended Application Segment page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/merging-recommended-application-segments/merge-defined-app-segment.png)
[]On the **AI-Powered Recommendation** tab:
- Check the following application details for the AI-powered recommendation:
- **Name**:** **The name of the application segment for the application.
- **Attack Surface Reduction**: The percentage reduction in the attack surface (i.e., percentage difference between potential users and recommended users).
- **Current Configuration**: The number of Applications, Defined Application Segments, and Current Users.
- **Recommended Configuration**: The number of Applications, Recommended Users, and Observed Users for the AI-Powered recommendation.
-
**Recommended Users**: If [SCIM Sync](/unified/enabling-scim-identity-management) is enabled, the number of suggested users for this recommended application segment is displayed. Click the number of users to list the recommended users. You can search by email.
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
[See image.](#img_aipowered)
[]
![Merge Defined Application Segment with Recommended Application Segment window.](/downloads/zpa/documentation-knowledgebase/applications/application-segments/merging-recommended-application-segments/ZPA-Merge-Recommendations.png)
[]On the **Applications and Ports Configuration** tab:
- All application information (e.g., TCP and UDP port ranges) associated with the merging of your selected application segment and AI-powered recommendation are prepopulated.
- Check if the application information is correct and configure as needed.
- Click **Next**.
[See image.](#img_apps-ports)
[]
![Application and Ports Configuration tab in Merge Recommended Application Segment window within the Recommended Application Segment page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/merging-recommended-application-segments/merge-apps-ports.png)
[]On the **General Information** tab, the following are pre-populated for the merged application segment:
- Under **General Information**, check the following:
- **Name**: Enter a name for the application segment. The name cannot contain special characters, with the exception of periods (.), hyphens (-), and underscores ( _ ).
- **Status**: Enable the application segment. If **Disabled**, the defined applications within the application segment are inaccessible to users.
-
**Disaster Recovery**: Enable to designate the application segment for disaster recovery. Application segments that are designated for disaster recovery ensure business continuity in the event of a disaster scenario. Disaster recovery is disabled by default. To learn more, see [Understanding Disaster Recovery](/unified/understanding-disaster-recovery) and [About Disaster Recovery Application Segments](/unified/about-disaster-recovery-application-segments).
Disaster Recovery Mode is triggered when you upload the DNS TXT records to the DNS server for the disaster recovery domain name. To learn more, see [Creating DNS TXT Records](/unified/creating-dns-txt-records).
-
**Source IP Anchor**: (Optional) Enable Source IP Anchoring.
This setting is tied to Source IP Anchoring for ZIA. When enabled, you can connect to it in ZIA. You can't delete the application while in use by a ZIA entity. There are ranges and limitations for Source IP Anchoring. To learn more, see [Understanding Source IP Anchoring](/unified/understanding-source-ip-anchoring) and [Ranges & Limitations](/unified/ranges-limitations).
- **Description**: (Optional) Enter a description.
- Under **Common Configuration**, check the following:
- **Default Port Ranges**: Enter the port ranges to set as the default for the application segment.
- **TCP Keepalive**: Enables the App Connector to periodically send TCP keepalives to an application server when a user has accessed that server on a TCP port. TCP keepalive is disabled by default. To learn more, see [Networking Deployed App Connectors](/unified/networking-deployed-app-connectors).
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
To learn more, see [Understanding Double Encryption](/unified/understanding-double-encryption).
-
**Bypass**: From the drop-down menu, choose when users can bypass ZPA to access an application. You can choose from the following options:
- **Use Client Forwarding Policy**: This option is selected by default. If selected, the decision to forward a user’s application request to ZPA is defined by the [client forwarding policy](/unified/about-client-forwarding-policy). If none of the policy rules apply, then access to the application is implicitly set to **Forward to ZPA**. To learn more, see [Configuring Client Forwarding Policies](/unified/configuring-client-forwarding-policies). This is also the case if you do not define any client forwarding policy rules at all within the Admin Portal
- **Always**: If selected, users can always bypass ZPA when accessing an application.
- **On Corporate Network**: If selected, users can bypass ZPA when accessing an application from a trusted network. ZPA checks if the user is on a trusted network defined in the [Zscaler Client Connector forwarding profile](/unified/configuring-forwarding-profiles-zscaler-client-connector).
You can click **Clear Selection** to remove any selections.
The **Bypass** setting within an application segment always takes precedence over any newly added client forwarding policy rule. To learn more, see [Configuring Bypass Settings](/unified/configuring-bypass-settings). Also, if the same FQDN is defined in multiple application segments, and one of them has the **Bypass** setting to **Always**, then that application segment takes precedence.
- **ICMP Access**: Enable for various Private Applications (ZPA) clients (Zscaler Client Connector, Cloud and Branch Connectors, or Source IP Anchoring) to allow ICMP communication to the applications in this Application Segment. By default, this is set to **Disabled**. ZPA allows or blocks ICMP requests based on [access policies](/unified/about-access-policy). If you configure an application for ICMP Access, there are some things to consider when using ICMP with ZPA:
- If ICMP is enabled for a specific application in an application segment and the same application is disabled for ICMP in a different application segment, then Zscaler Client Connector considers ICMP enabled for that application and forwards the ICMP request to ZPA.
- Zscaler Client Connector doesn't intercept ICMP requests for a destination IP that has the same subnet as the user's machine since this is considered an unreachable host.
- The [IP](/unified/accessing-user-activity-diagnostics#connector) data appears and the Internal Status Code on the [User Activity Diagnostics page](/unified/accessing-user-activity-diagnostics) shows as successful (e.g., BRK_MT_TERMINATED) after the App Connector is selected, even though it is unreachable. This can occur if the App Connector is set up to provide on access or no [health reporting](/unified/understanding-health-reporting), as health reporting does not work well with ICMP.
- If an application is blocked based on an [access policy](/unified/about-access-policy), Zscaler Client Connector creates a new Microtunnel request for every ICMP echo request.
- ICMP does not work with Double Encryption, so you might not want to enable Double Encryption for application segments where you enabled ICMP.
-
**Multimatch**: Enable to configure inclusive policies that allow an application request to match multiple application segments. To learn more, see [Using Application Segment Multimatch](/unified/using-application-segment-multimatch).
Multimatch is not supported for applications that have Browser Access, Privileged Remote Access, AppProtection, or Source IP Anchoring enabled. If Multimatch is enabled, Health Reporting on an app segment can only be set to On Access or None.
-
**Bypass during Reauthentication**: Choose whether application access during reauthentication bypasses ZPA (**Enabled**) or not (**Disabled**). For example, if your IdP is configured to do multi-factor authentication (MFA) for off-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts the user for MFA. For on-premises users, enabling this option redirects the user to the IdP via the internet where the IdP prompts them for MFA. This feature requires versions Zscaler Client Connector 4.3 or later for Windows and macOS.
If you select **Always** for the **Bypass** option, then **Bypass during Reauthentication** is automatically disabled and cannot be enabled.
- Click **Save**.
[See image.](#img_general)
AI-Powered recommendations do not support Extranet.
[]
![General Information tab in Merge Recommended Application Segment window within the Recommended Application Segment page](/downloads/zpa/documentation-knowledgebase/applications/application-segments/merging-recommended-application-segments/merge-general-1.png)