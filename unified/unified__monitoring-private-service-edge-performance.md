# Monitoring Private Service Edge Performance
Source: https://help.zscaler.com/unified/monitoring-private-service-edge-performance
PDF: https://help.zscaler.com/pdf/com/en/1496781.pdf

There are a variety of things to consider when monitoring Private Service Edges and their performance. The most important thing is to make sure your Private Service Edges are deployed in a manner that follows Zscaler's recommendations for image sizing and scalability, supported platform requirements, deployment best practices, networking configurations, and other essential guidelines. To learn more, see [Private Service Edge Deployment Prerequisites](/unified/private-service-edge-deployment-prerequisites) and [Networking Deployed Private Service Edges](/unified/networking-deployed-private-service-edges).
Within the Admin Portal, you can use the [Private Service Edge Dashboard](/unified/viewing-private-service-edge-dashboard) to help monitor your organization's Private Service Edges.
When monitoring Private Service Edges directly, consider the following:
- [CPU Utilization](#cpu)
- [Memory Utilization](#memory)
- [Data Throughput](#throughput)
- [Source Port Consumption](#port)
- [Host Application Access](#hostAppAccess)
- [Disk Space Utilization](#diskspace)
- [File Descriptors Exhaustion](#filedscrpt)
[]Peak sustained CPU utilization should be less than 70%. The value needs to take into account all Private Service Edges in the group. The CPU utilization of the group's Private Service Edges should be able to manage additional load and allow each Private Service Edge to operate under 70% utilization in the event that one of the Private Service Edges becomes unavailable. For example, if you only have two Private Service Edges and they are both at 50%, this is below the 70% threshold. However, if one Private Service Edge goes down, then the other Private Service Edge runs above 70%.
To monitor CPU utilization:
- [Review Private Service Edge Status Logs in the Log Streaming Service](#cpu_lss)
- [Review Private Service Edge Status Logs on the Host](#cpu_serviceEdgeHost)
- [Use CLI Commands on the Private Service Edge Host](#cpu_cli)
- [Use Simple Network Management Protocol](#cpu_snmp)
To reduce the CPU utilization on individual Private Service Edge hosts, consider the following:
- Deploy an additional Private Service Edge into the Private Service Edge Group to distribute users across additional Private Service Edges.
- Deploy dedicated Private Service Edge Groups for specific application segments to reduce the number of applications that are requested through each Private Service Edge Group.
The CPU steal percentage is the CPU time stolen from the VM by a Hypervisor and is reported every minute in the status log. When the CPU steal percentage is high, the Hypervisor is busy, resulting in degraded performance for the Private Service Edge.
[]Private Service Edge Status logs can be streamed to a SIEM or a syslog server using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Private Service Edge Status logs are generated periodically for each Private Service Edge, and the field **CPUUtilization** displays the Private Service Edge host's CPU utilization at that instance. For more information, see [About Private Service Edge Metrics Log Fields](/unified/about-private-service-edge-metrics-log-fields).
[]Private Service Edge logs can be viewed on the Private Service Edge host whenever the Private Service Edge is running. The information displayed in the [Private Service Edge logs](/unified/managing-deployed-private-service-edges-private-applications#Monitoring) includes the log output of the Private Service Edge to the local system logging facilities.
To reduce and balance the load among the VMs:
- Ensure the Hypervisor is healthy.
- Change the Hypervisor setup accordingly.
[]Linux provides several utilities to view CPU utilization using Command Line Interface (CLI) commands. For example:
- The `top` command reports the sum of utilization across all cores on all processors.
- The `sysstat` package contains different tools for performance and usage.
You can also create a script that periodically reports the Private Service Edge host’s CPU utilization to a separate statistics collection server.
If the CPU utilization is more than 100%, it may be due to multiple CPU cores on the Private Service Edge host. For example, if there are 4 cores, the top output shows usage at 400%. Use the `lscpu` command to check the number of CPU cores. In this case, the calculation of the peak CPU should be normalized across the number of cores.
[]Simple Network Management Protocol (SNMP) provides a well-defined interface for periodically monitoring performance metrics on host servers. CPU information on the Private Service Edge host can be read using SNMP object identifiers (OIDs).
Some of the well-known SNMP OIDs for monitoring CPU utilization on a Linux OS are:
- Percentage of user CPU time: .1.3.6.1.4.1.2021.11.9.0
- Raw user CPU time: .1.3.6.1.4.1.2021.11.50.0
- Percentage of system CPU time: .1.3.6.1.4.1.2021.11.10.0
- Raw system CPU time: .1.3.6.1.4.1.2021.11.52.0
- Percentage of idle CPU time: .1.3.6.1.4.1.2021.11.11.0
- Raw idle CPU time: .1.3.6.1.4.1.2021.11.53.0
[]Peak sustained memory utilization should be less than 80%. The value needs to take into account all Private Service Edges in the group. The memory of the group's Private Service Edge should be able to manage additional loads and allow each Private Service Edge to operate under 80% utilization in the event one of the Private Service Edge becomes unavailable. For example, if you only have two Private Service Edges and they are both at 50%, this is below the 80% threshold. However, if one Private Service Edge goes down, then the other Private Service Edge runs above 80%
To monitor memory:
- [Review Private Service Edge Status Logs in the Log Streaming Service](#memory_lss)
- [Review Private Service Edge Status Logs on the Host](#memory_serviceEdgeHost)
- [Use CLI Commands on the Private Service Edge Host](#memory_cli)
- [Use Simple Network Management Protocol](#memory_snmp)
To reduce memory utilization on individual Private Service Edge hosts, consider the following:
- Increase the amount of available memory on the Private Service Edge host.
- Deploy additional Private Service Edges into the Private Service Edge Group to distribute users across additional Private Service Edges.
- Deploy dedicated Private Service Edge Groups for specific application segments to reduce the number of applications that are requested through each Private Service Edge Group.
[]Private Service Edge Status logs can be streamed to a SIEM or a syslog server using the [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Private Service Edge Status logs are generated periodically for each Private Service Edge, and the field **MemUtilization** displays the Private Service Edge host’s memory utilization at that instance. For more information, see [About Private Service Edge Status Log Fields](/unified/about-private-service-edge-status-log-fields).
[]Private Service Edge logs can be viewed on the Private Service Edge host whenever the Private Service Edge is running. The information displayed in the [Private Service Edge logs](/unified/managing-deployed-private-service-edges-private-applications#Monitoring) includes the log output of the Private Service Edge to the local system logging facilities.
To reduce and balance the load among the VMs:
- Ensure the Hypervisor is healthy.
- Change the Hypervisor setup accordingly.
[]Linux provides several utilities such as `free`, `top`, `cat/proc/meminfo`, `htop`, and others to view memory utilization using CLI commands. You can create a script that periodically reports the Private Service Edge host’s memory utilization to a separate statistics collection server.
[]Simple Network Management Protocol (SNMP) provides a well-defined interface for periodically monitoring performance metrics on host servers. Memory information on the Private Service Edge host can be read using SNMP object identifiers (OIDs).
Some of the well-known SNMP OIDs for monitoring memory on a Linux OS are:
- Total RAM in machine: .1.3.6.1.4.1.2021.4.5.0
- Total RAM used: .1.3.6.1.4.1.2021.4.6.0
- Total RAM Free: .1.3.6.1.4.1.2021.4.11.0
[]Peak sustained throughput based on recommended Private Service Edge specifications should be less than 500 Mbps.
To monitor Private Service Edge throughput:
- [Review Private Service Edge Status Logs in the Log Streaming Service](#throughput_lss)
- [Review Private Service Edge Status Logs on the Host](#throughput_serviceEdgeHost)
- [Use CLI Commands on the Private Service Edge Host](#throughput_cli)
- [Use Simple Network Management Protocol](#throughput_snmp)
To reduce data throughput on individual Private Service Edge hosts, consider the following:
- Deploy an additional Private Service Edge into the Private Service Edge Group to distribute users across additional Private Service Edges.
- Deploy dedicated Private Service Edge Groups for specific application segments to reduce the number of applications that are requested through each Private Service Edge Group.
[]Private Service Edge Status logs can be streamed to a SIEM or a syslog server using [Log Streaming Service (LSS)](/unified/about-log-streaming-service). Private Service Edge Status logs are generated periodically for each Private Service Edge, and the fields **TotalBytesRx** and **TotalBytesTx **display the Private Service Edge host’s throughput at that instance. For more information, see [About Private Service Edge Status Log Fields](/unified/about-private-service-edge-status-log-fields).
[]Private Service Edge logs can be viewed on the Private Service Edge host whenever the Private Service Edge is running. The information displayed in the [Private Service Edge logs](/unified/managing-deployed-private-service-edges-private-applications#Monitoring) includes the log output of the Private Service Edge to the local system logging facilities. The CPU steal percentage is the CPU time stolen from the VM by a Hypervisor and is reported every minute in the status log. When the CPU steal percentage is high, the Hypervisor is busy, resulting in degraded performance for the Private Service Edge.
To reduce and balance the load among the VMs:
- Ensure the Hypervisor is healthy.
- Change the Hypervisor setup accordingly.
[]Linux provides several utilities such as `nload`, `iftop`, `nethogs`, `bmon`, and others to view bandwidth statistics on the Private Service Edge host interface using CLI commands. You can create a script that periodically reports the host’s bandwidth utilization to a separate statistics collection server.
[]Simple Network Management Protocol (SNMP) provides a well-defined interface for periodically monitoring performance metrics on host servers. Data throughput information on the Private Service Edge host can be read using SNMP object identifiers (OIDs).
Some of the well-known SNMP OIDs for monitoring Private Service Edge throughput on a Linux OS are:
- The total number of bytes received on the interface: .1.3.6.1.2.1.2.2.1.10
- The total number of bytes transmitted on the interface: .1.3.6.1.2.1.2.2.1.16
[]The number of used and free ports can be obtained from the Private Service Edge host by using the following command. In the following example, 11 is the number of UDP ports and 13 is the number of TCP ports in use.
[root@ip-10-0-0-116 admin]# sudo su
[root@ip-10-0-0-116 admin]# ss -uln | wc -l && ss -tn state connected | wc -l
11
13
If the in-use count for either TCP or UDP ports is equal or close to the available ports, the Private Service Edge host is likely to experience port exhaustion and the Private Service Edge may not be able to connect to the applications.
In the following example, the command is still used. It shows the difference of 60999-32768=28231, which indicates the number of ports available for use on this Private Service Edge host. The count of in-use UDP and TCP ports must be lower than 28231.
[root@ip-10-0-0-116 admin]# sysctl net.ipv4.ip_local_port_range
net.ipv4.ip_local_port_range = 32768 60999
[root@ip-10-0-0-116 admin]#
To adjust port usage, consider the following:
- [Increase the Available Maximum Number of Ports](#port_increase)
[]For a non-permanent increase in ports, which does not persist across the Private Service Edge host restart, use one of the following options. The text in red is an example of port ranges:
- Use `echo`
echo 32768 65000 > /proc/sys/net/ipv4/ip_local_port_range
- Use `sysctl`
sysctl -w net.ipv4.ip_local_port_range="32768 65000"
For a permanent increase in ports, add the following to `/etc/sysctl.conf`. The text in red is an example of port ranges:
net.ipv4.ip_local_port_range = 32768 65000
[]There may be degraded application performance if an excessive number of applications are accessed from a smaller number of Private Service Edges within a group. Too many applications accessed from a given Private Service Edge may result in increased application latency or higher amounts of CPU or memory used on the Private Service Edge.
To reduce the number of applications per Private Service Edge, consider the following:
- Deploy dedicated Private Service Edge Groups for specific application segments to reduce the number of applications that are requested through each Private Service Edge Group.
- Zscaler recommends that you add additional Private Service Edges to the existing Private Service Edge Groups to support excess applications.
[]Private Service Edges generate logs that are stored on the disk during the normal course of operation. To ensure adequate disk space is available for Private Service Edge logs and software updates, monitor the disk space for consumption.The Private Service Edge process restarts if there is less than 100 MB of disk space left, and generates a log in the `/var/log/message` file to reflect the cause of the restart. This ensures that the software updates for the Private Service Edge can download successfully.
If the Private Service Edge runs other software, it can generate large volumes of logs that can fill up the disk space.
To monitor disk space:
- [Review the Amount of Free Disk Space](#diskspace_amount)
- [Check the Top Process that Consumes Disk Space](#diskspace_topprocess)
- [Review the Number of System Log Lines Generated](#diskspace_syslog)
- [Use Simple Network Management Protocol](#diskspace_snmp)
To reduce disk space on individual Private Service Edge hosts, use the following options:
- [Archive the Files](#diskspace_archive)
- [Remove the Files](#diskspace_delete)
- [Create More Log Space](#diskspace_logSpace)
Zscaler recommends at least disabling `rsyslogd` to reduce disk space.
[]The `sudo df -h` command displays free disk space on the Private Service Edge host. For example:
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
[]Use the following command to get a rough estimate of the lines of `syslogd` written by the Private Service Edge process:
sudo grep -v "zpa-service-edge" /var/log/messages | wc -l
sudo grep "zpa-service-edge" /var/log/messages | wc -l
[]Simple Network Management Protocol (SNMP) provides a well-defined interface for periodically monitoring performance metrics on host servers. Disk space information on the Private Service Edge host can be read using SNMP object identifiers (OIDs).
Some of the well-known SNMP OIDs for monitoring disk space utilization on a Linux OS are:
- Available space on the disk: .1.3.6.1.4.1.2021.9.1.7.1
- Used space on the disk: .1.3.6.1.4.1.2021.9.1.8.1
- Percentage of space used on disk: .1.3.6.1.4.1.2021.9.1.9.1
- Percentage of inodes used on disk: .1.3.6.1.4.1.2021.9.1.10.1
- Path where the disk is mounted: .1.3.6.1.4.1.2021.9.1.2.1
- Path of the device for the partition: .1.3.6.1.4.1.2021.9.1.3.1
- Total size of the disk/partition (kBytes): .1.3.6.1.4.1.2021.9.1.6.1
[]Use a Linux utility like `logrotate` to archive files on a regular basis (e.g., daily, weekly, or monthly) with the `/etc/logrotate.conf` command.
Some ways to use `logrotate` for archiving are:
- Archive log files daily: `daily`
- Keep 7 days worth of logs: `rotate 7`
- Create new (empty) log files after archiving old ones: `create`
- Use a date as a suffix of the archived file: `dateext`
- Un-comment to compress log files: `compress`
[]Run a cron job to delete log files or use the `rm` command to remove any files you think are not necessary, including archived files. For example, there is no functional implication for deleting `/var/log/messages`. Before deleting, check if you require the files for Private Service Edge troubleshooting.
If you archive files to reduce disk space, you do not need to remove files as well.
[]To create more space in `/var/log/journal`, use the `vacuum-size` or the `vacuum-time` commands. For example:
sudo journalctl --vacuum-size=100m
sudo journalctl --vacuum-time=1d
[]If the number of file descriptors is not sufficient on the Private Service Edge host, transactions can fail due to file descriptor exhaustion. To address this, increase the `SYSTEM_FD` limit by executing the following command:
sudo sysctl -w fs.file-max=1000000
To learn more, see [About the Private Service Edge Dashboard](/unified/viewing-private-service-edge-dashboard#TopWidgets).