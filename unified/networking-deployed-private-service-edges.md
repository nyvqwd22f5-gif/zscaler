# Networking Deployed Private Service Edges
Source: https://help.zscaler.com/unified/networking-deployed-private-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1496771.pdf

Before you deploy the Private Service Edge on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Service Edge](#DHCP_IP)
- [Configure Static IP Addressing for a Private Service Edge](#Static_IP)
- [Configure Additional Interfaces for a Private Service Edge](#Interfaces)
- [Configure Static Routing for a Private Service Edge](#Routing)
- [Configure the Domain Name System (DNS) Resolver for a Private Service Edge](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](#NTP)
- [Configure a Private Service Edge to Use an Explicit Proxy Server](#proxy)
- [Configure yum to Use an HTTP Proxy Server](#yumhttpproxy)
[]By default, virtual machine-based Private Service Edges are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Service Edge.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Service Edge.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/ifcfg-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth0
In the following example, the edited file is using a Private Service Edge IP address of 192.168.2.100, highlighted in green:
DEVICE="eth0"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- Edit the /etc/sysconfig/network file and configure the default gateway. For example:
NETWORKING=yes
GATEWAY=192.168.2.254
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]If necessary, additional interfaces can be configured by creating additional files in /etc/sysconfig/network-scripts.
- Log in to the Private Service Edge console using your admin credentials.
- Copy the /etc/sysconfig/network-scripts/ifcfg-eth0 file to /etc/sysconfig/network-scripts/ifcfg-eth1. For example:
[admin@zpa-service-edge ~]$ sudo cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth1
- Edit the new /etc/sysconfig/network-scripts/ifcfg-eth1 file with the network configuration information required for the interface. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/sysconfig/network-scripts/ifcfg-eth1
The content within the new file should be similar to the following:
DEVICE="eth1"
BOOTPROTO="none"
ONBOOT="yes"
NETWORK="192.168.2.0"
NETMASK="255.255.255.0"
IPADDR="192.168.2.100"
USERCTL="no"
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To add static routes to the interface control files for a Private Service Edge:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/sysconfig/network-scripts/route-eth0 file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/sysconfig/network-scripts/route-eth0
Add additional static routes using the following format: <CIDR> via <GATEWAY> dev <INTERFACE>. For example:
192.168.0.0/16 via 192.0.2.1 dev eth0
172.16.0.0/12 via 192.0.2.1 dev eth0
10.0.0.0/8 via 192.0.2.2 dev eth0
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]DNS resolution is critical for the successful operation of the Private Service Edge. Private Service Edges must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/resolv.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/resolv.conf
Replace the example nameserver IP addresses and search domains with your company-specific configuration. For example:
nameserver 8.34.34.34
nameserver 8.35.35.35
search myexampledomain.com
- To apply the changes, restart the networking subsystem using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart network
[]To configure Private Service Edges to use internal NTP servers:
- Log in to the Private Service Edge console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@zpa-service-edge ~]$ systemctl restart chronyd
[]If your traffic is going through a proxy, you must manually configure the Private Service Edge to work through that proxy. The following procedure allows the Private Service Edge to communicate with the broker by using CONNECT requests through a standard HTTP proxy server.
To configure the Private Service Edge to work through an explicit proxy:
- Log in to the Private Service Edge console using your admin credentials.
- Create a file named, /opt/zscaler/var/service-edge/proxy. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/proxy
Enter the proxy information using the following format: <Proxy Hostname or IP Address>:<Proxy Port> (e.g., 192.0.2.0:0).
- To apply the changes, restart the Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The Private Service Edge will attempt to create a TLS session through the proxy specified in step 2.
[]If you want to configure yum to communicate through an HTTP proxy server, refer to the [CentOS](https://docs.centos.org/en-US/docs/) and [Red Hat](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/ch-yum) documentation.