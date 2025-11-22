# Configuring Advanced NSS Settings
Source: https://help.zscaler.com/zia/configuring-advanced-nss-settings
PDF: https://help.zscaler.com/pdf/com/en/1399051.pdf

This article describes additional features that facilitate deploying the NSS in cases where you have specific requirements or restrictions. It includes the following topics:
The first three sections listed pertain to the [NSS deployment over VMware vSphere](/zia/nss-deployment-guide-vmware-vsphere) only.
- [Configuring a Second Management Interface](#Management)
- [Configuring a Second Service Interface](#Service)
- [Configuring the Additional Interfaces from the Console](#Additional)
- [Configuring a Local NTP Server](#Local)
- [Configuring NSS in Explicit Proxy Mode](#proxy)
- [Updating an NSS VM Hostname](#update_hostname)
- [Allowing SSH Access to the NSS Only from a Specific Subnet or IP](#allowing)
- [Setting Up Key-Based Authentication to the NSS](#key_based_auth)
[]Sometimes, the default management interface can't be used for SSH due to VLAN restrictions. In those cases, Zscaler recommends that you add an additional interface just for management, so the first interface is used only for control connections to the cloud.
There are two ways to add a second management interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- [Alternatively, you can manually configure the second management interface.](#second-management-manual)
[]To manually add a management interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Update the system configuration file `/etc/rc.conf` to configure the interface automatically after each system restart. To do this, run the following command:
sudo vi /etc/rc.conf
- Add the em2 interface to the list of network interfaces. Modify the line that starts with `network_interfaces` and change it to:
network_interfaces="em0 em1 em2 lo0"
- Add a new line at the end of the file:
ifconfig_em2="<subnet-ip-address>"
Ensure that you replace <subnet-ip-address> with the IP address of the subnet. For example:
ifconfig_em2="192.168.1.100/24”
- The default gateway is automatically added via the em0 interface. To add a static route to a different subnet or VLAN for the newly added em2 interface, add the following lines at the end of the file:
static_routes="em2"
route_em2="-net <destination-subnet> <gateway-ip-address>"
Replace <destination-subnet> with the IP address of the destination subnet, and replace <gateway-ip-address>** **with the appropriate gateway IP address. For example:
static_routes="em2"
route_em2="-net 198.51.100.0/24 192.168.1.3"
- Reboot the VM.
- To verify the changes, ping the newly added subnet gateway and run the following command to print the route information:
sudo netstat -rn
[]The NSS typically uses the service interface to download logs from the Nanolog in the Zscaler cloud and send them to the security information and event management (SIEM) system.
Some organizations might need to use one interface to connect to the Zscaler cloud and another interface to connect to the SIEM. For example, an organization might have a SIEM in a management LAN that is not routed to the internet, and it might also have a service LAN that is routed to the internet but not to the management LAN, as shown in the following diagram.
![Diagram of one interface connecting to the Zscaler cloud and another interface connecting to the SIEM. ](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/mgmt_service_lan_siem_nss_diagram.png.png)
If your organization has a similar requirement, you can configure a second service interface. You can then use one interface to connect to the Zscaler cloud to download the logs and a different interface to send the logs to the SIEM located in the management LAN.
There are two ways to add a second service interface:
- Zscaler recommends that you log in to your client and configure the additional interface from the console tab. See [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- [Alternatively, you can manually configure the second service interface.](#second-service-manual)
[]To manually add a second service interface:
- Shut down the NSS and stop the VM.
- Using your client, assign an additional interface to the VM. Map it to an appropriate network or VLAN.
- Reboot the NSS.
- Run the following command and ensure that the em2 interface is active:
ifconfig
- Copy the `sc.conf` file.
cp /sc/conf/sc.conf /sc/conf/sc.conf.old
- Use the vi Editor to edit the `sc.conf` file. Run the following command:
vi /sc/conf/sc.conf
- Add the following lines to the file, replacing the sample values in red per your configuration:
smnet_dev=em2=zs1:192.168.223.41/24
smnet_route=10.0.0.0/8/192.168.223.1
In this example, em2=zs1 is the second service interface and 192.168.223.41/24 is the service IP address with the subnet mask. If your SIEM is in the same subnet, then the second line is not required. If your SIEM is in a different subnet, add `smnet_route` and define values in the second line. For example, to reach 10.0.0.0/8, use gateway 192.168.223.1.
- Save the changes in the file and then restart the NSS by running the following command:
sudo nss restart
- Verify if the NSS is using the second service interface by running the following command:
sudo nss dump-config
[]To configure a second management interface and service interface, first ensure that you run the following** **command to set your network settings:
sudo nss configure
Then, run the following command to specify the IP addresses for the additional interfaces and their corresponding routes:
sudo nss configure split-interface
****![Screenshot of FreeBSD command prompt showing the command sudo nss configure split-interface](/downloads/zia/documentation-knowledgebase/analytics/nss/nss-deployment-guides/nss-advanced-deployment/NSS%20sudo%20route%201.png)
****
During a split-interface configuration, the NSS asks for an `smnet_route`. If your SIEM is in a different network compared to the NSS smnet interface (em3=zs1) subnet, you can enter specific routes for feeds.
See the following example:
[root@NSS /sc/update]# nss configure split-interface
ifconfig_em2 (Internal Management interface IP address with netmask) [1.1.1.1/23]:
route_net:-net 1.1.1.2/12 2.1.1.1 (Options <c:change, d:delete, n:no change>) [n]
Do you wish to add a new route_net? <n:no y:yes> [n]:
smnet_dev=em3 (Internal Service interface IP address with netmask) [10.10.35.20/24]:
Do you wish to add a new smnet_route? <n:no y:yes> [n]: y
Atleast one entry required for smnet_route
smnet_route (Static route for Siem N/w ,e.g (network/subnet/gateway): 172.12.1.0/21/10.10.35.1) []: 1.3.2.1/2/2.2.1.2
Do you wish to add a new smnet_route? <n:no y:yes> [n]: 2.1.2.3/2/43.3.3.2
[]If you have a local NTP Server, you can configure the NSS to synchronize time with that server:
- Run the following as root:
crontab -e
- Add the following command:
PATH=/sbin:/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/usr/games:/sc/update:/home/zsroot/bin:/sc/update
- Add the following command:
*/10 * * * * ntpdate <ntp-server-name>
Replace <ntp-server-name> with your local NTP server's FQDN or IP address.
- Save and exit.
The time synchronization command runs every 10 minutes. You can find logs for the NTP process in `/var/log/cron.`
[]Some customers might have a [no default route environment](/zia/implementing-zscaler-no-default-route-environments). This prevents the NSS from establishing connections to the Zscaler cloud. For this scenario, you can configure the NSS in explicit proxy mode, so that it tunnels all Zscaler cloud-bound connections through a proxy. These include [network connections](https://config.zscaler.com/zscaler.net/nss) and TCP connections from the NSS to the:
- Nanolog (SMSM)
- Zscaler Central Authority (CA) (SMCA)
- Update server (SMCDSS) for software updates
- Kafka server for audit log streaming
Connections from the NSS to the SIEM are not tunneled.
The NSS in explicit proxy mode can tunnel Zscaler cloud-bound connections. Based on your configuration, you can tunnel these connections without the need for internet-facing DNS resolution.
If you configure the `dnsoverproxy` flag to `1`, then the NSS in explicit proxy mode makes a CONNECT request to the following domains and the explicit proxy performs the name resolution:
- msmca.<cloudname> for the connection to the Zscaler CA
- zdistribute.<cloudname> for the connection to the update server
- kproxy.hdeu1.zdataservices.net for the connection to the Kafka server
If you configure the `dnsoverproxy` flag to `0`, then the NSS needs DNS resolution for the connections to the current master CA IP address, update server, and Kafka server.
NTP connections are not tunneled. The NSS needs DNS resolution for the NTP server. To learn more, see [Configuring a Local NTP Server](/zia/configuring-advanced-nss-settings#Local).
To configure the NSS in explicit proxy mode:
- Run the `nss configure` command to configure the two network interfaces.
- Run the `nss configure proxy` command. For example:
[root@NSS /usr/home/zsroot]# nss configure proxy
proxyserver (Proxy Host ) [10.81.153.26]:
proxyport (Proxy Port ) [443]:
dnsoverproxy (DNS over proxy: 0/1 ) []: 1
Successfully configured proxy
To undo this configuration, you can use `remove`:
nss configure proxy remove
-
Run the `sudo nss restart` command to restart the NSS service.
When the NSS starts, it tries to connect to the Zscaler CA or Nanolog using the proxy it configured.
-
Run the `nss troubleshoot netstat` command to verify the proxy (e.g., 10.81.153.26) connections for the Zscaler CA and Nanolog.
[See image.](#nss-explicit-proxy-mode-tcp-connections)
[]![Screenshot of established TCP connections to the Zscaler CA and Nanolog ](/downloads/tech-pubs-drafts/zia-draft-articles/draft-configuring-advanced-nss-settings-doc-51613/zia-nss-explicit-proxy-mode_0.png)
[]
- Log in to your NSS VM.
- Edit the file `/etc/rc.conf` using the vi Editor.
[zsroot@New_Hostname ~/$ vi /etc/rc.conf
- Add the hostname entry to the file.
hostname=<name>
- Run the `reboot` command.
root@New_Hostname:/usr/home/zsroot # reboot
- After the NSS restarts, your new hostname appears.
[]You can restrict SSH access based on IP/Subject using the following configuration in `sshd_config`:
AllowUsers zsroot@10.66.70.*
In this example, SSH is allowed only from the source IP range 10.66.70.0/24. Then, run the following** **command to make the configuration change effective:
service sshd restart
[]
- Create a .ssh directory in the home directory:* *`/home/zsroot/` under the user` root`*.*
- Upload your user public key file to the file `authorized_keys` under the directory `/home/zsroot/.ssh.`
- Adjust the file `/etc/ssh/sshd_config` with the following updates. Make a backup of this file before changing it.
ChallengeResponseAuthentication no
PasswordAuthentication no
These entries are set to `yes` by default. You can set them to `no`** **or comment them out.
- Use the following command to restart the sshd service:
service sshd restart
Replace option `restart` with `stop` and `start` as required.
- Test the new configuration on the client side using SSH (e.g., PuTTY).