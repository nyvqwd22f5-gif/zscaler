# Understanding the Zscaler Cellular Architecture
Source: https://help.zscaler.com/zscaler-cellular/understanding-zscaler-cellular-architecture
PDF: https://help.zscaler.com/pdf/com/en/1518221.pdf

Zscaler Cellular is a transformative solution designed to address the complexities of securing cellular-connected IoT and mobile devices. By leveraging the Zscaler Zero Trust Exchange (ZTE), it extends Zero Trust principles to the cellular domain, ensuring secure, scalable, and efficient connectivity for diverse use cases. This article outlines the Zscaler Cellular architecture and how its components work together to deliver robust security and operational simplicity.
Key Architectural Components
The key architectural components of Zscaler Cellular are:
Zscaler SIM
A Zscaler SIM serves as the gateway for a cellular-connected device to access the ZTE. It is a data-only SIM card that integrates directly with the ZTE, providing seamless security for IoT devices such as vending machines, EV chargers, machinery, and tablets/kiosks where agent-based solutions are not feasible. It provides:
- **Secure Traffic Forwarding**: Cellular traffic is routed directly to the ZTE for inspection, policy enforcement, and visibility.
- **Agentless Security**: Devices connected via Zscaler SIMs do not require additional software agents, simplifying deployment and management.
- **Policy Enforcement**: Zscaler SIMs enable you to enforce security policies based on IP address, IMEI, or IMSI via Zscaler Internet Access (ZIA) and Zscaler Private Access (ZPA).
- **Anomaly Detection**: Telemetry data from Zscaler SIMs helps identify abnormal behavior in IoT and mobile deployments.
Zscaler Cellular Edge
Cellular Edge is an intelligent mechanism to forward traffic from or to a Zscaler SIM to the ZTE. It is an egress point to funnel cellular traffic to the Zero Trust Exchange (ZTE) for inspection and policy enforcement. It provides:
- **Traffic Aggregation**: Funnels cellular traffic to the ZTE for inspection and policy application.
- **Bidirectional Traffic Control**: Ensures secure communication between devices and their endpoints.
- **High Availability**: Supports continuous service delivery with its failover infrastructure.
- **Telemetry Insights**: Delivers granular data on SIM traffic, enabling detailed analytics and reporting.
![Illustration of Zscaler Cellular Architecture](/downloads/zscaler-cellular/getting-started/understanding-zscaler-cellular-architecture/diagram_cell-services_features_3.png)