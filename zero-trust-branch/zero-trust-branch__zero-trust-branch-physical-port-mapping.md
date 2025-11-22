# Zero Trust Branch Physical Port Mapping
Source: https://help.zscaler.com/zero-trust-branch/zero-trust-branch-physical-port-mapping
PDF: https://help.zscaler.com/pdf/com/en/1532276.pdf

This article depicts the physical ports on Zero Trust Branch appliances and identifies their interface names, port types, and roles.
For appliance specifications, refer to the [Zero Trust Branch Data Sheet](https://www.zscaler.com/resources/data-sheets/zscaler-zero-trust-branch.pdf).
- [Zscaler ZT400](#ZT400)
- [Zscaler ZT600](#ZT600)
- [Zscaler ZT800](#ZT800)
- [Zscaler ZT8010](#ZT8010)
[]This section describes the physical port mapping on the ZT400 appliance.
![ZT400 appliance physical port diagram that identifies the console port on the back of the appliance](/downloads/zero-trust-branch/deploying-zero-trust-branch/zero-trust-branch-physical-port-mapping/dia_hw_ZT400-Rear_callouts.png)
![ZT400 appliance physical port diagram that identifies four interface ports on the front of the appliance ](/downloads/zero-trust-branch/deploying-zero-trust-branch/zero-trust-branch-physical-port-mapping/dia_hw_ZT400-Front_callouts.png)
| Port | Interface | Port Type | Role |
| ---- | --------- | --------- | ---- |
| C | Console | RJ45 | Serial console |
| 1 | GE1/enp4s0 | 1GbE RJ45 | Management |
| 2 | GE2/enp5s0 | 1GbE RJ45 | LAN or WAN |
| 3 | GE3/enp6s0 | 1GbE RJ45 | WAN |
| 4 | GE4/enp7s0 | 1GbE RJ45 | LAN or high availability (HA) (when appliances are running in a cluster) |
[]This section describes the physical port mapping on the ZT600 appliance.
![ZT600 appliance physical port diagram that identifies the console port and six interface ports](/downloads/zero-trust-branch/deploying-zero-trust-branch/zero-trust-branch-physical-port-mapping/dia_hw_ZT600_callouts.png)
| Port | Interface | Port Type | Role |
| ---- | --------- | --------- | ---- |
| C | Console | RJ45 | Serial console |
| 1 | GE1/enp3s0 | 1GbE RJ45 | Management |
| 2 | GE2/enp2s0 | 1GbE RJ45 | LAN |
| 3 | GE3/eno1 | 1GbE RJ45 | LAN |
| 4 | GE4/eno2 | 1GbE RJ45 | LAN or high availability (HA) (when appliances are running in a cluster) |
| 5 | GE5/eno3 | 1GbE RJ45 | WAN |
| 6 | GE6/eno4 | 1GbE RJ45 | WAN |
[]This section describes the physical port mapping on the ZT800 appliance.
![ZT800 appliance physical port diagram that identifies the console port and eight interface ports](/downloads/zero-trust-branch/deploying-zero-trust-branch/zero-trust-branch-physical-port-mapping/dia_hw_ZT800-Rear_callouts.png)
| Port | Interface | Port Type | Role |
| ---- | --------- | --------- | ---- |
| C | Console | RJ45 | Serial console |
| 1 | GE1/enp2s0f0 | 1G SFP | LAN |
| 2 | GE2/enp2s0f1 | 1G SFP | WAN |
| 3 | GE3/enp2s0f2 | 1GbE RJ45 | Management |
| 4 | GE4/enp2s0f3 | 1GbE RJ45 | LAN or high availability (HA) (when appliances are running in a cluster) |
| 5 | GE5/enp8s0f0 | 1GbE RJ45 | LAN |
| 6 | GE6/enp8s0f1 | 1GbE RJ45 | LAN |
| 7 | GE7/enp10s0f0 | 1GbE RJ45 | WAN |
| 8 | GE8/enp10s0f1 | 1GbE RJ45 | WAN |
[]This section describes the physical port mapping on the ZT8010 appliance.
![ZT8010 appliance physical port diagram that identifies the console port and 18 interface ports](/downloads/zero-trust-branch/deploying-zero-trust-branch/zero-trust-branch-physical-port-mapping/dia_hw_ZT8010_callouts.png)
| Port | Interface | Port Type | Role |
| ---- | --------- | --------- | ---- |
| C | Console | RJ45 | Serial console |
| 1 | GE1/eno1 | 1GbE RJ45 | Management |
| 2 | GE2/enp1s0 | 1GbE RJ45 | WAN |
| 3 | GE3/ens84f3 | 1GbE RJ45 | LAN |
| 4 | GE4/ens84f2 | 1GbE RJ45 | LAN or high availability (HA) (when appliances are running in a cluster) |
| 5 | GE5/ens84f1 | 1GbE RJ45 | LAN |
| 6 | GE6/ens84f0 | 1GbE RJ45 | LAN |
| 7 | XE7/eno4 | 10G SFP+ | WAN |
| 8 | XE8/eno5 | 10G SFP+ | WAN |
| 9 | XE9/eno2 | 10G SFP+ | WAN |
| 10 | XE10/eno3 | 10G SFP+ | WAN |
| 11 | GE11/ens83f0 | 1GbE RJ45 | LAN |
| 12 | GE12/ens83f1 | 1GbE RJ45 | LAN |
| 13 | GE13/ens83f2 | 1GbE RJ45 | LAN |
| 14 | GE14/ens83f3 | 1GbE RJ45 | LAN |
| 15 | XE15/ens5f3 | 10G SFP+ | LAN |
| 16 | XE16/ens5f2 | 10G SFP+ | LAN |
| 17 | XE17/ens5f1 | 10G SFP+ | LAN |
| 18 | XE18/ens5f0 | 10G SFP+ | LAN |