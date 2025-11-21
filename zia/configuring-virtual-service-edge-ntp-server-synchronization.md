# Configuring Virtual Service Edge and NTP Server Synchronization
Source: https://help.zscaler.com/zia/configuring-virtual-service-edge-ntp-server-synchronization
PDF: https://help.zscaler.com/pdf/com/en/1401161.pdf

ZIA [Virtual Service Edges](/zia/about-virtual-service-edges) are extremely sensitive to the VM and cloud times being in sync. By default, the VM synchronizes the time with public NTP servers (e.g. `pool.ntp.org`). However, if you have a local NTP server, you can configure the Virtual Service Edge to synchronize time with it.
Custom Configuration of NTP Servers Using CLI
To custom configure NTP servers using CLI:
- Use SSH to connect to the management IP address.
- Run the following command:
sudo vzen enable-ntpd
This command prompts you to enter the custom NTP servers. After adding the NTP servers, you are prompted to start NTPD immediately.
The Virtual Service Edge and NTP service are restarted in this process. Ensure that your organization is prepared for the services to shut down momentarily before restarting.
[Sample output of this command.](#enable-ntpd)
You can remove the configured NTP servers using the `vzen disable-ntpd `command.
Synchronizing Times
You can synchronize times using one of the following methods:
- [Create a Cron Job](#cron-job)
- [Edit the /etc/hosts File](#hosts-file)
Adding alternate NTP servers to the `/etc/ntp.conf` file is not supported. However, you can modify the `/etc/hosts` file as described in the [Edit the /etc/hosts File](/zia/configuring-virtual-service-edge-ntp-server-synchronization#hosts-file) section.
[]To create a cron job to synchronize the time from the configured local NTP servers:
- Run the following as root: `crontab -e`
- Add the following line: `*/10 * * * * ntpdate` `<ntp-server-name>`
Replace <ntp-server-name> with your local NTP server's FQDN or IP address.
- Save and exit.
This time synchronization command will run every 10 minutes.
[]To make pool.ntp.org hostnames resolve to your local NTP server IP address by manipulating the /etc/hosts file:
- Open the `/etc/hosts` file.
- Add up to 4 NTP servers by adding the following lines:
- `<ntp-server-IP-address1>`` 0.pool.ntp.org`
- `<ntp-server-IP-address2>`` 1.pool.ntp.org`
- `<ntp-server-IP-address3>`` 2.pool.ntp.org`
- `<ntp-server-IP-address4>`` 3.pool.ntp.org`
- Save your changes.
[]![Screenshot of the Sample Output of VZEN Enable NTPD](/downloads/zia/documentation-knowledgebase/traffic-forwarding/zscaler-enforcement-nodes/virtual-service-edge/configuring-virtual-service-edge-google-cloud-platform/GCP-Sample-Output-VZEN-Enable-NTPD.png)