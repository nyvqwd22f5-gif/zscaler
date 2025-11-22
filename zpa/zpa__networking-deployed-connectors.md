# Networking Deployed App Connectors
Source: https://help.zscaler.com/zpa/networking-deployed-connectors
PDF: https://help.zscaler.com/pdf/com/en/1484131.pdf

After you have deployed the App Connector on a supported platform, you can complete the following networking configurations:
- [Configure Additional Interfaces for an App Connector](#Interfaces)
- [Configure an App Connector to Use an Explicit Proxy Server](#proxy)
- [Configure DHCP IP Addressing for an App Connector](#DHCP_IP)
- [Configure Domain Name System (DNS) Resolver for an App Connector](#DNS)
- [Configure Network Time Protocol (NTP) Servers for an App Connector](#NTP)
- [Configure a Proxy Bypass for an App Connector](#proxybypass)
- [Configure Static IP Addressing for an App Connector](#Static_IP)
- [Configure Static Routing for an App Connector](#Routing)
- [Configure TCP Communication Sockets for an App Connector](#Tcpcommunication)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
- [Verify That Keepalive Is Enabled for TCP Sessions](#verify-keep-alive)
[]By default, virtual machine-based App Connectors are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for the App Connector.
[]If DHCP is not available, you can configure a static IP address on a VM-based App Connector.
- Log in to the App Connector console using your admin credentials.
- View the current connection profile.
[admin@zpa-connector ~]$ nmcli connection show
- Modify the connection profile using the following format: <profile name> connection.id <new connection name>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
- Review the current connection profile.
`[admin@zpa-connector ~]$ nmcli connection show`
- Edit the profile using a static IP and a default gateway with the following format: <connection ID> ipv4.method manual ipv4.addresses <IP addresses> ipv4.gateway <gateway IP> ipv4.dns <DNS IP> ipv4.dns-search <domain name>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
- To apply the changes, bring the connection ID back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection up LAN `
- Verify the IP address.
`[admin@zpa-connector ~]$ ip addr show`
- Verify the default gateway.
[admin@zpa-connector ~]$ ip route show default
- Verify the DNS settings.
[admin@zpa-connector ~]$ sudo cat /etc/resolv.conf
[]If necessary, additional changes can be made to interfaces by configuring new ones using nmcli connection add con-name or by renaming existing ones using nmcli connection modify.
- Log in to the App Connector console using your admin credentials.
- View the IP address.
[admin@zpa-connector ~]$ ip addr show
- View the current connection profiles.
[admin@zpa-connector ~]$ nmcli connection show
- Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For static, modify the connection profile and identify the IP addresses and gateway using the following format: <profile name> ipv4.method manual ipv4.addresses <address> ipv4.gateway <gateway IP>. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254`
- To apply the changes, bring the connection profile back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1" `
- Reverify the IP address.
`[admin@zpa-connector ~]$ ip addr show`
- Reverify the new connection.
`[admin@zpa-connector ~]$ nmcli connection show`
[]To add static routes to the interface control files for an App Connector:
- Log in to the App Connector console using your admin credentials.
- Edit the static route for an existing Ethernet connection using the following format: <profile name> ipv4.routes <address and gateway>. For example:
[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes "192.168.2.241/24 10.10.10.1"
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-connector ~]$ sudo nmcli connection down "Profile 1" [admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1"
- Verify the new route is added.
[admin@zpa-connector ~]$ ip route
[]DNS resolution is critical for the successful operation of the App Connector. App Connectors use DNS to discover applications, as well as enumerate each of the IP addresses that an application DNS name resolves to as a separately tracked and load-balanced server. During dynamic application discovery, DNS is used as the initial reachability check from each App Connector in an App Connector group. It is possible for App Connectors to function in partitioned environments where a subset of App Connectors are able to resolve a given DNS name without additional configuration. App Connectors must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the App Connector console using your admin credentials.
- View the current connection profile.
[admin@zpa-connector ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@zpa-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
`[admin@zpa-connector ~]$ sudo nmcli connection down "Profile 1"`` [admin@zpa-connector ~]$ sudo nmcli connection up "Profile 1"`
- Verify the nameservers record was added.
`[admin@zpa-connector ~]$ sudo cat /etc/resolv.conf`
[]You cannot configure NTP servers for App Connectors running on the Amazon Web Services (AWS) or Microsoft Azure platforms.
To configure App Connectors to use internal NTP servers:
- Log in to the App Connector console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@zpa-connector ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list, for example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-connector ~]$ systemctl restart chronyd
- To verify the NTP servers, check that NTP is working successfully using the following command:
[admin@zpa-connector ~]$ chronyc sources
[]The proxy setting on the App Connector is used to proxy the traffic between the App Connector and the ZPA Private Service Edge. It is not used to proxy the traffic between the App Connector and internal applications.
If your traffic is going through a proxy (i.e., traffic between the App Connector and the ZPA Public Service Edges or ZPA Private Service Edges), you must manually configure the App Connector to work through that proxy. The following procedure allows the App Connector to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the App Connector to work through an explicit proxy:
- Log in to the App Connector console using your admin credentials.
- Create a file named /opt/zscaler/var/proxy. Use an editor, such as vi.
[admin@zpa-connector ~]$ sudo vi /opt/zscaler/var/proxy
Enter the proxy information using the following format: <Proxy Hostname or IP Address>:<Proxy Port> (e.g., 192.0.2.0:0).
- To apply the changes, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
The App Connector attempts to create a TLS session through the proxy specified previously.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.
To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).
[]If an App Connector is configured to send traffic to a proxy, you can set up a proxy bypass on it for the traffic that needs to be exempted from the proxy (i.e., traffic between the App Connector and the ZPA Public Service Edges or Public Service Edges). To use a proxy bypass for an App Connector, a proxy bypass file needs to be added to the App Connector.
To configure the App Connector to do a proxy bypass:
- Log in to the App Connector console using your admin credentials.
- Create a file named `opt/zscaler/var/proxy-bypass`. Use an editor, such as vi. For example:
[admin@zpa-connector ~]$sudo vi /opt/zscaler/var/proxy-bypass
- Enter the necessary bypass entries using IP addresses, subnets, domains, or domains with a prefix wildcard. For example:
1.2.3.4
111.222.33.0/24
myexampledomain.com
*.internal.local
- To apply the changes, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
[]To temporarily configure TCP communication sockets using the profs interface and the `SO_KEEPALIVE` socket option for an App Connector:
- Enable **TCP Keepalive** for your segment group in the ZPA Admin Portal. To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
The socket used for TCP communication is set to `SO_KEEPALIVE` and establishes an App Connector-to-Server connection. Communication using this socket looks at the system value corresponding to `SO_KEEPALIVE` and performs the action according to the parameters.
- Tune your App Connector's kernel to configure the TCP parameters and choose how the keepalive packets are sent using the following commands:
# echo 600 > /proc/sys/net/ipv4/tcp_keepalive_time
# echo 60 > /proc/sys/net/ipv4/tcp_keepalive_intvl
# echo 20 > /proc/sys/net/ipv4/tcp_keepalive_probes
Default values are used if no system parameters are chosen. The values in red represent examples of values that can be configured.
Changes to the App Connector's kernel to configure the TCP parameters using the profs interface are temporary and return to default after reboot.
To permanently configure TCP communication sockets using the sysctl interface:
- Enable **TCP Keepalive** for your segment group in the ZPA Admin Portal. To learn more, see [Configuring Defined Application Segments](/zpa/configuring-application-segments).
- Edit your `/etc/sysctl.conf` using the following command:
# vi /etc/sysctl.conf
- Tune your App Connector's kernel to configure the TCP parameters and choose how the keepalive packets are sent using the following commands:
net.ipv4.tcp_keepalive_time = 60
net.ipv4.tcp_keepalive_intvl = 10
net.ipv4.tcp_keepalive_probes = 6
Default values are used if no system parameters are chosen. The values in red represent examples of values that can be configured.
- To load the settings, enter the following command:
# sysctl -p
The keepalive packets have the following parameters:
| Parameter | Definition | Default Value |
| --------- | ---------- | ------------- |
| `tcp_keepalive_time` | The interval between the last data packet sent (simple ACKs are not considered data) and the first keepalive probe; after the connection is marked to need keepalive, this counter is not used any further. | 7,200 seconds (2 hours) |
| `tcp_keepalive_intvl` | The interval between subsequent keepalive probes, regardless of what the connection has exchanged in the meantime. | 75 seconds |
| `tcp_keepalive_probes` | The number of unacknowledged probes to send before considering the connection dead and notifying the application layer. The `tcp_keepalive_probes` value is a pure number. | 9 |
For example:
- If the `tcp_keepalive_time value` is one hour, the keepalive routines wait for one hour before sending the first keepalive probe, and then resend it at a 75-second interval according to the `tcp_keepalive_intvl` value.
- If the `tcp_keepalive_intvl` value is 60 seconds, the keepalive probes are sent every 60 seconds after the initial `tcp_keepalive_time` value.
- If the `tcp_keepalive_probes` value is 7, and no ACK response is received after 7 consecutive times, then the connection is marked as broken.
If there is no data communication within the `tcp_keepalive_time` value, it sends out a keepalive probe to the app server:
- If ACK is returned, another keepalive probe is sent after 2 hours (`tcp_keepalive_time`) if no data communication happens in between.
- If RST is returned, then the socket closes.
- If there is no reply, it resends the keepalive every 75 seconds (`tcp_keepalive_intvl`) for a reply, and it retries 9 times (`tcp_keepalive_probes`). If there is no reply after 9 probes, the socket closes.
To learn more about configuring a kernel, refer to the [Linux documentation](https://tldp.org/HOWTO/html_single/TCP-Keepalive-HOWTO/#configuringkernel).
[]To see which TCP sessions have `keepalive` enabled and what their current timer is, run the `ss` command on the App Connector with the `-t` (tcp only) and `-o` (show timers) options:
`# ss -to
State  Recv-Q  Send-Q  Local Address:Port  Peer Address:Port
ESTAB  0       0       10.18.4.210:42452   10.251.33.110:https  timer:(keepalive,29sec,0)`
For sessions that have `keepalive` enabled, timer information (`timer:(<timer_name>,<expire_time>,<retrans>)`) indicates when `keepalive` will be sent. To learn more, refer to the [Linux documentation](https://www.man7.org/linux/man-pages/man8/ss.8.html).