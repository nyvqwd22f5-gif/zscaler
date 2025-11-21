# Upgrading the Host OS and Software Packages
Source: https://help.zscaler.com/unified/upgrading-host-os-and-software-packages
PDF: https://help.zscaler.com/pdf/com/en/1496206.pdf

In this article, software components refer to App Connectors, Private Service Edges, and Private Cloud Controllers. Software components are licensed so that Zscaler can periodically update their software. However, updates to the host operating system (OS) and software packages are the organization's responsibility. Zscaler ensures that the virtual machine software is the latest version. The software component is designed to be compatible with updates to the host OS. To learn more, see [Managing Deployed App Connectors](/unified/managing-deployed-app-connectors#Updating), [Managing Deployed Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications), and [Managing Deployed Private Cloud Controllers](/unified/managing-deployed-private-cloud-controllers).
You can use this article to update RHEL 9.4 and 9.5 to RHEL 9.6.
Prerequisites
Before you update a software component's host OS, ensure the following prerequisites are met:
- Determine the frequency that the host OS should be updated. Zscaler recommends updating the OS at least every 5 weeks.
- Validate the software components and connectivity to the update servers.
- For prebuilt images, software components must be provisioned to a Private Applications tenant to receive software updates via the OS package manager.
For enhanced security, you must use the `passwd` command to change the credentials on the default admin account if you have not already done so.
- Enter the admin credentials for [App Connectors](/unified/managing-deployed-app-connectors#Default), [Private Service Edges](/unified/managing-deployed-private-service-edges-private-applications#Default), or [Private Cloud Controllers](/unified/managing-deployed-private-cloud-controllers#Default):.
zpa-connector login: admin
Password: *******
- Test connectivity by running the following command:
curl https://yum.private.zscaler.com
This is to validate that connectivity to the specific update URL is working. If you are waiting for the command to timeout, and you don't get any errors, you must troubleshoot connectivity. To learn more, see [Troubleshooting App Connectors](/unified/troubleshooting-app-connectors) or [Troubleshooting Private Service Edges for Private Applications](/unified/troubleshooting-private-service-edges-private-applications).
Updating the Host OS and Software Packages
The update of the host OS is scheduled according to local policy. Zscaler recommends notifying users of the potential for rolling reconnections during the update window. Each software component is estimated to be down for 20 minutes during the update.
To avoid application access and performance issues, you should not upgrade all App Connectors within an App Connector group or Private Service Edges within a Private Service Edge group at the same time. You can upgrade multiple App Connectors or Private Service Edges in a group simultaneously, provided that there are enough running App Connectors or Private Service Edges in the group to handle the traffic load.
Starting with App Connector version 24.650.4 and later, a version check and automated upgrade are performed during an initial connection. To learn more, see [Zscaler Trust](https://trust.zscaler.com/private.zscaler.com/security-advisories).
For host OS and software package updates, choose the component you want to update:
- [App Connector](#appc-update)
- [Private Service Edge](#pse-update)
- [Private Cloud Controller](#pcc-update)
-
[](Optional) Disable the App Connector you want to update.
When you disable the App Connector in the Admin Portal prior to stopping the service and updating, new connections are no longer routed through the component and existing connections will continue through to their conclusion. If you stop the service without first disabling the App Connector and allowing traffic to drain, it results in forced connection resets for users connected through that App Connector.
- Log in to the Admin Portal.
- Go to the App Connectors page (Infrastructure > Private Access > App Connectors).
- Click the **Edit** icon (![Pencil Icon in the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connector-managing-troubleshooting/updating-app-connector-host-os-and-software-packages/zpa-admin-portal-pencil-icon.png)
) for the App Connector you want to update.
-
Select **Disabled** under **Status** to disable the individual App Connector in the group.
[See image.](#See3)
- Access the [App Connector Status](/unified/accessing-app-connector-status-diagnostics) log type in the Admin Portal to view the list of currently active App Connectors to make sure any existing or long-lived critical transactions have ended or stopped.
- Log in to the App Connector console using your admin credentials.
- Stop the Private Applications service using the following command:
$ sudo systemctl stop zpa-connector
The command to stop the Private Applications service for a Private Service Edge is `sudo systemctl stop-zpa-service-edge`.
- Remove all cached files using the following command:
$ sudo yum clean all
Only use this command when Disaster Recovery Mode or Business Continuity is not activated and the system has full access to the repository.
- Using the following commands, remove old packages that are not used:
sudo yum remove --oldinstallonly -y
sudo yum autoremove -y
- After stopping the Private Applications service and removing the old packages, log in and enter the following command to update the local system software:
$ sudo yum update -y
- After completing the update, reboot the App Connector using the following command:
$ sudo reboot
- After the reboot, go to the Admin Portal and click the **Edit **icon for the App Connector.
- Select **Enabled** to enable the App Connector.
[See image.](#Enabled)
- Click **Save**.
- [](Optional) Disable the Private Service Edge you want to update.
- Log in to the Admin Portal.
- Go to the Private Service Edges page (Infrastructure > Private Access Components > Private Service Edges).
- Click the **Edit** icon (![Pencil Icon in the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connector-managing-troubleshooting/updating-app-connector-host-os-and-software-packages/zpa-admin-portal-pencil-icon.png)
) for the Private Service Edge that you want to update.
-
Select **Disabled** under **Status** to disable the individual Private Service Edge in the group.
[See image.](#pse-disable)
- Access the [Private Service Edge Status log type](/unified/accessing-private-service-edge-status-diagnostics) in the Admin Portal to view the list of currently active Private Service Edges to make sure any existing or long-lived critical transactions have ended or stopped.
- Log in to the Private Service Edge console using your admin credentials.
- Stop the `zpa-service-edge` using the following command:
`sudo systemctl stop-zpa-service-edge`
- Remove all cached files using the following command:
$ sudo yum clean all
Only use this command when Disaster Recovery Mode or Business Continuity is not activated and the system has full access to the repository.
- Using the following commands, remove old packages that are not used:
sudo yum remove --oldinstallonly -y
sudo yum autoremove -y
- After stopping the Private Applications service and removing the old packages, log in and enter the following command to update the local system software:
$ sudo yum update -y
- After completing the update, reboot the Private Service Edge using the following command:
$ sudo reboot
- After the reboot, go to the Admin Portal and click the **Edit **icon to edit the Private Service Edge.
- Select **Enabled** to enable the Private Service Edge.
[See image.](#pse-enabled)
- Click **Save**.
- [](Optional) Disable the Private Cloud Controller you want to update.
- Log in to the Admin Portal.
- Go to the Private Cloud Controllers page (Configuration & Control > Business Continuity > Business Continuity Management > Private Cloud Controllers).
- Click the **Edit** icon (![Pencil Icon in the ZPA Admin Portal](/downloads/zpa/app-connector-management/app-connector-managing-troubleshooting/updating-app-connector-host-os-and-software-packages/zpa-admin-portal-pencil-icon.png)
) for the Private Cloud Controller that you want to update.
-
Select **Disabled** under **Status** to disable the individual Private Cloud Controller in the group.
[See image.](#pcc-disable)
- Access the [Private Cloud Controller Status log type](/unified/accessing-private-cloud-controller-status-diagnostics) in the Admin Portal to view the list of currently active Private Cloud Controllers to make sure any existing or long-lived critical transactions have ended or stopped.
- Log in to the Private Cloud Controller console using your admin credentials.
- Stop the `zpa-pcc-service` using the following command:
$ sudo systemctl stop zpa-pcc
- Remove all cached files using the following command:
$ sudo yum clean all
Only use this command when Disaster Recovery Mode or Business Continuity is not activated, and the system has full access to the repository.
- Using the following commands, remove old packages that are not used:
sudo yum remove --oldinstallonly -y
sudo yum autoremove -y
- After stopping the service and removing the old packages, log in and enter the following command to update the local system software:
$ sudo yum update -y
- After completing the update, reboot the Private Cloud Controller using the following command:
$ sudo reboot
- After the reboot, go to the Admin Portal and click the **Edit **icon for the Private Cloud Controller.
- Select **Enabled** to enable the Private Cloud Controller.
[See image.](#pcc-enabled)
- Click **Save**.
[]![Disabling App Connector ](/downloads/zpa/app-connector-management/app-connector-managing-troubleshooting/updating-app-connector-host-os-and-software-packages/zpa-app-connector-disabled_0.png)
[]![Enabling an App Connector](/downloads/zpa/app-connector-management/app-connector-managing-troubleshooting/updating-app-connector-host-os-and-software-packages/zpa-app-connector-enabled_0.png)
[]![Disabling a Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/updating-host-os-and-software-packages-draft-doc-60000/pse-disable.png)
[]![Enabling a Private Service Edge](/downloads/tech-pubs-drafts/zpa-draft-articles/updating-host-os-and-software-packages-draft-doc-60000/pse-enable.png)
[]![Disabling a Private Cloud Controller in the Admin Portal](/downloads/tech-pubs-drafts/zpa-draft-articles/updating-host-os-and-software-packages-draft-doc-60000/pcc-disable_0.png)
[]![Enabling a Private Cloud Controller](/downloads/tech-pubs-drafts/zpa-draft-articles/updating-host-os-and-software-packages-draft-doc-60000/pcc-enable.png)