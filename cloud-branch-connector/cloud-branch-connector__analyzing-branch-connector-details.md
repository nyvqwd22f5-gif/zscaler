# Analyzing Branch Connector Details
Source: https://help.zscaler.com/cloud-branch-connector/analyzing-branch-connector-details
PDF: https://help.zscaler.com/pdf/com/en/1447011.pdf

The Branch Connector Details page provides general, management, and forwarding information for a selected Branch Connector. You can access the Branch Connector Details page by clicking the **View** icon (![View Icon in the Cloud & Branch Connector Monitoring Table](/downloads/cloud-connector/analytics-monitoring/about-cloud-connector-details/View%20icon%20C%26B%20Connector.jpg)
) in the [Cloud & Branch Connector Monitoring](/cloud-branch-connector/accessing-cloud-branch-connector-monitoring) table for a selected Branch Connector.
Analyzing the Branch Connector Details Page
The Branch Connector details page varies based on whether you select a hypervisor host or a hardware device. If you select a hardware device, the page varies depending on whether the device is deployed in gateway mode. Non-gateway mode refers to hypervisor hosts and hardware devices not deployed in one-arm mode. Depending on what you select, you can view the following:
- [Gateway Mode](#GatewayMode)
- [Non-Gateway Mode (One-Arm)](#NonGatewayMode)
[]
Configure gateway mode details in your Branch Connector Configuration Template. You cannot configure them on the Branch Connector Details page. To learn more, see [Configuring a Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- [General](#BCDetailsGeneral)
- [ZIA Tunnel](#BCDetailsZIATunnel)
- [ZPA Tunnel](#BCDetailsZPATunnel)
- [System](#BCDetailsSystem)
- [WAN](#WAN)
- [LAN](#LAN)
- [Routing](#BCDetailsRouting)
[]
In the General Information section:
- [Deployment Details](#deployment-details)
- [Operational Status](#health-status)
- [Gateway Details](#gateway-details)
The Hardware Device section only applies to deployed hardware devices. In the Hardware Device section:
- [Device Details](#hardware-devicedetails)
- [Specifications](#hardware-devicespecifications)
In the Forwarding Information section:
- [DNS Details](#dns-details2)
- [Ingress Details](#ingress-details)
- [Egress Details](#egress-details)
In the Management Information section:
- [Management Details](#management-details)
- [DNS Details](#dns-details)
[]
The hypervisor host deployment details are as follows:
- **Deployment Type**: The Branch Service Provider (i.e., Branch Cloud) used to deploy the selected Branch account.
- **Group**: The name of the group to which the Branch Connector virtual machine (VM) is assigned.
- **Location**: The location of the Branch Connector Group.
- **Geo Location**: The physical location of the Branch Connector when deployed.
- **VM Size**: The size of the VM, which is set to **Small **by default. Small and Medium VM sizes are supported.
- **Version**: The version of the Branch Connector.
[See image.](#hypervisorhost-deploymentdetails)
The hardware device deployment details are as follows:
- **Device Model**: The model of the hardware device.
- **Serial Number**: The serial number associated with the hardware device.
- **Group**: The group associated with the hardware device.
- **Location**: The location associated with the hardware device.
- **Geo Location**: The physical location associated with the hardware device.
- **Version**: The version of the hardware device.
[See image.](#hardwaredevice-deploymentdetails)
[]
The hypervisor host operational status details are as follows:
- **Status**: The Health Status table shows the deployed Branch Connector as Active or Inactive.
- **HA Status**: The high availability status of the deployed Branch Connector.
[See image.](#hypervisorhost-operationalstatus)
The hardware device **Operational Status** displays the health status of the hardware device as Active or Inactive.
[See image.](#hardwaredevice-operationalstatus)
[]
- **Management Default Gateway**: The IP address of the default gateway.
- **ZIA Gateway**: The IP address of the ZIA proxy gateway.
- **ZPA Broker**: The IP address of the default ZPA (Public or Private Service Edge).
- **Internal Gateway IP Address**: The IP address of the internal gateway.
[See image.](#gatewaydetails)
[]
- **Device Serial Number**: The serial number associated with the hardware device.
- **Device Name**: The name of the hardware device.
- **Device Type**: The type of hardware device.
- **Model Number**: The model number of the hardware device.
[See image.](#devicedetails)
[]
- **CPU**: The CPU of the hardware device.
- **Proxy Ports**: The number of proxy ports the hardware device has.
- **MEMORY**: The amount of memory the hardware device has.
[See image.](#specifications)
[]
- **DNS Server 1**: The IP address of the primary DNS Server.
- **DNS Server 2**: The IP address of the secondary DNS Server.
[See image.](#forwarding-dnsdetails)
[]The Ingress Details table shows the load balancer IP address. This option is currently not supported.
[See image.](#forwarding-ingressdetails)
[]
- **Service IP Address 1**: The primary service IP address.
- **NAT IP Address**: The NAT IP address.
- **Outgoing Gateway IP Address**: The outgoing gateway IP address.
[See image.](#forwarding-egressdetails)
[]
- **Management IP Address**: The IP address of the management gateway.
- **NAT IP Address**: The NAT IP address.
- **Default Gateway IP Address**: The IP address of the default gateway.
[See image.](#management-managementdetails)
[]
- **DNS Server 1**: The IP address of the primary DNS Server.
- **DNS Server 2**: The IP address of the secondary DNS Server.
[See image.](#management-dnsdetails)
[]
- **Operational Status**: The health status of the hardware device, either **Active** or **Inactive**.
- **Device Model**: The model of the hardware device.
- **Configuration Template Name**: The name of the Branch Connector configuration template.
- **Location**: The location associated with the hardware device.
- **Geo Location**: The geo location associated with the hardware device.
- **Branch Connector Group**: The name of the Branch Connector group.
- **Version**: The version of the Branch Connector.
- **Deploy as Gateway**: The status of gateway mode set as **Enabled** or **Disabled**.
- [Zscaler Gateway Details](#ZscalerGatewayDetails)
[See image.](#General-BCDetails)
[]
- **ZIA Gateway**: The IP address of the Zscaler Internet Access (ZIA) proxy gateway.
- **ZPA Broker**: The IP address of the default Zscaler Private Access (ZPA) (Public or Private Service Edge).
[]
- **Interface**: This field shows user-configured interfaces from where the tunnel originated.
- **Interface Primary Gateway**: The tunnel to the primary ZIA gateway.
- **Status**: The status of the interface primary gateway (i.e., **Up** or **Down**).
- **IP Address**: The IP address of the primary gateway.
- **TX | RX Bytes**: The traffic transferred and received displayed in bytes.
- **TX | RX Packets**: The traffic transferred and received displayed in packets.
- **Uptime**: The time this tunnel instance has been up.
- **Interface Secondary Gateway**: The tunnel to the secondary ZIA gateway.
- **Status**: The status of the secondary gateway (i.e., **Up** or **Down**).
- **IP Address**: The IP address of the secondary gateway.
- **TX | RX Bytes**: The traffic transferred and received displayed in bytes.
- **TX | RX Packets**: The traffic transferred and received displayed in packets.
- **Uptime**: The time this tunnel instance has been up.
[See image.](#ZIATunnel)
[]
- **Interface**: This field shows user-configured interfaces from where the tunnel originated.
- **Interface Tunnel**: The tunnel to the ZPA broker.
- **Status**: The status of the tunnel (i.e., **Up** or **Down**).
- **IP Address**: The IP address of the ZPA tunnel.
- **TX | RX Bytes**: The traffic transferred and received displayed in bytes.
- **TX | RX Packets**: The traffic transferred and received displayed in packets.
- **Uptime**: The time this tunnel instance has been up.
- **Control/Data**: The type of tunnel (i.e., **CONTROL**, **DATA**, or **CONTROL/DATA**).
[See image.](#ZPATunnel)
[]
- [Device Info](#Device_Info)
- [Management Interface](#Management_Interface)
[See image.](#System-BCDetails)
[]
- **Device Serial Number**: The serial number associated with the hardware device.
- **Device Name**: The name of the hardware device.
- **Description**: The description entered for the hardware device.
[]
The management interface is set based on the hardware device selected and cannot be changed. GE1 is set for ZT400 and ZT600. GE3 is set for ZT800.
- **Shutdown**: This field indicates whether the management port is administratively shutdown.
- **DHCP**: This field indicates whether the management interface receives its IP address via the DHCP client or has a statically configured IP address.
- **IP Address**: The IP address of the management interface.
- **Default Gateway**: The IP address of default gateway.
- **Primary DNS Server**: The IP address of primary DNS server.
- **Secondary DNS Server**: The IP address of secondary DNS server.
- **NAT IP Address**: The public IP address of the management interface if it is behind a NAT device.
- **Port Status**: The status of the operational port link.
[]
- **Interface**: This field shows user-configured WAN interfaces.
- **Status**: The status of the operational port link.
- **MTU**: The permissible IP Maximum Transmission Units (MTU) of the parent interface. The default value is `1500` bytes.
- [Untagged](#Untagged)
- **Sub Interface VLAN**: The subinterface and its virtual local area network (VLAN) tag.
- **IP Address**: The IP address of the subinterface.
- **MTU**: The IP MTU of the subinterface. The default value is `1496` bytes. This is always set to 4 bytes less than the MTU of the parent interface.
- [Uplink Mode](#BCDetailsUplinkMode)
- [Traffic Distribution](#TrafficDistribution)
[See image.](#WAN-BCDetails)
[]
- **Untagged**: This field indicates that the interface belongs to an untagged VLAN.
- **IP Address**: The IP address of the interface.
- **Uplink Mode**: You can set this field to **Active** or **Standby** in your Branch Connector Configuration Template. You must set at least one WAN interface to **Active**. You can set the other WAN interface to either **Active** or **Standby**. You can only configure two WAN interfaces. If one interface is set to **Active** and one interface to **Standby**, data traffic goes over the active links. If the probes detect a 100 percent loss on the current active link, failover is triggered. Zscaler also sends WAN link monitoring probes on the standby link and establishes and maintains tunnels to ZIA and ZPA for a fast switchover during a failover from the active link. If both interfaces are set to **Active**, Zscaler actively monitors the health of the links and determines the best link. All WAN-bound traffic follows the traffic distribution method described in [Traffic Distribution](/cloud-branch-connector/analyzing-branch-connector-details#TrafficDistribution). Optionally, for specific applications, you can override the device-wide traffic distribution method using traffic forwarding rules.
- **Configured Mode**: The uplink mode as set by the configuration.
- **Current Mode**: The operational uplink mode, which can be set to **Active**, **Standby**, or **INIT**.
- **DHCP**: This field indicates whether the management interface receives its IP address via the DHCP client or has a statically configured IP address.
- **IP Address**: The IP address of the management interface.
- **Default Gateway**: The IP address of the default gateway.
- **Primary DNS Server**: The IP address of primary DNS server.
- **Secondary DNS Server**: The IP address of secondary DNS server.
- **NAT IP Address**: The public IP address of the management interface if it is behind a NAT device.
- **Link Score**: The quality score of the uplink, determined from measurements of loss, latency, and jitter.
[]
- **Uplink Mode**: You can set this field to **Active** or **Standby** in your Branch Connector Configuration Template. You must set at least one WAN interface to Active. You can set the other WAN interface to either Active or Standby. You can only configure two WAN interfaces. If one interface is set to Active and one interface to Standby, data traffic goes over the active links. If the probes detect a 100 percent loss on the current active link, failover is triggered. Zscaler also sends WAN link monitoring probes on the standby link and establishes and maintains tunnels to ZIA and ZPA for a fast switchover during a failover from the active link. If both interfaces are set to Active, Zscaler actively monitors the health of the links and determines the best link. All WAN-bound traffic follows the traffic distribution method described in Traffic Distribution. Optionally, for specific applications, you can override the device-wide traffic distribution method using traffic forwarding rules.
- **Configured Mode**: The uplink mode as set by the configuration.
- **Current Mode**: The operational uplink mode, which can be set to **Active**, **Standby**, or **INIT**.
- **DHCP**: This field indicates whether the WAN interface receives its IP address via DHCP client or has a statically configured IP address.
- **IP Address**: The IP address of the WAN interface.
- **Default Gateway**: The IP address of the default gateway.
- **Primary DNS Server**: The IP address of primary DNS server.
- **Secondary DNS Server**: The IP address of secondary DNS server.
- **NAT IP Address**: The public IP address of the management interface if it is behind a NAT device.
- **Link Score**: The quality score of the uplink, determined from measurements of loss, latency, and jitter.
[]
The traffic distribution method set on the device. **None** is set by default. **Balanced** indicates that traffic is distributed via all active WAN links. **Best** indicates that traffic is forwarded via the best performing WAN link.
[]
- **Interface**: This field shows user-configured LAN interfaces.
- **Status**: The status, which is reported as **Up** or **Down**.
- **MTU**: The permissible IP Maximum Transmission Units (MTU) of the parent interface. The default value is `1500` bytes.
- **Shutdown**: The shutdown behavior. If set to **Yes**, this shuts down the LAN interface, which brings down the physical port and all of its subinterfaces. If set to **No**, this feature is disabled.
- [Untagged](#LANUntagged)
- [Sub Interface VLAN](#LANSubInterface)
[]
- **Untagged**: The description of the interface.
- **IP Address**: The IP address of the interface.
- **High Availability**: This field is set to **Enabled** or **Disabled**.
- **HA State**: This field is set to **Active**, **Standby**, or **Init**.
- **ID**: This value is set to the same as the ID configured on the HA pair device.
- **Virtual IP Address**: This is set to the virtual IP address of the same network as specified on the corresponding interface.
- **Preferred**: By default, this field is set to **No**. The Preferred value is set to **Yes** on a specific device if you want it to assume the Active role in an HA pair.
- **DHCP Server**: The DHCP server, which is set to **Enabled** or **Disabled**. If it is **Enabled**, you can configure IP address details for DHCP clients to use.
- **Include Address Range**: This range is included as a part of the same network specified on the interface.
- **Default Lease Time**: The default lease time is automatically set to `86400` seconds, but you can change it. The maximum permissible value is `3155673600` seconds.
- **Max Lease Time**: The default maximum lease time is `604800` seconds. The maximum permissible value is `3155673600` seconds.
- **DHCP Options**: The options include **Default Gateway**, **DNS Server**, and **Domain Name**.
- **Static Lease**: The MAC address and the IP assigned to a device with that MAC address. You can configure a maximum of 32 static leases per DHCP server. In HA, the static leases must be duplicated.
[]
- **Sub Interface VLAN**: The description of the subinterface.
- **IP Address**: The IP address of the subinterface.
- **MTU**: The IP MTU of the subinterface. The default value is `1496` bytes. This is always set to 4 bytes less than the MTU of the parent interface.
- **Interface Shutdown**: The shutdown behavior. If set to **Yes**, this shuts down the subinterface, which brings down the specific subinterface selected and does not affect the parent interface or any other subinterface. If set to **No**, this feature is disabled.
- **High Availability**: This field is set to **Enabled** or **Disabled**.
- **HA State**: This field is set to **Active**, **Standby**, or **Init**.
- **ID**: This value is set to the same as the ID configured on the HA pair device.
- **Virtual IP Address**: This is set to the virtual IP address on the same network as specified on the corresponding interface.
- **Preferred**: By default, this field is set to **No**. The Preferred value is set to **Yes** on a specific device if you want it to assume the Active role in an HA pair.
- **DHCP Server**: The DHCP server, which is set to **Enabled** or **Disabled**. If it is **Enabled**, you can configure IP address details for DHCP clients to use.
- **Include Address Range**: This range is included as a part of the same network specified on the interface.
- **Default Lease Time**: The default lease time is automatically set to `86400` seconds, but you can change it. The maximum permissible value is `3155673600` seconds.
- **Max Lease Time**: The default maximum lease time is `604800` seconds. The maximum permissible value is `3155673600` seconds.
- **DHCP Options**: The options include **Default Gateway**, **DNS Server**, and **Domain Name**.
- **Static Lease**: The MAC address and the IP assigned to a device with that MAC address. You can configure a maximum of 32 static leases per DHCP server. In HA, the static leases must be duplicated.
- [LAN DNS](#LANDNS)
[See image.](#LAN-BCDetails)
[]
- **Use WAN DNS Server**: If set to **Yes**, the DNS server from the WAN interfaces is used as the DNS server for LAN. If set to **No**, provides a primary and secondary DNS server. The App Connector uses the LAN DNS servers to resolve the original IP of an application at the branch. The LAN DNS servers can also be referenced in the DNS gateway object, which is then used in DNS policies.
- **Primary DNS Server**: The IP address of the primary DNS server.
- **Secondary DNS Server**: The IP address of the secondary DNS server.
[]
**Static Route**: A list of all admin-configured static routes on the device.
- **Route**: The route IP address of the prefix you want to reach.
- **Gateway**: The gateway IP address.
[See image.](#Routing-BCDetails)
![The Deployment Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/Hypervisordeploymentdetails.png)
[]
[]![The Deployment Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/hardwaredeploymentdetails.png)
[]![The Operational Status section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/hypervisoroperationalstatus.png)
[]![The Operational Status section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/hardwareoperationalstatus.png)
![The Gateway Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/gatewaydetails.png)
[]
![The Device Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/devicedetails.png)
[]
![The Specifications section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/Specifications.png)
[]
![The DNS Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/DNSDetails.png)
[]
![The Ingress Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/IngressDetails.png)
[]
![The Egress Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/EgressDetails.png)
[]
![The Management Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/ManagementDetails.png)
[]
![The DNS Details section of the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/2DNSDetails.png)
[]
[]
![The General Tab of the Branch Connector Details page.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/General-BranchConnectorDetails-MVP1.png)
[]
![The System Tab of the Branch Connector Details page.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/System-BranchConnectorDetails-MVP1.png)
[]
![The WAN Tab of the Branch Connector Details page.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/WANBCDetailsMVP1.png)
[]
![The LAN Tab of the Branch Connector Details page.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/LANBCDetailsMVP1.png)
[]
![The Routing Tab of the Branch Connector Details page.](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/Routing-BranchConnectorDetails-MVP1.png)
[]![The ZIA Tunnel section on the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/AnalyzingBCDetailsZIATunnel.png)
[]![The ZPA Tunnel section on the Branch Connector Details page](/downloads/cloud-branch-connector/analytics-monitoring/analyzing-branch-connector-details/AnalyzingBCDetailsZPATunnel.png)