# App Connector Deployment and Operations Guide
Source: https://help.zscaler.com/zscaler-deployments-operations/app-connector-deployment-and-operations-guide
PDF: https://help.zscaler.com/pdf/com/en/1417951.pdf

This guide describes the benefits of using App Connectors and the steps necessary for configuring Zscaler Private Access (ZPA) to add App Connectors to your security posture.
App Connectors provide a secure authenticated interface between a customer’s servers and the Zscaler cloud. App Connectors can be deployed in several forms. Zscaler distributes a standard virtual machine (VM) image for deployment in enterprise data centers, local private cloud environments such as VMware, or public cloud environments such as Amazon Web Services (AWS) EC2. Additionally, Zscaler provides packages that can be installed on supported Linux distributions.
To learn more, see [About App Connectors](/zpa/about-connectors).
Value of Deploying App Connectors
Using App Connectors provides the following benefits:
- Provides a cleaner and faster infrastructure by selecting the closest App Connector given the location of the user and App Connector-to-application latency.
- Facilitates an always active, redundant configuration.
Deployment Phase
The deployment phase initially sets up and integrates ZPA solutions into an existing network infrastructure. During the deployment phase, you configure App Connectors to meet the needs of your infrastructure. The following sections discuss steps to deploy App Connectors.
Prerequisites
For App Connector deployment, verify and complete the following prerequisites:
- One of the following Zscaler subscriptions is required:
- ZPA Professional Edition
- ZPA Business Edition
- ZPA Transformation Edition
- [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites)
Deployment Steps
For information on how to configure an App Connector on the respective platforms, see [App Connector Deployment Guides for Supported Platforms](/zpa/app-connector-management/app-connector-deployment-guides-supported-platforms).
Considerations
Review the following considerations:
- [List of platforms supported by ZPA](/zpa/about-connectors#platforms).
- By design, certificate verification is not configurable to maintain the service's integrity. Ensure that *.prod.zpath.net is in your SSL bypass list for traffic originating from the App Connector, which is necessary for App Connectors to resolve and reach ZPA Public Service Edges or ZPA Private Service Edges.
- For ZPA integration with Zscaler Digital Experience (ZDX), App Connector firewall requirements must align with the respective ZDX configuration and require the configured report protocols to egress the App Connector (i.e., UDP, ICMP, or UDP). The traffic must egress the App Connector towards the configured application port and to the Zscaler Public Service Edge on port 443.
- The customer is responsible for maintaining the host on which the App Connector is running. Zscaler does not maintain the underlying operating system, only the App Connector application. To learn more about updating the App Connector system software, see [Update App Connector System Software](/zpa/managing-deployed-connectors#Updating).
Operations Phase
This section describes standard practices used to operate Zscaler solutions when integrated with your environment. You can monitor and tune App Connectors during operations to meet your infrastructure needs.
Prerequisites
For App Connector operation, complete the following prerequisites:
- Check the [App Connector health status](/zpa/managing-deployed-connectors#Status) by accessing the App Connectors page and using the Health dashboard within the ZPA Admin Portal.
- Verify the [App Connector Sizing Specifications](/zpa/managing-deployed-connectors#VerifySizing).
Common Troubleshooting Items
The following list describes common issues related to App Connector operations:
- App Connector is not connecting to the Zscaler cloud: If the App Connector was previously working and now shows an error about not being connected to the cloud, see [Troubleshooting App Connectors](/unified/troubleshooting-app-connectors).
-
In the command prompt, enter the following command to stop the zpa-connector service:
[admin@zpa-connector ~]$ sudo systemctl stop zpa-connector
-
Enter the following command to delete the App Connector:
[admin@zpa-connector ~]$ rm -f /opt/zscaler/var/*
-
Enter the following command to restart services:
[admin@zpa-connector ~]$ sudo systemctl restart zpa-connector
- Collect the App Connector logs to see App Connector log information. Collect the App Connector logs by running the `journalctl` sudo command as an admin.
-
Enter the following command to collect the logs:
[admin@zpa-connector ~]$ sudo journalctl -u zpa-connector -f
-
Enter the following command to collect the logs with a maximum of 1000 lines (you don't need to use the root level for this command):
[root@ip-10-0-0-228 admin]# journalctl -n1000 | grep zpa-connector
-
Enter the following command to collect the logs and store in a file called journalctl.log:
sudo journalctl -u zpa-connector > journalctl.log
For more troubleshooting information, see [Troubleshooting App Connectors](/zpa/troubleshooting-app-connectors).
Deployment Checklist
Zscaler recommends downloading the [App Connector Deployment and Operations Checklist](/downloads/zscaler-deployments-operations/zpa-deployments-operations/app-connector-deployment-and-operations-guide/App-Connector-Deployment-Operations-Checklist.pdf) to help plan and implement App Connector: [Download PDF](/downloads/zscaler-deployments-operations/zpa-deployments-operations/app-connector-deployment-and-operations-guide/App-Connector-Deployment-Operations-Checklist.pdf)
Additional Information
For more App Connector information and troubleshooting instructions, see the [Zscaler Support Portal](https://zscaler.my.site.com/customers/s/) and the [Zscaler Zenith Community](https://community.zscaler.com/).