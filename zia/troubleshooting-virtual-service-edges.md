# Troubleshooting Virtual Service Edges
Source: https://help.zscaler.com/zia/troubleshooting-virtual-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1401261.pdf

You can use the following commands within the virtual machine (VM) console to configure and troubleshoot Virtual Service Edges. By default, root login is not permitted, so admins must use the sudo utility to run a command with higher privileges.
- To start the Virtual Service Edge service, use the following command:
sudo vzen start
This command displays the process identifier (PID) for the services it started.
- To start the Virtual Service Edge instance, use the following command:
sudo vzen start sme
This command displays the PID for the SME instance it started.
- To start the load balancer service, use the following command:
sudo vzen start smlb
This command displays the PID only for the LB cluster.
- To stop the Virtual Service Edge service, use the following command:
sudo vzen stop
- To restart the Virtual Service Edge service, use the following command:
sudo vzen restart
This command stops the service and then starts the service again. It also displays the PID for the services it started.
- To shut down the operating system, use the following command:
sudo vzen halt
- To view the configured values of the Virtual Service Edge, use the following command:
sudo vzen dump-config
This command displays the following configured values of the Virtual Service Edge:
- `CloudName`: Name of the cloud in which the Virtual Service Edge is configured.
- `nameserver`: The primary DNS IP configured for the Virtual Service Edge.
- `Mgmt IP`: The management IP configured for the Virtual Service Edge.
- `Default gateway for Mgmt IP`: The default gateway configured for the management IP.
- `Service IP`: The service IP configured for the Virtual Service Edge.
- `Default gateway for Service IP`: The default gateway configured for the service IP.
- To start the Virtual Service Edge service automatically after a reboot, use the following command:
sudo vzen enable-autostart
- To disable the automatic start of the Virtual Service Edge service after a reboot, use the following command:
sudo vzen disable-autostart
- To remove a previous installation of the Virtual Service Edge service, use the following command:
sudo cd /home/zsroot
sudo vzen stop
sudo vzen cleanup
- To view the software version of the Virtual Service Edge instance, use the following command:
sudo /sc/sme/bin/sme -V
- To check the latest available software version of the Virtual Service Edge, use the following command:
sudo vzen checkversion
This command displays the update server's IP address, the currently installed software version, and the latest available software version of the Virtual Service Edge.
- To check the Virtual Service Edge status, use the following command:
sudo vzen status
This command displays the following status for the respective services:
- Either running or stopped with its PID for SME.
- Either running or stopped with its PID for CDSC.
- Either running or stopped with its PID for an LB cluster and not installed for a standalone LB.
- To check the Virtual Service Edge cluster configuration and status, use the following command:
sudo /sc/smlb/bin/smmgr -ys show=smlbclusters
[Sample output of this command.](#VZEN-clusterconfig)
- To generate Virtual Service Edge diagnostic information, use the following command:
sudo vzen collect-diagnostics
This command collects the configuration, vital statistics regarding the health of the Virtual Service Edge instance, and error statistics. It then downloads the data to a local file (.tgz) in the /sc/sme/log/ folder. If you uncompress the .tgz file, the following data files are available:
- scripts.version
- unixcommands
- vzen.upgrade.log
- vzensmesmmgr.log
- vzensmlbsmmgr.log
Email the .tgz file to Zscaler Support for troubleshooting purposes.
- To check the firewall configuration, use the following command:
sudo vzen test-firewall
This command probes active firewall configuration by attempting to resolve the DNS names and establishing outbound connections to the Zscaler cloud.
Ensure to run this command on the ESXi console to avoid SSH connection disruption.
- To change the network configuration (i.e., IP addresses and gateway information) for the service, use the following command:
sudo vzen configure-network
- To show the active connections on the service IP address, use the following command:
sudo vzen troubleshoot netstat
The output is similar to that of the netstat utility.
- To show the ports on which the Zscaler services listen, use the following command:
sudo vzen troubleshoot netstat listen
[Sample output of this command.](#netstat-listen)
- To show the connections and their statuses, use the following command:
sudo vzen troubleshoot connection
This command probes the connection for some time and displays one of the following connection statuses for cloud-config, log-stream, SMBA (if configured), and LB Status:
- `Stable`: Indicates that the connections are stable.
- `Suspicious`: Indicates that there was at least one disconnection to the Zscaler CA in the last two hours. To troubleshoot the disconnection to the CA, contact Zscaler Support.
- `Not present`: Indicates that there is no connectivity.
[Sample output of this command.](#VZEN-troubleshoot-connection)
- To check the status of the Virtual Service Edge connectivity to Zscaler CA, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys show=auth
[Sample output of this command.](#CA-connectivity)
- To check the TCP connectivity to the destination server or establish a connection to a website, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys host=<Domain Name> -ys port=80 -ys waittime=15 -ys connect=tcp
[Sample output of this command.](#tcp-connectivity)
The following error messages appear for the respective scenario:
- Failed to resolve <Domain Name> if the domain name is invalid.
- Connection timed out to <Domain Name>(Resolution):<Port> if the TCP connection is not established.
- To ping a public IP address, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys smnet='ping <IP address or Domain Name>'
- To check the Virtual Service Edge interface status, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys smnet=ifconfig
- To view the route table of the Virtual Service Edge, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys smnet='route'
[Sample output of this command.](#route-table)
- To view the ARP table of the Virtual Service Edge, use the following command:
sudo ZSINSTANCE=/sc/sme/ /sc/sme/bin/smmgr -ys smnet="arp"
[Sample output of this command.](#ARP-table)
- To show all the interfaces in the VM, use the following command:
ifconfig
[Sample output of this command.](#Sample-output-ifconfig)
- To show all the SME service interfaces in the VM, use the following command:
sudo /sc/sme/bin/smmgr -s smnet=ifconfig
[Sample output of this command.](#smnet-ifconfig-command)
Enabling Remote Access
An admin can request remote assistance and allow Zscaler Support to log in to their Virtual Service Edge instance without opening a firewall connection for inbound traffic. This feature is disabled by default and must be enabled explicitly for the duration that remote support assistance is required. You can enable this feature from the ZIA Admin Portal. To learn more, see [Adding Virtual Service Edge Instances](/zia/adding-virtual-service-edge-instances#zs-support-tunnel).
Logs required for troubleshooting
Share the following logs with the Zscaler Support for troubleshooting issues:
- zscaler.log in the /sc/sme/log/ and /sc/smlb/log/ folders.
- autoupgrade.log in the /sc/update/log/ folder.
[]![Screenshot of the VZEN cluster configuration and status sample.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-Cluster-Confinguration.png)
[]![Screenshot of the VZEN troubleshoot connection output and its status sample.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-troubleshoot-connection.png)
[]![Screenshot of sample output of the VZEN troubleshoot netstat listen command.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-troubleshoot-netstat-listen.png)
[]![Screenshot of sample output of the TCP connectivity to the destination server command.](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-TCP-connectivity.png)
[]![Screenshot of sample Route Table](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-route%20table.png)
[]![Screenshot of sample ARP Table](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-ARP%20table.png)
[]![Sample output of Virtual Service Edge or VZEN connectivity to CA](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/troubleshooting-virtual-zens/ZIA-VZEN-CA-Connectivity.png)
[]![Sample output for command to show interfaces in the VM](/downloads/zia/traffic-forwarding/service-edges/troubleshooting-virtual-service-edges/sample-output-ifconfig.png)
[]![Sample output for the command to show sme service interfaces in the VM](/downloads/zia/traffic-forwarding/service-edges/troubleshooting-virtual-service-edges/sample-output-smnet%3Difconfig.png)