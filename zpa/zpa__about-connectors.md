# About App Connectors
Source: https://help.zscaler.com/zpa/about-connectors
PDF: https://help.zscaler.com/pdf/com/en/1483541.pdf

[Watch a video about App Connectors.](https://fast.wistia.net/embed/iframe/qatvjbrtwn)
App Connectors provide the secure authenticated interface between a customer’s servers and the ZPA cloud.
App Connectors provide the following benefits and enable you to:
- Securely connect to private applications hosted in a data center, virtual private cloud (VPC), or virtual network (VNET).
- Deploy in a variety of physical and virtual environments, including virtual machines, private clouds, public clouds, and container orchestration platforms.
- View individual App Connector connections and health status.
- Disable App Connectors from accepting traffic in an App Connector group.
- Force a staged update in advance of the update schedule.
App Connectors can be deployed in several forms. Zscaler distributes a standard virtual machine (VM) image for deployment in enterprise data centers, local private cloud environments such as VMware, or public cloud environments such as Amazon Web Services (AWS) EC2. Additionally, Zscaler provides packages that can be installed on supported Linux distributions.
- [List of Platforms Supported by ZPA](#platforms)
App Connectors can be built in other hypervisor environments, such as VMware, and other cloud environments (i.e., Google Cloud Platform, Oracle Cloud, etc.) by deploying a Linux instance and following the RPM-based deployment instructions. To learn more, see [App Connector Deployment Guide for Linux](/zpa/app-connector-deployment-guide-linux).
App Connectors can be co-located with your enterprise applications, or they can be deployed in any location that has connectivity to the applications. ZPA selects the closest App Connector given the location of the user and the App Connector-to-application latency. Typically, they are deployed on network segments that can access secured applications and the ZPA cloud simultaneously, such as in a DMZ. App Connectors only connect outbound; they do not need any inbound open ports to operate correctly. App Connectors are always active, so they are typically deployed in a redundant configuration. However, App Connectors never communicate with each other.
Before you begin, see [App Connector Deployment Prerequisites](/zpa/connector-deployment-prerequisites) which provides detailed information on VM image sizing and scalability, supported platform requirements, deployment best practices, and other essential guidelines.
Configuring connectors involves two main tasks:
- [Adding App Connectors](/zpa/configuring-connectors) using the ZPA Admin Portal, which includes obtaining an [App Connector Provisioning Key](/zpa/about-connector-provisioning-keys).
- [Deploying App Connectors](/zpa/about-deploying-connectors) on the [supported platform](/zpa/about-connectors#platforms) of your choice.
After an App Connector is added and deployed, it is displayed on the App Connectors page.
You can perform additional software management and maintenance tasks after deployment. To learn more, see [Managing Deployed App Connectors](/zpa/managing-deployed-connectors) and [App Connector Software Updates](/zpa/app-connector-management/app-connector-software-updates).
If any App Connectors have been disconnected for one year or more, an alert appears when you log in to the ZPA Admin Portal. Click the number of disconnected App Connectors in the alert to open this page, which is filtered by the disconnected App Connectors so you can review or delete them.
[]About the App Connectors Page
On the App Connectors page (Configuration & Control > Private Infrastructure > App Connector Management > App Connectors), you can do the following:
- View a list of applied filters available from the current and previous user sessions. Applied filters must be saved to the user session first before they can be viewed. Use the drop-down menu to select the applied filters to view. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- Hide the filters on the page by clicking **Hide Filters**. Click **Show Filters** to show the filters.
- Refresh the App Connector page to reflect the most current information.
- [Configure the App Connectors settings](/zpa/configuring-app-connectors-settings). You can enable **Auto Delete** to remove disconnected or optionally disabled App Connectors after a set number of days.
- Filter the information that appears in the table. By default, no filters are applied. You can also save applied filters to your preferences so that they're visible in future user sessions. To learn more, see [Using Tables](/zpa/using-tables#filterData).
- [Add a new App Connector.](/zpa/about-connectorProvisioningWizard)
- Expand all the rows in the table to see more information about each App Connector.
- View a list of all deployed App Connectors. App Connectors that you've added, but have not deployed, are not listed. For each deployed App Connector, you can see:
- **Name**: The name of the App Connector. When expanded, the following information is displayed depending on the defined App Connector:
- **Description**: The description of the App Connector, if available.
- **App Connector Group**: The App Connector group that the App Connector is a member of.
- In most cases, the following fields appear on the page. In cases where an App Connector is managed using a Branch Connector, Zscaler Deception, or a Host Dedicated IP (HDIP) address, the following fields do not appear:
- **App Connector Host Platform**: The platform that the App Connector is deployed on (e.g., AWS, Azure, ESXi, Docker, or Nutanix).
- **App Connector Host OS**: The run time OS on which the App Connector is running (e.g., CentOS Linux 7, Red Hat Enterprise Linux 7, Red Hat Enterprise Linux 8, Red Hat Enterprise Linux 9).
- **App Connector Package OS**: The compile time OS on which the .rpm binary is packaged (e.g. Enterprise Linux 7).
- **Last Software Update**: The date and time the App Connector was last updated to a newer software version.
- **Public Service Edge**: The ZPA Public Service Edge that the App Connector connects to.
- **Last Connection to Zscaler**: The last time the App Connector connected to Zscaler.
- **Last Disconnect from Zscaler**: The last time the App Connector disconnected from Zscaler.
- **Location**: The location where the App Connector group that the App Connector belongs to is set up.
- **Public IP**: The public IP address of the App Connector. Disconnected App Connectors show the last known public IP address.
- **Private IP**: The private IP address of the App Connector. Disconnected App Connectors show the last known private IP address.
- **Uptime**: The period of time the App Connector is available for use. Disconnected App Connectors show the value **Not Available**.
- **Enrollment Certificate**: The certificate the App Connector uses for enrollment.
- **Manager Version**: The version of the current App Connector Manager software. To learn more, see [Understanding the Manager Software](/zpa/understanding-manager-software).
- **Current Software Version**: The current App Connector software version.
- **Connection Status**: The status of the App Connector connection.
- **Upgrade Status**: The status of the last App Connector software update.
- **Status**: Indicates whether the App Connector is enabled or disabled.
- [Modify the columns displayed in the table.](/zpa/using-tables)
-
[View a configuration graph of connected objects.](/zpa/pselabel/viewing-configuration-graphs)
-
[Edit the configuration of a deployed App Connector.](/zpa/editing-deployed-connector)
App Connectors that are managed by Zscaler are read only and cannot be edited or deleted.
- Delete a deployed App Connector configuration.
To replace a [deployed App Connector](/zpa/about-deploying-connectors), you must delete the configuration and then re-enroll it. However, you can apply the new App Connector provisioning key to the virtual machine (VM) image that you already deployed by [replacing the old key](/zpa/managing-deployed-connectors#ReplaceProvisioningKey).
If an App Connector is configured using Zscaler Deception, then the edit and delete options are unavailable.
[See image.](#DeceptionAppConnector)
- Display more rows or a different page of the table.
- Open the [Zscaler Help Browser](/zpa/using-zscaler-help-browser) and view Help Portal articles without leaving the ZPA Admin Portal.
- Go to the [App Connector Groups](/zpa/about-connector-groups) page to manage your App Connector groups.
- Go to the [App Connector Provisioning Keys](/zpa/about-connector-provisioning-keys) page to manage your App Connector provisioning keys.
![App Connectors page within the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connectors/about-connectors/app-connecto-page-w-steps_0.png)
- [][Amazon Web Services (AWS)](/zpa/connector-deployment-guide-amazon-web-services)
- [Docker](/zpa/app-connector-deployment-guide-docker)
- [Google Cloud Platform (GCP)](/zpa/app-connector-deployment-guide-google-cloud-platform)
- [Linux (Red Hat Enterprise Linux 8 or 9)](/zpa/app-connector-deployment-guide-linux)
- [Microsoft Azure](/zpa/connector-deployment-microsoft-azure)
- [Nutanix](/zpa/app-connector-deployment-guide-nutanix-ahv)
- [OpenShift](/zpa/app-connector-deployment-guide-openshift)
- [VMware vCenter or vSphere Hypervisor (ESXi)](/zpa/connector-deployment-guide-vmware-platforms)
ZPA provides Security Technical Implementation Guide (STIG) images for AWS, GCP, Microsoft Azure, Nutanix, and VMware by default. To learn more, see [App Connector Software by Platform](/zpa/zpa-app-connector-software-by-platform).
[]![Deception App Connector](/downloads/zpa/app-connector-management/app-connectors/about-connectors/zpa-deception-integration-appConnectors2.png)