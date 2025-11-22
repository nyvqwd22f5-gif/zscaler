# Installing Zero Trust SD-WAN Devices
Source: https://help.zscaler.com/cloud-branch-connector/installing-zero-trust-branch-devices
PDF: https://help.zscaler.com/pdf/com/en/1468541.pdf

Upon receipt of the Zscaler Branch Connector hardware, install your Zero Trust Software-Defined Wide Area Network (SD-WAN) Device according to the instructions provided for gateway and non-gateway (one-arm) mode.
In gateway mode, the Zero Trust SD-WAN Device enables direct, secure access from your private network to other geographically distributed parts of your private network, cloud applications, and the internet over one or more internet service provider (ISP) connections. It can also dynamically determine the best quality link, forward specific traffic toward that link, and function as a local router. Local devices can communicate without an external router. You can also deploy the hardware device in gateway mode inside of your local area network (LAN) while an existing device connects you to the internet through the wide area network (WAN).
In non-gateway (one-arm) mode, the Zero Trust SD-WAN Device does not connect directly to the internet service provider (ISP). Instead, the Zero Trust SD-WAN Device deploys in the internal network of the organization and provides access from your private network to other geographically distributed parts of your private network, cloud applications, and the internet. Non-gateway (one-arm) mode requires an external router.
Console Settings
The Zero Trust SD-WAN Device requires an RJ45 interface. To use a DB9 serial connection, you may also need a serial adapter. Configure the serial connection as follows:
- **Baud Rate**: 115200
- **Data Bits**: 8
- **Stop Bits**: 1
- **Parity**: None
- **Flow Control**: XON/XOFF
Installation Guides
- [Zero Trust SD-WAN Device 400 Installation Guide](#HW400)
- [Zero Trust SD-WAN Device 600 Installation Guide](#HW600)
- [Zero Trust SD-WAN Device 800 Installation Guide](#HW800)
Reset Button
To press the reset button on the Zero Trust SD-WAN Device, use the tip of a pen or a paperclip. When you press the reset button for 10 seconds, the system LED turns green, and the reset sequence is initiated.
After Installation
After installation is complete, you can [deploy the Zero Trust SD-WAN Device](/cloud-branch-connector/deploying-zero-trust-branch-devices).
- [][Package Contents](#package-HW4)
- [Non-Gateway (One-Arm) Installation](#install-HW4)
- [Gateway Installation](#install-HW4-gateway)
[]The package contains the following items:
- 1 Zero Trust SD-WAN Device 400
- 1 power adapter
- 19-inch mounting brackets
The following items are not included, but are required for non-gateway (one-arm) installation:
- Minimum of 2 CAT6 Ethernet cables
- Minimum of 3 CAT6 Ethernet cables when deploying with App Connector
The following items are not included, but are required for gateway installation:
- Minimum of 3 CAT6 Ethernet cables
- Maximum of 4 CAT6 Ethernet cables
When deploying in gateway mode, App Connector does not require its own cable.
[]To install the Zero Trust SD-WAN Device 400:
- Connect the power adapter. The Zero Trust SD-WAN Device 400 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
- **1 Gbps OS/Management Port**: Used for device management. On the ZT400 and ZT400 with App Connector devices, connect this cable to the port labeled **1**.
- **1 Gbps Zscaler Service Port**: Used by the Zscaler service for both incoming and outgoing data traffic. It hosts the IP address of a Zero Trust SD-WAN Device. On the ZT400 device, connect this cable to the port labeled **2**. On the ZT400 with App Connector device, connect this cable to the port labeled **3**.
- **1 Gbps App Connector Port**: (Optional) Used by App Connector for both incoming and outgoing data traffic. On the ZT400 with App Connector device, connect this cable to the port labeled **2**.
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![The Zero Trust Branch Device 400 cable connections](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/installing-zero-trust-branch-devices-draft-doc-49859/ZT400_ZT400AppC.jpg)
[]To install the Zero Trust SD-WAN Device 400:
- Connect the power adapter. The Zero Trust SD-WAN Device 400 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
-
**GE1 OS/Management Port 1**: Used for device management. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. You can update the IP configurations in the[ Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
If the DHCP client is enabled on the management interface via the [System Settings in the Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewaySystemSettings) and it does not receive a DHCP offer, the IP address automatically defaults to 192.168.1.1/24.
- **GE4 WAN Port 4**: Used by the Zscaler service for both incoming and outgoing data traffic. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. Port 4 is the default WAN port. Ports 2-3 can also be used as a WAN port. You can update the WAN ports and IP configurations in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- **LAN Ports**: You can use the remaining ports for LAN ports through which network devices can connect to each other and to the Zscaler service. Configure these ports in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![The Zero Trust Branch Device 400 cable connections when deploying in gateway mode. ](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/installing-zero-trust-branch-devices-draft-mvp-1/ZT400-GatewayMode-2.jpg)
- [][Package Contents](#package-HW6)
- [Non-Gateway (One-Arm) Installation](#install-HW6)
- [Gateway Installation](#install-HW6-gateway)
[]The package contains the following items:
- 1 Zero Trust SD-WAN Device 600
- 1 power adapter
- 19-inch mounting brackets
The following items are not included, but are required for non-gateway (one-arm) installation:
- Minimum of 2 CAT6 Ethernet cables
- Minimum of 3 CAT6 Ethernet cables when deploying with App Connector
The following items are not included, but are required for gateway installation:
- Minimum of 3 CAT6 Ethernet cables
- Maximum of 6 CAT6 Ethernet cables
App Connector does not require its own cable when deploying in gateway mode.
[]To install the Zero Trust SD-WAN Device 600:
- Connect the power adapter. The Zero Trust SD-WAN Device 600 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
- **1 Gbps OS/Management Port**: Used for device management. On the ZT600 and ZT600 with App Connector devices, connect this cable to the port labeled **1**.
- **1 Gbps Zscaler Service Port**: Used by the Zscaler service for both incoming and outgoing data traffic. It hosts the IP address of a Zero Trust SD-WAN Device. On the ZT600 device, connect this cable to the port labeled **2**. On the ZT600 with App Connector device, connect this cable to the port labeled **3**.
- **1 Gbps App Connector Port**: (Optional) Used by App Connector for both incoming and outgoing data traffic. On the ZT600 with App Connector device, connect this cable to the port labeled **2**.
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![Zero Trust Branch Device 600 with and without App Connector](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/installing-zero-trust-branch-devices-draft-doc-49859/ZT600_ZT600AppC.jpg)
[]To install the Zero Trust SD-WAN Device 600:
- Connect the power adapter. The Zero Trust SD-WAN Device 600 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
-
**GE1 OS/Management Port 1**: Used for device management. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. You can update the IP configurations in the[ Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
If the DHCP client is enabled on the Management Interface via the [System Settings in the Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewaySystemSettings) and it does not receive a DHCP offer, the IP address automatically defaults to 192.168.1.1/24.
- **GE6 WAN Port 6**: Used by the Zscaler service for both incoming and outgoing data traffic. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. Port 6 is the default WAN port. Ports 2-5 can be also be used as a WAN port. You can update the WAN ports and IP configurations in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- **LAN Ports**: You can use the remaining ports for LAN ports through which network devices can connect to each other and to the Zscaler service. Configure these ports in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![The Zero Trust Branch Device 600 cable connections when deploying in gateway mode.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/installing-zero-trust-branch-devices-draft-mvp-1/ZT600-GatewayMode.jpg)
- [][Package Contents](#package-800)
- [Non-Gateway (One-Arm) Installation](#install-800)
- [Gateway Installation](#install-800-gateway)
[]The following items are included:
- 1 Zero Trust SD-WAN Device 800
- 1 power adapter
- 19-inch mounting brackets
The following items are not included, but are required for non-gateway (one-arm) installation:
- Minimum of 4 CAT6 Ethernet cables
- Minimum of 5 CAT6 Ethernet cables when deploying with App Connector
The following items are not included, but are required for gateway installation:
- Minimum of 3 CAT6 Ethernet cables
- Maximum of 6 CAT6 Ethernet cables
App Connector does not require its own cable when deploying in gateway mode.
[]To install the Zero Trust SD-WAN Device 800:
- Connect the power adapter. The Zero Trust SD-WAN Device 800 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
- **1 Gbps OS/Management Port**: Used for device management. On the ZT800 and ZT800 with App Connector devices, connect this cable to the port labeled **3.**
- **3 Gbps Zscaler Service Ports**: Used by the Zscaler service for both incoming and outgoing data traffic. It hosts the IP address of a Zero Trust SD-WAN Device. On the ZT800 device, connect these cables to the ports labeled **5** and **6**. On the ZT800 with App Connector device, connect these cables to the ports labeled **6** and **7.**
- **1 Gbps Load Balancer Port: **Used to load balance traffic across multiple Branch Connectors. On the ZT800 device, connect this cable to the port labeled **4**. On the ZT800 with App Connector device, connect this cable to the port labeled **5**.
- **1 Gbps App Connector Port**: (Optional) Used by App Connector for both incoming and outgoing data traffic. On the ZT800 with App Connector device, connect this cable to the port labeled **4**.
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![Zero Trust Branch Device 800 with and without App Connector.](/downloads/cloud-branch-connector/deployment-management-physical-devices/installing-zero-trust-branch-devices/ZT800_ZT800AppC-3.jpg)
[]To install the Zero Trust SD-WAN Device 800:
- Connect the power adapter. The Zero Trust SD-WAN Device 800 uses universal power supply adapters.
- Connect the CAT6 Ethernet network cables as shown below.
-
**GE3 OS/Management Port 3**: Used for device management. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. You can update the IP configurations in the[ Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
If the DHCP client is enabled on the Management Interface via the [System Settings in the Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template#GatewaySystemSettings) and it does not receive a DHCP offer, the IP address automatically defaults to 192.168.1.1/24.
- **GE8 WAN Port 8**: Used by the Zscaler service for both incoming and outgoing data traffic. By default, it receives the IP address from the DHCP client to support Zero Touch Provisioning. Port 8 is the default WAN port. Ports 4-7 can be also be used as a WAN port. You can update the WAN port and IP configurations in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- **LAN Ports 5, 6, and 7**: You can use the remaining ports for LAN ports through which network devices can connect to each other and to the Zscaler service. Configure these ports in the [Branch Configuration Template](/cloud-branch-connector/configuring-branch-configuration-template).
- Press the power button. The LED light on the power button turns red and then turns green. If the device does not turn on, check the adapter connection. If the unit still does not power on, contact Zscaler Support.
![The Zero Trust Branch Device 800 cable connections when deploying in gateway mode.](/downloads/tech-pubs-drafts/cloud-connector-draft-articles/installing-zero-trust-branch-devices-draft-mvp-1/ZT800-GatewayMode.jpg)