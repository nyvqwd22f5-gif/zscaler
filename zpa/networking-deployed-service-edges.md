# Networking Deployed ZPA Private Service Edges
Source: https://help.zscaler.com/zpa/networking-deployed-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1484536.pdf

Before you deploy the ZPA Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a ZPA Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a ZPA Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a ZPA Private Service Edge](#Interfaces)
- [Configure Static Routing for a ZPA Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a ZPA Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a ZPA Private Service Edge](#NTP)
- [Configure a ZPA Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based ZPA Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a ZPA Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based ZPA Private Service Edge.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the connection profile using the following format: `<profile name>`` connection.id ``<new connection name>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN
- Review the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Edit the profile using a static IP address and a default gateway with the following format: `<connection ID>`` ipv4.method manual ipv4.addresses ``<IP addresses> ``ipv4.gateway ``<gateway IP> ``ipv4.dns ``<DNS IP> ``ipv4.dns-search ``<sub.subdomain.domain.com subdomain.domain.com domain.com>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com
- To apply the changes, bring the connection connection ID back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up LAN
- Verify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Verify the default gateway.
[admin@zpa-service-edge ~]$ ip route show default
- Verify the DNS settings.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]If necessary, additional changes can be made to interfaces by configuring new ones using `nmcli connection add con-name` or by renaming existing ones using `nmcli connection modify`.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- View the current connection profiles.
[admin@zpa-service-edge ~]$ nmcli connection show
- Configure the interface's IP network using either a dynamic or static Ethernet configuration.
For dynamic, modify the connection profile. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto
For static, modify the connection profile and identify the IP addresses and gateway using the following format: `<profile name>`` ipv4.method manual ipv4.addresses ``<address>`` ipv4.gateway ``<address>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254
- To apply the changes, bring the connection profile back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Reverify the IP address.
[admin@zpa-service-edge ~]$ ip addr show
- Reverify the new connection.
[admin@zpa-service-edge ~]$ nmcli connection show
[]To add static routes to the interface control files for a ZPA Private Service Edge:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the static route for an existing Ethernet connection using the following format: `<profile name>`` ipv4.routes ``<address and gateway>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.routes "192.168.2.241/24 10.10.10.1"
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1" [admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the new route is added.
[admin@zpa-service-edge ~]$ ip route
[]DNS resolution is critical for the successful operation of the ZPA Private Service Edge. ZPA Private Service Edges must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the ZPA Private Service Edge console using your admin credentials.
- View the current connection profile.
[admin@zpa-service-edge ~]$ nmcli connection show
- Modify the DNS settings using the following format: `<profile name> ``ipv4.dns`` <nameserver IP>`. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@zpa-service-edge ~]$ sudo nmcli connection down "Profile 1"[admin@zpa-service-edge ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@zpa-service-edge ~]$ sudo cat /etc/resolv.conf
[]To configure ZPA Private Service Edges to use internal NTP servers:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the `/etc/chrony.conf` file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the ZPA Private Service Edge to work through that proxy. The following procedure allows the ZPA Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the ZPA Private Service Edge to work through an explicit proxy:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Create a file named `/opt/zscaler/var/service-edge/proxy`. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: `<Proxy Hostname or IP Address>``:``<Proxy Port>` (e.g., `192.0.2.0:0`).
- To apply the changes, restart the ZPA Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The ZPA Private Service Edge will attempt to create a TLS session through the proxy specified previously.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation. To learn more about support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x, see [End-of-Support for CentOS 7.x, RHEL 7.x, and Oracle Linux 7.x](/eos-eol/end-support-centos-7.x-rhel-7.x-and-oracle-linux-7.x).