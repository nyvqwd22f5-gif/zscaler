# Troubleshooting Deployed NSS Servers
Source: https://help.zscaler.com/zia/troubleshooting-deployed-nss-servers
PDF: https://help.zscaler.us/pdf/com/en/1399031.pdf

You can use the following commands within the virtual machine (VM) console for your platform to configure and troubleshoot the NSS server. By default, root login is not permitted, so admins must use the `sudo` utility to run a command with higher privileges.
- To start the service:
sudo nss start
- To stop the service:
sudo nss stop
- To restart the service:
sudo nss restart
- To smoothly shut down the operating system:
sudo nss halt
- To change the network configuration (i.e., IP addresses, gateway information) for the service:
sudo nss configure
To learn more, see the [NSS deployment guide](/zia/deploying-nss-virtual-appliances) for your platform.
- To configure additional interfaces:
sudo nss configure split-interface
To learn more, see [Configuring the Additional Interfaces from the Console](/zia/nss-advanced-deployment#Additional).
- To configure an explicit proxy:
sudo nss configure proxy
To learn more, see [Configuring NSS in Explicit Proxy Mode](/zia/nss-advanced-deployment#proxy).
- If you configured additional interfaces using the `sudo nss configure split-interface` command and want to remove the configuration:
sudo nss configure split-interface --wipe
- To remove the network settings that were configured using the `sudo nss configure` command:
sudo nss configure --wipe
- To display the configuration file that was changed using the `sudo nss configure` command:
sudo nss dump-config
- To install NSS certificates from a specified certificate bundle file:
sudo nss install-cert <certificate bundle file>
- To check if a new NSS version is available:
sudo nss checkversion
- To manually update the NSS to the latest version:
sudo nss update-now
- To force the NSS to update, regardless of whether a new version is available:
sudo nss force-update-now
- To check the firewall configuration:
sudo nss test-firewall
This command does active firewall configuration probing by attempting to resolve the DNS names and establishing outbound connections to the Zscaler cloud. This command doesn't reset the management IP interface, so you can run it on an SSH connection.
- To view troubleshooting help command information:
sudo nss troubleshoot help
- To show the active connections on the service IP address:
sudo nss troubleshoot netstat
The output is similar to that of the netstat utility.
- To show the connections and their status:
sudo nss troubleshoot connection
This command probes the connection status over a period of time and indicates whether the connections are stable or flapping.
- To show the status of the NSS feeds:
sudo nss troubleshoot feeds
This command probes the status of the feeds and determines if the logs are queued due to the slow consumption of logs by the security information and event management (SIEM) system.
- To generate diagnostic information to send to Zscaler Support:
sudo nss collect-diagnostics
This command collects the configuration, vital statistics regarding the health of the NSS, and error statistics, and then downloads the data to a local file. This file can be emailed to Zscaler Support for troubleshooting purposes.
- To reset the network configuration:
sudo nss reset-network
- To change the SNMP admin user configuration:
sudo nss snmp-admin-configure
- To change the SNMP trap configuration:
sudo nss snmp-trap-configure
- To automatically start the NSS after reboot:
sudo nss enable-autostart
- To disable the automatic start of the NSS after reboot:
sudo nss disable-autostart
- To set up and enable MCAS:
sudo nss configure-mcas2
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. To learn more, see [Integrating with Microsoft Cloud App Security](/zia/integrating-microsoft-cloud-app-security).
- To disable MCAS:
sudo nss disable-mcas
You must restart the NSS using the `sudo nss restart` command for the changes to take effect. You can re-enable MCAS by re-issuing the `sudo nss configure-mcas2` command.
Enabling Remote Access
An admin can request remote assistance and allow Zscaler Support to log in to their NSS server without having to open a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required.
- To enable Zscaler Support to access your NSS server:
sudo nss support-access-start
This creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding. Zscaler Support can then use this tunnel to log in to your NSS server.
- To disable Zscaler Support access to your NSS server:
sudo nss support-access-stop
This brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
- To check the status of the Zscaler Support access to your NSS server:
sudo nss support-access-status
This checks the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your NSS server.
- To enable a remote debugging session:
sudo nss enable-remote-debugging
- To disable a remote debugging session:
sudo nss disable-remote-debugging
Error Codes
The following are error codes that you might encounter when executing an `sudo nss update-now` command:
| Error Code | Description |
| ---------- | ----------- |
| Error Code 96 | Invalid client certificate |
| Error Code 97 | Timeout occurred while contacting upgrade server |
| Error Code 99 | A problem occurred while downloading and installing the latest version. The `sudo force-update-now` command needs to be explicitly issued. |
Use Case
You can use the following commands to check the DNS resolution issues on the service interface and routes to the surface interface.
- To check the reachability of a server IP address using ICMP:
/sc/bin/smmgr -ys smnet='ping <IP address or Domain Name>'
- To print the server interface IP config details:
/sc/bin/smmgr -ys smnet=ifconfig
- To check the DNS resolution of a hostname:
/sc/bin/smmgr -ys smnet='route'/sc/bin/smmgr -ys host="<Domain Name>" -ys connect=dns
- To check the communication or port reachability of a server:
/sc/bin/smmgr -ys host="<FQDN of SIEM server>" -ys port=<Listening port> -ys connect=tcp
What happens if the NSS goes down?
In the event of a connection loss between the NSS server and the cloud [Nanolog](/zia/about-zscaler-cloud-architecture), the cloud retransmits the logs to the NSS up to a maximum of one hour. If the NSS is down for more than an hour, the logs falling out of the one-hour window aren't retrieved by the NSS.