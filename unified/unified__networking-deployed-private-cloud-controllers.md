# Networking Deployed Private Cloud Controllers
Source: https://help.zscaler.com/unified/networking-deployed-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1528736.pdf

Before you deploy the Private Cloud Controller on a supported platform, you need to complete the following networking configurations:
- [Configure DHCP IP Addressing for a Private Cloud Controller](#DHCP_IP)
- [Configure Static IP Addressing for a Private Cloud Controller](#Static_IP)
- [Configure the Domain Name System (DNS) Resolver for a Private Cloud Controller](#DNS)
- [Configure Network Time Protocol (NTP) Servers for a Private Cloud Controller](#NTP)
[]By default, virtual machine-based Private Cloud Controllers are configured to use DHCP networking on their primary interface. If necessary, you can configure a static IP address for a Private Cloud Controller.
[]If DHCP is not available, you can configure a static IP address on a VM-based Private Cloud Controller.
- Log in to the Private Cloud Controller console using your admin credentials.
- View the IP address.
` [admin@pcc ~]$ ip addr show`
- View the current connection profiles.
` [admin@pcc ~]$ nmcli connection show`
- Modify the connection profile to configure the interface's IP network for a dynamic Ethernet connection by using the following format: sudo nmcli connection modify <profile name> ipv4.method auto. For example:
` [admin@pcc ~]$ sudo nmcli connection modify "Profile 1" ipv4.method auto`
For a static Ethernet connection, modify the connection profile to identify the IP addresses and gateway using the following format: sudo nmcli connection modify <profile name> ipv4.method manual ipv4.<IPv4 address> ipv4.gateway<IPv4 gateway>.
` [admin@pcc ~]$ sudo nmcli connection modify "Profile 1" ipv4.method manual ipv4.addresses 192.168.2.241/24 ipv4.gateway 192.168.2.254`
- Apply the changes to bring the connection profile back up using the following format: sudo nmcli connection up <profile name>.
` [admin@pcc ~]$ sudo nmcli connection up "Profile 1"`
- Verify the IP address.
` [admin@pcc ~]$ ip addr show`
- Review the new connection profile.
`[admin@pcc ~]$ nmcli connection show`
[]DNS resolution is critical for the successful operation of the Private Cloud Controller. Private Cloud Controllers must also be able to resolve external DNS names, such as those of the cloud infrastructure.
- Log in to the Private Cloud Controller console using your admin credentials.
- View the current connection profile.
[admin@pcc ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@pcc ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@pcc ~]$ sudo nmcli connection down "Profile 1"[admin@pcc ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@pcc ~]$ sudo cat /etc/resolv.conf
[]To configure Private Cloud Controllers to use internal NTP servers:
- Log in to the Private Cloud Controller console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@pcc ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list. For example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@pcc ~]$ systemctl restart chronyd