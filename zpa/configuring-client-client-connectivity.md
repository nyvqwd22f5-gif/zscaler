# Configuring Client-to-Client Connectivity
Source: https://help.zscaler.com/zpa/configuring-client-client-connectivity
PDF: https://help.zscaler.com/pdf/com/en/1485196.pdf

[Client-to-client connectivity](/zpa/understanding-client-client-connectivity) allows an admin to connect to an end user's Windows, Mac, or Linux device to troubleshoot or provide remote assistance. To use this feature in Zscaler Private Access (ZPA), complete the following steps.
To enable client-to-client connectivity:
- Zscaler recommends that the destination Windows devices you are using for this feature are Active Directory (AD) domain-joined. However, client-to-client connectivity can work if you have Windows or Linux-based hybrid-joined or Azure cloud-joined devices. In this case, it is your organization's responsibility to ensure completeness and uniqueness of the destination device's FQDNs (e.g., on a Windows machine, make sure that the DNS primary suffix field is entered and valid).
Mac devices must be domain-joined. End users' Mac machines must be running Zscaler Client Connector versions 3.7 or later.
- Ensure the destination Windows device is running Zscaler Client Connector 3.9.0.169 or later. Zscaler Client Connector on the destination machine must have a machine tunnel deployed, or the destination machine must be logged in to ZPA in the Zscaler Client Connector. This ensures the connection to ZPA for the destination machine without the original local user of the destination that is logging into Windows. To learn more, see [Configuring Update Settings for Zscaler Client Connector](/client-connector/configuring-update-settings-zscaler-client-connector).
- On the endpoints, set Zscaler Client Connector to collect machine hostname information. To learn more, see [Configuring Zscaler Client Connector to Collect Hostnames](/z-app/configuring-zscaler-app-collect-hostnames).
- Include a regular expression in Client Hostname Validation that matches for the hostname of the Windows device you are remotely accessing. For example, enter the regular expression “desktop-[a-zA-Z0-9]{5}-AC\.example\.com” to enable a client-to-client connection to devices joined with fully qualified domain names (FQDNs) matching this regular expression (e.g., “desktop-10B38-AC.example.com”). To learn more, see [Validating a Client Hostname](/zpa/validating-client-hostname).
If you have the same namespace for both your applications and workstations, Zscaler recommends creating different application segments for client-based remote assistance and for application access, with separate FQDNs or wildcard subdomains if possible. To successfully enable remote assistance, the client-based remote assistance application segment must match the regular expression defined in step 5.
[See image.](#regex)
- When creating or editing application segments for client-to-client connectivity, the configured Windows hostnames (either FQDNs or wildcard domains) in the application segment must match the regular expression used to validate a client hostname. For example, the FQDN "desktop-10B38-AC.example.com” in the application segment matches the regular expression “desktop-[a-zA-Z0-9]{5}-AC\.example\.com”). If you use a wildcard domain such as “*.example.com” in the application segment and a more specific regular expression in the hostname validation, only devices with hostnames matching both the wildcard domain and the hostname validation regular expression are enabled for remote assistance. To learn more, see [Configuring Application Segments](/zpa/configuring-application-segments) or [Editing Application Segments](/zpa/editing-application-segments).
[See image.](#editappseg)
It is not necessary to select a server group because it is not required to have an App Connector assigned for client-to-client connectivity.
[See image.](#ServGrp)
- Create or update an existing access policy to control who can connect to existing remote users. Use additional criteria in your access policy if you want stricter access control. To learn more, see [Configuring Access Policies](/zpa/configuring-access-policies) or [Editing Access Policies](/zpa/editing-access-policies).
If access policies haven't been created or updated for client-to-client connectivity, then any user in their organization can use this feature to connect to any endpoints enrolled in this feature within their organization.
[See image.](#accesspolicy)
- The local endpoint (host-based firewall) must allow access from the localhost using the interface IP address (e.g., 192.168.1.100) from the ports or protocols that you expect to be available via the client-to-client access.
- Verify that the hostname is correct for the Zscaler Client Connector user you will be remotely accessing.
[See image.](#ZCC)
For Microsoft Remote Assistance (MSRA), the following changes must be made in the invitation file by either the destination user or the source user:
- Remove the LHTICKET attribute.
- Replace the IP address for the RCTICKET value with the registered hostname in ZPA. The following example is an RCTICKET value with the registered hostname:
<UPLOADINFO TYPE=“Escalated”><UPLOADDATA USERNAME=“Zscaler”
RCTICKET=“65538”, 1, desktop@safemarch.com:54606;100.64.0.2:54607,*,wmLNc8PLK1/q4ypjbU9+4PLWONEe6TKayN0ISF79EXdW+41xqXATVZDwGAQJcbrf…
To enable RDP Shadowing on the end user's machine locally or via Group Policy Editor (GPO):
- Go to the Remote Desktop Settings (Settings > System Settings > Remote Desktop).
- Select **Enable Remote Desktop**. The account must have local administrator permissions.
[See image.](#enableRdp)
- Enter `GPO` in the search bar and click **Edit group policy**.
- In the Local Group Policy Editor, go to the **Connections **folder (Computer Configuration > Administrative Templates > Windows Components > Remote Desktop Services > Remote Desktop Session Host > Connections).
- Double-click **Set rules for remote control of Remote Desktop Services user sessions**.
[See image.](#setRules)
The **Set rules for remote control of Remote Desktop Services user sessions** window appears.
- Click **Enabled**.
- Under **Options**, select the desired remote control of the Remote Desktop Services user sessions.
If **Full Control with user's permission** is selected, the target user receives the following notification to allow the source user to view their session.
[See image.](#rdpRequest)
- Click **Apply**, and then click **OK**.
[See image.](#selectRdpOptions)
- In the search bar, enter `Windows Defender Firewall` and select **Windows Defender Firewall with Advanced Security**.
- On the **Windows Defender Firewall with Advanced Security** page, go to **Inbound Rules** and enable the following Windows Defender Firewall rules to allow the incoming Remote Shadow Connection:
- Right-click **File and Printer Sharing (SMB-In)** and select **Enable Rule**.
- Right-click **Remote Desktop - Shadow (TCP-In)** and select **Enable Rule**.
- Determine the target user's session ID by executing the `query session` command via Command Prompt or Powershell.
- Using the session ID from step 6 and the hostname or IP address of the target user, execute the following command via Command Prompt or Powershell to remotely connect to the target user’s session:
mstsc /shadow:<Session ID> /v:<Hostname or IP>
You should now be able to connect to the remote endpoint via RDP, MSRA, or psexec. After making the connection, if the client-to-client connection is enabled successfully, the log data in the User Activity Log shows the Access Type as **Client to Client**. To learn more, see [About User Activity Diagnostics](/zpa/about-user-activity-diagnostics#filters).
[See image.](#useractlog)
[]![Editing the regular expression for client-based remote assistance](/downloads/zpa/administration/configuring-client-based-remote-assistance/Updatedregex.png)
[]![Editing an application segment for client-based remote assistance](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/edit%20app%20seg.png)
[]![Server Group tab in the Add Application Segment window](/downloads/zpa/administration/configuring-client-based-remote-assistance/servergroupnote.png)
[]![Adding an access policy for client-based remote assistance](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/access%20policy.png)
[]![Zscaler Client Connector window ](/downloads/zpa/administration/configuring-client-based-remote-assistance/ConfigC2CZCC.png)
[]![Access Type Client to Client highlighted in the expanded view of log data in User Activity Logs](/downloads/zpa/dashboard-diagnostics/about-applications-dashboard/Diagnosticsview.png)
[]![Enabling Remote Desktop in Windows](/downloads/zpa/administration/configuring-client-based-remote-assistance/setting-rules-for-remote-control-of-remote-desktop-services.png)
[]![Setting the rules for Remote Desktop Services in the GPO](/downloads/zpa/administration/configuring-client-based-remote-assistance/set-rules-in-gpo.png)
[]![Remote Control Request prompt](/downloads/zpa/administration/configuring-client-based-remote-assistance/remote-control-request.png)
[]![Setting the rules for the Remote Desktop Services user sessions](/downloads/zpa/administration/configuring-client-based-remote-assistance/set-rules-for-remote-control-of-remote-desktop-services-options.png)