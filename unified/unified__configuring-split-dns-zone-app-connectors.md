# Configuring a Split DNS Zone for App Connectors
Source: https://help.zscaler.com/unified/configuring-split-dns-zone-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496186.pdf

You can implement a split DNS configuration on your [App Connectors](/unified/about-app-connectors) by using the Linux based service Unbound. Unbound is a validating, recursive, and caching DNS server and it enables you to build a cache-only or forwarding DNS server. However, it cannot be used as an authoritative DNS server, so it cannot be used to host custom domain name records. To learn more, see the [Unbound documentation](https://nlnetlabs.nl/documentation/unbound/unbound/).
Prerequisites
Ensure you have privileged access to a Red Hat 7 Linux server with standard Red Hat repositories.
If you see a "You are not registered with RHN" warning message, ensure you have a licensed version of Linux.
Configuring a Split Zone
- [Step 1: Install unbound](#install)
- [Step 2: Configure unbound](#configure)
- [Step 3: Configure DNSSEC support](#dnssec)
- [Step 4: Test Unbound configuration](#test)
- [Step 5: Configure forward zones](#forward)
- [Step 6: Enable and start the Unbound server](#enable)
- [Step 7: Test server configuration](#server)
[]To begin you need to install the Unbound DNS server and the DNS tools you need to test your configuration.
To install Unbound:
- Install by entering the following command: yum install unbound bind-utils
- Verify the Unbound folder is present by entering the following command: cd /etc/unbound
Make sure unbound.conf appears in this folder. This file is essential to the setup.
[]Next, configure the server by editing Unbound’s configuration file with a text editor.
To do this:
- Open the configuration file /etc/unbound/unbound.conf with your preferred text editor.
- Instruct the server to listen on all local network interfaces by locating and uncommenting the line: # interface: 0.0.0.0.
- Enable the listening port by locating and uncommenting the line: # port: 53
- Enable IPv4, UDP, and TCP queries to be answered and issued by locating and uncommenting the following:
- do-ip4: yes
- do-udp: yes
- do-tcp: yes
Ensure the value is set to yes and not no.
- Log every unbound connection by adding the following: logfile: /var/log/unbound
- Hide the id.server and hostname.bind queries by locating and uncommenting: # hide-identity: yes
Ensure the value is set to yes and not no.
- Hide the version.server and version.bind queries by locating and uncommenting: # hide-version: yes
Ensure the value is set to yes and not no.
- Allow select clients to query this unbound server. Locate and uncomment the access-control command and set it to the following: access-control: <IP netblock> allow
The netblock can be entered as an IPv4 or IPv6 address and if you want to allow anyone to query this server, enter 0.0.0.0.
You can replace allow with allow_snoop to enable recursive and non-recursive queries.
- Once you have made your changes, save the file and exit the text editor.
[]Instruct the Unbound DNS server to generate RSA keys in order to provide DNSSEC support.
To do this:
- Enter the following command: unbound-control-setup
Upon a successful configuration, you will see the following message:
setup in directory /etc/unbound
generating unbound_server.key
Generating RSA private key, 1536 bit long modulus
.................++++
.........++++
e is 65537 (0x10001)
generating unbound_control.key
Generating RSA private key, 1536 bit long modulus
.........++++
..................................++++
e is 65537 (0x10001)
create unbound_server.pem (self signed certificate)
create unbound_control.pem (signed client certificate)
Signature ok
subject=/CN=unbound-control
Getting CA Private Key
Setup success. Certificates created. Enable in unbound.conf file to use
(Optional) Disable DNSSEC
If your upstream servers don't support DNSSEC, disable it for Unbound or you might not see responses for your dig requests.
To do this:
- Edit the Unbound configuration file /etc/unbound/unbounds.conf and uncomment: val-permissive-mode: yes
Or,
- Run the following SED command: sed -i '/val-permissive-mode: yes$/s/#//' /etc/unbound/unbound.conf
[]After completing your initial installation, perform a check to ensure Unbound’s configuration doesn’t contain syntax or other errors. To do this:
- Enter the following command: unbound-checkconf
If there are no errors, you will see the following message:
unbound-checkconf: no errors in /etc/unbound/unbound.conf
[]Next, you need to configure DNS forwarders. These control how your DNS zones are split.
To do this:
- Open /etc/unbound/conf.d with your preferred text editor.
- Add forward zones. For each forward zone enter the following:
- **forward-zone**: Leave this blank
- **name**: Add a domain name. All queries to this domain go to the server you list in the following fields. Add "." as the name to forward all remaining queries.
- **forward-addr**: Add the IP address for your server. You can choose to either list an IP address or a domain. The servers you list need to be capable of recursion to other nameservers.
- **forward-host**: Add the domain for your server. You can choose to either list an IP address or a domain. The servers you list need to be capable of recursion to other nameservers.
- Save and exit the configuration file.
Example Forward Zone Configuration
In the following sample configuration:
- All queries to internal.zscaler.com go the nameserver at 4.2.2.2
- All queries to prod.zpath.net go to the nameserver at fwd.example.com
- All other queries go to the name server at 8.8.4.4
forward-zone:
name: "internal.zscaler.com"
forward-addr: 4.2.2.2
forward-zone:
name: "prod.zpath.net"
forward-host: fwd.example.com
forward-zone:
name: "."
forward-addr: 8.8.4.
[]You need to start Unbound and set it to begin at startup.
To do this:
- Enable Unbound by entering the following commands:
sudo systemctl enable unbound
sudo service unbound start
- Make sure that the Unbound DNS server is running by checking its status. Enter the following command: service unbound status
- Configure DNS resolution on an App Connector by editing /etc/resolv.conf and making sure the line nameserver has a value of 127.0.0.1
- Open a DNS firewall port. This allows your local LAN clients to connect to the Unbound server. To do this, enter the following commands:
firewall-cmd --permanent --add-service dns
firewall-cmd --reload
[]After completing the configuration use tcpdump on the respective interfaces to verify that the correct DNS server is picked up.