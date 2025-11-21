# Troubleshooting App Connectors
Source: https://help.zscaler.com/zpa/troubleshooting-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1484651.pdf

This article provides troubleshooting information and guidelines about App Connectors. To learn more about App Connectors, see [About App Connectors](/zpa/about-connectors). To configure App Connectors, see [Configuring App Connectors](/zpa/configuring-connectors).
When troubleshooting App Connectors, consider the following:
- [App Connector Not Connected to the Cloud](#notconnectedcloud)
- [App Connector Not Communicating with the Cloud](#nocommunicationcloud)
- [DNS Failure, But App Connector Successful](#dnsfailure)
- [Server Domain Resolution Change Does Not Take Effect Immediately](#serverdnsnotimmediate)
- [SSL Interceptions](#sslinterceptions)
- [Memory Leaks or High Memory Usage](#memory)
- [High CPU](#cpu)
- [Unable to Connect to the ZPA Cloud](#cloudconnect)
- [App Connector ID Is Zero](#idzero)
- [Larger Number of TCP Sockets in the System](#tcpsockets)
- [Too Many TCP Failures to the Server](#tcpfailures)
- [Frequent Disconnections to the ZPA Cloud](#frequentclouddisconnect)
- [App Connector Load Not Balanced](#loadbalance)
- [App Connector Pause State](#pauseState)
- [App Connector Upgrade Failure](#upgradefailure)
- [Enrollment Failure](#enrollmentfailure)
- [Have Less Than 100 Active App Connectors, But Can’t Enroll More](#amtconnectors)
- [IMDSv2 Migrated App Connector Fails to Enroll to ZPA](#imdsv2)
- [Certificate Is Not Valid Yet](#certvalidity)
- [Disaster Recovery Configuration and Binary Snapshot Not Captured](#disasterRecovery)
- [Disaster Recovery Debugging](#debuggingDr)
[]If the App Connector was previously working and now shows an error about not being connected to the cloud, you might see an error similar to the following:
Apr 02 08:03:21 zpa-connector zpa-connector-child[1737]: [1;39mReceived event from [13.170.52.111]:38864;broker2.sha1.prod.zpath.net:[56.109.210.189]:2010: BEV_EVENT_CONNECTED, sock=63 using ECDHE-RSA-AES128-GCM-SHA256[0m
Apr 02 08:03:22 zpa-connector zpa-connector-child[1737]: [1;39mReceived event from [13.170.52.111]:38864;broker2.sha1.prod.zpath.net:[56.109.210.189]:2010: BEV_EVENT_READING BEV_EVENT_ERROR, sock=63[0m
Apr 02 08:03:22 zpa-connector zpa-connector-child[1737]: [1;39m*Connector not yet connected to cloud, please check connectivity, if this persists*[0m
The App Connector logs are automatically stored in the `/var/log/messages` file. To learn more about viewing log files for the App Connector, see [Managing Deployed App Connectors](/zpa/managing-deployed-connectors#Monitoring).
This error often occurs when an App Connector is deleted from the ZPA Admin Portal accidently. ZPA immediately recognizes that it should not communicate with the App Connector, and it breaks the active connection. There is no way to recover the App Connector.
To resolve this issue:
- Remove the App Connector on the deployed platform.
- Log in to the App Connector console using your admin credentials.
-
Enter the following command to stop the zpa-connector service:
[admin@zpa-connector ~]$ sudo systemctl stop zpa-connector
- Enter the following command to switch to a root user:
[admin@zpa-connector ~]$ sudo su
- Enter the following command to delete the App Connector:
[root@zpa-connector ~]$ rm -rf /opt/zscaler/var/*
- Enter the following command to switch back to a regular user:
[root@zpa-connector admin]# exit
-
Restart services:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
If you attempt to delete the App Connector and the App Connector still reports an ID number, then the App Connector is not fully deleted.
- Restart the process of [configuring](/zpa/configuring-connectors) an App Connector and [deploying](/zpa/about-deploying-connectors) on a platform.
[]If an App Connector successfully logged a connection but the App Connector shows as disconnected in the ZPA Admin Portal, there is most likely an issue with the connector process not getting CPU cycles on the virtual machine (VM) or the VM is frozen.
To resolve this issue, try stopping the VM and restarting it again. Sometimes, the issue resolves on its own.
[]If you have a DNS failure and the ZPA App Connector “root” process is successful, you might see an error similar to the following:
The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: Checking Enrollment
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: Resolve read certificatefailed
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: No valid certificate. Attempting to enroll
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: Enroll: Connecting to api.private.zscaler.com via co2br.prod.zpath.net.
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: DNS resolution failed for api.private.zscaler.com
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: Could not create HTTP client
May 25 14:32:53 ussy-nwopapp03 zpa-connector-child[2040]: Certificate enrollment failed.
May 25 14:32:55 ussy-nwopapp03 zpa-connector[3971]: zscaler-update: zpa-connector-child exited too fast, was running for 2 seconds
May 25 14:32:55 ussy-nwopapp03 zpa-connector[3971]: zscaler-update: zpa-connector-child failed too many times in a row- reverting to default software
The DNS failure may be an issue with the permissions for the user account “zscaler”. Typically, this means the “root” process is able to read `/etc/resolv.conf`, but the “zscaler” user account cannot.
To resolve this issue, correct the file permission on `/etc/resolv.conf` for the “zscaler” user account to allow it read access.
[]When DNS resolution changes on the health-monitored application server domain, it takes a few minutes for the change to take effect. During this time, you can expect to still see traffic still being routed to the old server IP address. This is because the App Connector has a little tolerance on DNS resolution to handle DNS flapping. To reduce this delay, you can change the application segment's **Health Reporting** option to **None**. For more information, see [About Applications](/zpa/about-applications).
[]If you have an error similar to the following, a device between the App Connector and ZPA cloud service is attempting an SSL interception:
Jul 10 13:58:18 zpa-connector zpa-connector-child[992]: Received event from [uninitialized]:0;co2br.prod.zpath.net:[52.28.10.14]:443: BEV_EVENT_READING BEV_EVENT_ERROR, sock=54 self signed certificate in certificate chain /C=US/ST=California/L=San Jose/O=Safemarch/OU=Certificate Authority/CN=Safemarch Inc CA/emailAddress=support@safemarch.com /C=US/ST=California/L=San Jose/O=Safemarch/OU=Certificate Authority/CN=Safemarch Inc CA/emailAddress=support@safemarch.com
ZPA does not support SSL interceptions. ZPA uses TLS connections and pinned certificates, so a device performing SSL interception causes the connection to fail between the App Connector and the Zscaler cloud.
To make sure traffic is not SSL intercepted, you need to allowlist all the ZPA domains or IP addresses in the SSL interception device that are listed on [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa) This ensures that App Connectors and the Zscaler URLs (e.g., *.zpath.net, *.zscaler.com) are bypassed from an SSL inspection.
[]You should routinely monitor and address memory leaks or high memory usage in your App Connectors. For more information, see [Monitoring App Connector Performance](/zpa/monitoring-connector-performance).
If there is a need to contact Zscaler Support, be prepared to run the following script. It collects a memory report every minute. This might need to run for at least one hour or up to multiple days.
Script:
#!/bin/bash
# trap ctrl-c and call ctrl_c()
trap ctrl_c INT
function ctrl_c() {
echo "** Trapped CTRL-C"
exit
}
echo "dumping memory report at $(date)"
uname -a >> memory_report.txt
hostname >> memory_report.txt
lscpu >> memory_report.txt
while :
do
echo "dumping memory report at $(date)"
date >> memory_report.txt
echo "ps aux --sort=-pmem | head -5" >> memory_report.txt
ps aux --sort=-pmem | head -5 >> memory_report.txt
echo "curl -s 127.0.0.1:9000/memory/status" >> memory_report.txt
curl -s 127.0.0.1:9000/memory/status >> memory_report.txt
echo "curl -s 127.0.0.1:9000/memory/argo" >> memory_report.txt
curl -s 127.0.0.1:9000/memory/argo >> memory_report.txt
sleep 60
done
[]You should routinely monitor and address high CPU for your App Connectors. For more information, see [Monitoring App Connector Performance](/zpa/monitoring-connector-performance).
If there is a need to contact Zscaler Support, be prepared to run the following script. It collects a CPU report. This might need to run for at least one hour or up to multiple days.
Script:
#!/bin/bash
# trap ctrl-c and call ctrl_c()
trap ctrl_c INT
function ctrl_c() {
echo "** Trapped CTRL-C"
exit
}
echo "dumping cpu report at $(date)"
uname -a >> cpu_report.txt
hostname >> cpu_report.txt
lscpu >> cpu_report.txt
while :
do
echo "dumping cpu report at $(date)"
date >> cpu_report.txt
echo "ps aux --sort=-pcpu | head -5" >> cpu_report.txt
ps aux --sort=-pcpu | head -5 >> cpu_report.txt
echo "vmstat" >> cpu_report.txt
vmstat >> cpu_report.txt
echo "curl -s 127.0.0.1:9000/memory/status" >> cpu_report.txt
curl -s 127.0.0.1:9000/memory/status >> cpu_report.txt
echo "curl -s 127.0.0.1:9000/memory/argo" >> cpu_report.txt
curl -s 127.0.0.1:9000/memory/argo >> cpu_report.txt
sleep 60
done
[]If you have issues with the App Connector connecting to the ZPA cloud, there are a few things to check when narrowing down what is preventing the App Connector connection:
- [Check the IP address ranges.](#cloudconnect_iprange)
- [Test the connectivity.](#cloudconnect_connectivity)
- [Check for a TLS connection.](#cloudconnect_tlsconnection)
- [Get the tcpdump.](#cloudconnect_tcpdump)
- [Verify the frequency of error occurrence.](#cloudconnect_errorfreq)
- [Do an ICMP ping.](#cloudconnect_icmpping)
[]Make sure all the IP address ranges allowed by the firewall match those in the ZPA firewall policies: [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
[]Test connectivity to the upstream ZPA Public Service Edge by querying the DNS address `co2br.prod.zpath.net` from the server that is running the App Connector software.
co2br is an endpoint for App Connectors to locate Public Service Edges.
Successful connectivity results in two IP addresses. For example:
[admin@localhost ~]$ dig +short co2br.prod.zpath.net
13.60.119.37
42.68.244.163
[admin@localhost ~]$
If you do not get two IP addresses, there is a DNS lookup issue that you need to investigate further.
[]Test if the App Connector can make a TLS connection to a ZPA Public Service Edge using the `openssl` command.
A successful TLS connection results in a certificate subject string returned from the ZPA Public Service Edge.
For example:
[admin@localhost ~]$ openssl s_client -servername mockcompany.com.server1.net -connect 13.60.119.37:443 2>&1 | grep subject
subject=/C=US/ST=California/L=San Jose/O=Zscaler/OU=Emerging Technologies/CN=broker1a.sjc8.prod.zpath.net
[admin@localhost ~]$
If the `openssl` command shows an error, then there is a problem with your network. You can try running the openssl command in a loop to see if there is a regular pattern to the success/failure rate. For example, the firewall rule might not allow the App Connector to open a connection to a ZPA Public Service Edge. Sometimes TCP goes through, but TLS fails. This is a sign that the firewall is blocking the application layer, but it’s allowing the transport layer.
[]Get the tcpdump and see the delay between the packet sent and the TCP RST received. If the delay is too short (e.g., 1 or 2 milliseconds), then most likely the firewall in your organization's premise is sending the RST.
[]This error sometimes occurs intermittently, which indicates a networking issue either in your organization’s environment or in the internet path from the App Connector to ZPA Public Service Edge. In those cases, do the following:
- Watch for messages similar to those in the example.
- Check the output of `journalctl -n10000 zpa-connector | grep fohh_connection_connected`. These messages are printed every minute and tell you if the connection is always connected.
- Review the `rx` and `tx` counters in the messages, which tell you how many bytes were transferred in this channel. Based on the state and the bytes counters, you can also see if the connection is inconsistent.
For example:
* FC f_conn [10.204.5.5]:41236;broker1b.was2.prod.zpath.net:[52.4.154.137]:443:fohh_connection_connected, rx = 195538, peer_tx = 195538, tx = 855420, tx_drop = 0, tx_limit = 34409852, tx_limit_update = 1559057907248724, r_rx = 855420, r_tx_limit = 33749970, tx_wnd_update = 1559057907248724, rx_wnd_update = 1559057881252092, tx_blocked = 0, enq = 855420, deq = 855420
* FC f_conn [10.204.5.5]:41236;broker1b.was2.prod.zpath.net:[52.4.154.137]:443:fohh_connection_backoff, rx = 0, peer_tx = 0, tx = 0, tx_drop = 0, tx_limit = 33554432, tx_limit_update = 1559057922248143, r_rx = 0, r_tx_limit = 33554432, tx_wnd_update = 0, rx_wnd_update = 0, tx_blocked = 0, enq = 0, deq = 0
[]Send an ICMP ping to the ZPA Public Service Edge.
[]You might see the App Connector ID as zero, if you are reviewing:
- The [diagnostic information](/zpa/about-connector-diagnostics) about App Connectors in the ZPA Admin Portal
- The App Connectors’ log information in either the [Live Logs](/zpa/about-live-logs) on the ZPA Admin Portal or through the [Log Streaming Service](/zpa/about-log-streaming-service)
If the Central Authority cannot determine an application or resolve the connection to the App Connector for the user, it displays the App Connector ID as zero. This can occur for the following ZPA session status codes:
- APP_NOT_REACHABLE.
- INVALID_DOMAIN
- NO_CONNECTOR_AVAILABLE
To learn more, see [Understanding ZPA Session Status Codes](/zpa/understanding-zpa-session-status-codes).
[]This is expected behavior. Each application requires a TCP port and has its health monitored. Many of these ports can reside in a TIME_WAIT state. To learn more, see [Monitoring App Connector Performance](/zpa/monitoring-connector-performance).
[]These TCP failures are normal and are mostly due to the App Connector doing health monitoring of the application server. You can see a lot of TCP 3-way handshakes and/or RST packets if you get a pcap from the App Connector facing the application server.
[]If you see frequent disconnections between an App Connector to the ZPA cloud, the problem might come from a couple of areas.
Questions to address:
- Is there an App Connector restart involved?
- Is the disconnect only on the control or data connection?
- Is there a pattern emerging out of the disconnection in data and control connection?
- Could there be a routing issue? Is only a specific set of ZPA Public Service Edge IP addresses (with common prefix) having the problem?
- Could the firewall have an out-of-memory state? If so, could the firewall do a TCP RST of the existing connection to claim more memory?
To find the ZPA Public Service Edge’s name and begin resolving the issue:
- Go to **Analytics **> **Diagnostics**. For more information, see [About App Connector Status Diagnostics](/zpa/about-connector-diagnostics).
- Under **Log Type**, choose **App Connector Status**.
- Apply the **Disconnected** status filter:
- Click **Add Filters** and select the **Connection: Status Code** filter from the drop-down menu.
- Select the **Equals** Boolean operator from the drop-down menu.
- Select the **Disconnected** status.
- Click **Apply**.
- Check the times in the **Disconnect Time** column to identify the correct App Connector.
- Find the name in the **Service Edge** column to identify the ZPA Public Service Edge name or ZPA Private Service Edge.
- Repeat steps 4 and 5 if there are multiple times for the disconnection.
[]Sometimes the load (i.e., the interface stats) is not equally split between the App Connectors in the App Connector group. ZPA maintains App Connector affinity for an active user for 30 minutes following the user’s last application request. This means that once an App Connector is selected for a user, all application requests for that user go through this App Connector.
You can check the [Health Dashboard](/zpa/about-health-dashboard) to help you address your questions about App Connector load balance and to see the application split between App Connectors in a given period of time.
[]An App Connector can be in a paused state for one of the following reasons:
- `#define PAUSE_REASON_CERT_EXPIRY`: Certificate expiry
- `#define PAUSE_REASON_UPGRADE`: Software upgrade
- `#define PAUSE_REASON_ADMIN_PROBE_PROCESS_RESTART`: Session process restart
- `#define PAUSE_REASON_ADMIN_PROBE_SYSTEM_RESTART`: Session system restart
An App Connector provides the following log when it enters the pause state:
ASSISTANT_LOG(AL_INFO, "Connector(ID = %"PRId64") (Name = %s) entering PAUSE mode because of - %s", global_assistant.gid, assistant_state_get_configured_name(), assistant_state_get_pause_reason());
Check the journalctl logs for the reason the App Connector is in a pause state using the following command:
sudo journalctl | grep "entering PAUSE mode because of"
For [remote troubleshooting](/zpa/accessing-and-viewing-support-information#Status), App Connectors might reject additional session commands when they are currently in a paused state. The following command is returned in the App Connector console when they are currently in a paused state and reject a session command:
ADMIN_PROBE_LOG(AL_NOTICE, "entity is currently in paused mode, not taking any probe commands");
[]There are different possible reasons for App Connector upgrade failures:
- [Upgrade is in a failed state for more than 24 hours.](#upgradefailure_24hours)
- [Image cannot download since there is no disk space left.](#upgradefailure_nodiskspace)
- [Image cannot download due to inconsistent connection between the App Connector and co2br (App Connector to Public Service Edge endpoint).](#upgradefailure_inconsistentconnection)
- [The provisioning key was deleted in the ZPA Admin Portal.](#upgradefailure_provisioningkey)
If none of the above reasons are causing the upgrade failures, complete the following steps to try and resolve the upgrade failure:
- Restart the App Connector. To learn more, see [Start, Stop, or Restart an App Connector](/zpa/managing-deployed-connectors#Starting).
- Stop the App Connector.
-
Verify that no processes are running.
[admin@localhost ~]$ sudo ps wU zscaler
PID TTY      STAT   TIME COMMAND
[admin@localhost ~]$
- Start the App Connector.
- Return to the [App Connectors page](/zpa/about-connectors#AboutConnectorsPage) to see if the **Update Status** changes from **Failure **to **Success**. If the status still says Failure, proceed to the next step.
- Check the logs and network connectivity by addressing any issues if identified.
- Test connectivity to the upstream ZPA Public Service Edge by querying the DNS address `co2br.prod.zpath.net` from the server that is running the App Connector software.
co2br is an endpoint for App Connectors to locate Public Service Edges.
Successful connectivity results in two IP addresses. For example:
[admin@localhost ~]$ dig +short co2br.prod.zpath.net
13.60.119.37
42.68.244.163
[admin@localhost ~]$
-
Check if the App Connector can start a TLS connection using the openssl command. You should receive a certificate subject string returned from the ZPA Public Service Edges. For example:
[admin@localhost ~]$ openssl s_client -servername mockcompany.com.server1.net -connect 13.60.119.37:443 2>&1 | grep subject
subject=/C=US/ST=California/L=San Jose/O=Zscaler/OU=Emerging Technologies/CN=broker1a.sjc8.prod.zpath.net
[admin@localhost ~]$
If you receive a certificate subject, proceed to the next step.
If you do not receive a subject string, there is likely an error with TLS communication. Review the ZPA firewall policies and make any adjustments as needed: [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
- Revert to the default App Connector version.
- Stop the App Connector. To learn more, see [Start, Stop, or Restart an App Connector](/zpa/managing-deployed-connectors#Starting).
-
Remove the App Connector binary image, the version identifier file, and the image metadata file.
[admin@zpa-connector ~]$ sudo rm /opt/zscaler/var/image.bin
[admin@zpa-connector ~]$ sudo rm /opt/zscaler/var/version
[admin@zpa-connector ~]$ sudo rm /opt/zscaler/var/metadata
- Start the App Connector. The App Connector reaches out to the Zscaler cloud and re-download the default App Connector software version. The App Connector attempts to upgrade at a later time.
-
Check the following logs to verify the software version downloaded:
[admin@zpa-connector ~]$ sudo journalctl -u zpa-connector -f
If the software downloads, return to the [App Connector page](/zpa/about-connectors#AboutConnectorsPage) to see if the Update Status changes from **Failure** to **Scheduled**.
If the software did not download or the App Connector still does not update, proceed to the next step.
- Wipe and rebuild the App Connector configuration.
Before wiping and rebuilding the App Connector, you need to:
- Identify the App Connector group for the App Connector.
- Identify the provisioning key of the App Connector group.
- On the App Connector Provisioning Keys page, verify that the number of provisioning keys in the **# of Enrolled Connectors** column is less than the number in the **Maximum # of Connectors** column for the provisioning key.
If needed, you can raise the maximum enrollment count. To learn more, see [Editing App Connector Provisioning Keys](/zpa/about-connectorprovisioning/edit).
- Stop the App Connector. To learn more, see [Start, Stop, or Restart an App Connector](/zpa/managing-deployed-connectors#Starting).
-
Wipe the configuration directory.
[admin@zpa-connector ~]$ sudo rm /opt/zscaler/var/*
-
Create a provisioning key file with 644 permissions.
[admin@zpa-connector ~]$ sudo touch /opt/zscaler/var/provision_key
[admin@zpa-connector ~]$ sudo chmod 644 /opt/zscaler/var/provision_key
- Copy the provisioning key from the ZPA Admin Portal and use an editor to paste it into the file. To learn more, see [About the App Connector Provisioning Keys Page](/zpa/about-connector-provisioning-keys).
- Save the provisioning key file.
- Start the App Connector. The App Connector service should pick up the provisioning key and re-enroll the App Connector under the appropriate App Connector group.
[]Collect the outputs for the following:
- sudo cat /opt/zscaler/var/version
- sudo ls -lrta /opt/zscaler/var/version
- sudo cat /opt/zscaler/var/updater.version
- sudo /opt/zscaler/var/image.bin -version
- sudo ls -lrta /opt/zscaler/var/image
- []Check the disk space for the following directories:
- sudo df -h /
- sudo du -h /
- sudo du -a/| -n -r | head -n
- Delete any extra directories, except `/opt/zscaler`, to free up space. When disk space is available, the image downloads to `opt/zscaler/var/image.bin`.
- []Verify the App Connector has a stable connection to ZPA Public Service Edge.
-
Run the following command:
journalctl -n1000 | grep zscaler-update
- []Go to the [App Connector page](/zpa/about-connectors#AboutConnectorsPage) and identify the App Connector’s group.
- Go to the [Provisioning key page](/zpa/about-connector-provisioning-keys) and find the App Connector group. If the group is not listed in the App Connector group column, the key is no longer in the ZPA Admin Portal.
- Delete the App Connector and re-enroll it, which allows you to create a new provisioning key for the App Connector.
[]If there is a failure when bringing up a new App Connector, check the following:
- Primary domain name length is less than 36 characters. Names greater than 36 characters can cause problems when forming a certificate.
- The user account “zscaler” has read access to `/etc/resolv.conf`
- The user account “zscaler” has write access to `/opt/zscaler/var`
[]You might experience issues where you cannot enroll a new App Connector in the ZPA Admin Portal, but you have less than 100 active App Connectors.
Within the ZPA Admin Portal, you can have up to 100 App Connectors. This total includes both App Connectors enrolled that are active and App Connectors that are disabled, but not deleted. If you need to add more App Connectors, [delete](/zpa/about-connectors#AboutConnectorsPage) the disabled App Connectors and try enrolling your new App Connectors. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors).
If an App Connector was provisioned in an AWS IMDSv2 required environment with App Connector version 24.566.1 or earlier, a new App Connector is automatically created during re-enrollment due to a hardware fingerprint change. This is due to IMDSv2 support added on App Connector versions 24.650.1 and later. Zscaler recommends that you manually delete the original App Connector from the ZPA Admin Portal to avoid consuming provisioning keys.
If you require an increase in the number of App Connectors, contact Zscaler Support.
[]If an App Connector is not enrolling, you might see an error signifying that the certificate is not valid yet, similar to the following:
The domain (e.g., api.private.com) in the echo statement will depend on what ZPA cloud you are on. To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Mar 02 11:49:56 zpa-connector zpa-connector-child[10500]: This provisioning key has already been enrolled. Attempting to re-enroll
Mar 02 11:49:56 zpa-connector zpa-connector-child[10500]: Send CSR from api.private.zscaler.com/shift/api/v1/admin/assistant/onboard/csr failed: Expected HTTP 204, got HTTP 400
Mar 02 11:49:56 zpa-connector zpa-connector-child[10500]: Send CSR failed, but that may be because we posted it in the past, so it is ok.
Mar 02 11:49:56 zpa-connector zpa-connector-child[10500]: Certificates retrieved do not successfully verify: depth 0:certificate is not yet valid, cert=
-----BEGIN CERTIFICATE-----
MIIDVTCCAj2gAwIBAgIRANb8NfIMTEiZ4WQxHGgSWSswDQYJKoZIhvcNAQELBQAw...
Mar 02 11:49:56 zpa-connector zpa-connector-child[10500]: Certificate enrollment failed.
Mar 02 11:49:57 zpa-connector zpa-connector[10437]: zscaler-update: zpa-connector-child exited too fast, was running for 2 s
The App Connector enrollment process involves the creation of certificates. If the App Connector’s timestamp does not match the timestamp on the ZPA back-end servers, there can be a delay before the certificate becomes valid and enrolls the App Connector.
To resolve this issue, verify that the time on the App Connector is properly set and maintained. To learn more, see [Configure Network Time Protocol (NTP) Servers for an App Connector](/zpa/connector-deployment-guide-amazon-web-services#NTP).
[]If the disk space utilization of the App Connector exceeds 90%, the [configuration and binary snapshots](/zpa/managing-disaster-recovery-configuration-and-binary-snapshots) used for disaster recovery can no longer be captured until the low disk space condition is resolved.
- Check the disk space in the following directories:
sudo df -h /
sudo du -h /
sudo du -a/| -n -r | head -n
- Review and delete any extra directories, except `/opt/zscaler`, to free up space. After sufficient disk space is available, the snapshot creation resumes and the snapshots are sent to the following directories:
- Configuration: `/opt/zscaler/var/config_snapshots`
- Binary: `/opt/zscaler/var/binary_snapshots`
[]When troubleshooting for [disaster recovery](/zpa/understanding-disaster-recovery), consider the following debug commands:
- [Dump the List of Applications Designated for Disaster Recovery](#dumpAppsDr)
- [Dump the Stats of the Configuration JSON Files](#dumpStatsDr)
- [Resolve the Disaster Recovery DNS A and DNS TXT Records](#resolveTxtRecords)
- [Show the Critical Settings for Disaster Recovery](#criticalDrSettings)
In Disaster Recovery Mode and Disaster Recovery Test Mode, all App Connectors in an App Connector group that are designated for disaster recovery restart their zpa-connector services, and all ZPA Private Service Edges in a ZPA Private Service Edge group that are designated for disaster recovery restart their zpa-service-edge services. When the services restart, existing user connections to the test App Connectors and ZPA Private Service Edges that are designated for disaster recovery are dropped. To learn more, see [Configuring Disaster Recovery](/zpa/configuring-disaster-recovery).
[]During a disaster scenario, it might be necessary to review the list of [applications](/zpa/about-disaster-recovery-application-segments) designated for disaster recovery. To dump the list of applications designated for disaster recovery, use the following curl command:
curl 'localhost:9000/assistant/zpn_dr/show_dr_apps'
For example:
% curl 'localhost:9000/assistant/zpn_dr/show_dr_apps'
App#1 name: test1_dr_app_enabled app_gid: 145257608574402742
App#2 name: test2_app_segment app_gid: 145257608574402724
App#3 name: test3_dr_app app_gid: 145257608574402582
%
[]Configuration and binary snapshots are copies of the disaster recovery configuration and binary files used for backup when App Connectors or ZPA Private Service Edges are designated for disaster recovery. To learn more, see [Managing Disaster Recovery Configuration and Binary Snapshots](/zpa/managing-disaster-recovery-configuration-and-binary-snapshots).
To dump the stats of the configuration JSON files, use the following curl command:
curl 'localhost:9000/assistant/zpn_dr/config_json_stats'
For example:
% curl 'localhost:9000/assistant/zpn_dr/config_json_stats'
Config file name :unknown, size :0 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :customer_conf.json, size :17218 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :application_conf.json, size :13336 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :override_conf.json, size :83386 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :other_conf.json, size :0 bytes, last_modified_time:Sep 30 22:36 2022
[]During a disaster scenario, it might be necessary to update an incorrect [DNS record domain name](/zpa/configuring-disaster-recovery#activatingDisasterRecovery). To resolve the disaster recovery DNS A and DNS TXT records and display the output to standard output, use the following curl command:
curl 'localhost:9000/assistant/zpn_dr/resolve_dr_domain?record_type={argument}'
Provide one of the following expected values for the `record_type` argument:
- `A`: Indicates a DNS A record.
- `TXT`: Indicates a DNS TXT record.
The argument values are not case-sensitive, meaning the values `a` and `txt` are supported as well.
For example:
% curl 'localhost:9000/assistant/zpn_dr/resolve_dr_domain?record_type=a'
Resolving DR domain:dr.zpa.drdemo.com record_type:A
Synchronous.
DNS A response addr1 : 192.168.76.18
%
[]During a disaster scenario, it might be necessary to review the [disaster recovery settings](/zpa/about-disaster-recovery-settings) that were configured. To show the critical settings for disaster recovery, use the following curl command:
curl 'localhost:9000/assistant/zpn_dr/show_configuration'
For example:
% curl 'localhost:9000/assistant/zpn_dr/show_configuration'
DR activation domain: dr.zpa.drdemo.com
DR publickey uploaded: NO
DR Max auth interval secs: 1209600
%
[]If an App Connector was provisioned in an AWS IMDSv2 required environment with App Connector version 24.566.1 or earlier, a new App Connector is automatically created during re-enrollment due to a hardware fingerprint change. This is because IMDSv2 support was added on App Connector version 24.650.1 and later. Zscaler recommends that you manually delete the original App Connector from the ZPA Admin Portal to avoid consuming provisioning keys. You might experience issues where you cannot enroll a new App Connector with the AWS-related provisioning key because it has exceeded its maximum key usage.
This total includes both App Connectors enrolled that are active and App Connectors that are disabled, but not deleted. If you need to add more App Connectors or the IMDSv2 App Connector re-enrollment stalls, delete any disabled or disconnected App Connectors and try enrolling your new App Connectors again. To learn more, see [Configuring App Connectors](/zpa/configuring-connectors). Alternatively, you can increase the **Maximum Reuse of Provisioning Key** option. To learn more, see [Editing App Connector Provisioning Keys](/zpa/editing-connector-provisioning-keys).
If you require an increase in the number of App Connectors due to the tenant's maximum App Connector system limit being reached (100 by default), contact Zscaler Support.