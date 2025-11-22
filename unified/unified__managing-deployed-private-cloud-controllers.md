# Managing Deployed Private Cloud Controllers
Source: https://help.zscaler.com/unified/managing-deployed-private-cloud-controllers
PDF: https://help.zscaler.com/pdf/com/en/1529609.pdf

After you deploy a Private Cloud Controller and complete the proper networking configurations, verify that the Private Cloud Controller is running and healthy, and that the [sizing and scalability specifications](/unified/private-cloud-controller-deployment-prerequisites) you selected before deployment are still adequate for your organization's needs:
- [Check Private Cloud Controller Status](#Status)
- [Verify Private Cloud Controller Sizing Specifications](#VerifySizing)
After verifying your deployment, manage and maintain the system:
- [Change the Default Admin Password for the Private Cloud Controller System Console](#Default)
- [Log In to and Out of the Private Cloud Controller System Console](#Login)
- [Start, Stop, or Restart a Private Cloud Controller](#Starting)
- [View Private Cloud Controller Logs](#Monitoring)
- [Install Endpoint Monitoring Tools](#Tools)
- [Replace a Provisioning Key or Move Private Cloud Controller to New Hardware](#ReplaceProvisioningKey)
- [Replace a Private Cloud Controller Using an Existing Private Cloud Controller Provisioning Key](#RefreshConnectorExistingKey)
- [Update Private Cloud Controller System Software](#Updating)
- [Update Private Cloud Controller Software Packages](#upgradingtheconnectorpackage)
[]To check the status of a Private Cloud Controller:
- Go to **Infrastructure **> **Private Access** > **Business Continuity** > **Private Cloud Controllers**.
- Check that the Private Cloud Controller you deployed appears in the table of configured Private Cloud Controllers.
[]After a Private Cloud Controller is deployed, check that the virtual machine (VM) image meets your requirements:
- Log in to the Private Cloud Controller console using your admin credentials.
- Enter the following command:
$ free -g
Verify that the total available memory is at least 16 GB, as shown in the total column as the value 8. For example:
`$ free -g
total        used        free      shared  buff/cache   available
Mem:             16           0           3           0           0           8
Swap:             0           0           0`
- Enter the following command:
$ cat /proc/cpuinfo | grep flags
Check to see if the list includes the `ht` flag, which is highlighted in green in this example:
flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca
cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx rdtscp lm
constant_tsc rep_good nopl xtopology eagerfpu pni pclmulqdq ssse3 fma cx16
pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx
f16c rdrand hypervisor lahf_lm abm fsgsbase bmi1 avx2 smep bmi2 erms
invpcid xsaveopt
- Enter the following command:
$ cat /proc/cpuinfo | grep processor
You should see a list of processors, for example:
processor : 0
processor : 1
processor : 2
processor : 3
If your list of flags included `ht` in the previous step, you should see a minimum of 4 processors displayed here. If not, then you should see a minimum of 2 processors.
To learn more, see [Private Cloud Controller Specifications and Sizing Requirements](/unified/private-cloud-controller-deployment-prerequisites).
[]To log in to the Private Cloud Controller console, enter the admin credentials.
zpa-pcc login: admin
Password: *******
After the initial boot of a Private Cloud Controller instance, it can take up to 15 minutes for the admin credentials to apply. If you receive an invalid credentials error after the initial boot, wait a few minutes and try again.
To log out of the Private Cloud Controller console, enter `logout`:
$ logout
[]The default admin account username is admin and the password is `zscaler`. For enhanced security, you must use the `passwd` command to change the credentials on the default admin account. If you forget a changed admin account password, Zscaler recommends deploying a new Private Cloud Controller rather than trying to recover it.
To change the default admin account credentials:
- [Log in to the Private Cloud Controller console](#Login) using the default admin username and password.
- Enter the `passwd` command, then enter the current default password (`zscaler`).
$ passwd
Changing password for user admin.
Changing password for admin.
(current) UNIX password:
New password:
Retype new password:
passwd: all authentication tokens updated successfully.
$
- Enter the `logout` command.
$ logout
[]The Private Cloud Controller is configured to start automatically at system boot. In some scenarios, it might be necessary to stop, start, or restart the Private Cloud Controller.
- Log in to the system hosting the Private Cloud Controller package via SSH, or log in to the local Private Cloud Controller console using your admin credentials.
- Using `systemd`, enter the appropriate command:
Start:
$ sudo systemctl start zpa-pcc
Stop:
$ sudo systemctl stop zpa-pcc
Restart:
$ sudo systemctl restart zpa-pcc
The following logs might be seen in the Private Cloud Controller console when a Private Cloud Controller is restarted, upgraded, or downgraded. This potential error can be ignored:
Mar 23 12:45:39 centos zpa-pcc-child[18383]: Upgrade prep error for: Connector, err: ZPATH_RESULT_ERR, upgrade_id: 73195382414249455
[]Private Cloud Controller records logs using the syslog facilities of the local Linux system.
To view Private Cloud Controller logs:
- Log in to the Private Cloud Controller console using your admin credentials.
- Enter the following command:
$ sudo journalctl -u zpa-pcc
The information displayed includes the log output of the Private Cloud Controller to the local system logging facilities. Also, a running Private Cloud Controller periodically outputs status messages, for example:
-------- Private Cloud Controller Status:ID=217246525011525974:Name=Test Private Cloud Controller-1:Ver=18.42.1 --------
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
- To create a text file containing the current Private Cloud Controller log information, use the following command:
$ sudo journalctl > dump-of-journalctl.txt
Older Private Cloud Controller logs are automatically stored in the `/var/log/messages` file.
[]You can install monitoring or endpoint security tools on the Private Cloud Controller host operating system as long as the tools do not interfere with Zscaler processes or compete for resources. You must ensure that other tools do not consume host operating system resources to an extent that results in resources available for the [Private Cloud Controller services](/unified/private-cloud-controller-deployment-prerequisites) dropping below minimum provisioning requirements. It is the organization’s responsibility to ensure that the tools you run don’t interfere with the proper operation of the internal processes and external communication of the Private Cloud Controller services.
[]Occasionally, it might be necessary to update the operating system software to mitigate major security vulnerabilities that were discovered on Linux.
To update the Private Cloud Controller system software:
- Log in to the Private Cloud Controller console using your admin credentials.
- Enter the following command to upgrade the local system software:
$ sudo yum update -y
After running the `sudo yum update` command, the following response is returned. Zscaler handles the entitlement and recommends ignoring this response:
Updating Subscription Management repositories.
Unable to read consume identity
This system is not registered with an entitlement server. You can use "rhc" or "subscription-manager" to register.
- After completing the update process, reboot the Private Cloud Controller using the following command:
$ sudo reboot
[]There are multiple ways to upgrade the Private Cloud Controller software package:
- [Update the Private Cloud Controller software package with a proxy server.](#upgradeviaproxyserver)
- [Update the Private Cloud Controller software package with access to the package repository.](#upgradewithconnection)
- [Update the Private Cloud Controller software package without access to the package repository.](#upgradewithoutconnection)
- []Log in to the Private Cloud Controller console using your admin credentials.
- Edit the `/etc/yum.conf` file. Use an editor, such as vi.
$ sudo vi /etc/yum.conf
Add the proxy server and port information as well as the proper authentication credentials for it as shown in this example:
# The proxy server - proxy server:port number
proxy=http://proxy.example.com:8080
# Proxy authentication
proxy_username=proxyusername
proxy_password=proxypassword
- Update the Private Cloud Controller software package using the following command:
$ sudo yum update
- After completing the update process, restart the Private Cloud Controller using the following command:
$ sudo systemctl restart zpa-pcc
- []Log in to the Private Cloud Controller console using your admin credentials.
- Update the Private Cloud Controller software package using the following command:
$ sudo yum update zpa-pcc
- After completing the update process, restart the Private Cloud Controller using the following command:
$ sudo systemctl restart zpa-pcc
- []Download the following files on a server with access for Red Hat Enterprise Linux 9-based deployments:
- RPM package ([zpa-pcc.rpm](https://yum.private.zscaler.com/yum/el9/zpa-pcc-25.43.2-1.el9.x86_64.rpm))
- GPG public key ([https://yum.private.zscaler.com/yum/el9/gpg](https://yum.private.zscaler.com/yum/el9/gpg))
- Use the `scp` command to copy the RPM package to the Private Cloud Controller as shown in this example:
`$ scp zpa-pcc.rpm admin@<server>:/home/admin
$ scp gpg admin@<server>:/home/admin`
- Log in to the Private Cloud Controller console using your admin credentials.
- Update the Private Cloud Controller software package using the following command:
`$ sudo rpm -Uvh zpa-pcc-25.43.2-1.el9.x86_64.rpm`
- Make sure that the update completes successfully as shown in this example:
`$ sudo rpm -Uvh zpa-pcc-25.43.2-1.el9.x86_64.rpm
[sudo] password for admin:
Preparing... ################################# [100%]
Updating / installing...
1:zpa-pcc-25.43.2-1-1.el9 ################################# [ 50%]
Warning: zpa-pcc.service changed on disk. Run 'systemctl daemon-reload' to reload units.
Cleaning up / removing...
2:zpa-pcc-25.43.2-1.el9 ################################# [100%]`
- Restart the Private Cloud Controller using the following command:
`$ sudo systemctl restart zpa-pcc`
[]You must re-enroll the Private Cloud Controller to replace its provisioning key or if it is moved to new hardware. For both cases, you must use a new key with the VM image you originally deployed.
To replace a provisioning key for a Private Cloud Controller:
- Go to **Infrastructure **> **Private Access** > **Business Continuity** > **Private Cloud Controllers**.
- Locate the Private Cloud Controller that you want to replace the provisioning key for and click the **Delete **icon.
- In the confirmation window that appears, click **Delete**.
- (Optional) If you do not already have your new Private Cloud Controller provisioning key, be sure to complete the procedure for [adding a new Private Cloud Controller with a new provisioning key](/unified/configuring-private-cloud-controllers).
- Log in to the Private Cloud Controller console using your admin credentials.
- To temporarily enable `sshd`, enter the following command:
$ sudo systemctl start sshd
- Enter the following command to stop the zpa-pcc service:
$ sudo systemctl stop zpa-pcc
- Enter the following command to remove the old provisioning key file:
$ sudo rm -rf /opt/zscaler/var/pcc/
-
Enter the following command to recreate the Private Cloud Controller directory:
`$ sudo mkdir -p /opt/zscaler/var/pcc/provision_key
$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key`
- Create a new provisioning key file with 644 permissions at `/opt/zscaler/var/pcc/provision_key`. For example:
$ sudo touch /opt/zscaler/var/pcc/provision_key/*
$ sudo chmod 644 /opt/zscaler/var/pcc/provision_key
- Copy the provisioning key from the Admin Portal, paste it into the file, and click **Save**. Use an editor, such as vi.
$ sudo vi /opt/zscaler/var/pcc/provision_key
If you are unfamiliar with the vi editor, you can also use the following `echo` and `tee` commands to paste in the provisioning key:
`echo "<Private Cloud Controller Provisioning Key>" | sudo tee /opt/zscaler/var/pcc/provision_key`
Make sure that the key is within double quotes (").
- Enter the following command to verify the file's content:
$ sudo cat /opt/zscaler/var/pcc/provision_key
The output should return the provisioning key you entered in the previous step.
- Enter the following command to start the zpa-pcc service:
$ sudo systemctl start zpa-pcc
- For all platforms, except AWS and Azure, enter the following command to disable `sshd`:
$ sudo systemctl stop sshd
For AWS and Azure, make sure that you disable inbound access via port 22.
[]If you need to replace a deployed Private Cloud Controller using a new provisioning key on an existing VM image, complete the previous procedure to [replace a Private Cloud Controller provisioning key](#ReplaceProvisioningKey). If you need to replace a deployed Private Cloud Controller using an existing provisioning key on a new VM image, complete these steps:
- Go to **Infrastructure **> **Private Access** > **Business Continuity** > **Private Cloud Controllers**.
- On the **Private Cloud Controller Provisioning Keys** page, locate the existing key you want to use and click the **Edit **icon.
- In the **Edit Private Cloud Controller Provisioning Key** window, increase the **Maximum Reuse of Provisioning Key** value to accommodate the number of Private Cloud Controllers you are going to replace. To learn more, see [Editing Private Cloud Controller Provisioning Keys](/unified/editing-private-cloud-controller-provisioning-keys).
- Deploy the new replacement Private Cloud Controller VM images using the existing provisioning key from the previous step. By doing so, these new Private Cloud Controllers automatically join the same Private Cloud Controller group as the Private Cloud Controller you are replacing. To learn more, see the [Deployment Guide for your Private Cloud Controller](/unified/infrastructure/private-applications/business-continuity-management/private-cloud-controller-deployment-guides-supported-platforms).
- Go to **Infrastructure **> **Private Access** > **Business Continuity** > **Private Cloud Controllers**.
- On the **Private Cloud Controllers **page, locate the Private Cloud Controllers you want to replace and click the **Edit **icon.
- In the **Edit Private Cloud Controllers** window, set the **Status **to **Disabled**. To learn more, see [Editing a Deployed Private Cloud Controller](/unified/editing-deployed-private-cloud-controller).
- Verify that user access to your applications is still available.
- To ensure that all user traffic has fully transferred to the new replacement Private Cloud Controller, wait at least 24 hours before deleting the old disabled Private Cloud Controller.
When the user sessions have expired on the disabled Private Cloud Controllers, delete them within the Admin Portal and remove any old VM instances from your environment.