# Troubleshooting Private Cloud Controllers
Source: https://help.zscaler.com/zpa/troubleshooting-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1532031.pdf

This article provides debugging commands within the Private Cloud Controller console to help with troubleshooting. To learn more about Private Cloud Controllers, see [About Private Cloud Controllers](/zpa/about-private-cloud-controllers). To configure Private Cloud Controllers, see [Configuring Private Cloud Controllers](/zpa/configuring-private-cloud-controllers).
To run the commands:
- Log in to the Private Cloud Controller console.
-
Enter the following command to navigate to the folder:
`cd /opt/zscaler/var/pcc/image/bin`
-
Run `./insight`. The following shows an example of this command:
``[root@ip-172-31-13-126 bin]# ./insight`
pcc> `
The following commands are available:
- [Print Help](#help)
- [Show a List of Available Commands](#view-commands)
- [Show the Private Cloud Controller Version](#version)
- [Exit the Program](#exit)
- [Show the Status of the Private Cloud Controller](#status-pcc)
- [Show the System Status](#status-system)
- [Show the Certificate Status](#status-cert)
- [Verify the Database Status](#status-db)
- [Show the Status of Business Continuity](#status-bcp)
- [Show the Redirect Statistics](#redirect-stats)
- [Show Outgoing Connections](#connections-client)
- [Show Incoming Connections](#connections-server)
- [Show the Current Configuration](#config)
- [Show a List of Backups](#backups)
- [Show Logs from the Last Hour](#logs)
- [Show Logs for a Specific Time Period](#logs-specific)
- [Check the Redirect IP Address](#redirect-ip)
- [Check the Name of the Trusted Network for Redirection](#redirect-trust)
- [Check Connection Activities](#check-connection)
- [Check Connection Activities for a Specific Time Period](#check-connection-activities-timeperiod)
- [Check for a Connection Match by SNI, IP, or User](#check-connection-match)
- [Check for a Connection](#check-connection-timeperiod)
- [Run All Commands Needed for Zscaler Support](#run-all)
[]To print a list of common commands, enter the following command:
`pcc> help`
The output should look similar to the following example:
`pcc> help
Suggestions:
show                                show command
check                               perform check
run-all | tech-support              execute all important commands in one shot
help | ?                            print this help
usage                               print usage
version                             print version
exit | quit                         exit the program`
[]To show a list of available commands, enter the following command:
``pcc> show``
The output should look similar to the following example:
`pcc> show
Suggestions:
logs                                    show journal logs from last 1 hours
status                                  show status of specified object
statistics | stats                      show statistics
connection                              show connections
config                                  show current configuration
backups                                 show backups`
[]To view the version of the Private Cloud Controller, enter the following command:
`pcc> version`
The output should look similar to the following example:
`pcc> version
Insight Version: 25.47.0-PR-11524-207-g6641d39042`
[]To exit the program, enter the following command command:
`pcc> {exit|quit}`
[]To show the status of the Private Cloud Controller, enter the following command:
`pcc> show status pcc`
The output should look similar to the following example:
`pcc> show status pcc
Version: 25.47.0-PR-11524-207-g6641d39042
Customer ID: 217329048513150976
Instance ID: 217329048513151239
Business Continuity Domain: mockland.site
Uptime: 01:32
Status: running`
[]To show the system status, enter the following command:
`pcc> show status system`
The output should look similar to the following example:
`pcc> show status system
zpa-pcc: CPU   0.79%      RSS   20.8MB      VMS  526.4MB      Uptime 1m52s
zpa-pcc-child: CPU  13.14%      RSS  270.2MB      VMS 3780.8MB      Uptime 1m52s
/opt/zscaler: Used 47.02GB     Total 195.80GB    Percent  25.3%
System Load: Load1 9.00%     Load5 17.00%      Load15 18.00%`
[]To show the status of the certificate, enter the following command:
`pcc> show status cert`
The output should look similar to the following example:
`pcc> show status cert
Issuer: CN=217329048513150976.zpa-customer.com/Root,OU=Private Access,O=Zscaler
Subject: CN=217329048513151239.sitec.dev.zpath.net,O=jnie@mockland.com
NotBefore: 2025-08-28 19:29:40 +0000 UTC
NotAfter: 2026-08-28 19:34:40 +0000 UTC`
[]To verify the status of the database, enter the following command:
`pcc> show status {db|database}`
The output should look similar to the following example:
`pcc> show status db
Result:
PASS /opt/zscaler/var/pcc/i.0
PASS /opt/zscaler/var/pcc/i.0.3
PASS /opt/zscaler/var/pcc/i.0.cz1.d1`
[]To show the status of Business Continuity, enter the following command:
`pcc> show status bcp`
The output should look similar to the following example:
`pcc> show status bcp
To Zero Trust Exchange:
44.242.16.32       sc2br.dev.zpath.net: 12 of 12 is connected
(scalog(5), scstats, scovd, scpbstats, scctl, scastats, sclog, scpblog)
54.218.32.105      sc2br.dev.zpath.net: 12 of 12 is connected
(scpblog(4), scalog(3), sccfg, sclog(3), scuserdb)
From App Connector:
10.10.10.200       appc.pkey-1-1745358133707 (217329048513151161): 8 of 8 is connected
(astats, acfg, actl, alog(4), aovd)
Running in Normal Mode (Non-BC Mode)`
[]To show the status of redirects to Business Continuity, enter the following command:
`pcc> show {stats|statistics} redirect`
The output should look similar to the following example:
`pcc> show stats redirect
In 1 Minute    In 5 Minutes    In 15 Minutes    In 30 Minutes    In 60 Minutes
Redirect to PSE - Failed                    0              0                0                0                0
Redirect to IDP                             0              0                0                0                0
Redirect to PSE - Successful                0              0                0                0                0`
[]To show outgoing connections to clients, enter the following command:
`pcc> show connection clients`
The output should look similar to the following example:
`pcc> show connection clients
217329048513151239.scovd.dev.zpath.net
CONNECTED       :37992 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
217329048513151239.scpbstats.dev.zpath.net
CONNECTED       :38050 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
217329048513151239.scpblog.dev.zpath.net
CONNECTED       :38022 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :41464 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :41462 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :41466 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :41524 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
217329048513151239.scalog.dev.zpath.net
CONNECTED       :38106 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :41500 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :41490 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :38034 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :38118 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :41504 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :38024 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :38092 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
217329048513151239.sccfg.dev.zpath.net
CONNECTED       :41452 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
217329048513151239.sclog.dev.zpath.net
CONNECTED       :41512 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :41540 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
CONNECTED       :38076 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
CONNECTED       :41532 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
217329048513151239.scastats.dev.zpath.net
CONNECTED       :38066 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
217329048513151239.1.1.scuserdb.dev.zpath.net
CONNECTED       :41456 -> broker-co2br2b.pdx2.dev.zpath.net@54.218.32.105:443
217329048513151239.scstats.dev.zpath.net
CONNECTED       :38006 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443
217329048513151239.scctl.dev.zpath.net
CONNECTED       :37976 -> broker-co2br2b.pdx2.dev.zpath.net@44.242.16.32:443`
[]To show incoming connections to the server, enter the following command:
`pcc> show connection servers`
The output should look similar to the following example:
`pcc> show connection servers
217329048513151161.aovd.mockland.site
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51388
217329048513151161.astats.mockland.site
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51338
217329048513151161.acfg.mockland.site
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51404
217329048513151161.actl.mockland.site
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51408
217329048513151161.alog.mockland.site
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51346
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51366
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51362
CONNECTED       217329048513151161.ast.dev.zpath.net@10.10.10.200:51382`
[]To view current configuration information for Business Continuity, enter the following command:
`pcc> show config`
The output should look similar to the following example:
`pcc> show config
Customer ID: 217329048513150976
Instance ID: 217329048513151239
Business Continuity Domain: mockland.site
Primary Control Channel Path: Private Cloud Controller
New User Enrollment: true
Switch Users to Public Cloud: Automatic
-------Private Cloud: site-zero
--ID: 217329048513151024
--Enabled: enabled
--Reenroll Period: 101 days
-------Cloud Controller Group: "pcc-group-a"
--Enabled: enabled
--Location: San Jose, CA, USA
----------Cloud Controller: "pcc-pkey-a-1756409680818"
---ID: 217329048513151239
---Enabled: enabled
----------Cloud Controller: "pcc-pkey-a-1753821829650"
---ID: 217329048513151228
---Enabled: enabled
----------Cloud Controller: "pcc-pkey-a-1748578922124"
---ID: 217329048513151209
---Enabled: enabled
-------Cloud Controller Group: "pcc-group-b"
--Enabled: enabled
--Location: San Diego, CA, USA
----------Service Edge Group: "pse-group-a"
---Enabled: enabled
---Location: San Jose, CA, USA
----------Private Service Edge: "pse-pkey-a-1753826822281"
---ID: 217329048513151232
---Enabled: enabled
----------Private Service Edge: "pse-pkey-a-1748027086666"
---ID: 217329048513151181
---Enabled: enabled
----------Private Service Edge: "pse-pkey-a-1744918504061"
---ID: 217329048513151158
---Enabled: enabled
----------Service Edge Group: "pse-group-b"
---Enabled: enabled
---Location: New York, NY, USA
----------App Connector Group: "appc.group-a"
---Enabled: enabled
---Location: San Jose, CA, USA
----------App Connector: "appc.pkey-a-1753828984664"
---ID: 217329048513151235
---Enabled: enabled
----------App Connector: "appc.pkey-1-1748027384696"
--- ID: 217329048513151184
---Enabled: enabled
----------App Connector: "appc.pkey-1-1745358133707"
---ID: 217329048513151161
---Enabled: enabled
-------Private Cloud: site-one
--ID: 217329048513151179
--Enabled: enabled
--Reenroll Period: 101 days
-------Cloud Controller Group: "pcc-group-c"
--Enabled: enabled
--Location: Phoenix, AZ, USA`
[]To show backups for the Private Cloud Controller, enter the following command:
`pcc> show backups`
The output should look similar to the following example:
`pcc> show backups
Snapshot #0  2025-08-28-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug
Snapshot #1  2025-08-27-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug
Snapshot #2  2025-08-26-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug
Snapshot #3  2025-08-25-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug
Snapshot #4  2025-08-24-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug
Snapshot #5  2025-08-23-00-00-00_25.48.0-ET-xxxxxx-bcp-lo-g21bc064244-debug`
[]To view logs for the last hour, enter the following command:
`pcc> show logs`
The output should look similar to the following example:
`pcc> show logs
2025-08-28T20:02:41.114331 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:49570
2025-08-28T20:03:00.115913 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:49658
2025-08-28T20:03:27.114959 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:59838
2025-08-28T20:03:32.914503 -------- Sitec Status:ID=217329048513151239:Name=pcc-pkey-a-1756409680818:Ver=25.47.0-PR-11524-207-g6641d39042:Mem(System|Process)=3%|1%:Mem_abs(MemTotal|MemFree|SwapTotal|SwapFree|SysUsed|ProcessUsed)= 65313704kB |51991068kB |0kB |0kB |1567792kB |281212kB :Disk (Avail|Total)=138.77GB|195.80GB:CPU(Util|Steal|Configured|Avail)=1%|0%|16|16:Uptime=3M:6S --------
2025-08-28T20:03:32.914519 -------- Sitec thread CPU usage: zthread=0% argo_global_memory_thread=0% event_log=0% statistics_log=2% fohh_resolve=0% fohh_thread_0=0% fohh_thread_1=0% fohh_thread_2=0% fohh_thread_3=0% fohh_thread_4=0% fohh_thread_5=0% fohh_thread_6=0% fohh_thread_7=0% fohh_thread_8=0% fohh_thread_9=0% fohh_thread_10=0% fohh_thread_11=0% fohh_thread_12=0% fohh_thread_13=0% fohh_thread_14=0% fohh_thread_15=0% debug=0% zpn_pcap_thread=0% sitec_wally_cfg=1% sqlt_request_thread=0% local_sqlt=0% sitec_wally_ovd=3% local_sqlt=0% wally_userdb_thread=0% config_monitor=0% userdb-cz1d1=0% userdb-cz1d1_sqlt=0% tld_1_send_thread=0% app_thread_0=0% app_thread_1=0% apps_misc_thread=0% zpn_sitec_monitor=0% zhealth_probe_thread=0% admin_probe=0% file_fetch_geo=0% file_fetch_isp=0% 217329048513151239.sitec.dev.zpath.net=0% zpn_sitec_backup=0% app_multi_match_toggle_thread=0% asst_event_log=0% zpn_sc_asst_auth_log=0%
2025-08-28T20:03:32.914524 Certificate will expire in 364 days, 23 hours, 31 minutes, 8 seconds
2025-08-28T20:03:32.914528 Public Broker config connection, state fohh_connection_connected, [10.10.10.59]:41452;broker-co2br2b.pdx2.dev.zpath.net:[54.218.32.105]:443;1 uptime 3M:4S, RTT (tcp|app): 34667|13269 us, disconnect_duration_s 0, tx_b 7196, rx_b 8173
2025-08-28T20:03:32.914532 Public Broker config override connection, state fohh_connection_connected, [10.10.10.59]:37992;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;2 uptime 3M:3S, RTT (tcp|app): 35638|14270 us, disconnect_duration_s 0, tx_b 5062, rx_b 4748
2025-08-28T20:03:32.914536 Public Broker control connection, state fohh_connection_connected, [10.10.10.59]:37976;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;1 uptime 3M:5S, RTT (tcp|app): 34757|13417 us, disconnect_duration_s 0, tx_b 9429, rx_b 4339
2025-08-28T20:03:32.914539 Public Broker static wally config connection - NONE
2025-08-28T20:03:32.914544 Public Broker stats connection, state fohh_connection_connected, [10.10.10.59]:38006;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;1 uptime 3M:2S, RTT (tcp|app): 36983|15917 us, disconnect_duration_s 0, tx_b 10802, rx_b 4283
2025-08-28T20:03:32.914547 Public Broker event log connection, state fohh_connection_connected, [10.10.10.59]:41512;broker-co2br2b.pdx2.dev.zpath.net:[54.218.32.105]:443;2 uptime 3M:0S, RTT (tcp|app): 27133|21424 us, disconnect_duration_s 0, tx_b 199626, rx_b 12499
2025-08-28T20:03:32.914550 fproxy conn stats (disabled) alloc: 0, free queue: 0, num active conn: 0, total conn: 0, rx bytes: 0, tx bytes: 0
2025-08-28T20:03:32.914554 Time skew: local time lags cloud time by 0.001620s
2025-08-28T20:03:32.914558 Siem log stats summary: {"zpn_sitec_siem_log_stats":{"argo_log_copy_success":2,"argo_log_copy_failure":0,"trans_log_success":0,"trans_log_failure":0,"auth_log_success":0,"auth_log_failure":0,"ast_auth_log_success":0,"ast_auth_log_failure":0,"pb_auth_log_success":0,"pb_auth_log_failure":0,"ast_comprehensive_stats_log_success":0,"ast_comprehensive_stats_log_failure":0,"pb_comprehensive_stats_log_success":0,"pb_comprehensive_stats_log_failure":0,"sc_comprehensive_stats_log_success":0,"sc_comprehensive_stats_log_failure":0,"ast_inspection_log_success":0,"ast_inspection_log_failure":0,"ast_app_inspection_log_success":0,"ast_app_inspection_log_failure":0,"ast_krb_inspection_log_success":0,"ast_krb_inspection_log_failure":0,"ast_ldap_inspection_log_success":0,"ast_ldap_inspection_log_failure":0,"ast_smb_inspection_log_success":0,"ast_smb_inspection_log_failure":0,"ast_api_log_success":0,"ast_api_log_failure":0,"siem_ids_lookup_success":4,"siem_ids_lookup_failure":0,"siem_config_fetch_err_counter":0,"log_filtered_counter":4,"no_memory_err_counter":0,"serialize_err_counter":0,"siem_active_connections":0}}
2025-08-28T20:03:32.915009 File descriptors(max|in-use): System 9223372036854775807|2752, Process 102400|465
2025-08-28T20:03:32.915297 System Sockets: Created 208 TCP4 in-use 46, TCP4 time-wait 63, UDP4 in-use 4, TCP6 in-use 4, UDP6 in-use 3, Ports available per interface 28232, IPv4 interfaces 2, IPv6 interfaces 3
2025-08-28T20:03:32.915330 Fetch sitec group for 217329048513151079 returned ZPN_RESULT_NOT_FOUND
2025-08-28T20:03:32.915491 cfg_fohh_conn connected`
[]To view logs for a specific time period, enter the following command:
`pcc> show logs <e.g. 3h, 90m>`
The output should look similar to the following example, which shows logs for one minute:
`pcc> show logs 1m
2025-08-28T20:02:41.114331 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:49570
2025-08-28T20:03:00.115913 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:49658
2025-08-28T20:03:27.114959 SNI not found: sni = 217329048513151161.aslog.mockland.site, ip = 10.10.10.200:59838
2025-08-28T20:03:32.914503 -------- Sitec Status:ID=217329048513151239:Name=pcc-pkey-a-1756409680818:Ver=25.47.0-PR-11524-207-g6641d39042:Mem(System|Process)=3%|1%:Mem_abs(MemTotal|MemFree|SwapTotal|SwapFree|SysUsed|ProcessUsed)= 65313704kB |51991068kB |0kB |0kB |1567792kB |281212kB :Disk (Avail|Total)=138.77GB|195.80GB:CPU(Util|Steal|Configured|Avail)=1%|0%|16|16:Uptime=3M:6S --------
2025-08-28T20:03:32.914519 -------- Sitec thread CPU usage: zthread=0% argo_global_memory_thread=0% event_log=0% statistics_log=2% fohh_resolve=0% fohh_thread_0=0% fohh_thread_1=0% fohh_thread_2=0% fohh_thread_3=0% fohh_thread_4=0% fohh_thread_5=0% fohh_thread_6=0% fohh_thread_7=0% fohh_thread_8=0% fohh_thread_9=0% fohh_thread_10=0% fohh_thread_11=0% fohh_thread_12=0% fohh_thread_13=0% fohh_thread_14=0% fohh_thread_15=0% debug=0% zpn_pcap_thread=0% sitec_wally_cfg=1% sqlt_request_thread=0% local_sqlt=0% sitec_wally_ovd=3% local_sqlt=0% wally_userdb_thread=0% config_monitor=0% userdb-cz1d1=0% userdb-cz1d1_sqlt=0% tld_1_send_thread=0% app_thread_0=0% app_thread_1=0% apps_misc_thread=0% zpn_sitec_monitor=0% zhealth_probe_thread=0% admin_probe=0% file_fetch_geo=0% file_fetch_isp=0% 217329048513151239.sitec.dev.zpath.net=0% zpn_sitec_backup=0% app_multi_match_toggle_thread=0% asst_event_log=0% zpn_sc_asst_auth_log=0%
2025-08-28T20:03:32.914524 Certificate will expire in 364 days, 23 hours, 31 minutes, 8 seconds
2025-08-28T20:03:32.914528 Public Broker config connection, state fohh_connection_connected, [10.10.10.59]:41452;broker-co2br2b.pdx2.dev.zpath.net:[54.218.32.105]:443;1 uptime 3M:4S, RTT (tcp|app): 34667|13269 us, disconnect_duration_s 0, tx_b 7196, rx_b 8173
2025-08-28T20:03:32.914532 Public Broker config override connection, state fohh_connection_connected, [10.10.10.59]:37992;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;2 uptime 3M:3S, RTT (tcp|app): 35638|14270 us, disconnect_duration_s 0, tx_b 5062, rx_b 4748
2025-08-28T20:03:32.914536 Public Broker control connection, state fohh_connection_connected, [10.10.10.59]:37976;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;1 uptime 3M:5S, RTT (tcp|app): 34757|13417 us, disconnect_duration_s 0, tx_b 9429, rx_b 4339
2025-08-28T20:03:32.914539 Public Broker static wally config connection - NONE
2025-08-28T20:03:32.914544 Public Broker stats connection, state fohh_connection_connected, [10.10.10.59]:38006;broker-co2br2b.pdx2.dev.zpath.net:[44.242.16.32]:443;1 uptime 3M:2S, RTT (tcp|app): 36983|15917 us, disconnect_duration_s 0, tx_b 10802, rx_b 4283
2025-08-28T20:03:32.914547 Public Broker event log connection, state fohh_connection_connected, [10.10.10.59]:41512;broker-co2br2b.pdx2.dev.zpath.net:[54.218.32.105]:443;2 uptime 3M:0S, RTT (tcp|app): 27133|21424 us, disconnect_duration_s 0, tx_b 199626, rx_b 12499
2025-08-28T20:03:32.914550 fproxy conn stats (disabled) alloc: 0, free queue: 0, num active conn: 0, total conn: 0, rx bytes: 0, tx bytes: 0
2025-08-28T20:03:32.914554 Time skew: local time lags cloud time by 0.001620s
2025-08-28T20:03:32.914558 Siem log stats summary: {"zpn_sitec_siem_log_stats":{"argo_log_copy_success":2,"argo_log_copy_failure":0,"trans_log_success":0,"trans_log_failure":0,"auth_log_success":0,"auth_log_failure":0,"ast_auth_log_success":0,"ast_auth_log_failure":0,"pb_auth_log_success":0,"pb_auth_log_failure":0,"ast_comprehensive_stats_log_success":0,"ast_comprehensive_stats_log_failure":0,"pb_comprehensive_stats_log_success":0,"pb_comprehensive_stats_log_failure":0,"sc_comprehensive_stats_log_success":0,"sc_comprehensive_stats_log_failure":0,"ast_inspection_log_success":0,"ast_inspection_log_failure":0,"ast_app_inspection_log_success":0,"ast_app_inspection_log_failure":0,"ast_krb_inspection_log_success":0,"ast_krb_inspection_log_failure":0,"ast_ldap_inspection_log_success":0,"ast_ldap_inspection_log_failure":0,"ast_smb_inspection_log_success":0,"ast_smb_inspection_log_failure":0,"ast_api_log_success":0,"ast_api_log_failure":0,"siem_ids_lookup_success":4,"siem_ids_lookup_failure":0,"siem_config_fetch_err_counter":0,"log_filtered_counter":4,"no_memory_err_counter":0,"serialize_err_counter":0,"siem_active_connections":0}}
2025-08-28T20:03:32.915009 File descriptors(max|in-use): System 9223372036854775807|2752, Process 102400|465
2025-08-28T20:03:32.915297 System Sockets: Created 208 TCP4 in-use 46, TCP4 time-wait 63, UDP4 in-use 4, TCP6 in-use 4, UDP6 in-use 3, Ports available per interface 28232, IPv4 interfaces 2, IPv6 interfaces 3
2025-08-28T20:03:32.915330 Fetch sitec group for 217329048513151079 returned ZPN_RESULT_NOT_FOUND
2025-08-28T20:03:32.915491 cfg_fohh_conn connected`
[]To check the IP addresses targeted by the redirect, enter the following command:
`pcc> check redirect ip <IP-Address>`
The output should look similar to the following example:
pcc> check redirect ip 10.10.10.200
The redirect targets:
34.169.20.1
[]To check the names of the trusted networks targeted by the redirect, enter the following command:
`pcc> check redirect trust-network`
The output should look similar to the following example:
`pcc> check redirect trust-network
The redirect targets:
34.169.20.1
34.170.22.1`
[]To check connection activities from the logs, enter the following command:
`pcc> check connection`
The output should look similar to the following example:
`pcc> check connection
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:52775 -> 172.31.13.126:443:
2025-09-24T15:43:01.133022: Created
2025-09-24T15:43:01.374903: Received "Buffer Event": BEV_EVENT_CONNECTED
2025-09-24T15:43:01.375184: Received "Create Tunnel": M+ddFPEtYtujUf8BGs3C
2025-09-24T15:43:01.376315: Received "Redirect to IDP":
2025-09-24T15:43:06.489720: Received "Buffer Event": BEV_EVENT_READING, BEV_EVENT_EOF
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:52779 -> 172.31.13.126:443:
2025-09-24T15:43:06.495059: Created
2025-09-24T15:43:06.501407: Received "Buffer Event": BEV_EVENT_CONNECTED
2025-09-24T15:43:06.501641: Received "Create Tunnel": LxjdlrNp6cX5mVTH+Blm
2025-09-24T15:43:06.502661: Received "Redirect to IDP":
2025-09-24T15:43:11.635335: Received "Buffer Event": BEV_EVENT_READING, BEV_EVENT_EOF`
[]To view connection activities for a specific time period in the logs, enter the following command:
`pcc> check connection <e.g. 3h, 90m>`
The output should look similar to the following example if 5 minutes was entered:
`pcc> check connection 5m
217329048513151161.actl.mockland.site: 10.10.10.200:51742 -> :0:
2025-08-28T19:35:02.116590: Created
2025-08-28T19:35:02.127960: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.astats.mockland.site: 10.10.10.200:51748 -> :0:
2025-08-28T19:35:03.118418: Created
2025-08-28T19:35:03.127628: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.alog.mockland.site: 10.10.10.200:51756 -> :0:
2025-08-28T19:35:03.118441: Created
2025-08-28T19:35:03.135447: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.alog.mockland.site: 10.10.10.200:51772 -> :0:
2025-08-28T19:35:03.118467: Created
2025-08-28T19:35:03.139324: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.alog.mockland.site: 10.10.10.200:51778 -> :0:
2025-08-28T19:35:03.118614: Created
2025-08-28T19:35:03.142945: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.aovd.mockland.site: 10.10.10.200:51810 -> :0:
2025-08-28T19:35:03.118732: Created
2025-08-28T19:35:03.146580: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.alog.mockland.site: 10.10.10.200:51794 -> :0:
2025-08-28T19:35:03.118845: Created
2025-08-28T19:35:03.131608: Received "Buffer Event": BEV_EVENT_CONNECTED
217329048513151161.acfg.mockland.site: 10.10.10.200:51812 -> :0:
2025-08-28T19:35:03.122977: Created
2025-08-28T19:35:03.150546: Received "Buffer Event": BEV_EVENT_CONNECTED`
[]To check a connection match for a specific server name indication (SNI), IP address, or user, enter the following command:
`pcc> check connection match {sni|ip|user} <KEYWORD>`
The output should look similar to the following example:
`pcc> check connection match ip 3.109.182.54
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:52775 -> 172.31.13.126:443:
2025-09-24T15:43:01.133022: Created
2025-09-24T15:43:01.374903: Received "Buffer Event": BEV_EVENT_CONNECTED
2025-09-24T15:43:01.375184: Received "Create Tunnel": M+ddFPEtYtujUf8BGs3C
2025-09-24T15:43:01.376315: Received "Redirect to IDP":
2025-09-24T15:43:06.489720: Received "Buffer Event": BEV_EVENT_READING, BEV_EVENT_EOF`
[]To check a connection match for a specific time period and server name indication (SNI), IP address, or user, enter the following command:
`pcc> check connection <e.g. 3h, 90m> match {sni|ip|user} <KEYWORD>`
The output should look similar to the following example:
`pcc> check connection 90m match ip 3.109.182.54
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:53879 -> 172.31.13.126:443:
2025-09-24T16:15:13.584350: Created
2025-09-24T16:15:13.651299: Received "Buffer Event": BEV_EVENT_CONNECTED
2025-09-24T16:15:13.651535: Received "Create Tunnel": cXbcVQRH5qiIAmU4RTJi
2025-09-24T16:15:13.652440: Received "Redirect to IDP":
2025-09-24T16:15:18.780099: Received "Buffer Event": BEV_EVENT_READING, BEV_EVENT_EOF
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:53883 -> 172.31.13.126:443:
2025-09-24T16:15:18.794485: Created
2025-09-24T16:15:18.802467: Received "Buffer Event": BEV_EVENT_CONNECTED
2025-09-24T16:15:18.802485: Received "Create Tunnel": 1FATULK7qtYb4reWtrGt
2025-09-24T16:15:18.803632: Received "Redirect to IDP":
2025-09-24T16:15:23.913746: Received "Buffer Event": BEV_EVENT_READING, BEV_EVENT_EOF
zpapm-bc.org.c2.bc.zpapm.org: 3.109.182.54:53932 -> 172.31.13.126:443:`
[]To run all commands needed by Zscaler Support at one time, enter the following command:
`pcc> run-all`