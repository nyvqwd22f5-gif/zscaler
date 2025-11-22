# Managing Objects
Source: https://help.zscaler.com/zero-trust-branch/managing-objects
PDF: https://help.zscaler.com/pdf/com/en/1525226.pdf

Zero Trust Branch supports several different types of objects (e.g., devices, networks, ports, DNS gateways, etc.), and allows you to create groups of objects so that you can enforce security policies dynamically to prevent lateral movement of threats.
To manage objects:
- Go to **Resources > Objects**.
-
Click **Add **to add a new object group, or click the **Gear **icon and select **Edit **to modify an existing object.
[See image.](#add-object-image)
- In the **Add **or **Edit **panel, define the object group as needed. See the following sections for descriptions of the group types:
- [Device](#device)
- [Domains](#domain)
- [DNS Gateways](#dns)
- [Network](#network)
- [MAC](#mac)
- [Port](#port)
- [Time Schedule](#time)
- [Zone](#zone)
- [SaaS Apps](#saas)
[]A device group provides the ability to group devices by several attributes:
- **Name: **Enter a name for this device group.
- **Autonomous**: If enabled, newly discovered assets matching the defined attributes are automatically added to the group.
- **Device Attribute:** Select an item from the drop-down menu and define additional parameters for that attribute:
- **Manufacturers**, **Operating System**, **Services:** Select the manufacturer of this device in the **Attribute Value** field.
- **Network**: Enter the network address of this device in the **Attribute Value** field.
- **Operating System:** Select the OS of this device in the **Attribute Value** field.
- **Services:** Select the type of service for this device (e.g., printer, scanner, etc.) in the **Attribute Value** field.
- **Tags**: Select one or more tags to identify groups of devices and click **Add**. For instance, all Windows devices can be grouped using the tag `type:windows`. You can also create custom tags to organize devices. To learn more, see [Working with Tags](/zero-trust-branch/working-with-tags).
[See image.](#add-device-image)
[]A domain group provides the specific domains that you can use as a destination in a DNS policy rule, or in other policy engines. In addition to custom domains, you can use predefined domain objects, such as **All Zscaler App Segments** and **All Zscaler Domains**, to support one or more domains.
- **Name: **Enter a name for this group.
- **Domains**: Enter one or more wildcard domains (e.g., *.example.com) or FQDNs (host.example.com). Top-level domains (e.g., example.com) are not supported.
- **Any Domain:** Select this checkbox to make this object match any domain (i.e., *.*).
[See image.](#add-domain-image)
[]A DNS server group supports the addition of one or more DNS servers that can be used as redirect (forwarding) targets in a DNS policy rule. To learn more, see [Configuring Site DNS Policies](/zero-trust-branch/configuring-site-dns-policies)
- **Name: **Enter a name for this group.
- **DNS Servers**: Enter one or more IP addresses.
[See image.](#add-dns-image)
[]A network group supports both a CIDR block and FQDN.
Enter a name for this group in the **Name **field, then enter the network address. Non-CIDR block IP address ranges (e.g., 192.168.0.2–192.168.0.10) are converted to CIDR notation.
When an FQDN is added to a network group, the branch appliance resolves the FQDN locally and adds the IP addresses to the group. The branch appliance also honors the Time to Live (TTL) value of the DNS records and refreshes when the TTL expires.
You can combine multiple network groups into a single group by selecting them in the **Member Groups** field. This feature is useful when creating a single policy for multiple network objects.
[See image.](#add-network-image)
[]A MAC group supports the addition of static MAC addresses. Enter a name for this group in the **Name **field, then enter one or more MAC addresses using a colon (`:`) as a separator (e.g., `20:7B:D2:24:33:83`).
You can combine multiple MAC groups into a single group by selecting them in the **Member Groups** field. This feature is useful when creating a single policy for multiple MAC objects.
[See image.](#add-mac-image)
[]A port group supports ports in several formats:
- protocol:port-number pairs (e.g., `udp:8080`)
- protocol:port-range pairs (e.g., `TCP:1024-1030`)
- Well-known protocols or ports (e.g., `bgp`)
Enter a name for the group in the **Name **field. Use a comma after each entry to add it to the list (e.g., `udp:8080, TCP:1024-1030`) so you don't have to click **Add **for each entry.
[See image.](#add-port-image)
[]A time schedule group allows you to specify a group of absolute and periodic time ranges:
- **Name: **Enter a name for this group.
- **Time Zone**: Select the time zone used for this group.
- **Absolute Time Range**: Select the start and end dates and times to create a specific date and time range.
- **Periodic Time Range**: Select the days and time schedules for a period time range (e.g., every Monday, Wednesday, and Friday).
Click **Add Time Range** to add each time range to the group.
[See image.](#add-time-image)
[]A zone group allows you to group one or more networks of a single type together:
- **Zone type: **Select the type of network for this zone:
- **LAN Zone**: Local area network zone.
- **WAN Zone**: Wide area network zone.
- **Management Zone**: Management entities zone.
- **HA Zone**: High availability (HA) network zone.
- **Name**: Enter a name for the group.
[See image.](#add-zone-image)
[]A SaaS Apps group specifies Software as a Service (SaaS) apps to be used as destinations for policy-based routing (PBR) based on applications.
Enter a name for the group in the **Name **field, then select one or more apps from the **SaaS Apps** drop-down menu.
[See image.](#add-saas-image)
[]![The Objects page showing the Add Group drop-down menu.](/downloads/device-segmentation/administration/resources/managing-objects/add-object.png)
[]![The Objects page showing the Add Device panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-device.png)
[]![The Objects page showing the Add Domain panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-domain.png)
[]![The Objects page showing the Add DNS Gateways panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-dns.png)
[]![The Objects page showing the Add Network panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-network.png)
[]![The Objects page showing the Add MAC panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-mac.png)
[]![The Objects page showing the Add Port panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-port.png)
[]![The Objects page showing the Add Time Schedule panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-time-sched.png)
[]![The Objects page showing the Add Zone panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-zone.png)
[]![The Objects page showing the Add SaaS Apps panel.](/downloads/device-segmentation/administration/resources/managing-objects/add-saas.png)