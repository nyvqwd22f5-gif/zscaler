# Modifying Predefined Network Services
Source: https://help.zscaler.com/zia/modifying-predefined-network-services
PDF: https://help.zscaler.com/pdf/com/en/1399961.pdf

Zscaler provides over 50 predefined [network services](/zia/about-network-services) along with the TCP and UDP ports (for source and destination) over which these services typically operate. You can customize the ports assigned to the predefined network services by adding new ports and modifying and deleting existing ones.
The following predefined network services are view-only and cannot be modified: ESP, GRE, ICMP, TCP, UDP, and Zscaler Proxy Network Services (includes all Zscaler-specific web proxy ports including customer-specific Dedicated Proxy Ports).
To modify the ports of a predefined network service:
- Go to **Administration **>** Network Services**.
-
Locate the predefined network service you want to modify and click the **Edit** icon displayed for the service.
[See image.](#edit-option-network-services)
The **Edit Network Service** window appears.
-
In the **Edit Network Service** window, you can modify:
- **Description**: Information about the network service.
- **TCP Ports**: TCP source and destination ports by adding new ports or removing existing ones.
- **UDP Ports**: UDP source and destination ports by adding new ports or removing existing ones.
[See image.](#edit-network-service)
- Click **Save** and [activate the change](/zia/saving-and-activating-changes-admin-portal).
Similarly, you can edit custom network services and modify their port assignments. Additionally, you can delete a custom service using the option provided on the Edit Network Service window.
[]![Edit option for predefined network services](/downloads/zia/policies/firewall/firewall-policy-resources/modifying-predefined-network-services/predefined-network-services-edit-option.png)
[]![Editing a predefined network service](/downloads/zia/policies/firewall/firewall-policy-resources/modifying-predefined-network-services/edit-predefined-network-service.png)