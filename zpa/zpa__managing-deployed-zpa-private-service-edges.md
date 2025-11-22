# Managing Deployed ZPA Private Service Edges
Source: https://help.zscaler.com/zpa/managing-deployed-zpa-private-service-edges
PDF: https://help.zscaler.com/pdf/com/en/1485481.pdf

After you deploy a ZPA Private Service Edge and complete the proper networking configurations, verify that the ZPA Private Service Edge is running and healthy, and that the [sizing and scalability specifications](/zpa/zpa-service-edge-deployment-prerequisites) you selected before deployment are still adequate for your organization's needs:
- [Check ZPA Private Service Edge Status](#Status)
- [Verify ZPA Private Service Edge Sizing Specifications](#VerifySizing)
After verifying your deployment, manage and maintain the system:
- [Disable the Password Expiration for a STIG-hardened ZPA Private Service Edge Image](#step3disablepassword)
- [Change the Default Admin Password for the ZPA Private Service Edge System Console](#Default)
- [Log In to and Out of the ZPA Private Service Edge System Console](#Login)
- [Start, Stop, or Restart a ZPA Private Service Edge](#Starting)
- [View ZPA Private Service Edge Logs](#Monitoring)
- [Install Endpoint Monitoring Tools](#Tools)
- [Replace a Provisioning Key or Move ZPA Private Service Edge to New Hardware](#ReplaceProvisioningKey)
- [Replace a ZPA Private Service Edge Using an Existing ZPA Private Service Edge Provisioning Key](#RefreshConnectorExistingKey)
- [Update ZPA Private Service Edge System Software](#Updating)
- [Update ZPA Private Service Edge Software Packages](#upgradingtheconnectorpackage)
[]After a ZPA Private Service Edge is deployed, check that the virtual machine (VM) image meets your requirements:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Enter the following command:
[admin@zpa-service-edge ~]$ free -g
Verify that the total available memory is at least 8 GB, as shown in the total column as the value 8. For example:
`[admin@zpa-service-edge ~]$ free -g
total        used        free      shared  buff/cache   available
Mem:              8           0           3           0           0           8
Swap:             0           0           0`
- Enter the following command:
[admin@zpa-service-edge ~]$ cat /proc/cpuinfo | grep flags
Check to see if the list includes the `ht` flag, which is highlighted in green in this example:
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca
cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm
constant_tsc rep_good nopl xtopology eagerfpu pni pclmulqdq ssse3 fma cx16
pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx
f16c rdrand hypervisor lahf_lm abm fsgsbase bmi1 avx2 smep bmi2 erms
invpcid xsaveopt
- Enter the following command:
[admin@zpa-service-edge ~]$ cat /proc/cpuinfo | grep processor
You should see a list of processors, for example:
processor : 0
processor : 1
processor : 2
processor : 3
If your list of flags included `ht` in step 3, you should see a minimum of 4 processors displayed here. If not, then you should see a minimum of 2 processors.
To learn more, see [ZPA Private Service Edge Specifications and Sizing Requirements](/zpa/zpa-service-edge-deployment-prerequisites).
[]To log in to the ZPA Private Service Edge console, enter the admin credentials.
zpa-service-edge login: admin
Password: *******
After the initial boot of a ZPA Private Service Edge instance, it can take up to 15 minutes for the admin credentials to apply. So, if you receive an invalid credentials error after initial boot, wait a few minutes and try again.
To log out of the ZPA Private Service Edge console, enter `logout`:
[admin@zpa-service-edge ~]$ logout
[]The default admin account username is admin and the password is `zscaler`. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. If you forget a changed admin account password, Zscaler recommends deploying a new ZPA Private Service Edge rather than trying to recover it.
To change the default admin account credentials:
- [Log in to the ZPA Private Service Edge console](#Login) using the default admin username and password.
- Enter the `passwd` command, then enter the current default password (`zscaler`).
[admin@zpa-service-edge ~]$ passwd
Changing password for user admin.
Changing password for admin.
(current) UNIX password:
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
[admin@zpa-service-edge ~]$
- Enter the `logout` command.
[admin@zpa-service-edge ~]$ logout
[]The ZPA Private Service Edge is configured to start automatically at system boot. In some scenarios, it might be necessary to stop, start, or restart the ZPA Private Service Edge.
- Log in to the system hosting the ZPA Private Service Edge package via SSH, or log in to the local ZPA Private Service Edge console using your admin credentials.
- Using `systemd`, enter the appropriate command:
Start:
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
Stop:
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
Restart:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
The following logs might be seen in the ZPA Private Service Edge console when a ZPA Private Service Edge is restarted, upgraded, or downgraded. This potential error can be ignored:
Mar 25 12:45:39 rhel zpa-service-edge-child[18383]: Upgrade prep error for: Connector, err: ZPATH_RESULT_ERR, upgrade_id: 73195382414249455
[]You can check the status of ZPA Private Service Edges in two ways:
- Using the ZPA Private Service Edges page and Health dashboard. You can check the status by accessing the [ZPA Private Service Edges page](/zpa/about-zpa-private-service-edges) and using the [Health dashboard](/zpa/about-health-dashboard) within the ZPA Admin Portal.
- Go to **Configuration & Control** > **Private Infrastructure** > **Service Edge Management** > **Service Edges**. Check that the ZPA Private Service Edge you deployed appears in the table of configured ZPA Private Service Edges.
-
Go to **Dashboard** > **Health**. Check that the ZPA Private Service Edge you deployed appears in the **Service Edge** widget. The ZPA Private Service Edge must have enrolled successfully at least once for it to appear within the Health dashboard.
For example, if you deployed **Test Private Service Edge Group -1**, you see the following:
-
In **Configuration & Control** > **Private Infrastructure** > **Service Edge Management** > **Service Edges**:
![Service Edges page within the ZPA Admin Portal](/downloads/zpa-about-service-edges.png)
-
In **Dashboards** > **Health**, within the **Service Edges** widget:
![Health Dashboard with Service Edges widget displayed within the ZPA Admin Portal](/downloads/zpa-health-dashboard-service-edges.png)
- Using `systemd`, you can check that the `zpa-service-edge` service is running on the local system.
- Log in to the ZPA Private Service Edge console using your admin credentials.
-
Enter the following command:
`[admin@zpa-service-edge~]$ sudo systemctl status zpa-service-edge`
A healthy ZPA Private Service Edge typically consists of two processes, the parent process and the child. However, if only the parent process is present, this could mean that the ZPA Private Service Edge is not healthy. For example, the output below indicates a healthy ZPA Private Service Edge that is in an active/running status. Both the parent process of `PID 2696` and the child process of `PID 2705` are present.
``zpa-service-edge.service - Zscaler Private Access Service Edge                                                                                                                                                                                                                    Loaded: loaded (/usr/lib/systemd/system/zpa-service-edge.service; enabled; vendor preset: enabled)                                                                                                                                                                                                                                                                    Active: active (running) since Thu 2016-08-18 00:58:44 UTC; 2h 16min ago                                                                                                                                                                                                                                                                 Main PID: 2696 (zpa-connector)                                                                                                                                                                                                                                                                        CGroup: /system.slice/zpa-service-edge.service                                                                                                                                                                                                                                                                                ├─2696 /opt/zscaler/bin/zpa-service-edge                                                                                                                                                                                                                                                                                └─2705 zpa-service-edge-child``
The next example shows that the ZPA Private Service Edge (with parent process `PID 2696`) is in an inactive/stopped status:
`zpa-service-edge.service - Zscaler Private Access Service Edge                                                                                                                                                                                                                                                              Loaded: loaded (/usr/lib/systemd/system/zpa-service-edge.service; enabled; vendor preset: enabled)                                                                                                                                                                                                                                                                               Active: inactive (dead) since Thu 2016-08-18 03:19:03 UTC; 9s ago                                                                                                                                                                                                                                                                               Process: 2696 ExecStart=/opt/zscaler/bin/zpa-service-edge (code=killed, signal=TERM)                                                                                                                                                                                                                                                                               Main PID: 2696 (code=killed, signal=TERM)`
[]ZPA Private Service Edge records logs using the syslog facilities of the local Linux system.
To view ZPA Private Service Edge logs:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Enter the following command:
[admin@zpa-service-edge ~]$ sudo journalctl -u zpa-service-edge
The information displayed includes the log output of the ZPA Private Service Edge to the local system logging facilities. Also, a running ZPA Private Service Edge periodically outputs status messages, for example:
-------- Service Edge Status:ID=217246525011525974:Name=Test Service Edge-1:Ver=18.42.1 --------
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
- To create a text file containing the current ZPA Private Service Edge log information, use the following command:
[admin@zpa-service-edge ~]$ sudo journalctl > dump-of-journalctl.txt
Older ZPA Private Service Edge logs are automatically stored in the `/var/log/messages` file.
[]You can install monitoring or endpoint security tools on the ZPA Private Service Edge host operating system as long as the tools do not interfere with Zscaler processes or compete for resources. You must ensure that other tools do not consume host operating system resources to an extent that results in resources available for the [ZPA Private Service Edge services](/zpa/zpa-service-edge-deployment-prerequisites) dropping below minimum provisioning requirements. It is the organization’s responsibility to ensure that the tools you run don’t interfere with the proper operation of the internal processes and external communication of the ZPA Private Service Edge services.
[]Occasionally, it might be necessary to update the operating system software to mitigate major security vulnerabilities that were discovered on Linux. Zscaler recommends that you update the operating system every 30 days to stay up-to-date with the latest security patches.
To update the ZPA Private Service Edge system software:
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Enter the following command to upgrade the local system software:
[admin@zpa-service-edge ~]$ sudo yum update -y
After running the `sudo yum update` command, the following response is returned. Zscaler handles the entitlement and recommends ignoring this response:
Updating Subscription Management repositories.
Unable to read consume identity
This system is not registered with an entitlement server. You can use "rhc" or "subscription-manager" to register.
- After completing the update process, reboot the ZPA Private Service Edge using the following command:
[admin@zpa-service-edge ~]$ sudo reboot
[]There are multiple ways to upgrade the ZPA Private Service Edge software package:
- [Update the ZPA Private Service Edge software package with a proxy server.](#upgradeviaproxyserver)
- [Update the ZPA Private Service Edge software package with access to the package repository.](#upgradewithconnection)
- [Update the ZPA Private Service Edge software package without access to the package repository.](#upgradewithoutconnection)
- []Log in to the ZPA Private Service Edge console using your admin credentials.
- Edit the `/etc/yum.conf` file. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /etc/yum.conf
Add the proxy server and port information as well as the proper authentication credentials for it as shown in this example:
# The proxy server - proxy server:port number
proxy=http://proxy.example.com:8080
# Proxy authentication
proxy_username=proxyusername
proxy_password=proxypassword
- Update the ZPA Private Service Edge software package using the command:
[admin@zpa-service-edge ~]$ sudo yum update
- After completing the update process, restart the ZPA Private Service Edge using the command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
- []Log in to the ZPA Private Service Edge console using your admin credentials.
- Update the ZPA Private Service Edge software package using the following command:
[admin@zpa-service-edge~]$ sudo yum update zpa-service-edge
- After completing the update process, restart the ZPA Private Service Edge using the command:
[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge
- []Download one of the RPM packages:
- RPM package for Red Hat Enterprise Linux 8-based deployments: ([zpa-service-edge.rpm](https://yum.private.zscaler.com/yum/el8/zpa-service-edge-25.49.5-1.el8.x86_64.rpm))
- RPM package for Red Hat Enterprise Linux 9-based deployments: ([zpa-service-edge.rpm](https://yum.private.zscaler.com/yum/el9/zpa-service-edge-25.49.5-1.el9.x86_64.rpm))
- Use the `scp` command to copy the RPM package to the ZPA Private Service Edge as shown in this example:
`$ scp <RPM Version>`
- Log in to the ZPA Private Service Edge console using your admin credentials.
- Update the ZPA Private Service Edge software package using the following command:
`[admin@zpa-service-edge ~]$ sudo rpm -Uvh zpa-service-edge-25.49.5-1.el9.x86_64.rpm`
- Make sure that the update completes successfully as shown in this example:
`[admin@zpa-service-edge~]$ sudo rpm -Uvh zpa-service-edge-25.49.5-1.el9.x86_64.rpm
[sudo] password for admin:
Preparing... ################################# [100%]
Updating / installing...
1:zpa-service-edge-25.49.5-1.el9 ################################# [ 50%]
Warning: zpa-service-edge.service changed on disk. Run 'systemctl daemon-reload' to reload units.
Cleaning up / removing...
2:zpa-service-edge-25.49.5-1.el9 ################################# [100%]`
- Restart the ZPA Private Service Edge using the command:
`[admin@zpa-service-edge ~]$ sudo systemctl restart zpa-service-edge`
[]You must re-enroll the ZPA Private Service Edge to replace its provisioning key or if it is moved to new hardware. For both cases, you must use a new key with the VM image you originally deployed.
To replace a provisioning key for an ZPA Private Service Edge:
- Log in to the ZPA Admin Portal and go to **Configuration & Control** > **Private Infrastructure** > **Service Edge Management** > **Service Edges**.
- Locate the ZPA Private Service Edge that you want to replace the provisioning key for and click the **Delete **icon.
- In the confirmation window that appears, click **Delete**.
- (Optional) If you do not already have your new ZPA Private Service Edge provisioning key, be sure to complete the procedure for [adding a new ZPA Private Service Edge with a new provisioning key](/zpa/configuring-service-edges).
- Log in to the ZPA Private Service Edge console using your admin credentials.
- To temporarily enable `sshd`, enter the following command:
[admin@zpa-service-edge ~]$ sudo systemctl start sshd
- Enter the following command to stop the zpa-service-edge service:
[admin@zpa-service-edge ~]$ sudo systemctl stop zpa-service-edge
- Enter the following command to remove the old provisioning key file:
[admin@zpa-service-edge ~]$ sudo rm -rf /opt/zscaler/var/service-edge/*
-
Enter the following command to recreate the Service Edge directory:
`[admin@zpa-service-edge ~]$ sudo mkdir -p /opt/zscaler/var/service-edge/provision_key
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key`
- Create a new provisioning key file with 644 permissions, at `/opt/zscaler/var/service-edge/provision_key`. For example:
[admin@zpa-service-edge ~]$ sudo touch /opt/zscaler/var/service-edge/provision_key/*
[admin@zpa-service-edge ~]$ sudo chmod 644 /opt/zscaler/var/service-edge/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@zpa-service-edge ~]$ sudo vi /opt/zscaler/var/service-edge/provision_key
If you are unfamiliar with the vi editor, you can also use the following `echo` and `tee` commands to paste in the provisioning key:
`echo "<Service Edge Provisioning Key>" | sudo tee /opt/zscaler/var/service-edge/provision_key`
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
[admin@zpa-service-edge ~]$ sudo cat /opt/zscaler/var/service-edge/provision_key
The output should return the provisioning key you entered in the previous step.
- Enter the following command to start the zpa-service-edge service:
[admin@zpa-service-edge ~]$ sudo systemctl start zpa-service-edge
- For all platforms, except AWS and Azure, enter the following command to disable `sshd`:
[admin@zpa-service-edge ~]$ sudo systemctl stop sshd
For AWS and Azure, make sure that you disable inbound access via port 22.
[]If you need to replace a deployed ZPA Private Service Edge using a new provisioning key on an existing VM image, complete the [Replace a ZPA Private Service Edge provisioning key](/zpa/managing-deployed-connectors) procedure above. If you need to replace a deployed ZPA Private Service Edge using an existing provisioning key on a new VM image, complete these steps:
- Log into the ZPA Admin Portal and go to **Configuration & Control** > **Private Infrastructure** > **Service Edge Management** > **Service Edge Provisioning Keys**.
- On the **Service Edge Provisioning Keys** page, locate the existing key you want to use and click the **Edit **icon.
- In the **Edit Service Edge Provisioning Key** window, increase the **Maximum Reuse of Provisioning Key** value to accommodate the number of ZPA Private Service Edges you are going to replace. To learn more, see [Editing ZPA Private Service Edge Provisioning Keys.](/zpa/editing-a-zpa-private-service-edge-provisioning-key)
- Deploy the new replacement ZPA Private Service Edge VM images using the existing provisioning key from step 3. By doing so, these new ZPA Private Service Edges automatically join the same ZPA Private Service Edge Group as the ZPA Private Service Edges you are replacing. To learn more, see the [Deployment Guide for your ZPA Private Service Edge](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms).
- When the new ZPA Private Service Edges are deployed, they appear within the [Health dashboard](/zpa/about-health-dashboard). Verify that the new ZPA Private Service Edges in the ZPA Private Service Edge Group are enabled and showing an **Up Time**. To learn more, see [Viewing Service Edge Details](/zpa/about-health-dashboard).
- Go to **Configuration & Control** > **Private Infrastructure** > **Service Edge Management** > **Service Edges**.
- On the **Service Edges **page, locate the ZPA Private Service Edges you want to replace and click the **Edit **icon.
- In the **Edit Service Edges** window, set the **Status **to **Disabled**. To learn more, see [Editing a Deployed ZPA Private Service Edge](/zpa/editing-deployed-service-edge).
- Verify that user access to your applications is still working as desired.
- To ensure that all user traffic has fully transferred to the new replacement ZPA Private Service Edges, wait at least 24 hours before deleting the old disabled ZPA Private Service Edges.
When the user sessions have expired on the disabled ZPA Private Service Edges, delete them within the ZPA Admin Portal and remove any old VM instances from your environment.
[]
This information applies to Security Technical Implementation Guide (STIG) images that were released on November 24, 2024 and December 12, 2024. STIG images released after these dates are not affected.
If you're using an affected STIG image, passwords automatically expire every 60 days for Amazon Web Services (AWS), Google Cloud Platform (GCP), and Microsoft Azure, or 95 days (60 days + a 35-day grace period) for VMware.
If the password expires without changing it or disabling expiration, admin access to a ZPA Private Service Edge is no longer available. When admin access expires, the only recovery method is to deploy a new ZPA Private Service Edge.
[]STIG-hardened prebuilt Private Service Edge images affected by password expiration were released on:
- AWS and GCP: November 24, 2024
- Azure and VMware: December 12, 2024
To verify if an image is STIG-hardened:
- Go to the Private Service Edges page in the ZPA Admin Portal.
- Expand the row for a Private Service Edge in the table.
- Under **Private Service Edge Host Platform**, if you see `ZSIVersion: 2024.11` or `ZSIVersion: 2024.12` for the ZSIVersion, the image is STIG-hardened.
[See image.](#StigImage)
Zscaler recommends using one of these methods for passwords:
- [Disable or Set a Password for AWS, GCP, and Azure.](#StigMarketplace)
- [Disable or Set a Password for VMware.](#StigOVAs)
- []Disable the password expiration:
-
Enter the following command (replacing `admin` with your admin username):
``[admin@zpa-service-edge ~]$ sudo chage -M -1 adm`in`
-
Verify that the password is set to never expire.
``[admin@zpa-service-edge ~]$ sudo chage -l adm`in
`Last password change                               : Feb 18, 20`25
`Password expires                                   : never`
`Password inactive                                  : never`
`Account expires                                    : never`
Minimum number of days between password change     : 1
Maximum number of days between password change     : -1
Number of days of warning before password expires  : 7`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 days.
-
[]Disable the password expiration by entering the following command (replacing `admin` with your admin username):
`$ sudo chage -M -1 admin`
- Set a password when creating a new instance using `passwd admin` (replacing `admin` with your admin username) and renew it every 60 or 95 days.
[]
Example STIG-hardened image with `ZSIVersion: 2024.11.`
![Verify STIG-hardened image on a ZPA Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/app-connector-deployment-guide-amazon-web-services-draft-doc-56293/zpa-pse-stig-image-verification-nov2024.png)