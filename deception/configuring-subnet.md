# Configuring a Subnet
Source: https://help.zscaler.com/deception/configuring-subnet
PDF: https://help.zscaler.com/pdf/com/en/1531286.pdf

Before you configure a subnet or VLAN, you must pass it to one of the decoy interfaces on the Decoy Connector virtual machine (VM). You can use the subnet or VLAN to create network decoys on the associated VLAN.
To configure a subnet:
- Go to **Settings** >** Interfaces**.
-
Click **Add Subnet**.
[See image.](#add-subnet)
-
In the **Subnet Details** window:
- **Interface**: Select a Decoy Connector's network interface card (NIC) on which the VLAN or subnet is passed.
- **VLAN ID**: Enter an ID for the VLAN that is trunked to the selected Decoy Connector's NIC. Keep this field blank if the VLAN is untagged or there is no VLAN trunked to the interface.
- **DHCP**: Enable if DHCP is available on the VLAN or subnet.
- **Name**: Enter the name of the VLAN or subnet.
- **Gateway/Mask**: Enter the default gateway for the VLAN or subnet with the CIDR details in the `<Gateway-IP>/<CIDR>` format. For example, if the gateway is 192.0.2.1 and the network mask is 24, enter either `192.0.2.1/24` or `192.0.2.1/255.255.255.0`. These details are not required if **DHCP** is enabled.
- **IPv6 Enabled**: Enable if the subnet of VLAN supports IPv6 networking. This allows you to deploy decoys in IPv6 networks.
- **IPv6 DHCP**: Enable if DHCP is available on the IPv6 VLAN or subnet.
- **IPv6 Gateway/Mask**: Enter the default gateway for the IPv6 VLAN or subnet with the CIDR details in the `<Gateway-IPv6>/<CIDR>` format. For example, if the gateway is 2001:db8::1 and the network prefix length is /64, enter either `2001:db8::1/64` or specify the appropriate subnet mask. These details are not required if **IPv6 DHCP** is enabled.
- **DNS Servers**: (Optional) Enter the IP address of the DNS server that the systems in the VLAN or subnet can access.
[See image.](#configure-subnet-details)
-
Click **Save**.
The subnet or VLAN is added.
[]![Adding a subnet in the Interfaces tab located in the Topology page](/downloads/deception/settings/topology/configuring-a-subnet/deception-add-subnet-button.png)
[]![Configure subnet details](/downloads/deception/settings/topology/configuring-a-subnet/deception-subnet-details.png)