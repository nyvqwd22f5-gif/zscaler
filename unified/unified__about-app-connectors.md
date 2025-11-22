# About App Connectors
Source: https://help.zscaler.com/unified/about-app-connectors
PDF: https://help.zscaler.com/pdf/com/en/1496021.pdf

App Connectors provide the secure authenticated interface between a customer’s servers and the Private Applications cloud.
App Connectors provide the following benefits and enable you to:
- Securely connect to private applications hosted in a data center, virtual private cloud (VPC), or virtual network (VNET).
- Deploy in a variety of physical and virtual environments, including virtual machines, private clouds, public clouds, and container orchestration platforms.
- View individual App Connector connections and health status.
- Disable App Connectors from accepting traffic in an App Connector group.
- Force a staged update in advance of the update schedule.
App Connectors can be deployed in several forms. Zscaler distributes a standard virtual machine (VM) image for deployment in enterprise data centers, local private cloud environments such as VMware, or public cloud environments such as Amazon Web Services (AWS) EC2. Additionally, Zscaler provides packages that can be installed on supported Linux distributions.
- [List of Platforms Supported by Private Applications](#platforms)
App Connectors can be built in other hypervisor environments, such as KVM, and other cloud environments (i.e., Google Compute Platform, Oracle Cloud, etc.) by deploying a Linux instance and following the RPM-based deployment instructions. To learn more, see [App Connector Deployment Guide for Linux](/unified/app-connector-deployment-guide-linux).
App Connectors can be co-located with your enterprise applications, or they can be deployed in any location that has connectivity to the applications. The closest App Connector will be selected given the location of the user and the App Connector-to-application latency. Typically, they are deployed on network segments that can access secured applications and the Private Applications cloud simultaneously, such as in a DMZ. App Connectors only connect outbound; they do not need any inbound open ports to operate correctly. App Connectors are always active, so they are typically deployed in a redundant configuration. However, App Connectors never communicate with each other.
Before you begin, see [App Connector Deployment Prerequisites](/unified/app-connector-deployment-prerequisites) which provides detailed information on VM image sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
Configuring connectors involves two main tasks:
- [Adding App Connectors](/unified/configuring-app-connectors) using the Admin Portal, which includes obtaining an [App Connector Provisioning Key](/unified/about-app-connector-provisioning-keys).
- [Deploying App Connectors](/unified/about-deploying-app-connectors) on the [supported platform](/unified/about-app-connectors#platform) of your choice.
After an App Connector is added and deployed, it is displayed on the App Connectors page.
You can perform additional software management and maintenance tasks after deployment. To learn more, see [Managing Deployed App Connectors](/unified/managing-deployed-app-connectors) and [App Connector Software Updates](/unified/networking/private-applications/app-connector-management/app-connector-software-updates).
If any App Connectors have been disconnected for one year or more, an alert appears when you log in to the Admin Portal. Click the number of disconnected App Connectors in the alert to open this page, which is filtered by the disconnected App Connectors so you can review or delete them.
[]About the App Connectors Page
On the App Connectors page (Infrastructure > Private Access > Component > App Connectors), you can do the following:
- [Configure the App Connectors settings](/unified/configuring-app-connectors-settings). You can enable Auto Delete to remove disconnected or optionally disabled App Connectors after a set amount of days.
- Expand all of the rows in the table to see more information about each App Connector.
- [Add a new App Connector.](/unified/about-app-connectors)
- Refresh the App Connectors page to reflect the most current information.
- Filter the information that appears in the table. By default, no filters are applied.
- View a list of all deployed App Connectors. App Connectors that you've added, but have not deployed, are not listed. For each deployed App Connector, you can see:
- **Name**: The name of the App Connector. When expanded, the following information is displayed depending on the defined App Connector:
- **Description**: The description of the App Connector, if available.
- **App Connector Group**: The App Connector Group that the App Connector is a member of.
- **App Connector Host Platform**: The platform that the App Connector is deployed on (e.g., AWS, Azure, ESXi, Docker, or Nutanix).
- **App Connector Host OS**: The run time OS on which the App Connector is running (e.g., CentOS Linux 7, Red Hat Enterprise Linux 7, Red Hat Enterprise Linux 8, Red Hat Enterprise Linux 9).
- **App Connector Package OS**: The compile time OS on which the .rpm binary is packaged (e.g. Enterprise Linux 7).
- **Last Software Update**: The date and time the App Connector was last updated to a newer software version.
- **Public Service Edge**: The Public Service Edge that the App Connector connects to.
- **Last Connection to Zscaler**: The last time the App Connector connected to Zscaler.
- **Last Disconnect from Zscaler**: The last time the App Connector disconnected from Zscaler.
- **Location**: The location where the App Connector Group that the App Connector belongs to is set up.
- **Public IP**: The public IP address of the App Connector. Disconnected App Connectors show the last known public IP address.
- **Private IP**: The private IP address of the App Connector. Disconnected App Connectors show the last known private IP address.
- **Uptime**: The period of time the App Connector is available for use. Disconnected App Connectors show the value **Not Available**.
- **Enrollment Certificate**: The certificate the App Connector uses for enrollment.
- **Manager Version**: The version of the current App Connector Manager software. To learn more, see [Understanding the Manager Software](/unified/understanding-manager-software).
- **Current Software Version**: The current App Connector software version.
- **Connection Status**: The status of the App Connector connection.
- **Upgrade Status**: The status of the last App Connector software update.
- **Status**: Indicates whether the App Connector is enabled or disabled.
- See a graphical view for how the App Connector connects to other configuration objects (e.g., App Connector group, Server group, etc.).
You can edit any of the objects directly from the graphical view.
[See image.](#image_editobject)
-
[Edit the configuration of a deployed App Connector.](/unified/editing-deployed-app-connector)
App Connectors that are managed by Zscaler are read only and cannot be edited or deleted.
- Delete a deployed App Connector configuration.
To replace a [deployed App Connector](/unified/about-deploying-app-connectors), you must delete the configuration and then re-enroll it. However, you can apply the new App Connector provisioning key to the virtual machine (VM) image that you already deployed by [replacing the old key](/unified/managing-deployed-app-connectors#ReplaceProvisioningKey).
If an App Connector is configured using Zscaler Deception, then the edit and delete options are unavailable.
[See image.](#DeceptionAppConnector)
![Viewing and managing App Connectors](/downloads/unified/networking/private-applications/app-connector-management/app-connectors/about-app-connectors/Infrastructure.png)
- [][Amazon Web Services (AWS)](/unified/app-connector-deployment-guide-amazon-web-services)
- [Docker](/unified/app-connector-deployment-guide-docker)
- [Google Cloud Platform (GCP)](/unified/app-connector-deployment-guide-google-cloud-platform)
- [Linux (Red Hat Enterprise Linux 8 or 9)](/unified/app-connector-deployment-guide-linux)
- [Microsoft Azure](/unified/service-edge-deployment-guide-aws)
- [Nutanix](/unified/app-connector-deployment-guide-nutanix-ahv)
- [OpenShift](/unified/app-connector-deployment-guide-openshift)
- [VMware vCenter or vSphere Hypervisor (ESXi)](/unified/app-connector-deployment-guide-vmware-platforms)
Security Technical Implementation Guide (STIG) images for AWS, GCP, Microsoft Azure, Nutanix, and VMware are provided by default. To learn more, see [App Connector Software by Platform](/unified/app-connector-software-platform).
[]![Edit object from Graphical View](/downloads/zpa/app-connector-management/app-connectors/about-connectors/zpa-segmentgroupspage-editingraphview.png)
[]![Deception App Connector](/downloads/zpa/app-connector-management/app-connectors/about-connectors/zpa-deception-integration-appConnectors2.png)