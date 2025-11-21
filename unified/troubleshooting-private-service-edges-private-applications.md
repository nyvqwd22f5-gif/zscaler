# Troubleshooting Private Service Edges for Private Applications
Source: https://help.zscaler.com/unified/troubleshooting-private-service-edges-private-applications
PDF: https://help.zscaler.com/pdf/com/en/1496786.pdf

This article provides troubleshooting information and guidelines about Private Service Edges. To learn more about Private Service Edges, see [About Private Service Edges](/unified/about-private-service-edges-private-applications). To configure Private Service Edges, see [Configuring Private Service Edges](/unified/configuring-private-service-edges-private-applications).
When troubleshooting Private Service Edges, consider the following scenarios:
- [Private Service Edges Not Connected to the Cloud](#notConnectedCloud)
- [Private Service Edges Connectivity to App Connectors](#connectivityConnectors)
- [DNS Failure, but Private Service Edges Successful](#dnsFailure)
- [SSL Interceptions](#sslinterceptions)
- [Memory Leaks or High Memory Usage](#memory)
- [High CPU](#cpu)
- [Unable to Connect to the Cloud](#cloudConnect)
- [Larger Number of TCP Sockets in the System](#tcpSockets)
- [Frequent Disconnections to the Cloud](#frequentCloudDisconnects)
- [Private Service Edges Load Not Balanced](#loadBalance)
- [Private Service Edges Pause State](#pauseState)
- [Private Service Edges Upgrade Failure](#upgradeFailure)
- [Private Service Edges Upgrade Partial Failure](#partialFailure)
- [Enrollment Failure](#enrollmentFailure)
- [Configuration and Binary Snapshots Not Captured](#disasterRecovery)
- [Disaster Recovery Debugging](#debuggingDr)
[]If the Private Service Edge was previously working and now shows an error about not being connected to the cloud, you might see an error similar to the following:
Apr 02 08:03:21 zpa-service-edge zpa-service-edge-child[1737]: [Received event from [13.170.52.111]:38864;broker2.sha1.prod.zpath.net:[56.109.210.189]:2010: BEV_EVENT_CONNECTED, sock=63 using ECDHE-RSA-AES128-GCM-SHA256
Apr 02 08:03:22 zpa-service-edge zpa-service-edge-child[1737]: [Received event from [13.170.52.111]:38864;broker2.sha1.prod.zpath.net:[56.109.210.189]:2010: BEV_EVENT_READING BEV_EVENT_ERROR, sock=63
Apr 02 08:03:22 zpa-connector zpa-connector-child[1737]: [*Connector not yet connected to cloud, please check connectivity, if this persists*
You might see this error if a Private Service Edge was deleted from the Admin Portal accidentally. Private Applications immediately recognizes that it should not communicate with the Private Service Edge, and it breaks the active connection. There is no way to recover the Private Service Edge.
To resolve this issue:
- Remove the Private Service Edge on the deployed platform.
- Log in to the Private Service Edge console using your admin credentials.
- Enter the following command to stop the service-edge service:
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Enter the following command to switch to a root user:
[admin@zpa-service-edge ~]$ sudo su
- Enter the following command to delete the Private Service Edge:
[root@zpa-service-edge ~]$ rm -rf /opt/zscaler/var/*
- Enter the following command to switch back to a regular user:
[root@zpa-service-edge admin]# exit
- Restart the services.
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
If you attempt to delete the Private Service Edge and the Private Service Edge still reports an ID number, then the Private Service Edge was not fully deleted.
- Restart the process for [configuring](/unified/configuring-private-service-edges-private-applications) a Private Service Edge and [deploying](/unified/about-deploying-private-service-edges-private-applications) on a platform.
[]If the Private Service Edge does not have a direct connection to the App Connector that is providing access to the application, the Private Service Edge forwards traffic to the nearest Public Service Edge. Traffic is not routed automatically to App Connectors.
If no App Connector for the requested application can establish a data connection to the required Private Service Edge where the user is connected, then the Private Service Edge relays the Zscaler Client Connector request to a Public Service Edge. The Public Service Edge then connects to the closest App Connector that it can reach for that application request and completes the application request via the Private Service Edge through an additional hop.
Use the following command to confirm which App Connectors your Private Service Edges are connected to:
curl localhost:8500/fohh/servers?small
Provided is a sample output:
[eng@localhost.dev ~]$ curl localhost:8500/fohh/servers?small
[
["[10.18.15.130]:443;145254333661845533.ast.prod.zpath.net:[10.18.6.255]:59948;0", "client", "fohh_connection_connected", "145254333661845533.145254333661845486.a2pb_ctl.prod.zpath.net", "145254333661845533.ast.prod.zpath.net"],
["[10.18.15.130]:443;145254333661845470.ast.prod.zpath.net:[10.18.11.183]:58956;1", "client", "fohh_connection_connected", "145254333661845470.145254333661845486.a2pb_ctl.prod.zpath.net", "145254333661845470.ast.prod.zpath.net"],
["[10.18.15.130]:443;145254333661845448.ast.prod.zpath.net:[10.18.15.180]:50074;3", "client", "fohh_connection_connected", "145254333661845448.145254333661845486.a2pb_ctl.prod.zpath.net", "145254333661845448.ast.prod.zpath.net"]
]
[]If you have a DNS failure and the Private Service Edge `root` process is successful, you might see an error similar to the following:
The domain (e.g., api.private.com) in the echo statement will depend on what cloud you are on.
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: Checking Enrollment
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: Resolve read certificatefailed
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: No valid certificate. Attempting to enroll
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: Enroll: Connecting to api.private.zscaler.com via pb2br.prod.zpath.net.
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: DNS resolution failed for api.private.zscaler.com
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: Could not create HTTP client
May 25 14:32:53 ussy-nwopapp03 zpa-service-edge-child[2040]: Certificate enrollment failed.
May 25 14:32:55 ussy-nwopapp03 zpa-service-edge[3971]: zscaler-update: zpa-service-edge-child exited too fast, was running for 2 seconds
May 25 14:32:55 ussy-nwopapp03 zpa-service-edge[3971]: zscaler-update: zpa-service-edge-child failed too many times in a row- reverting to default software
The DNS failure might be an issue with the permissions for the user account `Zscaler`. Typically, this means the `root` process is able to read `/etc/resolv.conf`, but the `Zscaler` user account cannot.
To resolve this issue, correct the file permission on `/etc/resolv.conf` for the `Zscaler` user account to allow it read access as well.
[]If you have an error similar to the following, a device between the Private Service Edge and cloud service is attempting a SSL interception:
Jul 10 13:58:18 zpa-service-edge zpa-service-edge-child[992]: Received event from [uninitialized]:0;co2br.prod.zpath.net:[52.28.10.14]:443: BEV_EVENT_READING BEV_EVENT_ERROR, sock=54 self signed certificate in certificate chain /C=US/ST=California/L=San Jose/O=Safemarch/OU=Certificate Authority/CN=Safemarch Inc CA/emailAddress=support@safemarch.com /C=US/ST=California/L=San Jose/O=Safemarch/OU=Certificate Authority/CN=Safemarch Inc CA/emailAddress=support@safemarch.com
Private Applications do not support SSL interceptions. uses TLS connections and pinned certificates, so a device performing SSL interception causes the connection to fail between the Private Service Edge and the Zscaler cloud.
To make sure traffic is not SSL intercepted, you need to allowlist all the domains or IP addresses in the SSL interception device that are listed on [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). This ensures Private Service Edges and the Zscaler URLs (e.g., *.zpath.net, *.zscaler.com) are bypassed from a SSL inspection.
[]You should routinely monitor and address memory leaks or high memory usage in your Private Service Edges. For more information, see [Monitoring Private Service Edge Performance](/unified/monitoring-app-connector-performance).
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
[]You should routinely monitor and address high CPU for your Private Service Edges. For more information, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance).
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
[]If you have issues with the Private Service Edge connecting to the cloud, the problem can come from one of a couple areas. There are a few things to check when narrowing down what is preventing the Private Service Edge to connect:
- [Check the IP ranges.](#cloudConnect_ipRanges)
- [Test the connectivity.](#cloudConnect_connectivity)
- [Check for a TLS connection.](#cloudConnect_tlsConnection)
- [Get the tcpdump.](#cloudConnect_tcpDump)
- [Verify the frequency of error occurrence.](#cloudConnect_error)
- [Do an ICMP ping.](#cloudConnect_icmp)
[]Make sure all the IP ranges allowed by the firewall match those in the firewall policies: refer to [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
[]Test connectivity to the upstream Public Service Edge by querying the DNS address `pb2br.prod.zpath.net` from the server that is running the Private Service Edge software.
The endpoint for Private Service Edges to locate Public Service Edges is pb2br.
Successful connectivity results in two IPs. For example:
[admin@localhost ~]$ dig +short pb2br.prod.zpath.net
13.60.119.37
42.68.244.163
[admin@localhost ~]$
If you do not get two IPs, there is a DNS lookup issue that you need to investigate further.
[]Test if the Private Service Edge can do a TLS connection to a Public Service Edge using the `openssl` command.
A successful TLS connection results in a certificate subject string returned from the Public Service Edge.
In the following example, repeat the test and replace the domain name `safemarch.com` highlighted in red with your own domain name:
[admin@localhost ~]$ openssl s_client -servername safemarch.com.c2.prod.zpath.net -connect pb2br.prod.zpath.net:443 2>&1 | grep subject
subject=/C=US/ST=California/L=San Jose/O=Zscaler/OU=Emerging Technologies/CN=broker1.was1.prod.zpath.net
If the `openssl` command shows an error, an empty response, or no response, then there is a problem with your network. You can try running the openssl command in a loop to see if there is a regular pattern to the success or failure rate. For example, the firewall rule may not allow the Private Service Edge to open a connection to a Public Service Edge. Sometimes the TCP connection goes through, but TLS fails. This is a sign that the firewall is blocking the application layer, but it’s allowing the transport layer.
[]Get the tcpdump and see the delay between the packet sent and the TCP RST received. If the delay is too little (e.g., 1 or 2 milliseconds), then most likely the firewall in your organization's premise is sending the RST.
[]This error sometimes occurs intermittently, which indicates a networking issue either in your organization’s environment or in the internet path from the Private Service Edge to the Public Service Edge. In those cases, perform the following actions:
- Watch for messages similar to those in the example.
- Check the output of `journalctl -n10000 -u zpa-service-edge | grep fohh_connection_connected`. These messages are printed every minute and tell you if the connection is always connected.
- Review the `rx` and `tx` counters in the messages, which tell you how many bytes were transferred in this channel. Based on the state and the bytes counters, you can also see if the connection is inconsistent.
For example:
Aug 23 06:59:39 prod.zpath.net zpa-service-edge-child[7069]: Log(event_log) connection, state fohh_connection_connected, [10.204.5.5]:41131;broker1b.was2.prod.zpath.net:[52.4.154.137]:443;1 uptime , RTT (tcp|app): 0|0 us, tx_b 75698, rx_b 2480
[]Do an ICMP ping to the Public Service Edge.
[]This is expected behavior. Each application requires a TCP port and has its health monitored. Many of these ports can reside in a `TIME_WAIT` state. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance).
[]If you see frequent disconnections between a Private Service Edge to the cloud, the problem can come from one of a couple areas.
Questions to address:
- Is there a Private Service Edge restart involved?
- Is the disconnect only on the control or data connection?
- Is there a pattern emerging out of the disconnection in data and control connection?
- Could there be a routing issue? Is only a specific set of Public Service Edge IPs (with common prefix) having the problem?
- Could the firewall have an out-of-memory state? If so, could the firewall do a TCP RST of the existing connection to claim more memory?
To find the Public Service Edge’s name and begin resolving the issue:
- Go to the **Diagnostics** page (Logs > Diagnostics). For more information, see [About Private Service Edge Status Diagnostics](/unified/accessing-private-service-edge-status-diagnostics).
- Choose **Private Service Edge Status** under **Log Type**.
- Apply the **Disconnected** status filter:
- Click **Add Filters** and select the **Connection: Status Code** filter from the drop-down menu.
- Select the **Equals** Boolean operator from the drop-down menu.
- Select the **Disconnected** status.
- Click **Apply**.
- Check the times in the **Disconnect Time** column to identify the correct Private Service Edge.
- Find the name in the **Service Edge** column to identify the Public Service Edge name or Private Service Edge.
- Repeat steps 4 and 5 if there are multiple times for the disconnection.
[]Sometimes the load (i.e., the interface stats) is not equally split between the Private Service Edges in the Private Service Edge group. Each Private Service Edge shares its load utilization with the Zscaler cloud once per minute. The Public Service Edges redirect the load across different Private Service Edges in a group by accounting for the relative CPU and memory utilization of each Private Service Edge. This redirection steers new connections over a period of time towards less loaded Private Service Edges over Private Service Edges that are heavily loaded.
To address the load not balancing, Zscaler recommends that the CPU and memory utilization of your Private Service Edges do not exceed the threshold. To learn more, see [Monitoring Private Service Edge Performance](/unified/monitoring-private-service-edge-performance).
[]A Private Service Edge can be in a paused state for one of the following reasons:
- `#define PAUSE_REASON_CERT_EXPIRY`: Certificate expiry
- `#define PAUSE_REASON_UPGRADE`: Software upgrade
- `#define PAUSE_REASON_ADMIN_PROBE_PROCESS_RESTART`: Session process restart
- `#define PAUSE_REASON_ADMIN_PROBE_SYSTEM_RESTART`: Session system restart
A Private Service Edge provides the following log when it enters the pause state:
ZPN_LOG(AL_INFO, "Private broker(ID = %"PRId64") (Name = %s) entering PAUSE mode because of - %s",
gs->private_broker_id, gs->cfg_name, private_broker_state_get_pause_reason(gs->pause_reason));
Check the journalctl logs for the reason the Private Service Edge is in a pause state using the following command:
sudo journalctl | grep "entering PAUSE mode because of"
For [remote troubleshooting](/unified/accessing-and-viewing-support-information#Status), Private Service Edges may reject additional session commands when they are currently in a paused state. The following command is returned in the Private Service Edge console when they are currently in a paused state and reject a session command:
ADMIN_PROBE_LOG(AL_NOTICE, "entity is currently in paused mode, not taking any probe commands");
[]There are different possible reasons for Private Service Edge upgrade failures:
- [Upgrade is in a failed state for more than 24 hours.](#upgradeFailure_24hours)
- [Private Service Edge cannot download the image since there is no disk space left.](#upgradeFailure_noDiskSpace)
- [Private Service Edge cannot download the image due to inconsistent connection between the Private Service Edge and pb2br (Private Service Edge to Public Service Edge endpoint).](#upgradeFailure_inconsistentConnection)
- [Provisioning Key was deleted in the Admin Portal.](#upgradeFailure_provisioningKey)
If none of the above reasons are causing the upgrade failures, complete the following steps to try and resolve the upgrade failure:
- Restart the Private Service Edge. To learn more, see [Start, Stop, or Restart a Private Service Edge](/unified/managing-deployed-private-service-edges-private-applications#Starting).
- Stop the Private Service Edge.
- Verify no processes are running.
[admin@localhost ~]$ sudo ps wU zscaler
PID TTY      STAT   TIME COMMAND
[admin@localhost ~]$
- Start the Private Service Edge.
- Return to the [Private Service Edges page](/unified/about-private-service-edges-private-applications) to see if the Update Status changes from **Failure **to **Success**. If the status still says **Failure**, proceed to the next step.
- Check the logs and network connectivity by addressing any issues if identified.
- Test connectivity to the upstream Public Service Edge by querying the DNS address `pb2br.prod.zpath.net` from the server that is running the Private Service Edge software.
The endpoint for Private Service Edge to locate Public Service Edges is pb2br.
Successful connectivity results in two IPs. For example:
[admin@localhost ~]$ dig +short pb2br.prod.zpath.net
13.60.119.37
42.68.244.163
[admin@localhost ~]$
- Check if the Private Service Edge can start a TLS connection using the openssl command. You should receive a certificate subject string returned from the Public Service Edges.
In the following example, repeat the test and replace the domain name `safemarch.com` highlighted in red with your own domain name:
[admin@localhost ~]$ openssl s_client -servername safemarch.com.c2.prod.zpath.net -connect pb2br.prod.zpath.net:443 2>&1 | grep subject
subject=/C=US/ST=California/L=San Jose/O=Zscaler/OU=Emerging Technologies/CN=broker1.was1.prod.zpath.net
If you receive a certificate subject, proceed to the next step.
If you do not receive a subject string, there is likely an error with TLS communication. Review the firewall policies and make any adjustments as needed: [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud).
- Revert to the default Private Service Edge version.
- Stop the Private Service Edge. To learn more, see [Start, Stop, or Restart a Private Application Private Service Edge](/unified/managing-deployed-private-service-edges-private-applications#Starting).
- Remove the Private Service Edge binary image, the version identifier file, and the image metadata file.
[admin@zpa-service-edge ~]$ sudo rm /opt/zscaler/var/image.bin
[admin@zpa-service-edge ~]$ sudo rm /opt/zscaler/var/version
[admin@zpa-service-edge ~]$ sudo rm /opt/zscaler/var/metadata
- Start the Private Service Edge. The Private Service Edge reaches out to the Zscaler cloud and re-downloads the default Private Service Edge software version. The Private Service Edge attempts to upgrade at a later time.
- Check the following logs to verify the software version downloaded:
[admin@zpa-service-edge ~]$ sudo journalctl -u zpa-service-edge -f
If the software downloads, return to the [Private Service Edges page](/unified/about-private-service-edges-private-applications) to see if the Update Status changes from **Failure** to **Scheduled**.
If the software did not download or the Private Service Edge still does not update, proceed to the next step.
- Wipe and rebuild the Private Service Edge configuration.
Before you wipe and rebuild the Private Service Edge, you must:
- Identify the Private Service Edge group for the Private Service Edge.
- Identify the Provisioning Key of the Private Service Edge group.
- On the Service Edge Provisioning Key page, verify the number of provisioning keys in the **# of Enrolled Service Edges **column is less than the number in the **Maximum # of Service Edges **column for the provisioning key.
If needed, you can raise the maximum enrollment count. To learn more, see [Editing Private Service Edge Provisioning Keys](/unified/editing-private-service-edge-provisioning-key-private-applications).
- Stop the Private Service Edge. To learn more, see [Start, Stop, or Restart a Private Service Edge](/unified/managing-deployed-private-service-edges-private-applications#Starting).
- Wipe the configuration directory.
[admin@zpa-serivce-edge ~]$ sudo rm /opt/zscaler/var/*
- Create a provisioning key file with 644 permissions.
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/provision_key
- Copy the provisioning key from the Admin Portal and use an editor to paste it into the file. To learn more, see [About the Private Service Edge Provisioning Keys](/unified/about-private-service-edge-provisioning-keys-private-applications).
- Save the provisioning key file.
- Start the Private Service Edge. The Private Service Edge service should pick up the provisioning key and re-enroll the Private Service Edge under the appropriate Private Service Edge group.
[]Collect the outputs for the following:
- `sudo cat /opt/zscaler/var/version`
- `sudo ls -lrta /opt/zscaler/var/version`
- `sudo cat /opt/zscaler/var/updater.version`
- `sudo /opt/zscaler/var/image.bin -version`
- `sudo ls -lrta /opt/zscaler/var/image`
- []Check the disk space for the following directories:
- `sudo df -h /`
- `sudo du -h /`
- `sudo du -a/| -n -r | head -n`
- Delete any extra directories, except `/opt/zscaler`, to free up space. After disk space is available, the image downloads to `opt/zscaler/var/image.bin`.
- []Verify the Private Service Edge has a stable connection to the Public Service Edge.
- Run the following command:
journalctl -n1000 | grep zscaler-update
[]Go to the [Private Service Edge page](/unified/about-private-service-edges-private-applications) (Infrastructure > Private Access > Component > Private Service Edges) and identify the Private Service Edge’s group.
- Go to the [provisioning key page](/zpa/about-zpa-service-edge-provisioning-keys) (Infrastructure > Private Access > Component > Service Edge Keys) and find the Private Service Edge group. If the group is not listed in the Private Service Edge group column, the key is no longer in the Admin Portal.
- Delete the Private Service Edge and re-enroll it, which allows you to create a new provisioning key for the Private Service Edge.
[]If there is a failure when bringing up a new Private Service Edge, check the following:
- Primary domain name length is less than 36 characters. Names greater than 36 characters can cause problems when forming a certificate.
- The user account `zscaler` has read access to /etc/resolv.conf.
- The user account `zscaler` has write access to /opt/zscaler/var.
If enrollment failure is still an issue, there are different possible reasons for Private Service Edge enrollment failures:
- [Have Less Than 100 Active Private Service Edges, But Can't Enroll More](#enrollmentFailure_amtServiceEdge)
- [Certificate Is Not Valid Yet](#enrollmentFailure_certificateNotValid)
[]You might experience issues where you cannot enroll a new Private Service Edge in the Admin Portal, but you have less than 100 active Private Service Edge.
Within the Admin Portal, you can have up to 100 Private Service Edges. This total includes both Private Service Edges enrolled that are active and Private Service Edges that are disabled, but not deleted. If you need to add more Private Service Edges, [delete](/unified/about-private-service-edges-private-applications#AbourSvcEdgePage) the disabled Private Service Edges and try enrolling your new Private Service Edge. To learn more, see [Configuring Private Service Edges](/unified/configuring-private-service-edges-private-applications).
[]If a Private Service Edges is not enrolling, you might see an error signifying that the certificate is not valid yet, similar to the following:
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Fetch CSR Fields from api-f4.prod.zpath.nethttps://api-f4.prod.zpath.net/zpn/api/v2/admin/broker/onboard/details failed: Expected HTTP 200, got HTTP 400
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Could not fetch CSR fields
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Fetch CSR Response - nonce(<2|api-f4.prod.zpath.net|Y7Pn1SF...>) fingerprint(<DzGT1uFr76...>)
{
"reason": "nonce usage count reached the limit nonce.maxUsage",
"id": "nonce.usage.exceeded",
"params": [
"nonce.maxUsage"
],
"hostname": "localhost"
}
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Certificate enrollment failed.
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Failed to enroll.
Sep 19 14:12:40 localhost.prod.zpath.net zpa-service-edge-child[13303]: Error: ZPATH_RESULT_ERR, Could not enroll Service Edge
The Private Service Edges enrollment process involves the creation of certificates. If the Private Service Edge’s timestamp does not match the timestamp on the back-end servers, there can be a delay before the certificate becomes valid and enrolls the Private Service Edge.
To resolve this issue, verify that the time on the Private Service Edges is properly set and maintained. To learn more, see [Configure Network Time Protocol (NTP) Servers for a Private Service Edge](/unified/private-service-edge-deployment-guide-amazon-web-services).
[]If the disk space utilization of the Private Service Edge exceeds 90%, the [configuration and binary snapshots](/unified/managing-disaster-recovery-configuration-and-binary-snapshots) used for disaster recovery can no longer be captured until the low disk space condition is resolved.
- Check the disk space in the following directories:
sudo df -h /
sudo du -h /
sudo du -a/| -n -r | head -n
- Review and delete any extra directories, except `/opt/zscaler`, to free up space. After sufficient disk space is available, the snapshot creation resumes and the snapshots are sent to the following directories:
- Configuration: `/opt/zscaler/var/service-edge/config_snapshots`
- Binary: `/opt/zscaler/var/service-edge/binary_snapshots`
[]When troubleshooting for [disaster recovery](/unified/understanding-disaster-recovery), consider the following debug commands:
- [Dump the List of Applications Designated for Disaster Recovery](#dumpAppsDr)
- [Dump the Stats of the Configuration JSON Files](#dumpStatsDr)
- [Resolve the Disaster Recovery DNS A and DNS TXT Records](#resolveTxtRecords)
- [Show the Critical Settings for Disaster Recovery](#criticalDrSettings)
In Disaster Recovery Mode and Disaster Recovery Test Mode, all App Connectors in an App Connector group that are designated for disaster recovery restart their connector services, and all Private Service Edges in a Private Service Edge group that are designated for disaster recovery restart their service-edge services. When the services restart, existing user connections to the test App Connectors and Private Service Edges that are designated for disaster recovery are dropped. To learn more, see [Configuring Disaster Recovery](/unified/configuring-disaster-recovery).
[]During a disaster scenario, it might be necessary to review the list of [applications](/unified/about-disaster-recovery-application-segments) designated for disaster recovery. To dump the list of applications designated for disaster recovery, use the following curl command:
curl 'localhost:8500/zpn/zpn_dr/show_dr_apps'
For example:
% curl 'localhost:8500/assistant/zpn_dr/show_dr_apps'
App#1 name: test1_dr_app_enabled app_gid: 145257608574402742
App#2 name: test2_app_segment app_gid: 145257608574402724
App#3 name: test3_dr_app app_gid: 145257608574402582
%
[]Configuration and binary snapshots are copies of the disaster recovery configuration and binary files used for backup when App Connectors or Private Service Edges are designated for disaster recovery. To learn more, see [Managing Disaster Recovery Configuration and Binary Snapshots](/unified/managing-disaster-recovery-configuration-and-binary-snapshots).
To dump the stats of the configuration JSON files, use the following curl command:
curl 'localhost:8500/zpn/zpn_dr/config_json_stats'
For example:
% curl 'localhost:9000/zpn/zpn_dr/config_json_stats'
Config file name :unknown, size :0 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :customer_conf.json, size :17218 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :application_conf.json, size :13336 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :override_conf.json, size :83386 bytes, last_modified_time:Sep 30 22:36 2022
Config file name :other_conf.json, size :0 bytes, last_modified_time:Sep 30 22:36 2022
[]During a disaster scenario, it might be necessary to update an incorrect [DNS record domain name](/unified/configuring-disaster-recovery#activatingDisasterRecovery). To resolve the disaster recovery DNS A and DNS TXT records and display the output to standard output, use the following curl command:
curl 'localhost:8500/zpn/zpn_dr/resolve_dr_domain?record_type={argument}'
Provide one of the following expected values for the `record_type` argument:
- `A`: Indicates a DNS A record.
- `TXT`: Indicates a DNS TXT record.
The argument values are not case sensitive, meaning the values `a` and `txt` are supported as well.
For example:
% curl 'localhost:8500/zpn/zpn_dr/resolve_dr_domain?record_type=a'
Resolving DR domain:dr.zpa.drdemo.com record_type:A
Synchronous.
DNS A response addr1 : 192.168.76.18
%
[]During a disaster scenario, it might be necessary to review the [disaster recovery settings](/unified/about-disaster-recovery-settings) that were configured. To show the critical settings for disaster recovery, use the following curl command:
curl 'localhost:8500/zpn/zpn_dr/show_configuration'
For example:
% curl 'localhost:8500/zpn/zpn_dr/show_configuration'
DR activation domain: dr.zpa.drdemo.com
DR publickey uploaded: NO
DR Max auth interval secs: 1209600
%
[]When one of the supporting files fails to upgrade, the Upgrade Status of the Private Service Edge results in a Partial Failure. There are different reasons why the Private Service Edge can fail to install the supporting file:
- [Private Service Edge is not connected to a Public Service Edge.](#partialFailure_notConnectedToPublicSe)
- [Private Service Edge does not have enough bandwidth.](#partialFailure_notEnoughBw)
- [Private Service Edge does not have enough disk space.](#partialFailure_notEnoughDiskSpace)
If none of the above reasons are causing the Partial Failure, contact Zscaler Support.
[]View the [event logs](/unified/viewing-and-managing-events-diagnostics#Event) to confirm the connection to the Public Service Edge.
[]Monitor and reduce the [data throughput](/unified/monitoring-private-service-edge-performance#throughput) of the Private Service Edge.
[]Installing the supporting files requires 150 MB of disk space for the initial installation, and then an additional 150 MB for the upgrade. If there is not adequate disk space for the upgrade, reduce the [disk space](/unified/monitoring-private-service-edge-performance#diskspace) of the Private Service Edge.