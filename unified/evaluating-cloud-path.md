# Evaluating the Cloud Path
Source: https://help.zscaler.com/zdx/evaluating-cloud-path
PDF: https://help.zscaler.com/pdf/com/en/1450291.pdf

The Cloud Path provides a path visualization of metrics between hop points of traffic. It can capture a direct traffic path, as in the case of Zscaler Client Connector to Egress to destination, or tunneling through a Zscaler Internet Access (ZIA) Public Service Edge (from Zscaler Client Connector to Egress to ZIA Public Service Edge to destination). The Cloud Path has the following views:
- A graph that shows latency or packet loss** **for a particular time period.
- A Hop View and Command Line View that detail the path from the user's device to the application or destination.
Monitoring Latency and Packet Loss
Select either **Latency **or **Packet Loss** in the drop-down menu to view the graph. Click a point in the graph to see the time period and either the latency in milliseconds or the packet loss percentage. In the Latency graph, metrics over the different legs display in the tooltip, and you can also select the metrics from the checkbox options below the graph. If an error is present, that is also displayed in the tooltip. Select a point to update the path tracked from the device to the application.
![View Latency over the legs in the Cloud Path](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-cloud-path-latency2.png)
Monitoring the Hop View and Command Line View
The Hop View and Command Line View each reflect the path from the user's device to the application.
Hop View
Hover over different sections of the path to see more information. You can also use the arrows on either side to expand this view. Depending on the part of the path you hover over, details such as device information, the service provider, latency details, packet loss, hop count, etc. are displayed.
[See image.](#ISPinCloudPath)
- [Maximum Latency](#cp-max-latency)
- [Tunnels](#cp-tunnels)
- [VPN Concentrator](#cp-vpn)
- [External Proxy](#cp-eproxy)
- [Cloud Path Icons](#cp-icons)
- [Device Location](#cp-device-location)
- [Public Service Edges](#cp-pse)
- [Cloud Path Protocols](#cp-protocols)
[]Differential latency is shown over the different legs of the Cloud Path, and the leg with the highest latency displays in orange. The latency shown on top of the ZIA Public Service Edge represents the network latency between the ZIA Public Service Edge and the first router in the Zscaler Data Center. This might indicate ZIA Public Service Edge congestion. Click the magnifying glass icon to expand the Hop View and to see the individual values. To learn more about Service Edges, see [ZIA Public Service Edges](/zia/about-public-service-edges), [ZPA Public Service Edges](/zpa/understanding-service-edges), and [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
[See image.](#image-cloudpathhops)
[]You can see the flow of traffic through the applicable tunnels as per the configured policies. For GRE tunnels, the Hop View displays underlay hops in the routing path to provide more accurate metrics for latency and packet loss. In cases where the ZIA Private Service Edge is on a private network (such as a VPN) with a private IP address, the Hop View provides a path from the client to the ZIA Private Service Edge. To learn more about tunnels in the Cloud Path, see [About Tunnel Information in the Cloud Path](/zdx/about-tunnel-information-cloud-path).
[See image.](#reverse-tr)
[]When Citrix is the network interface for TCP or UDP probes, ZDX displays the path to the VPN Concentrator. ZDX also supports the topology where traffic from the VPN Concentrator flows to the ZIA Public Service Edge via a GRE/IPSec tunnel.
[See image.](#vpn-concentrator)
[]When an External Proxy is detected in the path, the Cloud Path supports several proxy topologies within the Hop View. Two examples are represented here.
The following scenario shows a third-party proxy forwarding traffic to the destination:
![External proxy forwarding traffic in direct use case](/downloads/zdx/analytics/users/evaluating-cloud-path/eproxy-direct3.png)
The following scenario shows the External Proxy forwarding traffic to the ZIA Private Service Edge through a GRE tunnel:
![External proxy forwarding traffic to ZIA Private Service Edge](/downloads/zdx/analytics/users/evaluating-cloud-path/eproxy-gre-tunnel4.png)
[]If there are any errors, icons are displayed on the Cloud Path. Click the icon to display the error message. To learn more, see [Cloud Path Errors](/zdx/cloud-path-errors).
[See image.](#CPErrors)
Network interface types that are neither Wi-Fi nor Ethernet are indicated with one of the following icons above the client icon (![Client icon in hop view](/downloads/zdx/analytics/users/evaluating-user-details/client-icon.png)
) in the Hop View:
- Cellular (SIM card) (![Cellular network type icon in hop view](/downloads/zdx/analytics/users/evaluating-user-details/cellular2.png)
) network type
- Bluetooth (![Bluetooth network type icon in hop view](/downloads/zdx/analytics/users/evaluating-user-details/bluetooth2.png)
) network type
- USB (![USB network type icon in hop view](/downloads/zdx/analytics/users/evaluating-user-details/ic-usb2.png)
) network type
If the network type cannot be detected, the icon for an unknown network type (![Unknown network type icon in hop view](/downloads/zdx/analytics/users/evaluating-user-details/unknown-type3.png)
) is displayed.
[]Geolocation information and the Zscaler location are displayed for the device, and geolocation information is also displayed for the Zscaler node in both the Hop View and the Command Line View.
[See image.](#GeoInfo_inCloudPath)
A device location icon confirms that a device's location was determined by latitude and longitude coordinates. If no icon is displayed, the device was located by its IP address.
[See image.](#location-icon)
[]When accessing an internet application, you can see the path from Zscaler Client Connector to the application, and if there is a ZIA Public Service Edge or ZPA Public Service Edge in the path, that is also displayed. If a private application is accessed, you can view the path from Zscaler Client Connector to the ZPA Public Service Edge or ZPA Private Service Edge. In case you have configured a path for traffic through the ZIA Public Service Edge, both the ZIA Public Service Edge and the ZPA Public Service Edge or the ZPA Private Service Edge are seen in the Cloud Path. This is displayed in the Hop View and the Command Line View. To learn more about Service Edges, see [ZIA Public Service Edges](/zia/about-public-service-edges), [ZPA Public Service Edges](/zpa/understanding-service-edges), and [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
The following image shows both the ZIA Public Service Edge and ZPA Public Service Edge in the Hop view. The ZPA Public Service Edge sends packets to the App Connector in the path to the application. To learn more, see [About App Connectors](/zpa/about-connectors), [ZIA Public Service Edges](/zia/about-public-service-edges), and [ZPA Public Service Edges](/zpa/understanding-service-edges).
[See image.](#ZPAinClodpath)
Both views display a 4-digit number for the ZIA Public Service Edge or ZPA Public Service Edge. This internal hash value helps Zscaler Support quickly locate and troubleshoot any issues. To learn more, see [ZIA Public Service Edges](/zia/about-public-service-edges) and [ZPA Public Service Edges](/zpa/understanding-service-edges).
[See image.](#FourDigitID)
[]Both views display the protocol used over the different legs of the Cloud Path. If ICMP, TCP, or UDP was selected, it is displayed in the Cloud Path. If Adaptive mode was selected, the protocol used for the different legs of the Cloud Path is displayed.
Adaptive mode is not supported for internal applications through ZPA. Only ICMP, TCP, and UDP are supported.
[See image.](#CloudPath-Graph-Protocol-Dropdown)
For Adaptive probes, legs that are grouped according to tunnel type also show their corresponding protocol. The following image shows the grouping of Z-Tunnel 2.0 and ICMP protocol within the Hop View:
[See image.](#tunnel-protocol)
To learn how Adaptive mode works, see [Using Adaptive Mode](/zdx/using-adaptive-mode). To learn more about setting probes for the Cloud Path, see [Configuring a Probe](/zdx/configuring-probe).
Command Line View
Click the **Command Line View** tab to view further details about the Cloud Path, including the Hop Direction (probe direction, from the client to your egress IP ↓, from ZIA Public Service Edge or ZIA Private Service Edge, or ZPA Public Service Edge or ZPA Private Service Edge to your egress IP ↑, and from Service Edges to destination ↓), Region and Geolocation, Packet Loss (%) and Packets Failed, as well as Latency metrics. If there are any errors, they are indicated by an icon next to the IP address. Click the icon to display the error message. To learn more, see [Cloud Path Errors](/zdx/cloud-path-errors), [ZIA Public Service Edges](/zia/about-public-service-edges), [ZIA Private Service Edges](/zia/understanding-private-service-edge), [ZPA Public Service Edges](/zpa/understanding-service-edges), and [ZPA Private Service Edges](/zpa/about-zpa-private-service-edges).
[See image.](#Cloud-Path-Command-Line-View)
[]![View Maximum Zscaler Latency in the Cloud Path ](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx_MaxLatencyonZEN.png)
[]![Example of reverse traceroute for GRE tunnels](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-gre-reverse-tr_a_0.png)
![VPN Concentrator shown in Hop View](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-state-street-cp-pc4.png)
[]
[]![Cloud Path Errors on the User Page](/downloads/zdx/analytics/users/evaluating-cloud-path/ZDX_UpdatedCloudPathErrors1.png)
[]![Cloud Path Errors in Command Line View](/downloads/zdx/analytics/users/evaluating-cloud-path/Errors-on-Command-Line-view_0.png)
[]![Four-digit number for ZIA Public Service Edge](/downloads/zdx/analytics/users/evaluating-cloud-path/ZDX_ZEN_ID_CLV.png)
[]![Viewing Private Applications in the Cloud Path](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-hop-view-zpa-public.png)
[]![Device profile in Cloud Path](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-device-profile-tooltip-time-zone2.png)
[]![Geo Information in the Cloud Path](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx_GeoInfo.png)
[]![Example of device location icon in the Hop View](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-location-icon.png)
[]![Choose protocol to view in the graph using the drop-down menu](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-cp-graph-protocol-dropdown.png)
[]![Tunnel and protocol for Adaptive probes](/downloads/zdx/analytics/users/evaluating-cloud-path/zdx-protocol-leg.png)