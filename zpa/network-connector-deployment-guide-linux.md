# Network Connector Deployment Guide for Linux
Source: https://help.zscaler.com/zpa/network-connector-deployment-guide-linux
PDF: https://help.zscaler.com/pdf/com/en/1517176.pdf

This deployment guide provides information on prerequisites, how to deploy a Network Connector on Red Hat Enterprise Linux 9.x, and post-deployment verification checks.
RHEL 9 deployments are only supported on ESXi 7.0 Update 2 or later. To learn more about ESXi support, see [End-of-Support for VMware vSphere Hypervisor (ESXi) Version 5.5](/eos-eol/end-support-vmware-vsphere-hypervisor-esxi-version-5.5).
- [Step 1: Make Sure You Have Met All Network Connector Deployment Prerequisites](#Prereqs)
- [Step 2: Configure the Networking for the Deployed Network Connector](#Networking)
- [Step 3: Deploy the Network Connector on Red Hat Enterprise Linux 9](#Deployment)
- [Step 4: Verify That the Deployed Network Connector Is Running and Healthy](#Status)
After Network Connectors are deployed, you can [create network segments](/zpa/configuring-network-segments) to pass application traffic. For example, to test your configuration, consider setting up a simple application segment that allows SSH access to your Network Connectors.
[]
Before deploying a Network Connector on any supported platform, Zscaler highly recommends reading the following information and making the necessary changes to your organization's environment, where applicable.
- [Network Connector Specifications and Sizing Requirements](#SpecsAndSizing)
- [Network Connector Platform Prerequisites](#PlatformPrereqs)
- [Network Connector Security Guidance and Firewall Requirements](#SecurityAndFirewallReqs)
After you have met all the prerequisites, you can deploy the Network Connector.
[]The following specifications are recommended by Zscaler for each Network Connector:
- Memory: 4 GB RAM
- CPU:
- 2 CPU cores (Xeon E5 class) for physical machines without hyperthreading
- 8 CPU cores (Xeon E5 class) recommended for virtual machines (VMs) with hyperthreading; minimum 4 CPU cores (Xeon E5 class) for virtual machines (VMs) with hyperthreading
Using the [PassMark Software Pty Ltd](https://www.cpubenchmark.net/cpu_list.php) benchmark to verify the CPU Mark score, Zscaler recommends using a minimum CPU benchmark score of 2640 when choosing a CPU processor. The Intel Advanced Encryption Standard New Instructions (AES-NI) instecc3a2ruction set must also be enabled on the CPU processor.
To learn more, see the [Network Connector Deployment Guide for Linux](/zpa/network-connector-deployment-guide-linux).
- Disk Space: 64 GB (thin provisioned) for all deployment platforms
- Network Card: 1 NIC (minimum)
- For VMware platform deployment, the default configuration to allow the host to dynamically allocate VM resources is not recommended. Configure the VM setting to reserve the following memory and CPU allocations:
- Memory: 8 GB RAM
- CPU: total CPU GHz (the number of cores (2 or 8 cores) multiplied by the GHz per core)
To learn more, refer to the [VMware documentation](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.resmgmt.doc/GUID-8B88D3D8-E9D9-4C05-A065-B3DE1FFFB401.html).
After a Network Connector is enrolled, an outbound TLS tunnel over port 443 is established to the ZPA cloud infrastructure. Outbound VPN tunnels establish a gateway to VPN Service Edge using a port range from 51820 to 53000. This communication channel provides various functionality and utilizes minimal bandwidth, which includes traffic: for Network Connector software upgrades (upgrades are completed based on a weekly schedule).
Each Network Connector maps to a single Network Connector group. It is critical that the Network Connector is always available and running or there won't be any traffic. A Network Connector fronts the subnets configured in Network segments. For example, if you have 4 IP address ranges, they can all be mapped to the same Network Connector group. That means the Network Connector needs to route all the packets to these IP addresses. Subnets can be mapped to the same Network Connector, but you must make sure that they are reachable to each other.
[]Before you begin any procedures within the [Network Connector Deployment Guide for Linux](/zpa/vpn-connector-deployment-prerequisites), make sure that you have met all the following prerequisites:
-
Intel x86_64/AMD64-based architecture
-
systemd
-
Root or sudo access to the system in order to configure a new package repository and install packages
-
DNS resolution and network access
-
A Network Connector [provisioning key](/zpa/about-network-connector-provisioning-keys) obtained from the ZPA Admin Portal
-
A static MAC address
- Network Connector can connect to the Zero Trust Network Access Service Edge - TCP port 443 for all Public Service Edges
- An outbound connection to the VPN Service Edges IP address on the UDP port range from 51820 to 53000 must be allowed, not blocked. This is required to establish a VPN tunnel between the Network Connector and VPN Service Edge.
- Gateway IP address is available in the ZPA Admin Portal after you instantiate a gateway instance in VPN Service Edges. To learn more, see [About VPN Service Edges](/zpa/about-vpn-service-edges).
- Network Connector is sized appropriately. The minimum instance size can support an AWS instance size of:
- vCPU: 8
- Memory (GiB): 32
- Instance Storage (GB): EBS-Only
- Network Bandwidth (Gbps): Up to 10
[]Zscaler recommends treating access to Network Connectors as privileged, so only authorized personnel can access a Network Connector's console. By limiting access, there is the added benefit of shielding interprocess communication within the Network Connector from attack.
Operating System Security
The Network Connector is installed as an OS package. Due to the fact that vulnerabilities are regularly found in core open-source components such as DNS resolvers and the Linux Kernel, Zscaler recommends patching the OS on a regular basis or protecting Network Connectors using firewall policies.
Some organizations choose to firewall or otherwise restrict outbound traffic to the internet from the data center. It is possible to deploy a Network Connector in such an environment as long as the Network Connector can reach all Zscaler data centers containing ZPA Public Service Edges. For firewall configuration information for your deployment, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewall Requirements and Interoperability Guidelines
All Zscaler data centers containing ZPA Public Service Edges must be allowed. A partial firewall configuration can result in connectivity problems for end users. Zscaler’s policy is to provide a 90-day notice for activating additional IP CIDR ranges to provide organizations with sufficient opportunity for changing control policies.
Because the service enforces TLS certificate pinning for both client and server certificates, all forms of inline or man-in-the-middle TLS interception or inspection must be disabled. Network Connectors do not function if the TLS certificates presented by the ZPA Public Service Edges or ZPA Private Service Edges do not cryptographically verify against Zscaler-trusted public keys.
By design, certificate verification is not configurable in order to maintain the integrity of the service. So ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the Network Connector. This is necessary for allowing the Network Connector to resolve and reach ZPA Public Service Edges or ZPA Private Service Edges. If you need to allowlist additional Zscaler IP addresses, see [config.zscaler.com/private.zscaler.com/zpa](https://config.zscaler.com/private.zscaler.com/zpa) (for the private.zscaler.com cloud) or [config.zscaler.com/zpatwo.net/zpa](https://config.zscaler.com/zpatwo.net/zpa) (for the zpatwo.net cloud). To learn more, see [What Is My Cloud Name for ZPA?](/zpa/what-my-cloud-name-zpa)
Firewalld Configuration for VPN Redundancy
If you want to use firewalld on a Network Connector that's using VPN redundancy, you must perform additional steps to modify the firewall filter rule so VPN redundancy can work properly.
- [See instructions.](#firewalld)
- []Log in to the Network Connector console.
-
Enter the following command to verify whether firewalld is running:
`$ systemctl status firewalld
● firewalld.service - firewalld - dynamic firewall daemon
Loaded: loaded (/usr/lib/systemd/system/firewalld.service; enabled; preset: enabled)
Active: active (running) since Wed 2025-08-27 16:12:04 UTC; 3min 15s ago
Docs: man:firewalld(1)
Main PID: 768075 (firewalld)
Tasks: 2 (limit: 402811)
Memory: 23.6M
CPU: 292ms
CGroup: /system.slice/firewalld.service
└─768075 /usr/bin/python3 -s /usr/sbin/firewalld --nofork --nopid
Aug 27 16:12:04 npconnector1.pdx2.dev.zpath.net systemd[1]: Starting firewalld - dynamic
firewall daemon...
Aug 27 16:12:04 npconnector1.pdx2.dev.zpath.net systemd[1]: Started firewalld - dynamic
firewall daemon.`
- Ensure that `NftablesTableOwner` is set to `no` in `firewalld.conf`.
-
Open `/etc/firewalld/firewalld.conf` and enter the following command:
`$ sudo vi /etc/firewalld/firewalld.conf`
-
If `NftablesTableOwner` is currently set to `yes`, change the value to `no`. If `NftablesTableOwner` doesn't exist, enter the following configuration:
`# NftablesTableOwner
# If set to yes, the generated nftables rule set will be owned exclusively by
# firewalld. This prevents other entities from mistakenly (or maliciously)
# modifying firewalld's rule set. If you intentionally modify firewalld's
# rules, then you will have to set this to "no"
# Defaults to "yes"
NftablesTableOwner=no`
-
Verify that the configuration was updated:
`$ grep NftablesTableOwner /etc/firewalld/firewalld.conf
# NftablesTableOwner
NftablesTableOwner=no`
-
Reload the firewall:
`$ sudo firewall-cmd --reload`
-
Create a Python script named `network-connector-firewall.py` with the following command:
- [Learn more.](#python-script)
`#!/usr/bin/env python3
import dbus
import dbus.mainloop.glib
from gi.repository import GLib
import subprocess
import sys
# The D-Bus interface and path for firewalld
DBUS_INTERFACE = "org.fedoraproject.FirewallD1"
DBUS_PATH = "/org/fedoraproject/FirewallD1"
# Commands you want to run after firewalld reload
PORT_COMMANDS = [
"firewall-cmd --add-port=51820/udp",
"firewall-cmd --add-port=3784/udp",
"firewall-cmd --add-port=4784/udp",
]
RULE_COMMANDS = [
('if ! nft list chain inet firewalld filter_FORWARD | grep -q \'iifname "npwg0" accept\'; then '
'nft insert rule inet firewalld filter_FORWARD iifname npwg0 accept; fi'),
('if ! nft list chain inet firewalld filter_FORWARD | grep -q \'oifname "npwg0" accept\'; then '
'nft insert rule inet firewalld filter_FORWARD oifname npwg0 accept; fi')
]
def execute_shell_commands(commands):
"""
Helper function to execute a list of shell commands.
"""
for cmd in commands:
try:
subprocess.run(cmd, shell=True, check=True)
print(f"Executed: {cmd}")
except subprocess.CalledProcessError as e:
print(f"Error executing '{cmd}': {e}", file=sys.stderr)
def apply_firewall_rules_for_npwg0():
# Execute port-opening commands
print("Running port-opening commands...")
execute_shell_commands(PORT_COMMANDS)
# Execute rule insertion commands
print("Running rule insertion commands...")
execute_shell_commands(RULE_COMMANDS)
def reloaded_signal_handler():
"""
This function is called when the Reloaded signal is received.
"""
print("Firewalld has been reloaded. Running post-reload actions.")
apply_firewall_rules_for_npwg0()
def main():
apply_firewall_rules_for_npwg0()
# Set up the D-Bus main loop
dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
# Connect to the system bus
bus = dbus.SystemBus()
# Add a signal receiver
bus.add_signal_receiver(
reloaded_signal_handler,
signal_name="Reloaded",
dbus_interface=DBUS_INTERFACE,
bus_name=DBUS_INTERFACE,
path=DBUS_PATH
)
print("Listening for firewalld 'Reloaded' signal...")
# Start the GLib main loop
loop = GLib.MainLoop()
try:
loop.run()
except KeyboardInterrupt:
print("\nStopping listener.")
loop.quit()
if __name__ == '__main__':
main()`
-
Save the script to `/opt/zscaler/etc/network-connector-firewall.py` and make it an executable:
`$ sudo chmod +x /opt/zscaler/etc/network-connector-firewall.py`
-
Create a systemd service file at `/etc/systemd/system/network-connector-firewall.service` with the following command:
`[Unit]
Description=Network Connector Firewall Rules
After=firewalld.service
Requires=firewalld.service
[Service]
ExecStart=/opt/zscaler/etc/network-connector-firewall.py
Restart=always
User=root
[Install]
WantedBy=multi-user.target`
-
Enable and start the `network-connector-firewall` service:
`$ sudo systemctl enable network-connector-firewall
$ sudo systemctl start network-connector-firewall`
-
Check the status of the `network-connector-firewall` service:
`$ systemctl status network-connector-firewall
● network-connector-firewall.service - Network Connector Firewall Rules
Loaded: loaded (/etc/systemd/system/network-connector-firewall.service; enabled; preset: disabled)
Active: active (running) since Thu 2025-08-28 20:47:07 UTC; 3min 34s ago
Main PID: 9253 (python3)
Tasks: 1 (limit: 98904)
Memory: 7.3M
CPU: 610ms
CGroup: /system.slice/network-connector-firewall.service
└─9253 python3 /usr/local/bin/network-connector-firewall.py
Aug 28 20:47:07 ip-10-3-21-9.us-west-2.compute.internal systemd[1]: Started Network Connector Firewall Rules.
Aug 28 20:47:07 ip-10-3-21-9.us-west-2.compute.internal network-connector-firewall.py[9254]: success
Aug 28 20:47:07 ip-10-3-21-9.us-west-2.compute.internal network-connector-firewall.py[9255]: success
Aug 28 20:47:08 ip-10-3-21-9.us-west-2.compute.internal network-connector-firewall.py[9256]: success`
[]This Python script is a utility that manages and maintains custom firewall configurations for a specific network setup. It interacts with firewalld through D-Bus and listens for the reloaded signal whenever firewalld reloads its rules. It executes shell commands when the reload signal is detected or during script initialization to:
- Open specific ports.** **Adds UDP ports (51820, 3784, 4784) using the `firewall-cmd` tool for enabling communication over these ports, typically used for services like VPNs or other networking tools.
- Apply traffic forwarding rules. Inserts `Nftables` rules to allow all traffic in both directions on the npwg0 interface (iifname npwg0 for incoming traffic, and oifname npwg0 for outgoing traffic). These rules are set conditionally to prevent redundant entries and ensure forwarding functionality for the interface.
The script ensures that these firewall configurations persist and are reapplied dynamically after any firewalld reload event. It runs indefinitely, monitoring signal events, unless interrupted manually. This tool is particularly useful in scenarios where maintaining consistent network rules and access is critical—such as with VPN setups, custom networking interfaces, or specific port-based services.
[]
After you have deployed the Network Connector, you can complete the following networking configurations:
- [Configure Network Time Protocol (NTP) Servers for a Network Connector](#NTP)
- [Configure Static IP Addressing for a Network Connector](#Static_IP)
- [Configure the Domain Name System (DNS) Resolver for a Network Connector](#DNS)
[]An administrator must configure a static IP address on a VM-based Network Connector.
- Log in to the Network Connector console using your admin credentials.
- View the current connection profile.
[admin@np-connector ~]$ nmcli connection show
- Modify the connection profile using the following format: <profile name> connection.id <new connection name>. For example:
`[admin@np-connector ~]$ sudo nmcli connection modify "Profile 1" connection.id LAN`
- Review the current connection profile.
`[admin@np-connector ~]$ nmcli connection show`
- Edit the profile using a static IP and a default gateway with the following format: <connection ID> ipv4.method manual ipv4.addresses <IP addresses> ipv4.gateway <gateway IP> ipv4.dns <DNS IP> ipv4.dns-search <domain name>. For example:
`[admin@np-connector ~]$ sudo nmcli connection modify LAN ipv4.method manual ipv4.addresses 172.30.1.88/24 ipv4.gateway 172.30.1.1 ipv4.dns 172.30.1.254 ipv4.dns-search company.com`
- To apply the changes, bring the connection ID back up. For example:
`[admin@np-connector ~]$ sudo nmcli connection up LAN `
- Verify the IP address.
`[admin@np-connector ~]$ ip addr show`
- Verify the default gateway.
[admin@np-connector ~]$ ip route show default
- Verify the DNS settings.
[admin@np-connector ~]$ sudo cat /etc/resolv.conf
[]To configure Network Connectors to use internal NTP servers:
- Log in to the Network Connector console using your admin credentials.
- Edit the /etc/chrony.conf file. Use an editor, such as vi.
[admin@np-connector ~]$sudo vi /etc/chrony.conf
Add your internal NTP servers to the list, for example:
server 0.zscaler.pool.ntp.org iburst
server 1.zscaler.pool.ntp.org iburst
server 2.zscaler.pool.ntp.org iburst
server 3.zscaler.pool.ntp.org iburst
- To apply the changes, restart the chrony daemon using the following command:
[admin@np-connector ~]$ systemctl restart chronyd
- To verify the NTP servers, check that NTP is working successfully using the following command:
[admin@np-connector ~]$ chronyc sources
[]DNS resolution is critical for the successful operation of the Network Connector. Network Connectors must also be able to resolve external DNS names, such as those of the ZPA cloud infrastructure.
- Log in to the Network Connector console using your admin credentials.
- View the current connection profile.
[admin@np-connector ~]$ nmcli connection show
- Modify the DNS settings using the following format: <profile name> ipv4.dns <nameserver IP>. For example:
[admin@np-connector ~]$ sudo nmcli connection modify "Profile 1" +ipv4.dns 192.168.2.241
- To apply the changes, bring the connection profile down and then back up. For example:
[admin@np-connector ~]$ sudo nmcli connection down "Profile 1"[admin@np-connector ~]$ sudo nmcli connection up "Profile 1"
- Verify the nameservers record was added.
[admin@np-connector ~]$ sudo cat /etc/resolv.conf
[]To deploy a Network Connector, you need to download the RPM package on the Network Connector] you're deploying. However, in some cases, the Network Connector might be unable to download the package, and you'll have to download it on a server instead. Choose one of the following deployment options depending on your situation.
- [Downloading the RPM Package on the Network Connector](#rpmconnector)
- [Downloading the RPM Package on a Server](#rpmserver)
[]If the Network Connector can download the RPM package:
- Log in to the Network Connector console with sudo access or directly as the root user.
- Create a file named `/etc/yum.repos.d/zscaler.repo.` Use an editor, such as vi.
[admin@np-connector ~]$ sudo vi /etc/yum.repos.d/zscaler.repo
For Red Hat Enterprise Linux 9-based deployments, enter the following content within the file:
[zscaler]
name=Zscaler Private Access Repository
baseurl=https://yum.private.zscaler.com/yum/el9
enabled=1
gpgcheck=1
gpgkey=https://yum.private.zscaler.com/yum/el9/gpg
- Install the package using the `yum install` command. For example:
[admin@np-connector ~]$ sudo yum install np-connector
If you have a proxy environment, you need to configure the proxy server IP address and proxy port in `/etc/yum.conf.` For example:
proxy=http://10.0.0.1:8080
- The Network Connector console asks for confirmation twice. Enter `y` both times and ensure that the GPG fingerprint matches, `a6fe 2422 fce7 e8ac 672e 9e51 644e a315 8765 e1dd`, as highlighted in green within the example below:
[admin@np-connector ~]$ sudo yum install np-connector
Loaded plugins: fastestmirror, langpacks
Determining fastest mirrors
* base: mirror.keystealth.org
* epel: mirrors.kernel.org
* extras: mirror.lug.udel.edu
* updates: mirrors.cat.pdx.edu
Resolving Dependencies
--> Running transaction check
---> Package np-connector.x86_64 0:25.49.4-1.el9 will be installed
--> Finished Dependency Resolution
Dependencies Resolved
================================================================================
Package               Arch        Version               Repository      Size
================================================================================
Installing:
np-connector         x86_64      25.49.4-1.el9         zscaler         1.1 M
Transaction Summary
================================================================================
Install 1 Package
Total download size: 1.1 M
Installed size: 2.9 M
Is this ok [y/d/N]: y
Downloading packages:
warning: /var/cache/yum/x86_64/7/zscaler/packages/np-connector-25.49.4-1.el9.x86_64.rpm: Header V4 RSA/SHA1 Signature, key ID 8765e1dd: NOKEY kb 00:00:01 ETA
Public key for np-connector-25.49.4-1.el9.x86_64.rpm is not installed
np-connector-25.49.4-1.el9.x86_64.rpm                                                                                              | 1.1 MB      00:00:03
Retrieving key from https://yum.private.zscaler.com/gpg
Importing GPG key 0x8765E1DD:
Userid     : "Zscaler, Inc. (External Package Repository Signing Key) <ext-pkg-repo@zscaler.com>"
Fingerprint: a6fe 2422 fce7 e8ac 672e 9e51 644e a315 8765 e1dd
From       : https://yum.private.zscaler.com/gpg
Is this ok [y/N]: y
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
Installing : np-connector-25.49.4-1.el9.x86_64                           1/1
Verifying  : np-connector-25.49.4-1.el9.x86_64                           1/1
Installed:
np-connector.x86_64 0:25.49.4-1.el9
Complete!
- Apply the Network Connector provisioning key.
- [See instructions.](#pkey_original)
- After the Network Connector provisioning key is applied, be sure to verify that the deployed Network Connector is [running and healthy](/zpa/viewing-network-connectors-dashboard%20).
- Zscaler highly recommends updating the Network Connector system software before proceeding. To learn more, see [Configuring Network Connectors](/zpa/configuring-network-connectors).
[]To deploy a Network Connector, download the RPM package on a server.
- Log in to the Network Connector console with sudo access or directly as the root user.
- Create a file named `/etc/yum.repos.d/zscaler.repo.` Use an editor, such as vi.
[admin@np-connector ~]$ sudo vi /etc/yum.repos.d/zscaler.repo
For Red Hat Enterprise Linux 9-based deployments, enter the following content within the file:
[zscaler]
name=Zscaler Private Access Repository
baseurl=https://yum.private.zscaler.com/yum/el9
enabled=1
gpgcheck=1
gpgkey=https://yum.private.zscaler.com/yum/el9/gpg
- Download the following Red Hat Enterprise Linux 9-based deployment files on a server with access:
- RPM package ([np-connector.rpm](https://yum.private.zscaler.com/yum/el9/np-connector-25.49.4-1.el9.x86_64.rpm))
- GPG public key ([https://yum.private.zscaler.com/yum/el9/gpg](https://yum.private.zscaler.com/yum/el9/gpg))
- Use the `scp` command to copy the RPM package and GPG public key to the Network Connector. For example:
$ scp np-connector-25.49.4-1.el9.x86_64.rpm admin@<Network Connector Hostname or IP Address>
$ scp gpg admin@<<Network Connector Hostname or IP Address>
- On the Network Connector console, verify that the RPM package is signed by entering the following command:
[admin@np-connector ~]$ rpm --import <GPG public key file>
- After the RPM package has been verified, enter the following command:
[admin@np-connector ~]$ rpm -i <RPM package file>
- Configure the Network Connector.
-
Edit the file `/etc/sysctl.conf` and add this setting:
`net.ipv4.ip_forward = 1`
- Save the file `/etc/sysctl.conf`.
-
In the Linux 'root' shell prompt, enter the following command:
`# sysctl -p`
-
Verify that the following entry is included in the Network Connector VM's `etc/sudoers` file.
`#includedir /etc/sudoers.d`
-
Add a firewall interface and reload it using the following commands:
`sudo firewall-cmd --zone=public --permanent --add-interface=npwg0
sudo firewall-cmd --reload`
- Apply the Network Connector provisioning key.
- [See instructions.](#pkey_duplicate)
- After the Network Connector provisioning key is applied, be sure to verify that the deployed Network Connector is [running and healthy](/zpa/viewing-network-connectors-dashboard%20).
- Zscaler highly recommends updating the Network Connector system software before proceeding. To learn more, see [Configuring Network Connectors](/zpa/configuring-network-connectors).
- []Complete the following steps if you need to enable SSH:
- Log in to the Network Connector console using your [admin credentials](/zpa/managing-deployed-connectors#Default).
After the initial boot of a Network Connector instance, it might take up to 15 minutes for the admin credentials to apply. If you receive an invalid credentials error after initial boot, wait a few minutes and try again.
- Start the SSH daemon using the following command:
[admin@np-connector ~]$ sudo systemctl start sshd
[]This command will temporarily enable SSH, but it will not persist if a reboot occurs. If you need SSH to remain enabled after a reboot, use the `sudo systemctl enable sshd` command.
- Verify the Network Connector's IP address using the following command:
[admin@np-connector ~]$ ip addr show
The configuration output should look similar to the following:
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST> mtu 1500
inet 192.0.2.1 netmask 255.255.255.128 broadcast 192.168.144.127
inet6 fe80::20c:29ff:fef5:5d43 prefixlen 64 scopeid 0x20<link>
ether 00:0c:29:f5:5d:43 txqueuelen 1000 (Ethernet)
RX packets 8504 bytes 8732964 (8.3 MiB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 4900 bytes 427768 (417.7 KiB)
TX errors 0 dropped 0 overruns 0 carrier 0 collisions 0,broadcast,running,multicast>
- SSH into the virtual machine (VM) using a standard SSH client. Using the previous example, the Network Connector IP address is 192.0.2.1:
[admin@np-connector ~]$ ssh admin@192.0.2.1
- Populate the provisioning key file.
- Stop running the Network Connector service. If the provisioning key was not detected when the Network Connector was first started, the Network Connector is in a sleep cycle and will look for the key again every 24 hours.
[admin@np-connector ~]$ sudo systemctl stop np-connector
- Create a provisioning key file with 644 permissions at `/opt/zscaler/var/provision_key`. For example:
[admin@np-connector ~]$ sudo touch /opt/zscaler/var/provision_key
[admin@np-connector ~]$ sudo chmod 644 /opt/zscaler/var/provision_key
- Copy the provisioning key from the ZPA Admin Portal, paste it into the file, and save. Use an editor, such as vi.
[admin@np-connector ~]$ sudo vi /opt/zscaler/var/provision_key
If you are using vi, make sure it is in insert mode before you paste the key into the file.
If you are unfamiliar with the vi editor, you can also use the following `echo` and `tee` commands to paste in the provisioning key:
echo "<Network Connector Provisioning Key>" | sudo tee /opt/zscaler/var/provision_key
Make sure that the key is within double quotes (").
-
Enter the following command to verify the file's content:
`[admin@np-connector ~]$ sudo cat /opt/zscaler/var/provision_key`
The output should return the provisioning key you entered in the previous step.
-
Start the np-connector service.
`[admin@np-connector ~]$ sudo systemctl start np-connector`
-
Verify the status of the np-connector service.
`[admin@np-connector ~]$  sudo systemctl status np-connector`
-
After the Network Connector is enrolled, disable SSH using the following command:
`[admin@np-connector ~]$ sudo systemctl stop sshd`
However, if you used the `sudo systemctl enable sshd` command when applying the [Network Connector provisioning key](#enable-ssh), then enter the `sudo systemctl disable sshd` command.
In the ZPA Admin Portal, the Network Connector appears as “up” and “connected”.
[]To check the status of a Network Connector:
- Go to **VPN (for Legacy Apps)** > **Network Connector** > **Network Connectors**.
- Check that the Network Connector you deployed appears in the table of configured Network Connectors.
[]On Zscaler-provided virtual appliances, SSH is not enabled by default. It is required for a short time to configure the provisioning key for the Network Connector. Complete the following steps to temporarily enable SSH:
- Log in to the Network Connector console using your [admin credentials](/zpa/managing-deployed-connectors#Default).
After the initial boot of a Network Connector instance, it might take up to 15 minutes for the admin credentials to apply. So, if you receive an invalid credentials error after the initial boot, wait a few minutes and try again.
- Start the SSH daemon using the following command:
[admin@np-connector ~]$ sudo systemctl start sshd
This command will temporarily enable SSH, but it will not persist if a reboot occurs. If you need SSH to remain enabled after a reboot, use the `sudo systemctl enable sshd` command.
- Verify the Network Connector's IP address using the following command:
[admin@np-connector ~]$ ip addr show
The configuration output should look similar to the following:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
valid_lft forever preferred_lft forever
inet6 ::1/128 scope host
valid_lft forever preferred_lft forever
2: ens192: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default glen 1000
link/ether 00:50:56:9b:f4:6d bird ff:ff:ff:ff:ff:ff
altname enp11s0
inet 10.66.13.249/24 bird 10.66.13.255 scope global dynamic noprefixroute ens192
valid_lft 690049sec preferred_lft 690049sec
inet6 2605:4300:fe00:420d:c724:58a4:2cea:c0fc/64 scope global dynamic noprefixroute
valid_lft 2591936 sec preferred_lft 604736sec
inet6 fe80::fbe0:b0a6:5347:62dc/64 scope link noprefixroute
valid_lft forever preferred_lft forever
- SSH into the virtual machine (VM) using a standard SSH client. Using the previous example, the Network Connector IP address is 192.0.2.1:
[admin@np-connector ~]$ ssh admin@192.0.2.1
- Populate the provisioning key file.
- Stop the running np-connector service. If the provisioning key was not detected when the Network Connector was first started, the Network Connector is in a sleep cycle and will look for the key again every 24 hours.
[admin@np-connector ~]$ sudo systemctl stop np-connector