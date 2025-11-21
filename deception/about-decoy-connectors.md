# About Decoy Connectors
Source: https://help.zscaler.com/deception/about-decoy-connectors
PDF: https://help.zscaler.com/pdf/com/en/1531272.pdf

[Watch a video on Adding and Connecting Decoy Connectors.](https://fast.wistia.net/embed/iframe/u6tiabaqnr)
Decoy Connectors (formerly known as Appliances) are lightweight virtual machines (VMs) that host network decoys. They also act as a network broker to connect the Zscaler Deception service to on-premises systems and Active Directory (AD) decoys in your environment.
Deception distributes a standard VM image for deploying Decoy Connectors in enterprise data centers and cloud environments for various supported platforms.
Decoy Connectors provide the following benefits and enable you to:
- Host internal network decoys and bridge a connection between the Deception service and various on-premises systems.
- Leverage third-party cloud services such as AWS, Microsoft Azure, etc. to set up internal decoys.
After a Decoy Connector is added and connected to the Zscaler Deception Admin Portal, it is displayed on the Decoy Connectors page. To learn more about ranges and limits for Decoy Connectors, see [Ranges & Limitations](/deception/ranges-and-limitations).
About the Decoy Connectors Page
On the Decoy Connectors page (Settings > Topology > Decoy Connectors), you can do the following:
- Download the virtual machine (VM) image file to deploy the Decoy Connectors on the following supported platforms:
- [VMware vSphere Hypervisor (ESXi)](/deception/decoy-connector-deployment-guide-vmware)
- [Microsoft Hyper-V](/deception/decoy-connector-deployment-guide-microsoft-hyper-v)
- [Microsoft Azure](/deception/decoy-connector-deployment-guide-microsoft-azure)
- [Amazon Web Services (AWS)](/deception/decoy-connector-deployment-guide-aws)
- [Add a Decoy Connector to the Deception Admin Portal](/deception/adding-connecting-decoy-connector-admin-portal).
- View a list of all deployed Decoy Connectors. For each deployed Decoy Connector, you can see:
- **Name**: The name of the Decoy Connector. The following icons indicate the connection status of the Decoy Connector with the Deception Admin Portal:
- ![Green connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/about-decoy-connectors/zscaler-deception-green-status-icon.png?1647841041)
– Active or connected to the Deception Admin Portal.
- ![Red connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/about-decoy-connectors/zscaler-deception-red-status-icon.png?1647841255)
– Inactive or not connected to the Deception Admin Portal.
- ![Orange connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/decoy-connector-deployment-guides-supported-platforms/zscaler-deception-orange-status-icon.png)
– Not connected to an aggregator.
- ![Yellow connection status icon](/downloads/deception/product-documentation/settings/topology/appliances/about-decoy-connectors/zscaler-deception-yellow-status-icon.png)
– Update in progress or update failed.
- **Version**: The version of the Decoy Connector.
- **Management IP**: The management IP of the Decoy Connector.
- **Last Connected Time**: The time when the Decoy Connector was last connected to the Deception Admin Portal.
- Perform one of the following actions:
- [Obtain recovery and diagnostic credentials for a Decoy Connector](/deception/obtaining-decoy-connector-recovery-and-diagnostics-credentials).
- [Reboot a Decoy Connector](/deception/rebooting-decoy-connector).
- [Edit or delete a Decoy Connector](/deception/editing-or-deleting-decoy-connector).
- [View update logs](/deception/viewing-decoy-connector-update-logs) and [download the debug logs](/deception/downloading-decoy-connector-debug-logs) for a Decoy Connector.
![About the Decoy Connectors page](/downloads/deception/product-documentation/settings/topology/decoy-connectors/about-decoy-connectors/deception-about-decoy-connectors.png)