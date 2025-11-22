# Viewing the Protocol Discovery Dashboard
Source: https://help.zscaler.com/zpa/viewing-protocol-discovery-dashboard
PDF: https://help.zscaler.com/pdf/com/en/1486011.pdf

The Protocol Discovery dashboard displays protocols (KRB, LDAP, SMB, HTTP, and TLS) detected for domains with application segments that have AppProtection disabled. [You can enable AppProtection for the application segment](/zpa/configuring-application-segments#ADProtection) when you click on the application segment, the listed domains, and the ports and protocols mapped to it. The Protocol Discovery dashboard displays up to 100 of a domain's most recent transactions and 6,000 application segments for the time range selected.
![The Autodetect dashboard page within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/viewing-protocol-discovery-dashboard/Updated%20Autodetect%20dashboard%20page.png)
Dashboard Tools
The AppProtection dashboard displays the following information and functionality:
- **Time Range Filter**: View Protocol Discovery data over a period between 1 hour to 7 days, or you can select Custom Range. If you use a Custom Range, the start date must be within the last 7 days. The end date automatically sets to the system's current time. By default, the dashboard displays information for events that occurred in the last hour.
- **Refresh Icon**: Refresh the dashboard to reflect the most current information.
- **AppProtection Dashboard**: View the [AppProtection page](/zpa/about-appprotection-dashboard) for information about AppProtection policy activity in your organization.
- **Browser Protection Dashboard**: View the [Browser Protection](/zpa/about-browser-protection-dashboard) page for information about browser sessions in your organization.
![About the Protocol Doscpvery Dashboard tools](/downloads/zpa/dashboard-diagnostics/viewing-protocol-discovery-dashboard/Tools.png)
Protocol Discovery Widget
You can select the application segment that you want displayed from the drop-down menu. You can enter a keyword to search by domain within the displayed application segment.
![Selecting an application segment for the Protocol Discovery widget ](/downloads/zpa/documentation-knowledgebase/dashboard-diagnostics/viewing-protocol-discovery-dashboard/selecting%20app%20segments%20for%20table.png)
Enabling AppProtection for an Application Segment
If you haven't [enabled AppProtection ](/zpa/configuring-application-segments#ADProtection)for the displayed application segment and want to inspect it, follow these steps:
- Click on the displayed application segment or any of its related items (domain, port, or protocol).
- When you click one of the displayed items, the **Enable AppProtection** window appears. If the application segment doesn't include domains that have AppProtection enabled, and an AppProtection profile and policy don't already exist, you can adjust the AppProtection Profile Type and select the **Auto create an AppProtection policy** checkbox.
[See image.](#enable)
- When you are finished, click **Save**. A confirmation message appears notifying you that you have successfully updated the application segment.
Make sure you also [generate the AppProtection enrollment (CA) certificate](/zpa/generating-zscaler-issued-enrollment-ca-certificates) to use the AppProtection feature. If you haven't already generated the certificate, then another pop-up window appears to generate the certificate.
You can view the adjusted application segments on the[ Defined Application Segments page](/zpa/about-applications).
Inspect Application Segments
To inspect at the application segment level:
- Click on the displayed application segment.
- After you have clicked on the application segment, a pop-up message appears to confirm if you want to enable inspection for the application segment.
- If you want to continue with inspection of the entire application segment, click **Yes**. The application segment is then inspected. A confirmation message appears notifying you that you have successfully updated the application segment.
- If you don't want to inspect all of the application segment, click **Cancel**. You can go to the Defined Application page and [edit the application segment](/zpa/editing-application-segments) to adjust the domain and related ports.
[See image.](#appseg)
Inspect Domains and Ports
To inspect at the domain or port level:
- Click one of the displayed domains or ports.
- After you have clicked a domain or port, a pop-up message appears to confirm if you want to enable inspection for all of the UDP and TCP ports assigned to the application segment associated with the selected domain.
- If you want to continue with inspection of all the ports, click** Yes**. The domain and its related ports for the related application segment are then inspected. A confirmation message appears notifying you that you have successfully updated the application segment.
- If you don't want to inspect all of the current ports for the application segment that the domain is associated with, click **Cancel**. You can go to the Defined Application page and [edit the application segment](/zpa/editing-application-segments) to adjust the domain and related ports. Protocol Discovery allows AppProtection to be enabled for a domain with a single port or for all of the TCP/UDP ports configured with the application segment. If you have successfully enabled inspection for only one domain, when you refresh the page, if you click the same domain but with a different port than the one that you inspected, you are prompted to enable inspection on all the ports for that domain.
[See image.](#domain)
Inspect Protocols
To inspect at the protocol level:
- Click one of the listed protocols.
- When you have clicked a protocol, a pop-up message appears to confirm if you want to enable inspection for that specific protocol of the application segment displayed. If you want to continue, click **Yes**. A confirmation message appears notifying you that you have successfully updated the application segment.
[See image.](#protocol)
- After inspection has been enabled, the items that have been selected for inspection are removed from the widget.
[]![The Enable AppProtection window on the Autodetect Dashboard page ](/downloads/zpa/dashboard-diagnostics/about-browser-protection-dashboard/Enable%20AppProtection%20window.png)
[]![Info window to inspect all the domains in the application segment selected](/downloads/zpa/dashboard-diagnostics/viewing-protocol-discovery-dashboard/AppSegment%20Pop%20Up%20Window_0.png)
[]![Info window to inspect the domain selected](/downloads/zpa/dashboard-diagnostics/viewing-protocol-discovery-dashboard/Domain%20Pop%20Up%20Window.png)
[]![Info window to inspect all the domains in the protocol selected](/downloads/zpa/dashboard-diagnostics/viewing-protocol-discovery-dashboard/Protocol%20Popup%20window.png)