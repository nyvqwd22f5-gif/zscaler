# Network Connector Deployment Prerequisites
Source: https://help.zscaler.com/zpa/network-connector-deployment-prerequisites
PDF: https://help.zscaler.com/pdf/com/en/1517026.pdf

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