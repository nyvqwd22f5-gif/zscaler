# Configuring a Probe
Source: https://help.zscaler.com/zdx/configuring-probe
PDF: https://help.zscaler.com/pdf/com/en/1350846.pdf

To configure a probe for an application:
-
Go to one of the following:
- **Configuration** > **Applications**, under the **Predefined Applications** or **Custom Applications** sections, expand an application** **row within the table and click **Add Probe**.
- **Configuration** > **Probes**, and click **Add Probe**.
The **Add Probe** window appears.
[See image.](#Add_New_Probe)
A Web probe and Cloud Path probe are automatically enabled by default when you onboard a predefined application. The **Add Probe** link is disabled if you've reached the maximum number of allowed applications or probes for your subscription level. To learn more about application and probe limits, see [Ranges & Limitations](/zdx/ranges-limitations).
- In the **Add Probe** window:
- [a. Configure Probe](#ConfigureProbe)
- [b. Additional Parameters](#Additional_Parameters)
- [c. Review](#Review)
- Click **Save** and [activate the changes](/zdx/saving-and-activating-changes-admin-portal).
- []On the **Configure Probe** tab, for **General**:
- **Name**: Enter a name for your probe. The maximum length is 64 characters. Accepted characters are alphanumerics and a limited range of symbols, such as underscore (_), hyphen (-), space ( ), forward slash (/), period (.), pipe symbol (|), and parentheses ().
- **Status**: Select **Enable** or **Disable** to indicate the status of your probe.
- **Application**: If you accessed the **Add Probe** window from the **Configuration **> **Applications **page, then this field is automatically populated with the correct application and is view-only. If you accessed this window from the **Configuration** > **Probes **page, then you must select an application from the drop-down menu.
-
**Probe Type**: Select **Web** or **Cloud Path**. If you select Cloud Path, the **Follow Web Probe** field appears. Select a probe to follow from the drop-down menu. Selecting a Web probe for the Cloud Path probe to follow is recommended, but not required. Following a Web probe alters configuration choices for protocol ports in later steps.
If you've selected a Network application, the Cloud Path probe type is selected by default. Network applications do not require Web probes.
- **Run Frequency (minutes)**: Enter the number of minutes for how frequently your probe should run. The default probe frequency varies based on your subscription plan. To learn more, see [Ranges & Limitations](/zdx/ranges-limitations).
- **Probe Class**: Defines the application type as either Predefined or Custom.
-
For **Probing Criteria**: Select the criteria that you want to probe for the application. To learn more, see [Understanding Probing Criteria Logic](/zdx/understanding-probing-criteria-logic).
You can configure the probe to monitor multiple user groups, users in particular locations or departments, or a combination of these. For example, you might want to run a probe for the sales group using a sales business application (e.g., Salesforce.com). Running a probe for the sales group helps to limit the number of probes associated with the application and avoid unnecessary traffic from non-sales users.
Similarly, you can configure a probe to only run on multiple devices logged in by one user, or configure it to run on only specific devices.
By default, all user groups, users, Zscaler locations, location groups, departments, and devices in Zscaler Internet Access (ZIA) are applied. However, the maximum number of each selection for user groups, users, Zscaler locations, location groups, departments, or devices cannot exceed 100. If your organization has a ZIA account, each field defaults to your organization's information, such as the following examples:
- **User Groups**: Data Engineering
- **Users**: (Your organization's users)
- **Locations**: Zscaler HQ
- **Location Groups**: Server Traffic Group
- **Departments**: Dev Ops
- **Devices**: Desktop
When configuring Web probes for internal applications through Zscaler Private Access (ZPA), probe only for users, user groups, and departments that use the application.
-
For **Exclusion Criteria**: Select the criteria that you do not want to monitor for the application. To learn more, see [Understanding Probing Criteria Logic](/zdx/understanding-probing-criteria-logic).
You can configure monitors to run on all devices in a particular location by specifying the location in Monitoring Criteria, then exclude specific users or devices. For instance, you might want to run a probe for a productivity web application for all engineering group users but exclude the New York location, as that location does not use productivity web applications.
By default, no user groups, users, Zscaler locations, location groups, departments, or devices are excluded. The maximum number of each selection for user groups, users, Zscaler locations, location groups, departments, or devices cannot exceed 100. The following are examples of excluded criteria:
- **User Groups**: Mobile Development
- **Users**: DEFAULT ADMIN
- **Locations**: Zscaler Lab
- **Location Groups**: HQ IT Group
- **Departments**: Marketing
- **Devices**: AUROUS
When configuring Web probes for internal applications through ZPA, probe only for users, user groups, and departments that use the application.
- Click **Next**.
[]
- On the **Additional Parameters** tab, if you selected **Web **as your** Probe Type** on the previous tab, then the following parameters appear under **Web Probe Configuration**:
- **Probe Name**: This is the name you entered on the previous tab.
- **Application Name**: This is the name of the application** **that was either preselected for you or that you selected manually on the previous tab.
- **Request Type**: **GET** is the only request type applicable to **Web **monitoring. POST is not supported. This field is view-only.
- **Destination URL**: Enter the web destination, either an HTTP or HTTPS URL. This is the web address the probe requests. This is editable if the URL requires a tenant name.
- **Request Header**: Enter the **Name** and **Value** for the request header. If you need to enter more than one name and value pair, click **Add More**. This specifies the HTTP request header to pass as part of the probe. For example, you can specify authorization of the header to pass a security token. These fields are disabled for predefined applications.
-
**HTTP Response Status Codes**: You can probe for specific [HTTP Status Codes](https://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml). You can add HTTP codes that are not in the default list by entering any number between the range of 100–599. By default, the following 1xx (Informational), 2xx (Success), and 3xx (Redirection) codes are applied:
- 100 Continue
- 101 Switching Protocol
- 102 Processing
- 103 Early Hints
- 200 OK
- 201 Created
- 202 Accepted
- 203 Non-Authoritative Information
- 204 No Content
- 205 Reset Content
- 206 Partial Content
- 207 Multi-Status
- 208 Already Reported
- 226 IM Used
- 300 Multiple Choices
- 301 Moved Permanently
- 302 Found
- 303 See Other
- 304 Not Modified
- 307 Temporary Redirect
- 308 Permanent Redirect
You can remove any of these codes by clicking the **Close **icon. However, you cannot change the default codes for a predefined app.
- **Number of Attempts**: The number of attempts before considering the monitor request failed. The default is 1 attempt, but can be increased. You cannot change the default number of attempts for a predefined application.
- **Timeout (seconds)**: The default is 60 seconds and cannot be changed for a predefined application.
- **Follow Redirect**: **Enable** or **Disable** this feature. To ensure accurate performance measurements to the following predefined applications, this setting is disabled by default and you cannot enable it:
- Box
- Microsoft Teams Web App
- OneDrive for Business
- Outlook Online
- ServiceNow
- SharePoint Online
- **Maximum Redirects**: This specifies the number of times the probe attempts to follow the HTTP redirect before it is considered failed. The default is 5 redirects. You cannot change the number of redirects for a predefined application. If **Follow Redirect** is disabled, **Maximum Redirects** is also disabled.
- If you selected **Cloud Path** as your **Probe Type** on the previous tab, the following parameters appear under **Cloud Path Probe Configuration**:
- **Probe Name**: The name you entered on the previous tab.
- **Application Name**: The name of the application** **that was either preselected for you or that you selected manually on the previous tab.
- **Protocol**: Select a protocol from the drop-down menu. Options include **Adaptive**, **ICMP**, **TCP**, and **UDP**.
If you choose Adaptive Mode, the best protocol for each leg in the cloud is selected via an auto-discovery process. If you choose any of the other protocols, they are used for the path of the Cloud Path probe. To learn more, see [Using Adaptive Mode](/zdx/using-adaptive-mode).
- **TCP Port**: If you choose **Adaptive **or **TCP **as the protocol, this field is automatically displayed and populated with the standard TCP Port for HTTPS traffic, 443, though this can be edited. If you have chosen to follow a Web probe and then choose **TCP **as the protocol, you cannot edit the port value.
- **UDP Port**: If you choose **Adaptive **or **UDP **as the protocol, this field is automatically displayed and populated with the RFC-defined port for the destination server, 33434, though this can be edited.
-
**Packet Count**: The number of probe packets sent per hop discovery that have the same TTL value. The default is `5` packets, the maximum is `20` packets, and the minimum is `3` packets.
For ZPA, the recommended packet count is `3` packets, and the maximum is `6` packets.
- **Interval (ms)**: The time interval between probe packets with the same TTL. Probe packets of incremental TTL are paced evenly within this time interval. The number of iterations or cycles is defined by the configured Packet Count. The default is `1000`, the minimum is `1000`, and the maximum is `10000`.
- **Timeout (ms)**: The time to wait for a response to a probe packet before considering loss. The default is `1000`, the minimum is `500`, and the maximum is `5000`. The recommended setting for ZPA is `500`.
- **Cloud Path Host**: The host IP address or fully qualified domain name for the host (i.e., the IPv4 IP address; IPv6 is not supported). Zscaler partially provides the domain name if the application selected is predefined. This is editable if a tenant name is required.
-
**Force Reverse Cloud Path in Trusted Network**: The option to force a reverse traceroute in the trusted environment when a network device blocks the forward Cloud Path. Enable only if you cannot implement a different device configuration. Ideally, you should reconfigure the firewall or the device blocking the forward traceroute. If that isn't possible, this setting provides calculations for reverse latency from the Zscaler Internet Access (ZIA) Public Service Edge to the Egress in the Cloud Path.
During a reverse Cloud Path, the Egress IP address is derived from the location API, and therefore, can differ from the IP address used within the forward Cloud Path. In this scenario, the Egress is noted as a Reverse Egress, along with the IP address derived from the location API.
-
If the Interval is configured as `6000` ms, the packets for a run are spaced over 6000 ms. For a maximum of 30 hops, packets are paced at every 200 ms: the first packet with TTL 1 is sent at 0 ms, the packet with TTL 2 at 200 ms, the packet with TTL 3 at 400 ms, and so on.
If the Timeout is configured as `2000` ms, the first probe would time out at 2000 ms, the second at 2200 ms, the third at 2400 ms, and so on.
The Packet Count determines the number of these iterations or cycles. While the default packet count is 5, a higher packet count provides a more accurate measurement of packet loss.
Cloud Path probes are sent every 15 minutes by default for Standard ZDX subscriptions, and every 5 minutes for Advanced ZDX subscriptions.
[See image.](#ProbeConfigExample)
- Click **Next**.
[]On the **Review** tab, review your probe configuration, then click **Submit**.
[See image.](#Add-New-Monitor-Review-Page)
[]![Review probe configuration](/downloads/zdx/configuration/probes/configuring-probe/ZDX-Add-Probe-Cloud-Review.png)
[]![Example of Cloud Path probe configuration fields](/downloads/zdx/configuration/probes/configuring-probe/ZDX-Add-Probe-Cloud-AdditionalParameters.png)
[]![Add New Probe](/downloads/zdx/configuration/probes/configuring-probe/ZDX-Add-Probe-Configure-Probe.png)