# Analyzing Risk with MITRE ATT&CK for AppProtection
Source: https://help.zscaler.com/zpa/analyzing-risk-mitre-attck-appprotection
PDF: https://help.zscaler.com/pdf/com/en/1496246.pdf

MITRE ATT&CK is a cybersecurity framework funded by the US government that is used to detect, identify, and classify various tactics, techniques, and procedures (TTPs) used for cyber attacks by attackers. It helps you assess your organization's security posture and calculate the risk of a cyber attack.
The MITRE ATT&CK framework assumes the attacker's point of view to navigate through your organization's network. This helps in highlighting the attacker's journey from the point of access to a potential data exfiltration, among other harmful acts. The integration of the MITRE ATT&CK framework assists you in finding misconfigurations within your organization's network and provides in-depth knowledge of attackers' behavior. This framework is widely implemented and trusted across the industry, acts as a communal approach to threat reporting, and most importantly, helps you look at your organization's risk from a deeper and recognized perspective.
To learn more, refer to the [MITRE ATT&CK website](https://attack.mitre.org/).
Analyzing the MITRE Framework for AppProtection
The MITRE ATT&CK page in the ZPA Admin Portal (Insights > MITRE ATT&CK) shows the MITRE ATT&CK framework with all the TTPs that show any misconfiguration of policies, application segments, AppProtection profiles, and Browser Protection profiles in ZPA. The information displayed represents the misconfigurations that are refraining you from covering an attack technique that can be reconfigured to strengthen your security stance.
Each TTP tile shows the name of the technique and the technique ID. The TTP tiles highlighted in blue indicate that they are covered by Zscaler protection. The green, red, or orange color at the right side of these tiles indicates whether the protection is configured, misconfigured, or not configured at all.
Overview
The Legend section provides the following overview:
- The donut chart shows the number of configurations or policies in ZPA that are misconfigured and configured correctly for your organization.
- You can show or hide this section by using the arrow at the top right of this section.
[See image.](#legend)
Hover Over View
Hover over a technique tile to view whether the protections against these attack techniques are misconfigured, configured, or not configured correctly, as well as which ZPA features (AppProtection or Browser Protection) cover these attack techniques when enabled. To learn more about AppProtection and Browser Protection, see [About AppProtection Policy](/zpa/about-appprotection-policy) and [Browser Protection Policy](/zpa/about-browser-protection-policy).
[See image.](#hover-over-tile)
[]![Examples of MITRE ATT&CK technique tiles covered by AppProtection or Browser Fingerprinting for ZPA](/downloads/zpa/appprotection-private-application-traffic-formerly-inspection/analyzing-risk-mitre-attck/Covered%20by%20examples.png)
[]![The MITRE ATT&CK framework page in the ZPA Admin portal](/downloads/zpa/getting-started/admin-portal/accessing-and-navigating-zpa-admin-portal/Updated%20page.png)