# Understanding Private Application Connectivity for Branches
Source: https://help.zscaler.com/zero-trust-branch/understanding-private-app-connectivity-branches
PDF: https://help.zscaler.com/pdf/com/en/1532805.pdf

You can integrate Zscaler's Zero Trust Branch and Zscaler Private Access (ZPA) to enable secure, identity-aware connectivity between branches and private applications without extending the corporate network or relying on traditional Multiprotocol Label Switching (MPLS) and VPN architectures. This integration leverages the ZPA App Connector to securely connect users and appliances in branch offices to private applications hosted in other branch environments. In traditional networks, branches are connected to private apps through the corporate data center using hub-and-spoke routing. This approach introduces latency, cost, and complexity, and it exposes the internal network to potential lateral movement.
When Zero Trust Branch integrates with ZPA App Connector-based connectivity, it offers:
- A secure connection to private applications in branch sites through the App Connector, an outbound-only component deployed as part of ZPA.
- A mechanism to route branch traffic securely through the Zero Trust Exchange (ZTE), where access policies are enforced.
- Connections that are user based, application specific, and dynamically brokered, eliminating the need to extend the internal network between branches.
Key Advantages
Integrated App Connector–based connectivity allows Zero Trust Branch and ZPA to work as a unified system for secure, private application access. It replaces traditional network-centric approaches with an application-centric, policy-driven zero trust model that gives organizations a more efficient, scalable, and secure way to connect branches to private apps. The following are some of the key advantages of integrated App Connector–based connectivity:
- **No Network Extension**: Branches connect through the ZTE without extending corporate IP spaces.
- **Identity-Driven Access**: Access decisions are based on user identity, device posture, and application context.
- **Simplified Architecture**: Eliminates complex routing, VPNs, and MPLS dependencies.
- **Enhanced Security**: Reduces attack surface by replacing network segmentation with application segmentation.
- **Seamless User Experience**: Enables direct, fast, and secure access to private applications between branch environments.
This model ensures that connectivity between branches and private applications remains secure, segmented, and invisible to the internet.
Private Application Connectivity Workflow
The following workflow explains how Zero Trust Branch uses an integrated ZPA App Connector to enable secure, policy-based access to private applications hosted across branch sites. Each connection is established through the ZTE, ensuring identity verification and device posture checks before granting access.
- A user or appliance in a branch attempts to access a private application in another branch.
- Zero Trust Branch securely forwards the traffic to the ZTE.
- The ZTE evaluates the traffic based on identity, device posture, and policy context as configured in ZPA.
- A temporary, policy-based (ZPA) connection is created between the user and the application through the App Connector.
Configuring Private Application Connectivity for Branches
Complete the following steps to configure private application connectivity for branches:
- [Add an App Connector in ZPA for each branch site that hosts private applications](/zero-trust-branch/adding-app-connector-site).
- [Deploy the App Connectors to the respective sites in the Zero Trust Branch Admin Portal](/zpa/configuring-connectors).
- Define [application segments](/zpa/configuring-defined-application-segments) and [access policies](/zpa/about-access-policy) as required for the private applications in ZPA.
Depending on your requirements, the private applications in branch environments can use App Connector-based DNS resolutions or a private DNS server within the branch site behind its App Connector.