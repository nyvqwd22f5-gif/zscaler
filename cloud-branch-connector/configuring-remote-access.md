# Configuring Remote Access
Source: https://help.zscaler.com/cloud-branch-connector/configuring-remote-access
PDF: https://help.zscaler.com/pdf/com/en/1420846.pdf

An admin can request remote access and allow Zscaler Support to log in to their Zscaler Cloud or Branch Connector virtual machine (VM) instance without opening a firewall connection for inbound traffic. This feature is disabled by default. You must explicitly enable it for the duration that you need remote support assistance. To view your firewall requirements, go to the following URL: https://config.zscaler.com/<Zscaler Cloud Name>/cloud-branch-connector.
You can find the <Zscaler Cloud Name> in the URL you use to log in to the Cloud & Branch Connector Admin Portal. For example, if you log in to connector.zscaler.net, then go to https://config.zscaler.com/zscaler.net/cloud-branch-connector. To learn more, see [What Is My Cloud Name for Zscaler Cloud & Branch Connector?](/cloud-branch-connector/what-my-cloud-name-zscaler-cloud-branch-connector)
Ensure that you include `sudo` in every command that you run.
-
To enable Zscaler Support to access your Cloud or Branch Connector instance:
sudo zssupport tunnel start
This command creates a long-lived SSH tunnel to the Zscaler cloud and sets up remote port forwarding, which allows Zscaler Support to log in to your Cloud or Branch Connector instance. To run this command, allow outbound SSH traffic on port 12002 because the support servers monitor through this port.
-
To disable Zscaler Support access to your Cloud or Branch Connector instance:
sudo zssupport tunnel stop
This command brings down the long-lived SSH tunnel to the Zscaler cloud and all the remote connections.
-
To check the status of the Zscaler Support access to your Cloud or Branch Connector instance:
sudo zssupport tunnel status
This command checks the status of the long-lived SSH tunnel to the Zscaler cloud, which Zscaler Support uses to log in to your Cloud or Branch Connector instance.
If you are using Amazon Web Service (AWS) Session Manager (SSM), export the path environment variable and then run the command:
-
To start the tunnel:
`export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin:/home/zsroot/bin
sudo zssupport tunnel start`
-
To stop the tunnel:
`export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin:/home/zsroot/bin
sudo zssupport tunnel stop`
-
To check the status of the tunnel:
`export PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/sbin:/usr/local/bin:/home/zsroot/bin
sudo zssupport tunnel status`
If the support tunnel enablement fails, attach the logs at `/var/log/zscaler/ecsupport/ecsupport.log` for debugging.