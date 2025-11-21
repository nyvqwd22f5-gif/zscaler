# Understanding Protection Solutions
Source: https://help.zscaler.com/zero-trust-branch/understanding-protection-solutions
PDF: https://help.zscaler.com/pdf/com/en/1509976.pdf

Zero Trust Branch offers several solutions tailored to meet the unique security and isolation requirements of highly sensitive or regulated organizations. The three solutions, Airgap, Airgap-Lite, and Airgap+, address varying levels of network isolation and functionality needs.
When you add or edit an asset, you can choose one of these solutions in the Protection drop-down menu. To learn more, see[ Managing Your Assets](/zero-trust-branch/managing-your-assets).
- **Airgap**
- Behavior: Assigns a /32 network mask to endpoints, giving each device its own unique IP address and enabling admins to enforce device-level isolation. Admins can use firewall policies to explicitly prevent direct communication between hosts and effectively create a secure "network of one."
- Use Case: Ideal for environments that require complete isolation between endpoints, ensuring all traffic routes through the Zero Trust Branch appliance for inspection and enforcement.
- Challenge: Some systems might not support /32 masks due to hardware or software limitations. In such environments where the /32 subnet mask is not supported, the admins can choose Airgap+ or Airgap-Lite (if full isolation is not a strict requirement) mode.
-
**Airgap-Lite**
- Behavior: Uses the same subnet mask as the one the DHCP server provides, which simplifies integration in environments where endpoints need to communicate directly without routing all traffic through the gateway.
- Use Case: Suitable for systems or networks where full isolation is not a strict requirement.
- Trade-Off: Reduces isolation as compared to Airgap.
To learn more, see [Configuring Airgap-Lite Mode for Assets](/zero-trust-branch/configuring-protection-mode-assets).
- **Airgap+**
- Behavior: Implements micro-subnets by supporting subnet masks between /27 and /30. Devices within the same micro-subnet can communicate directly without routing through the Zero Trust Branch appliance. Traffic between different micro-subnets or external destinations is routed through the gateway for inspection and enforcement.
- Use Case: Provides a balance between complete isolation and full subnet communication, which is ideal for environments needing some level of local communication while still enforcing Zero Trust Branch policies for external traffic.
- Trade-Off: Adds configuration and maintenance complexity as multiple subnets are managed.
- Requirements:
- The Zero Trust Branch appliance must operate in server mode for the associated VLAN(s).
- Available starting with Airgap OS 7.7.6.