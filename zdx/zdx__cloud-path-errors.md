# Cloud Path Errors
Source: https://help.zscaler.com/zdx/cloud-path-errors
PDF: https://help.zscaler.com/pdf/com/en/1358806.pdf

If there are any errors in the Cloud Path in the Users dashboard, users see error icons in the Hop View as well as the Command Line View. In the Hop View, the icons are displayed under the hop, while in the Command Line View, icons are displayed next to the IP address. Clicking the icon displays the error message.
[See image.](#CloudPathErrors)
The icons in the Cloud Path indicate the following:
- ![Information Icon ](/downloads/zdx/analytics/cloud-path-errors/ZDX_Infoicon.png)
: This message is for informational purposes only. No action is required.
- ![Warning Error Message in ZDX ](/downloads/zdx/analytics/web-probe-error-messages/ZDX_WarningIcon.png?1607463684)
: This is a warning message. This indicates that action might be necessary to resolve an issue and achieve accurate Cloud Path results.
- ![Critical Error in ZDX ](/downloads/zdx/analytics/web-probe-error-messages/ZDX_CriticalIcon.png)
: This is a critical error. This indicates an issue that could affect the user experience.
|  |
| --- |
[][][][][][][][][][][][][][][][][][][][]
| Error Message | Error Description | Solution |
| ------------- | ----------------- | -------- |
| Zscaler Client Connector error. Contact Zscaler Support. | There is an internal error incurred by the Zscaler Client Connector. | Report the error to Zscaler Support. |
| Network communication failure. Either network interface is down or traffic is blocked. | There is a network error. One of the interfaces is down, the probes are not receiving a response, or the ISP upstream connectivity might be down. | Verify your ISP connectivity and that the ICMP/UDP protocol configured for the probe is not blocked on the network. |
| The domain is invalid or not resolvable. Verify your domain. | The domain is invalid or not resolvable. | Verify the name of the domain or your DNS configuration. |
| Proxy connection failed. | There were issues when connecting to your web proxy. | Verify your proxy policy and authentication mechanism and that access is allowed for this application URL. |
| Invalid HTTP URL. Check the Web probe configuration. | Connection to the host is successful, but there are issues in connecting to your URL. | Verify that your URL for the Web probe is correct. |
| The probe result was discarded due to a device network change. | The network changed during the Cloud Path probe run. Cloud Path probes for that sample were aborted. | Zscaler Client Connector detected the network change. No action is required. |
| The network path to the client egress cannot be traced. Configuring a GRE/IPSec tunnel bypass rule for the client egress router is recommended. | The network path to the client egress IP address cannot be traced correctly because the egress IP is tunneled. This also means that the end-to-end latency value does not include the latency from the client to the Internet egress point. | Configure an access list for your router or SD-WAN device to bypass ICMP/UDP from the tunnel (GRE/IPSec) for your client egress IP address. |
| The network path to the client egress cannot be traced. Zscaler Client Connector was unable to fetch ZDX service data from Zscaler cloud. | The network path from the client to the Internet egress point (client egress) cannot be traced. Zscaler Client Connector was unable to fetch ZDX service data from the Zscaler cloud. This also means that the end-to-end latency value does not include the latency from the client to the internet egress point. | Report the error to Zscaler Support. |
| Client egress detection was not possible with the configured protocol type in the Cloud Path. Try a different protocol type. | The Zscaler Client Connector could not discover the user's Internet egress IP address. | Verify the configuration and try a different protocol (ICMP/UDP). The current Cloud Path protocol is blocked. |
| Hop information from ZPA Public Service Edge to the application is not collected by ZDX. | We are not able to display the actual Cloud Path for applications accessed through Zscaler Private Access (ZPA). | No action required. |
| The Zscaler Public Service Edge is not reachable from Zscaler Client Connector. | The TCP traceroute to the Zscaler Service Edge was dropped. | Check your network connection. |
| Probe not allowed in NDR. | ICMP and UDP probes are not supported in a No Default Route (NDR) environment. | Ensure you're running probes via TCP. |
| Traceroute packets are not reaching the Zscaler Service Edge. | ICMP, TCP, or UDP protocol traceroute might not be supported on the network. | Ensure the underlying network permits the configured protocol. |
| Data from external proxy to destination is not discoverable. | Path is not available. | No action required. |
| Data from external proxy to egress is not discoverable. | Path is not available. | No action required. |
| Cloud Path packets are not reaching the external proxy. | ICMP protocol might not be supported on the network. | Ensure the underlying network allows ICMP packets. |
| Data from external proxy to data center egress is not discoverable. | Path is not available. | No action required. |
| Data from data center egress to destination is not discoverable when external proxy is present. | Path is not available. | No action required. |
| Data from egress to destination is not discoverable when external proxy is present. | Path is not available. | No action required. |
| The client egress router did not respond to Cloud Path probes coming from the ZIA Public Service Edge. | The egress could not be probed. It did not respond with an ICMP TTL expired message for the ZDX Cloud Path probe. | Configure the router to return ICMP TTL expired messages for packets with IP TTL1. |
[]ZPA and ZDX Error Codes
ZDX can report error codes for the following Zscaler Private Access (ZPA) errors. These errors are applicable to either the ZPA Public Service Edge or ZPA Private Service Edge component.
[][][][][][]
-
-
-
-
-
[][](/zpa/editing-server-groups)[][][]
-
-
[]
| Session Status | Description | Resolution |
| -------------- | ----------- | ---------- |
| ZPA internal error. | The probe might have encountered a ZPA internal error. | Report the error to Zscaler Support. |
| ZPA application is not reachable. | The probe might have failed to reach the ZPA destination. | Report the error to Zscaler Support. |
| Error in finding customer. | The ZPA Public Service Edge or ZPA Private Service Edge cannot retrieve customer information due to a configuration error when processing the data connection request. | Ask the user to reauthenticate. If the error persists, contact Zscaler Support. |
| User session expired. | The ZPA Public Service Edge or ZPA Private Service Edge cannot set up a data connection because reauthentication is required. | Ask the user to reauthenticate. If the error persists, contact Zscaler Support. |
| Error in filling assistant groups. | The ZPA Public Service Edge or ZPA Private Service Edge cannot fill assistant groups due to a configuration error when processing the data request. | Ask the user to validate configuration. If the error persists, contact Zscaler Support. |
| Policy or attributes misconfigured for access. | A valid policy cannot be matched to an application access request. There is a missing or mismatched configuration in policy settings, SAML/SCIM attributes, Posture Profiles, Trusted Networks, Client Types, Cloud Connector Groups, or Machine Groups. The application request is also blocked when an App Segment or App Group Segment is disabled. | Update the policy to allow the user.Ensure all SAML attributes are present in the SAML assertion and restart the Zscaler Client Connector.Ensure all SCIM attributes or SCIM groups are present.Modify policies to match the user's client type.Enable the App Segment or Segment Group. |
| App Connector group not configured. | The ZPA Public Service Edge was unable to process the application request since an App Connector group was not specified in the Server group configuration. | Edit the Server group to add the App Connector group(s). To learn more, see Editing Server Groups. |
| Application policy blocked access. | The ZPA service blocked the application request because the user isn't allowed to access the requested application. | Update the policy to allow the user access. |
| Timeout policy blocked access. | The ZPA service blocked the application request because the timeout policy requires the user to authenticate. | The user must reauthenticate in Zscaler Client Connector. |
| Application not configured. | The ZPA Public Service Edge or the ZPA Private Service Edge cannot set up a connection since the application is not configured. | Ensure that the Application and Application Segment are configured in the ZPA Admin Portal.Ask the user to access the application again. If the error persists, contact Zscaler Support. |
| Connection request timed out. | The ZPA Public Service Edge or ZPA Private Service Edge was waiting for a data connection request from an App Connector that could provide access to the application, but the request timed out while waiting. The request from an App Connector is triggered in response to the initial application request from Zscaler Client Connector. | Ensure that the App Connectors can reach the ZPA Public Service Edge or ZPA Private Service Edge and the requested application. |
[![Cloud Path Errors on the User Page ](/downloads/zdx/analytics/cloud-path-errors/ZDX_UpdatedCloudPathErrors1.png)
]
![Cloud Path Errors on Command Line View](/downloads/zdx/analytics/cloud-path-errors/Errors%20on%20Command%20Line%20view_0.png?1617589486)