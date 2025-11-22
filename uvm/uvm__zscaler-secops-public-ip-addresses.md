# Zscaler SecOps Public IP Addresses
Source: https://help.zscaler.com/uvm/zscaler-secops-public-ip-addresses
PDF: https://help.zscaler.com/pdf/com/en/1527781.pdf

To ensure seamless connectivity and uninterrupted access to essential resources, you can allowlist the public IP addresses used by outgoing traffic from the Zscaler Security Operations (SecOps) platform and its applications (e.g., UVM, AEM). These IP addresses serve as the source for all egress traffic originating from the Zscaler tenant.
Add the following IP addresses associated with your instance's region to your firewall's allowlist to ensure uninterrupted access to the required resources.
[](https://config.zscaler.com/zscalertwo.net/hubs)
| **Region** | **IP Addresses** |
| ---------- | ---------------- |
| **US** | 3.137.47.190/323.15.110.62/323.129.232.141/32 |
| **EU** | The recommended IP addresses listed in Zscaler Hub IP Addresses |