# Monitoring Internet & SaaS Virtual Service Edge Clusters
Source: https://help.zscaler.com/unified/monitoring-internet-saas-virtual-service-edge-clusters
PDF: https://help.zscaler.com/pdf/com/en/1495611.pdf

If you configured a GRE tunnel or L2 forwarding from your router to an Internet & SaaS Virtual Service Edge, you can enable IPSLAs to monitor the tunnels. Additionally, Virtual Service Edges support NET-SNMP, a collection of applications that are used to implement the SNMP protocol. To learn more about NET-SNMP and the MIB files distributed with NET-SNMP, refer to the [NET-SNMP documentation](http://net-snmp.sourceforge.net/).
You can use a management system that supports SNMPv3 to monitor a Virtual Service Edge cluster. Virtual Service Edge clusters include an SNMP agent that collects data and stores them as objects in Management Information Bases (MIBs). To learn more about accessing Zscaler SNMP MIBs, see [Accessing the Zscaler SNMP MIBs](/unified/accessing-zscaler-snmp-mibs). You can query the objects in the MIBs to retrieve information about the Virtual Service Edge. The SNMP agent can also send traps (or notifications) to alert you when certain events occur on the network or in the Virtual Service Edge.
[]Enabling SNMP for Virtual Service Edge
To enable SNMP for Virtual Service Edge:
-
Edit the `rc.conf` file:
vi /etc/rc.conf
-
Set the following setting to `YES`:
snmpd_enable="YES"
By default, this entry is set to `NO`.
-
Ensure the path of the `snmp.conf` file is as follows:
snmpd_conffile="/usr/local/etc/snmpd.conf"
- Save the` rc.conf` file.
-
Start the SNMP agent daemon (snmpd) service:
service snmpd start
-
Restart the Virtual Service Edge:
sudo vzen restart
Zscaler Recommended MIBs for Monitoring Virtual Service Edges
The following are the Zscaler recommended MIB objects for monitoring Virtual Service Edges:
-
-
-
-
-
-
-
-
| VSE-MIB ( .1.3.6.1.4.1.46262) |
| ----------------------------- |
| Object | Description |
| VSE-MIB::vseName( .1.3.6.1.4.1.46262.9.2) | The name of the Virtual Service Edge. |
| VSE-MIB::ca_connectivity(.1.3.6.1.4.1.46262.9.2.1.5) | The Virtual Service Edge connection to Zscaler Central Authority (CA). It's set to 3 if the connection is established.The connection is not established between Virtual Service Edge and Zscaler Central Authority (CA) if one of the following values is returned:0: Virtual Service Edge is not authenticated.1: Virtual Service Edge authentication is bypassed.2: Virtual Service Edge authentication is bypassed with probe.4: Virtual Service Edge is down. |
| VSE-MIB::smsm_connectivity(.1.3.6.1.4.1.46262.9.2.1.6) | The Virtual Service Edge connection to Zscaler log and reporting infrastructure. It's set to 4 or 5 if the connection is established.The connection is not established between Virtual Service Edge and Zscaler log and reporting infrastructure if one of the following values is returned:2: Initiated logging server connection.3: Waiting for logging server to connect to Virtual Service Edge.6: Closing logging server connection.7: Closed logging server connection. |
| VSE-MIB::cpu_percentage(.1.3.6.1.4.1.46262.4.2.1.12.1) | The CPU usage percentage. It's in integer value (e.g., 5,000); divide the integer value with 100 to get percentage value (e.g., 5,000/100 = 50%). A CPU usage percentage less than 90% is acceptable. If the CPU usage percentage is more than 90% an alert must be triggered. |
| VSE-MIB::swapinfo(.1.3.6.1.4.1.46262.6.2.1.11) | The swap memory usage percentage. It's in integer value (e.g., 3,500); divide the integer value with 100 to get percentage value (e.g., 3,500/100 = 35%). A swap memory usage percentage less than 50% is acceptable. If the swap memory usage percentage is more than 50% an alert must be triggered. |
The following OIDs generate SNMP alert traps by default:
- Process Monitoring – UCD-SNMP-MIB::prTable (.1.3.6.1.4.1.2021.2)
- Disk Monitoring – UCD-SNMP-MIB::dskTable (.1.3.6.1.4.1.2021.9)
- System Load – UCD-SNMP-MIB::laTable (.1.3.6.1.4.1.2021.10)
- Interface Events – IF-MIB::linkDown (.1.3.6.1.6.3.1.1.5.3) and IF-MIB::linkUp (.1.3.6.1.6.3.1.1.5.4)
SNMP MIB Objects
The following are the MIB objects that can be queried to retrieve information about the Virtual Service Edge cluster. To learn more about the objects, refer to the [NET-SNMP documentation](http://www.net-snmp.org/docs/mibs/ucdavis.html).
| UCD-SNMP-MIB (.1.3.6.1.4.1.2021) |
| -------------------------------- |
| Object | Description |
| UCD-SNMP-MIB::prTable(.1.3.6.1.4.1.2021.2) | A table containing information on running programs/daemons configured for monitoring in the snmpd.conf file of the agent. Processes violating the number of running processes required by the agent's configuration file are flagged with numerical and textual errors. |
| UCD-SNMP-MIB::prNames | The process name we're counting or checking on. |
| UCD-SNMP-MIB::prCount | The number of current processes running with the name in question. |
| UCD-SNMP-MIB::prErrorFlag | An error flag to indicate trouble with a process. It goes to 1 if there is an error, 0 if no error. |
| UCD-SNMP-MIB::prErrMessage | An error message describing the problem (if one exists). |
| UCD-SNMP-MIB::dskTable(.1.3.6.1.4.1.2021.9) | Disk watching information. Partitions to be watched are configured by the snmpd.conf file of the agent. |
| UCD-SNMP-MIB::dskPath | Path where the disk is mounted. |
| UCD-SNMP-MIB::dskDevice | Path of the device for the partition. |
| UCD-SNMP-MIB::dskMinPercent | Percentage of minimum space required on the disk before the errors are triggered. |
| UCD-SNMP-MIB::dskTotal | Total size of the disk or partition (kBytes). For large disks (>2Tb), this value latches at INT32_MAX (2147483647). |
| UCD-SNMP-MIB::dskAvail | Available space on the disk. For large lightly-used disks (>2Tb), this value latches at INT32_MAX (2147483647). |
| UCD-SNMP-MIB::laTable(.1.3.6.1.4.1.2021.10) | Load average information. |
| UCD-SNMP-MIB::laLoad | The 1,5 and 15-minute load averages (one per row). |
| UCD-SNMP-MIB::laErrorFlag | An error flag to indicate the load average has crossed its threshold value defined in the snmpd.conf file. It is set to 1 if the threshold is crossed, 0 otherwise. |
| UCD-SNMP-MIB::laErrMessage | An error message describing the load average and its surpassed watch-point value. |
| UCD-SNMP-MIB::systemStats(.1.3.6.1.4.1.2021.11) | System statistics. |
| UCD-SNMP-MIB::memory(.1.3.6.1.4.1.2021.4) | Memory-related information. |
| IF-MIB (.1.3.6.1) |
| ----------------- |
| Object | Description |
| IF-MIB::interfaces(.1.3.6.1.2.1.2) | Information about the interfaces. |
| IF-MIB::ifNumber(.1.3.6.1.2.1.2.1) | The number of network interfaces (regardless of their current state) present on this system. |
| IF-MIB::ifTable- (.1.3.6.1.2.1.2.2) | A list of interface entries. The number of entries is given by the value of ifNumber. |
| IF-MIB::ifDescr | A textual string containing information about the interface. This string should include the name of the manufacturer, the product name and the version of the interface hardware or software. |
| IF-MIB::ifType | The type of interface. Additional values for ifType are assigned by the Internet Assigned Numbers Authority (IANA), through updating the syntax of the IANAifType textual convention. |
| IF-MIB::ifMtu | The size of the largest packet which can be sent or received on the interface, specified in octets. |
| IF-MIB::ifPhysAddress | The interface's address at its protocol sublayer. For example, for an 802.x interface, this object normally contains a MAC address. The interface's media-specific MIB must define the bit and byte ordering and the format of the value of this object. |
| IF-MIB::ifAdminStatus | The desired state of the interface. The testing(3) state indicates that no operational packets can be passed. When a managed system initializes, all interfaces start with ifAdminStatus in the down(2) state. As a result of either explicit management action or per configuration information retained by the managed system, ifAdminStatus is then changed to either the up(1) or testing(3) states (or remains in the down(2) state). |
| IF-MIB::ifOperStatus | The current operational state of the interface. The testing(3) state indicates that no operational packets can be passed. If ifAdminStatus is down(2) then ifOperStatus should be down(2). If ifAdminStatus is changed to up(1) then ifOperStatus should change to up(1) if the interface is ready to transmit and receive network traffic; it should change to dormant(5) if the interface is waiting for external actions (such as a serial line waiting for an incoming connection); it should remain in the down(2) state if and only if there is a fault that prevents it from going to the up(1) state; it should remain in the notPresent(6) state if the interface has missing (typically, hardware) components. |
| IF-MIB::ifInOctets | The total number of octets received on the interface, including framing characters. |
| IF-MIB::ifInUcastPkts | The number of packets, delivered by this sublayer to a higher sublayer, which were not addressed to a multicast or broadcast address at this sublayer. |
| IF-MIB::ifOutOctets | The total number of octets transmitted out of the interface, including framing characters. |
| IF-MIB::ifOutUcastPkts | The total number of packets that higher-level protocols requested be transmitted, and which were not addressed to a multicast or broadcast address at this sublayer, including those that were discarded or not sent. |
| IF-MIB::ifOutNUcastPkts | The total number of packets that higher-level protocols requested be transmitted, and which were addressed to a multicast or broadcast address at this sublayer, including those that were discarded or not sent. |
| IF-MIB::ifPromiscuousMode | This object has a value of false(2) if this interface only accepts packets/frames that are addressed to this station. This object has a value of true(1) when the station accepts all packets or frames transmitted on the media. |
| IF-MIB::linkDown (.1.3.6.1.6.3.1.1.5.3) | The interface link down. |
| IF-MIB::linkUp (.1.3.6.1.6.3.1.1.5.4) | The interface link up. |
| HOST-RESOURCES-MIB (.1.3.6.1.2.1.25) |
| ------------------------------------ |
| Object | Description |
| HOST-RESOURCES-MIB::hrSystem (.1.3.6.1.2.1.25.1) | Information about the host. |
| HOST-RESOURCES-MIB::hrSystemUptime | The amount of time since this host was last initialized. |
| HOST-RESOURCES-MIB::hrSystemDate | The host's notion of the local date and time of day. |
| HOST-RESOURCES-MIB::hrSystemProcesses | The number of process contexts currently loaded or running on this system. |
| HOST-RESOURCES-MIB::hrSystemMaxProcesses | The number of processes that the system can support.The maximum number of process contexts this system can support. If there is no fixed maximum, the value should be zero. On systems that have a fixed maximum, this object can help diagnose failures that occur when this maximum is reached. |
| HOST-RESOURCES-MIB::hrStorage(.1.3.6.1.2.1.25.2) | Information about the storage areas of the host. |
| HOST-RESOURCES-MIB::hrStorageType | The type of storage represented by this entry. |
| HOST-RESOURCES-MIB::hrStorageDescr | A description of the type and instance of the storage described by this entry. |
| HOST-RESOURCES-MIB::hrStorageSize | The size of the storage represented by this entry, in units of hrStorageAllocationUnits. |
| HOST-RESOURCES-MIB::hrStorageUsed | The amount of the storage represented by this entry that is allocated, in units of hrStorageAllocationUnits. |
| HOST-RESOURCES-MIB::hrStorageAllocationUnits | The size, in bytes, of the data objects allocated from this pool. If this entry is monitoring sectors, blocks, buffers, or packets, for example, this number is commonly greater than one. Otherwise, this number is typically one. |
| SNMPv2-MIB::system (.1.3.6.1.2.1.1) |
| ----------------------------------- |
| Object | Description |
| SNMPv2-MIB::sysContact | The textual identification of the contact person for this managed node, together with information on how to contact this person. If no contact information is known, the value is the zero-length string. |
| SNMPv2-MIB::sysName | An administratively assigned name for this managed node. By convention, this is the node's fully qualified domain name. If the name is unknown, the value is the zero-length string. |
| SNMPv2-MIB::sysLocation | The physical location of this node (e.g., 'telephone closet, 3rd floor'). If the location is unknown, the value is the zero-length string. |
| SNMPv2-MIB::sysServices | A value which indicates the set of services that this entity may potentially offer. The value is a sum. This sum initially takes the value 0. Then, for each layer, L, in the range 1 through 7, that this node performs transactions for, 2 raised to (L - 1) is added to the sum. For example, a node which performs only routing functions would have a value of 4 (2^(3-1)). In contrast, a node which is a host offering application services would have a value of 72 (2^(4-1) + 2^(7-1)). In the context of the internet suite of protocols, values should be calculated accordingly:**Layer** **Functionality**1 physical (e.g., repeaters)2 datalink/subnetwork (e.g., bridges)3 internet (e.g., supports the IP)4 end-to-end (e.g., supports the TCP)7 applications (e.g., supports the SMTP)For systems including OSI protocols, layers 5 and 6 may also be counted. |
| SNMPv2-MIB::snmpEnableAuthenTraps | Indicates whether the SNMP entity is permitted to generate authenticationFailure traps. The value of this object overrides any configuration information; as such, it provides a means whereby all authenticationFailure traps might be disabled. |
| SNMPv2-MIB::snmpInPkts | The total number of messages delivered to the SNMP entity from the transport service. |
| SNMPv2-MIB::snmpOutPkts | The total number of SNMP Messages which were passed from the SNMP protocol entity to the transport service. |
| SNMPv2-MIB::snmpInGetRequests | The total number of SNMP Get-Request PDUs which have been accepted and processed by the SNMP protocol entity. |
| SNMPv2-MIB::snmpOutGetResponses | The total number of SNMP Get-Request PDUs which have been generated by the SNMP protocol entity. |
| SNMPv2-MIB::snmpOutTraps | The total number of SNMP Trap PDUs which have been generated by the SNMP protocol entity. |
-
-
-
| TCP-MIB (.1.3.6.1.2.1.6) |
| ------------------------ |
| Object | Description |
| TCP-MIB::tcpActiveOpens | The number of times that TCP connections have made a direct transition to the SYN-SENT state from the CLOSED state. |
| TCP-MIB::tcpPassiveOpens | The number of times TCP connections have made a direct transition to the SYN-RCVD state from the LISTEN state. |
| TCP-MIB::tcpCurrEstab | The number of TCP connections for which the current state is either ESTABLISHED or CLOSE-WAIT. |
| TCP-MIB::tcpConnectionTable | A table containing information about existing TCP connections. |
| TCP-MIB::tcpListenerTable | A table containing information about TCP listeners. A listening application can be represented in three possible ways:An application that is willing to accept both IPv4 and IPv6 datagrams is represented by a tcpListenerLocalAddressType of unknown (0) and a tcpListenerLocalAddress of ''h (a zero-length octet-string).An application that is willing to accept only IPv4 or IPv6 datagrams is represented by a tcpListenerLocalAddressType of the appropriate address type and a tcpListenerLocalAddress of '0.0.0.0' or '::' respectively.An application that is listening for data destined only to a specific IP address, but from any remote system, is represented by a tcpListenerLocalAddressType of an appropriate address type, with tcpListenerLocalAddress as the specific local address.The address type in this table represents the address type used for the communication, irrespective of the higher-layer abstraction. For example, an application using IPv6 'sockets' to communicate via IPv4 between ::ffff:10.0.0.1 and ::ffff:10.0.0.2 would use InetAddressType ipv4(1))." |
Virtual Service Edge Traps
The Virtual Service Edge SNMP agent generates traps when the following events occur:
Process Monitoring
- The snmpd restarts
- The SME goes down - The link to the Zscaler cloud becomes inactive
- The number of mountd processes is more than 1
- The number of ntalkd processes goes out of range (0–4)
- The number of sendmail processes goes out of range (1–10)
Disk Monitoring
- The root partition has less than 10 MBs of space
- Any of the other partitions have less than 10% space
System Load
- The load average crosses the threshold: 3 for 1 minute, 2 for 5 minutes, 1 for 15 minutes
- CPU usage goes beyond 90%
Interface events
- The link goes down or comes up
Virtual Service Edge Health Monitoring
Zscaler performs ICMP and HTTP monitoring from the Load Balancer (LB) to the Virtual Service Edge in order to monitor the health of the instance and ensure that traffic is distributed appropriately. If you wish to perform this monitoring yourself, you can enable an HTTP server on a Virtual Service Edge by implementing the following commands:
-
Go to the /sc/sme/conf folder:
cd /sc/sme/conf
-
Create a custom configuration file (e.g., vzen_custom.conf):
touch vzen_custom.conf
-
Edit the vzen_custom.conf file:
vi vzen_custom.conf
-
Enter the following port in the vzen_custom.conf file and save:
[SME]
serv_port=3128
[-end-of-SME-]
-
Ensure that the entries are saved in the vzen_custom.conf file:
cat vzen_custom.conf
-
Restart the SME instance:
/sc/update/vzen stop sme
/sc/update/vzen start sme
-
Ensure that the SME is running:
vzen status
You can check if the Virtual Service Edge is listening to port 3128 using the following command:
ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys smnet="netstat" | grep LISTEN | grep 3128
-
Enter the following command prompt:
curl -v http://<Virtual Service Edge IP>:3128/index.html?=100
The number 100 represents the size of the response sent back to the client making the cURL request. This means that if the monitoring tool makes a request to the URL http://< Virtual Service Edge IP>:3128/index.html?=100, the Virtual Service Edge responds back with a 200 OK and a payload size of 100 bytes.
After the commands have been applied, you can use the LB to fetch the page and investigate the availability of a particular Virtual Service Edge. This does not include ICMP monitoring.