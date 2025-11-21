# Creating an Internal Decoy
Source: https://help.zscaler.com/deception/creating-internal-network-decoy
PDF: https://help.zscaler.com/pdf/com/en/1531283.pdf

[Watch a video on Creating an Internal Decoy.](https://fast.wistia.net/embed/iframe/i113pmpxyt)
Internal decoys are decoy network assets that mimic servers, databases, and other internal applications in your network environment that are frequently targeted during scanning and lateral movement.
Prerequisites
[]Before creating an Internal decoy, Zscaler highly recommends reading the following information and allocating the resources, where applicable:
- Deploy a Decoy Connector on any of the supported platforms:
- [VMware vSphere Hypervisor (ESXi)](/deception/decoy-connector-deployment-guide-vmware)
- [Microsoft Hyper-V](/deception/decoy-connector-deployment-guide-microsoft-hyper-v)
- [Microsoft Azure](/deception/decoy-connector-deployment-guide-microsoft-azure)
- [Amazon Web Services (AWS)](/deception/decoy-connector-deployment-guide-aws)
- Configure VLANs or subnets where you want to place the decoys. The VLANs or subnets must be trunked or passed through the virtual NICs of the Decoy Connector. To learn more, see [Configuring a Subnet](/deception/configuring-subnet).
- Make sure that you have free IP addresses for trunked VLANs or subnets. Zscaler recommends two IP addresses per VLAN or subnet.
Zscaler recommends that you obtain information about your network, such as the type of network segment, hostname convention, and common services running on systems in the network segment.
Creating an Internal Decoy
To create an Internal decoy:
- [Stop the decoys](/deception/starting-and-stopping-decoys#stop-decoys).
- Go to **Deceive** > **Network Decoys** > **Internal**.
-
Click **Add Decoys**.
[See image.](#add-internal-network-decoy)
- []On the **Network Decoy Detail** page, under the **General** tab:
- **Enabled**: Select to enable the internal decoy.
-
**Personality**: Select a decoy personality based on the network segment.
When you select a decoy personality, the **Hostname/FQDN**, **MAC**, and **Services** fields are automatically configured to reflect the selected personality.
- **Decoy Connector**: Select a Decoy Connector to host the decoy.
- **Network Segment/Subnet**: Select a network where you want to place the decoy.
- **Network Decoy Groups**: Select an existing decoy group, or click **Create Decoy Group** to create a new decoy group.
- **Hostname/FQDN**: This field is automatically populated. You can click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate another hostname or FQDN suggestion, or manually enter a hostname or FQDN of your choice.
- **MAC**: This field is automatically populated. However, you can select a system manufacturer or click the **Autogenerate** icon (![Autogenerate icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-auto-generate-icon.png)
) to generate a manufacturer's name. Zscaler Deception automatically generates a MAC address that belongs to the manufacturer. You can also manually enter a MAC address of your choice.
-
**IP**: Enter a free IP address.
Keep this field blank if the selected network has Dynamic Host Configuration Protocol (DHCP) enabled.
-
**IPv6 Enabled**: Select and then enter an unused and unique IPv6 address in the text field.
You can only configure IPv6 if you select an IPv6 subnet in the **Network Segment/Subnet** field.
[See image.](#network-decoy-details)
- Click the **Services** tab to view, customize, enable, or disable the services that the network decoy will host. To learn more, see [Configuring Services for a Network Decoy](/deception/configuring-services-network-decoy).
- Click the **Active Directory** tab to add the decoy to an active directory (AD) as a domain-joined system. To learn more, see [Adding a Network Decoy to Active Directory](/deception/adding-network-decoy-active-directory).
-
Click **Submit**.
The Internal decoy is added. However, the red status icon (![Red decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-red-status-icon.png)
) next to the decoy indicates that the decoy is inactive and not yet deployed.
[See image.](#decoy-inactive-status)
- [Start the decoys](/deception/starting-and-stopping-decoys#start-decoys).
- Go to **Deceive** > **Network Decoys** > **Internal**.
-
Verify the Internal decoy deployment status. If it is successful, the status icon turns green (![Green decoy deployment status icon](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-green-status-icon.png)
).
[See image.](#decoy-active)
After the Internal decoy is created, you can [test](/deception/testing-network-decoy) it to simulate an attack.
[]![Add a decoy option](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-add-internal-decoy-5.png)
[]![Configure an internal network decoy](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-config-internal-decoy-5.png)
[]![Internal network decoy inactive status](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-internal-decoy-inactive-6.png)
[]![Internal network decoy active status](/downloads/deception/deceive/network-decoys/creating-internal-network-decoy/zscaler-deception-internal-decoy-active-6.png)