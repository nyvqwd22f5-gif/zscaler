# Managing Deployed App Connectors
Source: https://help.zscaler.com/unified/managing-deployed-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496201.pdf

After you deploy an App Connector and complete the proper networking configurations, perform the following procedures to verify that the App Connector is running and healthy, and that the [sizing and scalability specifications](/unified/app-connector-deployment-prerequisites) you decided upon before deployment are still adequate for your organization's needs:
- [Check App Connector Status](#Status)
- [Verify App Connector Sizing Specifications](#VerifySizing)
After verifying your deployment, perform the following procedures to manage and maintain the system:
- [Change the Default Admin Password for the App Connector System Console](#Default)
- [Log In to and Out of the App Connector System Console](#Login)
- [Start, Stop, or Restart an App Connector](#Starting)
- [View App Connector Logs](#Monitoring)
- [Install Endpoint Monitoring Tools](#Tools)
- [Replace a Provisioning Key or Move App Connector to New Hardware](#ReplaceProvisioningKey)
- [Replace an App Connector Using an Existing App Connector Provisioning Key](#RefreshConnectorExistingKey)
- [Update App Connector System Software](#Updating)
- [Update App Connector Software Packages](#upgradingtheconnectorpackage)
[]After an App Connector is deployed, check that the virtual machine (VM) image is meeting your requirements:
- Log in to the App Connector console using your admin credentials.
- Enter the following command:
[admin@zpa-connector ~]$ free -g
Verify that the total available memory is at least 4 GB, as shown in the total column as the value 4. For example:
[admin@zpa-connector ~]$ free -g
total        used        free      shared  buff/cache   available
Mem:              4           0           3           0           0           4
Swap:             0           0           0
- Enter the following command:
[admin@zpa-connector ~]$ cat /proc/cpuinfo | grep flags
Check to see if the list includes the ht flag, which is highlighted in green within the following example:
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca
cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm
constant_tsc rep_good nopl xtopology eagerfpu pni pclmulqdq ssse3 fma cx16
pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx
f16c rdrand hypervisor lahf_lm abm fsgsbase bmi1 avx2 smep bmi2 erms
invpcid xsaveopt
- Enter the following command:
[admin@zpa-connector ~]$ cat /proc/cpuinfo | grep processor
You should see a list of processors, for example:
processor : 0
processor : 1
processor : 2
processor : 3
If your list of flags included ht in step 3, then you should see a minimum of 4 processors displayed here. If not, then you should see a minimum of 2 processors.
To learn more, see [App Connector Specifications and Sizing Requirements](/unified/app-connector-deployment-prerequisites).
[]To log in to the App Connector console, enter the admin credentials.
zpa-connector login: admin
Password: *******
After the initial boot of an App Connector instance, it can take up to 15 minutes for the admin credentials to apply. So, if you receive an invalid credentials error after initial boot, wait a few minutes and try again.
To log out of the App Connector console, enter logout:
[admin@zpa-connector ~]$ logout
[]The default admin account username is admin and the password is zscaler. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. If you forget a changed admin account password, Zscaler recommends deploying a new App Connector rather than trying to recover it.
To change the default admin account credentials:
- [Log in to the App Connector console](/unified/managing-deployed-app-connectors#Login) using the default admin username and password.
- Enter the passwd command, then enter the current default password (zscaler).
[admin@zpa-connector ~]$ passwd
Changing password for user admin.
Changing password for admin.
(current) UNIX password:
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
[admin@zpa-connector ~]$
- Enter the logout command.
[admin@zpa-connector ~]$ logout
[]The App Connector is configured to start automatically at system boot. In some scenarios, it may be necessary to stop, start, or restart the App Connector.
- Log in to the system hosting the App Connector package via SSH or log in to the local App Connector console using your admin credentials.
- Using systemd, enter the appropriate command:
Start:
[admin@zpa-connector ~]$ sudo systemctl start zpa-connector
Stop:
[admin@zpa-connector ~]$ sudo systemctl stop zpa-connector
Restart:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
The following logs may be seen in the App Connector console when an App Connector is restarted, upgraded, or downgraded. This potential error can be ignored:
Mar 23 12:45:39 centos zpa-connector-child[18383]: Upgrade prep error for: Connector, err: ZPATH_RESULT_ERR, upgrade_id: 73195382414249455
[]You can check the status of App Connectors by using the [App Connectors page](/unified/about-app-connectors#AboutConnectorsPage) (Infrastructure > Private Access > Component > App Connectors) and the [Health dashboard](/unified/about-health-dashboard) (Analytics > Private Applications > Health).
- Go to the **App Connectors** page (Infrastructure > Private Access > Component > App Connectors). Check that the App Connector you deployed appears in the table of configured App Connectors.
-
Go to the **Health Dashboard** (Analytics > Private Applications > Health). Check that the App Connector you deployed appears in the **App Connector** widget. The App Connector must have enrolled successfully at least once in order for it to appear within the [Health dashboard](/unified/about-health-dashboard).
For example, if you deployed **San Jose App Connector 3**, you see the following:
-
In **App Connectors**:
![Deployed App Connector displayed within the ZPA Admin Portal](/downloads/unified/networking/private-applications/app-connector-management/app-connector-managing-troubleshooting/managing-deployed-app-connectors/san-jose-connector-3-example.jpg)
-
On the **Health Dashboard**, within the **App Connectors** widget:
![Health Dashboard with App Connectors widget displayed within the ZPA Admin Portal](/downloads/zpa/documentation-knowledgebase/connectors-and-connector-groups/connector-deployment-guides-supported-platforms/managing-deployed-connectors/zpa-connectordeployguides-connectorhealthexample.png)
-
Using systemd - You can use systemd to check that the connector service is running on the local system.
To check App Connector status using systemd:
- Log in to the App Connector console using your admin credentials.
- Enter the following command:
`[admin@zpa-connector ~]$ sudo systemctl status zpa-connector`
A healthy App Connector typically consists of two processes, the parent process and the child. However, if only the parent process is present, this could mean that the App Connector is not healthy. For example, the output below indicates a healthy App Connector that is in an active/running status. Both the parent process of PID 2696 and the child process of PID 2705 are present.
`zpa-connector.service - Zscaler Private Access App Connector
Loaded: loaded (/usr/lib/systemd/system/zpa-connector.service; enabled; vendor preset: enabled)
Active: active (running) since Thu 2016-08-18 00:58:44 UTC; 2h 16min ago
Main PID: 2696 (zpa-connector)
CGroup: /system.slice/zpa-connector.service
├─2696 /opt/zscaler/bin/zpa-connector
└─2705 zpa-connector-child`
The next example shows that the App Connector (with parent process PID 2696) is in an inactive/stopped status:
`zpa-connector.service - Zscaler Private Access App Connector
Loaded: loaded (/usr/lib/systemd/system/zpa-connector.service; enabled; vendor preset: enabled)
Active: inactive (dead) since Thu 2016-08-18 03:19:03 UTC; 9s ago
Process: 2696 ExecStart=/opt/zscaler/bin/zpa-connector (code=killed, signal=TERM)
Main PID: 2696 (code=killed, signal=TERM)`
The systemd core dump is enabled by default in Red Hat Enterprise Linux 8 (RHEL 8). If the systemd core dump is enabled, the systemd output of a connector service running on RHEL 8 can include core dump information.
[]The App Connector records logs using the syslog facilities of the local Linux system.
To view App Connector logs:
- Log in to the App Connector console using your admin credentials.
- Enter the following command:
[admin@zpa-connector ~]$ sudo journalctl -u zpa-connector
The information displayed includes the log output of the App Connector to the local system logging facilities. Also, a running App Connector will periodically output status messages, for example:
-------- App Connector Status:ID=217246525011525974:Name=Test App Connector-1:Ver=18.42.1 --------
Certificate will expire in 370 days, 21 hours, 39 minutes
Control connection state: fohh_connection_connected, local:[10.80.202.1]:53040
remote:broker1a.ec2.prod.zpath.net...3.245]:443
RPC Messages: BrkRq = 0, BrkRqAck = 0, BindReq = 0, BindReqAck = 0, AppRtDisc = 0,
AppRtReq = 0, DsnAstChk = 0
Broker data connection count = 0, backed_off connections = 0
Data Transfer: Total ToBroker = 0 bytes, Total FromBroker = 0 bytes
Mtunnels: Total Created = 0, Total Freed = 0, Current Active = 0
Registered apps count = 0, alive app = 0, passive_health = 0, service_count = 0,
target_count = 0, alive_target ...target = 0
- To create a text file containing the current App Connector log information, use the following command:
[admin@zpa-connector ~]$ sudo journalctl > dump-of-journalctl.txt
Older App Connector logs are automatically stored in the /var/log/messages file.
[]You can install monitoring or endpoint security tools on the App Connector host operating system as long as the tools do not interfere with Zscaler processes or compete for resources. You must ensure that other tools do not consume host operating system resources to an extent that results in resources available for the [App Connector services](/unified/app-connector-deployment-prerequisites#SpecsAndSizing) dropping below minimum provisioning requirements. It is the organization’s responsibility to ensure that the tools you run don’t interfere with the proper operation of the internal processes and external communication of the App Connector services.
[]Occasionally, it may be necessary to update the operating system software in order to mitigate major security vulnerabilities that were discovered in Linux. Because the images are based on the open-source CentOS operating system, you can use existing facilities to update the system.
To update the App Connector system software:
- Log in to the App Connector console using your admin credentials.
- Enter the following command to upgrade the local system software:
[admin@zpa-connector ~]$ sudo yum update -y
After running the `sudo yum update` command, the following response is returned. Zscaler handles the entitlement and recommends ignoring this response:
`Updating Subscription Management repositories.
Unable to read consume identity
This system is not registered with an entitlement server. You can use "rhc" or "subscription-manager" to register. `
- After completing the update process, reboot the App Connector using the following command:
[admin@zpa-connector ~]$ sudo reboot
[]There are multiple ways to upgrade the App Connector software package:
- [Update the App Connector software package with a proxy server](#upgradeviaproxyserver)
- [Update the App Connector software package with access to the package repository](#upgradewithconnection)
- [Update the App Connector software package without access to the package repository](#upgradewithoutconnection)
- []Log in to the App Connector console using your admin credentials.
- Edit the /etc/yum.conf file. Use an editor, such as vi.
[admin@zpa-connector ~]$ sudo vi /etc/yum.conf
Add the proxy server and port information as well as the proper authentication credentials for it, for example:
# The proxy server - proxy server:port number
proxy=http://proxy.example.com:8080
# Proxy authentication
proxy_username=proxyusername
proxy_password=proxypassword
- Update the App Connector software package using the following command:
[admin@zpa-connector ~]$ sudo yum update
- After completing the update process, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
- []Log in to the App Connector console using your admin credentials.
- Update the App Connector software package using the following command:
[admin@zpa-connector ~]$ sudo yum update zpa-connector
- After completing the update process, restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
- []Download one of the following RPM packages:
- RPM package for Red Hat Enterprise Linux 8-based deployments ([zpa-connector.rpm](https://yum.private.zscaler.com/yum/el8/zpa-connector-24.650.5-1.el8.x86_64.rpm))
- RPM package for Red Hat Enterprise Linux 9-based deployments ([zpa-connector.rpm](https://yum.private.zscaler.com/yum/el9/zpa-connector-24.650.5-1.el9.x86_64.rpm))
-
Use the scp command to copy the RPM package to the App Connector, for example:
$ scp <RPM Version>
- Log in to the App Connector console using your admin credentials.
- Update the App Connector software package using the following command:
`[admin@zpa-connector ~]$ sudo rpm -Uvh zpa-connector-24.650.5-1.el9.x86_64.rpm`
- Make sure that the update completes successfully. For example:
`[admin@zpa-connector ~]$ sudo rpm -Uvh zpa-connector-24.650.5-1.el9.x86_64.rpm
[sudo] password for admin:
Preparing... ################################# [100%]
Updating / installing...
1:zpa-connector-24.650.5-1.el9 ################################# [ 50%]
Warning: zpa-connector.service changed on disk. Run 'systemctl daemon-reload' to reload units.
Cleaning up / removing...
2:zpa-connector-24.650.5-1.el9 ################################# [100%]`
-
Restart the App Connector using the following command:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
[]You must re-enroll the App Connector in order to replace its provisioning key or if it is moved to new hardware. For both cases, you must use a new key with the virtual machine (VM) image you originally deployed.
To replace a provisioning key for an App Connector:
- Log in to the Admin Portal and go to the **App Connectors** page (Infrastructure > Private Access > Component > App Connectors).
- Locate the App Connector you want to replace the provisioning key for and click the **Delete **icon.
- In the confirmation window that appears, click **Delete**.
- (Optional) If you do not already have your new App Connector provisioning key, be sure to complete the procedure for [adding a new App Connector with a new provisioning key](/unified/configuring-app-connectors).
- Log in to the App Connector console using your admin credentials.
- Temporarily enable sshd:
- For Amazon Web Services (AWS), update your Security Group to allow inbound connections from port 22. To learn more, see the [App Connector Deployment Guide for Amazon Web Services (AWS)](/unified/app-connector-deployment-guide-amazon-web-services#security).
- For Microsoft Azure, update your Network security group (firewall) to allow inbound connections from port 22. To learn more, see the [App Connector Deployment Guide for Microsoft Azure](/unified/app-connector-deployment-guide-microsoft-azure#Deployment).
- For all other platforms, enter the following command:
`[admin@zpa-connector ~]$ sudo systemctl start sshd`
- Enter the following command to stop the connector service:
`[admin@zpa-connector ~]$ sudo systemctl stop zpa-connector`
- Use one of the following options to remove the old provisioning key file:
- Enter a command to get full root access, and then enter the remove command.
`[admin@zpa-connector ~]$ sudo su
[admin@zpa-connector /home/admin]# rm -f /opt/zscaler/var/*`
- Enter the remove command in a subshell.
`[admin@zpa-connector ~]$ sudo bash -c "rm -f /opt/zscaler/var/*"`
- Create a new provisioning key file with 644 permissions, at /opt/zscaler/var/provision_key. For example:
`[admin@zpa-connector ~]$ sudo touch /opt/zscaler/var/provision_key
[admin@zpa-connector ~]$ sudo chmod 644 /opt/zscaler/var/provision_key`
You must reconfigure your proxy settings in the App Connector after creating a new provisioning key file because the proxy settings are removed along with the old provisioning key file in Step 8.
- Copy the provisioning key from the Admin Portal, paste it into the file, and save. Use an editor, such as vi.
`[admin@zpa-connector ~]$ sudo vi /opt/zscaler/var/provision_key`
If you are unfamiliar with the vi editor, you can also use the following echo and tee commands to paste in the provisioning key, making sure that the key is within double quotes ("):
`echo "<App Connector Provisioning Key>" | sudo tee /opt/zscaler/var/provision_key`
- Enter the following command to verify the file's content:
`[admin@zpa-connector ~]$ sudo cat /opt/zscaler/var/provision_key`
The output should return the provisioning key you entered in the previous step.
- Enter the following command to start the connector service:
`[admin@zpa-connector ~]$ sudo systemctl start zpa-connector`
- For all platforms, with the exception of AWS and Azure, enter the following command to disable sshd:
`[admin@zpa-connector ~]$ sudo systemctl stop sshd`
- For AWS and Azure, make sure that you disable inbound access via port 22.
[]If you need to replace a deployed App Connector using a new provisioning key on an existing VM image, complete the [Replace an App Connector provisioning key](/unified/managing-deployed-app-connectors#ReplaceProvisioningKey) procedure above. If you need to replace a deployed App Connector using an existing provisioning key on a new VM image, complete the following steps:
- Log into the Admin Portal and go to the **App Connector Provisioning Keys** page (Infrastructure > Private Access > Component > App Connector Keys).
- On the **App Connector Provisioning Keys** page, locate the existing key you want to use and click the **Edit icon**.
- In the **Edit App Connector Provisioning Key** window, increase the **Maximum Reuse of Provisioning Key** value to accommodate the number of App Connectors you are going to replace. To learn more, see [Editing App Connector Provisioning Keys.](/unified/editing-app-connector-provisioning-keys)
- Deploy the new replacement App Connector VM images using the existing provisioning key from step 3 above. By doing so, these new App Connectors will automatically join the same App Connector Group as the App Connectors you are replacing. To learn more, see the [Deployment Guide for your App Connector](/unified/networking/private-applications/app-connector-management/app-connector-deployment-guides-supported-platforms).
- When the new App Connectors are deployed, they will appear within the [Health dashboard](/unified/about-health-dashboard). Verify that the new App Connectors in the App Connector Group are enabled and showing an **Up Time**.
- Go to the **App Connectors** page (Infrastructure > Private Access > Component > App Connectors).
- On the **App Connectors **page, locate the App Connectors you want to replace and click the **Edit icon**.
- In the **Edit App Connectors** window, set the **Status **to **Disabled**. To learn more, see [Editing a Deployed App Connector](/unified/editing-deployed-app-connector).
- Verify that user access to your applications is still working as desired.
- To ensure that all user traffic has fully transferred to the new replacement App Connectors, wait at least 24 hours before deleting the old disabled App Connectors.
When the user sessions have expired on the disabled App Connectors, delete them within the Admin Portal and remove any old VM instances from your environment.