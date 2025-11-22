# Zscaler Client Connector Performance Troubleshooting Runbook
Source: https://help.zscaler.com/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook
PDF: https://help.zscaler.com/pdf/com/en/1532324.pdf

The Zscaler Client Connector Performance Troubleshooting Runbook is a comprehensive guide designed to address and resolve reported slowness issues when using Zscaler Client Connector for traffic forwarding to the Zscaler cloud. As Zscaler Client Connector is a recommended forwarding method, maintaining its optimal performance is crucial for a seamless user experience. This runbook outlines essential steps for diagnosing performance bottlenecks, starting with client-side and intermediate network checks, before escalating to deeper Zscaler troubleshooting. Furthermore, it details various Zscaler Client Connector configuration modes and adjustments that can be leveraged to significantly improve Zscaler Internet Access (ZIA) performance in Zscaler Client Connector deployments.
Check UDP Throttling and MTU (Only Z-Tunnel 2.0)
The following troubleshooting information addresses the major types of symptoms commonly reported by users facing performance issues using Z-Tunnel 2.0:
- Slowness due to internet service provider (ISP) throttling UDP packets.
- Slowness due to maximum transmission unit (MTU) mismatch.
A My Traceroute (MTR) trace alone is not helpful in identifying these issues.
[ISP Throttling UDP Packets](#isp-throtting-udp-packets)
[]
Reports and data analysis reveal that certain ISPs deprioritize UDP-based traffic, meaning the ISPs deliberately apply policies to slow down UDP packets. DTLS is the primary transport protocol for Z-Tunnel 2.0, and DTLS uses UDP 443. Deprioritization can result in network traffic performance issues such as overall internet sluggishness.
Option 1: Switching Users to Z-Tunnel 2.0 or TLS
The following steps describe switching user to Z-Tunnel 2.0 / TLS:
- On Zscaler Client Connector Portal, go to **Administration **> **Client Connector Support **> **User Privacy** and enable the **Allow end user to override Z-Tunnel 2.0 or ZPA protocol settings** option.
[See image.](#zscaler-client-connector-portal)
- With Zscaler Client Connector turned on, browse to `http://127.0.0.1:9000/zconfig?q=@``<CustomerDomain>` (e.g., http://127.0.0.1:9000/zconfig?q=@zscaler.com) and select **TLS **as the **Protocol **in the drop-down menu:
[See image.](#zscaler-user-configuration)
- To enable these changes, click **Restart Service** in the **More **section of Zscaler Client Connector.
[See image.](#restart-service)
Option 2: Switching Users to Z-Tunnel 2.0 or TLS
You must create a new app profile and a new forwarding profile.
- In the new forwarding profile, select the **Primary Transport Selection** as **TLS**.
[See image.](#new-forwarding-profile)
- Map this new forwarding profile to the newly created app profile.
- Map the affected user to this new app profile.
- Users must click **Update Policy** in Zscaler Client Connector to be assigned to the new profile.
If the performance improves, it indicates that the ISP is throttling UDP packets. Contact the ISP and work towards resolution.
Until the ISP resolves the issue, you have two other options to work around it:
- Continue using TLS: Move users to an app profile that is configured with an app profile having Z-Tunnel 2.0 (TLS).
Z-Tunnel 2.0 with TLS can still intercept all ports and protocols, just like Z-Tunnel 2.0 with DTLS.
- Consider using a Zscaler Client Connector Hybrid configuration: Zscaler Client Connector 3.8 introduced a feature that you can use to tailor a new app profile for specific users affected by slow performance issues. The feature turns on **Redirect Web Traffic to Zscaler Client Connector Listening Proxy** and turns off **Use Z-Tunnel 2.0 for Proxied Web Traffic** in the **Advanced Z-Tunnel Configuration** menu while configuring the forwarding profile.
[See image.](#advanced-tunnel-configuration)
The results are as follows:
- Web traffic using Z-Tunnel 1.0.
- Non-web traffic using Z-Tunnel 2.0.
- Not using the forwarding profile Proxy Auto-Configuration (PAC) file.
[Issues With Path MTU](#issues-path-mtu)
[]
MTU Discovery is only applicable for DTLS mode. In the case of TLS mode, TCP negotiates the Maximum Segment Size (MSS) for the outer connection automatically.
Skip this section if you have enabled the Path MTU Discovery option for DTLS mode in the forwarding profile.
The MTU is used for identifying the maximum size of any data packet. The MSS is used for specifying the maximum size of packets that can be sent over a network. The MSS measures the non-header portion of a packet, which is called the payload.
- DTLS: In the case of DTLS Tunnel 2.0 mode, the default MTU value is 1400. Consequently, the MSS value is MTU - 40 = 1360.
- TLS: In the case of TLS, TCP negotiates the MSS for the outer connection automatically. Zscaler Client Connector is not involved in making it work.
Option 1: How to Check and Modify MTU Size
The following steps describe checking and modifying MTU size:
- On the Zscaler Client Connector Portal, go to **Administration **> **Client Connector Support** > **User Privacy** and enable **Allow end user to override Z-Tunnel 2.0 or ZPA protocol settings**.
- With the Zscaler Client Connector turned on, direct the user to browse to `http://127.0.0.1:9000/zconfig?q=@``<CustomerDomain>` (e.g., http://127.0.0.1:9000/zconfig?q=@zscaler.com) and select one of the available values under **MTU** as shown in the following image:
[See image.](#zscaler-user-configuration-2)
- To enable these changes, click **Restart Service **in the **More **section of Zscaler Client Connector.
[See image.](#restart-service-2)
Option 2: How to Check and Modify MTU Size
You must create a new app profile and a new forwarding profile.
- In the new forwarding profile, under the** MTU for Zscaler Adapter**, configure an MTU size less than 1400 (preferably in increments of 50).
- Map this new forwarding profile with the newly created app profile.
[See image.](#configure-MTU-size)
- Map the affected user to this new forwarding profile.
- Users must then click **Update Policy **in Zscaler Client Connector to get assigned to the new profile.
If the performance improves, this means that one of the hops in the path has less MTU size, thereby fragmenting the packets originating from Zscaler Client Connector and leading to performance degradation. You can either report this problem to the ISP and get this issue rectified or continue using this value which is determined to be optimal.
Alternatively, you can enable the Path MTU Discovery option in the forwarding profile, which enables Zscaler Client Connector to automatically determine the path MTU.
If there is no improvement in performance, switch to Z-Tunnel 1.0 to perform some tests and data gathering.
The workaround is *not *recommended as a permanent solution. Modifying the MTU size is only for testing purposes. Switching to Z-Tunnel 1.0 means Zscaler Client Connector is incapable of intercepting non-web traffic.
How to Switch to Z-Tunnel 1.0
Complete the following steps to temporarily switch to Z-Tunnel 1.0:
- In the new forwarding profile, under **Forwarding Profile Action for ZIA**, select the **Z-Tunnel 1.0** option.
- Map this new forwarding profile with the newly created app profile.
[See image.](#forwarding-action-profile)
- Map the affected user to this new forwarding profile.
- Click **Update Policy** on Zscaler Client Connector to be assigned to the new profile.
Analyzing and Isolating the Pattern
This section covers the most common patterns to help decide the next troubleshooting direction.
[Slowness Observed With a Particular OS Type](#slowness-particular-os)
[]
Slowness might be observed with a particular OS type, at office or at home, or when connected to any Zscaler data center.
Review the following events to understand the pattern. Understand when the issue started and try to note all the changes that happened during that time.
[](/zscaler-client-connector/zscaler-client-connector-processes-allowlist)
| Events | Steps to Try |
| ------ | ------------ |
| Did an OS upgrade occur? | Check the behavior on a device with the previous OS or revert the OS on one of the impacted machines. |
| Did a third-party security or VPN app get newly installed or updated? | Disable the services of the app and monitor the performance. |
| Have the processes required for Zscaler Client Connector to function been allowlisted? | Revisit this allowlist to validate it. |
| High CPU utilization with Zscaler Client Connector enabled. | High CPU usage on the host machine could lead to performance issues. |
[Performance Issues Observed by All Users of an Organization](#slowness-all-day)
[]
There are instances wherein all users of an organization can face slowness, regardless of where they are working from. A few reasons for such behavior could be:
-
-
- [](/contact-support)
-
-
- [](/contact-support)
| Events | Next Steps |
| ------ | ---------- |
| Slow performance after a recent Zscaler Client Connector version upgrade. | Revert to the previously known working version on a few workstations and monitor performance.If performance improvement is seen on all the workstations where Zscaler Client Connector was reverted, the Zscaler Client Connector version could be the issue.Collect the Zscaler Client Connector logs from a few workstations with old and new versions and escalate to Zscaler Support. |
| Slowness performance after a recent security patch or new software push. | Revert the security patch or software push on a few workstations.If performance improvement is seen on all the workstations where the security patch or software push was reverted, and is most likely caused by the recent change.Collect the Zscaler Client Connector logs from a few workstations with old and new versions and escalate to Zscaler Support. |
[Performance Issues Observed During a Particular Time of the Day or Day of the Week](#slowness-time-day)
[]
Although rare, this issue might have been reported previously. An intermittent issue could be caused by the following events:
- Scheduled big data upload or download, which restricts the firewall or internet bandwidth.
- Scheduled antivirus scans on the workstation, which restricts the CPU or memory utilization of the workstation.
[Performance Issues Observed at a Particular Office Location](#slow-office-location)
[]
There are instances where users at a particular office location are facing performance issues. When the users connect from a non-office location or connect to their mobile hotspot from the office, the performance is normal.
Here are some potential issues and next steps:
[](#scope-3-zia)[](#scope-3-zia)
| Events | Next Steps |
| ------ | ---------- |
| Ongoing issue or maintenance at the Zscaler data center. | Go to section Zscaler Public Data Center to continue with the troubleshooting. |
| Path congestion between office location and the Zscaler data center. | Go to section Zscaler Public Data Center to continue with the troubleshooting. |
| Issues with office networking components such as router, switch, or firewall. | Check the general health parameters (e.g., CPU, memory, throttling policies, etc.), and check any network monitoring tools. |
Further Steps
Compile all the relevant collected data and open a support case with [Zscaler Support](/contact-support).
[]![Forwarding Profile Action](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Forwarding-Action-Profile.png)
[]![Configure MTU Size](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/configure-an-MTU-size.png)
[]![Restart Service 2](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Restart-Service-2.png)
[]![Zscaler User Configuration 2](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Zscaler-User-Configuration-2.png)
[]![Advanced Tunnel Configuration](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Advanced-Z-Tunnel-2.0-Configuration.png)
[]![New Forwarding Profile](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/New-Forwarding-Profile.png)
[]![Restart Service](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Restart-Service.png)
[]![Zscaler User Configuration](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Zscaler-User-Configuration.png)
[]![Zscaler Client Connector](/downloads/troubleshooting-runbooks/zscaler-client-connector-performance-troubleshooting-runbook/Zscaler-Client-Connector-Admin-Portal.png)