# Monitoring App Connector Performance
Source: https://help.zscaler.com/zpa/monitoring-connector-performance
PDF: https://help.zscaler.com/pdf/com/en/1484611.pdf

There are a variety of things to consider when monitoring App Connectors and their performance. The most important thing is to make sure your App Connectors are deployed in a manner that follows Zscaler's recommendations for image sizing and scalability, supported platform requirements, deployment best practices, networking configurations, and other essential guidelines. To learn more, see [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites) and [Networking Deployed App Connectors](/zpa/networking-deployed-connectors).
Within the ZPA Admin Portal, you can use the [App Connector Dashboard](/zpa/viewing-app-connectors-dashboard) and [Health Dashboard](/zpa/about-health-dashboard) to help you monitor your organization's App Connectors.
When monitoring App Connectors directly, consider the following:
- [CPU Utilization](#cpu)
- [Memory Utilization](#memory)
- [Data Throughput](#throughput)
- [Source Port Consumption](#port)
- [Applications Reachability Monitoring](#appreach)
- [Disk Space Utilization](#diskspace)
- [File Descriptors Exhaustion](#filedscrpt)
[]Peak CPU utilization should be less than 75%. The value needs to take into account all connectors in the group. The CPU utilization of the group's App Connectors should be able to manage additional load and allow each App Connector to operate under 75% utilization in the event one of the App Connectors becomes unavailable. For example, if you only have two App Connectors and they are both at 50%, this is below the 75% threshold. However, if one App Connector goes down, then the other App Connector is running above 75%.
To monitor CPU utilization:
- [Review Logs in the Log Streaming Service](#cpu_lss)
- [Review Status Logs of the App Connector Host](#cpu_connectorHost)
- [Use CLI Commands on the App Connector Host](#cpu_cli)
- [Use Simple Network Management Protocol](#cpu_snmp)
To reduce the CPU utilization on individual App Connector hosts, consider the following:
- Deploy additional App Connectors into the App Connector Group to distribute users across additional connectors.
- Deploy dedicated App Connector Groups for specific application segments to reduce the number of applications that are requested through each App Connector Group.
[]App Connector Status logs can be streamed to a SIEM or a syslog server using the [Log Streaming Service (LSS)](/zpa/about-log-streaming-service). App Connector Status logs are generated periodically for each connector, and the field **CPUUtilization** displays the App Connector host’s CPU utilization at that instance. For more information, see [About App Connector Status Log Fields](/zpa/understanding-connector-status-log-fields).
[]App Connector logs can be viewed on the App Connector host whenever the App Connector is running. The information displayed in the [App Connector logs](/zpa/managing-deployed-connectors#Monitoring) includes the log output of the App Connector to the local system logging facilities. CPU steal percentage is the CPU time stolen from the VM by a Hypervisor and is reported every minute in the status log. When the CPU steal percentage is high, the Hypervisor is busy, resulting in degraded performance for the App Connector.
To reduce and balance the load among the VMs:
- Ensure the Hypervisor is healthy.
- Change the Hypervisor setup accordingly.
[]Linux provides several utilities to view CPU utilization using Command Line Interface (CLI) commands. For example:
- The `top` command reports the sum of utilization across all cores on all processors.
- The `sysstat` package contains different tools for performance and usage.
You can also create a script that periodically reports the App Connector host’s CPU utilization to a separate statistics collection server.
If the CPU utilization is more than 100%, it might be due to multiple CPU cores on the App Connector host. For example, if there are 4 cores, the top output could show usage at 400%. Use the `lscpu` command to check the number of CPU cores. In this case, the calculation of peak CPU should be normalized across the number of cores.
[]Simple Network Management Protocol (SNMP) provides a well defined interface for periodically monitoring performance metrics on host servers. CPU information on the App Connector host can be read using SNMP object identifiers (OIDs).
Some of the well known SNMP OIDs for monitoring CPU utilization on a Linux OS are:
- Percentage of user CPU time: .1.3.6.1.4.1.2021.11.9.0
- Raw user CPU time: .1.3.6.1.4.1.2021.11.50.0
- Percentage of system CPU time: .1.3.6.1.4.1.2021.11.10.0
- Raw system CPU time: .1.3.6.1.4.1.2021.11.52.0
- Percentage of idle CPU time: .1.3.6.1.4.1.2021.11.11.0
- Raw idle CPU time: .1.3.6.1.4.1.2021.11.53.0
[]Peak memory utilization should be less than 90%. The value needs to take into account all connectors in the group. The memory of the group's App Connectors should be able to manage additional load and allow each App Connector to operate under 90% utilization in the event one of the App Connectors becomes unavailable. For example, if you only have two App Connectors and they are both at 50%, this is below the 90% threshold. However, if one App Connector goes down, then the other App Connector is running above 90%
To monitor memory:
- [Review logs in the Log Streaming Service.](#memory_lss)
- [Use CLI commands on the App Connector host.](#memory_cli)
- [Use Simple Network Management Protocol.](#memory_snmp)
To reduce memory utilization on individual App Connector hosts, consider the following:
- Increase the amount of available memory on the App Connector host.
- Deploy additional App Connectors into the App Connector Group to distribute users across additional connectors.
- Deploy dedicated App Connector Groups for specific application segments to reduce the number of applications that are requested through each App Connector Group.
[]App Connector Status logs can be streamed to a SIEM or a syslog server using [Log Streaming Service (LSS)](/zpa/about-log-streaming-service). App Connector Status logs are generated periodically for each connector, and the field **MemUtilization** displays the App Connector host’s memory utilization at that instance. For more information, see [About App Connector Status Log Fields](/zpa/understanding-connector-status-log-fields).
[]Linux provides several utilities such as `free`, `top`, `cat /proc/meminfo`, `htop`, and others to view memory utilization using CLI commands. You can create a script that periodically reports the App Connector host’s memory utilization to a separate statistics collection server.
[]Simple Network Management Protocol (SNMP) provides a well defined interface for periodically monitoring performance metrics on host servers. Memory information on the App Connector host can be read using SNMP object identifiers (OIDs).
Some of the well known SNMP OIDs for monitoring memory on a Linux OS are:
- Total RAM in machine: .1.3.6.1.4.1.2021.4.5.0
- Total RAM used: .1.3.6.1.4.1.2021.4.6.0
- Total RAM Free: .1.3.6.1.4.1.2021.4.11.0
[]Peak throughput based on recommended App Connector specifications should be less than 500 Mbps.
500 Mbps of throughput is an aggregate of multiple streams of traffic.
To monitor App Connector throughput:
- [Review logs in the Log Streaming Service.](#throughput_lss)
- [Use CLI commands on the App Connector host.](#throughput-cli)
- [Use Simple Network Management Protocol.](#throughput_snmp)
To reduce data throughput on individual App Connector hosts, consider the following:
- Deploy additional App Connectors into the App Connector Group to distribute users across additional connectors.
- Deploy dedicated App Connector Groups for specific application segments to reduce the number of applications that are requested through each App Connector Group.
[]App Connector Status logs can be streamed to a SIEM or a syslog server using [Log Streaming Service (LSS)](/zpa/about-log-streaming-service). App Connector Status logs are generated periodically for each connector, and the fields **TotalBytesRx** and **TotalBytesTx** display the App Connector host’s throughput at that instance. For more information, see [About App Connector Status Log Fields](/zpa/understanding-connector-status-log-fields).
[]Linux provides several utilities such as `nload`, `iftop`, `nethogs`, `bmon`, and others to view bandwidth statistics on the App Connector host interface using CLI commands. You can create a script that periodically reports the host’s bandwidth utilization to a separate statistics collection server.
[]Simple Network Management Protocol (SNMP) provides a well defined interface for periodically monitoring performance metrics on host servers. Data throughput information on the App Connector host can be read using SNMP object identifiers (OIDs).
Some of the well known SNMP OIDs for monitoring App Connector throughput on a Linux OS are:
- The total number of bytes received on the interface: .1.3.6.1.2.1.2.2.1.10
- The total number of bytes transmitted on the interface: .1.3.6.1.2.1.2.2.1.16
[]The number of used and free ports can be obtained from the App Connector host by using the `ss` command. In the following example, 11 is the number of UDP ports and 13 is the number of TCP ports in use.
[root@ip-10-0-0-116 admin]# sudo su
[root@ip-10-0-0-116 admin]# ss -uln | wc -l && ss -tn state connected | wc -l
11
13
If the in-use count for either TCP or UDP ports is equal or close to the available ports, the App Connector host is likely to experience port exhaustion and the App Connector might not be able to connect to the application servers.
In the following example, the `sysctl` command is still used. It shows the difference of 60999-32768=28231, which indicates the number of ports available for use on this App Connector host. The count of in-use UDP and TCP ports must be lower than 28231.
[root@ip-10-0-0-116 admin]# sysctl net.ipv4.ip_local_port_range
net.ipv4.ip_local_port_range = 32768 60999
To adjust port usage, consider the following:
- [Increase the available max number of ports.](#port_increase)
- [Assign a secondary IP address to the existing interface.](#port_ip)
- [Add another interface to access internal applications.](#port_interface)
[]For a non-permanent increase in ports, which does not persist across the App Connector host restart, use one of the following options. The text in red shows example port ranges:
- Use `echo`
echo 32768 65000 > /proc/sys/net/ipv4/ip_local_port_range
- Use `sysctl`
sysctl -w net.ipv4.ip_local_port_range="32768 65000"
For a permanent increase in ports, add the following to `/etc/sysctl.conf`. The text in red shows example port ranges:
net.ipv4.ip_local_port_range = 32768 65000
[]The number of TCP ports available to the App Connector host can be increased by adding another IP address to the existing interface. This allows the host to access applications using the secondary IP address in combination with an additional set of TCP ports.
[]Create an additional interface on the App Connector host. The additional interface enables the host to use an additional set of TCP ports when accessing applications through this interface.
[]Starting with App Connector version 20.11.20, each App Connector records the number of applications that it is currently monitoring for reachability. This value is stored in the current_target_count field of the App Connector status logs.
An App Connector can only monitor a maximum of 6,000 application targets at any given time. Customers must distribute their application definitions across multiple Application Segments and App Connector groups to ensure that the maximum application targets monitored by an App Connector are less than 6,000. In the case that an App Connector reaches the maximum 6,000 application targets, the On Access health reporting of your application is converted to None, which means that the App Connector does not check and report reachability to the application.
To monitor application reachability:
- [Review the App Connector status log.](#appreach_statuslog)
- [Use CLI commands on the App Connector host.](#appreach_cli)
To reduce the number of applications per App Connector, consider the following:
- Deploy dedicated App Connector Groups for specific application segments to reduce the number of applications that are requested through each App Connector Group.
[]You can view the App Connector status log in the ZPA Admin Portal. To learn more, see [About App Connector Status Diagnostics](/zpa/accessing-connector-diagnostics).
[]Linux provides utilities to understand application reachability using CLI commands. The following example, shows one such way to check:
[root@ip-10-0-0-228 admin]# journalctl -n1000 | grep target
Apr 13 20:15:31 ip-10-0-0-228.us-west-2.compute.internal zpa-connector-child[32623]: Registered apps count 1, alive apps 1, apps with on-access health 1, service count 0, target count 3466, target alive 3466
[]App Connectors generate logs that are stored on the disk during the normal course of operation. To ensure adequate disk space is available for App Connector logs and software updates, monitor the disk space for consumption.
The App Connector process restarts if there is less than 100 MB of disk space left, and it generates a log in `/var/log/message` file to reflect the cause of the restart. This is done to ensure software updates for the App Connector can download successfully.
If the App Connector runs other software, it can generate large volumes of logs that can fill up the disk space.
To monitor disk space:
- [Review the amount of free disk space.](#diskspace_amount)
- [Check the top process that consumes disk space.](#diskspace_topprocess)
- [Review the number of system log lines generated.](#diskspace_syslog)
- [Use Simple Network Management Protocol.](#diskspace_snmp)
To reduce disk space on individual App Connector hosts, use the following options:
- [Disable rsyslogd for App Connector Process.](#diskspace_rsyslogd)
- [Archive the files.](#diskspace_archive)
- [Remove the files.](#diskspace_delete)
- [Create more log space.](#diskspace_logspace)
Zscaler recommends at least disabling rsyslogd to reduce disk space.
[]The `sudo df -h` command displays free disk space on the App Connector host. For example:
[admin@ip-10-0-0-228 ~]$ sudo df -h
Filesystem Size Used Avail Use% Mounted on
/dev/nvme0n1p1 8.0G 1.7G 6.4G 21% /
devtmpfs 1.9G 0 1.9G 0% /dev
tmpfs 1.9G 0 1.9G 0% /dev/shm
tmpfs 1.9G 181M 1.7G 10% /run
tmpfs 1.9G 0 1.9G 0% /sys/fs/cgroup
tmpfs 375M 0 375M 0% /run/user/1000
[]Use the following command to see the top process that consumes disk space:
sudo du -a /| sort -n -r | head -n 20
[]Use the following command to get a rough estimate of the lines of `syslogd` written by App Connector process:
sudo grep -v "zpa-connector" /var/log/messages | wc -l
sudo grep "zpa-connector" /var/log/messages | wc -l
[]Simple Network Management Protocol (SNMP) provides a well defined interface for periodically monitoring performance metrics on host servers. Disk space information on the App Connector host can be read using SNMP object identifiers (OIDs).
Some of the well known SNMP OIDs for monitoring disk space utilization on a Linux OS are:
- Available space on the disk: .1.3.6.1.4.1.2021.9.1.7.1
- Used space on the disk: .1.3.6.1.4.1.2021.9.1.8.1
- Percentage of space used on disk: .1.3.6.1.4.1.2021.9.1.9.1
- Percentage of inodes used on disk: .1.3.6.1.4.1.2021.9.1.10.1
- Path where the disk is mounted: .1.3.6.1.4.1.2021.9.1.2.1
- Path of the device for the partition: .1.3.6.1.4.1.2021.9.1.3.1
- Total size of the disk/partion (kBytes): .1.3.6.1.4.1.2021.9.1.6.1
[]To reduce the log volume generated on the disk, execute the following commands to stop the connector processes from logging to rsyslogd:
echo ‘:programname, isequal, “zpa-connector-child” stop’ >> /etc/rsyslog.d/zpa-connector.conf
echo ‘:programname, isequal, “zpa-connector” stop’ >> /etc/rsyslog.d/zpa-connector.conf
systemctl restart rsyslogd
[]Use a Linux utility like `logrotate` to archive files on a regular basis (e.g., daily, weekly, or monthly) with the `/etc/logrotate.conf` command.
Some ways to use `logrotate` for archiving are:
- Archive log files daily: `daily`
- Keep 7 days worth of logs: `rotate 7`
- Create new (empty) log files after archiving old ones: `create`
- Use a date as a suffix of the archived file: `dateext`
- Un-comment to compress log files: `compress`
[]Run a cron job to delete log files or use the `rm` command to remove any files you think are not necessary, including archived files. For example, there is no functional implication for deleting `/var/log/messages`. Before deleting, check if you require the files for App Connector troubleshooting.
If you archive files to reduce disk space, you do not need to remove files as well.
[]To create more space in `/var/log/journal` use the `vacuum-size` or the `vacuum-time` commands. For example:
sudo journalctl --vacuum-size=100m
sudo journalctl --vacuum-time=1d
[]If the number of file descriptors is not sufficient on the App Connector host, transactions can fail due to file descriptor exhaustion. To address this, increase the `SYSTEM_FD` limit by executing the following command:
sudo sysctl -w fs.file-max=1000000