# Understanding the Manager Software
Source: https://help.zscaler.com/zpa/understanding-manager-software
PDF: https://help.zscaler.com/pdf/com/en/1485136.pdf

This article provides information about the Manager software; details about the Manager version; details about the App Connector, ZPA Private Service Edge, Private Cloud Controller, and Network Connector software versions; and upgrades to all.
When you first deploy the software, a server is required to run the software. The server is available using a virtual machine (VM). The VMs run a service called `zpa-connector` for App Connectors, `zpa-service-edge` for ZPA Private Service Edges, `zpa-pcc` for Private Cloud Controllers, , and `np-connector` for Network Connectors. To learn about installing the service on your own server, see the [App Connector Deployment Guides for Supported Platforms](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms), [Private Service Edge Deployment Guides for Supported Platforms](/zpa/private-service-edge-management/private-service-edge-deployment-guides-supported-platforms), and [Private Cloud Controller Deployment Guides for Supported Platforms](/zpa/business-continuity-management/private-cloud-controller-deployment-guides-supported-platforms), and the [Network Connector Deployment Guide for Linux](/zpa/network-connector-deployment-guide-linux).
The Manager is the `zpa-connector`, `zpa-service-edge`, `zpa-pcc`, or `np-connector` software that is needed to manage the App Connector, ZPA Private Service Edge, Private Cloud Controller, or Network Connector components.
The `zpa-connector` software downloads a new software, called `zpa-connector-child`, that establishes Microtunnels (M-Tunnels) and talks to the internal applications. This child software facilitates access to internal applications for ZPA users.
Manager Version and Current Software Version
The purpose of the Manager software is to supervise and control the App Connector (`zpa-connector-child`), ZPA Private Service Edge (`zpa-service-edge-child`), Private Cloud Controller (`zpa-pcc-child`), or Network Connector (`np-connector-child`) software. The version of the Manager rarely requires updates. New features are constantly being added to ZPA and these features involve new functionality in App Connectors, ZPA Private Service Edges, Private Cloud Controllers, and Network Connectors. The child software (e.g., `zpa-connector-child`) does the primary work of the App Connector and gets updated frequently.
The Manager software uses the OS trusted Certificate Authority (CA) bundle for establishing a TLS connection to download software. The CentOS CA bundle can be found at the following location: `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`
Use the following command to update the CentOS CA bundle: `sudo update-ca-trust`
Manager, App Connector, ZPA Private Service Edge, Private Cloud Controller, and Network Connector Upgrades
The Manager software is what makes the upgrades possible.
- [Manager Upgrades](#managerUpgrades)
- [App Connector Upgrades](#appConnectorUpgrades)
- [Private Cloud Controller Upgrades](#pcc-upgrades)
- [ZPA Private Service Edge Upgrades](#privateServiceEdgeUpgrades)
- [Network Connector Upgrades](#vpnNetworkConnectorUpgrades)
[][App Connector] upgrades mean upgrading the `zpa-connector-child` software. To learn more, see [Understanding App Connector Software Upgrades](/zpa/understanding-connector-software-updates).
[]The Manager upgrades mean upgrading the `zpa-connector` or `zpa-service-edge` software. If you are using Linux software packages, the Manager must be upgraded manually in your App Connector or ZPA Private Service Edge console using the following command:
sudo yum upgrade
This command upgrades all software packages on the server, including `zpa-connector` and `zpa-service-edge`, which holds the Manager software.
To upgrade only the `zpa-connector` package, use the following command:
sudo yum upgrade zpa-connector
To upgrade only the `zpa-service-edge` package, use the following command:
sudo yum upgrade zpa-service-edge
To upgrade only the `zpa-pcc` package, use the following command:
`sudo yum upgrade zpa-pcc`
All commands include the upgrade of the Manager software.
The Manager software is included in upgrades to the host operating system (OS). Zscaler recommends periodically updating the App Connector, ZPA Private Service Edge, Private Cloud Controller, or Network Connector host OS using the `sudo yum update -y` command. To learn more, see [Upgrading the App Connector Host OS](/zpa/upgrading-app-connector-host-os).
[]Private Cloud Controller upgrades mean upgrading the `zpa-pcc-child` software. To learn more, see [Understanding Private Cloud Controller Software Upgrades](/zpa/understanding-private-cloud-controller-software-upgrades).
[]ZPA Private Service Edge upgrades means upgrading the `zpa-service-edge-child` software. To learn more, see [Understanding ZPA Private Service Edge Software Upgrades](/zpa/understanding-zpa-private-service-edge-software-upgrades).
[]Network Connector upgrades means upgrading the `np-connector-child` software.