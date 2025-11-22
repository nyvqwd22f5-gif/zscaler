# Configuring SIEM Integration
Source: https://help.zscaler.com/zero-trust-branch/configuring-siem-integration
PDF: https://help.zscaler.com/pdf/com/en/1532893.pdf

You can use security information and event management (SIEM) integration to forward Zero Trust Branch events to your organization's SIEM platform for centralized security analytics. The integration supports real-time event streaming over syslog to platforms such as Splunk or other compatible SIEM engines. Within the Zero Trust Branch architecture, branch gateways securely stream events directly to the configured SIEM engine. Depending on your organization's requirements, you can deploy the SIEM engine either on premises or in the cloud.
Zero Trust Branch uses a generic syslog format for SIEM integration. The Zero Trust Branch appliance sends syslog messages directly to the configured syslog server. Currently, Zero Trust Branch generates only one type of traffic log: the session-init logs. These session-init logs capture Layer 2, Layer 3, and Layer 4 header information when a new session is created. They also provide metadata about session initiation events and are exported to the SIEM server using the standard syslog format.
You can also view these traffic logs in the Zero Trust Branch Admin Portal under Packet Logs (Monitoring & Logs > Packet Logs) or Flow Logs (Monitoring & Logs > Flow Logs). To learn more, see [Monitoring & Logs](/zero-trust-branch/monitoring-and-logs).
SIEM integration is supported over both WAN and Zscaler Private Access (ZPA).
Only the session logs are forwarded to the SIEM server.
Prerequisites
Before configuring SIEM integration in the Zero Trust Branch Admin Portal, do the following:
-
Obtain the SIEM server details, such as SIEM host (IP address), SIEM protocol, and SIEM port number.
Zero Trust Branch supports TCP and UDP protocols only.
- Ensure that there is connectivity between the SIEM server and Zero Trust Branch's WAN interface.
Configuring SIEM Integration
To set up integration with a SIEM server:
- In the Zero Trust Branch Admin Portal, go to **Settings **> **Integrations**.
-
Locate the **SIEM Integration **tile and click **Settings**.
[See image.](#setting-siem-tile)
-
In the** SIEM Integration** drawer:
- **SIEM Host**: Enter the IP address of the SIEM server.
- **SIEM Protocol**: From the drop-down menu, select the SIEM protocol (**TCP **or **UDP**) you want to use.
- **SIEM Port Number**: Enter the port number that the SIEM server uses.
[See image.](#siem-integration-drawer)
- Click **Save**.
- (Optional) If the SIEM server is hosted on a cloud platform, ensure that you have configured the necessary [firewall policies](/zero-trust-branch/understanding-firewall-policies) to allow access to the port.
Verifying SIEM Integration
To verify whether SIEM integration works as expected:
-
In the Zero Trust Branch Admin Portal, go to **Deployments **> **Sites **(or **Hubs**) > **Console**.
[See image.](#console-view)
-
Run the following command:
`cat /etc/airgap/policy_container/rsyslog.d/20-siem.conf`
-
Check your syslog server for the message sent from the gateway.
All session logs are sent to the syslog server.
[]![Integrations page showing the option to integrate a SIEM server](/downloads/zero-trust-branch/administration/third-party-integrations/configuring-siem-integration/ztb-click-setting-siem.png)
[]![Configuring SIEM integration](/downloads/zero-trust-branch/administration/third-party-integrations/configuring-siem-integration/ztb-seim-integration-drawer.png)
![Image]()
[]![Sites page showing the option to launch Console](/downloads/zero-trust-branch/administration/third-party-integrations/configuring-siem-integration/zscaler-cellular-console-option.png)