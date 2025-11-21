# Understanding the Ransomware Kill Switch
Source: https://help.zscaler.com/zero-trust-branch/understanding-ransomware-kill-switch
PDF: https://help.zscaler.com/pdf/com/en/1532701.pdf

The Zscaler Ransomware Kill Switch is a one-click attack surface-reduction tool integrated into Zero Trust Branch. It empowers organizations to rapidly contain ransomware threats without disrupting critical business operations.
Core Capabilities
With the Ransomware Kill Switch, you can:
- Contain threats with a single click using one of four preset severity tiers designed like [DEFCON levels](https://en.wikipedia.org/wiki/DEFCON). This allows progressive lockdowns, from blocking vulnerable protocols such as Remote Desktop Protocol (RDP) and Server Message Block (SMB), to isolating entire Operational Technology (OT) segments like hospital floors or factory lines.
- Enact a tiered, policy-based response to block high-risk access (e.g., RDP/Command and Control items), all nonessential communication, and access to critical crown jewel applications.
- Maintain business uptime by enacting targeted containment to keep essential operations running and avoid total shutdowns.
- Have integrated visibility and control to provide complete east-west network traffic visibility for all endpoints, enabling real-time, granular policy enforcement.
- Fully control your configuration via APIs to allow seamless integration with security information and event management (SIEM); security orchestration, automation, and response (SOAR); endpoint detection and response (EDR); and extended detection and response (XDR) systems to enable automated incident response.
Use Cases
Here are some typical use cases for the Ransomware Kill Switch:
- **Incident response**: The Ransomware Kill Switch provides incident response with user-selectable security levels to lock down vulnerable protocols, stop lateral movement, and restrict access to critical assets, ensuring business continuity during cyber threats.
- **Enhanced visibility and control**: Constantly changing network devices make securing communications difficult. The Ransomware Kill Switch provides full visibility into all endpoint transactions, overcoming the limitations of monitoring lateral traffic across access switches. This enables real-time security policy enforcement and improved protection.
- **Critical infrastructure protection**: Integrates with SIEM, SOAR, and EDR/XDR via APIs, enabling automated incident response. It quarantines compromised endpoints, limiting infection spread, which enhances security while protecting existing IT investments.
Example of the Ransomware Kill Switch in Action
When creating a site-level firewall policy for device segmentation, you must assign one or more Ransomware Kill Switch threat level color codes. To learn more about assigning a threat level, see [Configuring the Ransomware Kill Switch for a Site](/zero-trust-branch/configuring-ransomware-kill-switch-site). During an incident, only the firewall policies associated with the selected threat level color code are evaluated in a top-down sequence. The evaluation stops at the first matching policy, ensuring fast and precise containment.
In this example, Pod 80 has two hosts, `pod-80-lnx-a` and `pod-80-lnx-b`, connected to the LAN side of Zero Trust Branch, while the Zero Trust Branch WAN port is connected to the DHCP server. Each host is microsegmented to subnet `32`, as shown in the following image.
[See image.](#rks-topo)
In this example, Pod 80 (designated as `site-80` in the Zero Trust Branch Admin Portal) has the following policy rules:
- Rule 1, `block-ssh`, blocks Secure Shell (SSH) traffic when the threat level is orange.
- Rule 2, `all-protocol-allow`, allows all ports when the threat level is either green or yellow.
[See image.](#policies-list)
Initially, the Ransomware Kill Switch is set to green.
[See image.](#rks-green)
With this setting, `pod-80-lnx-b` can ping and SSH into `pod-80-lnx-a` successfully.
`admin80@pod-80-Inx-b:~$ping 10.*xx*.*xx*.4
PING 10.98.80.4 (10.*xx.*xx.4) 56(84) bytes of data.
64 bytes from 10.*xx.xx*.4: icmp_seq=1 ttl=63 time=0.463 ms
64 bytes from 10.*xx.xx*.4: icmp_seq=2 ttl=63 time=0.373 ms
^C
--- 10.xx.xx.4 ping statistics •--
2 packets transmitted, 2 received, 0% packet loss, time 1036ms
rtt min/avg/max/mdev = 0.373/8.418/0.463/.045 ms
admin80@pod-80-lnx-b:~$
admin80@pod-80-2nx-b: ~$ssh admin@10.*xx.xx*.4
The authenticity of host '10.*xx.xx*.4 (10.*xx.xx*.4)' can't be established.
ED25519 key fingerprint is SHA256:HsYaMx...vs0YtJLtyso.
This key is not known by any other names
`
Now, let’s change `site-80`'s threat level to orange to simulate a high-risk network scenario.
[See image.](#rks-orange)
In this case, Rule 1, which blocks SSH traffic when the threat level is orange (and was previously skipped), is now enforced. In the following example, the ping is successful, but SSH access is blocked and does not return a response.
`admin80@pod-80-Inx-b:~$ ping 10.xx.xx.4
PING 10.90.80.4 (10.xx.xx.4) 56(84) bytes of data.
64 bytes from 10.xx.xx.4: icmp_seq=1 ttl=63 time=0.486 ms
64 bytes from 10.xx.xx.4: icmp_seq=2 ttl=63 time=0.456 ms
^C
--- 10.xx.xx.4 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1036ms
rtt min/avg/max/mdev = 0.456/0.471/0.486/0.015 ms
admin80@pod-80-1nx-b:~$
admin80@pod-80-1nx-b:~$ssh admin@10.xx.xx.4
admin80@pod-80-1nx-b:~$`
The Hit Count column on the Policies tab indicates the number of times the policy was accessed.
[See image.](#hit-count)
This example highlights how the Ransomware Kill Switch enables dynamic, color-coded policy enforcement for rapid incident response. By simply adjusting the threat level, you can instantly contain high-risk traffic, block malicious activity, and isolate compromised workloads.
[]![Schematic diagram showing a Zero Trust Branch installation.](/downloads/zero-trust-branch/analytics-monitoring/understanding-ransomware-kill-switch/topo-rks.png)
[]![Ransomware Kill Switch set to green](/downloads/zero-trust-branch/analytics-monitoring/understanding-ransomware-kill-switch/rks_green.png)
[]![Site Policies tab on the Policies page showing how policies with different threat levels can enhance site security.](/downloads/zero-trust-branch/analytics-monitoring/understanding-ransomware-kill-switch/policies-list.png)
[]![Ransomware Kill Switch set to orange](/downloads/zero-trust-branch/analytics-monitoring/understanding-ransomware-kill-switch/rks-orange.png)
[]![Site Policies tab on the Policies page highlighting the Hit Count column.](/downloads/zero-trust-branch/analytics-monitoring/understanding-ransomware-kill-switch/policies-hit-count.png)