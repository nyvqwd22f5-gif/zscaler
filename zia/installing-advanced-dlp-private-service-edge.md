# Installing Advanced DLP Private Service Edge
Source: https://help.zscaler.com/zia/installing-advanced-dlp-private-service-edge
PDF: https://help.zscaler.com/pdf/com/en/1529877.pdf

Upon receipt of the hardware, install your pair of Advanced DLP Private Service Edges according to the instructions provided. Both servers must be installed in the same location alongside your standard Private Service Edges.
Installation Guides
- [Advanced DLP Private Service Edge 3 Installation Guide](#AHW3)
- [Advanced DLP Private Service Edge 5 Installation Guide](#AHW6)
- [Dedicated Load Balancer Installation Guide](#pse-LB)
After Installation
After installation is complete, notify Zscaler by sending an email to the assigned Zscaler Cloud Operations project manager.
Your company name and Advanced DLP Private Service Edge location must be included in the email.
When we receive the email from your organization, Zscaler Cloud Operations:
- Verifies remote connectivity.
- Installs the Zscaler software.
- Activates your Advanced DLP Private Service Edges in the Zscaler cloud.
- Activates the proactive monitoring capability.
- Tests and ensures that the Advanced DLP Private Service Edges are ready for service.
After these actions are completed, you are notified via email.
- [][Package Contents](#package-AHW3)
- [Installation](#install-AHW3)
[]The package contains the following items:
- 1 Advanced DLP Private Service Edge 3
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- Up to 6 CAT6 Ethernet cables
[]To install the Advanced DLP Private Service Edge 3:
- Rack the Advanced DLP Private Service Edge using the included rail kit. Each Advanced DLP Private Service Edge requires 1U of space and is 17.2" wide.
- Connect the CAT6 Ethernet network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
- **1 Gb Zscaler Service Ports**: Used by the Zscaler service for both incoming and outgoing web traffic. It hosts the IP address of an Advanced DLP Private Service Edge instance.
- Connect the power cables according to your internal specifications. All Zscaler devices use universal power supply adapters. The Advanced DLP Private Service Edge should power on automatically and the LED light at the front of the box should turn green. If the Advanced DLP Private Service Edge does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the assigned Zscaler Cloud Operations project manager for assistance.
![Diagram of Service Edge 3 hardware](/downloads/zia/traffic-forwarding/service-edges/private-service-edge/understanding-private-service-edge/Installing%2001.png)
- [][Package Contents](#package-AHW6)
- [Installation](#install-AHW6)
[]The package contains the following items:
- 1 Advanced DLP Private Service Edge 5
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- 2 CAT6 Ethernet cables
- 2 10G SFP+ / SFP Optic Modules or Direct Attach Cables
To learn more about compatible cables and optics, refer to the [Intel documentation](https://www.intel.com/content/www/us/en/support/articles/000007045/network-and-i-o/ethernet-products.html).
[]To install the Advanced DLP Private Service Edge 5:
- Rack the Advanced DLP Private Service Edge using the included rail kit. Each Advanced DLP Private Service Edge requires 1U of space and is 17.2" wide.
- Connect the network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
- **10 Gb Zscaler Service Ports**: Used by the Zscaler service for both incoming and outgoing web traffic. It hosts the IP addresses of multiple Advanced DLP Private Service Edge instances.
- Connect the power cables according to your internal specifications. All Zscaler devices use universal power supply adapters. The Advanced DLP Private Service Edge should power on automatically and the LED light at the front of the box should turn green. If the Advanced DLP Private Service Edge does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the assigned Zscaler Cloud Operations project manager for assistance.
![Diagram of the Service Edge 5 ports](/downloads/zia/traffic-forwarding/service-edges/private-service-edge/understanding-private-service-edge/Installing%2002.png)
- [][Package Contents](#package-pse-LB)
- [Installation](#install-pse-LB)
[]The following items are included:
- 1 Dedicated Load Balancer (LB)
- 1 set of snap in rails
The following items are not included, but are required:
- 2 power cables
- 3 CAT6 Ethernet cables
- up to 6 10G SFP+ / SFP Optic Modules or Direct Attach Cables
To learn more about compatible cables and optics, refer to the [Intel documentation](https://www.intel.com/content/www/us/en/support/articles/000007045/network-and-i-o/ethernet-products.html).
[]To install the LB:
- Rack the LB using the included rail kit. LBs require 1U of space and are 17.2" wide.
- Connect the network cables according to the following image.
- **1 Gb IPMI Port**: Used for out-of-band management.
- **1 Gb OS/Management Port**: Used for server management.
- **10 Gb VIP 1 Ports **(te2 and te6): Bundled via LACP.
- **10 Gb VIP 2 Ports **(te3 and te7): (Optional) Bundled via LACP.
- **10 Gb VIP 3 Ports** (te4 and te8): (Optional) Bundled via LACP.
- Connect the power cables according to your internal specifications. LBs use universal power supply adapters. The LB powers on automatically and the LED light at the front of the box turns green. If the LB does not power on, press the power button on the front panel. If the unit still does not power on, or the power light is yellow or red, contact the Zscaler Cloud Operations project manager for assistance.
![LB Port Diagram](/downloads/zia/traffic-forwarding/service-edges/private-service-edge/understanding-private-service-edge/Installing%2003.png)