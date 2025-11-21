# Resolving Zscaler Client Connector Linux 1.2 DNS Configuration Issues for VPNs
Source: https://help.zscaler.com/zscaler-client-connector/resolving-zscaler-client-connector-linux-1.2-dns-configuration-issues-vpns
PDF: https://help.zscaler.com/pdf/com/en/1385861.pdf

Zscaler Client Connector for Linux 1.2 requires changes to the DNS configuration for older third-party VPNs, like Pulse Secure and Cisco AnyConnect, in order for it to work for ZIA only mode. These changes are not required if you are using both ZIA and ZPA or if you are using modern VPN clients like Openconnect.
Complete the following to resolve the issue:
- Run command `resolvectl` or `systemd-resolve --status` to identify the physical network interface's DNS search domains. This information will be required later.
You must complete this step prior to connecting to the VPN server.
- Connect to the VPN server and log in.
- Run the `ifconfig` command to identify the VPN network interface name (e.g., tun0 for Pulse Secure).
- Run command `cat /etc/resolv.conf` to gather the VPN name server and search domain information.
- Find the IP addresses for the VPN name server in the `nameserver` lines. Ignore the 127.0.0.53 IP address in the `nameserver` line.
- Find the domains in the `search` line for the VPN domain names. Ignore the physical network interface’s search domains identified in step 1.
In the following example, the VPN `nameserver` IPs are `10.11.12.13` and `10.11.12.14`, and the domain is `corp.testco.com`. They are highlighted in green.
$ cat /etc/resolv.conf
search corp.testco.com localdomain
nameserver 10.11.12.13
nameserver 10.11.12.14
nameserver 127.0.0.53
- Run the /opt/zscaler/scripts/config_vpn_dns.sh script with root permission using the information gathered in steps 3 and 4. Use the command format: `sudo ./vpn_dns_config.sh` `<vpn_interface_name> <vpn_name_server> <vpn_search_domain>`.
If either `<vpn_name_server>` or `<vpn_search_domain>` have multiple entries, they should be separated by a space with quotation marks on either side of all the entries.
For example:
sudo ./config_vpn_dns.sh tun0 "10.11.12.13 10.11.12.14" corp.testco.com