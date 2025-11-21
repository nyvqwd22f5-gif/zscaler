# Networking Deployed Network Connectors
Source: https://help.zscaler.com/unified/networking-deployed-network-connectors
PDF: https://help.zscaler.com/pdf/com/en/1532386.pdf

After you have deployed the Network Connector, you can complete the following networking configurations:
- [Configure Network Time Protocol (NTP) Servers for a Network Connector](#NTP)
- [Configure Static IP Addressing for a Network Connector](#Static_IP)
- [Configure the Domain Name System (DNS) Resolver for a Network Connector](#DNS)
[]An administrator must configure a static IP address on a VM-based Network Connector.
- Log in to the Network Connector console using your admin credentials.
- View the current connection profile.
[admin@np-connector ~]$ nmcli connection show
- Modify the connection profile using the following format: <profile name> connection.id <new connection name>. For example:
`[admin@np-connector ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
- Review the current connection profile.
`[admin@np-connector ~]$ nmcli connection show`
- Edit the profile using a static IP and a default gateway with the following format: <connection ID> ipv4.method manual ipv4.addresses <IP addresses> ipv4.gateway <gateway IP> ipv4.dns <DNS IP> ipv4.dns-search <domain name>. For example:
`[admin@np-connector ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
- To apply the changes, bring the connection ID back up. For example:
`[admin@np-connector ~]$ sudo nmcli connection up LAN `
- Verify the IP address.
`[admin@np-connector ~]$ ip addr show`
- Verify the default gateway.
[admin@np-connector ~]$ ip route show default
- Verify the DNS settings.
[admin@np-connector ~]$ sudo cat /etc/resolv.conf
[]To configure Network Connectors to use internal NTP servers:
- Log in to the Network Connector console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@np-connector ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list, for example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@np-connector ~]$ systemctl restart chronyd
- To verify the NTP servers, check that NTP is working successfully using the following command:
[admin@np-connector ~]$ chronyc sources
[]DNS resolution is critical for the successful operation of the Network Connector. Network Connectors must also be able to resolve external DNS names, such as those of the Private Applications cloud infrastructure.
- Log in to the Network Connector console using your admin credentials.
- View the current connection profile.
[admin@np-connector ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@np-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@np-connector ~]$ sudo nmcli connection down "Profile 1"[admin@np-connector ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@np-connector ~]$ sudo cat /etc/resolv.conf