# Adding EDNS Client Subnet (ECS) Prefixes
Source: https://help.zscaler.com/zia/adding-edns-client-subnet-ecs-prefixes
PDF: https://help.zscaler.com/pdf/com/en/1449946.pdf

In the ZIA Admin Portal, you can configure a list of EDNS Client Subnet (ECS) prefixes and designate one of them to be embedded in DNS queries when they arrive at the ZIA Service Edges (Public, Private, or Virtual).
- A maximum of 128 ECS prefixes, including the default prefix, is supported for an organization.
- After configuring the ECS prefixes, you must enable the ECS option and designate an ECS prefix to be embedded into DNS queries using the [Advanced Settings](/zia/configuring-advanced-settings#ecs-prefix).
- Zscaler supports ECS prefixes corresponding to the IPv4 family only. ECS prefixes corresponding to the IPv6 family in client DNS queries are not processed by Zscaler.
To add an ECS prefix:
- Go to **Administration** > **EDNS Client Subnet Prefix Objects**.
- Click **Add ECS Prefix**.
The **Add ECS Prefix** window appears.
- In the **Add ECS Prefix** window:
- **Name**: Enter a unique name for the ECS prefix. Only alphanumeric characters are allowed and the name cannot exceed 255 characters.
- **ECS Prefix**: Select how you want to configure the ECS prefix from the following options and specify a value:
- **Prefix Length**: Select the length of the client’s IP address (IPv4) that can be specified for the ECS option in DNS queries. For example, if /24 is selected and the client’s IP address is 2.2.2.2, the Client Subnet value would be 2.2.2.0. The Zscaler service supports a prefix length range of /20 to /24 (the full IP address).
- **Static Prefix**: Specify a static prefix (IPv4 only) with the subnet mask that must be used for the ECS option in DNS queries. For example, if you specify 2.2.2.2/24, the Client Subnet value would be 2.2.2.0. This prefix can be a private or a public IP address that can be recognized by the DNS resolver used by your organization.
The prefix must be of an appropriate length to support the geo-location of the client without unnecessarily exposing the client’s IP network information. Too long prefixes may be rejected by certain DNS resolvers, whereas very short prefixes may not be sufficient to geo-locate the clients initiating the DNS query.
- **Retain ECS prefix if present**: Enable this option if the current ECS prefix in the DNS query must be retained and not be overridden by the configured prefix.
- **Description**: (Optional) Provide additional information about the ECS prefix. The description cannot exceed 255 characters.
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
[See image.](#add-ecs-prefix)
[]![A screenshot of the Add ECS Prefix window](/downloads/zia/traffic-forwarding/adding-ecs-prefixes/add-ecs-prefix-window.png)