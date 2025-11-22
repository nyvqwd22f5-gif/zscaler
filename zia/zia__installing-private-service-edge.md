# Installing Private Service Edge
Source: https://help.zscaler.com/zia/installing-private-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1401246.pdf

Upon receipt of the hardware, install your pair of Private Service Edges according to the instructions provided. Both Private Service Edges must be installed in the same location.
Zscaler also offers Advanced DLP Private Service Edges as a complementary dedicated hardware role within the Zscaler cloud that can be deployed to provide on-premises support for Private Service Edge customers who also require Advanced DLP product features, such as [Exact Data Match (EDM)](/zia/about-exact-data-match) and [Indexed Data Match (IDM)](/zia/about-indexed-document-match). To learn more, see [Understanding Advanced DLP Private Service Edge](/zia/understanding-advanced-dlp-private-service-edge) and [Installing Advanced DLP Private Service Edge](/zia/installing-advanced-dlp-private-service-edge).
Installation Guides
- [Private Service Edge 3 Installation Guide](#HW3)
- [Private Service Edge 5 Installation Guide](#HW6)
- [Dedicated Load Balancer Installation Guide](#pse-LB)
After Installation
After installation is complete, notify Zscaler by sending an email to your assigned Project Manager on the Zscaler Cloud Operations team.
Your company name and Private Service Edge location must be included in the email.
When we receive the email from your organization, Zscaler Cloud Operations:
- Verifies remote connectivity.
- Installs the Zscaler software.
- Activates your Private Service Edges in the Zscaler cloud.
- Activates the proactive monitoring capability.
- Tests and ensures that the Private Service Edges are ready for service.
After these actions are completed, you are notified via email.
- [][Package Contents](#package-HW3)
- [Installation](#install-HW3)
[]The package contains the following items:
- 1 Private Service Edge 3
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- Up to 7 CAT6 Ethernet cables
[]To install the Private Service Edge 3:
- Rack the Private Service Edge using the included rail kit. Private Service Edge requires 1U of space and is 17.2" wide.
- Connect the CAT6 Ethernet network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
-
**1 Gb Zscaler Service Ports**: Used by the Zscaler service for both incoming and outgoing web traffic. It hosts the IP address of a Private Service Edge instance.
The VPN service port should only be cabled if IPSec tunnel traffic is required.
- Connect the power cables according to your internal specifications. Private Service Edge uses universal power supply adapters. The Private Service Edge powers on automatically and the LED light at the front of the box turns green. If the Private Service Edge does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the Zscaler Cloud Operations project manager for assistance.
![Diagram of Service Edge 3 hardware](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/private-zens/installing-private-zens/Private-Service-Edge-3-Port-Diagram.png)
- [][Package Contents](#package-HW6)
- [Installation](#install-HW6)
[]The package contains the following items:
- 1 Private Service Edge 5
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- Up to 3 CAT6 Ethernet cables
-
2 10G SFP+ / SFP Optic Modules or Direct Attach Cables
To learn more about compatible cables and optics, see [Compatible SFP+ Modules, SFP Modules, and Cables for Intel® Ethernet Server Adapter X710 Series](https://www.intel.com/content/www/us/en/support/articles/000007045/network-and-i-o/ethernet-products.html).
[]To install the Private Service Edge 5:
- Rack the Private Service Edge using the included rail kit. Private Service Edge requires 1U of space and is 17.2" wide.
- Connect the network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
-
**1 Gb MTS Port**: (Optional) Used for Message Transport System.
The MTS port is only required for a standalone cluster of 3 x Private Service Edge 5 (without dedicated load balancers).
- **10 Gb Zscaler Service Ports**: Used by the Zscaler service for both incoming and outgoing web traffic. It hosts the IP address of a Private Service Edge instance.
- Connect the power cables according to your internal specifications. Private Service Edge uses universal power supply adapters. The Private Service Edge powers on automatically and the LED light at the front of the box turns green. If the Private Service Edge does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the Zscaler Cloud Operations project manager for assistance.
![Diagram of the Service Edge 5 ports](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/private-zens/installing-private-zens/Private-Service-Edge-5-Port-Diagram.png)
- [][Package Contents](#package-pse-LB)
- [Installation](#install-pse-LB)
[]The following items are included:
- 1 Dedicated Load Balancer (LB)
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- 3 CAT6 Ethernet cables
-
up to 6 10G SFP+ / SFP Optic Modules or Direct Attach Cables
To learn more about compatible cables and optics, see [Compatible SFP+ Modules, SFP Modules, and Cables for Intel® Ethernet Server Adapter X710 Series](https://www.intel.com/content/www/us/en/support/articles/000007045/network-and-i-o/ethernet-products.html).
[]To install the LB:
- Rack the LB using the included rail kit. LBs require 1U of space and are 17.2" wide.
- Connect the network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
-
**1 Gb MTS Port**: (Optional) Used for Message Transport System.
The port is required only for throughput exceeding 5 Gbs.
- **10 Gb VIP 1 Ports **(te2 and te6): Bundled via LACP.
- **10 Gb VIP 2 Ports **(te3 and te7): (Optional) Bundled via LACP.
-
**10 Gb VIP 3 Ports** (te4 and te8): (Optional) Bundled via LACP.
The LACP configuration is not required at the Private Service Edge installation time, but it is required after Zscaler Private Service Edge provisioning. The Zscaler Cloud Operations project manager lets you know when to configure it.
- Connect the power cables according to your internal specifications. LBs use universal power supply adapters. The LB powers on automatically and the LED light at the front of the box turns green. If the LB does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the Zscaler Cloud Operations project manager for assistance.
![LB Port Diagram](/downloads/zia/documentation-knowledgebase/forwarding-your-traffic/zscaler-enforcement-nodes-zens/private-zens/installing-private-zens/LB-Port-Diagram.png)